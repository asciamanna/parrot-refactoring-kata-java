# Parrot Refactoring Kata in Java

This is a fork of Emily Bache's repository, [which can be found here](https://github.com/emilybache/Parrot-Refactoring-Kata). The tests have been updated to use assertj. 

Can you spot any code smells in this code? I'll give you a clue - a spot of Pol(l)ymorphism should improve matters!

Refactor this code, take small steps, run the tests often. See how small and beautiful you can make it.

## Acknowledgements
This code is heavily inspired by one of the examples in Martin Fowler's book "Refactoring". It's a classic, and if it's not on your bookshelf already I suggest you treat yourself to a copy!

## Instructions
For this exercise you are going to get another opportunity to practice the refactoring rhythm. You'll also learn the steps to replacing the _Switch Statement_ or _Repeated Switches_ code smell.

1. Refactor into a polymorphic solution (see diagram below).
2. Take small steps and run the tests often.
3. Use automated refactorings as much as possible.

![Parrot Kata Design](./parrot-kata.png)

## Steps - Parrot Refactoring Kata TODO List
These are the steps to remove the Switch Statement (or Repeated Switches) code smell. 
They consist of two refacotrings. Replace Type Code with Subclasses & Replace Conditional with Polymorphism.

### Replace Type Code with Sublclasses
- [ ] Introduce a static creation method on the `Parrot Class` that wraps the construction of the parrot. Call it instead of the Parrot constructor from the tests. (You can use find and replace in a single step for this).
- [ ] Make `type` a self encapsulated field (a getter for the field `type`). Look for the refactoring in the IntelliJ Refactoring Menu
- [ ] Create sublcass for Parrot type (auotmated subclass creation is available from context actions menu off of the class name).
- [ ] Override type getter on the subclass, return the hardcoded type enum value.
- [ ] Create instance of subclass in creation method by checking provided type parameter in Parrot creation method.
- [ ] Repeat the previous three stps for the other two Parrot types.
- [ ] Remove creation of base Parrot in creation method (it is dead code now).
- [ ] Make Parrot class `abstract`
- [ ] Make `getType()` method `abstract`
- [ ] Remove dead code (using Safe Delete from context actions menu)

### Replace Conditional with Polymorphism
What can get pushed down into child classes, what needs to stay in the parent `Parrot` class? 

- [ ] Change access modifer for `getBaseSpeed()` to `protected`
- [ ] Override `getSpeed()` method in `EuropeanParrot` class
- [ ] Paste code from base class `getSpeed()` European case into overridden method on child class. 
- [ ] Delete case code from switch in base class.
- [ ] Repeat the previous three steps for the other two parrot types (what methods and fields can be pushed down into base classes?) 
- [ ] Push down fields and methods before overriding `getSpeed()` in the child class (Push Members Down refactoring is available from the Refactoring Menu)
- [ ] Remove dead code (context action menu has the Safe Delete refactoring)
- [ ] Make `getSpeed()` abstract on the base Parrot class (requires making `Parrot` base class abstract).
- [ ] Remove dead code from classes (context action menu Safe Delete)
    - Make sure to get rid of the `getType()` method, the `type` field, and the corresponding overrides. 

You Did it! 

