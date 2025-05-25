.
# Object Oriented Programming Notes - Last Minute Revision :white_check_mark: 

Here we have last minute revision notes of object oriented programming language. These questions will familiarize you with the most important object-oriented programming concepts and help you ace your job interviews :raised_hands:


---


## Most Asked OOPS Interview Questions

### 1: What is OBJECT-ORIENTED PROGRAMMING?

**Answer**: Object-oriented programming is a programming paradigm built on the concept of objects.

In Other Words, it is an approach to problem-solving where all computations are carried out using objects.

---

### 2: Class and Object

**Answer**: 

**Class**: A class is the building block that leads to Object-Oriented programming. It is a user-defined datatype, which holds its own data members and member functions, which can be accessed and used by creating an instance of that class.

**Object**: An Object is an instance of a Class. When a class is defined, no memory is allocated but when it is instantiated (i.e. an object is created) memory is allocated.

```c++
#include <bits/stdc++.h>
using namespace std;
class Person{
	// Access specifier
	public:

	// Data Members
	string name;

	// Member Functions()
	void printname(){
	   cout << "Person name is: " << name;
	}
};

int main() {

	// Declare an object of class Person
	Person obj1;

	// accessing data member
	obj1.name = "Thanos";

	// accessing member function
	obj1.printname();
	return 0;
}

```

**Output**
> Person name is: Thanos

---

### 3: Constructor

**Answer**: 

- Constructors are special class members which are called by the compiler every time an object of that class is instantiated.

- Constructors have the same name as the class and may be defined inside or outside the class definition.

There are 3 types of constructors:

    1. Default constructors
    2. Parameterized constructors
    3. Copy constructors

1. **Default Constructor**: Default constructor is the constructor which doesn’t take any argument. It has no parameters.

2. **Parameterized Constructor**: A constructor is called Parameterized Constructor when it accepts a specific number of parameters.

3. **Copy Constructor**: A copy constructor is a member function which initializes an object using another object of the same class.

#### Characteristics of the constructor:

- Constructor has the same name as the class itself.
- Constructors don’t have a return type.
- A constructor is automatically called when an object is created.
- It must be placed in the public section of class.
- If we do not specify a constructor, C++ compiler generates a default constructor for object (expects no parameters and has an empty body).
- Constructors can be overloaded.
- Constructor cannot be declared virtual.

```C++
#include <bits/stdc++.h>
using namespace std;

class student
{
     string name;
     public:
       int age;
       bool gender;
    
    // Default Constructor
    student(){
      cout<<"Default Constructor"<<endl;
    }
    
    // Parameterised Constructor
    student(string s, int a, int b)  
    {
       name = s;
       age = a;
       gender = b;
       cout <<"parameterised constructor"<<endl;
    }

    // Copy Constructor
    student (student &p){              
      name = p.name;
      age = p.age;
      gender = p.gender;
      cout<<"copy constructer"<<endl;
    }

    void printinfo()
    {
        cout << "Name = ";
        cout << name << endl;
        cout << "Age = ";
        cout << age << endl;
        cout << "Gender = ";
        cout << gender << endl;
        cout << "\n";
    }
};

int main()
{   
    // Default Constructer Call
    student s1;
    s1.printinfo();
    // Parameterised Constructer Call
    student s2("sumeet", 20, 1);
    s2.printinfo();
    // Copy Constructor Call
    student s3(s2);
    s3.printinfo();

    return 0;
}

```

**Output**
>Default Constructor\
Name = \
Age = 2 \
Gender = 0 

>parameterised constructor \
Name = sumeet \
Age = 20 \
Gender = 1 

>copy constructer \
Name = sumeet \
Age = 20 \
Gender = 1 

---


### 4: Destructor

**Answer**: 

- A destructor is also a special member function as a constructor. Destructor destroys the class objects created by the constructor. 

- Destructor has the same name as their class name preceded by a tiled (~) symbol.

#### Characteristics of the constructor:

- Destructor is invoked automatically by the compiler when its corresponding constructor goes out of scope and releases the memory space that is no longer required by the program.
- Destructor neither requires any argument nor returns any value therefore it cannot be overloaded.
- Destructor cannot be declared as static and const.
- Destructor should be declared in the public section of the program.
- When is a Destructor Most Useful?
- A destructor is most useful in the following scenarios:

