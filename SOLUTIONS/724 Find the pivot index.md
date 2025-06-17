#PrefixSum #fullsum
Given an array of integers `nums`, calculate the **pivot index** of this array.

The **pivot index** is the index where the sum of all the numbers **strictly** to the left of the index is equal to the sum of all the numbers **strictly** to the index's right.

If the index is on the left edge of the array, then the left sum is `0` because there are no elements to the left. This also applies to the right edge of the array.

Return _the **leftmost pivot index**_. If no such index exists, return `-1`.

**Example 1:**

**Input:** nums = [1,7,3,6,5,6]
**Output:** 3
**Explanation:**
The pivot index is 3.
Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
Right sum = nums[4] + nums[5] = 5 + 6 = 11

**Example 2:**

**Input:** nums = [1,2,3]
**Output:** -1
**Explanation:**
There is no index that satisfies the conditions in the problem statement.

**Example 3:**

**Input:** nums = [2,1,-1]
**Output:** 0
**Explanation:**
The pivot index is 0.
Left sum = 0 (no elements to the left of index 0)
Right sum = nums[1] + nums[2] = 1 + -1 = 0


---
1,7,3,6,5,6
prefix sum array [1,8,11,17,22,28]'
right sum  = [28,27,20,17,11,6]


lets think of two pointer approach 
```python
l=0
r=len(nums)-1
while(len(nums)!=0){
	lsum+=nums[l]
	
}
```

That’s solid work on **1480 Running Sum**, Nav — clean and intuitive. Now let’s break down **LeetCode 724: Find Pivot Index** the same way: intuitively, surgically, and in a way that builds your prefix sum instincts.

---

## 🔍 Problem: **Find Pivot Index**

> A **pivot index** is where the sum of all numbers **to the left** is equal to the sum of all numbers **to the right**.

Given an array `nums`, return the _leftmost_ pivot index. If it doesn't exist, return `-1`.

---

## 🧠 INTUITION FIRST

Let’s say:

```text
nums = [1, 7, 3, 6, 5, 6]
```

Try index 3 (value `6`):

```text
Left sum = 1 + 7 + 3 = 11  
Right sum = 5 + 6 = 11 ✅  
```

So pivot index = 3

### ✨ Key Insight:

If you **know total sum**, and you're scanning from left to right, at index `i`:

```text
leftSum = sum of elements before i  
rightSum = totalSum - leftSum - nums[i]
```

So if:

```text
leftSum == rightSum  
→ leftSum == totalSum - leftSum - nums[i]  
→ 2 * leftSum + nums[i] == totalSum
```

Boom 💥 That's your condition.

---

## ✅ Java Code (Clean and Fast):

```java
public int pivotIndex(int[] nums) {
    int total = 0;
    for (int num : nums) total += num;

    int leftSum = 0;
    for (int i = 0; i < nums.length; i++) {
        if (2 * leftSum + nums[i] == total) return i;
        leftSum += nums[i];
    }

    return -1;
}
```

---

### 🔍 Dry Run Example:

```text
nums = [2, 1, -1]

total = 2

Index 0:
leftSum = 0 → 2 * 0 + 2 == 2 ✅ → return 0
```

---

## ⏱️ Time & Space Complexity

- **Time:** O(n) → one pass to get total, another to find pivot
    
- **Space:** O(1) → only variables, no extra array
    

---

## 🧠 Why This Is Prefix Sum

This is a **prefix sum** problem in disguise:

- You build the **running sum from the left**
    
- You use **total sum** to calculate the **right side**
    

So you're comparing a **prefix vs a derived suffix**, which is a core prefix sum trick.

---

## 🔥 Final Tip:

Don't compute left and right sums every time in O(n) (brute). Instead:

- Compute total sum once.
    
- Build leftSum progressively.
    
- Use math to **infer rightSum**.
    

This is how you **engineer efficiently**.

---

## 💬 TL;DR for Obsidian Notes:

```markdown
### 🧠 Leetcode 724: Find Pivot Index

- Pivot index: left sum == right sum
- totalSum = sum(nums)
- For index i:
  if (2 * leftSum + nums[i] == totalSum) → pivot!
- One pass: O(n) time, O(1) space
```

---

You're mastering not just problems — but the _thinking structure_ behind them. Honor that by sticking to the principle: **"Don’t repeat effort — optimize it."** Ready for the next challenge when you are, brother.