# Programming Fundamentals — Q&A

## Q1. What is a "program" vs an "algorithm"?
**Real-life example:** A recipe written on paper (steps to cook biryani) is the *algorithm*. You actually cooking it in Urdu, English, or with different masalas is the *program* — the same recipe implemented in a specific way.
**Simple answer:** An algorithm is the step-by-step *idea/plan* to solve a problem. A program is that plan written in a programming language so a computer can run it.
**Exam tip:** If asked "algorithm is language-independent, program is language-dependent" — that's TRUE.

## Q2. What are variables and data types?
**Real-life example:** A variable is like a labeled box — you write "Age" on a box and put a number inside. The data type tells you what kind of thing can go in the box (numbers only, text only, etc.).
**Simple answer:** A variable is a named storage location. A data type defines what kind of value it holds: `int` (whole numbers), `float`/`double` (decimals), `char` (single letter), `bool` (true/false), `string` (text).
**In code:**
```cpp
int age = 25;
float price = 99.5;
char grade = 'A';
bool isPassed = true;
string name = "Adnan";
```
**Exam tip:** Know memory-ish facts: `int` for whole numbers, `float`/`double` for decimals, `char` uses single quotes `'A'`, `string`/text uses double quotes `"A"`.

## Q3. What is type casting?
**Real-life example:** Converting Pakistani Rupees to Dollars — same value, different "type" of representation.
**Simple answer:** Converting one data type to another. **Implicit** (automatic, done by compiler, e.g., int → float) vs **Explicit** (you force it, e.g., `(int)3.9` → `3`).
**In code:**
```cpp
int x = (int) 3.9;   // explicit cast, x becomes 3 (decimal is truncated, NOT rounded)
double y = 5;         // implicit cast, y becomes 5.0
```
**Exam tip:** Classic trap — `(int)3.9` gives `3`, not `4`. Casting to int always *truncates* (chops off decimals), it does not round.

## Q4. What are arithmetic operators?
**Real-life example:** Splitting a bill among friends uses `/` (division) for equal share and `%` (modulus) for the leftover coins that don't divide evenly.
**Simple answer:** `+ - * / %`. The tricky one is `%` (modulus) which gives the **remainder** of division.
**In code:**
```cpp
cout << 10 / 3;   // 3 (integer division drops the decimal)
cout << 10 % 3;   // 1 (remainder)
cout << 10.0 / 3; // 3.33333 (float division keeps decimals)
```
**Exam tip:** `int / int` = `int` result (decimal truncated). This is a VERY common "predict the output" question.

## Q5. What are relational and logical operators?
**Real-life example:** "If age >= 18 AND has CNIC, then allowed to vote" — combining two conditions with AND.
**Simple answer:** Relational compares values: `== != > < >= <=`. Logical combines true/false conditions: `&&` (AND, both must be true), `||` (OR, at least one true), `!` (NOT, flips true/false).
**In code:**
```cpp
if (age >= 18 && hasCNIC) { cout << "Can vote"; }
```
**Exam tip:** Don't confuse `=` (assignment, puts a value in) with `==` (comparison, checks equality). `if (x = 5)` is a classic bug — it assigns 5 instead of comparing, and is always "true" since 5 is non-zero.

## Q6. What's the difference between pre-increment and post-increment (`++x` vs `x++`)?
**Real-life example:** Post-increment is like handing someone their current turn number, THEN updating the counter for next time. Pre-increment updates the counter FIRST, then hands it out.
**Simple answer:** `++x` increases x first, then uses the new value. `x++` uses the current value first, then increases it.
**In code:**
```cpp
int x = 5;
cout << x++; // prints 5, then x becomes 6
cout << ++x; // x becomes 7, then prints 7
```
**Exam tip:** This is one of the most common "trace the output" MCQs. Practice a few by hand.

## Q7. What is operator precedence?
**Real-life example:** Order of operations in math (BODMAS/PEMDAS) — multiplication happens before addition.
**Simple answer:** Rules that decide which operator runs first when several appear together. `*`, `/`, `%` run before `+`, `-`. Parentheses `()` always run first.
**In code:**
```cpp
int result = 2 + 3 * 4; // 14, not 20, because * runs before +
```

## Q8. `if-else` vs `switch` — when to use which?
**Real-life example:** `if-else` is like a flexible checklist ("if it's raining, take umbrella; else if it's sunny, wear sunglasses..."). `switch` is like a vending machine — you press one exact button (1, 2, or 3) and get one exact result.
**Simple answer:** `if-else` handles ranges and complex conditions. `switch` compares one variable against several **exact** fixed values (usually int/char).
**In code:**
```cpp
switch (day) {
  case 1: cout << "Monday"; break;
  case 2: cout << "Tuesday"; break;
  default: cout << "Unknown";
}
```
**Exam tip:** Forgetting `break;` causes "fall-through" — execution continues into the next case. This is a favorite trick question.

