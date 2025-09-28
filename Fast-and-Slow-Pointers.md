
# Fast and Slow Pointers Pattern (Tortoise and Hare)

The **Fast and Slow Pointers** pattern (also known as **Floyd's Cycle Detection Algorithm** or the **Tortoise and Hare technique**) is a two-pointer strategy used to efficiently traverse data structures.

---

## Key Idea

* **Slow Pointer (`slow`)** → moves **1 step** at a time.
* **Fast Pointer (`fast`)** → moves **2 steps** at a time.

If there is a cycle (or repetition), they will eventually **meet**.

---

## Visual Intuition

### 1. Detecting a Cycle

```
Linked List with a Cycle:

head → A → B → C → D → E
               ↑       ↓
               H ← G ← F

slow = 1 step  
fast = 2 steps  

Eventually: slow == fast (inside cycle)
```

---

### 2. Finding the Middle of a List

```
List: A → B → C → D → E → F

slow: moves 1 step
fast: moves 2 steps

Steps:
1. slow=A, fast=A
2. slow=B, fast=C
3. slow=C, fast=E
4. fast reaches end → slow = C (middle)
```

---

### 3. Tortoise and Hare Race Analogy 

```
Track: ────────────────────────────────● (finish)

🐢 moves 1 step: ──>
🐇 moves 2 steps: ─────>

They meet if there is a loop on the track.
```

---

## When to Use

* Cycle detection (linked lists, number sequences, circular arrays)
* Finding the middle of a list
* Detecting palindromes in linked lists
* Finding the start of a loop
* Math-based problems with repetitive cycles (e.g., **Happy Number**)
* Problems requiring **O(1) space**

---

## How to Recognize When to Apply

| Signal                | Description                                                                       |
| --------------------- | --------------------------------------------------------------------------------- |
| **Repetition**        | You repeatedly transform/traverse values (e.g., linked list, digit-sum problems). |
| **Cycle possibility** | The structure may form a loop (linked list, array with jumps).                    |
| **Need for midpoint** | You need the middle element in **one pass**.                                      |
| **O(1) space**        | Must avoid using extra memory like hashmaps/sets.                                 |

---

## Steps to Apply

```java
// Step 1: Initialize
ListNode slow = head;
ListNode fast = head;

// Step 2: Traverse
while (fast != null && fast.next != null) {
    slow = slow.next;         // 1 step
    fast = fast.next.next;    // 2 steps
    
    // Step 3: Meeting point
    if (slow == fast) {
        // cycle detected
    }
}
```

### Step 4: Logic

* **Detect cycle** → if `slow == fast` → cycle exists
* **Find cycle start** → reset `slow = head`, move both 1 step until they meet
* **Find middle** → stop when `fast == null`
* **Happy Number / transformations** → treat transformation as “next”

---

## Benefits

* **O(n) Time** → linear traversal, no nested loops
* **O(1) Space** → only two pointers
* **No modification** → works without altering structure
* **Elegant cycle detection & midpoint access**

---

## Example Problems

| #  | Problem                              | Type                       | Platform                                                                        |
| -- | ------------------------------------ | -------------------------- | ------------------------------------------------------------------------------- |
| 1  | Linked List Cycle Detection          | Detect cycle               | [LeetCode](https://leetcode.com/problems/linked-list-cycle/)                    |
| 2  | Linked List Cycle II                 | Find start of cycle        | [LeetCode](https://leetcode.com/problems/linked-list-cycle-ii/)                 |
| 3  | Middle of the Linked List            | Find middle node           | [LeetCode](https://leetcode.com/problems/middle-of-the-linked-list/)            |
| 4  | Happy Number                         | Detect cycle in numbers    | [LeetCode](https://leetcode.com/problems/happy-number/)                         |
| 5  | Palindrome Linked List               | Check palindrome           | [LeetCode](https://leetcode.com/problems/palindrome-linked-list/)               |
| 6  | Remove Nth Node From End             | Two-pointer gap            | [LeetCode](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)     |
| 7  | Reorder List                         | Middle + rearranging       | [LeetCode](https://leetcode.com/problems/reorder-list/)                         |
| 8  | Find the Duplicate Number            | Cycle detection in array   | [LeetCode](https://leetcode.com/problems/find-the-duplicate-number/)            |
| 9  | Circular Array Loop                  | Detect loop in array       | [LeetCode](https://leetcode.com/problems/circular-array-loop/)                  |
| 10 | Detect Cycle in Circular Linked List | Custom                     | [GFG](https://www.geeksforgeeks.org/detect-loop-in-a-linked-list/)              |
| 11 | Intersection of Two Linked Lists     | Cycle trick (alt method)   | [LeetCode](https://leetcode.com/problems/intersection-of-two-linked-lists/)     |
| 12 | Merge in Between Linked Lists        | Mid finding + manipulation | [LeetCode](https://leetcode.com/problems/merge-in-between-linked-lists/)        |
| 13 | Find Middle of Circular Linked List  | Middle node variation      | [GFG](https://www.geeksforgeeks.org/find-the-middle-of-a-circular-linked-list/) |
| 14 | Sort List (Merge Sort)               | Midpoint splitting         | [LeetCode](https://leetcode.com/problems/sort-list/)                            |
| 15 | Detect Loop Length in Linked List    | Cycle length               | [GFG](https://www.geeksforgeeks.org/find-length-of-loop-in-linked-list/)        |

---

**Great for Linked List & Number Cycle Problems**
**Best choice when asked for O(1) space**
