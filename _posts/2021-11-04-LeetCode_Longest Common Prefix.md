---
title: LeetCode_Longest Common Prefix
author: 다연
date: 2021-11-04 15:35:00 +0900
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy, String]
---

## [문제](https://leetcode.com/problems/longest-common-prefix/)
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string  `""`.
## 코드
```
var longestCommonPrefix = function(strs) {
    let commonPrefix = strs[0];
    for(let i =1;i<strs.length;i++){
        let tmp = '';
        for(let j = 0; j<strs[i].length;j++){
            if(strs[i][j]!=commonPrefix[j]) break;
            
            tmp += strs[i][j]
        }
        if(tmp.length<commonPrefix.length) commonPrefix = tmp
    }
    return commonPrefix
};
```
## 후기
1. Edge Case(가령 strs의 길이가 0인 경우)에 대해 작성하지 않았다. 다음에는 해당 부분 역시 고려할 것.
2. Time Complexity와 Space Complexity 정확한 값 역시 생각할 것. 

