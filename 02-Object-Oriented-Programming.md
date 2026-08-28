# Object-Oriented Programming (OOP) — Q&A

## Q1. What is the difference between a Class and an Object?
**Real-life example:** "Car" as a concept (has a color, has wheels, can drive, can brake) is the **class** — a blueprint. Your actual Toyota Corolla parked outside, with its specific red color and specific number plate, is an **object** — a real instance built from that blueprint.
**Simple answer:** A class is a blueprint/template that defines what properties (data) and behaviors (functions) something will have. An object is an actual instance created from that class, with real values.
**In code:**
```cpp
class Car {
public:
    string color;
    void drive() { cout << "Driving..."; }
};
Car myCar;              // myCar is an OBJECT of class Car
myCar.color = "Red";
```
**Exam tip:** Multiple objects can be created from one class, each with its own data. "Class = definition, Object = actual thing" is asked in nearly every version of this test.

## Q2. What is Encapsulation?
**Real-life example:** A medicine capsule wraps the actual medicine powder inside a shell — you can't touch the powder directly, you interact with the capsule as a whole. Similarly, an ATM machine hides its internal wiring/logic; you only use the buttons (interface) it exposes.
**Simple answer:** Bundling data (variables) and the functions that operate on that data together into one unit (a class), and restricting direct access to the internal data — usually by making variables `private` and providing `public` functions (getters/setters) to access them safely.
**In code:**
```cpp
class BankAccount {
private:
    double balance;                    // hidden from outside
public:
    void deposit(double amt) { balance += amt; }   // controlled access
    double getBalance() { return balance; }
};
```
**Exam tip:** Encapsulation = **data hiding + bundling**. It protects data from being changed in unexpected/invalid ways from outside the class.

## Q3. What is Abstraction?
**Real-life example:** When you drive a car, you use the steering wheel, accelerator, and brake — you don't need to know how the engine's combustion works internally. That hiding of complex internal details is abstraction.
**Simple answer:** Showing only the necessary/essential features to the user while hiding the complex implementation details.
**Exam tip:** Students often confuse Encapsulation and Abstraction:
- **Encapsulation** = HOW you hide it (wrapping data + restricting access, a mechanism).
- **Abstraction** = WHAT is hidden (hiding complexity, a design concept/goal).
In C++, abstraction is achieved via abstract classes / interfaces; encapsulation via access specifiers (`private`/`public`).

## Q4. What is Inheritance?
**Real-life example:** A child inherits traits from a parent (eye color, family surname) but can also have their own unique traits. In code, a "Child" class can reuse a "Parent" class's properties/functions and add its own.
**Simple answer:** A mechanism where one class (child/derived class) acquires the properties and behaviors of another class (parent/base class), enabling code reuse.
**In code:**
```cpp
class Animal {
public:
    void eat() { cout << "Eating..."; }
};
class Dog : public Animal {     // Dog inherits from Animal
public:
    void bark() { cout << "Barking..."; }
};
Dog d;
d.eat();   // inherited from Animal
d.bark();  // Dog's own
```
**Exam tip:** "is-a" relationship = inheritance (a Dog **is an** Animal).

## Q5. What is Polymorphism?
**Real-life example:** The word "cut" behaves differently depending on context — "cut the cake" vs "cut the grass" vs "cut a deal." Same word (function name), different behavior depending on the situation. Similarly, pressing "play" on a music app, a video app, and a game does different specific things even though the button/action name is the same.
**Simple answer:** "Many forms" — the ability of the same function/operator name to behave differently depending on context. Two types:
- **Compile-time (static) polymorphism:** Function overloading, operator overloading — decided at compile time.
- **Run-time (dynamic) polymorphism:** Function overriding using virtual functions — decided while the program runs.
**Exam tip:** If asked to classify "function overloading" vs "virtual functions/overriding" — overloading is compile-time, overriding is run-time. This distinction is a favorite MCQ.

## Q6. What is a Constructor?
**Real-life example:** When a new SIM card is issued, it automatically comes activated with a default balance — no manual setup step needed. A constructor "sets up" an object automatically the moment it's created.
**Simple answer:** A special function that runs automatically when an object is created, usually used to initialize data. Same name as the class, NO return type.
**In code:**
```cpp
class Student {
public:
    string name;
    Student() { name = "Unknown"; }              // default constructor
    Student(string n) { name = n; }                // parameterized constructor
};
Student s1;              // calls default constructor
Student s2("Adnan");     // calls parameterized constructor
```
**Exam tip:** Constructors have NO return type — not even `void`. This is a common trick question (asking "what does the constructor return?" — answer: nothing, not even void).

## Q7. What is a Copy Constructor?
**Real-life example:** Photocopying an ID card to create a near-identical second card, using the original as the template.
**Simple answer:** A constructor that creates a new object as a copy of an existing object of the same class.
**In code:**
```cpp
Student s1("Adnan");
Student s2 = s1;    // copy constructor invoked, s2 is a copy of s1
```

