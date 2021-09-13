# NGINX PRACTICE

## 01_map

Split requests to specific upstream using map.

```
$ cd 01_map
$ docker build -t nginx:01_map
$ docker run -p 8080:80 nginx:01_map
$ curl localhost:8080/item/100001
> go to upstream ts-web
$ curl localhost:8080/item/100002
> go to upstream normal-web
```

