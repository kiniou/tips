# Tips and tricks 👌

## Linux

## Dbus error when calling `systemctl --user`

This will happen when `libpam-systemd` package is not installed.

Should be installed by default with `dbus-session-user` package in latest
Debian-based distributions.

## Unbound

### wildcard *.docker.localhost

In `/etc/unbound/unbound.conf.d/docker.localhost.conf` :

```
local-zone: "docker.localhost." redirect
local-data: "docker.localhost IN A 127.0.0.1"
```

## Traefik.io

### get Docker containers registered in Traefik (API) :

```shell
$ curl -s "http://localhost:8080/api" | \
  jq '.docker | .frontends | .[] | .routes | .[] | .rule | split(":")[1]'
```


## Saltstack

### states order matters :

In top.sls (or included sls within a state), the order of states will be
processed in the declared order.

```sls
 - "role:webserver":
    - apache
    - php-fpm
    - other_packages
```

The webserver role will apply its states in the following order:
1. apache.sls
2. php-fpm.sls
3. other_packages.sls
