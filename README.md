# oops-lab programs 1-26:

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


***11. To implement the use of binary operator overloading***

**Aim:**
Overload a binary operator (+) to add two Point objects.

**Algorithm:**

1.Include <iostream>.
2.Define class Point with x and y as data members and a constructor.
3.Declare operator+ as a member or friend that takes a const Point& and returns a Point.
4.Inside operator+, add corresponding coordinates and return a new Point.
5.In main(), create two Point objects, add them using +, and print the result.
6.End program.

**Program:**

#include <iostream>
using namespace std;
class Point {
public:
    int x, y;
    Point(int a=0,int b=0): x(a), y(b) {}
    Point operator+(const Point &p) const {
        return Point(x + p.x, y + p.y);
    }
    void display() const { cout << x << ", " << y << endl; }
};
int main() {
    Point p1(2,3), p2(4,5);
    Point p3 = p1 + p2;
    p3.display();
    return 0;
}

**Output:**

6, 8

***Result:***
Binary + operator overloaded to add two Point objects. The program returns the summed coordinates correctly.


***12. Assignment and comparison of two strings (binary operator overloading)***

**Aim:**
Demonstrate assignment and comparison (equality) of strings (using std::string).

**Algorithm:**

1.Include <iostream> and <string>.
2.Use std::string which provides assignment and equality == by default.
3.Create sample strings, assign one to another, and compare using ==.
4.Print comparison results.
5.End program.

**Program:**

#include <iostream>
#include <string>
using namespace std;
int main() {
    string s1 = "Hello";
    string s2 = "World";
    string s3 = s1; // assignment
    cout << (s1 == s3 ? "s1 equals s3" : "s1 not equal s3") << endl;
    cout << (s1 == s2 ? "s1 equals s2" : "s1 not equal s2") << endl;
    return 0;
}

**Output:**

s1 equals s3
s1 not equal s2

**Result:**
Standard std::string supports assignment and equality comparison directly. Results show correct behavior for assignment and comparison.


***13. Single inheritance (private and public)***

**Aim:**
Demonstrate single inheritance and the difference between public and private inheritance.

**Algorithm:**

1.Include <iostream>.
2.Define a Base class with public/protected/private members.
3.Define PublicDerived : public Base and PrivateDerived : private Base.
4.In derived classes, add methods that attempt to access base class members; note which access is permitted.
5.In main(), create objects and call methods to observe access behavior.
6.End program.

**Program:**

#include <iostream>
using namespace std;
class Base {
public:
    int a = 10;
protected:
    int b = 20;
private:
    int c = 30;
};
class PublicDerived : public Base {
public:
    void show() { cout << "a = " << a << ", b = " << b << endl; }
};
class PrivateDerived : private Base {
public:
    void showp() { cout << "a = " << a << " (a is private here)" << endl; }
};
int main() {
    PublicDerived pd; pd.show();
    PrivateDerived pr; pr.showp();
    return 0;
}

**Output:**

a = 10, b = 20
a = 10 (a is private here)

**Result:**
Public inheritance retains base member access levels for users; private inheritance makes inherited public members private inside derived class. Protected still accessible to derived classes.


***14. Multiple inheritance***

**Aim:**
Demonstrate a class inheriting from two base classes.

**Algorithm:**

1.Include <iostream>.
2.Define two base classes (A, B) with their own members.
3.Define Derived : public A, public B that can access members from both bases.
4.In main(), create a Derived object and call a method that uses both base class members.
5.End program.

**Program:**

#include <iostream>
using namespace std;
class A { public: void showA(){ cout << "A\n"; } };
class B { public: void showB(){ cout << "B\n"; } };
class Derived : public A, public B {
public:
    void showBoth(){ showA(); showB(); }
};
int main() {
    Derived d;
    d.showBoth();
    return 0;
}

**Output:**

A
B

