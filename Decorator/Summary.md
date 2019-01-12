
## The Role of the Interface in the Decorator Pattern
1. The decorator pattern **benefits heavily from the use of interfaces**. The most important feature
of the decorator is that it can be used in place of its component. 

2. If a decorator cannot be used interchangeably with its component, it is **broken**. This is
a key feature of the pattern, This is only possible if they maintain identical interfaces.

## The Decorator Pattern vs. the Composite Pattern
1. Composites do not modify the method calls and instead focus on organizing the sub-objects. 
2. Decorators exist solely to modify the method calls and do no organization, since
there is only one sub-object.

## In What Ways Can a Decorator Modify Its Component?
Adding Behavior After aMethod

## Benefits of the Decorator Pattern
1. Decorators are great for **adding features or responsibilities** to objects at run-time.
    - In the bicycle
shop example, you were able to add optional features to the bicycle objects dynamically through
the use of decorators. This is especially beneficial if only some of the objects need these features.
2. It prevents you from having to use large numbers of subclasses to achieve the same effect.
3. Decorators work transparently, meaning you can wrap them around objects and then
continue to use them the same way you would before.
4. As you saw in the MethodProfiler example,
this can even be done dynamically, **without knowing the interface of the component object**
in advance. Decorators give you an enormous range of flexibility in making additions to existing
objects.

## Drawbacks of the Decorator Pattern
1. The first is that any code that
relies on **type checking** will fail if an object has been wrapped with a decorator. It’s true that
strict type checking of objects is rarely done in JavaScript, but if it is done in your code, decorators
will not match the required type.  Decorators are normally completely transparent to the
client code; but this is one case where the client code will be able to tell the difference between
a decorator and its component.

2. The second drawback is that using decorators can often **complicate your architecture**. They have a tendency to introduce a lot of small objects that look relatively similar(see the
bicycle shop example) but do very different things. They can often be confusing, especially to
developers not familiar with the decorator pattern. Also, the syntax required to implement, **decorators with dynamic interfaces** (such as MethodProfiler) can be frightening at best. You
must use extra care when creating an architecture that uses decorators to ensure that your
code is well-documented and easy to understand.

## Notice
when you implement the decorator, there are some points you need to notice
1. if the behavior add to method change, you need to know if the applied order be restricted.
2. if you add method to a decorator that component does not have,  checks the
component object and creates pass-through methods for each of the methods present in
the component.
3. the factory can encapsulate the process of create a object, also order the options. eg6-The Role of the Factory
4. Decorators need not be limited to just classes. It is possible to create decorators that wrap
individual functions and methods as well. This is a common technique in some languages.

## Summary
In this chapter we investigated a pattern that allows you to **add functionality** to objects transparently
and dynamically, without creating subclasses. The decorator pattern can be used to
add features to specific objects **without modifying the class definition**. We took another look at
the bicycle shop example and used factories to create bicycles with many customizable options.
We discussed the different ways that decorators can be used to modify the objects they wrap,
and some of the pitfalls associated with each. As a practical exercise, we created a decorator
with a **dynamic interface** that allows you to log the elapsed time an object’s methods take to
execute.
Decorators are extraordinarily useful once you understand how they work. Just the fact that
we accomplished with seven decorators what would have taken several thousand subclasses
proves this point. By being totally transparent, this pattern can be used without too much fear of
breakage or incompatibility. Decorators are a simple way to augment your objects without
redefining them.