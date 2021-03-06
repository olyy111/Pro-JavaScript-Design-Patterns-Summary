```javascript
/* Person Prototype Object. */
var Person = {
  name: 'default name',
  getName: function () {
    return this.name;
  }
};

var reader = clone(Person);
alert(reader.getName()); // This will output 'default name'.
reader.name = 'John Smith';
alert(reader.getName()); // This will now output 'John Smith'.

/* Author Prototype Object. */
var Author = clone(Person);
Author.books = []; // Default value.
Author.getBooks = function () {
  return this.books;
}

var author = [];
author[0] = clone(Author);
author[0].name = 'Dustin Diaz';
author[0].books = ['JavaScript Design Patterns'];
author[1] = clone(Author);
author[1].name = 'Ross Harmes';
author[1].books = ['JavaScript Design Patterns'];
author[1].getName();
author[1].getBooks();

/* Asymmetrical Reading and Writing of Inherited Members */
var authorClone = clone(Author);
alert(authorClone.name); // Linked to the primative Person.name, which is the
// string 'default name'.
authorClone.name = 'new name'; // A new primative is created and added to the
// authorClone object itself.
alert(authorClone.name); // Now linked to the primative authorClone.name, which
// is the string 'new name'.
authorClone.books.push('new book'); // authorClone.books is linked to the array
// Author.books. We just modified the
// prototype object's default value, and all
// other objects that link to it will now
// have a new default value there.
authorClone.books = []; // A new array is created and added to the authorClone
// object itself.
authorClone.books.push('new book'); // We are now modifying that new array.

var CompoundObject = {
  string1: 'default value',
  childObject: {
    bool: true,
    num: 10
  }
}

var compoundObjectClone = clone(CompoundObject);
// Bad! Changes the value of CompoundObject.childObject.num.
compoundObjectClone.childObject.num = 5;
// Better. Creates a new object, but compoundObject must know the structure
// of that object, and the defaults. This makes CompoundObject and
// compoundObjectClone tightly coupled.
compoundObjectClone.childObject = {
  bool: true,
  num: 5
};

// Best approach. Uses a method to create a new object, with the same structure and
// defaults as the original.
var CompoundObject = {};
CompoundObject.string1 = 'default value',
  CompoundObject.createChildObject = function () {
    return {
      bool: true,
      num: 10
    }
  };
CompoundObject.childObject = CompoundObject.createChildObject();
var compoundObjectClone = clone(CompoundObject);
compoundObjectClone.childObject = CompoundObject.createChildObject();
compoundObjectClone.childObject.num = 5;

/* Clone function. */
function clone(object) {
  function F() { }
  F.prototype = object;
  return new F;
}
```

The key function is `clone`:
```javascript
function clone(object) {
  function F() { }
  F.prototype = object;
  return new F;
}
```