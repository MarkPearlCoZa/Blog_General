---
layout: post
title: React Notes
tags: React
category: Tech
---

### Scripts to use ###

~~~
script src="vendors/react.js"
script src="vendors/react-dom.js"
script src="vendors/babel.js">
script type="text/babe;" src="components.js"
~~~

### Props & Components Communication ###

When writing a component, there is a pattern we follow:

~~~
class NewComponent extends React.Component {
  render() {
    return ( ... );
  }
}
~~~

Arguments passed to components are called props. They look similar to regular HTML element attributes.

Arguments passed to components can be accessed using the this.props object.

e.g.

~~~
{this.props.author}
~~~

then using it in a compontns can be done as follows...

~~~
<MyComponent autor="Bob" />
~~~

#### Mapping an array to Jsx ####

~~~
class CommentBox extends React.Component {
 ...
   _getComments() {
    const commentList = [
     { id: 1, author: 'Morgan', body: "Great picutre!" },
     { id: 2, author: 'Bending', body: "Thanks" }
    ];

    return commentList.map((comment) => {
      return (
        <Comment author={comment.author} body={comment.body} key={comment.id} />
    )};
  }

  render() {
    const comments = this._getComments();
    return (
	<p> {comments} </p>
    )
  }
}
~~~

** In Jsx, anything written in {} is interpreted as literal javascript. **

### Component State ###

The state is a JavaScript object that lives inside each component. We can access it via this.state

~~~
if (this.state.ShowComments) ...
~~~

We set the initial state of our component in the class constructor...

~~~
class CommentBox extends React.Components {
  constructor() {
    super();       // super() must be called in our constructor
    this.state = {
      stateName : stateValue
    };
  }
}

We don't assign to the state object directly - instead, we call setState by passing it an object.

~~~
this.setState({stateName: newValue});
~~~

Things that can cause state to change:
- button clicks  
- link clicks  
- form submission  
- ajax calls  

~~~
class CommentBox extends React.Component { ...  
  render() {
   ...
   <button onClick={this._handleClick.bind(this)}> Show Comments</button>
   ...
  }

  _handleClick() {
    this.setState({ 
      showComments: !this.state.showComments
    }); 
  }
~~~

### Something ###

In order to ensure events have consistent properties across different browsers, React wraps the browser's native events into synthetic events, consolidating browser behaviors into one API.

We use reacts events system to capure user input, including form submissions and button clicks.

Refs allow us to reference DOM Elements in our code after the component has been rendered.

Parent components can pass callback functions as props to child componets to allow two-way communication.

In React we use **refs** to reference DOM Elements in our code after the component has been rendered.

### Talking to remote servers ###

jQuery helps us make Ajax request. 

An example of getting data using JQuery.

~~~
class CommentBox extends React.Component {
 ...
 _featchComments() {
	jQuery.ajax({
		method: 'GET',
		url: '/api/comments',
		success: (comments) => {
			this.setState({ comments })
		}
 });
}
~~~

To call a method before the render method is called use React's life cycle methods.

### Lifecycle Events ###

Lifecycle methods in React are functions that get called while the component is rendered for the first time or about to be removed from the DOM.

LifeCycle... 
- constructor() ->  
- componentWillMount() ->  
- render() ->  
- componentDidMount() ->  
- componentWillUnmount() ->

For a full lust of React's lifecycle methods, visit http://go.codeschool.com/react-lifecycle-methods  

In React, mounting means rendering for the first time.  

~~~
class CommentBox extends React.Component {

 ...

 componentWillMOunt() {
	_fetchComments();
 }

 ...

 _featchComments() {
	jQuery.ajax({
		method: 'GET',
		url: '/api/comments',
		success: (comments) => {
			this.setState({ comments })
		}
 });
}
~~~

### Polling ###

In order to check whether new comments are added, we can periodically check the server for updates.  

The componentDidMount method is called after the component is rendered to the page it is a good place to wire up polling.

~~~
class CommentBox extends React.Component {

 ...

 componentWillMount() {
	_fetchComments();
 }

 ...

 componentDidMount() {	// Mounts a polling event
	this._timer = setInterval(() => this._fetchComments(), 5000);
 }

 ...

 _featchComments() {
	jQuery.ajax({
		method: 'GET',
		url: '/api/comments',
		success: (comments) => {
			this.setState({ comments })
		}
 });
}
~~~

React optimizes the rendering process by only updating the DOM when changes are detected on the resulting markup.

### Memory Leads on Page Change ###

- Page changes in a single-page app environment will cause each CommentBox component to keep loading new comments every five seconds, even when they're no longger being displayed.

Each component should be responsible for removing any timers it has created. We do this in the componentWillUnmount method.

~~~
class CommentBox extends React.Component {

 ...

 componentDidMount() {
	this._timer = setInterval(() => this._fetchComments(), 5000);
 }
 ...

 componentWillUnmount() {
	clearInterval(this._timer); //Run when component is about to be removed from the DOM
 }
}
~~~

### Working with remote servers ###

~~~
class CommentBox extends React.Component { ...
	_deleteComment(comment) {
		jQuery.ajax({
			method: 'DELETE',
			url: '/api/comments/${comment.id}'
		});

	
		const comments = [...this.state.comments];
		const commentIndex = comments.infexOf(comment);
		comments.splice(commentIndex, 1);

		this.setState({ comments });
	}

	_handleDelete(event) {
		event.prevenDeault();
		if (confirm('Are you sure?')) {
			this.props.onDelete(this.props.comment);
		}
	}

	_addComment(author, body) {
		const comment = { author, body };

		jQuery.post('/api/comments', { comment })
			.success(newComment => {
				this.setState({ comments: this.state.comments.concat([newComment]) });
		});
	}
}
~~~

One way control flow.

In reazct controls flows from higher level components down to child components, forcing changes to happen reactively. This keeps apps modular and fast.


## Remember ##

Parent components can send data to child components using props
Child components can accept call functions as props to communicate back with parent com
#### References ####

[Add a Build System to a React Application]("https://www.codeschool.com/screencasts/add-a-build-system-to-a-react-application")
[ES2015 and the Virtual DOM in a React Application]("https://www.codeschool.com/screencasts/es2015-and-the-virtual-dom-in-a-react-application")
[Add a Router to a React Application]("https://www.codeschool.com/screencasts/add-a-router-to-a-react-application")
[Pluralsight Course: Styling React Components]("https://www.pluralsight.com/courses/react-styling-components")
[Egghead series: React Fundamentals]("https://egghead.io/series/react-fundamentals")
[Tutorial: React in 15ish minutes]("https://youtu.be/PGUMRVowdv8")
[Official React Documentation]("https://facebook.github.io/react/index.html")