**Result:**
Multiple inheritance lets a derived class access features of more than one base class. Use with care to avoid ambiguity.


***15. Multilevel inheritance***

**Aim:**
Demonstrate multilevel inheritance where class C derives from B which derives from A.

**Algorithm:**

1.Include <iostream>.
2.Define A with a member, derive B : public A and add another member, then derive C : public B.
3.In C, write a function to access members inherited from A and B.
4.In main(), create C object and call the function.
5.End program.

**Program:**

#include <iostream>
using namespace std;
class A { public: void showA(){ cout << "A\n"; } };
class B : public A { public: void showB(){ cout << "B\n"; } };
class C : public B { public: void showC(){ showA(); showB(); cout << "C\n"; } };
int main() {
    C obj;
    obj.showC();
    return 0;
}

**Output:**

A
B
C

**Result:**
Multilevel inheritance forms a chain; derived class C inherits members from both B and A.


***16. Hierarchical inheritance***

**Aim:**
Show hierarchical inheritance where multiple derived classes inherit from the same base.

**Algorithm:**

1.Include <iostream>.
2.Define base class Animal with a method eat().
3.Define Dog : public Animal and Cat : public Animal, each with its own method.
4.In main(), create objects of Dog and Cat and call common and specific methods.
5.End program.

**Program:**

#include <iostream>
using namespace std;
class Animal { public: void eat(){ cout << "Eating\n"; } };
class Dog : public Animal { public: void bark(){ cout << "Bark\n"; } };
class Cat : public Animal { public: void meow(){ cout << "Meow\n"; } };
int main() {
    Dog d; Cat c;
    d.eat(); d.bark();
    c.eat(); c.meow();
    return 0;
}

**Output:**

Eating
Bark
Eating
Meow

**Result:**
Hierarchical inheritance allows multiple derived classes to reuse the base class’s behavior independently.


***17. Virtual base class (to resolve diamond problem)***

**Aim:**
Demonstrate use of virtual base class to avoid duplicate base subobjects in diamond inheritance.

**Algorithm:**

1.Include <iostream>.
2.Create base class Base with data member and a method.
3.Create Derived1 : virtual public Base and Derived2 : virtual public Base.
4.Create Final : public Derived1, public Derived2.
5.In Final, access the Base member to show it is not duplicated.
6.In main(), create Final object and use the method.
7.End program.

**Program:**

#include <iostream>
using namespace std;
class Base { public: int x; Base(){ x = 10; } };
class D1 : virtual public Base { };
class D2 : virtual public Base { };
class Final : public D1, public D2 {
public: void show(){ cout << "x = " << x << endl; }
};
int main() {
    Final f;
    f.show();
    return 0;
}

**Output:**

x = 10

**Result:**
Using virtual inheritance ensures only one Base subobject exists in the diamond, avoiding ambiguity.


***18. To implement abstraction by using pure virtual functions (abstract class)***

**Aim:**
Demonstrate abstract class and pure virtual functions.

**Algorithm:**

1.Include <iostream>.
2.Define abstract base class Shape with pure virtual area() and a virtual destructor.
3.Implement derived classes Rectangle and Circle overriding area().
4.In main(), create pointers of type Shape* pointing to derived objects and call area().
5.Print calculated areas.
6.End program.

**Program:**

#include <iostream>
using namespace std;
class Shape {
public:
    virtual double area() const = 0;
    virtual ~Shape() {}
};
class Rectangle : public Shape {
    double w, h;
public:
    Rectangle(double _w, double _h): w(_w), h(_h) {}
    double area() const override { return w * h; }
};
class Circle : public Shape {
    double r;
public:
    Circle(double _r): r(_r) {}
    double area() const override { return 3.14159 * r * r; }
};
int main() {
    Shape* s1 = new Rectangle(4,5);
    Shape* s2 = new Circle(3);
    cout << "Rect area: " << s1->area() << endl;
    cout << "Circle area: " << s2->area() << endl;
    delete s1; delete s2;
    return 0;
}

