# Data Structures — Q&A

## Q1. What is a Data Structure? Linear vs Non-Linear?
**Real-life example:** A queue of people at a bank counter is arranged in a line (linear — one after another). A family tree, with parents branching into children, is non-linear (branches, not a straight line).
**Simple answer:** A data structure is a way of organizing and storing data so it can be used efficiently. **Linear** structures arrange elements sequentially (Array, Linked List, Stack, Queue). **Non-linear** structures arrange elements in a hierarchical/networked way (Tree, Graph).

## Q2. Array vs Linked List — what's the real difference?
**Real-life example:** An Array is like numbered parking spots in a straight row in a parking lot — fixed spots, easy to jump to spot #7 directly. A Linked List is like a treasure hunt — each clue (node) tells you where to find the NEXT clue; you can't jump straight to clue #7, you must follow the chain from the start.
**Simple answer:**
| | Array | Linked List |
|---|---|---|
| Memory | Contiguous (side-by-side) | Scattered, connected via pointers |
| Size | Fixed at creation (in plain arrays) | Grows/shrinks dynamically |
| Access | Direct/instant via index — O(1) | Must traverse from head — O(n) |
| Insert/Delete (middle) | Slow — must shift elements — O(n) | Fast once position found — O(1) |
**Exam tip:** "Which allows faster random access — array or linked list?" → **Array** (O(1) via index). "Which is easier to insert/delete in the middle?" → **Linked List**.

## Q3. What is a Singly Linked List?
**Real-life example:** A treasure hunt where each clue only tells you where the NEXT clue is — you can only move forward, never backward.
**Simple answer:** A chain of nodes where each node stores data + a pointer to the NEXT node only. The last node points to `NULL`.
**In code (concept):**
```cpp
struct Node {
    int data;
    Node* next;
};
```

## Q4. What is a Doubly Linked List?
**Real-life example:** A train where each coach is connected to BOTH the coach in front AND the coach behind — you can walk forward or backward through the train.
**Simple answer:** Like a singly linked list, but each node also has a pointer to the PREVIOUS node, allowing traversal in both directions. Uses more memory (extra pointer) but is more flexible.

## Q5. What is a Circular Linked List?
**Real-life example:** People sitting in a circle playing a passing game — after the last person, the "next" goes back to the first person, forming a loop with no true "end."
**Simple answer:** A linked list where the last node points back to the FIRST node instead of `NULL`, forming a loop.

## Q6. What is a Stack? (LIFO)
**Real-life example:** A stack of plates in your kitchen cupboard — you always place a new plate on TOP, and you always take a plate from the TOP. The plate at the very bottom is the last one you'd ever use.
**Simple answer:** A LIFO (Last In, First Out) structure. Main operations: `push` (add to top), `pop` (remove from top), `peek/top` (view top without removing).
**Real-world uses:** Undo button in Word/Photoshop, the back button in a browser, evaluating math expressions, and how function calls work (the call stack — see [01-Programming-Fundamentals.md](01-Programming-Fundamentals.md) Q25).
**Exam tip:** "Which data structure is used for function call management / recursion / undo operations?" → **Stack**.

## Q7. What is a Queue? (FIFO)
**Real-life example:** A line at a bank counter or a ATM — the first person to join the line is the first person served. Whoever joins last waits at the back.
**Simple answer:** A FIFO (First In, First Out) structure. Main operations: `enqueue` (add to the back/rear), `dequeue` (remove from the front).
**Real-world uses:** Printer job scheduling, customer service systems, CPU task scheduling, WhatsApp message delivery order.
**Exam tip:** "Which data structure is used for scheduling / order-preserving processing?" → **Queue**.

## Q8. What is a Circular Queue?
**Real-life example:** A roundabout (traffic circle) — vehicles keep going around, and there's no true "front" or "end" of the road, positions just wrap around.
**Simple answer:** A queue where the last position connects back to the first, so it re-uses freed-up space instead of wasting it (a problem plain arrays-based queues have).

## Q9. What is a Priority Queue?
**Real-life example:** An emergency room in a hospital — patients are NOT treated first-come-first-served; the most critical patient is treated first, regardless of arrival order.
**Simple answer:** A queue where each element has a priority, and elements with higher priority are served/removed before lower-priority ones, regardless of insertion order. Usually implemented internally using a **Heap**.

## Q10. What is a Deque (Double-Ended Queue)?
**Real-life example:** A row of people where new people can join OR leave from BOTH the front and back ends, not just one side.
**Simple answer:** A queue where insertion and deletion can happen from BOTH the front and the back.

