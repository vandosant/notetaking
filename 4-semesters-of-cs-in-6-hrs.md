[four-semesters-of-cs](http://btholt.github.io/four-semesters-of-cs/)
[introduction to algorithms book](https://mitpress.mit.edu/books/introduction-algorithms)

### Big O
- Big picture of an algorithm
- Ignore little things and focus on big picture
- Typically focuses on time
- Also can consider spatial analysis (memory req)
- O(n): go through everything once, or some nested for loops
- O(n^2): loop within a loop
- O(1): no loops, just return something (constant time)
- O(log n): divide an conquer strategy (recursion), time diminishes per input as input grows
- [big o cheatsheet](http://bigocheatsheet.com)

### Sorting
- Bubble sort: useful to understand sorting, but very slow O(n^2)
  - Loop over the list until there are no more variables to swap
- Insertion sort: useful for arrays that are already close to being sorted
- Merge sort: typically the most useful algorithm because it is very dependable (preserves order of equivalent items)
- Quick sort: take pivot element and sort a greater-than-pivot and less-than-pivot list, recursively quick sorting down, and concatenating less-than + pivot + greater-than lists

### Data Structures
- When you have ordered data and you want to search for nodes very quickly
