# 695. Max Area of Island

Another DFS|BFS problem. YES!

First thought -> When we find '1' while we traverse the grid, do DFS or BFS -> add indices to `visited` array. -> if end, count += 1

And the code is

```
class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        m = len(grid)
        n = len(grid[0])
        maximum = 0
        count = 0
        queue = []
        visited = []

        x = [-1, 0, 0, 1]
        y = [0, -1, 1, 0]

        for i in range(m):
            for j in range(n):
                if grid[i][j] != 1:
                    continue
                else:
                    queue.append((i,j))
                    visited.append((i,j))
                    while(queue):
                        pointx, pointy = queue.pop(0)
                        count += 1
                        for dx, dy in zip(x,y):
                            if 0<=pointx+dx<m and 0<=pointy+dy<n and (pointx+dx,pointy+dy) not in visited and grid[pointx+dx][pointy+dy] == 1:
                                visited.append((pointx+dx,pointy+dy))
                                queue.append((pointx+dx,pointy+dy))
                    maximum = max(maximum, count)
                    count = 0
        return maximum
```
I did BFS here.

However, it is slower than I expected.