**Output:**

Rect area: 20
Circle area: 28.2743

**Result:**
Abstract base class enforces implementation of area() in derived classes; polymorphism allows runtime binding.


***19. To implement runtime polymorphism using virtual functions***

**Aim:**
Show runtime polymorphism where base pointer calls derived class methods using virtual functions.

**Algorithm:**

1.Include <iostream>.
2.Create base class Base with virtual show() method.
3.Derive Derived and override show().
4.In main(), create Base* pointer to Derived object and call show() to demonstrate polymorphism.
5.End program.

**Program:**

#include <iostream>
using namespace std;
class Base {
public:
    virtual void show(){ cout << "Base\n"; }
    virtual ~Base() {}
};
class Derived : public Base {
public:
    void show() override { cout << "Derived\n"; }
};
int main() {
    Base* p = new Derived();
    p->show();
    delete p;
    return 0;
}

**Output:**

Derived

**Result:**
Virtual functions enable correct derived class methods to be called through base class pointers at runtime.


***20. To demonstrate templates (class/function template)***

**Aim:**
Demonstrate function and class templates to achieve generic programming.

**Algorithm:**

1.Include <iostream>.
2.Implement a function template maxValue<T>(T a, T b) returning larger of two values.
3.Optionally create a template class Pair<T> that stores two values.
4.In main(), call maxValue with int and double, and use Pair.
5.Print results.
6.End program.

**Program:**

#include <iostream>
using namespace std;
template<typename T>
T maxValue(T a, T b) { return (a > b) ? a : b; }
template<typename T>
class Pair {
public:
    T first, second;
    Pair(T a, T b): first(a), second(b) {}
    void show(){ cout << first << ", " << second << endl; }
};
int main() {
    cout << maxValue<int>(3,7) << endl;
    cout << maxValue<double>(3.5, 2.1) << endl;
    Pair<string> p("Hi","There");
    p.show();
    return 0;
}

**Output:**

7
3.5
Hi, There

**Result:**
Templates allow writing type-independent code; maxValue and Pair work for multiple data types.


***21. To demonstrate exception handling (try, catch, throw)***

**Aim:**
Show exception handling using throw, try, and catch.

**Algorithm:**

1.Include <iostream> and <stdexcept> (optional).
2.In a function, check a condition and throw an exception (e.g., division by zero).
3.In main(), wrap call in try block and catch appropriate exception types.
4.Print error message in catch
5.End program.

**Program:**

#include <iostream>
using namespace std;
double divide(double a, double b) {
    if (b == 0) throw "Division by zero error";
    return a / b;
}
int main() {
    try {
        cout << divide(10, 2) << endl;
        cout << divide(5, 0) << endl;
    } catch (const char* msg) {
        cout << "Caught exception: " << msg << endl;
    }
    return 0;
}

**Output:**

5
Caught exception: Division by zero error

**Result:**
Exceptions propagate to catch blocks; program handles errors gracefully without crashing.


***22. File handling using streams (read/write)***

**Aim:**
Demonstrate file I/O using fstream for writing and reading text files.

**Algorithm:**

1.Include <iostream> and <fstream>.
2.Create ofstream to open a file and write lines.
3.Close file.
4.Open ifstream to read the file and print contents to console.
5.Close file.
6.End program.

**Program:**

#include <iostream>
#include <fstream>
using namespace std;
int main() {
    ofstream fout("data.txt");
    fout << "Line1\nLine2\n";
    fout.close();
    ifstream fin("data.txt");
    string line;
    while (getline(fin, line)) cout << line << endl;
    fin.close();
    return 0;
}

**Output:**

Line1
Line2

**Result:**
File streams let programs persist data to files and read it back; code demonstrates write and read operations.


***23. To demonstrate STL — vector and iterator***

