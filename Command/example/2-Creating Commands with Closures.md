```javascript
/* Commands using closures. */
function makeStart(adObject) {
  return function () {
    adObject.start();
  };
}
function makeStop(adObject) {
  return function () {
    adObject.stop();
  };
}
/* Implementation code. */
var startCommand = makeStart(ads[0]);
var stopCommand = makeStop(ads[0]);
startCommand(); // Execute the functions directly instead of calling a method.
stopCommand();
```