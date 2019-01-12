```javascript
/* BellDecorator class. ringBell is new */
var BellDecorator = function(bicycle) {
  // implements Bicycle
  this.superclass.constructor(bicycle); // Call the superclass's constructor.
};
extend(BellDecorator, BicycleDecorator); // Extend the superclass.
BellDecorator.prototype.assemble = function() {
  return this.bicycle.assemble() + " Attach bell to handlebars.";
};
BellDecorator.prototype.getPrice = function() {
  return this.bicycle.getPrice() + 6.0;
};
BellDecorator.prototype.ringBell = function() {
  return "Bell rung.";
};

var myBicycle = new AcmeComfortCruiser(); // Instantiate the bicycle.
myBicycle = new BellDecorator(myBicycle); // Decorate the bicycle object
// with a bell.
alert(myBicycle.ringBell()); // Returns 'Bell rung.'

// If you were to add a headlight after adding a bell,
// the new method would be effectively masked by the HeadlightDecorator:
var myBicycle = new AcmeComfortCruiser(); // Instantiate the bicycle.
myBicycle = new BellDecorator(myBicycle); // Decorate the bicycle object
// with a bell.
myBicycle = new HeadlightDecorator(myBicycle); // Decorate the bicycle object
// with a headlight.
alert(myBicycle.ringBell()); // Method not found.

/* The BicycleDecorator abstract decorator class, improved. */
var BicycleDecorator = function(bicycle) {
  // implements Bicycle
  this.bicycle = bicycle;
  this.interface = Bicycle;
  // Loop through all of the attributes of this.bicycle and create pass-through
  // methods for any methods that aren't currently implemented.
  outerloop: for (var key in this.bicycle) {
    // Ensure that the property is a function.
    if (typeof this.bicycle[key] !== "function") {
      continue outerloop;
    }
    // Ensure that the method isn't in the interface.
    for (var i = 0, len = this.interface.methods.length; i < len; i++) {
      if (key === this.interface.methods[i]) {
        continue outerloop;
      }
    }
    // Add the new method.
    var that = this;
    (function(methodName) {
      that[methodName] = function() {
        return that.bicycle[methodName]();
      };
    })(key);
  }
};
BicycleDecorator.prototype = {
  assemble: function() {
    return this.bicycle.assemble();
  },
  wash: function() {
    return this.bicycle.wash();
  },
  ride: function() {
    return this.bicycle.ride();
  },
  repair: function() {
    return this.bicycle.repair();
  },
  getPrice: function() {
    return this.bicycle.getPrice();
  }
};
```