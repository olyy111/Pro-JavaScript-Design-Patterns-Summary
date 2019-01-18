```javascript
// example using listeners
var element = $('example');
var fn1 = function (e) {
  // handle click
};
var fn2 = function (e) {
  // do other stuff with click
};
addEvent(element, 'click', fn1);
addEvent(element, 'click', fn2);
However, it’s not possible using event handlers, as shown below:
// example using handlers
var element = document.getElementById('b');
var fn1 = function (e) {
  // handle click
};
var fn2 = function (e) {
  // do other stuff with click
};
element.onclick = fn1;
element.onclick = fn2;
```