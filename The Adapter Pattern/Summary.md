you can
intercept incoming logic from the suppliers and transform them in a way that the receivers
can understand.


## How to use adapter pattern
Find the point of integration
in the eg4, exactly, the method `fooMail.getMail`, only receive a callback, and the callback be invoked with a argument named text(the xhr obj's property responseText), so if in the adpater, wo receive the callback, and **give the responseText to the callback**. This is the point of integration, when you get it, you get the adapter
```javascript
fooMail.getMail(function(text) {
  $('message-pane').innerHTML = text;
});
```

## When Should the Adapter Pattern Be Used?

1. Adapters should be used in any place where clients expect a particular interface but the interface
offered by the existing API is incompatible.
2. Adapters should only be used to **reconcile
differences** in syntax;
3. he method you are adapting still needs to be able to **perform the needed**
task. If this is not true, an adapter will not solve your problem.
4. Adapters can also be used when
clients **prefer a different interface**, perhaps one that is easier for them to use.
5. When you create
an adapter, just like a bridge or a facade, you **decouple an abstraction from its implementation**, 
allowing them to vary independently.
6. you don't need to implement the client code existing.

## Benefits of the Adapter Pattern
1. As mentioned throughout this chapter, adapters can help **avoid massive code rewrites**. They
handle logic by wrapping a new interface around that of an existing class so you can use new
APIs (with different interfaces) and **avoid breaking existing implementations**.

## Drawbacks of the Adapter Pattern
1. they necessarily entail writing brand-new code. avoid adapters.
2. Some say adapters are unnecessary overhead that can be avoided
by simply rewriting existing code.
3. Adapters may also introduce a new set of utilities to be
supported.
4. Adapters may also introduce a new set of utilities to be
supported. **If an existing API is not finalized or, even more likely, a newer interface is not finalized**, the adapters may not continue to work. In the case where keyboard hardware created PS2-to-USB adapters, it made complete sense because the PS2 plug was essentially finalized on thousands of keyboards; and the USB interface became the new
standard. In software development, this is **not always guaranteed**.

## Summary
The adapter pattern is a useful technique that allows you to wrap classes and objects, thus
giving client code exactly the interface that it expects. You can **avoid breaking existing implementations**
and **adapt to newer, better interfaces**. You can customize the interface to your own
needs as an implementer. Adapters do in fact introduce new code; however, the benefits most
likely outweigh the drawbacks in **large systems and legacy frameworks**.