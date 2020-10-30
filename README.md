# docker_starter

```
FROM alpine as base
WORKDIR /foo
RUN echo test > test.txt

FROM alpine
WORKDIR /bar
COPY --from=base foo/test.txt .
```
