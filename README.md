# Creating A Class Instance

## Learning Goals

- Create an object in Java using the `new` operator
- Initialize a field based on data type
- Declare a variable having a class type
- Assign a variable to reference an object
- Initialize a field at variable declaration

## Instantiating An Object

As stated before, in Java, an **object** is an _instance_ of a **class**.
The  class serves as a blueprint describing the data structure for each object,
along with the methods that implement the object behavior.

Let's go back to our `Dog` class from earlier:

```java
public class Dog {

  String name;
  String breed;
  int age;
  boolean waggingTail;

}
```

How do we go about creating an instance of `Dog` in Java?

When we create an instance of this class, we are telling Java to create something
that will comply with the data structure described by the class. In other
words, each dog object needs memory to be allocated to store values for the
`name`, `breed`, `age`, and `waggingTail` properties.

If we want to create an instance of `Dog`, we can do so with the following code snippet:

```java
new Dog()
```

The code consists of 2 parts:

- Instantiation − The `new` operator is used to create an instance of `Dog` by allocating memory
  to store the four instance variables defined in the `Dog` class (name, breed, age, waggingTail).

- Initialization − The `new` operator is followed by a call to a constructor `Dog()`.  The
  constructor is a method that initializes the new object by assigning a value to each instance variable.
  We will cover constructors in detail in a later lesson.  But for now just understand that
  the default constructor initializes each variable based on their data type:   
  
| Data Type                       | Default Value  |
|---------------------------------|----------------|
| int, long, byte, short          | 0              |
| float, double                   | 0.0            |
| boolean                         | false          |
| char                            | '\u0000'       |
| Reference type (such as String) | null           |

When we execute the code `new Dog()`, the fields are assigned default values as shown:

![new dog instance](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/new_dog.png)

But creating a `Dog` instance is not useful unless we have a way to reference the new object.
We need to declare a variable with a defined type of `Dog`, then assign the variable to the newly
created object.  

For example, we can declare a variable named `bigDog` and assign it to the
newly created `Dog` instance:

```java
Dog bigDog = new Dog(); 
```

- A variable declared with a class type, such as `Dog bigDog`, stores an object reference
  (i.e. the memory address of the object).
- The `new` operator returns the memory address of the newly instantiated object.
- The `=` assignment operator assigns the memory address of the new `Dog` object to the variable named `bigDog`.

While the variable `bigDog` stores an actual memory address as a value, we can visualize
the object reference like an arrow pointing to the object in memory.

![dog#1 created](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/new_dog1.png)

## Adding a `main` method to create instances of `Dog`

Let's update the `Dog` class to have a `main` method that
creates two instances of `Dog`.  

```java
public static void main(String[] args) {

    // create 2 Dog instances
    Dog bigDog = new Dog();
    Dog smallDog = new Dog();

}
```

Eventually we will create a separate class to contain the `main` method,
but for now we will just add the method to the current `Dog` class.

While a method can be placed anywhere within the class body, we normally place it after the fields:

```java
public class Dog {

  String name;
  String breed;
  int age;
  boolean waggingTail;

  public static void main(String[] args) {

    // create 2 Dog instances
    Dog bigDog = new Dog();
    Dog smallDog = new Dog();

  }

}
```


Executing the `main` method results in the creation of two `Dog` instances:

![dog#2 created](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/new_dog2.png)

- The visualization shows the `main` method as a frame on the call stack.
- The variables `bigDog` and `smallDog` are defined as local variables in the `main` method,
  thus the variables are stored in the `main` method frame.
- The assignment `Dog bigDog = new Dog();` assigns the variable `bigDog` to
  the memory address of the first `Dog` instance that was created.  
- The assignment `Dog smallDog = new Dog();` assigns the variable `smallDog` to
  the memory address of the second `Dog` instance that was created.

While local variables are stored on the call stack as part of the method frame,
objects are stored in an area of memory called the **heap**. Each time the `new`
operator is used, memory from the heap is dynamically allocated to store the instance
variables defined in the class.

## Variable Declaration and Initialization

As we saw in the previous section, fields are initialized to default values based on their data type.

To review, let's define a new class `Cat` and create two `Cat` instances in the `main` method: 

```java
public class Cat {
    boolean meowing;
    boolean purring;
    String favoriteToy;

    public static void main(String[] args) {
        Cat fluffy = new Cat();
        Cat whiskers = new Cat();
    }

}
```

The variables `meowing` and `purring` are initialized to the default boolean value `false`,
while the variable `favoriteToy` is initialized to the default string value  `null`:

![cat default initialization](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/cat_default_init.png)

However, we may want to initialize a field to a value that is different from the default data type value.
We can do this by assigning a value at the variable declaration.

For example, let's assign `meowing` to have an initial value of `true`, and `favoriteToy`
to have an initial value of `"catnip ball"`.  Since `purring` is not assigned a value, it
will be initialized to the default boolean value `false`.

```java
public class Cat {
    
    boolean meowing = true;
    boolean purring;
    String favoriteToy = "catnip ball";

    public static void main(String[] args) {
        Cat fluffy = new Cat();
        Cat whiskers = new Cat();
    }

}
```

Now when a `Cat` instance is created, the variable `meowing` is initialized to `true`,
`purring` is initialized to `false`, and `favoriteToy` is initialized  to `"catnip ball"`:

![cat field initializers](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/cat_field_initialize.png)

Assigning an initial value as part of the variable declaration means every
`Cat` instance will have the same initial set of values.

In a later lesson, we will see how to create constructor methods to initialize
a class instance using values passed as method parameters.  Constructors let us
initialize different objects with different values.

## Comprehension Check


Assume the following `Bike` class:

```java
public class Bike {
    String color;
    int height;
    int wheels = 2;

    public static void main(String[] args) {
        Bike mountainBike = new Bike();
        Bike touringBike = new Bike();
        Bike tricycle = new Bike();
    }
}
```


<details>
    <summary>How many <code>Bike</code> instances are created when the <code>main</code> method executes?</summary>

  <p>Answer: 3.  The <code>new</code> operator is used 3 times to create 3 <code>Bike</code> instances.</p>

</details>

<br>


<details>
    <summary>What is the initial value assigned to the <code>color</code> field?</summary>

  <p>Answer: <code>null</code></p>
  <p>The default value for <code>String</code> is <code>null</code>.</p>

</details>

<br>


<details>
    <summary>What is the initial value assigned to the <code>height</code> field?</summary>

  <p>Answer: <code>0</code></p>
  <p>The default value for <code>int</code> is <code>0</code>.</p>

</details>

<br>

<details>
    <summary>What is the initial value assigned to the <code>wheels</code> field?</summary>

  <p>Answer: <code>2</code></p>
  <p>The variable declaration defines an initial value <code>int wheels = 2;</code></p>

</details>

<br>

<details>
    <summary>What kind of value is stored in the variables
             <code>mountainBike</code>, <code>touringBike</code>, and <code>tricycle</code>?
    </summary>

  <p>
  Answer: Each variable stores the memory address of a <code>Bike</code> class instance.
  The visualization uses an arrow to point to the object referenced by the variable.
  </p>
  <img src="https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/bike_objects.png">

</details>

<br>



## Conclusion

```java
Dog bigDog = new Dog(); 
```

We create an instance of a class by using the `new` operator followed by a call to a class constructor.
The `new` operator allocates memory to store the fields (instance variables),
while the constructor initializes the field values.  

By default, variables are initialized based on their data type.
However, a different initial value can be assigned at the variable declaration.

A variable declared with a class type can be assigned to store the address of a newly created object.

## Resources

- [Creating Objects in Java](https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html)
