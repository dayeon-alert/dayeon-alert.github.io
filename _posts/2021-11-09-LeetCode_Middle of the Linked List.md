---
title: LeetCode_Middle of the Linked List
author: 다연
date: 2021-11-09 00:32:00 +0900
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy, Linked List, Two Pointers]
---
# [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

Given the  `head`  of a singly linked list, return  _the middle node of the linked list_.

If there are two middle nodes, return  **the second middle**  node.
>**Input:** head = [1,2,3,4,5]  
**Output:** [3,4,5]  
**Explanation:** The middle node of the list is node 3.

>**Input:** head = [1,2,3,4,5,6]  
**Output:** [4,5,6]  
**Explanation:** Since the list has two middle nodes with values 3 and 4, we return the second one.

# 과정
---
> I: Linked List  
O: the middle node of the Linked List  
C: 1<= the number of nodes <= 100, 1 <= node.val <= 100  
E: if head is null  

> DS: Linked List  
Algo: Iteration  


> Pseudo:  
```
1. 
s,f
[1, 2, 3, 4, 5]
2. 
    s  f
[1, 2, 3, 4, 5]
3. f.next is null
       s     f
[1, 2, 3, 4, 5]
4. 
s,f
[1, 2, 3, 4, 5, 6]
5. 
    s  f
[1, 2, 3, 4, 5, 6]
6.
       s     f
[1, 2, 3, 4, 5, 6]
7. f is null
          s        f
[1, 2, 3, 4, 5, 6]
```
{: file='Pseudo Code'}
> Time: O(N)  
Space: O(1)  

# 코드
---
```
var middleNode = function(head) {
    let first = head; // head를 가리키는 포인터.
    let second = head;
    
    while(first.next!==null&&first!==null){
        
        first = first.next.next;
        second = second.next;
    }
    
    return(second);
};
```
{: file='JavaScript'}
# Submission Detail
---
Runtime:  **68 ms**  
: Your runtime beats 89.83 % of javascript submissions.  
  
Memory Usage:  **39.1 MB**  
: Your memory usage beats 12.57 % of javascript submissions.  

# 후기
---
1. 절반의 위치에 도달하는 방법을 생각해낸다면 쉽게 풀 수 있다.
2. A가 두 칸을 갈 때 B는 한 칸을 간다. 이 때 A가 목적지에 도달했을 때 B는 당연히 목적지의 절반 거리만큼 도달해 있다. 라는 걸 떠올리면 된다.
