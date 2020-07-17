# Docker

### Cleanup networks without containers attached and only created by docker-compose
```
docker network ls -q \
    | xargs docker network inspect \
    | jq -r '.[] | select((.Containers|length == 0) and (.Labels|has("com.docker.compose.network")) ) | .Id' \
    | xargs docker network rm
```
