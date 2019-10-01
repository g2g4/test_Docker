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
cat /tmp/index.html | grep GET
```
## Also your can bring up http-server (index.html reveals incoming requests)
```
docker run -dit --name ponytestHTTP -p 82:80 -v /tmp:/usr/local/apache2/htdocs/ httpd:2.4
```
## show requests

web-browser http://127.0.0.1:82

or
```
curl http://127.0.0.1:82
```
## P.S. You can get access to your HTTP servers from another host. Just use your server-ip instead of 127.0.0.1.
## Inspired by 
 ..* https://pypi.org/project/httpony/ 
 ..* https://github.com/mblayman/httpony
