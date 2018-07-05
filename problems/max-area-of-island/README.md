# Leetcode: Max Area of Island     :BLOG:Medium:


---

Max Area of Island  

---

Given a non-empty 2D array grid of 0's and 1's, an island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.  

Find the maximum area of an island in the given 2D array. (If there is no island, the maximum area is 0.)  

    Example 1:
    [[0,0,1,0,0,0,0,1,0,0,0,0,0],
     [0,0,0,0,0,0,0,1,1,1,0,0,0],
     [0,1,1,0,1,0,0,0,0,0,0,0,0],
     [0,1,0,0,1,1,0,0,1,0,1,0,0],
     [0,1,0,0,1,1,0,0,1,1,1,0,0],
     [0,0,0,0,0,0,0,0,0,0,1,0,0],
     [0,0,0,0,0,0,0,1,1,1,0,0,0],
     [0,0,0,0,0,0,0,1,1,0,0,0,0]]
    Given the above grid, return 6. Note the answer is not 11, because the island must be connected 4-directionally.

    Example 2:
    [[0,0,0,0,0,0,0,0]]
    Given the above grid, return 0.

Note: The length of each dimension in the given grid does not exceed 50.  

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/max-area-of-island)  

Credits To: [leetcode.com](https://leetcode.com/problems/max-area-of-island/description/)  

Leave me comments, if you have better ways to solve.  

---

    ## Blog link: https://code.dennyzhang.com/max-area-of-island
    ## Basic Ideas: DFS
    ##              For each dfs, return the positions it has changed.
    ## Complexity:
    class Solution(object):
        def maxAreaOfIsland(self, grid):
            """
            :type grid: List[List[int]]
            :rtype: int
            """
            self.row_count = len(grid)
            if self.row_count == 0: return 0
            self.col_count = len(grid[0])
            max_count = 0
            for i in xrange(self.row_count):
                for j in xrange(self.col_count):
                    if grid[i][j] == 1:
                        max_count = max(max_count, self.DFSMark(grid, i, j))
            return max_count
    
        def DFSMark(self, grid, i, j):
            if i < 0 or i >= self.row_count \
                or j < 0 or j >= self.col_count:
                return 0
    
            # stop digging, if not 1
            if grid[i][j] != 1:
                return 0
    
            res = 1
            grid[i][j] = 0
            # mark four positions in a recursive way
            res += self.DFSMark(grid, i-1, j)
            res += self.DFSMark(grid, i+1, j)
            res += self.DFSMark(grid, i, j-1)
            res += self.DFSMark(grid, i, j+1)
            return res