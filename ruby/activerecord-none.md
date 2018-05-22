ActiveRecord's `none` method will return:

> a chainable relation with zero records, specifically an instance of the ActiveRecord::NullRelation class.

https://apidock.com/rails/v4.0.2/ActiveRecord/QueryMethods/none

As the docs imply, this allows for some neat functionality with classes that implement the Null Object pattern.

```ruby
# Null::Author object
require 'singleton'

module Null
  class Author
    include Singleton

    def posts
      Post.none
    end
  end
end
```

Now we can treat `posts` like an ActiveRecord relation, and not worry about anything breaking:

```ruby
author = Author.find_by(id: params[:author_id]) || Null::Author
published_posts = author.posts.where(published: true)
#=> []
```

This is obviously a contrived example.
