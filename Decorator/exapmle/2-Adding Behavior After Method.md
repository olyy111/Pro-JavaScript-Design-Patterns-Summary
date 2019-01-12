```javascript
var myBicycle = new AcmeComfortCruiser(); // Instantiate the bicycle.
myBicycle = new FrameColorDecorator(myBicycle, "red"); // Decorate the bicycle
// object with the frame color.
myBicycle = new HeadlightDecorator(myBicycle); // Decorate the bicycle object
// with the first headlight.
myBicycle = new HeadlightDecorator(myBicycle); // Decorate the bicycle object
// with the second headlight.
myBicycle = new TaillightDecorator(myBicycle); // Decorate the bicycle object
// with a taillight.
alert(myBicycle.assemble());
/* Returns:
"Paint the frame red and allow it to dry. (Full instructions for assembling
the bike itself go here) Attach headlight to handlebars. Attach headlight
to handlebars. Attach taillight to the seat post."
*/
```
