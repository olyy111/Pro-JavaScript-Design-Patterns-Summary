## When Should the Flyweight Pattern Be Used?
1. Your page must use a large number of resource-intensive objects. This is the most important condition;
2. The next condition is that at least some of the data stored within each of these objects must be able to be made extrinsic.
3. The last condition is that once the extrinsic data is removed, you must be left with a relatively small number of unique objects.

## General Steps for Implementing the Flyweight
1. Strip all extrinsic data from the target class.
instance to instance.
2. Create a factory to control how the class is instantiated.
3. Create amanager to store the extrinsic data.

## Benefits of the Flyweight Pattern
1. The flyweight pattern can reduce your page’s resource load by several orders of magnitude.
2. It doesn’t require huge changes to your code to get these savings. Once you have created
the manager, the factory, and the flyweight, the only change you must make to your code is to
call a method of the manager object instead of instantiating the class directly.

## Drawbacks of the Flyweight Pattern
**This is only an optimization pattern.**
1. It’s harder to debug
2. Maintenance can also be more difficult because of this optimization.
3. if you are **unsure** whether a flyweight is needed, it probably isn’t.
4. The flyweight pattern is for situations where system resources are almost entirely utilized, and where it is obvious that some sort of
optimization must be done. It is then that the benefits outweigh the costs.