---
layout: post
title: Node Notes
tags: Node
category: Tech
---

### Installing 

#### Installing in Ubuntu 

[Installing Node via Package Manager](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)  

~~~
sudo apt-get install nodejs
sudo apt-get install npm
~~~

#### Install Locations

npm - /usr/share/npm

### First Steps  

#### Creating an Empty Project

~~~
npm init
~~~

npm init create an empty node project, which is a package.json file. The file will look something like this...  

~~~
{
  "name": "projectName",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
~~~

#### Adding Test Framework for specific location

We use mocha with chai. 

- Mocha is a test framework for JavaScript.  
- Chai is a BDD / TDD assertion library for node  

[Mocha](https://mochajs.org/)  
[Chai](http://chaijs.com/)  

By default the package.json file does not have any test framework setup. To leverage mocha, adjust the "test" attribute to look as follows...  

~~~	
  ...

  "scripts": {
    "test": "mocha sourceDir testDir --watch"
  },

  ...
~~~

> sourceDir & testDir are directories where your source and test code are located. Using the --watch means that mocha will rerun everytime there is a source code change.  

To start your test framework enter the following...

~~~
npm test  
~~~

#### Adding Test Framework for file convention

The following runs all tests under the src folder that match the file extension .test.js

~~~
  "scripts": {
    "test": "find ./src -iregex '.*.test.js' | xargs mocha -u tdd --reporter spec"
  },
~~~

#### Working with Dates

The [Moment.js](https://momentjs.com/) library a good library for handling dates in js.

#### General

Also called NTier Pattern

#### Node References 

[Structuring NodeJs Projects](https://blog.risingstack.com/node-hero-node-js-project-structure-tutorial/)

### Modules

#### Old approach

In you module file doSomethingModule.js...

~~~
module.exports = {
    doSomething: function() {
        return "something";
    }
}
~~~

in the file you want to consume it from...

~~~
var obj = require("../doSomethingModule.js");
console.log(obj.doSomething());                     // return something
~~~

#### New approach

In you module file doSomethingModule.js...

~~~
module.exports = class TheClass{
    
    doSomething() {
        return -1;
    }
}
~~~

in the file you want to consume it from...

~~~
var objType = require("../doSomethingModule.js");
var theObject = new objType();
theObject.doSomething();                            // return something
~~~

### Express 

### Hosting

[Running Node as a background service](http://stackoverflow.com/questions/4018154/node-js-as-a-background-service/29042953#29042953)  
[Latest Running Node as a background service](https://certsimple.com/blog/deploy-node-on-linux#shrinkwrap)  

### Sessions

[Using sessions in express](https://blog.xervo.io/nodejs-and-express-sessions)  

#### Express References 

[Express 4.x API](http://expressjs.com/4x/api.html)  
[Express source code](https://github.com/strongloop/express)  
[Express tutorials](https://shapeshed.com/creating-a-basic-site-with-node-and-express/)
[express.static](https://github.com/expressjs/serve-static)  
[Morgan](https://github.com/expressjs/morgan)  
[Soup to Bits: Building Blocks of Express.JS](https://www.codeschool.com/screencasts/soup-to-bits-building-blocks-of-express-js)  
[Soup to Bits: Real-time Web With Node.JS](https://www.codeschool.com/screencasts/soup-to-bits-real-time-web-with-node-js)  
[CodeSchool Discussion Forum](http://discuss.codeschool.io/t/building-blocks-of-express-js/7197)  
