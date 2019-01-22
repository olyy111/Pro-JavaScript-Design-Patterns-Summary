## The Structure of the Chain of Responsibility
1. The sender knows of the **first receiver** in the chain. It will send a request to that first
receiver.
2. Each receiver will analyze the request and either handle it or pass it on.
3. Each receiver only knows about one other object, its successor in the chain.
4. If none of the receivers handles the request, it falls off the chain, unhandled. Depending
on the implementation, this can either happen silently, or it can cause an error to be
thrown.

## Event Delegation
The chain of responsibility pattern is used in the JavaScript language to decide how events are
handled.

## Implementing a Chain of Responsibility in an
Existing Hierarchy. see eg2

## When Should the Chain of Responsibility Pattern Be Used?

1. It should be used in situations **where you don’t know ahead of time which of several objects
will be able to handle a request**. It should also be used if that list of handler objects isn’t known
at development time and will be specified dynamically.

    In the library example, you wanted to issue a request for a book to be sorted. You didn’t know ahead of time
which catalog it would be sorted into, if any. You also didn’t know how many or what type of
catalogs might be available. To solve these problems, you used a chain of catalogs, each passing
the book object down the chain to its successor.

2. The chain of responsibility can also be
used if more than one object should handle each request

    In the library example, for instance,
each book can be sorted into more than one catalog. The request can be handled by an object
and can then continue to be passed on, possibly to be handled by another object further down
the chain.

## Benefits of the Chain of Responsibility Pattern
1. The chain of responsibility pattern allows you to **dynamically choose which object handles a request**. This means you can use conditions known only at run-time to assign tasks to the most appropriate object. As shown in the photo gallery example, this can be much more efficient than trying to statically assign an object at development time to handle the same request. 
2. This pattern also allows you to **decouple the object making the request from the one that handles it**. This allows you to be more flexible in how you structure your modules. It also allows you to refactor and change the code around without worrying about having class names **hard-coded** in your algorithms.
3. The chain of responsibility pattern can be most effective when a chain or hierarchy already exists, as **with the composite pattern**. You can reuse the composite object’s structure to pass the request down until you reach an object that can handle it. You don’t have to write glue code to instantiate the objects or set up the chain when you use a composite because all of that is done for you. You can piggyback on this to implement methods that pass requests on to the
appropriate handler.

## Drawbacks of the Chain of Responsibility Pattern
1. Since a request is **decoupled from a specific handler**, you can never be sure that it will be handled. There is no guarantee that it won’t just fall off the end of the chain. This pattern uses **implicit receivers**, so you can never know which specific object will handle a request, if it is handled at all. This concern can be mitigated by creating catch-all receivers and always adding them to the end of the chain, but this can be cumbersome and removes the flexibility of always being able to add objects to the end of the chain.
2. Using the chain of responsibility with the composite class can be somewhat **confusing**. The promise of the composite node is that it can be used completely interchangeably with the leaf nodes, and the client code will never know the difference. All methods are passed down the hierarchy. Chain of responsibility methods **change this contract**. Some methods might never be passed on, and instead are handled at the composite level. It can be tricky to code
these methods in such a manner as to be interchangeable with the leaf methods. They can be very efficient, but at the cost of code complexity.