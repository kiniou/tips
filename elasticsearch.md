# Elasticsearch

## Get recovery status and progression

watch 'curl -sSL http://localhost:9200/_cat/recovery?active_only=true\&v'

## List indices

curl -sSL http://localhost:9200/_cat/indices?v
