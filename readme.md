## usage 
```
docker run -d -p 81:81 -v /tmp:/tmp g2g4/ponytest 
```
## make test request to HTTP listener

web-browser http://127.0.0.1:81/your_message

or
``` 
curl http://127.0.0.1:81/your_message2/test/
```
## check incomming requests
```
cat /tmp/index.html
```
## Also your can bring up http-server and publish all http-request which stored in /tmp/index.html
```
docker run -dit --name ponytestHTTP -p 82:80 -v /tmp:/usr/local/apache2/htdocs/ httpd:2.4
```
## show requests

web-browser http://127.0.0.1:82

or
```
curl http://127.0.0.1:82
```
## Example. My real output
```
cat /tmp/index.html
```
```
GET /test1/test2/test3 HTTP/1.1
Accept-Language: ru-RU,ru;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
Host: 192.168.50.50:81
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Upgrade-Insecure-Requests: 1
Connection: keep-alive
Cookie: PHPSESSID=b98smjrkc7tkgnder
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:69.0) Gecko/20100101 Firefox/69.0

GET /test1/test2/test3/test4/test55 HTTP/1.1
Host: 127.0.0.1:81
Accept: */*
User-Agent: curl/7.58.0

GET /test1/test2/test3/test4/test556677 HTTP/1.1
Host: 127.0.0.1:81
Accept: */*
User-Agent: curl/7.58.0
```
```
cat /tmp/index.html | grep GET
```
```
GET /tiesto/est/testo.html34 HTTP/1.1
GET /mama/myla/ramu HTTP/1.1
GET /test1 HTTP/1.1
GET /test1/test2 HTTP/1.1
GET /test1/test2/test3 HTTP/1.1
GET /test1/test2/test3/test4 HTTP/1.1
GET /test1/test2/test3/test4/test55 HTTP/1.1
GET /test1/test2/test3/test4/test556677 HTTP/1.1
```
===========================================
## P.S. You can get access to your HTTP servers from another host. Just use your server-ip instead of 127.0.0.1.
## Inspired by 
 * https://pypi.org/project/httpony/ 
 * https://github.com/mblayman/httpony
