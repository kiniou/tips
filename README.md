# Tips and tricks 👌

## Linux

## Dbus error when calling `systemctl --user`

This will happen when `libpam-systemd` package is not installed.

Should be installed by default with `dbus-session-user` package in latest
Debian-based distributions.

## Unbound

### wildcard *.docker.localhost

💡 *This minimal configuration is handy to target Traefik containers by their
generated hostnames.*

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
processed in the declared order :

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


## Docker

### Cleanup images and containers

1. Remove containers that are not running anymore:
```shell
docker ps -q -a -f=status={created,exited,dead} | xargs --no-run-if-empty docker rm
```

2. Remove unused images
```shell
docker images -f=dangling=true -q | xargs --no-run-if-empty docker rmi
```


### fix bind mounts permissions with `userns-remap`

`/etc/docker/daemon.json`
```json
{
  "userns-remap": "USER"
}
```

`/etc/subuid`
```
USER:1000:1
USER:100000:65536
```


`/etc/subgid`
```
USER:<docker_group>:1
USER:100000:65536
```

Replace USER with your `user` login and `<docker_group>` with GID of docker
(usefull in order to allow some container to access `docker.socket`)

Restart your docker daemon and you will see future bind mounted volumes owned by your user 😜.


## SSH

### Proxy HTTP(S) to remote host via SOCKS5

```
ssh -D localhost:8080 <user>@<remote-host>
```

Then setup your browser's proxy extension with a SOCK5 proxy pointing at localhost:8080


## SystemD

### Completely override ExecStart service with drop-in configuration

Put an `override.conf` file in the corresponding `<service>.d` (eg. `/etc/systemd/user/amazing.service.d`):

```
[Service]
ExecStart=
ExecStart=/bin/true
```

## .env (dotenv)

### Load .env in shell
```shell
export $(grep -Ev '^#' ./.env | xargs );
```
