# Quick Revision Cheat Sheet — Read This Tonight & Tomorrow Morning

## Exam Facts (don't forget these!)
- Tomorrow, Aug 29, 2026 — arrive **11:00 AM sharp**, City Campus PECHS
- Bring **original CNIC**
- Mock test: 11:15–11:25 AM (do it — free warm-up)
- Real test: 11:30 AM–12:30 PM, **50 MCQs, 1 hour, NO negative marking**
- **Strategy: answer EVERY question. Guessing costs nothing.**

---

## Big-O Growth Order (memorize this order!)
**O(1) < O(log n) < O(n) < O(n log n) < O(n²)**
(constant < logarithmic < linear < linearithmic < quadratic)

| Complexity | Example situation |
|---|---|
| O(1) | Array access by index, hash table lookup |
| O(log n) | Binary search, balanced BST search |
| O(n) | Linear search, single loop |
| O(n log n) | Merge sort, Quick sort (average) |
| O(n²) | Bubble/Selection/Insertion sort, nested loops |

---

## Data Structure Operations — Complexity Table
| Structure | Access | Search | Insert | Delete |
|---|---|---|---|---|
| Array | O(1) | O(n) | O(n) | O(n) |
| Linked List | O(n) | O(n) | O(1)* | O(1)* |
| BST (balanced) | O(log n) | O(log n) | O(log n) | O(log n) |
| BST (worst/skewed) | O(n) | O(n) | O(n) | O(n) |
| Hash Table (avg) | — | O(1) | O(1) | O(1) |

## Sorting Algorithms — Complexity Table
| Algorithm | Best | Worst | Stable | In-place |
|---|---|---|---|---|
| Bubble Sort | O(n) | O(n²) | Yes | Yes |
| Selection Sort | O(n²) | O(n²) | No | Yes |
| Insertion Sort | O(n) | O(n²) | Yes | Yes |
| Merge Sort | O(n log n) | O(n log n) | Yes | No |
| Quick Sort | O(n log n) | O(n²) | No | Yes |

---

## Stack vs Queue (asked almost every time)
- **Stack** = LIFO (Last In, First Out) → push/pop from top → undo, browser back, recursion/call stack
- **Queue** = FIFO (First In, First Out) → enqueue rear/dequeue front → line at bank, printer jobs

## BFS vs DFS
- **BFS** = level by level, uses a **Queue**, good for shortest path
- **DFS** = go deep first, uses a **Stack**/recursion, good for exploring all paths

## Tree Traversals
- **Inorder** (L, Root, R) → gives **SORTED** output for a BST ⭐ most-asked fact
- **Preorder** (Root, L, R) → used to copy a tree
- **Postorder** (L, R, Root) → used to delete a tree safely

---

## The 4 Pillars of OOP (guaranteed question)
1. **Encapsulation** — bundle data + hide it (medicine capsule)
2. **Abstraction** — hide complexity, show essentials (driving without knowing the engine)
3. **Inheritance** — child reuses parent's features (child inherits traits)
4. **Polymorphism** — same name, different behavior (the word "cut" in different contexts)

## Overloading vs Overriding
| | Overloading | Overriding |
|---|---|---|
| Same class? | Yes | No — parent/child |
| Parameters | Different | Same |
| Decided when | Compile-time | Run-time |
| Needs `virtual`? | No | Yes (for true dynamic behavior) |

## Constructor vs Destructor
- **Constructor**: same name as class, runs on object creation, NO return type (not even void), CAN be overloaded
- **Destructor**: `~ClassName`, runs on object destruction, no parameters, CANNOT be overloaded

## Access Specifiers
- `private` → only same class
- `protected` → same class + child classes
- `public` → accessible from anywhere
- Default in `class` = private. Default in `struct` = public.

---

## Programming Fundamentals — Rapid Fire
- `int/int` division = truncates decimal (10/3 = 3, not 3.33)
- `(int)3.9` = 3 (truncation, NOT rounding)
- `x++` = use then increase (post) | `++x` = increase then use (pre)
- Pass by value = copies (original unchanged) | Pass by reference (`&`) = original CAN change
- Arrays are zero-indexed: size 5 array → valid indices 0 to 4
- `&` = address of | `*` = value at address (dereference)
- Missing `break` in switch = falls through to next case
- Missing base case in recursion = infinite recursion = stack overflow
- Syntax error = caught before running | Logical error = wrong output, runs fine | Runtime error = crashes while running

---

## Common "Which one is it?" Quick Answers
| Question pattern | Answer |
|---|---|
| Data structure for undo/redo | Stack |
| Data structure for scheduling/order | Queue |
| Search needing sorted data | Binary Search |
| Sort with guaranteed O(n log n) worst case | Merge Sort |
| Traversal giving sorted BST output | Inorder |
| Structure for instant key lookup | Hash Table |
| OOP concept = hiding data | Encapsulation |
| OOP concept = hiding complexity | Abstraction |
| OOP concept = "is-a" relationship | Inheritance |
| OOP concept = "has-a" relationship | Composition |
| Same function name, different parameters, same class | Overloading |
| Same function name/signature, parent vs child class | Overriding |

---

## Final Reminders
1. **No negative marking → NEVER leave a blank answer.**
2. Trace code carefully for "what's the output" questions — write it on scratch paper if allowed.
3. When unsure of complexity, COUNT THE LOOPS in the code (nested = multiply, sequential = the bigger one wins).
4. Don't panic on one hard question — mark and move on, 72 seconds/question average.
5. Sleep well tonight — a clear head traces code faster than a tired one that "knows more."

**Good luck tomorrow — you've prepared well. Go pass this thing.**
