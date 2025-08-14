#  Two Pointers Pattern

## What is the Two Pointers Pattern?

The **Two Pointers** technique means using **two variables (pointers or indices)** to scan through data (like arrays or strings) **in a coordinated way** instead of using nested loops.

The main goal: **Solve problems faster — usually O(n) instead of O(n²).**

💡 **Think of it as**: two people reading the same story but starting at different pages and moving depending on the clues in the story.

---

## When to Recognize That Two Pointers Will Work

Look for problems where:

* The input is **sorted** (array or linked list).
* You need to **find pairs/triplets/subarrays** with a certain property (sum, product, difference, etc.).
* You need to **reverse or rearrange data** in place.
* You are working with **two sequences** and comparing them.
* You need to **detect cycles** (slow & fast pointer technique in linked lists).
* You want to **skip duplicates or filter elements** without extra space.

💡 **Key Recognition Tip:**
If you find yourself writing a **nested loop (O(n²))** but the data is sorted OR you can sort it, there’s a good chance Two Pointers can replace that with **O(n)**.

---

## Common Types of Two Pointers

| Type                           | Direction                          | When to Use                                    | Example Problem                           |
| ------------------------------ | ---------------------------------- | ---------------------------------------------- | ----------------------------------------- |
| **Opposite Direction**         | Start one at beginning, one at end | Find a pair with a given sum, reverse an array | Find two numbers that sum to a target     |
| **Same Direction**             | Both start from same point         | Compare/subsequence matching                   | Merge two sorted arrays                   |
| **Slow & Fast**                | One moves faster                   | Detect cycles, find middle of list             | Linked list cycle detection               |
| **Sliding Window (variation)** | Adjust start & end                 | Subarray problems with constraints             | Longest substring without repeating chars |

---

## Core Tricks for Applying Two Pointers

1. **Move the correct pointer**

   * If sum too small → move `left++`
   * If sum too big → move `right--`

2. **Avoid unnecessary comparisons**

   * If already processed an element, skip duplicates.

3. **Use sorting if needed**

   * Many problems need sorting first to make Two Pointers possible.

4. **Work in-place when possible**

   * Reduces space usage from O(n) → O(1).

5. **Think about stopping condition**

   * Usually `left < right` for opposite direction.

---

## 🛠 How It Works

You maintain **two pointers** that move through the data structure according to certain rules:

---

### **Opposite Direction**

* One pointer starts at the **beginning** of the array.
* The other starts at the **end**.
* Move them towards each other depending on the condition.
* **Example:** Finding a pair with a given sum.

 **Example (Find Pair with Target Sum)**:

```java
int left = 0, right = arr.length - 1;
while (left < right) {
    int sum = arr[left] + arr[right];
    if (sum == target) {
        System.out.println(arr[left] + ", " + arr[right]);
        break;
    } else if (sum < target) {
        left++;
    } else {
        right--;
    }
}
```

---

### **Same Direction**

* Both pointers start at the **beginning**.
* One pointer moves ahead to explore, the other follows to shrink or expand the range.
* Often used in **sliding window** or **fast & slow pointer** problems.
* **Example:** Find subarray with given sum.

**Example (Sliding Window for Subarray Sum)**:

```java
int left = 0, sum = 0;
for (int right = 0; right < arr.length; right++) {
    sum += arr[right];
    while (sum > target) {
        sum -= arr[left];
        left++;
    }
    if (sum == target) {
        System.out.println("Subarray: " + left + " to " + right);
    }
}
```

---

### **Slow & Fast Pointers**

* One pointer moves **one step at a time**, the other **two steps at a time**.
* Useful for **cycle detection** in linked lists or finding the middle node.

**Example (Cycle Detection in Linked List)**:

```java
ListNode slow = head, fast = head;
while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
    if (slow == fast) {
        System.out.println("Cycle detected");
        break;
    }
}
```

---

### Opposite Direction Visual (Two Pointers)

![Two Pointers Visualization](https://miro.medium.com/v2/resize\:fit:1400/1*iJ753jJDtXzC3kMw7LNqcg.gif)

* **Left Pointer** starts at the beginning.
* **Right Pointer** starts at the end.
* They move inward based on the comparison with the target value.