- Releasing Dynamically Allocated Memory:
  If a class allocates memory on the heap using new, the destructor ensures that the memory is properly released using delete.
  Closing File Handles or Network Connections:
 If a class opens a file or establishes a network connection, the destructor ensures that these resources are closed when the object is destroyed.
- Avoiding Resource Leaks:
  Destructors help prevent resource leaks by ensuring that all resources are released when the object is no longer needed.
- RAII (Resource Acquisition Is Initialization):
  Destructors are a key part of the RAII design pattern, where resource management is tied to the lifetime of an object.

```C++
#include <iostream>
using namespace std;

int count = 0 ;

class num{
public:
    num(){ // Constructor
        count++;
        cout << "This is the time when constructor is called for object number" << count << endl;
    }

    ~num(){ // Destructor
        cout << "This is the time when my destructor is called for object number" << count << endl;
        count--;
    }
};

```

---


### 5: The main features of OOPs?

**Answer**: The main four pillar of oops are given below.

![pillar of OPPS](/assets/images/pillar_of_OOPS.png)


---

### 6: Inheritance

**Answer**: Inheritance is one of the most important features of Object-Oriented Programming. The capability of a class to derive properties and characteristics from another class is called Inheritance.


**Real Life Example**

<img src="/assets/images/inheritance.png" width="400" height="400">

There are 5 types of Inheritance:

    1. Single Inheritance
    2. Multiple Inheritance
    3. Multilevel Inheritance
    4. Hierarchical Inheritance.
    5. Hybrid Inheritance.

1. **Single Inheritance**: When a subclass(child) is inherited from a base class is called single inheritance.

```C++
#include<bits/stdc++.h>
using namespace std;

class A{
    public:
      void funcA(){
        cout<<"Base Class"<<endl;
      }
};
// Class B is inherited from Class A
class B : public A{
    public:
      void funcB(){
        cout<<"Inherited from class A"<<endl;
      }
};

int main(){
    B obj;
    // As Class B inherited properties of A.
    // We can access funcA from class B object also.
    obj.funcA();
    obj.funcB();
    return 0;
}
```
**Output**
> Base Class \
Inherited from class A



2. **Multiple Inheritance**: when one subclass is inherited from more than one base class is called multiple inheritance.

```C++
#include<bits/stdc++.h>
using namespace std;

class A{
    public:
      void func(){
        cout<<"Base class A"<<endl;
      }
};

class B{
    public:
      void func(){
        cout<<"Base class B"<<endl;
      }
};
// Class C inherits both Class A and B
class C : public A, public B{

    public:
      void func(){
        cout<<"Inherited from class C"<<endl;
      }
};

int main()
{
    C obj;
    obj.A :: func();  // resolving ambiguity
    obj.B :: func();
    obj.func();
    return 0;
}
```

**Output**
>Base class A \
Base class B \
Inherited from class A and B


3. **Multilevel Inheritance**: In this type of inheritance, a derived class is created from another derived class.

```C++
#include<bits/stdc++.h>
using namespace std;

class A{
     public:
       void funcA(){
         cout<<"Base class A"<<endl;
       }
};
// Class B inherited from Class A
class B : public A{
     public:
       void funcB() {
         cout<<"Inherted from class A"<<endl;
       }
};
// Class C inherited from Class B
class C : public B{
     public:
       void func() {
         cout<<"Inherited from class B"<<endl;
       }
};

int main()
{
    C obj;
    obj.funcA();
    obj.funcB();
    obj.func();
    return 0;
}
```
**Output**
> Base class A \
Inherted from class A \
Inherited from class B



4. **Hierarchical Inheritance**: In this type of inheritance, more than one subclass is inherited from a single base class.

