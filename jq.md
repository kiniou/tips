# JQ examples

### select dict keys when their values does not match a string

```
jq -r 'to_entries | map(select(.value.altname | contains("monitoring") | not) | .key) | join(",")' < data.json
```

### filter nginx json logs by selecting POST queries on a specific vhost with response >= 400 and with timestamp transformed to ISO8601

```
jq '.| select(.verb == "POST") | select(.vhost | contains("srv1.")) | select(.response | tonumber >= 400)' | jq '.["timestamp_todate"] = (.timestamp | tonumber | todate)'
```
