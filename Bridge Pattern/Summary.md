## Summary
a bridge should “**decouple an abstraction from its implementation so that the two can
vary independently.**” Bridges are very beneficial when it comes to event-driven programming,
which is a style that is used often in JavaScript. 

It's a basic coding skill in javascript
## When Should the Bridge Pattern Be Used?
It’s usually simple to diagnose where a bridge
should be included. Say, for instance, that your code looks like the following:
```javascript
$('example').onclick = function() {
new RichTextEditor();
};
```
Nowhere does this tell you where the editor is going to show up, what the configuration
options are, or how to modify it. The key here is to make your interfaces **“bridgeable”** and in
fact, adaptable (as you will learn in Chapter 11).


In real life, this is critical to the construction of cities and the integration of roads within
them. Neighborhoods are equivalent to modules, and roads are like the methods that connect
them. **The usability of a road often affects the population of that region**. Likewise, the interface
you offer clients will most likely affect its popularity.

### 1. decouple the implementation from event handler method.

> eg1...

### 2. use privileged methods 
You can use privileged methods as a bridge to
gain access to the private variable space without venturing into the dirty waters of the implementation
```javascript
var Public = function() {
  var secret = 3;
  // this is a bridge
  this.privilegedGetter = function() {
    return secret;
  };
};

var o = new Public;
var data = o.privilegedGetter();
```

### 3. Bridging Multiple Classes Together
a bridge can also serve as the link between
public API code and private implementation code, Furthermore, you can use bridges as a way
to connect multiple classes together.
Just as bridges in real life connect multiple things together, they can do the same for JavaScript
classes:
```javascript
var Class1 = function(a, b, c) {
  this.a = a;
  this.b = b;
  this.c = c;
}
var Class2 = function(d) {
  this.d = d;
};

var BridgeClass = function(a, b, c, d) {
  this.one = new Class1(a, b, c);
  this.two = new Class2(d);
};

```

## Benefits of the Bridge Pattern
Implementing the bridge pattern into your software design repertoire helps not only you but
those who have to maintain your work. **Decoupling abstractions from their implementations
allows pieces to be independently managed**, Bugs are easier to locate, and software is less
likely to be seriously broken. Bridges should essentially be the glue to every abstraction.

## Drawbacks of the Bridge Pattern
- Each bridge used
adds another function call, which can negatively affect the performance of your application.
- They also add complexity, which can make your code harder to debug if a problem does arise.

## don’t overuse them
For
example, if you have a bridge that connects two functions, but the functions are never called
in any place other than the bridge, the bridge isn’t strictly needed and can be safely removed.