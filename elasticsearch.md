# Elasticsearch

## Get recovery status and progression

```shell
watch 'curl -sSL http://localhost:9200/_cat/recovery?active_only=true\&v'
```

## List indices

```shell
curl -sSL http://localhost:9200/_cat/indices?v
```
