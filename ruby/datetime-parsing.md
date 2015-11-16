If you do not specify a timezone when parsing using the `DateTime`
class, what you get back is a time in "UTC" time:

```
> DateTime.parse("11/16/2015")
Mon, 16 Nov 2015 00:00:00 +0000
```

I had incorrectly assumed you could "chain" the `in_time_zone` method,
giving me the time I passed into `DateTime.parse`, in the time zone I
requested. But the time is not "lazily evaluated", and so the following
won't be equal

```
> DateTime.parse("11/16/2020 11:59:58 PM").in_time_zone("Berlin).utc.to_s
"2020-11-16 23:59:58 UTC"
> ActiveSupport::TimeZone[site.time_zone].parse("11/16/2020 11:59:58 PM").utc
2020-11-16 22:59:58 UTC
```

The first example is essentially saying, "what is 11:59:59 PM UTC in
Berlin time?", and the second is saying, "what is 11:59:59 PM Berlin
time in UTC time?", which is what I was after.

In retrospect it's so obvious!

Relatedly, you can do:
```
> Time.zone = "Berlin"
> Time.zone.parse("11/16/2020 11:59:58 PM").utc
2020-11-16 22:59:58 UTC
```
