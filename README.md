# Front-end Job Interview Questions

This file contains a number of front-end interview questions that can be used when vetting potential candidates. It is by no means recommended to use every single question here on the same candidate (that would take hours). Choosing a few items from this list should help you vet the intended skills you require.

**Note:** Keep in mind that many of these questions are open-ended and could lead to interesting discussions that tell you more about the person's capabilities than a straight answer would.

## Table of Contents

  1. [General Questions](#general-questions)
  1. [HTML Questions](#html-questions)
  1. [CSS Questions](#css-questions)
  1. [JS Questions](#js-questions)
  1. [Testing Questions](#testing-questions)
  1. [Performance Questions](#performance-questions)
  1. [Network Questions](#network-questions)
  1. [Coding Questions](#coding-questions)
  1. [Fun Questions](#fun-questions)

## Getting Involved

  1. [Contributors](#contributors)
  1. [How to Contribute](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/CONTRIBUTING.md)
  1. [License](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/LICENSE.md)

#### General Questions:

* What did you learn yesterday/this week?
* What excites or interests you about coding?
* What is a recent technical challenge you experienced and how did you solve it?
* What UI, Security, Performance, SEO, Maintainability or Technology considerations do you make while building a web application or site?
* Talk about your preferred development environment.
* Which version control systems are you familiar with?
* Can you describe your workflow when you create a web page?
* If you have 5 different stylesheets, how would you best integrate them into the site?
* Can you describe the difference between progressive enhancement and graceful degradation?
* How would you optimize a website's assets/resources?
* How many resources will a browser download from a given domain at a time?
  * What are the exceptions?
* Name 3 ways to decrease page load (perceived or actual load time).
* If you jumped on a project and they used tabs and you used spaces, what would you do?
* Describe how you would create a simple slideshow page.
* If you could master one technology this year, what would it be?
* Explain the importance of standards and standards bodies.
* What is Flash of Unstyled Content? How do you avoid FOUC?
* Explain what ARIA and screenreaders are, and how to make a website accessible.
* Explain some of the pros and cons for CSS animations versus JavaScript animations.
* What does CORS stand for and what issue does it address?

#### HTML Questions:

* What does a `doctype` do?
* What's the difference between full standards mode, almost standards mode and quirks mode?
* What's the difference between HTML and XHTML?
* Are there any problems with serving pages as `application/xhtml+xml`?
* How do you serve a page with content in multiple languages?
* What kind of things must you be wary of when design or developing for multilingual sites?
* What are `data-` attributes good for?
* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.
* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
* What is progressive rendering?
* Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
* Have you used different HTML templating languages before?

#### CSS Questions:

* What is the difference between classes and IDs in CSS?
* What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
* Describe Floats and how they work.
* Describe z-index and how stacking context is formed.
* Describe BFC(Block Formatting Context) and how it works.
* What are the various clearing techniques and which is appropriate for what context?
* Explain CSS sprites, and how you would implement them on a page or site.
* What are your favourite image replacement techniques and which do you use when?
* How would you approach fixing browser-specific styling issues?
* How do you serve your pages for feature-constrained browsers?
  * What techniques/processes do you use?
* What are the different ways to visually hide content (and make it available only for screen readers)?
* Have you ever used a grid system, and if so, what do you prefer?
* Have you used or implemented media queries or mobile specific layouts/CSS?
* Are you familiar with styling SVG?
* How do you optimize your webpages for print?
* What are some of the "gotchas" for writing efficient CSS?
* What are the advantages/disadvantages of using CSS preprocessors?
  * Describe what you like and dislike about the CSS preprocessors you have used.
* How would you implement a web design comp that uses non-standard fonts?
* Explain how a browser determines what elements match a CSS selector.
* Describe pseudo-elements and discuss what they are used for.
* Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
* What does ```* { box-sizing: border-box; }``` do? What are its advantages?
* List as many values for the display property that you can remember.
* What's the difference between inline and inline-block?
* What's the difference between a relative, fixed, absolute and statically positioned element?
* The 'C' in CSS stands for Cascading.  How is priority determined in assigning styles (a few examples)?  How can you use this system to your advantage?
* What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
* Have you played around with the new CSS Flexbox or Grid specs?
* How is responsive design different from adaptive design?
* Have you ever worked with retina graphics? If so, when and what techniques did you use?
* Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?

# JS Questions:

## Explain event delegation
##### Definitions
**Event** is an action or occurrence detected by a program. Events can be user actions, such as clicking a mouse button or pressing a key, or system occurrences, such as running out of memory.

**Event Propagation** is the process of calling all the listeners for the given event type, attached to the nodes on the branch. Each listener will be called with an event object that gathers information relevant to the event.

The propagation is bidirectional, from the window to the event target and back. This propagation can be divided into three phases:
1. From the window to the event target parent: this is the capture phase
2. The event target itself: this is the target phase
3. From the event target parent back to the window: the bubble phase

![Event Propagation](https://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2017/05/1495534508eventflow.svg)

Capturing and bubbling allow to implement one of most powerful event handling patterns called **Event Delegation**.

The idea is that if we have a lot of elements handled in a similar way, then instead of assigning a handler to each of them – we put a single handler on their common ancestor.

In the handler we get ```event.target```, see where the event actually happened and handle it.

##### The algorithm
1. Put a single handler on the container.
2. In the handler – check the source element event.target.
3. If the event happened inside an element that interests us, then handle the event.
##### Benefits
1. Simplifies initialization and saves memory: no need to add many handlers.
2. Less code: when adding or removing elements, no need to add/remove handlers.
3. DOM modifications: we can mass add/remove elements with innerHTML and alike.
##### The delegation has its limitations of course
1. First, the event must be bubbling. Some events do not bubble. Also, low-level handlers should not use ```event.stopPropagation()```.
2. Second, the delegation may add CPU load, because the container-level handler reacts on events in any place of the container, no matter if they interest us or not. But usually the load is negligible, so we don’t take it into account.

Source: https://www.sitepoint.com/event-bubbling-javascript/ 

Source: https://javascript.info/event-delegation

## Explain how `this` works in JavaScript

**this** is the current execution context of a function. The language has 4 function invocation types:
1. function invocation: ```alert('Hello World!')```

_**this** is the **global object** in a function invocation_

if 'use strct'

_**this** is the **undefined** in a function invocation_

2. method invocation: ```console.log('Hello World!')```

_**this** is the **object that owns the method** in a method invocation_

3. constructor invocation: ```new RegExp('\\d')```

_**this** is the **newly created object** in a constructor invocation_\

4. indirect invocation: ```alert.call(undefined, 'Hello World!')```

_**this** is **the first argument of .call() or .apply()** in an indirect invocation_

ES6

5. this in () => {} functions

_**this** is **the enclosing context** where the arrow function is defined

Source: https://dmitripavlutin.com/gentle-explanation-of-this-in-javascript/

## Explain how prototypal inheritance works

### Definition

**What’s Prototype?**

Almost all objects in JavaScript have the prototype property. By using it and more specifically the prototype chain we can mimic inheritance. The prototype is a reference to another object and it is used whenever JS can’t find the property you’re looking for on the current object. Simply put, whenever you call a property on an object and it doesn’t exist, JavaScript will go to the prototype object and look for it there. If it finds it it will use it, if not it will go to that object’s property and look there. This can bubble up all the way to Object.prototype before returning undefined. This is the essence of the prototype chain and the behavior that sits behind JavaScript’s inheritance.

**Class Inheritance**: A class is like a blueprint — a description of the object to be created. Classes inherit from classes and create subclass relationships: hierarchical class taxonomies.

**Prototypal Inheritance**: A prototype is a working object instance. Objects inherit directly from other objects.

 There are three different kinds of prototypal OO inheritace.
 
 1. **Concatenative inheritance**: The process of inheriting features directly from one object to another by copying the source objects properties. In JavaScript, source prototypes are commonly referred to as mixins.
 
 ```javascript
 const proto = {
  hello: function hello() {
    return `Hello, my name is ${ this.name }`;
  }
};

const george = Object.assign({}, proto, {name: 'George'});

const msg = george.hello();

console.log(msg); // Hello, my name is George
 ```
 
 2. **Prototype delegation**: In JavaScript, an object may have a link to a prototype for delegation. If a property is not found on the object, the lookup is delegated to the delegate prototype, which may have a link to its own delegate prototype, and so on up the chain until you arrive at ```Object.prototype```, which is the root delegate. 
 
 ```javascript
 function A() {
  this.hello = function() {
    console.log('A new function is created in memory every time');
    console.log('an instance of A is created');
  };
}

function B() { }
B.prototype.hello = function() {
  console.log('Only one function is created and every instance');
  console.log('of B shares this one function');
};
 ```
 
 3. **Functional inheritance**: In JavaScript, any function can create an object. When that function is not a constructor (or `class`), it’s called a factory function.
 
 ```javascript
 // Base object constructor function
function base(spec) {
    var that = {}; // Create an empty object
    that.name = spec.name; // Add it a "name" property
    return that; // Return the object
}

// Construct a child object, inheriting from "base"
function child(spec) {
    var that = base(spec); // Create the object through the "base" constructor
    that.sayHello = function() { // Augment that object
        return 'Hello, I\'m ' + that.name;
    };
    return that; // Return it
}

// Usage
var object = child({ name: 'a functional object' });
result.textContent = object.sayHello();
```

Source: https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9

Source: https://hackernoon.com/understanding-javascript-prototype-and-inheritance-d55a9a23bde2

## What do you think of AMD vs CommonJS?

### CommonJS
CommonJS modules were designed with server development in mind. Naturally, the API is synchronous. In other words, modules are loaded at the moment and in the order they are required inside a source file.

**PROS**

1. Simple: a developer can grasp the concept without looking at the docs.

2. Dependency management is integrated: modules require other modules and get loaded in the needed order.

3. ```require``` can be called anywhere: modules can be loaded programmatically.

4. Circular dependencies are supported.

**CONS**

1. Synchronous API makes it not suitable for certain uses (client-side).

2. One file per module.

3. Browsers require a loader library or transpiling.

4. No constructor function for modules (Node supports this though).

5. Hard to analyze for static code analyzers.

### Asynchronous Module Definition (AMD)

"The main difference between AMD and CommonJS lies in its support for asynchronous module loading."

**PROS** 

1. Asynchronous loading (better startup times).

2. Circular dependencies are supported.

3. Compatibility for ```require``` and ```exports```.

4. Dependency management fully integrated.

5. Modules can be split in multiple files if necessary.

6. Constructor functions are supported.

7. Plugin support (custom loading steps).

**CONS**

1. Slightly more complex syntactically.

2. Loader libraries are required unless transpiled.

3. Hard to analyze for static code analyzers.

Source: https://auth0.com/blog/javascript-module-systems-showdown/

## Explain why the following doesn't work as an IIFE: `function foo(){ }();`.
### What needs to be changed to properly make it an IIFE?

Because foo isn’t being called

This is a function **definition**, it defines foo. But it’s not a function **expression** - that is, it’s not understood by the JS parser to actually call a function.

```javascript 
function foo(){
} // ok, done with that function definition
  // (silly human left off the semicolon, how embarrassing!)

(); // Are they trying to call something? What’s the function’s name?
    // PARSE ERROR
```

In order to prep the parser that we're actually dealing with a function expression we have to wrap things up in () like so:

```javascript 
(
  function foo(){
  }()
);
```

Now the parser reads this as:

```javascript
( // oh goody, we're going to call some function expressions!
  function foo(){ // here's the function definition
  }() // and here's where the function is actually called
);
```

Source: http://lucybain.com/blog/2014/immediately-invoked-function-expression/

## What's the difference between a variable that is: `null`, `undefined` or undeclared? How would you go about checking for any of these states?
  
  ### Definition
  
  **Null** means an empty or non-existent value. Null is assigned, and explicitly means nothing.
  
  **Undefined** means a variable has been declared, but the value of that variable has not yet been defined. 
  
  **null** is an assigned value. It means nothing.
  
  **undefined** means a variable has been declared but not defined yet.
  
  **null** is an object. **undefined** is of type **undefined**.
  
  **null** !== undefined but **null** == **undefined**.
  
  
  ```javascript

  typeof value === 'undefined'
  
  typeof value === 'object' && !value
  
  //or 
  
  value === null
  
  ```
  
  Source: https://codeburst.io/javascript-whats-the-difference-between-null-undefined-37793b5bfce6
  
## What is a closure, and how/why would you use one?

### Definition

A **closure** is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

Source: https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36

## Can you describe the main difference between a `forEach` loop and a `.map()` loop and why you would pick one versus the other?

The ```forEach()``` method executes a provided function once for each array element.

The ```map()``` method creates a new array with the results of calling a provided function on every element in the calling array.

Let’s take a look at another example. Say we need to produce an array that adds 1 to each value in that array:

```javascript
var nums = [
    5,
    9,
    7
];
```

**Procedural style:**

```javascript
nums.forEach(function (num, index) {
    return nums[index] = num + 1;
});
```

**Functional style:**

```javascript
var oneBetterThanNums = nums.map(function (num) {
    return num + 1;
});
```

The idea here is to avoid transforming the original array, one of the pillars of functional design is to create something new when something changes.

Source: https://ryanpcmcquen.org/javascript/2015/10/25/map-vs-foreach-vs-for.html

## What's a typical use case for anonymous functions?

Since Anonymous Functions are function expressions rather than the regular function declaration which are statements. Function expressions are more flexible. We can assign functions to variables, object properties, pass them as arguments to other functions, and even write a simple one line code enclosed in an anonymous functions.

Source: https://medium.com/@rlynjb/js-interview-question-what-s-a-typical-use-case-for-anonymous-functions-54cf547b2a0e

## How do you organize your code? (module pattern, classical inheritance?)

# TODO

Source: https://addyosmani.com/resources/essentialjsdesignpatterns/book/

## What's the difference between host objects and native objects?

**Host Objects** are objects supplied by a certain environment. They are not always the same because each environment differs and contains host objects that accommodates execution of ECMAScript. Example, browser environment supplies objects such as window. While a node.js/server environment supplies objects such as NodeList.

**Native Objects** or Built-in Objects are standard built-in objects provided by Javascript. Native objects is sometimes referred to as ‘Global Objects’ since they are objects Javascript has provided natively available for use.

Source: https://medium.com/@rlynjb/js-interview-question-what-s-the-difference-between-host-objects-and-native-objects-b395f7c5fbf1

## Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?

JavaScript has two different ways of creating functions. Function declarations have been used for a long time, but function expressions have been gradually taking over.

```javascript
function funcDeclaration() {
    return 'A function declaration';
}

var funcExpression = function () {
    return 'A function expression';
}
```

Similar to the var statement, function declarations are hoisted to the top of other code. Function expressions aren’t hoisted, which allows them to retain a copy of the local variables from the scope where they were defined.

```javascript
new constructor[([arguments])]
```

The new operator creates an instance of a user-defined object type or of one of the built-in object types that has a constructor function.

Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new
Source: https://www.sitepoint.com/function-expressions-vs-declarations/

## What's the difference between `.call` and `.apply`?

The call() method calls a function with a given this value and arguments provided individually.

```javascript
function.call(thisArg, arg1, arg2, ...)
```

The apply() method calls a function with a given this value, and arguments provided as an array

```javascript
func.apply(thisArg, [argsArray])
```

Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply
Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call

## Explain `Function.prototype.bind`.

The ```bind()``` method creates a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

```javascript
fun.bind(thisArg[, arg1[, arg2[, ...]]])
```
A simple, naive implementation of bind would be like:

```javascript
Function.prototype.bind = function(context){
    var	that = this,
        slicedArgs = Array.prototype.splice.call(arguments, 1),
        bounded = function (){
            var newArgs = slicedArgs.concat(Array.prototype.splice.call(arguments));
            return that.apply(context,newArgs);
        }
    bounded.prototype = that.prototype;
    return bounded;
};
```

Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind

## When would you use `document.write()`?

It seems that the only “approved” time to use document.write() is for third party code to be included (such as ads or Google Analytics). Since document.write() is always available (mostly) it is a good choice for third party vendors to use it to add their scripts. They don’t know what environment you're using, if jQuery is or isn’t available, or what your onload events are. And with document.write() they don’t have to.

So don’t use it yourself, unless your working for the third party.

Source: http://lucybain.com/blog/2015/js-document-write/

## What's the difference between feature detection, feature inference, and using the UA string?

These 3 are just practices of determining if a certain web technology feature exists in a user’s browser or environment. Though features may vary with not just modern web technology but with programming languages as well.

**Feature Detection**

Feature detection is just a way of determining if a feature exists in certain browsers. A good example is a modern HTML5 feature ‘Location’.

**Feature Inference**

Feature Inference is when you have determined a feature exists and assumed the next web technology feature you are implementing unto your app exists as well. Its usually bad practice to assume, so its better to explicitly specify features you want to detect and plan a fallback action.

**UA String**

UA String or User Agent String is a string text of data that each browsers send and can be access via navigator.userAgent. These “string text of data” contains information of the browser environment you are targeting.
If you open your console and run

Modernizr is a small piece of JavaScript code that automatically detects the availability of next-generation web technologies in your user’s browsers. Rather than blacklisting entire ranges of browsers based on “UA sniffing,” Modernizr uses feature detection to allow you to easily tailor your user’s experiences based on the actual capabilities of their browser.

Source: https://medium.com/@rlynjb/js-interview-question-what-s-the-difference-between-feature-detection-feature-inference-and-76d2e4956a9b

## Explain Ajax in as much detail as possible.

Simply put, AJAX is the use of JavaScript to send and receive using HTTP without reloading the page. AJAX is an acronym for asynchronous JavaScript and XML, and is used as a technique for creating client-side asynchronous web applications. It uses a host object called XMLHttpRequest to communicate to a server-side script to retrieve data formatted in either JSON, XML, HTML, or plain text. 

```javascript
 /*
    here, we are using an IIFE to wrap our code so our
    variables and closures doesn't pollute the global namespace
  */
  (function() {
    var httpRequest;

    /*
      this is an event handler,
      once user clicked on ajaxButton html element,
      it will execute the onclick function and call the
      makeRequest function with a given 'test.html' value on its parameter.
      the 'test.html' url is just a sample api url which we'll be
      making a request from a server and expect a server response.
    */
    document.getElementById("ajaxButton").onclick = function() {
      makeRequest('test.html');
    };

    /*
      MAKING AN HTTP REQUEST
    */
    function makeRequest(url) {
      /*
        as mentioned above, we need to instantiate a new class 
        of XMLHttpRequest so we can make a HTTP request to the server.
        we are assigning this class to a variable defined on our
        outer scope so its accessible throughout our IIFE scope.
      */
      httpRequest = new XMLHttpRequest();

      /*
        were doing a Feature Detection here.
        as the name implies, we are just checking if
        XMLHttpRequest host object is NOT available and
        setting an alert action to notify user if
        XMLHttpRequest is not available on their browser/environment.
      */
      if (!httpRequest) {
        alert('Giving up :( Cannot create an XMLHTTP instance');
        return false;
      }

      /*
        before sending our HTTP server request,
        we need to set a handler for our server response.
        We can do this by assigning a function to our
        XMLHttpRequest object property 'onreadystatechange'.
        Or
        We can also assign an anonymous function, so 'onreadystatechange'
        doesn't need to carry a reference to a function.
        But for organization, we will just use the former method.
      */
      httpRequest.onreadystatechange = alertContents;

      /*
        Now that we have set our request server response handler,
        we'll need to make the request.
        - 1st parameter, is the HTTP request method (GET, POST, DELETE, etc).
          There are other request methods, whichever our server supports.
          It's also good practice to define these request methods
          in capital letters as per the HTTP standard or there are browsers
          (Firefox) that may not be able to process the request.
        - 2nd parameter, is the url for the data we are requesting.
          Make sure to use the exact domain name or it will throw a 'Permission Denied' error.
          For security purpose, we cannot make a 3rd party request, if needed,
          this is a CORS issue,
          ref: https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS
        - 3rd parameter, just sets whether the request is asynchronous. This is
          optional and default is set to true.
      */
      httpRequest.open('GET', url);

      /*
        As the method name implies, this HTTP request object method opens/sends the request.
        If we are simply doing a 'GET' request, we can leave the parameter empty, but
        if we are 'POST'ing data, we can pass in a value formatted in either
        query string, JSON, SOAP, etc.
      */
      httpRequest.send();

      /*
        NOTE:
        If we want to POST data, we may need to set the MIME type of the request.
        Ex: httpRequest.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
      */
    }

    /*
      HANDLING THE SERVER RESPONSE
    */
    /*
      this is the same function declaration we've assigned to 
      'onreadystatechange' object property above.
    */
    function alertContents() {
      /*
        this if statement checks for the state of the request.
        if the 'readyState' has a value of XMLHttpRequest.DONE (evaluating to 4),
        it means the server response has been received and its OK for us to continue processing.
        ref: https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#Properties
      */
      if (httpRequest.readyState === XMLHttpRequest.DONE) {
        /*
          Next, we'll check for HTTP Status Code. Most common HTTP Status Codes I've
          encountered are 200 OK, 403 Forbidden Error, and 500 Server Error.
          There is a list of HTTP Status Code available online with description of code.
          This if statement is just checking for which HTTP Status Code to respond to and
          execute code for whatever we want to do with the data.
        */
        if (httpRequest.status === 200) {
          alert(httpRequest.responseText);
        } else {
          alert('There was a problem with the request.');
        }

        /*
          There are 2 options to access data: httpRequest.responseText and httpRequest.responseXML
          Step above is only valid if asynchronous is set to true, if not, we don't need to specify
          a function.
        */
      }
    }
  })();
```

Source: http://rlynjb.github.io/wandrr/JS-Interview-Question-Explain-AJAX-in-as-much-detail-as-possible
Source: https://medium.com/@morgan_ashley/front-end-developer-interview-question-03-4b8c94a42442

## What are the advantages and disadvantages of using Ajax?

**PROS**

* Improved user experience
* Asynchronous processing
* Reduced server hits and network load
* Platform and architecture neutrality
* Multibrowser support
* Faster page renders and improved response times

**CONS**

* Because the updates are done by JavaScript on the client, the state will not register in the browsers history, making it impossible to use the Back and Forward buttons to navigate between various states of the page.
* For the same reason, a specific state can't be bookmarked by the user.
* Data loaded through AJAX won't be indexed by any of the major search engines.
* People using browsers without JavaScript support, or with JavaScript disabled, will not be able to use the functionality that you provide through AJAX.

Source: http://www.informit.com/articles/article.aspx?p=1228495&seqNum=4

Source: https://www.mindstick.com/blog/819/advantage-and-disadvantage-of-ajax

## Explain how JSONP works (and how it's not really Ajax).

JSONP stands for **J**ava**S**cript **O**ject **N**otation with **P**adding

An ajax call is an actual HTTP request from your client directly to a server. Ajax calls can be synchronous (blocking until they complete) or asynchronous. Because of same-origin security protections, ajax calls can only be made to the same server that the web page came from unless the target server explicitly allows a cross origin request using CORS.

JSONP calls are an interesting hack with the <script> tag that allows cross-origin communication. In a JSONP call, the client creates a script tag and puts a URL on it with an callback=xxxx query parameter on it. That script request (via the script tag insertion) is sent by the browser to the foreign server. The browser just thinks it's requesting some javascript code. The server then creates some special javascript for the purposes of this call and in that javascript that will get executed by the browser when it's returned, the server puts a function call to the function named in the callback=xxxx query parameter. By either defining variables of by passing data to that function, the server can communicate data back to the client. For JSONP, both client and server must cooperate on how the JSONP call works and how the data is defined. A client cannot make a JSONP call to a server that doesn't explicitly support JSONP because the exact right type of JSONP response has to be built by the server or it won't work.

So, the two communication methods work completely differently. Only ajax calls can be synchronous. By the nature of the <script> tag insertion, JSONP calls are always asynchronous.

In an Ajax call, the response comes back in a ajax event handler.

In a JSONP call, the response comes when the returned Javascript calls a function of yours.

In some ways, JSONP is a security hole that bypasses the cross-origin security mechanism. But, you can only call servers that explicitly choose to support a JSONP-like mechanism so if a server doesn't want you to be able to call it cross-origin, it can prevent it by not supporting JSONP. You can't make regular ajax calls to these other servers.

Source: http://lucybain.com/blog/2015/how-does-jsonp-work/
Source: https://stackoverflow.com/questions/10289789/i-dont-get-how-jsonp-is-any-different-from-ajax

## Have you ever used JavaScript templating? If so, what libraries have you used?
  
  1. Mustache
  2. Underscore Templates
  3. Embedded JS Templates
  4. HandlebarsJS
  5. Jade templating
  6. AngularJS tempaltes
  
  Source: http://www.creativebloq.com/web-design/templating-engines-9134396

## Explain "hoisting".

**Hoisting** is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution.

_Of note however, is the fact that the hoisting mechanism only moves the declaration. The assignments are left in place._

**Order of precedence**

1. Variable assignment takes precedence over function declaration
2. Function declarations take precedence over variable declarations

Function declarations are hoisted over variable declarations but not over variable assignments.

```javascript
var double = 22;

function double(num) {
  return (num*2);
}

console.log(typeof double); // Output: number
```

Function declarations over variable declarations

```javascript
var double;

function double(num) {
  return (num*2);
}

console.log(typeof double); // Output: function
```

Source: https://scotch.io/tutorials/understanding-hoisting-in-javascript


## What's the difference between an "attribute" and a "property"?

**Property**

JS DOM objects have properties. These properties are kind of like instance variables for the particular element. As such, a property can be different types (boolean, string, etc.).

**Attribute**

Attributes are in the HTML itself, rather than in the DOM. They are very similar to properties, but not quite as good. When a property is available it’s recommended that you work with properties rather than attributes. An attribute is only ever a string, no other type.

Source: http://lucybain.com/blog/2014/attribute-vs-property/

# Why is extending built-in JavaScript objects not a good idea?

Changing the behaviour of an object that will only be used by your own code is fine. But when you change the behaviour of something that is also used by other code there is a risk you will break that other code.

When it comes adding methods to the object and array classes in javascript, the risk of breaking something is very high, due to how javascript works. Long years of experience have taught me that this kind of stuff causes all kinds of terrible bugs in javascript.

Source: http://lucybain.com/blog/2014/js-extending-built-in-objects/

## Difference between document load event and document DOMContentLoaded event?

The DOMContentLoaded event is fired when the document has been completely loaded and parsed, without waiting for stylesheets, images, and subframes to finish loading (the load event can be used to detect a fully-loaded page).

Source: https://stackoverflow.com/questions/2414750/difference-between-domcontentloaded-and-load-events

## What is the difference between `==` and `===`?

```===``` checks for type and equality.

```==``` only checks for equality.

_If the two operands are not of the same type, JavaScript converts the operands then applies strict comparison. If either operand is a number or a boolean, the operands are converted to numbers if possible; else if either operand is a string, the other operand is converted to a string if possible. If both operands are objects, then JavaScript compares internal references which are equal when operands refer to the same object in memory._


Source: http://lucybain.com/blog/2014/triple-vs-double-equals/

## Explain the same-origin policy with regards to JavaScript.

The “origin” is the same if three things are the same: the protocol (http vs. https), the domain (subdomain.yoursite.com vs. yoursite.com vs. google.com), and the port (:80 vs. :4567). If all three of these line up, then JS views the sites as the same, and code is executed. If any of them are different then the code is marked as potentially malicious and is not run.

Internet Explorer has two major exceptions when it comes to same origin policy

* Trust Zones: if both domains are in highly trusted zone e.g, corporate domains, then the same origin limitations are not applied 
* Port: IE doesn't include port into Same Origin components, therefore http://company.com:81/index.html and http://company.com/index.html are considered from same origin and no restrictions are applied.\

These exceptions are non-standard and not supported in any other browser but would be helpful if developing an app for Windows RT (or) IE based web application.

The same-origin policy helps prevent malicious attacks by stopping code from another site executing on your site. An attacks like this is known as a Cross Site Scripting attack.

Source: http://lucybain.com/blog/2014/same-origin-policy/

Source: https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy#Changing_origin

## Make this work:

```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
easy

```javascript
function duplicate(array) {
   return array.concat(array)
}; // [1,2,3,4,5,1,2,3,4,5]
```

## Why is it called a Ternary expression, what does the word "Ternary" indicate?

A **un**ary operand accepts one parameter, e.g. -1, where - is the operand, and 1 is the parameter.

A **bin**ary operand accepts two parameters, e.g. 2 + 3, where + is the operand, and 2 and 3 are the parameters.

So a **tern**ary operand accepts three parameters.

In programming the ternary operand we use is a rewrite of an if statement. Before we write an actual ternary, we'll just take a quick look at an if statement:

```javascript
if(conditional) { // one
    truethy_block // two
} else {
    falsey_block // three
}
```

You can see there are three sections to an if statement. Let’s write them as a property ternary expression:

```javascript
conditional ? truethy_block : falsey_block
```

Source: http://lucybain.com/blog/2014/js-ternary/

## What is `"use strict";`? what are the advantages and disadvantages to using it?

If you put "use strict"; at the top of your code (or function), then the JS is evaluated in strict mode. Strict mode throws more errors and disables some features in an effort to make your code more robust, readable, and accurate.

Strict mode helps out in a couple ways:

* It catches some common coding bloopers, throwing exceptions.
* It prevents, or throws errors, when relatively “unsafe” actions are taken (such as gaining access to the global object).
* It disables features that are confusing or poorly thought out.

Source: http://lucybain.com/blog/2014/js-use-strict/

## Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`

```javascript
for(var i =0; i < 100; i++) {
	var statement1 = (i % 3 === 0) ? 'fizz' : ''
  var statement2 = (i % 5 === 0) ? 'buzz' : ''
 	
  console.log(i, statement1 + statement2)
}
```

Source: https://stackoverflow.com/questions/13845437/from-1-to-100-print-ping-if-multiple-of-3-pong-if-multiple-of-5-or-else-p

## Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?

* It’s harder to read the code and reason about it when variables seem to appear out of thin air (but really from the global scope).
* Anyone can update a global variable from any point in the program at any time (and from any thread if there’s more than one going).
* General code smell - if you're too lazy to put the variable only where it needs to be then what other corners are you cutting?
* It’s probable that you'll encounter global variable name clashes. Since there’s only one namespace you're more likely to double up on a variable name.

Source: http://lucybain.com/blog/2014/js-dont-touch-global-scope/

# Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?

The load event fires at the end of the document loading process. At this point, all of the objects in the document are in the DOM, and all the images, scripts, links and sub-frames have finished loading. To execute anything post document load, we fire these events. ‘DOMContentLoaded’ or jQuery’s loaded are another options. 

Source: https://medium.com/@nupoor_neha/javascript-front-end-interview-questions-1cbc5e32792b

# Explain what a single page app is and how to make one SEO-friendly.

Source: https://www.codeschool.com/beginners-guide-to-web-development/single-page-applications

* What is the extent of your experience with Promises and/or their polyfills?
* What are the pros and cons of using Promises instead of callbacks?
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?
* What language constructions do you use for iterating over object properties and array items?
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript?
  * What are the pros and cons of immutability?
  * How can you achieve immutability in your own code?
* Explain the difference between synchronous and asynchronous functions.
* What is event loop?
  * What is the difference between call stack and task queue?
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
* What are the differences between variables created using `let`, `var` or `const`?

#### Testing Questions:

* What are some advantages/disadvantages to testing your code?
* What tools would you use to test your code's functionality?
* What is the difference between a unit test and a functional/integration test?
* What is the purpose of a code style linting tool?

#### Performance Questions:

* What tools would you use to find a performance bug in your code?
* What are some ways you may improve your website's scrolling performance?
* Explain the difference between layout, painting and compositing.

#### Network Questions:

* Traditionally, why has it been better to serve site assets from multiple domains?
* Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.
* What are the differences between Long-Polling, Websockets and Server-Sent Events?
* Explain the following request and response headers:
  * Diff. between Expires, Date, Age and If-Modified-...
  * Do Not Track
  * Cache-Control
  * Transfer-Encoding
  * ETag
  * X-Frame-Options
* What are HTTP methods? List all HTTP methods that you know, and explain them.

#### Coding Questions:

*Question: What is the value of `foo`?*
```javascript
var foo = 10 + '20';
```

*Question: What will be the output of the code below?*
```javascript
console.log(0.1 + 0.2 == 0.3);
```

*Question: How would you make this work?*
```javascript
add(2, 5); // 7
add(2)(5); // 7
```

*Question: What value is returned from the following statement?*
```javascript
"i'm a lasagna hog".split("").reverse().join("");
```

*Question: What is the value of `window.foo`?*
```javascript
( window.foo || ( window.foo = "bar" ) );
```

*Question: What is the outcome of the two alerts below?*
```javascript
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```

*Question: What is the value of `foo.length`?*
```javascript
var foo = [];
foo.push(1);
foo.push(2);
```

*Question: What is the value of `foo.x`?*
```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```

*Question: What does the following code print?*
```javascript
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
console.log('three');
```

*Question: What is the difference between these four promises?*
```javascript
doSomething().then(function () {
  return doSomethingElse();
});

doSomething().then(function () {
  doSomethingElse();
});

doSomething().then(doSomethingElse());

doSomething().then(doSomethingElse);
```


#### Fun Questions:

* What's a cool project that you've recently worked on?
* What are some things you like about the developer tools you use?
* Who inspires you in the front-end community?
* Do you have any pet projects? What kind?
* What's your favorite feature of Internet Explorer?
* How do you like your coffee?


#### Contributors:

This document started in 2009 as a collaboration of [@paul_irish](https://twitter.com/paul_irish) [@bentruyman](https://twitter.com/bentruyman) [@cowboy](https://twitter.com/cowboy) [@ajpiano](https://twitter.com/ajpiano)  [@SlexAxton](https://twitter.com/slexaxton) [@boazsender](https://twitter.com/boazsender) [@miketaylr](https://twitter.com/miketaylr) [@vladikoff](https://twitter.com/vladikoff) [@gf3](https://twitter.com/gf3) [@jon_neal](https://twitter.com/jon_neal) [@sambreed](https://twitter.com/sambreed) and [@iansym](https://twitter.com/iansym).

It has since received contributions from over [100 developers](https://github.com/h5bp/Front-end-Developer-Interview-Questions/graphs/contributors).
