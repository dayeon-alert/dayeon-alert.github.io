---
title: BinarySearch_Strictly Increasing or Strictly
author: 다연
date: 2021-11-07 00:08:00
categories: [Algorithm, BinarySearch]
tags: [BinarySearch, easy, Array]
---
## [문제](https://binarysearch.com/problems/Strictly-Increasing-or-Strictly-Decreasing)
Given a list of integers `nums`, return whether the list is strictly increasing or strictly decreasing.
## 코드
```
class  Solution {
	solve(nums) {
		let descending=true;
		let ascending=true;

		for(let i = 0; i<nums.length-1;i++){
			if(nums[i]<=nums[i+1]) descending = false;
			if(nums[i]>=nums[i+1]) ascending = false;
		}
		
		return descending||ascending
	}
}
```

