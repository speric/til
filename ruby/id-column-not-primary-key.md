Given a (weird) table called `foos` with columns like:
```
rowid
id
nam
```

Where `rowid` is the primary key, and `id` is just a "regular" column in the database, you'd set up your model like:

```ruby
class Foo < ActiveRecord::Base
  self.primary_key = "rowid"
end
```

But if you did `Foo.first.id`, you'd get the value of the `rowid` column, because of [this](https://github.com/rails/rails/blob/4-2-stable/activerecord/lib/active_record/attribute_methods/read.rb#L86).

The way around this is to do:

```
Foo.first.handle.send(:_read_attribute, :id)
```

Which will give you the real value of `id`.

H/T @brandonhilkert
