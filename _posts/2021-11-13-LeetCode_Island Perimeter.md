---
title: LeetCode_Island Perimeter  
author: 다연
date: 2021-11-13 21:02:00 +0900
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy, DFS]
---
# [Island Perimeter](https://leetcode.com/problems/island-perimeter/)

You are given  `row x col`  `grid`  representing a map where  `grid[i][j] = 1`  represents land and  `grid[i][j] = 0`  represents water.

Grid cells are connected  **horizontally/vertically**  (not diagonally). The  `grid`  is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells).

The island doesn't have "lakes", meaning the water inside isn't connected to the water around the island. One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.
> **Input:** grid = [[0,1,0,0],[1,1,1,0],[0,1,0,0],[1,1,0,0]]  
**Output:** 16

> **Input:** grid = [[1]]  
**Output:** 4  

> **Input:** grid = [[1,0]]  
**Output:** 4  


# 코드
---
```JavaScript
var islandPerimeter = function(grid) {
    var dx = [1, -1, 0, 0];
    var dy = [0, 0, -1, 1];
    let cnt = 0;
    
    for(let i =0; i<grid.length; i++){
        for(let j = 0; j<grid[0].length; j++){
            if(grid[i][j]!=1) continue;
            
            for(let k = 0; k<dx.length;k++){
                if(i+dx[k]<0||j+dy[k]<0){
                    cnt++;
                    continue;
                }
                if(i+dx[k]>grid.length-1||j+dy[k]>grid[0].length-1){
                    cnt++
                    continue;
                }
                
                if(grid[i+dx[k]][j+dy[k]]!=0) continue;
                cnt++;
            }      
        }
    }
    return cnt;
};
```  
# Submission Detail
---
Runtime:  **160 ms**  
: Your runtime beats 92.67 % of javascript submissions.  
  
Memory Usage:  **48 MB**  
: Your memory usage beats 81.80 % of javascript submissions.  

# 후기
---
1. 2차원 배열에서 상하좌우 탐색을 진행할 때, x&y 이동 값을 배열 값으로 선언해두변 차후 탐색을 진행할 때 편리하다.
2. 3번째 for문에서 3가지의 if문으로 조건을 분리했는데, 1번과 2번 if문은 가독성을 위해 분리했고, 3번 if문의 경우 1번과 2번 if문을 거치지 않은 상황에서 3번 if문에 진입하게 되면 out of index에 진입하게 되며 오류가 발생하기 때문에 별도로 분리를 했다. 
