# waka-flocka-frame

<strong>Waka Flocka Frame HTTP Framework</strong>

A simple http framework to take mundane out of the mundane. Quickly create a basic http server with essential router functions by typing just a few lines of code.

<h2>Features</h2>
<ul>
 <li>HTTP Server</li>
 <li>REST request, response</li>
 <li>GET</li>
 <li>POST</li>
 <li>Automatic Content-Type Detection for Headers</li>
</ul>

<h2>How to use the WWF framework</h2>
-------------
<h3>Installation</h3>
-------------
<h4>Initialize your local repository</h4>
  ```npm init```

<h4>Install WFF</h4>
  ```npm install --save```

```npm install waka-flocka-frame```

<h4>Then require ('waka-flocka-frame') in your project.</h4>

```var wwf = require('waka-flocka-frame')```

--------------------
###Example code to quickly set up a http server
```var wff = require('waka-flocka-frame');```
```wff.server.listen();```

Syntax is
```wff.server.listen([optional port number]);```
Leaving out the port number will invoke the default port 3000.

```var wff = require('waka-flocka-frame');```

  ```wff.server.listen();```

###Example code to quickly set up a simple route.
Syntax is ```wff.router.get( '[your route]', '[a text string]');```
Parameters are a route and a simple text string you would like
in your response.
```wff.router.get('/home', 'a text string');```
This will return 'a text string' at the '/home' route.
If you want a response other than plain text you MUST use a callback
and response.writeHead.


###Example code to quickly set up a static route.
Syntax is ```wff.router.getStatic('[your resource]', '[your route]');```
Parameters are a path to a resource and a route.
```wff.router.getStatic('someText.txt', '/test')```
This will return the contents of the 'someText.txt' file at the '/test' route.

##Example code to quickly set up a POST route without a callback.
Syntax is ```wff.router.post('[url you are posting to]');```
Parameter is the route you are posting to.
```wff.router.post('/myBlog');
This will allow you to use a REST client to post JSON content to the '/myBlog' route.

##Example code to create a POST route with an optional callback.
```wff.router.post('[url you are posting to]', function(req, res){
  var concatData = '';
  req.on('data', function(data){
    concatData += data.toString();
  });
  req.on('end', function() {
    res.writeHead(200, {"Content-Type": "application/json"});
    res.write(concatData);
    res.end();
  });```
