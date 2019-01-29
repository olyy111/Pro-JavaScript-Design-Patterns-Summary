```javascript
/* Class Person. */
function Person(name) {
  this.name = name;
}
Person.prototype.getName = function () {
  return this.name;
}

/* Class Author. */
function Author(name, books) {
  Person.call(this, name); // Call the superclass's constructor in the scope of this.
  this.books = books; // Add an attribute to Author.
}
Author.prototype = new Person(); // Set up the prototype chain.
Author.prototype.constructor = Author; // Set the constructor attribute to Author.
Author.prototype.getBooks = function () { // Add a method to Author.
  return this.books;
};

var author = [];
author[0] = new Author('Dustin Diaz', ['JavaScript Design Patterns']);
author[1] = new Author('Ross Harmes', ['JavaScript Design Patterns']);
author[1].getName();
author[1].getBooks();

/* Extend function. */
function extend(subClass, superClass) {
  var F = function () { };
  F.prototype = superClass.prototype;
  subClass.prototype = new F();
  subClass.prototype.constructor = subClass;
}

/* Class Person. */
function Person(name) {
  this.name = name;
}
Person.prototype.getName = function () {
  return this.name;
}
/* Class Author. */
function Author(name, books) {
  Person.call(this, name);
  this.books = books;
}
extend(Author, Person);
Author.prototype.getBooks = function () {
  return this.books;
};

/* Extend function, improved. */
function extend(subClass, superClass) {
  var F = function () { };
  F.prototype = superClass.prototype;
  subClass.prototype = new F();
  subClass.prototype.constructor = subClass;
  subClass.superclass = superClass.prototype;
  if (superClass.prototype.constructor == Object.prototype.constructor) {
    superClass.prototype.constructor = superClass;
  }
}

/* Class Author. */
function Author(name, books) {
  Author.superclass.constructor.call(this, name);
  this.books = books;
}
extend(Author, Person);
Author.prototype.getBooks = function () {
  return this.books;
};

Author.prototype.getName = function () {
  var name = Author.superclass.getName.call(this);
  return name + ', Author of ' + this.getBooks().join(', ');
};
```

the encapsulation of extend is the key:
```javascript
/* Extend function, improved. */
function extend(subClass, superClass) {
  var F = function () { };
  F.prototype = superClass.prototype;
  subClass.prototype = new F();
  subClass.prototype.constructor = subClass;
  subClass.superclass = superClass.prototype;
  if (superClass.prototype.constructor == Object.prototype.constructor) {
    superClass.prototype.constructor = superClass;
  }
}
```