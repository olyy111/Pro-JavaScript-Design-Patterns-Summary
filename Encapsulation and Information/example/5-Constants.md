```javascript
var Class = (function () {
  // Private static attributes.
  var constants = {
    UPPER_BOUND: 100,
    LOWER_BOUND: -100
  }
  // Privileged static method.
  this.getConstant(name) {
    return constants[name];
  }
  //...
  // Return the constructor.
  return function (constructorArgument) {
  ...
  }
  }) ();
Class.getConstant('UPPER_BOUND');
```