## Q8. What is a Destructor?
**Real-life example:** When you check out of a hotel room, housekeeping cleans up and resets it for the next guest — cleanup happens automatically when you're "done."
**Simple answer:** A special function that runs automatically when an object is destroyed/goes out of scope, used to free resources (e.g., memory). Same name as class, preceded by `~`, no parameters, no return type, and cannot be overloaded.
**In code:**
```cpp
class Student {
public:
    ~Student() { cout << "Destructor called"; }
};
```

## Q9. What are Access Specifiers (`public`, `private`, `protected`)?
**Real-life example:** In a house: `public` is the living room (anyone/any guest can enter). `private` is your personal bedroom (only you — the family member/class itself — can enter). `protected` is like a family storeroom (family members and their kids/relatives — derived classes — can enter, but outside guests cannot).
**Simple answer:**
- `private`: accessible only within the same class.
- `protected`: accessible within the same class AND derived (child) classes.
- `public`: accessible from anywhere, including outside the class.
**Exam tip:** By default, class members in C++ are `private` if no specifier is written. (Struct members default to `public`.)

## Q10. What is the `this` pointer?
**Real-life example:** When you say "my phone," the word "my" refers to yourself. The `this` pointer is how an object refers to "myself" inside its own class functions.
**Simple answer:** A pointer available inside every non-static member function that points to the current object calling that function. Useful when a parameter name is the same as a member variable name.
**In code:**
```cpp
class Student {
    string name;
public:
    void setName(string name) {
        this->name = name;   // this->name = the object's member; name = the parameter
    }
};
```

## Q11. What are static members?
**Real-life example:** A shared family WhatsApp group counter that everyone in the family sees and updates — it's not "your" personal counter or "your sibling's" counter, it's ONE shared counter for the whole family (class), not per-person (object).
**Simple answer:** A static variable/function belongs to the CLASS itself, not to any individual object. All objects share the same single copy of a static variable.
**In code:**
```cpp
class Counter {
public:
    static int count;    // shared across all objects
    Counter() { count++; }
};
int Counter::count = 0;
Counter a, b, c;
cout << Counter::count;   // 3 — shared, not per-object
```

## Q12. Function Overloading vs Function Overriding — what's the difference?
**Real-life example:** Overloading is like a shop having several entrances (front door, side door, back door) — all lead into the same shop, just different ways in. Overriding is like a franchise branch changing the recipe slightly from the original headquarters' recipe, while keeping the same dish name.
**Simple answer:**
- **Overloading:** Same function name, DIFFERENT parameters, SAME class, compile-time decision.
- **Overriding:** Same function name, SAME parameters, occurs between a PARENT and CHILD class (inheritance), the child provides its own version, run-time decision (needs `virtual` for true dynamic behavior).
**In code:**
```cpp
// Overriding example
class Animal {
public:
    virtual void sound() { cout << "Some sound"; }
};
class Dog : public Animal {
public:
    void sound() override { cout << "Bark"; }   // overrides parent's version
};
```
**Exam tip:** This exact comparison (overloading vs overriding) is one of the MOST frequently asked OOP MCQs.

## Q13. What is Operator Overloading?
**Real-life example:** The `+` sign normally adds numbers (2+3=5), but we also informally "add" things like "mixing two colors" (red + blue = purple) — same symbol, different meaning depending on what you apply it to.
**Simple answer:** Redefining what an operator (`+`, `-`, `==`, etc.) does when used with objects of a user-defined class.
**In code:**
```cpp
class Point {
public:
    int x, y;
    Point operator+(Point p) {
        Point temp;
        temp.x = x + p.x;
        temp.y = y + p.y;
        return temp;
    }
};
```

## Q14. What are the types of Inheritance?
**Real-life example:**
- **Single:** One parent, one child (Father → Son).
- **Multilevel:** Grandparent → Parent → Child (a chain).
- **Multiple:** One child has two parents combined (rare in real biology, but common in code: a "Smartphone" class inheriting from both "Phone" and "Camera").
- **Hierarchical:** One parent, many children (Parent → Son, Daughter — both inherit from the same parent independently).
- **Hybrid:** A mix of two or more of the above types.
**Exam tip:** C++ supports all 5 types including multiple inheritance; Java does NOT support multiple inheritance with classes (only via interfaces) — this comparison is sometimes tested if the course touches Java too.

## Q15. What is a Virtual Function?
**Real-life example:** Ordering "the chef's special" at different branches of the same restaurant chain — each branch's chef prepares their own version, but you always just ask for "the special" without specifying which branch's exact recipe.
**Simple answer:** A member function in the base class that you expect to be redefined (overridden) in derived classes. Declared with the `virtual` keyword. Enables run-time polymorphism — the correct version is chosen based on the actual object type, even when accessed via a base class pointer/reference.
**In code:**
```cpp
Animal *a = new Dog();
a->sound();   // calls Dog's sound() because sound() is virtual — this is dynamic binding
```
**Exam tip:** Without `virtual`, calling through a base class pointer calls the BASE class's version, not the derived class's — this is a classic "predict the output" trap question.

