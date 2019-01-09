## Summary
JavaScript passes all objects by reference, so you can pass these references back in every method.

1. By returning this at the end of each method, you can create a class that is chainable. This style helps to streamline code authoring and, to a certain degree, make your code more elegant and
easier to read. 
2. Often you can avoid situations where objects are redeclared several times and
instead use a chain, which produces less code. 
3. If you want consistent interfaces for your classes, and you want both mutator and accessor methods to be chainable, you can use function callbacks for your accessors.