## Q9. How does a `for` loop work?
**Real-life example:** "Do 5 pushups" — you know exactly how many times (start at 1, stop after 5, add 1 each time).
**Simple answer:** Used when you know the number of repetitions in advance. Structure: `for(initialization; condition; update)`.
**In code:**
```cpp
for (int i = 0; i < 5; i++) {
    cout << i << " ";   // prints: 0 1 2 3 4
}
```
**Exam tip:** Loop runs WHILE condition is true, and stops the moment it becomes false. `i < 5` with `i` starting at 0 runs exactly 5 times (0,1,2,3,4) — off-by-one counting is a classic exam trap.

## Q10. `while` vs `do-while` — what's the real difference?
**Real-life example:** `while` is like checking if there's food in the fridge BEFORE deciding to cook. `do-while` is like cooking first, THEN checking if you should cook again — you always cook at least once.
**Simple answer:** `while` checks the condition BEFORE running the loop body (may run 0 times). `do-while` checks AFTER (always runs at least once).
**In code:**
```cpp
int x = 10;
while (x < 5) { cout << "Never runs"; }        // condition false immediately, body never runs

do {
    cout << "Runs once";                         // runs first, THEN checks
} while (x < 5);
```
**Exam tip:** `do-while` guarantees at least ONE execution even if the condition is false from the start.

## Q11. What do `break` and `continue` do?
**Real-life example:** `break` is like leaving a queue entirely because you gave up. `continue` is like skipping your turn but staying in the queue for the next round.
**Simple answer:** `break` exits the loop completely. `continue` skips the rest of the current iteration and moves to the next one.
**In code:**
```cpp
for (int i = 0; i < 5; i++) {
    if (i == 3) break;       // stops loop entirely at i=3 → prints 0 1 2
}
for (int i = 0; i < 5; i++) {
    if (i == 3) continue;    // skips only i=3 → prints 0 1 2 4
    cout << i;
}
```

## Q12. What is a function and why use one?
**Real-life example:** A blender is a "function" — you put fruit in (input/parameters), it does its job, and juice comes out (return value). You don't need to know how the blades work every time you use it.
**Simple answer:** A reusable, named block of code that takes input (parameters), does something, and can send back a result (return value). Avoids repeating code.
**In code:**
```cpp
int add(int a, int b) {   // parameters: a, b
    return a + b;          // return value
}
int sum = add(3, 4);       // function call, sum = 7
```

