
#two-pointer
#arrays
#medium


---

## 🔱 <span style="color:rgb(255, 0, 0)">L</span><span style="color:rgb(255, 0, 0)">eetCode </span>#11 – Container With Most Water

**Link:** [LeetCode #11](https://leetcode.com/problems/container-with-most-water/)  
**Category:** Arrays  
**Pattern:** Two Pointers  
**Difficulty:** Medium  
**Covered on:** Day 1 of DSA Vault

---

### 🧠 Problem Statement

> You are given an array `height[]` where each element represents the height of a vertical line.
> 
> Choose two lines such that, together with the x-axis, they form a container holding the **most water**.
> 
> Return the **maximum area** of water that can be contained.

---

### 📊 Example

```java
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49

// Chosen lines: height[1] = 8, height[8] = 7
// Width = 8 - 1 = 7
// Height = min(8, 7) = 7
// Area = 7 * 7 = 49
```

---

## ⚔️ Key Idea & Strategy

- **Area Formula:**  
    `area = (right - left) * min(height[left], height[right])`
    
- Start with widest container (`left = 0`, `right = n-1`)
    
- Always move the pointer pointing to the **shorter height** (greedy logic)
    
- This strategy ensures we **maximize height** while reducing width
    

---

### 🔁 Pattern: Two Pointer Technique

|Step|Action|
|---|---|
|1|Set `left = 0`, `right = n - 1`|
|2|While `left < right`:|
|3|→ Compute area with current pair|
|4|→ Update `maxArea` if current area is larger|
|5|→ Move the pointer at the **shorter bar** inward|
|6|Repeat until `left >= right`|

---

## ✅ Clean Java Solution

```java
public class Solution {
    public int maxArea(int[] height) {
        int maxArea = 0;
        int left = 0, right = height.length - 1;

        while (left < right) {
            int width = right - left;
            int ht = Math.min(height[left], height[right]);
            int area = width * ht;
            maxArea = Math.max(maxArea, area);

            // Move the shorter line inward
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxArea;
    }
}
```

---

## 📈 Time & Space Complexity

|Metric|Value|
|---|---|
|Time|`O(n)`|
|Space|`O(1)`|

---

### 🧠 What You Learned

- How to approach array problems using **two pointers**
    
- When to **greedily shrink width** while hoping to find a taller container
    
- Making **tradeoffs between height and width**
    
- Pattern recognition for future problems like:
    
    - Trapping Rain Water
        
    - Max Area in Binary Matrix
        
    - Container With Limited Height Constraints
        

---

### 🧱 Reps Completed

- ✅ Dry Run
    
- ✅ Code Written & Submitted
    
- ✅ Logic Understood (Pointer movement decision-making)
    
- ✅ Obsidian Vault Entry Created
    

---

### 🛡️ Integrity Checkpoint

> You said you're a man of honor. That means **showing up**, writing it down, and reflecting on it.  
> **Don’t just solve — master.**  
> This is **1/12 Array Problems**. Lock it in. We don't skip steps.

---

### 🔜 Up Next

**🧩 Problem 2 → Longest Substring Without Repeating Characters**  
**Topic:** Strings + HashSet  
**Pattern:** Sliding Window  
**LeetCode #3** — Let's go next level.

---