```C++
#include<bits/stdc++.h>
using namespace std;

class A{
    public:
      void funcA(){
        cout<<"Base class A"<<endl;
      }
};
// Class B inherited from Class A
class B : public A{
    public:
      void funcB(){
        cout<<"Inherited from class A"<<endl;
      }
};
// Class C also inherited from Class A
class C : public A{
    public:
      void funcC(){
        cout<<"Inherited also from class A"<<endl;
      }
};

int main()
{
    C obj;
    obj.funcA();
    obj.funcC();
    
    B obj2;
    obj2.funcA();
    obj2.funcB();
    return 0;
}
```

**Output**
> Base class A \
Inherited also from class A \
Base class A \
Inherited from class A



5. **Hybrid Inheritance**: The inheritance in which the derivation of a class involves more than one form of any inheritance is called hybrid inheritance. Basically C++ hybrid inheritance is combination of two or more types of inheritance. It can also be called multi path inheritance.

```C++
#include <iostream>
using namespace std;

class A
{
 	public:
 	  int x;
};
class B : public A
{
 	public:
	  //constructor to initialize x in base class A
 	  B()      
 	  {
 	     x = 10;
 	  }
};
class C
 {
 	public:
 	  int y;
	  
	  //constructor to initialize y
 	  C()   
 	  {
 	      y = 4;
          }
};

//D is derived from class B and class C
class D : public B, public C   
{
 	public:
 	  void sum()
 	  {
 	      cout << "Sum = " << x + y;
 	  }
};

int main()
{	
	//object of derived class D
        D obj1;          
 	obj1.sum();
 	return 0;
}               	
```

**Output**
> Sum = 14


---


### 7: Encapsulation

**Answer**: 

- In normal term encapsulation is defined as wrapping up of data and information under a single unit.
- Encapsulation define as binding together the data and function that manipulates them.

**Advantages**

- Increased security of data.
- Encapsulation allows access to a level without revealing the complex details below that level.
- It reduces human errors.
- Makes the application easier to understand.

**Real Life Example**

<img src="/assets/images/encapsulation.png" width="400" height="400">

```C++
#include<iostream>
using namespace std;

class Encapsulation
{
	private:
	  // data hidden from outside world
	  int x;
		
	public:
	  // function to set value of
	  // variable x
	  void set(int a)
	  {
		x =a;
	  }
		
	  // function to return value of
	  // variable x
	  int get()
	  {
		return x;
	  }
};
int main()
{
	Encapsulation obj;
	
	obj.set(5);
	
	cout<<obj.get();
	return 0;
}
```

**Output**
> 5

---

### 8: Abstraction

**Answer**: 

- Data Abstraction is one of the most essential and important feature of Object Oriented Programming in c++.
- Abstraction means displays only the relevant attributes of objects and hides the unnecessary details like the background details and implementation.

**Advantages**

- Helps user to avoid writing the low level code.
- Avoids code duplication and increases reusability.
- Helps to increase security of an application or program as only required details are provided to the user.

**Real Life Example**

<img src="/assets/images/abstraction.png" width="400" height="400">


```C++
#include <iostream>
using namespace std;

class implementAbstraction {
private:
   int a, b;

public:
   // method to set values of
   // private members
   void set(int x, int y)
   {
	a = x;
	b = y;
   }

   void display()
   {
	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
   }
};

int main()
{
	implementAbstraction obj;
	obj.set(10, 20);
	obj.display();
	return 0;
}
```

**Output**
> a = 10 \
b = 20

---

### 9: Polymorphism

**Answer**: 

- The word polymorphism means having many forms. Polymorphism occurs when there is a hierarchical mode inheritance.
- C++ polymorphism means that a call to a member function will cause a different function to be executed depending on the type of object that invokes the function.


**Advantages**

Polymorphism in C++ allows us to reuse code by creating one function that’s usable for multiple uses. We can also make operators polymorphic and use them to add not only numbers but also combine strings. This saves time and allows for a more streamlined program.

**Real Life Example**

<img src="/assets/images/polymorphism.png" width="400" height="400">


There are 2 types of Polymorphism:

    1. Compile time Polymorphism
    2. Run time Polymorphism
   
1. **Compile time Polymorphism**: Compile-time polymorphism is a polymorphism that is, the function call is resolved during the compilation process.

We can achieve Compile-time polymorphism by two ways:

1. **Function overloading**

