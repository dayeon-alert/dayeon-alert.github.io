---
title: LeetCode_Shortest Distance to a Character
author: 다연
date: 2021-11-08 21:22:00 +0900
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy, Array, Two Pointers, String, 100%]
---
# [Shortest Distance to a Character](https://leetcode.com/problems/shortest-distance-to-a-character/)

Given a list of integers `nums`, return whether the list is strictly increasing or strictly decreasing.
# 과정
---
> I: String, character  
O: Array of Integers  
C: 1<=s.length<=10^4, s[i] and c are lowercase Eng letters  
E: s is null, s.length is 0  

> DS: Array  
Algo: Two Pointer  


> Pseudo:  
첫번째 for문
1.  
"l" o v e l e e t c o d e  
left = 1  
2.  
l "o" v e l e e t c o d e  
left = 2  
3.  
l o "v" e l e e t c o d e  
left = 3  
4.  
l o v "e" l e e t c o d e  
arr = [3, 2, 1, Inf]  
left = 0  
5.  
l o v e "l" e e t c o d e  
arr = [3, 2, 1, Inf]  
left = 1  
6. 
l o v e l "e" e t c o d e  
arr = [3, 2, 1, Inf, 1, Inf]
left = 0  

>
두번째 for문
1.  
"l" o v e l e e t c o d e  
right = -1  
arr = [3, 2, 1, Inf, 1, Inf, ...]  
2.  
l "o" v e l e e t c o d e  
right = -1  
arr = [3, 2, 1, Inf, 1, Inf, ...]  
3.  
l o "v" e l e e t c o d e  
right = -1  
arr = [3, 2, 1, Inf, 1, Inf, ...]  
4.  
l o v "e" l e e t c o d e  
right = 0  
arr = [3, 2, 1, 0, 1, Inf, ...]  
5.   
l o v e "l" e e t c o d e  
right = 1
arr = [3, 2, 1, 0, 1, Inf, ...]  
6.  
l o v e l "e" e t c o d e
right = 0  
arr = [3, 2, 1, 0, 1, 0, ...]

> Time: O(n)  
Space:  O(n)  

# 코드
---
```JavaScript
var shortestToChar = function(s, c) {
    let left = 0;
    let right = -1;
    let arr = new Array(s.length).fill(Infinity);
    
    for(let i = 0; i<s.length;i++){
        if(s[i]!==c){
            left++;
            continue;
        }
        while(left>0){
            arr[i-left] = left;
            left--;
        }
    }
    
    for(let i = 0; i<s.length;i++){
        if(s[i]===c) right = 0;
        if(right<0) continue;
        
        arr[i] = Math.min(right, arr[i]);
        right++;
    }
    return arr;
};
```
# Submission Detail
---
Runtime:  **68 ms**  
: Your runtime beats 100.00 % of javascript submissions.  
  
Memory Usage:  **40.8 MB**  
: Your memory usage beats 71.78 % of javascript submissions.  

# 후기
---
1. Runtime 100%가 나왔다. 아직 갈 길이 멀긴 해도 기분이 좋다!
2. 아마도 두번째 for문을 돌 때, 초기에 c를 만나기 전까지 continue문을 사용해 배열 값을 갱신하는 부분을 건너 뛰어서 빠른 속도가 나온 게 아닐까. 추측해본다. 
