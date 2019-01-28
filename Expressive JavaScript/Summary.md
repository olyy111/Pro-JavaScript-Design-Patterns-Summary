## 1. The Flexibility of JavaScript
One of the most powerful features of the language is its **flexibility**. As a JavaScript programmer,
you can make your programs as simple or as complex as you wish them to be. The language
also allows several different programming styles. You can write your code in the **functional style**
or in the slightly more complex **object-oriented style**.
It also lets you write relatively complex
programs **without knowing anything** at all about functional or object-oriented programming;
you can be productive in this language just by writing simple functions. This may be one of the
reasons that some people see JavaScript as a toy, but we see it as a good thing. It allows programmers
to accomplish useful tasks with **a very small, easy-to-learn** subset of the language. It also
means that JavaScript scales up as you become a more advanced programmer.

## 2. A Loosely Typed Language
## 3. Functions As First-Class Objects
Functions can:
- can be stored in variables,
- passed into other functions as arguments, 
- passed out of functions as return values
- and constructed at run-time
- You can create anonymous functions, which are functions created using the `function()
{ ... }` syntax. They are not given names, but they can be assigned to variables.
    - The most interesting use of the anonymous function is to create a closure. A closure is
a protected variable space, created by using nested functions.
- JavaScript is
also **lexically scoped**, which means that functions run in the scope they are defined in, not the
scope they are **executed in**.

## 3. The Mutability of Objects
- giving attributes to functions
```javascript
function displayError(message) {
  displayError.numTimesExecuted++;
  alert(message);
};
displayError.numTimesExecuted = 0;
```
- It also means you can modify classes after they have been defined and objects after they
have been instantiated:
```javascript
/* Class Person. */
function Person(name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype = {
  getName: function () {
    return this.name;
  },
  getAge: function () {
    return this.age;
  }
}
/* Instantiate the class. */
var alice = new Person('Alice', 93);
var bill = new Person('Bill', 30);
/* Modify the class. */
Person.prototype.getGreeting = function () {
  return 'Hi ' + this.getName() + '!';
};
/* Modify a specific instance. */
alice.displayGreeting = function () {
  alert(this.getGreeting());
}
```

- You can examine any object at
run-time to see what attributes and methods it contains. You can also use this information to
instantiate classes and **execute methods dynamically, without knowing their names at development
time** (this is known as reflection). These are important techniques for dynamic scripting
and are features that static languages (such as C++) lack.
- In JavaScript, **everything can be modified at run-time**
- 
## Inheritance
JavaScript
uses **object-based(prototypal)** inheritance; this can be used to emulate **class-based (classical)**
inheritance.

## Design Patterns in JavaScript
There are three main reasons why you would want to use design
patterns in JavaScript:
1. Maintainability: Design patterns help to keep your modules more **loosely coupled**.
2. Communication: Design patterns provide a **common vocabulary** for dealing with different types of objects.
3. Performance: Some of the patterns we cover in this book are **optimization patterns**. The flyweight (Chapter 13) and proxy (Chapter 14) patterns are the most important examples of this.

There are two reasons why you might not want to use design patterns:
1. Complexity: Maintainability often comes at a **cost**, and that cost is that your code may be more complex and less likely to be understood by novice programmers.
2. Performance: While some patterns improve performance, most of them add a slight performance overhead to your code. Depending on the specific demands of your project, **this overhead may range from unnoticeable to completely unacceptable**.

Implementing patterns is the easy part; knowing which one to use (and when) is the hard part. Applying design patterns to your code **without knowing the specific reasons for doing so can be dangerous**. Make an effort to ensure that the pattern you select is the most appropriate
and won’t degrade performance below **acceptable limits**.