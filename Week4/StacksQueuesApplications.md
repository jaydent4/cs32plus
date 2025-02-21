# Applications of Stacks and Queues
Let's take a look at Homework 2's questions and implement the same thing in Python.

## Different Implementations
While we can implement the "Coord" class, we can use a different built-in data structure to store the coordinates instead.
```python
def pathExists(maze, nRows, nCols, sr, sc, er, ec):
    stack = [(sr, sc)] # Initialize a stack with a tuple containing sr and sc
    maze[sr][sc] = "!"
    while stack:
        i, j = stack.pop() # we can divide the tuple into i and j (i = first value in tuple, j = second value in tuple)
        if i == er and j == ec:
            return True
        if 0 <= i - 1 < nRows and (maze[i - 1][j] != "!" or maze[i - 1][j] != "X"):
            stack.append((i - 1, j))
            maze[i - 1][j] = "!"
        if 0 <= j + 1 < nCols and (maze[i][j + 1] != "!" or maze[i][j + 1] != "X"):
            stack.append((i, j + 1))
            maze[i][j + 1] = "!"
        if 0 <= i + 1 < nRows and (maze[i + 1][j] != "!" or maze[i + 1][j] != "X"):
            stack.append((i + 1, j))
            maze[i + 1][j] = "!"
        if 0 <= j - 1 < nCols and (maze[i][j - 1] != "!" or maze[i][j - 1] != "X"):
            stack.append((i, j - 1))
            maze[i][j - 1] = "!"
    return False
```

And here is a queue-based implementation too:
```python
def pathExists(maze, nRows, nCols, sr, sc, er, ec):
    queue = deque([(sr, sc)]) # Initialize a queue with a tuple containing sr and sc
    maze[sr][sc] = "!"
    while queue:
        i, j = queue.popleft() # we can divide the tuple into i and j (i = first value in tuple, j = second value in tuple)
        if i == er and j == ec:
            return True
        if 0 <= i - 1 < nRows and (maze[i - 1][j] != "!" or maze[i - 1][j] != "X"):
            queue.push((i - 1, j))
            maze[i - 1][j] = "!"
        if 0 <= j + 1 < nCols and (maze[i][j + 1] != "!" or maze[i][j + 1] != "X"):
            queue.push((i, j + 1))
            maze[i][j + 1] = "!"
        if 0 <= i + 1 < nRows and (maze[i + 1][j] != "!" or maze[i + 1][j] != "X"):
            queue.push((i + 1, j))
            maze[i + 1][j] = "!"
        if 0 <= j - 1 < nCols and (maze[i][j - 1] != "!" or maze[i][j - 1] != "X"):
            queue.push((i, j - 1))
            maze[i][j - 1] = "!"
    return False
```

Implementation-wised, the Python variant is very similar to the C++ variant.

## What are these?
Well, it turns out, both of these algorithms are two of the most important algorithms in all of CS (in my opinion). The stack-based implemention is called **Depth-First Search (DFS)**. Notice how we "reach all the way" on a specific path before we explore a different path. The queue-based implementation is called **Breath-First Search (BFS)**. Notice how we spread out (like a breath) in all paths at the same time.
While there are a lot of applications for these two algorithms (if you are curious, there is a whole class of problems called graph problems that mainly use these algorithms or some variation of it), we will just focus on applications involving matrices.

NOTE: Matrices can also be considered as graphs as graphs are a very general term for this type of data structure.

## Certain Qualities of BFS/DFS (but more of BFS)
Each of these algorithms have different qualities. However, in general, problems that DFS can solve can also be solved by BFS. However, the reverse is not necessarily true (at least easily). Questions BFS may not always be solved by DFS easily. Here are some qualities of BFS and DFS:

- If there is a path from one cell in a matrix to another cell in the matrix, BFS and DFS will find it
- If there is no path, BFS and DFS will return without ever reaching the cell.

**NOTE:** There are more elaborate proofs that show that these are true. However, that is not the goal of this lesson. For now, just assume that these are true or do my favorite type of proof--proof by "yeah that sounds kinda right."

Now, let us talk about a BFS specific quality (that DFS doesn't necessarily have)

- Assuming that moving from cell to cell doesn't have any cost or weight or all movement is equal cost or weight, BFS will return the shortest cost or weight path.

**NOTE:** Again, there is a more elaborate proof for this, but for now, let's use the hand-wavy proof of "yeah that makes sense." For some intuition, we can kind of see how BFS slowly explores all paths equally and stops once the first path reaches our goal, which implies that this first path is our shortest path.

## Another Example
Here's another example where we can use either BFS or DFS.

Let's say we have a 2D matrix consisting of 0's and 1's. 0 represents water and 1 represents land. We define an island as a grouping of 1's that are completely surrounded by the edge of the grid or by 0's (kind of like in real life). Count the total number of islands.
Implement the following function:
```python
def countIslands(grid):
    ...
```


EX:
```
grid = 
[[1, 1, 0],
 [1, 0, 1]
 [0, 1, 1]]

 countIslands(grid) should return 2 (the first island is the top left corner, the second island is the bottom right corner)
```

<details>
<summary>Solution</summary>

In this question, we can use either BFS or DFS (it doesn't matter). In order to count an island, we want to make sure we count all of the land cells of an island before moving on. Additionally, we need to make sure we don't recount any land spots. We can employ a similar strategy to the maze problem:

Pseudocode:
```
count = 0
Iterate through the grid
    if current cell is a "1" or land
        perform BFS/DFS from this cell (set each land to "0" or water as we perform BFS/DFS)
        increment count
return count
```

**TIP**: In general, it is a good idea to come up with some pseudocode before approaching any 

Here is how to do this in Python
```python
def dfs(grid, start_i, start_j):
    stack = [(start_i, start_j)]
    directions = [(1, 0), (0, 1), (-1, 0), (0, -1)]
    while stack:
        i, j = stack.pop()
        grid[i][j] = 0
        for di, dj in directions: # assigns di to the first item in each tuple and dj to the second item in each tuple
            if 0 <= i + di < len(grid) and 0 <= j + dj < len(grid[0]) and grid[i + di][j + dj] == 1:
                stack.append((i + di, j + dj))

def countIslands(grid):
    count = 0
    for i in range(len(grid)):
        for j in range(len(grid[0])):
            if grid[i][j] == 1:
                dfs(grid, i, j)
                count += 1
    return count
```

**TIP:** Create certain methods under their own separate function. Yes, we could stick the entire "dfs" code where "dfs(grid, i, j)" is called, but that makes the code harder to read, so don't do that.
**TIP:** When doing matrix BFS/DFS, do this to explore new cells:
```python
...
directions = [(1, 0), (0, 1), (-1, 0), (0, -1)]
for di, dj in directions:
    ...
```
It saves a lot of time (a lot less lines) compared checking every single direction in their own if-statement
</details>

## Final Thoughts
BFS and DFS are applicable to much more than just matrices (and you'll will probably see a lot more BFS/DFS questions that don't involve a matrix). However, the general idea is still same, matrix or not.


