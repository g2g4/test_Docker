##Dockerfile (df01)
```
root@ubuntu-bionic:/tmp/pony# vim df01
```
```
FROM alpine:latest
RUN apk add --update \
    py-pip \
   && pip install httpony
VOLUME ["/tmp"]
CMD httpony -l 0.0.0.0 -p 81 >> /tmp/wwwpony/index.html
EXPOSE 81
```
##StartContainer
```
root@ubuntu-bionic:/tmp/pony#docker build . -t g2g4/pony:v1 -f df01
root@ubuntu-bionic:/tmp/pony#docker run -d -p 81:81 -v /tmp:/tmp g2g4/pony:v1
```
##TestContainer
```
curl http://127.0.0.1:81/test1/test2/test3/test4/test55
cat /tmp/wwwpony/index.html | grep GET
```
```
GET /mama/myla/ramu HTTP/1.1
GET /test1 HTTP/1.1
GET /test1/test2 HTTP/1.1
GET /test1/test2/test3 HTTP/1.1
GET /test1/test2/test3/test4 HTTP/1.1
GET /test1/test2/test3/test4/test55 HTTP/1.1
```
##Dockerfile (df02)
```
FROM httpd:2.4

```
##StartContainer
```
root@ubuntu-bionic:/tmp/pony#docker build -t my-apache2:v1 . -f df02
root@ubuntu-bionic:/tmp/pony#docker run -dit --name my-running-app -p 82:80 -v /tmp/wwwpony:/usr/local/apache2/htdocs/ my-apache2:v1
```
##TestContainer
```
curl http://127.0.0.1:82
```
