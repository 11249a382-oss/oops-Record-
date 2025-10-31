# oops-lab programs 1-10:

***1. Illustrate class & objects***

**Aim:**
To demonstrate creation of class, objects, data members, and member functions in C++.

**Algorithm:**

1.Start the program and include <iostream> and <string>.
2.Define a class Car with data members brand, model, and yeaar.
3.Define a member function displayInfo() to display object data.
4.In main(), create an object of Car and assign values.
5.Call displayInfo() to print the details.
6.Stop the program.

**Program:**

#include <iostream>
#include <string>
using namespace std;
class Car {
public:
    string brand, model;
    int year;
    void displayInfo() {
        cout << "Brand: " << brand << ", Model: " << model << ", Year: " << year << endl;
    }
};
int main() {
    Car c;
    c.brand = "Toyota";
    c.model = "Camry";
    c.year = 2023;
    c.displayInfo();
    return 0;
}

**Output:**

Brand: Toyota, Model: Camry, Year: 2023

**Result:**

Program successfully creates a class and object, assigns values, and displays them using a member function.


***2. Implement member function defined inside and outside the class***

**Aim:**
To define member functions both inside and outside the class using the scope resolution operator.

**Algorithm:**

1.Start program; include <iostream>.
2.Define a class Car with data member brand.
3.Define one member function inside the class and one outside using ::.
4.In main(), create object, set data, and call both functions.
5.Display the output and end program.

**Program:**

#include <iostream>
using namespace std;
class Car {
public:
    string brand;
    void inside() { cout << "Inside Function: " << brand << endl; }
    void outside();
};
void Car::outside() { cout << "Outside Function: " << brand << endl; }
int main() {
    Car c;
    c.brand = "Honda";
    c.inside();
    c.outside();
    return 0;
}

**Output:**

Inside Function: Honda
Outside Function: Honda

**Result:**
Program demonstrates defining and calling member functions both inside and outside the class.


***3. Demonstrate function overloading applied to member functions***

**Aim:**
To show how function overloading works for member functions with different parameter lists.

**Algorithm:**

1.Include <iostream> and <string>.
2.Define a class Calculator with overloaded functions add() having different parameters.
3.In main(), create an object and call each overloaded version.
4.Display results for integers and strings.
5.End the program.

**Program:**

#include <iostream>
#include <string>
using namespace std;
class Calculator {
public:
    int add(int a,int b){return a+b;}
    int add(int a,int b,int c){return a+b+c;}
    string add(string a,string b){return a+b;}
};
int main() {
    Calculator c;
    cout << c.add(5,10) << endl;
    cout << c.add(2,3,4) << endl;
    cout << c.add("Hello ","World") << endl;
}

**Output:**

15
9
Hello World

**Result:**
Program successfully shows multiple functions with the same name working with different parameters.


***4. Implement passing object as function argument and return object***

**Aim:**
To demonstrate passing objects to functions and returning objects from functions.

**Algorithm:**

1.Define class MyClass with one data member value.
2.Create a function that takes object by value, modifies it, and prints data.
3.Create another that returns an object from a function.
4.In main(), call both functions and observe behavior.
5.End program.

**Program:**

#include <iostream>
using namespace std;
class MyClass {
public:
    int value;
    MyClass(int v=0){value=v;}
};
void show(MyClass obj){cout<<"Value: "<<obj.value<<endl;}
MyClass getObj(){MyClass temp(50);return temp;}
int main(){
    MyClass m(10);
    show(m);
    MyClass n = getObj();
    show(n);
    return 0;
}

**Output:**

Value: 10
Value: 50

**Result:**
Program demonstrates how objects can be passed and returned through functions.


***5. Demonstrate use of constructors and destructor***

**Aim:**
To illustrate the working of default, parameterized, and copy constructors, and destructor.

**Algorithm:**

1.Define class MyClass with data member value.
2.Write default, parameterized, and copy constructors.
3.Add a destructor to print a message when object is destroyed.
4.Create objects of different constructors in main().
5.Observe constructor and destructor call order.
6.End program.

**Program:**

#include <iostream>
using namespace std;
class MyClass {
public:
    int value;
    MyClass(){value=0;cout<<"Default Constructor\n";}
    MyClass(int v){value=v;cout<<"Parameterized Constructor\n";}
    MyClass(const MyClass& m){value=m.value;cout<<"Copy Constructor\n";}
    ~MyClass(){cout<<"Destructor for value "<<value<<"\n";}
};
int main(){
    MyClass a;
    MyClass b(10);
    MyClass c=b;
    return 0;
}

