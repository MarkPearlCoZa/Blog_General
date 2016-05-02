---
layout: post
title: React Notes
tags: React
category: Tech
---

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

#### References ####

[]()  
