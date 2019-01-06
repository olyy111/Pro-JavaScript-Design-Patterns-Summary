
## Technique Memoizing
in eg3 The factory method createXhrObject returns an XHR object based on what is available in
the current environment. The first time it is run, it will test three different ways of creating an XHR
object, and when it finds one that works, it will return the object created and **overwrite itself**
with the function used to create the object. This new function becomes the createXhrObject
method. This technique, called **memoizing**, can be used to create functions and methods that
store complex calculations so that they don’t have to be repeated. All of the complex setup code
is only called once, the first time the method is executed, and after that only the browser-specific
code is executed.

Let's look at the implementation
```javascript
createXhrObject: function() {
    var methods = [
      function() { return new XMLHttpRequest(); },
      function() { return new ActiveXObject('Msxml2.XMLHTTP'); },
      function() { return new ActiveXObject('Microsoft.XMLHTTP'); }
    ];
    
    for(var i = 0, len = methods.length; i < len; i++) {
      try {
        methods[i]();
      }
      catch(e) {
        continue;
      // i.e. select the corrent method and return a created obj to overwrite it.     
      this.createXhrObject = methods[i]; 
      return methods[i];
    }
    throw new Error('SimpleHandler: Could not create an XHR object.');
  } 
  ```

