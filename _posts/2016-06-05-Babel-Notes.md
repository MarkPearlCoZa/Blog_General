---
layout: post
title: Babel Notes
tags: Web JavaScript
category: Tech
---

#### Babel-polyfill ####

Allows you to use some of the features of ES6 that do not transcompile.
 
---------------------------------------------------------------------------------

#### Installing Babel Locally ####
 
~~~
npm init
npm install –save-dev babel-cli
~~~
 
Package.json is useful for resolving default projects - once setup on a new machine you just need to do

~~~
npm install
~~~
 
---------------------------------------------------------------------------------

#### Compiling code with Babel ####
 
The following outputs the transpiled code to the screen:  

~~~
babel src
~~~
 
 
npm install babel-preset-es2015 –save-dev
 
babel src –presets es2015
 
~~~
babel src –presets es2015 –out-dir build
~~~
 
#### Combine files into one bundle ####
 
~~~
babel src –presets es2015 –out-file build/bundle.js
~~~
 
##### using a json file for cli ####
 
.babelrc json file
 
---------------------------------------------------------------------------------

#### Installing Plugins ####
 
Go to babeljs.io > plugins section

---------------------------------------------------------------------------------

#### Getting Babel to work with React #### 

~~~
npm install react react-dom –save
npm install babel-preset-react –save-dev
~~~
 
Your Package.json file should look as follows:  
 
~~~
“scripts”: {
                “build” : “babel src –out-dir dist”
},
…
“devDependencies”: {
                “babel-cli”: “^6.2.0”,
                “babel-preset-es2015”: “^6.1.18”,
                “babel-preset-react”: “^6.3.13”
},
“dependencies”: {
                “react”: “^0.14.6”,
                “react-dom”: “^0.14.6”
}
~~~

#### Getting Babel as part of NPM Build Pipeline

[How to use babel for production](https://medium.com/@Cuadraman/how-to-use-babel-for-production-5b95e7323c2f#.u9v8j0k0e)  

#### References ####

[Pluralsight Babel Course](https://www.pluralsight.com/courses/babel-get-started)  
