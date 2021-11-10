---
title: LeetCode_Increasing Order Search Tree
author: 다연
date: 2021-11-10 23:09:00 +0900
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy, DFS]
---
# [Increasing Order Search Tree](https://leetcode.com/problems/increasing-order-search-tree/)
Given the `root` of a binary search tree, rearrange the tree in **in-order** so that the leftmost node in the tree is now the root of the tree, and every node has no left child and only one right child.
> **Input:** root = [5,3,6,2,4,null,8,1,null,null,null,7,9]  
**Output:** [1,null,2,null,3,null,4,null,5,null,6,null,7,null,8,null,9]

> **Input:** root = [5,1,7]  
**Output:** [1,null,5,null,7]
# 과정
---
> I: Tree  
O: Tree  
C: 0 <= Node.val <= 1000  

> DS: Tree  
Algo: Recursion  

> Time: O(N)  
Space: O(H)  

# 코드
---
``` console
var increasingBST = function(root) {
	let ansNode = new TreeNode(0);
    let cur = ansNode;
    inorder(root);
    function inorder(node){
        if(node === null) return;
        inorder(node.left); // L
        node.left = null; 
        cur.right = node; // U 
        cur = node;
        inorder(node.right); // R
    }
    return ansNode.right;
};
```
{: file='JavaScript'}
# Submission Detail
---
Runtime:  **76 ms**  
: Your runtime beats 73.31 % of javascript submissions.  
  
Memory Usage:  **40.1 MB**  
: Your memory usage beats 63.80 % of javascript submissions.  

# 후기
---
1. Recursion을 통해 가장 왼쪽에 위치한 노드에 접근한다.
2. 그리고 해당 노드가 null 값이면 종료하고 부모 노드로 올라온다.
3. 그리고 부모 노드의 Left 노드를 null 값으로 변경 후 현재 노드를  새로 만든 Tree에 값을 추가한다. 그리고 오른쪽을 탐색한다.
4. 그 다음 다시 부모 노드로 올라온다. 
5. 위와 같이 Bottom-up 접근 방식을 통해 문제를 풀 수 있다.
6. Space Complexity는 기본적으로 O(H)이지만, 최악의 경우는 O(N)이다.
```
      1
     / \
   2     5
  / \   / \
 3   4 6   7
```
	1. 1을 Stack에 추가. O(1)
	2. 1을 제거하고 2와 5를 추가. O(2)
	3. 2를 제거하고 3과 4를 추가. O(3)
	4. 3을 제거. O(2)
	5. 4를 제거. O(1)
	6. 5를 제거하고 6과 7을 추가. O(2)
	7. 6을 제거. O(1)
	8. 7을 제거. O(0)
	9. 이 때 최악의 Space는 O(3)으로 곧 높이와 동일한 것을 알 수 있다.
