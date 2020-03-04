# HAProxy Parser

This parser works for HAProxy, tested with documentation examples and a HAProxy instance running version 2.1

There might be missing types, and if you have customized the logs in any way this may not work.


Because of limits in syslog, the `http_request` field may be truncated, in this case the field `truncated` will be set to `true`.


Sometimes the `http_request` field contains garbage, I am assuming this comes from bad requests. To find cases of this you can run the search `http_request=* method!=*` as the method and path will not be parsed in this situation.

# Important

You have to change the timezone in the `parseTimestamp` line unless you are logging in UTC

# Tests
```
Feb  6 12:12:56 localhost haproxy[18989]: 10.0.0.1:34552 [15/Oct/2003:15:26:31.462] px-http px-http/srv1 3183/-1/-1/-1/11215 503 0 - - SC-- 205/202/202/115/3 0/0 "HEAD / HTTP/1.0"
```

```
Feb  6 12:12:56 localhost haproxy[674]: 127.0.0.1:33318 [15/Oct/2003:08:31:57.130] px-http px-http/srv1 6559/0/7/147/6723 200 243 - - ---- 5/3/3/1/0 0/0 "HEAD / HTTP/1.0"
```

```
Dec  3 18:27:14 localhost haproxy[6103]: 127.0.0.1:56059 [03/Dec/2012:17:35:10.380] frt/f1: Connection error during SSL handshake
```

```
Feb  6 12:14:14 localhost haproxy[14389]: 10.0.1.2:33317 [06/Feb/2009:12:14:14.655] http-in static/srv1 10/0/30/69/109 200 2750 - - ---- 1/1/1/1/0 0/0 {1wt.eu} {} "GET /index.html HTTP/1.1"
```

```
Feb  6 12:12:56 localhost haproxy[14387]: 10.0.1.2:33313 [06/Feb/2009:12:12:51.443] fnt bck/srv1 0/0/5007 212 -- 0/0/0/0/3 0/0
```

```
<134>Mar  4 10:35:10 Ubuntu-1804-bionic-64-minimal haproxy[27811]: 10.11.12.13:54485 [04/Mar/2020:10:35:10.553] http_front~ http_back/humio 1/0/0/8/10 200 1023 - - ---- 5/5/2/2/0 0/0 "GET /api/v1/repositories/HAProxy_local/queryjobs/1337 HTTP/1.1"
```


## Resources:
* [HAProxy log samples](https://www.haproxy.com/documentation/hapee/2-0r1/onepage/#8.9)
* [TCP format information](https://www.haproxy.com/documentation/hapee/2-0r1/onepage/#8.2.2)
* [HTTP format information](https://www.haproxy.com/documentation/hapee/2-0r1/onepage/#8.2.3)
* [Error format information](https://www.haproxy.com/documentation/hapee/2-0r1/onepage/#8.2.5)