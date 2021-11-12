---
title: LeetCode_Flood Fill
author: 다연
date: 2021-11-12 23:25:00 +0900
categories: [Algorithm, LeetCode]
tags: [LeetCode, easy, DFS]
---
# [Flood Fill](https://leetcode.com/problems/flood-fill/)

An image is represented by an  `m x n`  integer grid  `image`  where  `image[i][j]`  represents the pixel value of the image.

You are also given three integers  `sr`,  `sc`, and  `newColor`. You should perform a  **flood fill**  on the image starting from the pixel  `image[sr][sc]`.

To perform a  **flood fill**, consider the starting pixel, plus any pixels connected  **4-directionally**  to the starting pixel of the same color as the starting pixel, plus any pixels connected  **4-directionally**  to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with  `newColor`.

Return  _the modified image after performing the flood fill_.
> **Input:** image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, newColor = 2  
**Output:** [[2,2,2],[2,2,0],[2,0,1]]

> **Input:** image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, newColor = 2  
**Output:** [[2,2,2],[2,2,2]]  

# 과정
---
> I:  MxN Matrix, sr(Integer), sc(Integer), newColor(Integer)  
O:  MxN Matrix  
C:  1 <= m, n <= 50, 0<= sr < m, 0<= sc < n  

> DS:  Array  
Algo: DFS  


> Pseudo:  

```
[[1,1,1],
[1,"1",0],
[1,0,1]]

// val = image[sr][sc] // 1
[[1,1,1],
[1,"2",0],
[1,0,1]]

[[1,"1",1],
["1",2,"0"],
[1,"0",1]]

[["1",2,"1"],
[2,"2",0],
[1,0,1]]

[["2",2,"2"],
[2,"2",0],
[1,0,1]]

[0, 0, 0]
[0, "1", 1]

[0, 0, 0]
[0, "1", "1"]
```

> Time: O(n) // 이미지 내의 픽셀에 접근  
Space: O(n)  // DFS 호출 스택  

# 코드
---
```JavaScript
var floodFill = function(image, sr, sc, newColor) {
    let val = image[sr][sc];
    if(val == newColor) return image;
    
    floodFillMatrix(sr, sc);
    
    function floodFillMatrix(sr, sc){
        // out of boundary이거나, 값이 val과 일치하지 않으면 바로 return 
        if(sr<0 || sc<0 || sr>image.length-1 || sc>image[0].length-1 || image[sr][sc] !== val){ 
           return;
        }
        image[sr][sc] = newColor;
        floodFillMatrix(sr-1, sc); // 서쪽
        floodFillMatrix(sr+1, sc); // 동쪽
        floodFillMatrix(sr, sc-1); // 북쪽
        floodFillMatrix(sr, sc+1); // 남쪽
        // 상하좌우 탐색을 진행
    }
    return image;
};
```
# Submission Detail
---
Runtime:  **84 ms**  
: Your runtime beats 90.96 % of javascript submissions.  
  
Memory Usage:  **41.3 MB**  
: Your memory usage beats 29.46 % of javascript submissions.  

# 후기
---
1. newColor 값과 image[sr][sc] 값이 동일할 때 무한루프가 발생한다. 이에 관한 Edge Case를 잘 숙지해야 한다.
2. matrix에 접근할 때 out of boundary일 경우, Can not read property '?' of defined 오류가 발생하니 이 부분을 유의해야 한다.
