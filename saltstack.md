# Saltstack

## find last jobs with `state.highstate` function

```shell
salt-run jobs.list_jobs search_function='state.highstate'
```

## get info on a job based on its jid

```shell
salt-run jobs.list_job <jid>
```