- When there are multiple functions with the same name but take different parameters as an arguments then these function are said to be overloaded.
- Functions can be overloaded by changing the number of arguments or and changing the type of arguments.


```C++
#include<bits/stdc++.h>
using namespace std;

class Simple
{
  public :
    void fun()
    {
        cout<<"function with no argument"<<endl;
    }

    void fun(int x)
    {
        cout <<"function with int argument"<<endl;
    }
    void fun(double x)
    {
        cout<<"function with double argument"<<endl;
    }
};

int main()
{
    Simple obj;
    obj.fun();
    obj.fun(4);
    obj.fun(4.5);
    return 0;
}
```

**Output**
> function with no argument \
function with int argument \
function with double argument


2. **Operator Overloading**: C++ also provides the option to overload operators So a single operator ‘+’, when placed between integer operands, adds them and when placed between string operands, concatenates them.

```C++
#include<iostream>
using namespace std;

class Complex {
private:
   int real, imag;
public:
   Complex(int r = 0, int i = 0) {real = r; imag = i;}
	
   // This is automatically called when '+' is used with
   // between two Complex objects
   Complex operator + (Complex const &obj) {
	   Complex res;
	   res.real = real + obj.real;
	   res.imag = imag + obj.imag;
	   return res;
   }
   void print() { cout << real << " + i" << imag << '\n'; }
};

int main()
{
	Complex c1(10, 5), c2(2, 4);
	Complex c3 = c1 + c2;
	c3.print();
}
```

**Output**
> 12 + i9


2. Runtime Polymorphism

- Runtime polymorphism is also known as dynamic polymorphism or late binding. In runtime polymorphism, the function call is resolved at run time.
- This type of polymorphism is achieved by Function Overriding or Virtual function.

### **Virtual Function in C++**
A **virtual function** is a member function in a base class that you can override in a derived class. It allows **runtime polymorphism**, meaning the function that gets called is determined at runtime based on the type of the object being pointed to, not the type of the pointer.

#### **Key Points about Virtual Functions**
1. Declared using the `virtual` keyword in the base class.
2. Allows overriding in derived classes.
3. Enables **dynamic dispatch** (runtime decision of which function to call).
4. If a virtual function is not overridden in the derived class, the base class version is used.

---

#### **Example of Virtual Function**
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {  // Virtual function
        cout << "Base class display function" << endl;
    }
};

class Derived : public Base {
public:
    void display() override {  // Override the base class function
        cout << "Derived class display function" << endl;
    }
};

int main() {
    Base* basePtr;  // Pointer of type Base
    Derived derivedObj;

    basePtr = &derivedObj;
    basePtr->display();  // Calls Derived's display() due to dynamic dispatch

    return 0;
}
```

**Output**:
```plaintext
Derived class display function
```

**Explanation**:
- The `display` function in the base class is declared as `virtual`.
- When `basePtr` points to a `Derived` object, the `Derived` class's `display` function is called at runtime.

---

### **Pure Virtual Function in C++**
A **pure virtual function** is a virtual function that has no implementation in the base class. It is declared by assigning `= 0` to the function declaration. A class containing at least one pure virtual function is called an **abstract class**.

#### **Key Points about Pure Virtual Functions**
1. Declared using `= 0` in the base class.
2. Forces derived classes to provide an implementation for the function.
3. Abstract classes cannot be instantiated directly.
4. Used to define interfaces or enforce a contract for derived classes.

---

#### **Example of Pure Virtual Function**
```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void draw() = 0;  // Pure virtual function
    virtual ~Shape() {}       // Virtual destructor
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing a Circle" << endl;
    }
};

class Rectangle : public Shape {
public:
    void draw() override {
        cout << "Drawing a Rectangle" << endl;
    }
};

