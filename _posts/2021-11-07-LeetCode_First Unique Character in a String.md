---
title: LeetCode_First Unique Character in a String
author: 다연
date: 2021-11-07 00:07:00 +0900
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy, String, Hash Table]
---
## [문제](https://leetcode.com/problems/first-unique-character-in-a-string/)

Given a string `s`, _find the first non-repeating character in it and return its index_. If it does not exist, return `-1`.
## 코드
```
var firstUniqChar = function(s) {
    let wordMap = new Map();
    
    for(let i = 0; i<s.length; i++){
        if(!wordMap.has(s[i])){
            wordMap.set(s[i], 1);
            continue;
        }
        wordMap.set(s[i], 2);
    }
    for(let i = 0; i<s.length;i++){
        if(wordMap.get(s[i])===1) return i;
    }
    return -1;
};
```
## 후기
1. Map에 존재하지 않는 새로운 문자가 들어올 시, Map에 해당 문자를 key, value는 1로 세팅한다. 그러나 이미 존재하는 문자가 입력될 경우 value를 2로 변경해서 한 번만 사용된 문자와 구분한다.
2. 이후 for문을 돌면서 Map에서 value가 1인 key가 존재하는 경우, 인덱스인 i를 반환한다.
3. 그러나 Map에 value가 1인 key가 없는 경우 for문을 다 순회할 것이다. 이 때는 -1을 return 한다.
4. 코드를 작성하다 보면 if else문을 사용할지, continue문을 사용할지 고민이 될 때가 있다. 실무적인 면에서는 continue를 남발하는 것이 적절하지 않다는 이야기가 있으나, (애러 처리나 구조/기능 변경 시 다양한 실수를 유발할 수 있고, 자원 관리 측면의 문제가 있기 때문.) 적절한 선에서 사용 중이다. 이 부분은 기회가 되면 따로 정리해보는 것도 좋을 것 같다.