## Q11. What is a Tree, and what's its terminology?
**Real-life example:** A family/organization chart — a CEO at the top (root), managers below (children), employees below them (leaves — no one reports to them).
**Simple answer:** A hierarchical, non-linear structure of nodes connected by edges, starting from one **root** node.
- **Root:** the topmost node
- **Leaf:** a node with no children
- **Height:** the longest path from root to a leaf
- **Parent/Child:** direct connections between adjacent levels

## Q12. Binary Tree vs Binary Search Tree (BST) — what's the difference?
**Real-life example:** A **Binary Tree** is any family tree where each parent has at most 2 kids — no rule about how they're arranged. A **BST** is like a phonebook-organized binary tree — for any person, everyone with an "earlier/smaller" name goes to the left, everyone "later/bigger" goes to the right, at EVERY level, making search fast.
**Simple answer:** A Binary Tree = each node has at most 2 children (no ordering rule). A Binary Search Tree = a binary tree where for every node, the LEFT subtree contains only SMALLER values, and the RIGHT subtree contains only LARGER values. This ordering makes searching very fast — O(log n) on average.
**Exam tip:** BST search/insert/delete average case is O(log n), but worst case (a skewed/unbalanced tree, e.g., inserting sorted data 1,2,3,4,5 in order) degrades to O(n) — a commonly tested trap.

## Q13. What are Tree Traversals (Inorder, Preorder, Postorder)?
**Real-life example:** Think of visiting rooms in a 2-story house with a hallway connecting Left room, Middle stairs, Right room:
- **Inorder** (Left, Root, Right): visit left room → middle stairs → right room. For a BST, this visits nodes in SORTED ascending order — a very important exam fact.
- **Preorder** (Root, Left, Right): announce the middle stairs first, then go left, then right — used to copy/clone a tree.
- **Postorder** (Left, Right, Root): visit both rooms fully before announcing the stairs last — used to safely delete a tree (children removed before parent).
**Exam tip:** "Which traversal gives sorted output for a BST?" → **Inorder**. This is one of the most frequently asked tree MCQs.

## Q14. What is Level Order Traversal / BFS on a tree?
**Real-life example:** Announcing an organization chart floor by floor — CEO first (level 0), then all direct managers (level 1), then all their employees (level 2), etc., left to right on each level.
**Simple answer:** Visiting nodes level-by-level, top to bottom, left to right. Implemented using a **Queue**.

## Q15. What is DFS (Depth-First Search)?
**Real-life example:** Exploring a maze by picking one path and following it ALL the way to a dead end before backtracking and trying another path — going deep before going wide.
**Simple answer:** Explores as far down one branch as possible before backtracking. Implemented using a **Stack** (or recursion, which uses the call stack internally).
**Exam tip:** BFS uses a **Queue**; DFS uses a **Stack**/recursion. This pairing is heavily tested.

## Q16. What is a Heap (Min-Heap / Max-Heap)?
**Real-life example:** A company org chart where EVERY manager earns MORE than everyone below them (Max-Heap) or LESS than everyone below them (Min-Heap) — but siblings at the same level have no fixed order relative to each other, only the parent-child relationship matters.
**Simple answer:** A special binary tree where every parent is either always ≥ its children (**Max-Heap**, largest value at the root) or always ≤ its children (**Min-Heap**, smallest value at the root). Used to implement **Priority Queues** and **Heap Sort**.
**Exam tip:** The root of a max-heap is always the maximum value in the entire structure — instantly accessible in O(1).

## Q17. What is Hashing / a Hash Table (Hash Map)?
**Real-life example:** A library that assigns each book a specific shelf number based on a formula applied to its title, so you can jump DIRECTLY to the right shelf instead of searching every shelf one by one.
**Simple answer:** A structure that maps a "key" to a "value" using a **hash function**, which converts the key into an index/slot number, enabling near-instant (O(1) average) lookup, insertion, and deletion.
**Real-world use:** Dictionaries in Python, storing usernames→passwords, phonebook lookups by name.

## Q18. What is a Hash Collision, and how is it resolved?
**Real-life example:** Two different books' titles happen to compute the SAME shelf number by the library's formula — a collision. The library must decide: stack both books on that shelf (**chaining**) or move the second book to the next available shelf (**open addressing**).
**Simple answer:** A collision happens when two different keys hash to the same index.
- **Chaining:** each slot holds a small linked list of all items that hashed there.
- **Open addressing:** if a slot is taken, probe/search for the next available empty slot.

