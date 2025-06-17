#Array #BinarySearch 
Given an array of integers `nums` sorted in non-decreasing order, find the starting and ending position of a given `target` value.

If `target` is not found in the array, return `[-1, -1]`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

**Input:** nums = [5,7,7,8,8,10], target = 8
**Output:** [3,4]

**Example 2:**

**Input:** nums = [5,7,7,8,8,10], target = 6
**Output:** [-1,-1]

**Example 3:**

**Input:** nums = [], target = 0
**Output:** [-1,-1]

**Constraints:**

- `0 <= nums.length <= 105`
- `-109 <= nums[i] <= 109`
- `nums` is a non-decreasing array.
- `-109 <= target <= 109`
---
solution 
lets say the binary search finds the element , how do we estimate the first and last occurence
, we can also do two pointer approach but it would take time of O(n) 

```java
public int [] searchRange(int []nums, int target){
	int first = search(nums,target, true);
	int last = search(nums, target, false);
	int ans ={first,last};
	return ans;
}

syntax for normal binary search 
public int search(int []nums, int target, boolean searchindex){
	int index=-1l
	int s=0;
	int e=nums.length-1;
	while(s<=e){
		int m=s+(e-s)/2;
		if(m>target){
		e=m-1;
		}
		elif(m<target){
		s=m+1;}
		else{
		if(searchindex)e=m-1;
		else s=m+1;
		}
		index=m
	}
	return index;
	
	
}
```

this will work better as we only need 1 function less code and its just binary search 
even if we were to run in 2 time it will still be O(log(n))
