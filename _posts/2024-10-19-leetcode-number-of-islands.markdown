---
layout: post
title:  "Leetcode: Number of Islands"
date:   2024-10-19 23:25:14 -0700
categories: leetcode
---

# Number of Islands Problem using DFS in Python

The **Number of Islands** problem is a common interview question where you're given a 2D grid of '1's (land) and '0's (water). The goal is to count how many islands exist. An island is defined as a group of adjacent '1's connected horizontally or vertically.

## Approach
The approach uses Depth-First Search (DFS). Starting from a '1', we recursively visit all connected '1's, marking them as visited (by changing them to '0'). Each time we initiate a DFS, it indicates the discovery of a new island.

## Python Code using DFS
```python
def numIslands(grid):
    if not grid:
        return 0

    def dfs(i, j):
        if i < 0 or i >= len(grid) or j < 0 or j >= len(grid[0]) or grid[i][j] == '0':
            return
        grid[i][j] = '0'  # Mark the current cell as visited
        dfs(i+1, j)  # Visit the neighbor down
        dfs(i-1, j)  # Visit the neighbor up
        dfs(i, j+1)  # Visit the neighbor right
        dfs(i, j-1)  # Visit the neighbor left

    islands = 0
    for i in range(len(grid)):
        for j in range(len(grid[0])):
            if grid[i][j] == '1':  # Start a DFS if we find an unvisited land
                dfs(i, j)
                islands += 1  # One DFS call represents one island
    return islands

# Example usage
grid = [
  ["1", "1", "0", "0", "0"],
  ["1", "1", "0", "0", "0"],
  ["0", "0", "1", "0", "0"],
  ["0", "0", "0", "1", "1"]
]
print(numIslands(grid))  # Output: 3
```
## Explanation
### DFS Traversal: 
When we encounter a '1', we trigger a DFS to explore all connected lands (horizontally and vertically) and mark them as '0' (visited).
### Counting Islands: 
Each time we initiate a DFS from a '1', we count that as one island.