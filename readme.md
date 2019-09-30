##usage 
```
docker run -d -p 81:81 -v /tmp:/tmp g2g4/ponytest 
```
##make test request to HTTP listener
web http://127.0.0.1:81/your_message
or
``` 
curl http://127.0.0.1:81/your_message2/test/
```
##check incomming requests
```
cat /tmp/index.html | grep GET
```
##or bring up http server (index.html reveals incoming requests)
```
docker run -dit --name ponytestHTTP -p 82:80 -v /tmp:/usr/local/apache2/htdocs/ httpd:2.4
```
##show requests
web http://127.0.0.1:82
```
curl http://127.0.0.1:82
```
###note. You can use remote acees to the your HTTP-servers. Just use your server ip instead 127.0.0.1
====================================
###Dockerfile httpony HTTP Listener
```
FROM alpine:latest
RUN apk add --update \
    py-pip \
   && pip install httpony
VOLUME ["/tmp"]
CMD httpony -l 0.0.0.0 -p 81 >> /tmp/index.html
EXPOSE 81
```
