# 733. Flood Fill

I hate bfs and dfs.

We can solve this question with 2 different ways.

The solution suggests dfs but I solved this with bfs.

```
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, newColor: int) -> List[List[int]]:
        m = len(image)
        n = len(image[0])
        visited = []
        queue = []
        queue.append((sr,sc))
        visited.append((sr,sc))

        x = [-1, 0, 0, 1]
        y = [0, -1, 1, 0]

        color = image[sr][sc]
        image[sr][sc] = newColor

        while(queue):
            pointx, pointy = queue.pop(0)   
            for dx,dy in zip(x,y):
                if 0<= pointx+dx < m and 0<= pointy+dy < n and (pointx+dx,pointy+dy) not in visited and image[pointx+dx][pointy+dy] == color:
                    visited.append((pointx+dx,pointy+dy))
                    queue.append((pointx+dx,pointy+dy))    
                    image[pointx+dx][pointy+dy] = newColor

        return image
```
So basically, we need a queue and `visited` array to keep tracking steps. (steps? I don't know.. 'The procedure' maybe)

After that, I set a dx, dy index.

In the while loop, we traverse the indices of 4 directions of current index.

Here is an important thing.

We need to check the `valid range` of indices. For example, index of (-1,1) is not valid.

Both `current_x + dx` and `current_y + dy` should be 0<= `BOTH` < m or n.

And `current_x + dx` and `current_y + dy` should not be in `visited` list.

Finally `current_x + dx` and `current_y + dy` should be same color of the `initial` one which is `image[sr][sc]`.

```
Complexity Analysis (same as dfs)

Time Complexity: O(N), where N is the number of pixels in the image.
We might process every pixel.

Space Complexity: O(N), the size of the implicit call queue when calling bfs.

```
