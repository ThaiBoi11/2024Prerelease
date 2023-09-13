# 2024Prerelease
here we go 
## Class Diagrams
![A set of 4 class diagrams detailing the fields and methods that belong to that class](/2024%20Class%20Diagram.png)
## Classes
A class, in object-oriented programming, can be thought of as a blueprint for creating an object, where an object is a collection of related variables (called fields or attributes in the context of classes) and subroutines (called methods) that define or act upon the object respectively. Since this definition is a bit word-heavy, a simple example of a simple class would be 
```cs
class Rectangle {
    public int width;
    public int height;
    public int area;
    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
        this.area = width * height;
    }
    
}
```
This class represents a rectangle, with a width, height and even a way to calculate the area of the rectangle. Any method that shares the same name as the class it belongs to is called a constructor, and is used when you want to create an object (the this keyword is just used so you don't end up typing `width=width`). A use case of the above constructor would be `Rectangle r1 = new Rectangle(7,4);` and to find the area, you would use `Console.Write(r1.Area());` You could also use `Console.Write(r1.height * r1.width)`, but only because the access modifier is public for both attributes, which is explained next.

The words `public`, `private` and `protected` appear throughout the program, and they specify the _scope_ of certain attributes and methods (This is an example of _encapsulation_, one of the 4 pillars of object-oriented programming). For example, in the above class, the area attribute is initially created by multiplying the width and height, which is entirely reasonable. However, there is nothing stopping us from running the following code:
```cs
Rectangle r1 = new Rectangle(7,4);
r1.area = 56;
```
This would run, and modify the area attribute of the r1 object, but obviously you cannot have a rectangle with side lengths 7 and 4, and also have an area of 56. For this reason, we use access modifiers to decide whether code that exists outside of the class is able to access and modify objects. The `public` keyword means that the attribute can be read and modified by code outside the class, `private` means that it can only be read and modified by the class, and `protected` means that it can only be accessed by the class, and any derived classes. (NB: In the context of methods, access modifiers decide where the method can be called from.) Derived classes are a part of the concept of inheritance. 

Inheritance, another of the four pillars of OOP, is the idea of creating classes that "inherit" fields and methods from other classes. In the context of the pre-release, we have a derived/child class (the BlockedCell class) that inherits attributes and methods from its base/parent class (the Cell class). In essence, a derived class expands on or modifies a class, making it more specialised for specific scenarios. We can identify that the BlockedCell class inherits from the Cell class by the way it is created; the `:` in `class BlockedCell : Cell` statement is equivalent to saying "inherits from". This means that we don't need to rewrite an entire class just to represent a different type of cell; we can just add on to the original Cell class. The constructor for the BlockedCell class has a `:base()`, which just says it is referencing the base class' constructor because we don't have a standalone Symbol attribute that belongs to the BlockedCell class to reference. 

Another point of importance is the `override` keyword, which relates to the `virtual` keyword. Virtual and override are used in conjunction with one another, and are used to change the behaviour of methods depending on where they are declared. In the pre-release, in the `Cell` class, the `CheckSymbolAllowed` method has a `virtual` keyword attached to it, which "marks" it to say "If a derived class has a method with the same name AND the `override` keyword attached, when the method is called by an object that belongs to the derived class, this method will be called instead of the one that exists in the base class". In the context of the BlockedCell class, the presence of the virtual/override pair in the `CheckSymbolAllowed` means that whenever a BlockedCell object exists, and calls the method, a "@" is always returned, as opposed to having to check the `SymbolsNotAllowed` list.

## Notes of importance
- The Cell class has an empty void method called UpdateCell(). It can be reasonable assumed that we are going to do something with this during the exam, but figuring out what "updating" a cell would be might be a challenge.
- There are nine instances where the `virtual` keyword is attached to a method, but only one instance where `override` is used. Seeing as how the `virtual/override` keyword pair are only implemented when using derived classes, it may be that we would have to create derived classes that implement overridden methods.