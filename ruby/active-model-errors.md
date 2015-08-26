In Rails 3.2.x, simply accessing any key of an `ActiveModel::Errors` object will initialize that key with a blank value. Consider:

```
> errors = ActiveModel::Errors.new(self)
{}
> errors["foo"].present?
false
> errors
{
  :foo => []
}
```

This is because of the following:

```ruby
def [](attribute)
  get(attribute.to_sym) || set(attribute.to_sym, [])
end
```

If you want to see if some key has an error defined already, it'd be better to do:

```ruby
errors.include?(:key) && errors[:key].present?
```

Even though it `ActiveModel::Errors` behaves like a Hash, the implementation details are different.

Check the <a href="https://github.com/rails/rails/blob/6c8cf21584ced73ade45529d11463c74b5a0c58f/activemodel/lib/active_model/errors.rb#L135">source</a>, and also <a href="https://github.com/rails/rails/pull/18634">this PR</a>.
