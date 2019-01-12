```javascript
/* LifetimeWarrantyDecorator class. */
var LifetimeWarrantyDecorator = function(bicycle) {
  // implements Bicycle
  this.superclass.constructor(bicycle); // Call the superclass's constructor.
};
extend(LifetimeWarrantyDecorator, BicycleDecorator); // Extend the superclass.
LifetimeWarrantyDecorator.prototype.repair = function() {
  return (
    "This bicycle is covered by a lifetime warranty. Please take it to " +
    "an authorized Acme Repair Center."
  );
};
LifetimeWarrantyDecorator.prototype.getPrice = function() {
  return this.bicycle.getPrice() + 199.0;
};

/* TimedWarrantyDecorator class. */
var TimedWarrantyDecorator = function(bicycle, coverageLengthInYears) {
  // implements Bicycle
  this.superclass.constructor(bicycle); // Call the superclass's constructor.
  this.coverageLength = coverageLengthInYears;
  this.expDate = new Date();
  var coverageLengthInMs = this.coverageLength * 365 * 24 * 60 * 60 * 1000;
  expDate.setTime(expDate.getTime() + coverageLengthInMs);
};
extend(TimedWarrantyDecorator, BicycleDecorator); // Extend the superclass.
TimedWarrantyDecorator.prototype.repair = function() {
  var repairInstructions;
  var currentDate = new Date();
  if (currentDate < expDate) {
    repairInstructions =
      "This bicycle is currently covered by a warranty. " +
      "Please take it to an authorized Acme Repair Center.";
  } else {

    // notice here you expect call the component's method, if any other decorator
    // had modify the bicyle object, you can't control the repair behavior, beacuse
    // it dependent the unmodified method
    repairInstructions = this.bicycle.repair();
  }
  return repairInstructions;
};
TimedWarrantyDecorator.prototype.getPrice = function() {
  return this.bicycle.getPrice() + 40.0 * this.coverageLength;
};
```