---
layout: post
title:  "The Power of Bind method in Javascript"
date:   2017-08-17 8:28:41 +0000
---


During the course of coding the final project using React framework, I found myself using 'bind' quite a few times. Wherever I have click/hover actions, I would subconsciously/automatically write something along the line of:

```
this.handleClickCallback = this.handleClickCallback.bind(this);

```

When instructor asked me why did I used bind, my mind went into panick mode and I utterred something like: so when user clicks on the button and this function will be used later??? If it's not bound, then the button doesn't work???  All the question marks are not for dramatic effect, I have been using the method though my understanding was only skin deep... Here is a refresher on bind() in the context of React & ES6.


**what is this???**

 'this' is a powerful word in Javascript. Everything in Javascript is an object including a function. 
 
> The value of this, when used in a function, is the object that "owns" the function. [source](https://www.w3schools.com/js/js_function_invocation.asp)
> 

**bound to 'this'**

'this' could refer to different objects as the scopes change.

> The simplest use of bind() is to make a function that, no matter how it is called, is called with a particular this value. [source]https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
> 


**something borrowed**

In the context of React written in ES6 syntax, when the component is instantiated from the React library, 'this' is referred to the component itself and the event handler method is usually declared inside the classs.  The buttons, links or other non-React sources are the objects being clicked on, hovered over, etc.   Since class methods are not bound automatically, to get access to the states & props, we have to bind this.handleClickCallback and pass it to onClick explicitly, otherwise 'this' will be undefined.

It is recommended to do the binding in constructor where it will be called once:

```
  constructor() {
    super()
    this.handleClick = this.handleClickCallback.bind(this)  
  }
	```
	
	Rather than in render() where it gets called every time the component re-renders:
	```
	  render() {
    return <button onClick={this.handleClickCallback.bind(this)}>Click me!</button>
  }
	```

[source 1](https://facebook.github.io/react/docs/handling-events.html)
[source 2](http://reactkungfu.com/2015/07/why-and-how-to-bind-methods-in-your-react-component-classes/)

The above explanation is still only skin deep because skin has multiple layers. Learning continues...










 


