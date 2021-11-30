---
title: LeetCode_Maximum Nesting Depth of the Parentheses
author: 다연
date: 2021-11-25 21:28:00 +0900
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy,  Stack]
---
# [Maximum Nesting Depth of the Parentheses](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/)

A string is a  **valid parentheses string**  (denoted  **VPS**) if it meets one of the following:

-   It is an empty string  `""`, or a single character not equal to  `"("`  or  `")"`,
-   It can be written as  `AB`  (`A`  concatenated with  `B`), where  `A`  and  `B`  are  **VPS**'s, or
-   It can be written as  `(A)`, where  `A`  is a  **VPS**.

We can similarly define the  **nesting depth**  `depth(S)`  of any VPS  `S`  as follows:

-   `depth("") = 0`
-   `depth(C) = 0`, where  `C`  is a string with a single character not equal to  `"("`  or  `")"`.
-   `depth(A + B) = max(depth(A), depth(B))`, where  `A`  and  `B`  are  **VPS**'s.
-   `depth("(" + A + ")") = 1 + depth(A)`, where  `A`  is a  **VPS**.

For example,  `""`,  `"()()"`, and  `"()(()())"`  are  **VPS**'s (with nesting depths 0, 1, and 2), and  `")("`  and  `"(()"`  are not  **VPS**'s.

Given a  **VPS**  represented as string  `s`, return  _the  **nesting depth**  of_ `s`.
> **Input:** s = "(1+(2*3)+((8)/4))+1"  
**Output:** 3

> **Input:** s = "(1)+((2))+(((3)))"  
**Output:** 3

> **Input:** s = "1+(2*3)/(2-1)"  
**Output:** 1

> **Input:** s = "1"  
**Output:** 0
# 과정
---
> Time: O(n)  
Space: O(1)  

# 코드
---
```JavaScript
var maxDepth = function(s) {
    let max = 0;
    let sCnt = 0;
    for(let i = 0; i<s.length; i++){
        if(s[i]==="("){
            sCnt++;
            max = Math.max(sCnt, max);
        }
        if(s[i]===")"){
            sCnt--;
        }
    }
    return max
};
```
# Submission Detail
---
Runtime:  **86 ms**  
: Your runtime beats 26.46 % of javascript submissions.  
  
Memory Usage:  **38.7 MB**  
: Your memory usage beats 86.89 % of javascript submissions.  

# 후기
---
1. 처음에는 Stack의 pop과 push를 이용해서 문제를 풀었다.
2. 이후, 공간 복잡도를 고려해 Stack 대신 sCount라는 변수를 사용해서 문제를 풀었다.
