# EJS Layouts

`EJS Layouts` aims to add layout capibilities to frameworks for ejs.

## Install

```
npm install ejs-layouts
```

## Usage

**Layout.ejs**

```html
<html>
	<head>
		<title><%- title %></title>
  <body>
  	<%- content %>
  </body>
</html>
```

**Home.ejs**

    <div>
      <%- name %>! Welcome to my site!
    </div>

### Express

```
var express = require('express')
var ejs_layout = require('ejs-layouts');

var app = express();

app.configure(function(){
  app.set('views', __dirname + '/views');
  app.set('view engine', 'ejs');
  app.use(ejs_layout.express);
  app.use(app.router);
});

server.listen(3000);

app.get('/', function(req, res) {
  res.layout('Layout', {title:"Homepage"}, {content:{block:"Home", data:{name:"Matthew"}}});
});
```

**Result**

```
<html>
	<head>
		<title>Homepage</title>
  <body>
  	<div>
      Matthew! Welcome to my site!
    </div>
  </body>
</html>
```