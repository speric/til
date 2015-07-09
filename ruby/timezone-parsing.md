`Time.zone.parse` differences depending on mm dd yyyy separator character:

```ruby
# Rails 3.2.21, ruby 2.0.0p353

# 'American' style
> Time.zone.parse("11/12/2012 10:10")
=> Mon, 12 Nov 2012 10:10:00 EST -05:00

# 'Rest of the world' style
> Time.zone.parse("11-12-2012 10:10")
=> Tue, 11 Dec 2012 10:10:00 EST -05:00
```
