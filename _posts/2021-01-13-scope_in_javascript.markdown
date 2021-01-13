---
layout: post
title:      "Scope in JavaScript "
date:       2021-01-13 14:53:44 +0000
permalink:  scope_in_javascript
---


If you are a beginner in JavaScript, it is really important to understand the concept of scope. It will save you a lot of time and hours of debugging. 

Imagine you are chatting with two friends, A and B on Facebook. Whatever texts you send to A, B does not have access to that messages. Same goes for A. But if you create a group then everyone can see or have access to all the messages. This is because these chat windows have their own audiences or scopes. The same principal of scope exists in JS. Whether you will have access to a variable from a particular position in your code depends on the scope. Scope is created by functions and code blocks. 

There are three types of scope in JavaScript … well, unless you define variables with the keyword ‘var’. We will get into this in a second. Before that let’s see an example of these different scopes.

```
let globalScope= "I am on the global scope"

function testScope(){
    let functionalScope= "I am on the functional scope"
        {
          let blockScope= "But me on the block scope! "
        }
}
```

Here, every variable declared outside the function testScope has global scope. And any variable declared inside the function testScope has a functional scope but if any variable is declared inside curly braces then it has its own scope which is called block scope. But what are meant by these scopes and who has access to whom. Let’s see!

First, we’ll see who has access to global scope. With JavaScript, the global scope is the complete JavaScript environment. In HTML, the global scope is the window object.

```
let globalScope= "I am on the global scope";

function testScope(){
    let functionalScope= "I am on the functional scope";
    console.log(globalScope)
        {
          let blockScope= "But me on the block scope! ";
          console.log(globalScope)
        }
}
console.log(globalScope)
testScope()
```

This will console log:

```
I am on the global scope
I am on the global scope
I am on the global scope
```

This means we can access global variable from any scope. You can think of global scope as the group chat! Everyone has access to the messages!

In case of functional scope, we’ll only have access to functional scoped variable only if we are inside the function. Here is an example:

```
function testScope(){
    let functionalScope= "I am on the functional scope";
    console.log(functionalScope) 
        // this will log "I am on the functional scope"
        {
          let blockScope= "But me on the block scope! "
          console.log(functionalScope)
            // this will log "I am on the functional scope"
        }
}

testScope();
```

Even if we have nested scopes inside a function, we’ll still have access to the functional scoped variable.

```
function testScope(){
    let functionalScope= "I am on the functional scope";
    // console.log(functionalScope) 
        // this will log "I am on the functional scope"
        function innerFuntion(){
            
            function innerMostFunction(){
                console.log(functionalScope)
                    // this will log "I am on the functional scope"
            }
            
            innerMostFunction();
        }
    
    innerFuntion();
        // this will call innerFuntion, which calls the innerMostFuntion hence logs "I am on the functional scope"
}

testScope();
```

At this point, we should have a clear idea of what global and functional scopes are! If not, take a pause and read the code snippets again!

Now, let’s talk about block scope. ES2015 introduced two important new JavaScript keywords: let and const. If you don’t have any idea about versions in JavaScript, you can read [this](https://www.w3schools.com/js/js_versions.asp).

These two keywords introduced block scoped variables in JavaScript. Anything written inside a block {} (curly braces) are block scoped. 

```
{ 
    let x = "block scoped"
}
console.log(x)

// ReferenceError: x is not defined
```

BUT variables declared with keyword ‘var’ are not block scoped. So, 

```
{ 
    var x = "block scoped"
}
console.log(x)

// logs "block scoped"
```

If you are interested in learning more about the differences between ‘var’, ‘let’ and ‘const’ you can read [this](https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/) article.

Now that we have a clear understanding about all the scopes, let’s see an example with nested scopes.

```
function testScope(){
    let functionalScope= "I am on the functional scope";
        function innerFunction(){
            let innerScope = "I am on the inner scope"
            function innerMostFunction(){
                let innerMostScope = "I am on the inner most scope"
                console.log(innerScope)
                    // logs innerScope variable
                console.log(functionalScope) 
                    // logs functionalScope variable
            }
            innerMostFunction();
            console.log(innerMostScope)
                // ReferenceError: innerMostScope is not defined
        }
    innerFunction();
}

testScope();
```

Here, innerMostFunction() has access to all the variables of its outer scopes. But innerFunction() can’t access its inner scope variables. 

To sum up the idea of scoping, we can say:

*•	Global scoped variables can be accessed from anywhere in the code base.

•	Block scopes variables are only accessible within the block.

•	The variables of the outer scope are accessible inside the inner scope.*

