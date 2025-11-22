[Link to ChatGPT chat](https://chatgpt.com/share/691f51ac-5c68-8003-be7f-e765ba9551fd)

In this study session, I'll be solving some LeetCode problems using python.

## **[Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)**

For this problem I came up with the following solutions:

### Using a set:

Runtime: 13ms ; Memory :31.52 MB; Time Complexity: O(n) ; Space Complexity: O(n)
```Python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
		# create a set to store the elements, 
		#if any element is already in the set,return true
        
        seen = set()
        for num in nums:
            if num in seen:
                return True
            else:
                seen.add(num)
        return False
```

## Sort the list and check 2 consecutive values.

Runtime: 43ms ; Memory :26.8 MB; Time Complexity: O(n log n) ; Space Complexity: O(n)
The n log n time complexity comes from the call to sort.
```Python
class Solution:

    def containsDuplicate(self, nums: List[int]) -> bool:
        # sort the list in place, and check if 2 consecutive elements are the same.
        nums.sort()
        for i in range(len(nums) - 1):
            if nums[i] == nums[i + 1]:
                return True
        return False
```

## Use a set to remove duplicates and compare the size

Runtime: 23ms ; Memory :31.65 MB; Time Complexity: O(n) ; Space Complexity: O(n)
```Python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(set(nums)) != len(nums)
```

***Notice***: Despite the first and last solutions being O(n) time complexity, the first could achieve lower run times since it doesn't necessarily needs to insert all elements in the set. This is a great example that shows how time complexity and run time although related, are still two different concepts.


## **[Maximum Sub Array](https://leetcode.com/problems/maximum-subarray/)**

Runtime 60ms; Memory: 32.82MB ; Time Complexity: O(n) ; Space Complexity: O(1)
```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:

        total = 0
        result = nums[0]

        for num in nums:
            if total < 0:
                total = 0
            total += num
            
            result = max(result, total)
        return result
```

## **[Binary Tree In Order Traversal ](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)**

```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if(root == None):
            return []
        result = []
        
        if(root.left != None):
            result.extend( self.inorderTraversal(root.left) )
        ## Do something with the current node
        result.append(root.val)
        
        if(root.right != None):
            result.extend( self.inorderTraversal(root.right) )
        
        return result
```

## **[Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)**
At first I tried implementing a recursive solution to the problem. It passed the example test cases but failed on some hidden tests, but had some issues caused by nodes exponentially being none.
I solved this by adding a check for this case at the beginning of the build output function.

This solution works but is rather slow, also it modifies the output list while also iterating over it.
It is messy and hard to read.

Time Complexity: O(n)
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:

    def levelOrder(self, root):
        output =[]
        visited = set()

        def buildOutput(node, currentLevel):
            # mark the node as visited
            if node is None:
                return
            visited.add(node)

            # create a new level in output if neede
            if len(output) < currentLevel + 1:
                output.append([node])
            else:
                # if the level already exists, just add the node value
                output[currentLevel].append(node)

            # repeat the procedure for each node in the current level
            for n in output[currentLevel]:
                if n.left not in visited:
                    buildOutput(n.left, currentLevel + 1)
                if n.right not in visited:
                    buildOutput(n.right, currentLevel + 1)

        buildOutput(root, 0)

        # result = map(lambda level: [node.val for node in level], output)
        result = [[node.val for node in level] for level in output]

        return result

```

A better more readable solution is to use a queue to store the nodes in the order they are visited, and pop them into an array to store the nodes in a per level basis.

The key point in this solution, is in the inner for loop:
`for _ in range(level_size)`
This makes sure only the nodes from the same level are popped from the queue and stored in the level list.

```Python


from collections import deque

class Solution:

    def levelOrder(self, root):
        if not root:
            return []
        
        result = []
        queue = deque([root])

        while queue:
            level_size = len(queue)
            level = []

            for _ in range(level_size):
                node = queue.popleft()
                level.append(node.val)

                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            result.append(level)
        
        return result

```