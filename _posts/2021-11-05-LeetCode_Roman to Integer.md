---
title: LeetCode_Roman to Integer
author: 다연
date: 2021-11-05 04:08:00
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy, String, Hash Table]
---

## [문제](https://leetcode.com/problems/roman-to-integer/)
Roman numerals are represented by seven different symbols: `I`,  `V`,  `X`,  `L`,  `C`,  `D`  and  `M`.

**Symbol**       **Value**
I             1
V             5
X             10
L             50
C             100
D             500
M             1000

For example, `2`  is written as  `II` in Roman numeral, just two one's added together.  `12`  is written as `XII`, which is simply  `X + II`. The number  `27`  is written as  `XXVII`, which is  `XX + V + II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not  `IIII`. Instead, the number four is written as  `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as  `IX`. There are six instances where subtraction is used:

-   `I`  can be placed before  `V`  (5) and  `X`  (10) to make 4 and 9.
-   `X`  can be placed before  `L`  (50) and  `C`  (100) to make 40 and 90.
-   `C`  can be placed before  `D`  (500) and  `M`  (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer.
## 코드
```
var romanToInt = function(s) {
    
    const symbol = {
        I:1,
        V:5,
        X:10,
        L:50,
        C:100,
        D:500,
        M:1000
    };
    
    let result = 0;
    
    for(let i = 0; i<s.length; i++){
        if(symbol[s[i]]<symbol[s[i+1]]){
            result -= symbol[s[i]]
            continue;
        }
        result += symbol[s[i]]
    }
    return result;
};
```
## 후기
유의해야 할 조건은 언제 뺄셈이 되는가. 다시 말해, IV는 4이고, VI는 6이라는 값이 되는 기준이 무엇인가. 답은  첫번째 글자의 값이 두번째 글자의 값보다 작을 때, 첫번째 글자의 값에 -를 부여한다는 것이다. 
먼저 Hash Table을 사용해서 글자(I, V, X...)에 해당하는 값을 부여한다. 이후 iteration을 통해 모든 글자를 순회하며, 글자에 부합하는 값을 가져오고 조건에 따라 값을 더하거나 빼는 형태로 문제를 풀 수 있다.