**output:**

Default Constructor
Parameterized Constructor
Copy Constructor
Destructor for value 10
Destructor for value 10
Destructor for value 0

**Result:**
Constructors and destructor execute automatically, showing object creation and destruction order.


***6. Illustrate static data member and static member function***

**Aim:**
To demonstrate static members shared by all objects of a class.

**Algorithm:**

1.Define class Car with static data member carCount.
2.Increment it inside the constructor.
3.Define static function getCount() returning total objects.
4.Create multiple objects in main().
5.Display count using class name.
6.End program.

**Program:**

#include <iostream>
using namespace std;
class Car {
public:
    static int carCount;
    Car(){carCount++;}
    static int getCount(){return carCount;}
};
int Car::carCount=0;
int main(){
    Car a,b,c;
    cout<<"Total Cars: "<<Car::getCount()<<endl;
}

**Output:**

Total Cars: 3

**Result:**
Static member carCount is shared among all objects and tracks total count successfully.



***7. Illustrate array of objects***

**Aim:**
To use an array of class objects for storing multiple records.

**Algorithm:**

1.Define class Student with name and roll number.
2.Create an array of 3 student objects.
3.Assign data to each object.
4.Use a loop to display all data using member function.
5.End program.

**Program:**

#include <iostream>
#include <string>
using namespace std;
class Student {
public:
    string name;
    int roll;
    void display(){cout<<"Name: "<<name<<", Roll: "<<roll<<endl;}
};
int main(){
    Student s[3];
    s[0].name="Alice"; s[0].roll=101;
    s[1].name="Bob"; s[1].roll=102;
    s[2].name="Charlie"; s[2].roll=103;
    for(int i=0;i<3;i++) s[i].display();
    return 0;
}

**Output:**

Name: Alice, Roll: 101
Name: Bob, Roll: 102
Name: Charlie, Roll: 103


**Result:**
Program successfully uses an array of objects to store and display multiple records.


***8. Illustrate memory management operator***

**Aim:**
To demonstrate dynamic memory allocation using new and delete.

**Algorithm:**

1.Include <iostream>.
2.Define a class Item with one integer data member.
3.Create an object dynamically using new.
4.Access data members using pointer and display value.
5.Free memory using delete.
6.End program.

**Program:**

#include <iostream>
using namespace std;
class Item {
public:
    int value;
    Item(int v){value=v;}
};
int main(){
    Item* obj = new Item(25);
    cout<<"Value: "<<obj->value<<endl;
    delete obj;
    return 0;
}

**Output:**

Value: 25

**Result:**
Program allocates and deallocates memory dynamically using new and delete.


***9. Illustrate friend class and friend function***

**Aim:**
To access private data of a class using a friend function and friend class.

**Algorithm:**

1.Define class A with private data x.
2.Declare a friend function and a friend class inside class A.
3.Define friend function outside the class to access private members.
4.Use friend class method to modify data.
5.In main(), create object of A and call both.
6.End program.

**Program:**

#include <iostream>
using namespace std;
class A {
    int x;
public:
    A(int v){x=v;}
    friend void show(A &a);
    friend class B;
};
void show(A &a){cout<<"x="<<a.x<<endl;}
class B {
public:
    void change(A &a){a.x+=10;}
};
int main(){
    A obj(5);
    show(obj);
    B b;
    b.change(obj);
    show(obj);
}

**Output:**

x=5
x=15

**Result:**
Friend function and friend class can directly access private members of another class.


***10. Implement unary operator overloading***

**Aim:**
To overload a unary operator such as ++ for a user-defined class.

**Algorithm:**

1.Create a class Counter with integer data member.
2.Define constructor to initialize value.
3.Overload prefix ++ operator using operator++().
4.Increment the data and return updated object.
5.In main(), create object, apply ++, and display result.
6.End program.

**Program:**

#include <iostream>
using namespace std;
class Counter {
    int value;
public:
    Counter(int v=0){value=v;}
    void operator++(){++value;}
    void display(){cout<<"Value: "<<value<<endl;}
};
int main(){
    Counter c(5);
    ++c;
    c.display();
    return 0;
}

**Output:**

Value: 6

**Result:**
Program successfully overloads the unary ++ operator for a user-defined type.

