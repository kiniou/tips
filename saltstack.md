# Saltstack

## find last jobs with `state.highstate` function

```shell
salt-run jobs.list_jobs search_function='state.highstate'
```
