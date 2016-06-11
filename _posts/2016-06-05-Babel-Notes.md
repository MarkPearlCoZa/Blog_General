---
layout: post
title: Babel Notes
tags: html
category: Tech
---

#### Babel-polyfill ####

Allows you to use some of the features of ES6 that do not transcompile.

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

#### References ####

[Pluralsight Babel Course](https://www.pluralsight.com/courses/babel-get-started)  
