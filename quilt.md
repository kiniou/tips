# Quilt usage

## Create patch series

- Initialize quilt metadata (optional)
```shell
quilt init
```

- Create _ab-style_ patches
```shell
quilt new -p ab <name_of_your>.patch
```

- Add file to the patch
```shell
quilt add <file>
```

- Do your changes in <file>
```shell
(nano|vim|emacs) <file>
```

- Refresh quilt patch
```shell
quilt refresh
```

- Remove patches from the stack (ie. revert patches)
```shell
quilt pop -a
```

## Edit patches

```shell
quilt push <name_of_your>.patch
```


## Apply patches

with quilt:
```shell
quilt apply
```

without quilt:
```
patch -p1 < patches/<name_of_your>.patch
```
