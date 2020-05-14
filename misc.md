# Miscellaneous

### Ubuntu Xenial debhelper mayhem

Ubuntu Xenial debhelper has a weird dependency issue with debhelper: debhelper-autoreconf is not installed on schroot creation ... needs to investigate (or not 🤷)

### Split file content based on regex into multiple files

```
awk '/<regexp>/{filename=NR".txt"}; {print >filename}' dump.txt
```

### Add logger to a shell script

```shell
cat >>/tmp/vagrant.log<<EOF
$(date) '${dir_name}' '${name}' '$*'
EOF
```

### Check start date of commands

```shell
ps -C <cmd> -o pid,ppid,command,lstart
```