## Q19. What is a Graph? Directed vs Undirected, Weighted vs Unweighted?
**Real-life example:** A road map is a graph — cities are "nodes," roads connecting them are "edges." A one-way street is a **directed** edge (only one direction allowed); a normal two-way street is **undirected**. If some roads have tolls (a "cost" to use them), that's a **weighted** graph; if all roads are equal/free, it's **unweighted**.
**Simple answer:** A graph is a set of nodes (vertices) connected by edges, used to model networks/relationships (social networks, maps, the internet).

## Q20. Adjacency Matrix vs Adjacency List — how do we store a graph?
**Real-life example:** An Adjacency Matrix is like a big table where every city has a row and column, and you mark a "1" if there's a direct road between them (fast lookup, but wastes space if most cities aren't directly connected). An Adjacency List is like each city keeping its OWN short list of "directly connected neighboring cities" (saves space when connections are sparse).
**Simple answer:**
- **Adjacency Matrix:** a 2D grid, `matrix[i][j] = 1` if an edge exists between node i and j. Simple but uses O(V²) space.
- **Adjacency List:** each node keeps a list of its direct neighbors. More space-efficient for sparse graphs (few connections).

## Q21. BFS vs DFS on Graphs — quick comparison
**Real-life example:** Finding the shortest way to reach a friend-of-a-friend on Facebook by checking ALL your direct friends first, then all of THEIR friends (BFS, level by level) vs. following ONE friend's entire friend chain deeply before trying another friend (DFS).
**Simple answer:** **BFS** (Breadth-First Search) explores level-by-level using a Queue — good for finding the SHORTEST path in an unweighted graph. **DFS** (Depth-First Search) explores as deep as possible first using a Stack/recursion — good for exploring all possibilities, detecting cycles, maze-solving.

## Q22. Time Complexity Cheat Table for Common Data Structure Operations
| Structure | Access | Search | Insert | Delete |
|---|---|---|---|---|
| Array | O(1) | O(n) | O(n) | O(n) |
| Linked List | O(n) | O(n) | O(1)* | O(1)* |
| Stack (push/pop) | — | O(n) | O(1) | O(1) |
| Queue (enqueue/dequeue) | — | O(n) | O(1) | O(1) |
| BST (balanced, average) | O(log n) | O(log n) | O(log n) | O(log n) |
| BST (worst case, skewed) | O(n) | O(n) | O(n) | O(n) |
| Hash Table (average) | — | O(1) | O(1) | O(1) |

*Linked List insert/delete is O(1) ONLY if you already have a pointer to the position; finding that position first is O(n).
**Exam tip:** Memorize this table — a huge chunk of MCQs directly ask "what is the time complexity of X operation on Y structure?"

## Q23. Quick Real-World Mapping — "Which data structure should I use?"
| Situation | Best Structure | Why |
|---|---|---|
| Undo/redo in an app | Stack | LIFO — last action undone first |
| Customers waiting in line | Queue | FIFO — first come, first served |
| Browser back button | Stack | Goes back to the most recently visited page |
| Emergency room patients | Priority Queue | Most critical treated first |
| Autocomplete/dictionary lookup | Hash Table | Instant key-based lookup |
| Organizing employees by rank | Tree | Hierarchical relationships |
| Social network connections | Graph | Models many-to-many relationships |
| Finding shortest path between two points | Graph + BFS | Explores level by level |

## Q24. Stack vs Queue — side-by-side
| | Stack | Queue |
|---|---|---|
| Order | LIFO (Last In First Out) | FIFO (First In First Out) |
| Add | push (top) | enqueue (rear) |
| Remove | pop (top) | dequeue (front) |
| Real-life | Plate stack | Bank line |
**Exam tip:** This exact comparison is asked almost every time, in some form ("Which is FIFO?" / "Which is LIFO?").

## Q25. Why is Recursion connected to the Stack data structure?
**Real-life example:** See [01-Programming-Fundamentals.md](01-Programming-Fundamentals.md) Q25 (mirrors/queue-of-questions analogy) — each recursive call is "pushed" onto the call stack, and as functions return, they're "popped" off, in LIFO order.
**Simple answer:** Every recursive call adds a new frame onto the program's call stack. This is why deep, unstoppable recursion (missing base case) causes a **stack overflow** — the exact same LIFO structure as the Stack data structure.
