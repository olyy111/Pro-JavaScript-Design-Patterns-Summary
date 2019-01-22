```javascript
/* Interfaces. */
var Publication = new Interface('Publication', ['getIsbn', 'setIsbn', 'getTitle',
  'setTitle', 'getAuthor', 'setAuthor', 'getGenres', 'setGenres', 'display']);
var Library = new Interface('Library', ['addBook', 'findBooks', 'checkoutBook',
  'returnBook']);
var Catalog = new Interface('Catalog', ['handleFilingRequest', 'findBooks',
  'setSuccessor']);

/* Book class. */
var Book = function (isbn, title, author, genres) { // implements Publication
  // ...
}
/* PublicLibrary class. */
var PublicLibrary = function (books) { // implements Library
  this.catalog = {};
  for (var i = 0, len = books.length; i < len; i++) {
    this.addBook(books[i]);
  }
};
PublicLibrary.prototype = {
  findBooks: function (searchString) {
    var results = [];
    for (var isbn in this.catalog) {
      if (!this.catalog.hasOwnProperty(isbn)) continue;
      if (this.catalog[isbn].getTitle().match(searchString) ||
        this.catalog[isbn].getAuthor().match(searchString)) {
        results.push(this.catalog[isbn]);
      }
    }
    return results;
  },
  checkoutBook: function (book) {
    var isbn = book.getIsbn();
    if (this.catalog[isbn]) {
      if (this.catalog[isbn].available) {
        this.catalog[isbn].available = false;
        return this.catalog[isbn];
      }
      else {
        throw new Error('PublicLibrary: book ' + book.getTitle() +
          ' is not currently available.');
      }
    }
    else {
      throw new Error('PublicLibrary: book ' + book.getTitle() + ' not found.');
    }
  },
  returnBook: function (book) {
    var isbn = book.getIsbn();
    if (this.catalog[isbn]) {
      this.catalog[isbn].available = true;
    }
    else {
      throw new Error('PublicLibrary: book ' + book.getTitle() + ' not found.');
    }
  },
  addBook: function (newBook) {
    this.catalog[newBook.getIsbn()] = { book: newBook, available: true };
  }
};

/* PublicLibrary class, with hard-coded catalogs for genre. */
var PublicLibrary = function (books) { // implements Library
  this.catalog = {};
  this.biographyCatalog = new BiographyCatalog();
  this.fantasyCatalog = new FantasyCatalog();
  this.mysteryCatalog = new MysteryCatalog();
  this.nonFictionCatalog = new NonFictionCatalog();
  this.sciFiCatalog = new SciFiCatalog();
  for (var i = 0, len = books.length; i < len; i++) {
    this.addBook(books[i]);
  }
};
PublicLibrary.prototype = {
  findBooks: function (searchString) {
    //... 
  },
  checkoutBook: function (book) {
    //... 
  },
  returnBook: function (book) {
    //... 
  },
  addBook: function (newBook) {
    // Always add the book to the main catalog.
    this.catalog[newBook.getIsbn()] = { book: newBook, available: true };
    // Try to add the book to each genre catalog.
    this.biographyCatalog.handleFilingRequest(newBook);
    this.fantasyCatalog.handleFilingRequest(newBook);
    this.mysteryCatalog.handleFilingRequest(newBook);
    this.nonFictionCatalog.handleFilingRequest(newBook);
    this.sciFiCatalog.handleFilingRequest(newBook);
  }
};

/* PublicLibrary class, with genre catalogs in a chain of responsibility. */
var PublicLibrary = function (books, firstGenreCatalog) { // implements Library
  this.catalog = {};
  this.firstGenreCatalog = firstGenreCatalog;
  for (var i = 0, len = books.length; i < len; i++) {
    this.addBook(books[i]);
  }
};
PublicLibrary.prototype = {
  findBooks: function (searchString) {
    //... 
  },
  checkoutBook: function (book) {
    //... 
  },
  returnBook: function (book) {
    //... 
  },
  addBook: function (newBook) {
    // Always add the book to the main catalog.
    this.catalog[newBook.getIsbn()] = { book: newBook, available: true };
    // Try to add the book to each genre catalog.
    this.firstGenreCatalog.handleFilingRequest(newBook);
  }
};

// Instantiate the catalogs.
var biographyCatalog = new BiographyCatalog();
var fantasyCatalog = new FantasyCatalog();
var mysteryCatalog = new MysteryCatalog();
var nonFictionCatalog = new NonFictionCatalog();
var sciFiCatalog = new SciFiCatalog();
// Set the links in the chain.
biographyCatalog.setSuccessor(fantasyCatalog);
fantasyCatalog.setSuccessor(mysteryCatalog);
mysteryCatalog.setSuccessor(nonFictionCatalog);
nonFictionCatalog.setSuccessor(sciFiCatalog);
// Give the first link in the chain as an argument to the constructor.
var myLibrary = new PublicLibrary(books, biographyCatalog);
// You can add links to the chain whenever you like.
var historyCatalog = new HistoryCatalog();
sciFiCatalog.setSuccessor(historyCatalog);

/* GenreCatalog class, used as a superclass for specific catalog classes. */
var GenreCatalog = function () { // implements Catalog
  this.successor = null;
  this.catalog = [];
};
GenreCatalog.prototype = {
  _bookMatchesCriteria: function (book) {
    return false; // Default implementation; this method will be overriden in
    // the subclasses.
  }
  handleFilingRequest: function (book) {
    // Check to see if the book belongs in this catagory.
    if (this._bookMatchesCriteria(book)) {
      this.catalog.push(book);
    }
    // Pass the request on to the next link.
    if (this.successor) {
      this.successor.handleFilingRequest(book);
    }
  },
  findBooks: function (request) {
    if (this.successor) {
      return this.successor.findBooks(request);
    }
  },
  setSuccessor: function (successor) {
    if (Interface.ensureImplements(successor, Catalog) {
      this.successor = successor;
    }
  }
};
/* SciFiCatalog class. */
var SciFiCatalog = function () { }; // implements Catalog
extend(SciFiCatalog, GenreCatalog);
SciFiCatalog.prototype._bookMatchesCriteria = function (book) {
  var genres = book.getGenres();
  if (book.getTitle().match(/space/i)) {
    return true;
  }
  for (var i = 0, len = genres.length; i < len; i++) {
    var genre = genres[i].toLowerCase();
    if (genres === 'sci-fi' || genres === 'scifi' || genres === 'science fiction') {
      return true;
    }
  }
  return false;
};
/* PublicLibrary class. */
var PublicLibrary = function (books) { // implements Library
  //...
};
PublicLibrary.prototype = {
  findBooks: function (searchString, genres) {
    // If the optional genres argument is given, search for books only in
    // those genres. Use the chain of responsibility to perform the search.
    if (typeof genres === 'object' && genres.length > 0) {
      var requestObject = {
        searchString: searchString,
        genres: genres,
        results: []
      };
      var responseObject = this.firstGenreCatalog.findBooks(requestObject);
      return responseObject.results;
    }
    // Otherwise, search through all books.
    else {
      var results = [];
      for (var isbn in this.catalog) {
        if (!this.catalog.hasOwnProperty(isbn)) continue;
        if (this.catalog[isbn].getTitle().match(searchString) ||
          this.catalog[isbn].getAuthor().match(searchString)) {
          results.push(this.catalog[isbn]);
        }
      }
      return results;
    }
  },
  checkoutBook: function (book) {
    //... 
  },
  returnBook: function (book) {
    //... 
  },
  addBook: function (newBook) {
    //... 
  }
};
/* GenreCatalog class, used as a superclass for specific catalog classes. */
var GenreCatalog = function () { // implements Catalog
  this.successor = null;
  this.catalog = [];
  this.genreNames = [];
};
GenreCatalog.prototype = {
  _bookMatchesCriteria: function (book) {
    //... 
  },
  handleFilingRequest: function (book) {
    //... 
  },
  findBooks: function (request) {
    var found = false;
    for (var i = 0, len = request.genres.length; i < len; i++) {
      for (var j = 0, nameLen = this.genreNames.length; j < nameLen; j++) {
        if (this.genreNames[j] === request.genres[i]) {
          found = true; // This link in the chain should handle
          // the request.
          break;
        }
      }
    }
    if (found) { // Search through this catalog for books that match the search
      // string and aren't already in the results.
      outerloop: for (var i = 0, len = this.catalog.length; i < len; i++) {
        var book = this.catalog[i];
        if (book.getTitle().match(searchString) ||
          book.getAuthor().match(searchString)) {
          for (var j = 0, requestLen = request.results.length; j < requestLen; j++) {
            if (request.results[j].getIsbn() === book.getIsbn()) {
              continue outerloop; // The book is already in the results; skip it.
            }
          }
          request.results.push(book); // The book matches and doesn't already
          // appear in the results. Add it.
        }
      }
    }
    // Continue to pass the request down the chain if the successor is set.
    if (this.successor) {
      return this.successor.findBooks(request);
    }
    // Otherwise, we have reached the end of the chain. Return the request
    // object back up the chain.
    else {
      return request;
    }
  },
  setSuccessor: function (successor) {
    //... 
  }
};
/* SciFiCatalog class. */
var SciFiCatalog = function () { // implements Catalog
  this.genreNames = ['sci-fi', 'scifi', 'science fiction'];
};
extend(SciFiCatalog, GenreCatalog);
SciFiCatalog.prototype._bookMatchesCriteria = function (book) {
  //... 
};
```