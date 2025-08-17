
# Two Pointers Pattern

## What is the Two Pointers Pattern?

The Two Pointers technique involves using two indices (pointers) to iterate over a data structure (usually an array or a string) to solve problems efficiently by avoiding nested loops.

**Imagine you and your friend reading the same book:**
- You start from the **front page**  
- Your friend starts from the **last page**  
- Both of you move inward depending on certain rules  

This is exactly how the Two Pointers technique works — using two indices to scan data together instead of using slow nested loops.

It makes solutions much faster (often **O(n)** instead of **O(n²)**) and with minimal space complexity.

---

## How It Works — 3 Main Styles

### 1) Opposite Direction (meet-in-the-middle)
- Two pointers start at **left** and **right**, move towards each other based on a condition.  
- Great for: pair sum, max area, palindrome checks.  

**Time Complexity:** O(n)  
**Space Complexity:** O(1)  

**Java Template**
```java
int l = 0, r = arr.length - 1;
while (l < r) {
    int sum = arr[l] + arr[r];
    if (sum == target) { /* record/return */ break; }
    if (sum < target) l++; else r--;
}
````

---

### 2) Same Direction / Sliding Window

* Both start at the **beginning**.
* Right pointer **expands** the window; left pointer **shrinks** it to maintain constraints.
* Great for: subarray sums/products, longest/shortest windows.

**Time Complexity:** O(n)
**Space Complexity:** O(1)

**Java Template**

```java
int l = 0, sum = 0; // or long prod = 1;
for (int r = 0; r < arr.length; r++) {
    sum += arr[r];   // or prod *= arr[r];
    while (sum > target) { // or prod >= k
        sum -= arr[l];     // or prod /= arr[l];
        l++;
    }
    // window [l..r] is valid here
}
```

---

### 3) Slow & Fast Pointers

* One pointer moves **1 step**, the other **2 steps**.
* Great for: cycle detection, middle of linked list.

**Time Complexity:** O(n)
**Space Complexity:** O(1)

**Java Template**

```java
ListNode slow = head, fast = head;
while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
    if (slow == fast) { /* cycle */ break; }
}
```

---

## Typical Steps (mental model)

1. Place pointers (left/right or slow/fast).
2. Check the condition (sum/window/cycle/etc.).
3. Move the correct pointer (increase/decrease/advance).
4. Repeat until meet / cross / reach end.

---

## Must-Practice Problems

| #  | Problem                                                | How It Uses Two Pointers                                                    | Time  | Space         |
| -- | ------------------------------------------------------ | --------------------------------------------------------------------------- | ----- | ------------- |
| 1  | Remove Duplicates from Sorted Array (LeetCode 26)      | Writer pointer places the next unique value while reader scans ahead        | O(n)  | O(1)          |
| 2  | Two Sum II – Input Array Is Sorted (LeetCode 167)      | Left + Right sum → too small? move left; too big? move right                | O(n)  | O(1)          |
| 3  | Move Zeroes (LeetCode 283)                             | Writer compacts non-zeros; reader scans. Fill rest with 0s                  | O(n)  | O(1)          |
| 4  | Reverse String (LeetCode 344)                          | Swap left/right, move towards center (like zipping a jacket)                | O(n)  | O(1)          |
| 5  | Container With Most Water (LeetCode 11)                | Left/right bars: area = width × min(height). Move shorter bar inward        | O(n)  | O(1)          |
| 6  | Valid Palindrome (LeetCode 125)                        | Skip non-alphanumerics. Compare left/right chars, move inward               | O(n)  | O(1)          |
| 7  | Squares of a Sorted Array (LeetCode 977)               | Biggest square is at ends. Compare abs(left) vs abs(right), fill from back  | O(n)  | O(n) (output) |
| 8  | Subarray Product < K (LeetCode 713)                    | Sliding window: expand right (multiply), shrink left (divide) while ≥ K     | O(n)  | O(1)          |
| 9  | Remove Element (LeetCode 27)                           | Writer keeps non-target elements; reader scans all                          | O(n)  | O(1)          |
| 10 | 3Sum (LeetCode 15)                                     | Sort. Fix i, then use left/right to find pairs = -nums\[i]. Skip duplicates | O(n²) | O(1) extra    |
| 11 | Sort Colors (Dutch National Flag) (LeetCode 75)        | Three zones with low, mid, high. Swap and move pointers                     | O(n)  | O(1)          |
| 12 | Longest Substring Without Repeating Chars (LeetCode 3) | Sliding window with set/map. Expand right; if duplicate, shrink left        | O(n)  | O(min(n, Σ))  |
| 13 | Minimum Size Subarray Sum (LeetCode 209)               | Sliding window: expand until sum ≥ target, then shrink to minimize          | O(n)  | O(1)          |
| 14 | Trapping Rain Water (LeetCode 42)                      | LeftMax/RightMax with two pointers; add water where lower side limits       | O(n)  | O(1)          |
| 15 | Longest Mountain in Array (LeetCode 845)               | Scan peaks; expand left downwards and right downwards to measure mountain   | O(n)  | O(1)          |

---

## Quick “Which Style Do I Use?” Guide

* Need pair from sorted array → Opposite Direction
* Need max/min window or count subarrays → Sliding Window
* Need cycle/middle in linked list → Slow & Fast
* Need in-place reordering/compaction → Same Direction (writer/reader)


