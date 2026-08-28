# Algorithms & Complexity — Q&A

## Q1. What is an Algorithm, and what makes a good one?
**Real-life example:** A recipe for making tea — clear steps, a definite start and end, and it should actually produce tea (not coffee) every single time you follow it.
**Simple answer:** A finite, well-defined sequence of steps to solve a problem. A good algorithm is: **Correct** (gives the right answer), **Finite** (terminates, doesn't run forever), **Efficient** (doesn't waste time/memory), and **Unambiguous** (each step is clear).

## Q2. Time Complexity vs Space Complexity — what's the difference?
**Real-life example:** Time complexity is like asking "how long does it take to clean the house?" Space complexity is like asking "how many buckets/tools do I need to clean it?" — one measures TIME, the other measures MEMORY/RESOURCES used.
**Simple answer:** **Time complexity** measures how the RUNNING TIME of an algorithm grows as input size grows. **Space complexity** measures how much MEMORY it needs as input size grows.

## Q3. What is Big-O Notation?
**Real-life example:** If you're told a job takes "roughly a day" vs "roughly a month," you don't need the exact minute — you just need the general scale to plan around it. Big-O is that "general scale" for how an algorithm's speed grows as input size (n) grows, ignoring exact constants.
**Simple answer:** A way to describe the WORST-CASE (or general) growth rate of an algorithm's time/space needs as the input size `n` increases, focused on the dominant/biggest-impact term, ignoring constants.
**Exam tip:** Big-O describes growth trend, not exact seconds. "O(n)" means: if input doubles, work roughly doubles too.

## Q4. Best Case, Worst Case, Average Case — what's the difference?
**Real-life example:** Looking for your friend's name in a phonebook — **Best case:** their name is the very first one you check (lucky!). **Worst case:** their name is the very last one, or not there at all (you check everything). **Average case:** typically somewhere in the middle.
**Simple answer:** These describe an algorithm's performance under different scenarios of input arrangement. Big-O usually refers to the **worst case** unless stated otherwise.

## Q5. Common Complexity Classes — with real-life analogies
| Complexity | Name | Real-life example |
|---|---|---|
| O(1) | Constant | Checking if the FIRST person in a line is your friend — always 1 check, regardless of line length |
| O(log n) | Logarithmic | Finding a word in a dictionary by flipping to the middle and eliminating half each time |
| O(n) | Linear | Checking every person in a line one by one to find your friend |
| O(n log n) | Linearithmic | Efficiently sorting a deck of cards using merge sort |
| O(n²) | Quadratic | Comparing every person in a room to every OTHER person (like a round-robin tournament) |
**Exam tip:** Growth order from BEST (fastest) to WORST (slowest): O(1) < O(log n) < O(n) < O(n log n) < O(n²). This ranking is asked constantly — memorize it.

