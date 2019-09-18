# JQ examples

### select dict keys with its value does not match a string

```
jq -r 'to_entries | map(select(.value.altname | contains("monitoring") | not) | .key) | join(",")' < data.json
```
