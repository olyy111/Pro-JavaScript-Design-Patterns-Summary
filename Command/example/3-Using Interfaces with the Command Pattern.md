```javascript
/* Command interface. */
var Command = new Interface('Command', ['execute']);
//You can then check that the command implements the correct execute operation by
//using code like this:
/* Checking the interface of a command object. */
// Ensure that the execute operation is defined. If not, a descriptive exception
// will be thrown.
Interface.ensureImplements(someCommand, Command);
// If no exception is thrown, you can safely invoke the execute operation.
someCommand.execute();
//If you are using closures to create command functions, this check is even simpler, since
//you only need to check that the command really is a function:
  If(typeof someCommand != 'function') {
  throw new Error('Command isn't a function');
}
```