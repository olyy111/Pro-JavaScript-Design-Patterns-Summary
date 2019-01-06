
### illustration
Adding additional manufacturers is easy; simply create another subclass of BicycleShop
and override the createBicycle factory method. You can also modify each subclass to allow for
additional models specific to a certain manufacturer. **This is the most important feature of the
factory pattern**. You can write all of your general Bicycle code in the parent class, BicycleShop,
and then defer the actual instantiation of specific Bicycle objects to the subclasses. **The general
code is all in one place, and the code that varies is encapsulated in the subclasses**.
```javascript
/* BicycleShop class (abstract). */

var BicycleShop = function() {};
BicycleShop.prototype = {
  sellBicycle: function(model) {
    var bicycle = this.createBicycle(model);
    
    bicycle.assemble();
    bicycle.wash();
    
    return bicycle;
  },
  createBicycle: function(model) {
    throw new Error('Unsupported operation on an abstract class.');
  }
};

/* AcmeBicycleShop class. */

var AcmeBicycleShop = function() {};
extend(AcmeBicycleShop, BicycleShop);
AcmeBicycleShop.prototype.createBicycle = function(model) {
  var bicycle;

  switch(model) {
    case 'The Speedster':
      bicycle = new AcmeSpeedster();
      break;
    case 'The Lowrider':
      bicycle = new AcmeLowrider();
      break;
    case 'The Flatlander':
      bicycle = new AcmeFlatlander();
      break;
    case 'The Comfort Cruiser':
    default:
      bicycle = new AcmeComfortCruiser();
  }

  Interface.ensureImplements(bicycle, Bicycle);
  return bicycle;  
};

/* GeneralProductsBicycleShop class. */

var GeneralProductsBicycleShop = function() {};
extend(GeneralProductsBicycleShop, BicycleShop);
GeneralProductsBicycleShop.prototype.createBicycle = function(model) {
  var bicycle;

  switch(model) {
    case 'The Speedster':
      bicycle = new GeneralProductsSpeedster();
      break;
    case 'The Lowrider':
      bicycle = new GeneralProductsLowrider();
      break;
    case 'The Flatlander':
      bicycle = new GeneralProductsFlatlander();
      break;
    case 'The Comfort Cruiser':
    default:
      bicycle = new GeneralProductsComfortCruiser();
  }

  Interface.ensureImplements(bicycle, Bicycle);
  return bicycle;
};


/* Usage. */

var alecsCruisers = new AcmeBicycleShop();
var yourNewBike = alecsCruisers.sellBicycle('The Lowrider');

var bobsCruisers = new GeneralProductsBicycleShop();
var yourSecondNewBike = bobsCruisers.sellBicycle('The Lowrider');
```