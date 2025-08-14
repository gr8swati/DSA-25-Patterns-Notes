# 📌 Two Pointers Pattern

## 1️⃣ What is the Two Pointers Pattern?

The **Two Pointers** technique means using **two variables (pointers or indices)** to scan through data (like arrays or strings) **in a coordinated way** instead of using nested loops.

The main goal: **Solve problems faster — usually O(n) instead of O(n²).**

💡 **Think of it as**: two people reading the same story but starting at different pages and moving depending on the clues in the story.

---

## 2️⃣ When to Recognize That Two Pointers Will Work

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

## 3️⃣ Common Types of Two Pointers

| Type                           | Direction                          | When to Use                                    | Example Problem                           |
| ------------------------------ | ---------------------------------- | ---------------------------------------------- | ----------------------------------------- |
| **Opposite Direction**         | Start one at beginning, one at end | Find a pair with a given sum, reverse an array | Find two numbers that sum to a target     |
| **Same Direction**             | Both start from same point         | Compare/subsequence matching                   | Merge two sorted arrays                   |
| **Slow & Fast**                | One moves faster                   | Detect cycles, find middle of list             | Linked list cycle detection               |
| **Sliding Window (variation)** | Adjust start & end                 | Subarray problems with constraints             | Longest substring without repeating chars |

---

## 4️⃣ Core Tricks for Applying Two Pointers

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

1. **Opposite Direction**

   * One pointer starts at the **beginning** of the array.
   * The other starts at the **end**.
   * Move them towards each other depending on the condition.
   * **Example:** Finding a pair with a given sum.

2. **Same Direction**

   * Both pointers start at the **beginning**.
   * One pointer moves faster than the other.
   * Often used in **sliding window** or **fast & slow pointer** problems.
   * **Example:** Detecting cycles in linked lists.

3. **Pointer Movement Logic**

   * If the current sum/product/difference is **too small**, move the **left pointer** forward.
   * If it’s **too large**, move the **right pointer** backward.
   * Stop when pointers meet or condition is satisfied.

💻 **Quick Example (Opposite Direction — Find Pair with Target Sum)**:

```java
int left = 0, right = arr.length - 1;
while (left < right) {
    int sum = arr[left] + arr[right];
    if (sum == target) {
        System.out.println("Pair: " + arr[left] + ", " + arr[right]);
        break;
    } else if (sum < target) {
        left++;
    } else {
        right--;
    }
}
```

---

### Opposite Direction Visual (Two Pointers)

Here’s a diagram to help you visualize two pointers moving inward:

![Two Pointers Visualization](https://miro.medium.com/v2/resize\:fit:1400/1*iJ753jJDtXzC3kMw7LNqcg.gif)

* **Left Pointer** starts at the beginning.
* **Right Pointer** starts at the end.
* They move inward based on the comparison with the target value.