## Q13. Pass by value vs pass by reference — what's the difference?
**Real-life example:** Pass by value is like giving someone a **photocopy** of a document — they can scribble on it, but your original is untouched. Pass by reference is giving them the **original document** — any change they make affects your real copy.
**Simple answer:** Pass by value copies the variable into the function (changes inside DON'T affect the original). Pass by reference passes the actual variable's address (changes DO affect the original).
**In code:**
```cpp
void changeVal(int x) { x = 100; }         // pass by value
void changeRef(int &x) { x = 100; }        // pass by reference (note the &)

int a = 5;
changeVal(a);   // a is still 5
changeRef(a);   // a is now 100
```
**Exam tip:** This is one of the MOST commonly tested concepts. The `&` symbol before a parameter name signals pass-by-reference in C++.

## Q14. What is function overloading?
**Real-life example:** A single word "book" can mean a "reading book" or "to book a ticket" — same name, different meaning based on context (how it's used). Function overloading is similar: same function name, different behavior based on the parameters given.
**Simple answer:** Multiple functions with the SAME name but DIFFERENT parameter lists (different number or types of parameters).
**In code:**
```cpp
int add(int a, int b) { return a + b; }
double add(double a, double b) { return a + b; }
int add(int a, int b, int c) { return a + b + c; }
```
**Exam tip:** Overloading is decided based on parameters, NOT return type. You cannot overload two functions that differ ONLY in return type.

## Q15. What are default arguments?
**Real-life example:** Ordering "chai" at a restaurant with no specific instructions gets you the default (regular sugar/milk) — but you can still customize it if you want.
**Simple answer:** A parameter that already has a value if the caller doesn't provide one.
**In code:**
```cpp
void greet(string name = "Guest") {
    cout << "Hello " << name;
}
greet();          // Hello Guest
greet("Adnan");   // Hello Adnan
```

## Q16. Local variable vs global variable — what's "scope"?
**Real-life example:** Cash in your own wallet (local) can only be used by you inside your house. Cash in a shared family locker (global) can be accessed and changed by anyone in the house.
**Simple answer:** Scope = where a variable is visible/usable. **Local** variables exist only inside the function/block they're declared in. **Global** variables are declared outside all functions and are accessible everywhere in the file.
**Exam tip:** If a local variable has the SAME name as a global one, the local one "wins" (shadows the global) inside its own function.

## Q17. What is recursion?
**Real-life example:** Standing between two mirrors facing each other — the reflection contains a reflection, which contains a reflection... until it becomes too small to see (the "base case"). Or: asking the person in front of you in a queue "what number are you?", who asks the person in front of them, and so on, until someone at the front just says "1" (base case) and the answer counts back up.
**Simple answer:** A function that calls itself to solve a smaller version of the same problem, until it hits a **base case** (a condition that stops the calls).
**In code:**
```cpp
int factorial(int n) {
    if (n == 0) return 1;          // base case — stops recursion
    return n * factorial(n - 1);   // recursive case
}
// factorial(4) = 4 * 3 * 2 * 1 * 1 = 24
```
**Exam tip:** Missing base case = infinite recursion = program crashes (stack overflow). Very common MCQ: "trace factorial(4)" or "what happens if there's no base case?"

## Q18. What is a 1D array?
**Real-life example:** A row of numbered lockers — locker 0, locker 1, locker 2... each holds one item, and you find items by their locker number (index).
**Simple answer:** A fixed-size collection of same-type elements stored in contiguous memory, accessed by an **index starting at 0**.
**In code:**
```cpp
int marks[5] = {90, 85, 70, 60, 95};
cout << marks[0];   // 90 (first element, index 0)
cout << marks[4];   // 95 (last element, index = size - 1)
```
**Exam tip:** Arrays are **zero-indexed**. An array of size 5 has valid indexes 0 to 4. Accessing `marks[5]` is out-of-bounds — a classic bug/trap question.

## Q19. What is a 2D array?
**Real-life example:** A cinema seating chart — rows and columns, e.g. seat at Row 2, Column 3.
**Simple answer:** An array of arrays, accessed with two indices: `array[row][col]`.
**In code:**
```cpp
int grid[2][3] = { {1,2,3}, {4,5,6} };
cout << grid[1][2];   // 6 (row index 1, column index 2)
```

## Q20. Char array vs `string` — what's the difference?
**Real-life example:** A `char` array is like spelling a word letter tile by letter tile (Scrabble tiles in a row, ending with a special "stop" tile). A `string` object is like a ready-made word card you can resize and manipulate easily.
**Simple answer:** A C-style string is a `char` array ending with a null character `'\0'`. C++'s `string` class is a built-in object type that's easier to use (supports `+`, `.length()`, comparisons, etc. directly).
**In code:**
```cpp
char cstr[] = "Hi";        // stored as 'H','i','\0'
string s = "Hi";
cout << s.length();        // 2
```

## Q21. What is a pointer?
**Real-life example:** A pointer is like a house **address** written on paper. The paper itself isn't the house — it just tells you WHERE the house is. You can go to that address to see or change what's inside the house.
**Simple answer:** A variable that stores the **memory address** of another variable, instead of storing a value directly.
**In code:**
```cpp
int x = 10;
int *p = &x;      // p stores the address of x (& = "address of")
cout << *p;        // 10 (* = "value at this address" — dereferencing)
*p = 20;            // changes x to 20 through the pointer!
```
**Exam tip:** `&` = "address of", `*` = "value pointed to" (dereference). These two symbols are heavily tested — know which is which.

## Q22. What is a NULL pointer and dynamic memory?
**Real-life example:** A NULL pointer is like an empty, unassigned mailbox address — it points to "nowhere." Dynamic memory is like renting extra storage space on-demand instead of only using the fixed space you were born with.
**Simple answer:** `nullptr`/`NULL` means a pointer points to nothing. `new` allocates memory while the program is running; `delete` frees it. Forgetting `delete` causes a **memory leak** (space stays reserved but unusable forever).
**In code:**
```cpp
int *p = new int(5);   // dynamically allocate memory holding 5
delete p;                // free that memory
p = nullptr;             // good practice: avoid a "dangling pointer"
```

## Q23. What is a `struct`?
**Real-life example:** A student ID card groups different pieces of info (name, roll number, department) into one card. A struct groups different variables (possibly different types) under one name.
**Simple answer:** A user-defined type that bundles multiple variables (of possibly different types) together under one name.
**In code:**
```cpp
struct Student {
    string name;
    int rollNo;
    float gpa;
};
Student s1;
s1.name = "Adnan";
s1.rollNo = 101;
```
**Exam tip:** A `struct` is very similar to a `class` in C++, except struct members are `public` by default, while class members are `private` by default.

## Q24. Compiler vs Interpreter, and types of errors?
**Real-life example:** A compiler is like translating a whole book to another language before anyone reads it. An interpreter is like a live translator converting sentence-by-sentence as the speaker talks.
**Simple answer:** A **compiler** translates the entire source code into machine code before running (e.g., C++). An **interpreter** translates and runs line-by-line (e.g., Python, at a high level).
- **Syntax error:** broken grammar rules (e.g., missing semicolon) — caught before running.
- **Logical error:** code runs fine but gives the wrong answer (e.g., using `+` instead of `-`).
- **Runtime error:** crashes while running (e.g., dividing by zero, accessing invalid array index).
**Exam tip:** "Program compiles but gives wrong output" = logical error, NOT a syntax error. This distinction is commonly tested.

## Q25. How does the "call stack" relate to function calls?
**Real-life example:** A stack of plates in a cafeteria — the last plate you placed is the first one someone picks up (Last In, First Out). Function calls behave the same way.
**Simple answer:** Every time a function is called, its info (local variables, where to return to) is pushed onto a call stack. When the function finishes, it's popped off, and control returns to whoever called it.
**Exam tip:** This is exactly why deep/infinite recursion crashes with a "stack overflow" — too many function calls pile onto the stack without being popped off.
