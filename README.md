# NGINX PRACTICE

## 01_map

Split requests to specific upstream using map.
Key is $uri, value is boolean(0, 1).
If $uri exist on map, it makes $is_ts_item(custom variable) as 1.

```
map $uri $is_ts_item {
  default 0;
  volatile; # indicates that the variable is not cacheable
  /item/100001  1;
  /item/100003  1;
  /item/100001/ 1;
  /item/100003/ 1;
}
```


### How to run
```
$ cd 01_map
$ docker build -t nginx:01_map
$ docker run -p 8080:80 nginx:01_map
$ curl localhost:8080/item/100001
> go to upstream ts-web
$ curl localhost:8080/item/100002
> go to upstream normal-web
```