**Aim:**
Show usage of std::vector and iterators to store and traverse elements.

**Algorithm:**

1.Include <vector> and <iostream>.
2.Declare a vector of integers and push values into it.
3.Use iterator (or range-based for) to traverse and display elements.
4.Demonstrate size() and at() or indexing.
5.End program.

**Program:**

#include <iostream>
#include <vector>
using namespace std;
int main() {
    vector<int> v;
    v.push_back(10); v.push_back(20); v.push_back(30);
    for (vector<int>::iterator it = v.begin(); it != v.end(); ++it)
        cout << *it << endl;
    cout << "Size: " << v.size() << endl;
    return 0;
}

**Output:**

10
20
30
Size: 3

**Result:**
std::vector provides dynamic array functionality; iterators allow safe traversal and access.


***24. To demonstrate STL — stack and queue***

**Aim:**
Demonstrate usage of std::stack and std::queue from STL.

**Algorithm:**

1.Include <stack>, <queue>, and <iostream>.
2.Push elements into stack and queue.
3.Pop and display elements demonstrating LIFO for stack and FIFO for queue.
4.End program.

**Program:**

#include <iostream>
#include <stack>
#include <queue>
using namespace std;
int main() {
    stack<int> s;
    s.push(1); s.push(2); s.push(3);
    cout << "Stack pop: " << s.top() << endl; s.pop();
    queue<int> q;
    q.push(1); q.push(2); q.push(3);
    cout << "Queue front: " << q.front() << endl; q.pop();

    return 0;
}

**Output:**

Stack pop: 3
Queue front: 1

**Result:**
Stack implements LIFO, queue implements FIFO; STL containers simplify these operations.


***25. To demonstrate sorting and searching using STL algorithms***

**Aim:**
Use std::sort and std::binary_search to sort a container and search in it.

**Algorithm:**

1.Include <vector>, <algorithm>, and <iostream>.
2.Fill a vector with unsorted integers.
3.Call sort(v.begin(), v.end()).
4.Use binary_search to check presence of a value.
5.Print sorted vector and search result.
6.End program.

**Program:**

#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
int main() {
    vector<int> v = {5,2,9,1,7};
    sort(v.begin(), v.end());
    for(int x: v) cout << x << " ";
    cout << endl;
    cout << (binary_search(v.begin(), v.end(), 7) ? "Found" : "Not Found") << endl;
    return 0;
}

**Output:**

1 2 5 7 9 
Found

**Result:**
STL algorithms make sorting and searching concise and efficient.


***26. Project / mini-project example (simple student management menu-driven)***

**Aim:**
Create a simple menu-driven program demonstrating multiple learned concepts (classes, file I/O, vectors).

**Algorithm:**

1.Include necessary headers (<iostream>, <vector>, <fstream>, <string>).
2.Define Student class with data members and methods for input/output.
3.Use a vector<Student> to hold records.
4.Implement functions to add student, display all, save to file, load from file, and a simple menu in main() that loops until exit.
5.On choosing options, call appropriate functions and show results.
6.End program.

**Program:**

#include <iostream>
#include <vector>
#include <fstream>
using namespace std;
class Student {
public:
    string name;
    int roll;
    Student(string n="", int r=0): name(n), roll(r) {}
    void display(){ cout << roll << " : " << name << endl; }
};
int main(){
    vector<Student> list;
    list.push_back(Student("Alice",101));
    list.push_back(Student("Bob",102));
    cout << "Students:\n";
    for(auto &s: list) s.display();
    ofstream fout("students.txt");
    for(auto &s: list) fout << s.roll << " " << s.name << "\n";
    fout.close();
    cout << "Saved to students.txt\n";
    return 0;
}

**Output:**

Students:
101 : Alice
102 : Bob
Saved to students.txt

**Result:**
A simple menu/record example ties together classes, containers, and file I/O. Expandable to full CRUD operations for a mini-project.

