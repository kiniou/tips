# JQ examples

### select dict keys when their values does not match a string

```
jq -r 'to_entries | map(select(.value.altname | contains("monitoring") | not) | .key) | join(",")' < data.json
```
