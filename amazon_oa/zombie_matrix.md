zombie matrix
---

# Description
Given a 2D grid, each cell is either a zombie or a human. Zombies can turn adjacent (up/down/left/right) human beings into zombies every day. Find out how many days does it take to infect all humans?

Input:
matrix, a 2D integer array where a[i][j] = 1 represents a zombie on the cell and a[i][j] = 0 represents a human on the cell.

Output:
Return an integer represent how many days does it take to infect all humans.
Return -1 if no zombie exists.

Example :
Input:
[[0, 1, 1, 0, 1],
[0, 1, 0, 1, 0],
[0, 0, 0, 0, 1],
[0, 1, 0, 0, 0]]

Output:
2

Explanation:
At the end of the day 1, the status of the grid:
[[1, 1, 1, 1, 1],
[1, 1, 1, 1, 1],
[0, 1, 0, 1, 1],
[1, 1, 1, 0, 1]]

At the end of the day 2, the status of the grid:
[[1, 1, 1, 1, 1],
[1, 1, 1, 1, 1],
[1, 1, 1, 1, 1],
[1, 1, 1, 1, 1]]

# Solution
```python3
def humanDays(matrix):
    """
    :type matrix: List[List[int]]
    :rtype: int
    """
    import collections
    if not len(matrix) or not len(matrix[0]) or not any([any(row) for row in matrix]):
        return -1
    
    directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
    def bfs(days):
        while q:
            days += 1
            for _ in range(len(q)):
                x, y = q.popleft()
                for direction in directions:
                    r, c = x + direction[0], y + direction[1]
                    if 0 <= r < m and 0 <= c < n and matrix[r][c] == 0:
                        matrix[r][c] = 1
                        q.append((r, c))
        return days
                
    
    m, n = len(matrix), len(matrix[0])
    q = collections.deque()
    for i in range(m):
        for j in range(n):
            if matrix[i][j] == 1:
                q.append((i, j))
    
    return bfs(-1)
```