## Q16. What is a Pure Virtual Function and an Abstract Class?
**Real-life example:** A job posting that says "Manager position — duties to be defined by each department" is like a pure virtual function — it exists as a placeholder, but each department (derived class) MUST define exactly what "manager" does for them.
**Simple answer:** A pure virtual function has no body and is declared with `= 0`. A class containing at least one pure virtual function becomes an **abstract class** — you CANNOT create objects of it directly; it must be inherited, and the derived class must implement (override) that function.
**In code:**
```cpp
class Shape {
public:
    virtual double area() = 0;   // pure virtual function
};
// Shape s;  // ERROR — cannot instantiate an abstract class
class Circle : public Shape {
public:
    double area() override { return 3.14 * 5 * 5; }
};
```

## Q17. What is an Interface, and how does it relate to Abstract Classes?
**Real-life example:** A "job contract" that only lists duties/responsibilities with no details on HOW to do them — every employee who signs must fulfill ALL listed duties in their own way.
**Simple answer:** An interface is a fully "abstract" blueprint — normally containing ONLY function declarations (no implementation at all), which implementing classes must define. C++ doesn't have a separate `interface` keyword — it simulates interfaces using a class where ALL functions are pure virtual. Java/C# have a dedicated `interface` keyword.
**Exam tip:** Abstract class CAN have some implemented functions + some pure virtual ones; a "pure interface" has ALL functions unimplemented.

## Q18. Composition vs Inheritance ("has-a" vs "is-a")?
**Real-life example:** A Car "has-a" Engine (composition — the car contains/owns an engine object, but a car IS NOT a type of engine). A Dog "is-a" Animal (inheritance — a dog genuinely is a kind of animal).
**Simple answer:** **Inheritance** models an "is-a" relationship (a Dog IS an Animal). **Composition** models a "has-a" relationship (a Car HAS an Engine) — one class contains an object of another class as a member variable, instead of inheriting from it.
**In code:**
```cpp
class Engine { public: void start() { cout << "vroom"; } };
class Car {
    Engine engine;    // composition — Car HAS an Engine
public:
    void start() { engine.start(); }
};
```

## Q19. What is a Friend Function?
**Real-life example:** Normally only family members can enter your private room, but you might give your best friend special permission to enter it too, even though they aren't family.
**Simple answer:** A function that is NOT a member of a class but is still granted access to that class's private/protected members, by declaring it with the `friend` keyword inside the class.
**In code:**
```cpp
class Box {
private:
    int width;
    friend void printWidth(Box b);   // grants access
};
void printWidth(Box b) { cout << b.width; }   // can access private member
```

## Q20. What is Exception Handling (`try`/`catch`/`throw`)?
**Real-life example:** A safety net under a tightrope walker — if something goes wrong (they slip), the net catches them instead of letting them crash to the ground.
**Simple answer:** A mechanism to handle runtime errors gracefully without crashing the whole program. Risky code goes in `try`, the error is "thrown" with `throw`, and handled in `catch`.
**In code:**
```cpp
try {
    int a = 10, b = 0;
    if (b == 0) throw "Division by zero!";
    cout << a / b;
} catch (const char* msg) {
    cout << "Error: " << msg;
}
```

## Q21. What are Templates (generic programming)?
**Real-life example:** A universal phone charger cable that works with any brand of phone, instead of buying a separate charger for each brand.
**Simple answer:** Templates let you write one function/class that works with ANY data type, instead of writing separate versions for `int`, `float`, `string`, etc.
**In code:**
```cpp
template <typename T>
T getMax(T a, T b) { return (a > b) ? a : b; }
getMax(3, 7);        // works with int
getMax(3.5, 7.2);    // works with double too
```

## Q22. What is the Diamond Problem in Multiple Inheritance?
**Real-life example:** If your mother's side AND your father's side of the family BOTH gave you a "family business," which one do you inherit/run when both claim ownership? Ambiguity/conflict.
**Simple answer:** When a class inherits from two classes that both inherit from a common base class, the derived class ends up with two copies of the base class's members, causing ambiguity about which one to use.
**Exam tip:** C++ solves this using `virtual inheritance`. Java avoids the whole problem by not allowing multiple class inheritance (only interfaces, which don't hold state).

## Q23. What does `const` mean for a member function or variable?
**Real-life example:** A laminated menu at a restaurant — you can read it, but you cannot write on it or change it.
**Simple answer:** `const` means "this value/object cannot be modified." A `const` member function promises it will NOT change any of the object's data.
**In code:**
```cpp
class Point {
    int x;
public:
    int getX() const { return x; }   // promises not to modify the object
};
```

## Q24. Quick recap — the 4 Pillars of OOP
| Pillar | One-line meaning | Real-life analogy |
|---|---|---|
| Encapsulation | Bundle data + restrict direct access | Medicine capsule / ATM |
| Abstraction | Hide complexity, show only essentials | Driving a car without knowing the engine |
| Inheritance | Reuse a parent class's features | Child inheriting parent's traits |
| Polymorphism | Same name, different behavior | The word "cut" meaning different things |

**Exam tip:** "Which of the following is NOT a pillar of OOP?" is an almost guaranteed question — options often sneak in "Compilation," "Iteration," or "Recursion" as fake pillars. The real 4 are always: Encapsulation, Abstraction, Inheritance, Polymorphism.
