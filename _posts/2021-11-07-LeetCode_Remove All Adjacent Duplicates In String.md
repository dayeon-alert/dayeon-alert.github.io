---
title: LeetCode_Remove All Adjacent Duplicates In String
author: 다연
date: 2021-11-07 23:39:00
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy, Stack]
---
# [Remove All Adjacent Duplicates In String - LeetCode](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)
---
You are given a string  `s`  consisting of lowercase English letters. A  **duplicate removal**  consists of choosing two  **adjacent**  and  **equal**  letters and removing them.

We repeatedly make  **duplicate removals**  on  `s`  until we no longer can.

Return  _the final string after all such duplicate removals have been made_. It can be proven that the answer is  **unique**.
# 과정
---
> I: String(문자열)  
O: String(문자열)  
C: 1<=s.length<=10^5, s is always lowercase Englich letters.  
E: If s.length is 0 or s is null, return -1  


> DS: Stack  
Algo: Iteration  


> Pseudo:  
for문을 사용해 글자 단위로 Stack에 삽입.  
이 때, 방금 Stack에 넣은 글자와, 현재 글자가 같을 경우, Stack에 삽입한 글자를 다시 빼낸다.(pop)

> Time: O(N)  
Space: O(N)  

# 코드
---
```JavaScript
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
# Submission Detail
---
Runtime:  **92 ms**  
: Your runtime beats 77.00 % of javascript submissions.  
  
Memory Usage:  **48.3 MB**  
: Your memory usage beats 38.01 % of javascript submissions.  

# 후기
---
1. Stack을 알고 있다면 어렵지 않게 풀 수 있는 문제다.
