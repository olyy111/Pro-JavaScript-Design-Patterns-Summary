## Usage of the Command Pattern
The Client, the Invoker, and the Receiver, commented in eg1

## Types of Command Objects, eg4
1. **SimpleCommand**,  which is nothing more than a binding between an existing receiver’s
action (the ad object’s start and stop methods) and an invoker (the button).
2. **ComplexCommand**, It doesn’t really have a receiver because the action is implemented concretely
within the command object itself
3. **GreyAreaCommand** A command may have some
implementation code in its execute method, along with a receiver’saction, which would put it somewhere in the middle of the range

## When to Use the Command Pattern
The main purpose of the command pattern is to **decouple** an invoking object (a UI, an API,
a proxy, etc.) from the object implementing the action.

As such, it should be used wherever
**more modularity is needed** in the interaction between two objects. It is an organizational pattern
and can be applied to almost any system;

It is an organizational pattern
and can be applied to almost any system; but **it is most effective in circumstances where
actions need to be normalized so that a single class of invoker can call a wide array of methods**,
without knowing anything about them. A lot of user interface elements fit this bill perfectly, such as the menu in the last example. **eg5**

There are a couple of other specialized cases that can benefit from the command pattern. It can be used to **encapsulate a callback function**, for use in an XHR call or some other delayedinvocation
situation. Instead of passing a callback function, you can pass a callback command,
which allows you to encapsulate multiple function calls in a single package. 

Command objects
also make it almost trivial to implement an undo mechanism in your application. By **pushing
executed commands to a stack**, you can have an **unlimited undo**. This command logging can
be used to implement undo even for actions that are not inherently reversible. It can also be
used to **restore the entire state** of any app after a crash.

## Benefits of the Command Pattern
1. when properly
used, your program will be more **modular and flexible**.
2. The second is that it allows you to
implement **complex and useful features** such as undo and state restoration extremely easily.

3. It allows you to **parameterize it** and
store those parameters through multiple invocations. 
4. It lets you define methods **other than
just execute88, such as undo, which allow the same action to be performed in different ways. 
5. It allows you to define **metadata concerning the action**, which can be used for object introspection
or event logging purposes. 
6. Command objects are 88encapsulated method invocations**, and
that encapsulation gives them many features that amethod invocation on its own does not have.

## Drawbacks of the Command Pattern
1. It can be **inefficient** to create a command object around a single method invocation if that is all it is used for.
2. Command objects also can make it a little **tougher** to debug problems in your code, since there is now another
layer on top of your methods that can contain errors.