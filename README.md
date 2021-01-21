# docker_starter


## little example of build docker using multistage

```
FROM alpine as base
WORKDIR /foo
RUN echo test > test.txt

FROM alpine
WORKDIR /bar
COPY --from=base foo/test.txt .
```

## clean docker space

```
docker rm $(docker ps -a | awk '{ print $1 }')
```

### Cleanup exited processes:
```
docker rm $(docker ps -q -f status=exited)
```
### Cleanup dangling volumes:
```
docker volume rm $(docker volume ls -qf dangling=true)
```
### Cleanup dangling images:
```
docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
```
### Remove all images
```
docker rmi -f $(docker images -q)
```
### Stop all
```
docker stop $(docker ps -a -q)
```
### Remove all containers
```
docker rm $(docker ps -a -q)
```
