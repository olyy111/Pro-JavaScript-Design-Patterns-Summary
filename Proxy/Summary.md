## Benefits of the Proxy Pattern
Each type of proxy has a different set of benefits.

1. The remote proxy allows you to treat a remote
resource as a **local JavaScript object**. look **eg2**
    - This is obviously a huge benefit; it reduces the amount of
glue code you have to write to access the remote resource and provides a single interface for
interacting with it. You only have to change your code in **one place** if the API provided by the
remote resource changes. It also **stores all of the data associated with the ** in a single
place. This includes the URL of the resource, the data format used, and the structure of the
commands and responses. If there is more than one web service, it is possible to create a general
remote proxy as an abstract class and then subclass it for each of the web services that you
need to access.

2. The virtual proxy has a very different set of benefits. This is an optimization pattern and should be used only **when a resource is expensive to create or
maintai**n and needs a proxy to control when and how it is created.

look **eg3 and eg4**

## Drawbacks of the Proxy Pattern
Even though the benefits to each type of proxy are different, the drawbacks are the same. By
its very design, **a proxy masks a lot of complex behavior**.

## Summary
In this chapter, we discussed the various forms of the proxy pattern. Each form controls access
to a resource in some way. This resource is called the real subject.
1. The protection proxy controls which clients can access methods of the real subject. It is
impossible to implement in JavaScript and was ignored in this chapter.
2. The remote proxy controls access to a remote resource. In other languages, such as Java,
the remote proxy simply connects to a persistent Java virtual machine and passes along any
method calls. This isn’t possible in client-side JavaScript, but the remote proxy can be very
useful for encapsulating a web service written in another language. This type of proxy allows
you to access the remote resource as if it were a local object.
3. The virtual proxy controls access to a class or object that is expensive to create or maintain.
This can be very helpful in JavaScript, where the end user’s browser may only have a limited
amount of memory with which it runs your code. It can also be helpful if you find that the real
subject loads slowly, because the virtual proxy can provide a loading message or a dummy UI
that the end user can interact with until the real UI is loaded.


The proxy pattern **can be swapped with the real subject at any time and adds complexity
to your project**. It is important to use it only when it will make your code **less redundant**, **more
modular**, or **more efficient**. When used in these situations, a proxy can make it much easier to
access an otherwise difficult resource.