int main() {
    Shape* shape1 = new Circle();
    Shape* shape2 = new Rectangle();

    shape1->draw();  // Calls Circle's draw()
    shape2->draw();  // Calls Rectangle's draw()

    delete shape1;
    delete shape2;

    return 0;
}
```

**Output**:
```plaintext
Drawing a Circle
Drawing a Rectangle
```

**Explanation**:
- The `Shape` class contains a pure virtual function `draw()`, making it an abstract class.
- The `Circle` and `Rectangle` classes override the `draw()` function.
- The `Shape` class cannot be instantiated directly, but pointers to `Shape` can point to derived class objects.

---

### **Key Differences Between Virtual and Pure Virtual Functions**

| **Aspect**                | **Virtual Function**                                   | **Pure Virtual Function**                              |
|---------------------------|-------------------------------------------------------|-------------------------------------------------------|
| **Definition**            | A function with a default implementation in the base class. | A function with no implementation in the base class (declared as `= 0`). |
| **Purpose**               | Allows overriding but provides a default implementation. | Forces derived classes to implement the function.     |
| **Base Class Instantiation** | The base class can be instantiated if it has no pure virtual functions. | The base class becomes abstract and cannot be instantiated. |
| **Usage**                 | Used when some default behavior is needed in the base class. | Used to define interfaces or enforce implementation in derived classes. |

---

### **When to Use Virtual vs Pure Virtual Functions**
- **Virtual Function**:
  - Use when you want to provide a default implementation in the base class but allow derived classes to override it.
  - Example: A `print()` function in a base class that prints generic information but can be overridden for specific details in derived classes.

- **Pure Virtual Function**:
  - Use when you want to enforce that all derived classes must implement the function.
  - Example: A `draw()` function in a `Shape` class that must be implemented by all specific shapes like `Circle` or `Rectangle`.

---


### 10: Abstract Class

**Answer**

- Sometimes implementation of all function cannot be provided in a base class because we don’t know the implementation. Such a class is called abstract class.
Example, let Shape be a base class. We cannot provide implementation of function draw() in Shape, but we know every derived class must have implementation of draw().
- Class is Abstract, if we have atleast one pure virtual function.

---

### 11: Pure Virtual Function

**Answer**

- Also called Absract function.
- A pure virtual function in c++, is a virtual function for which we can have implementation, but we must override that function in the derived class, otherwise the derived class will also become abstract class.

```
class X
{
	public:
	virtual void show() = 0; // pure virtual func
};
```

---

### 12: Friend Class & Friend Function

#### Friend Class

**Answer**

- A friend class can access private and protected members of other class in which it is declared as friend.
- It is sometimes useful to allow a particular class to access private members of other class.


```C++
#include<iostream>
using namespace std;

class A{
   int x;
   public:
			
    A(){
       x=10;
    }
    friend class B; //friend class
};

class B{
    public:
      void display(A &t){
	 cout<<endl<<"The value of x="<<t.x;
      }
};

int main(){
	A _a;
	B _b;
	_b.display(_a);
	return 0;
}
```

**Output**
>  The value of x=10


### **Friend Class and Friend Function in C++**

In C++, the **friend** keyword allows a class or a function to access the private and protected members of another class. This is useful when two or more classes or functions need to work closely together and require access to each other's private data.

---

### **1. Friend Function**

A **friend function** is a function that is not a member of a class but has access to its private and protected members. It is declared in the class using the `friend` keyword.

#### **Key Points**
- A friend function is not a member of the class but can access its private and protected members.
- It is declared inside the class but defined outside.
- It can be a normal function or a member function of another class.

---

#### **Example of Friend Function**
```cpp
#include <iostream>
using namespace std;

class Box {
private:
    double width;

public:
    Box(double w) : width(w) {}

    // Declare a friend function
    friend void printWidth(Box b);
};

// Friend function definition
void printWidth(Box b) {
    cout << "Width of the box: " << b.width << endl;  // Access private member
}

int main() {
    Box b(10.5);
    printWidth(b);  // Call the friend function
    return 0;
}
```

**Output**:
```plaintext
Width of the box: 10.5
```

**Explanation**:
- The `printWidth` function is declared as a friend of the `Box` class.
- It can access the private member `width` of the `Box` class.

---

### **2. Friend Class**

A **friend class** is a class that is allowed to access the private and protected members of another class. This is useful when two classes need to work closely together.

#### **Key Points**
- A friend class is declared using the `friend` keyword inside the class whose private members it needs to access.
- Friendship is **not reciprocal**: If `ClassA` is a friend of `ClassB`, `ClassB` does not automatically become a friend of `ClassA`.

---

#### **Example of Friend Class**
```cpp
#include <iostream>
using namespace std;