## Q6. What is Linear Search?
**Real-life example:** Looking for your car key by checking every pocket, one at a time, until you find it (or check them all and realize it's not there).
**Simple answer:** Check each element one by one from the start until the target is found or the list ends. Works on ANY list (sorted or unsorted).
**Complexity:** O(n) — worst case checks every single element.

## Q7. What is Binary Search?
**Real-life example:** Finding a word in a physical dictionary — you open to the middle, see if your word comes before or after, and repeat on just that half, again and again, eliminating half the remaining pages each time.
**Simple answer:** Repeatedly divide the search range in half by comparing the middle element to the target. **REQUIRES the data to be SORTED first.**
**Complexity:** O(log n) — much faster than linear search for large data.
**Exam tip:** "Binary search requires the array to be sorted" is a fact tested VERY often — trying binary search on unsorted data gives WRONG results, not just slower ones.

## Q8. What is Bubble Sort?
**Real-life example:** Arranging people in a line by height, where you repeatedly compare TWO NEIGHBORS at a time and swap them if they're in the wrong order, walking down the line again and again until nobody needs swapping — like bubbles rising to the surface.
**Simple answer:** Repeatedly compares adjacent elements and swaps them if they're in the wrong order, making multiple passes through the list.
**Complexity:** O(n²) worst/average case. Simple but slow for large data.

## Q9. What is Selection Sort?
**Real-life example:** Sorting exam papers by picking out the SMALLEST-scoring paper from the whole pile each time and placing it next in the sorted stack, repeating until the pile is empty.
**Simple answer:** Repeatedly finds the minimum (or maximum) element from the unsorted part and moves it to the sorted part.
**Complexity:** O(n²).

## Q10. What is Insertion Sort?
**Real-life example:** Sorting playing cards in your hand — you pick up cards one at a time and insert each new card into its correct position among the cards you're already holding (like organizing a hand of cards as you draw them).
**Simple answer:** Builds the sorted list one element at a time, inserting each new element into its correct position among the already-sorted part.
**Complexity:** O(n²) worst case, but performs very well (close to O(n)) on already nearly-sorted data.

## Q11. What is Merge Sort? (Divide and Conquer)
**Real-life example:** Splitting a huge pile of exam papers between multiple teachers, each sorting their own small pile quickly, and then combining ("merging") the sorted piles back together into one final sorted pile.
**Simple answer:** Recursively splits the list into halves until each piece has 1 element (trivially sorted), then merges the sorted halves back together in order.
**Complexity:** O(n log n) — always, in best/worst/average case. Uses extra memory (not "in-place").
**Exam tip:** Merge Sort is a classic example of the **Divide and Conquer** approach.

## Q12. What is Quick Sort?
**Real-life example:** Picking one "reference" student's height (a **pivot**), then splitting everyone else into "shorter than pivot" and "taller than pivot" groups, and repeating this splitting process within each group.
**Simple answer:** Picks a "pivot" element, partitions the list so smaller elements go left and larger go right of the pivot, then recursively sorts each side.
**Complexity:** O(n log n) average case, but O(n²) worst case (e.g., if the pivot is always the smallest/largest element, like with an already-sorted list and a poor pivot choice).

## Q13. Sorting Algorithms — Comparison Table
| Algorithm | Best Case | Worst Case | Stable? | In-place? |
|---|---|---|---|---|
| Bubble Sort | O(n) | O(n²) | Yes | Yes |
| Selection Sort | O(n²) | O(n²) | No | Yes |
| Insertion Sort | O(n) | O(n²) | Yes | Yes |
| Merge Sort | O(n log n) | O(n log n) | Yes | No |
| Quick Sort | O(n log n) | O(n²) | No | Yes |
**"Stable"** means equal elements keep their original relative order after sorting.
**Exam tip:** "Which sorting algorithm has the best guaranteed worst-case time complexity?" → **Merge Sort** (always O(n log n), unlike Quick Sort which can degrade to O(n²)).

## Q14. Recursion vs Iteration — trade-offs?
**Real-life example:** Climbing stairs by repeating the SAME action ("take one step") in a loop (iteration) vs. describing it as "climb to the top = take one step, then climb the REST of the stairs the same way" (recursion — the problem calls a smaller version of itself).
**Simple answer:** **Iteration** uses loops (for/while) — generally more memory-efficient. **Recursion** uses function calls that call themselves — often cleaner/more intuitive for problems that are naturally repetitive in structure (like trees, factorial, Fibonacci) but uses more memory (call stack) and can be slower due to function call overhead.

## Q15. What is the Divide and Conquer paradigm?
**Real-life example:** Studying for a huge syllabus by splitting it into 4 topic files (like this prep!), studying each one separately, then combining your understanding for the full picture.
**Simple answer:** Break a problem into smaller SUB-problems of the same type, solve each sub-problem (often recursively), then COMBINE the results into a final solution. Examples: Merge Sort, Quick Sort, Binary Search.

## Q16. What is a Greedy Algorithm?
**Real-life example:** Making change for a bill by always giving the LARGEST possible coin/note first, over and over, without thinking ahead about whether it's truly optimal for every case.
**Simple answer:** Makes the locally best (optimal-looking) choice at each step, hoping it leads to a globally optimal solution. Fast and simple, but doesn't always guarantee the best overall answer for every problem.

## Q17. What is Dynamic Programming (DP)?
**Real-life example:** Instead of re-calculating your monthly budget total from scratch every single time someone asks, you save ("store") the total once you calculate it, and just reuse that saved answer next time — avoiding repeated work.
**Simple answer:** Solves a problem by breaking it into overlapping sub-problems, SOLVING each sub-problem only ONCE, and storing ("memoizing") the result for reuse — avoiding redundant recomputation.
**Classic example:** Computing Fibonacci numbers. A plain recursive solution recalculates the same values repeatedly (very slow); a DP version stores previously computed values.
**Exam tip:** "Recursion + storing/reusing previous results" = Dynamic Programming. This is a commonly tested one-liner definition.

## Q18. How do you identify time complexity by counting loops? (important exam skill)
**Real-life example:** If you check every item in a shopping list ONCE, that's like one loop (O(n)). If for EVERY item on your list, you ALSO re-check the ENTIRE list again (a loop inside a loop), that's much slower (O(n²)) — like comparing every item to every other item.
**Simple answer / rules of thumb:**
- A single loop running `n` times → **O(n)**
- A loop inside another loop (both running `n` times) → **O(n²)**
- A loop that keeps HALVING the problem each time (like binary search) → **O(log n)**
- Two separate (not nested) loops, one after another → still **O(n)** (they add, not multiply: O(n) + O(n) = O(n))
**In code:**
```cpp
for (int i = 0; i < n; i++) {          // this loop alone = O(n)
    cout << i;
}
for (int i = 0; i < n; i++) {          // nested loops = O(n^2)
    for (int j = 0; j < n; j++) {
        cout << i << j;
    }
}
```
**Exam tip:** This "count the nested loops" trick is one of the most reliable ways to answer complexity MCQs quickly — look at the CODE, count how deep the loops are nested, that's your power of n.

## Q19. Searching & Sorting Complexity — Master Summary Table
| Algorithm | Time Complexity |
|---|---|
| Linear Search | O(n) |
| Binary Search | O(log n) — needs sorted data |
| Bubble/Selection/Insertion Sort | O(n²) |
| Merge Sort | O(n log n), always |
| Quick Sort | O(n log n) average, O(n²) worst |

## Q20. Common Exam Traps in Algorithms — quick recap
- Binary search on UNSORTED data → gives wrong results, not just "slower."
- `(int)` casting truncates, doesn't round (see [01-Programming-Fundamentals.md](01-Programming-Fundamentals.md) Q3).
- Nested loops multiply complexity; sequential loops add (and simplify to the bigger one).
- Merge Sort worst case is STILL O(n log n) — it never degrades. Quick Sort CAN degrade to O(n²) with a bad pivot.
- Missing a recursion base case = infinite recursion = stack overflow crash.
- "Stable" sort ≠ "fast" sort — they're unrelated properties (see Q13 table).
