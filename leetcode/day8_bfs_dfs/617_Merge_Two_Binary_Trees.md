# 617. Merge Two Binary Trees

I hate BFS and DFS...
We can solve this problem with 2 different approaches.

The first one is recursive one.

```
class Solution:
    def mergeTrees(self, root1: Optional[TreeNode], root2: Optional[TreeNode]) -> Optional[TreeNode]:
        if root1 == None:
            return root2
        elif root2 == None:
            return root1

        root1.val += root2.val

        root1.left = self.mergeTrees(root1.left, root2.left)
        root1.right = self.mergeTrees(root1.right, root2.right)

        return root1
```
First, we need to check whether the binary tree is None.

If None, set it to another binary tree.


Complexity Analysis:

Time complexity : `O(m)`. A total of m nodes need to be traversed. Here, m represents the minimum number of nodes from the two given trees.

Space complexity : `O(m)`. The depth of the recursion tree can go upto m in the case of a skewed tree. In average case, depth will be `O(logm)`.