class Engine {
private:
    int horsepower;

public:
    Engine(int hp) : horsepower(hp) {}

    // Declare Car as a friend class
    friend class Car;
};

class Car {
public:
    void showEngineDetails(Engine e) {
        cout << "Engine horsepower: " << e.horsepower << endl;  // Access private member
    }
};

int main() {
    Engine e(300);
    Car c;
    c.showEngineDetails(e);  // Car can access Engine's private members
    return 0;
}
```

**Output**:
```plaintext
Engine horsepower: 300
```

**Explanation**:
- The `Car` class is declared as a friend of the `Engine` class.
- The `Car` class can access the private member `horsepower` of the `Engine` class.

---

### **3. Important Concepts and Use Cases**

#### **When to Use Friend Functions and Classes**
- **Tightly Coupled Classes**:
  - When two classes need to work closely together and share private data.
  - Example: A `Car` class accessing private details of an `Engine` class.
- **Operator Overloading**:
  - Friend functions are often used to overload operators that require access to private members of a class.
  - Example: Overloading the `<<` or `>>` operators for input/output.

---

#### **Friend Function for Operator Overloading**
```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    double real, imag;

public:
    Complex(double r, double i) : real(r), imag(i) {}

    // Declare friend function for overloading <<
    friend ostream& operator<<(ostream& out, const Complex& c);
};

// Friend function definition
ostream& operator<<(ostream& out, const Complex& c) {
    out << c.real << " + " << c.imag << "i";
    return out;
}

int main() {
    Complex c(3.5, 2.5);
    cout << c << endl;  // Calls the friend function
    return 0;
}
```

**Output**:
```plaintext
3.5 + 2.5i
```

**Explanation**:
- The `operator<<` function is declared as a friend of the `Complex` class.
- It can access the private members `real` and `imag` of the `Complex` class.

---

#### **Friendship is Not Inherited**
- If `ClassA` is a friend of `ClassB`, and `ClassB` is a base class of `ClassC`, `ClassA` does not automatically become a friend of `ClassC`.

---

#### **Friendship is Not Reciprocal**
- If `ClassA` declares `ClassB` as a friend, `ClassB` does not automatically declare `ClassA` as a friend.

---

#### **Friendship is Not Transitive**
- If `ClassA` is a friend of `ClassB`, and `ClassB` is a friend of `ClassC`, `ClassA` is not automatically a friend of `ClassC`.

---

### **4. Advantages and Disadvantages**

#### **Advantages**
1. **Access Control**:
   - Allows controlled access to private members without exposing them to the entire program.
2. **Flexibility**:
   - Useful for operator overloading and tightly coupled classes.

#### **Disadvantages**
1. **Breaks Encapsulation**:
   - Friendship violates the principle of encapsulation by exposing private members.
2. **Tight Coupling**:
   - Makes classes tightly coupled, which can reduce modularity and make the code harder to maintain.

---

### **5. Summary**

| **Aspect**              | **Friend Function**                                   | **Friend Class**                                   |
|-------------------------|------------------------------------------------------|--------------------------------------------------|
| **Definition**          | A function that can access private/protected members of a class. | A class that can access private/protected members of another class. |
| **Declaration**         | Declared using `friend` inside the class.            | Declared using `friend` inside the class.        |
| **Use Case**            | Operator overloading, accessing private data.        | Tightly coupled classes that need to share data. |
| **Scope**               | Only the specific function is granted access.        | All member functions of the friend class are granted access. |

---

Let me know if you'd like further clarification or additional examples!---

### 13: Access Modifiers

- **Private** – The access level of a private modifier is only within the class. It cannot be accessed from outside the class.
- **Default** – The access level of a default modifier is only within the package. It cannot be accessed from outside the package. If you do not specify any access level, it will be the default.
- **Protected** – The access level of a protected modifier is within the package and outside the package through child class. If you do not make the child class, it cannot be accessed from outside the package.
- **Public** – The access level of a public modifier is everywhere. It can be accessed from within the class, outside the class, within the package and outside the package.


---


### **2. What is a Virtual Destructor? How is it different from a Normal Destructor?**

A **virtual destructor** ensures that the destructor of the derived class is called when deleting an object through a base class pointer. Without a virtual destructor, only the base class destructor is called, which can lead to resource leaks if the derived class allocates resources.

---

#### **Example Without Virtual Destructor**
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    ~Base() {  // Normal destructor
        cout << "Base destructor called" << endl;
    }
};

class Derived : public Base {
public:
    ~Derived() {  // Destructor for Derived
        cout << "Derived destructor called" << endl;
    }
};

int main() {
    Base* basePtr = new Derived();  // Base pointer pointing to Derived object
    delete basePtr;  // Only Base destructor is called
    return 0;
}
```

