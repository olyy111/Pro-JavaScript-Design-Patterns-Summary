## The Information Hiding Principle
The information hiding principle serves to **reduce the interdependency of two actors** in a system. It states that all information between
two actors should be obtained through well-defined channels. In this case, these channels are
**the interfaces of your objects**.

### 1. Encapsulation vs. Information Hiding
How is encapsulation related to information hiding? You can think of it as two ways of referring
to the same idea. Information hiding is the **goal**, and encapsulation is the technique you
use to **accomplish** that goal.

Encapsulation can be defined as the hiding of internal data representation and implementation
details in an object. The only way to access the data within an encapsulated object
is to **use defined operations**. By using encapsulation, you are **enforcing information hiding**

### 2. The Role of the Interface
How does the interface help you hide information from other objects?
1. It provides a contract
that **documents the publicly accessible methods**. 
2. It defines the **relationship that two objects
can have** either object in this relationship can be replaced as long as the interface is maintained.
3. It isn’t always necessary to use a **strict interface**, like the one we defined in Chapter 2,
but most of the time you will find it very helpful to **have the available methods documented**.
Even with a known interface in place, **it is important to not expose methods that are not
defined in that interface**.
4. The ideal software system will **define interfaces for all classes**. Those classes will **provide
only the methods defined in their interfaces**; any other method will be **kept private**. All attributes
will be private and **only** accessible through **accessor** and **mutator** operations defined in
the interface. Rarely in the real world does a system have all of these characteristics. Good
code should aim toward them **whenever possible**, but not at the **cost of complicating a simple
project that doesn’t really need them**.

### 3. Basic Patterns
In this section we look at examples of the various ways an object can be created and the features
available in each.

#### 3.1 Fully Exposed Object
see eg1

#### 3.2 Private Methods Using a Naming Convention
It is essentially the same as the fully exposed object but with underscores in front of methods
and attributes you want to keep private

#### 3.3 Scope,Nested Functions, and Closures
A variable defined within a function is accessible to its nested functions. see eg2 eg3

### 4. More Advanced Patterns
#### 4.1 Static Methods and Attributes
see eg4

#### 4.2 Constants
In JavaScript, you can emulate
constants by creating a private variable with an accessor but no mutator.
see eg5


## Benefits of Using Encapsulation
1. Encapsulation protects the **integrity** of the internal data.
2. This allows you to reduce the amount of **error-checking code** you need in your other functions, and ensures that the data can never be in a bad state
3. It also has the added benefit of
allowing **easier refactoring** of your objects. Since the internal details are **shielded** from the users
of the object, you are free to change data structures and algorithms in midstream without anyone
knowing or caring.
4. By making only the methods specified in the interface public, you are **promoting loosely
coupled modules**. This is one of the most important principles of object-oriented design.
5. Using private variables also protects you from having to
worry about **namespace collisions**.
6. in general, you can make changes
more easily because you already know exactly what it will affect. If you expose internal data
directly, it would be **impossible** to know what consequences code changes could have.

## Drawbacks to Using Encapsulation
1. It can be very hard to unit test private methods. The best solution to this problem is to **only
unit test the public methods**. This should provide complete coverage of the private methods,
though only indirectly. This problem is not specific to JavaScript, and it is generally accepted
that you should only unit test your public methods.
2. Encapsulation could make your classes so inflexible that **it is impossible to reuse them to achieve a purpose you hadn’t anticipated**.
3. it is hard to implement encapsulation in JavaScript. **Descriptive comments and documentation** can reduce this
problem a bit, but not eliminate it completely. If you are going to be using these patterns, it is
important that the other programmers you work with **also understand** them.