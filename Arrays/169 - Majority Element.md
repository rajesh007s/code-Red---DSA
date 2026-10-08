# 📁 Folder: Arrays / Brute Force

# 📄 File Name: `169 - Majority Element.md`

# 🧩 LeetCode 169 - Majority Element

## 🔗 Problem

[LeetCode 169 - Majority Element](https://leetcode.com/problems/majority-element/?utm_source=chatgpt.com)

---

## 🏷️ Tags

* Array
* Counting
* Brute Force

---

## 📚 Topics

* Arrays
* Nested Loops
* Frequency Counting

---

## 📊 Difficulty

**Easy**

---

## 💡 Intuition

The problem asks us to find the element that appears **more than `n / 2` times** in the array.

For example:

```text
nums = [2, 2, 1, 1, 1, 2, 2]
```

Here:

```text
2 → appears 4 times
1 → appears 3 times
```

Array size:

```text
n = 7
```

Majority condition:

```text
n / 2 = 7 / 2 = 3
```

`2` appears `4` times, which is greater than `3`.

Therefore:

```text
Answer = 2
```

### Simple idea:

For every element:

1. Count how many times it appears.
2. Check whether its count is greater than `n / 2`.
3. If yes, return that element.

---

## 🧠 Thought Process

### Start from:

Start with the first element `nums[i]`.

### Step 1:

Take one element from the array.

```java
nums[i]
```

### Step 2:

Use another loop to compare it with every element.

```java
nums[i] == nums[j]
```

If they are equal, increase the count.

```java
cnt++;
```

### Step 3:

After counting, check:

```java
if (cnt > n / 2)
```

If true, we found the majority element.

### Step 4:

Return the element.

```java
return nums[i];
```

---

## 🏃 Dry Run

### Example

```text
nums = [2, 2, 1, 1, 1, 2, 2]
```

```text
n = 7
n / 2 = 3
```

### Checking `2`

| Index `i` | Value | Count |
| --------- | ----: | ----: |
| 0         |     2 |     1 |
| 1         |     2 |     2 |
| 2         |     1 |     2 |
| 3         |     1 |     2 |
| 4         |     1 |     2 |
| 5         |     2 |     3 |
| 6         |     2 |     4 |

So:

```text
cnt = 4
n/2 = 3
```

Check:

```text
4 > 3
```

✅ True

Therefore:

```text
return 2;
```

### Output

```text
2
```

---

## ⭐ Main Logic

The important part of your solution is:

```java
for (int i = 0; i < nums.length; i++) {
    int cnt = 0;

    for (int j = 0; j < n; j++) {
        if (nums[i] == nums[j]) {
            cnt++;
        }
    }

    if (cnt > n / 2) {
        return nums[i];
    }
}
```

Think of it like this:

```text
Pick one element
      ↓
Compare with all elements
      ↓
Count how many times it occurs
      ↓
Is count > n/2?
      ↓
   YES → Return element
   NO  → Check next element
```

---

## 🎯 Key Pattern

### Frequency Counting

The main pattern used here is **frequency counting**.

We need to know:

> "How many times does each element appear?"

For every element, we count its occurrences.

Example:

```text
[3, 3, 4, 3, 2]

3 → 3 times
4 → 1 time
2 → 1 time
```

Then we check whether the frequency is greater than `n/2`.

### When to recognize this pattern?

If a problem asks:

* How many times does an element appear?
* Find the most frequent element
* Find an element appearing more than a certain number of times
* Count occurrences

👉 Think about **frequency counting**.

---

## ☕ Java Solution

Your solution is correct for LeetCode 169:

```java
class Solution {
    public int majorityElement(int[] nums) {

        int n = nums.length;

        for (int i = 0; i < nums.length; i++) {

            int cnt = 0;

            for (int j = 0; j < n; j++) {

                if (nums[i] == nums[j]) {
                    cnt++;
                }
            }

            if (cnt > n / 2) {
                return nums[i];
            }
        }

        return -1;
    }
}
```

### Important lines

```java
int n = nums.length;
```

Stores the size of the array.

---

```java
if (nums[i] == nums[j])
```

Checks whether the current element is equal to another element.

---

```java
cnt++;
```

If they are equal, increase the occurrence count.

---

```java
if (cnt > n / 2)
```

Checks whether the element appears **more than half** of the array size.

---

```java
return nums[i];
```

Returns the majority element when found.

---

## 🧪 Another Example

### Input

```text
nums = [3, 3, 4]
```

Array size:

```text
n = 3
```

Majority condition:

```text
n / 2 = 1
```

Check `3`:

```text
3 → appears 2 times
```

Since:

```text
2 > 1
```

Return:

```text
3
```

### Output

```text
3
```

---

## ⚠️ Edge Case

### Input

```text
nums = [1]
```

Here:

```text
n = 1
n/2 = 0
```

`1` appears `1` time.

```text
1 > 0
```

So:

```text
Output = 1
```

---

## ⏱️ Complexity

### Time Complexity

```text
O(n²)
```

Why?

There are **two nested loops**.

```text
Outer loop → O(n)
Inner loop → O(n)
```

Therefore:

```text
O(n) × O(n) = O(n²)
```

### Space Complexity

```text
O(1)
```

We only use a few variables:

```text
n
cnt
i
j
```

No extra array, HashMap, or other data structure is used.

---

## 🚀 Better Approach

There is a much faster solution called **Boyer-Moore Voting Algorithm**.

It reduces the time complexity from:

```text
O(n²)
```

to:

```text
O(n)
```

and still uses:

```text
O(1)
```

extra space.

For your current beginner practice, **understanding your brute-force solution first is completely fine**. Once you're comfortable with frequency counting, learn Boyer-Moore as the optimized version.

---

## 📌 Key Takeaways

* A majority element appears **more than `n/2` times**.
* Use the outer loop to select an element.
* Use the inner loop to count its occurrences.
* `cnt++` increases the occurrence count.
* `cnt > n/2` checks the majority condition.
* Two nested loops give **O(n²)** time.
* Only a few variables are used, so space is **O(1)**.
* The optimized pattern for this problem is **Boyer-Moore Voting Algorithm**.

---

## 🧠 Pattern to Remember

```text
Pick an element
      ↓
Count its occurrences
      ↓
Compare count with n/2
      ↓
count > n/2 ?
    ↙       ↘
  YES       NO
   ↓         ↓
 Return    Check next
 element    element
```

💡 **Remember:**

> **"Count how many times each element appears; if it appears more than half, that's the majority element."**