**Output**:
```plaintext
Base destructor called
```

**Problem**:
- The `Derived` destructor is not called, so any resources allocated in the `Derived` class are not released, leading to a **resource leak**.

---

#### **Example With Virtual Destructor**
```cpp
class Base {
public:
    virtual ~Base() {  // Virtual destructor
        cout << "Base destructor called" << endl;
    }
};

class Derived : public Base {
public:
    ~Derived() {
        cout << "Derived destructor called" << endl;
    }
};

int main() {
    Base* basePtr = new Derived();
    delete basePtr;  // Both Derived and Base destructors are called
    return 0;
}
```

**Output**:
```plaintext
Derived destructor called
Base destructor called
```

**Explanation**:
- The `virtual` keyword ensures that the destructor of the derived class is called first, followed by the base class destructor.
- This prevents resource leaks and ensures proper cleanup.

---

#### **Key Difference**
| **Aspect**              | **Normal Destructor**                              | **Virtual Destructor**                              |
|-------------------------|---------------------------------------------------|---------------------------------------------------|
| **Behavior**            | Only the base class destructor is called when deleting through a base class pointer. | Both the derived and base class destructors are called. |
| **Use Case**            | Use when the class is not intended to be inherited. | Use when the class is intended to be inherited.   |

---

### **3. When is `Shape* shape1 = new Circle();` Useful?**

This kind of code is useful in scenarios where **runtime polymorphism** is required. It allows you to write code that works with objects of different derived classes through a common base class interface.

---

#### **Example Use Case: Drawing Shapes**
Suppose you are building a graphics application where you need to handle different shapes (e.g., `Circle`, `Rectangle`, `Triangle`). Instead of writing separate code for each shape, you can use a common interface (`Shape`) and achieve polymorphism.

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Shape {
public:
    virtual void draw() = 0;  // Pure virtual function
    virtual ~Shape() {}
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing a Circle" << endl;
    }
};

class Rectangle : public Shape {
public:
    void draw() override {
        cout << "Drawing a Rectangle" << endl;
    }
};

int main() {
    vector<Shape*> shapes;  // Store pointers to different shapes

    // Add shapes to the collection
    shapes.push_back(new Circle());
    shapes.push_back(new Rectangle());

    // Draw all shapes
    for (Shape* shape : shapes) {
        shape->draw();  // Calls the appropriate draw() function
    }

    // Clean up
    for (Shape* shape : shapes) {
        delete shape;
    }

    return 0;
}
```

**Output**:
```plaintext
Drawing a Circle
Drawing a Rectangle
```

---

#### **Why is This Useful?**
1. **Flexibility**:
   - You can add new shapes (e.g., `Triangle`) without modifying the existing code. Just create a new class that inherits from `Shape` and implements the `draw()` function.

2. **Code Reusability**:
   - The `draw()` function is called polymorphically, so you don't need to write separate code for each shape.

3. **Real-World Applications**:
   - **Graphics Libraries**: Handling different types of graphical objects (e.g., shapes, buttons, widgets).
   - **Game Development**: Managing different types of game entities (e.g., players, enemies, obstacles).
   - **UI Frameworks**: Managing different UI components (e.g., text boxes, buttons, sliders).

---

### Thanks for Reading 

<img src="/assets/images/save.png" width="600" height="200">

---


