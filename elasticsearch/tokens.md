Preview how Elasticearch will tokenize a given string:

```
curl http://localhost:9200/my_index_name/_analyze\?tokenizer\=uax_url_email \
-d 'eric@example.com'

> {"tokens":[{"token":"eric@example.com","start_offset":0,"end_offset":16,"type":"<EMAIL>","position":0}]}%
```

Reference:

https://tryolabs.com/blog/2015/02/25/elasticsearch-analyzers-or-how-i-learned-to-stop-worrying-and-love-custom-filters/
