# Diameter-of-Binary-Tree
Given the root of a binary tree, return the length of the diameter of the tree.  The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.  The length of a path between two nodes is represented by the number of edges between them.


class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        def diameter(node, res):
            if not node:
                return 0
            
            left = diameter(node.left, res)
            right = diameter(node.right, res)

            res[0] = max(res[0], left + right)
            
            return max(left, right) + 1
        
        res = [0]
        diameter(root, res)
        return res[0]
