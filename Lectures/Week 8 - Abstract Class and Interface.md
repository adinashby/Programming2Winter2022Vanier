# 2.3 Abstract Class and Interface

## 1. Abstract Method

### 1.1 What is abstract method

* `Abstract method` is a method with only the method header but no method body. `Abstract method` has the name, the parameter list and the return type, so it tells what the methods is for and how to use it. But since it does not have a body, it does not provide the details of the implementation of it.  

### 1.2 How to define

* Abstract method` is a method with only keyword `abstract`, the method header and ";"

  ```java
  // Example of abstract method
  public abstract calcArea();
  ```

  

## 2. Abstract Class

### 2.1 What is Abstract Class

* `Abstract class` is a class that may contain `abstract method`, (it can also contain normal method). On the other hand, **normal classes are not allowed to have `abstract methods`**. 

* Except can have abstract methods in the class, there is no difference between an abstract class and a regular class, both of them can have data members, static variables, and regular methods.

  

### 2.2 How to Define 

Abstract class is a class defined with keyword `abstract`. 

```java
// Example of an abstract class, this abstract class contains both abstract method and normal methods
public abstract class Shape {

    /**
     * Calculates the area of a shape
     *
     * @return the area of a shape
     */
    public abstract double calcArea();      	// abstract method, with no body

    /**
     * Calculates the perimeter of a shape
     *
     * @return the perimeter of a shape
     */
    public abstract double calcPerimeter();      // abstract method, with no body

    /**
     * Normal methods are allowed
     */
    private void print() {
        System.out.println("hello");
    }
}
```

### 2.3 When to Use Abstract Class

Usually an `Abstract class` is a superclass. By defining a superclass abstract, we can add `abstract methods` in it. In this case, all subclasses of that class will also inherit the abstract methods, and then they can **override** it in the way they want. Adding abstract methods in the superclass forces the subclass to implement those methods. You can also understand it as the superclass creates a Todo List for all the subclasses, and the subclasses have to complete the Todo List by overriding the abstract methods. (A subclass can also choose to not override the abstract method, then that class should also be defined as an abstract class)

In the previous example, the `Shape` class contains two abstract methods: `calcArea()` and `calcPerimeter()`. The shape class does not represent a specific shape, so in the class we do not know what formula to use to calculate the area or parameter. But these two abstract methods will be inherited by the subclasses, which could be a more specific shape like a rectangular or a ellipse. And they can override the methods with the body to calculate the area and perimeter.

### 2.4 Downside of Abstract Class

There is a cost of using abstract class, in short you can remember it as: **you cannot create an object of an abstract class**. Take the `Shape` class for example, since it is an abstract class with two abstract methods inside. Let's assume if Java allows us to create an object of it, `Shape s = new Shape();`, then we can call methods through that object, e.g.: `s.calcArea()`. However, this method is abstract with no method body in the `Shape` class, thus Java does not know how to execute it, and that is a serious problem for Java. Because of this, Java does not allow us to create the object first. (There is a way to create the object, but you have to override all abstract methods when you create the object).

**Notice**: You can still create a reference of an abstract class. In fact, it is very common to see that, e.g.: `Shape s = new Circle();`  , if the `Circle` is a normal class that override the abstract method inherited from the `Shape` class, then `s` is just a `Shape` type reference, the object is still `Circle` type.