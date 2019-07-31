# Saltstack

## find last jobs with `state.highstate` function

```shell
salt-run jobs.list_jobs search_function='state.highstate'
```

## get info on a job based on its jid

```shell
salt-run jobs.list_job <jid>
```

## 🛡 Don't store a job run with sensitive data in the salt-master job cache


>ℹ As of writing this, i'm not aware of any method to sanitize sensitive data saved by salt returners.
>
>The job publication is passed to the returners in the `_prep_jid` method in
>ClearFuncs (somehow used by salt.client.LocalClient 🤷)
>
>Therefore, if you just want to avoid storing the sensitive arguments passed to minion (and
>until saltstack comes with a job cache sanitizer), you just need to add an
>`extra` kwarg to the `client.cmd` with a dictionary containing `'nocache':
>True`.

```python
client = salt.client.get_local_client()
results = client.cmd('*',
                      "some_module.some_sensitive_func",
                      kwarg={'password': password},
                      extra={'nocache': True})
```
