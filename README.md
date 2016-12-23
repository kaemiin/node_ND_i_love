# About this Project

##This is a TEST - Node.js + Docker 

###Ref:
https://hub.docker.com/_/node/
https://nodejs.org/en/docs/guides/anatomy-of-an-http-transaction/

###Download a image:
```
docker pull node
```

###Write a Echo Server:
```
vim echo-server.js
```
```
var http = require('http');

http.createServer(function(request, response) {
  if (request.method === 'GET' && request.url === '/echo') {
    request.pipe(response);
  } else {
    response.statusCode = 404;
    response.end();
  }
}).listen(8080);
```

###Run a single Node.js script:
```
docker run -it --rm --name local-node -p 8080:8080 -v "$PWD":/usr/src/app -w /usr/src/app node:latest node echo-server.js
```

###驗證
```
http://192.168.99.100:8080/echo
```

