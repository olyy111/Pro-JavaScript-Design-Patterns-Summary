```javascript
/* FrameColorDecorator class. */
var FrameColorDecorator = function(bicycle, frameColor) {
  // implements Bicycle
  this.superclass.constructor(bicycle); // Call the superclass's constructor.
  this.frameColor = frameColor;
};
extend(FrameColorDecorator, BicycleDecorator); // Extend the superclass.
FrameColorDecorator.prototype.assemble = function() {
  return (
    "Paint the frame " +
    this.frameColor +
    " and allow it to dry. " +
    this.bicycle.assemble()
  );
};
FrameColorDecorator.prototype.getPrice = function() {
  return this.bicycle.getPrice() + 30.0;
};
```
