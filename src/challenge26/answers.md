# Answer

## Python

```py
from collections import deque

def reconstruct_path(came_from, current_node):
    """Reconstructs the path from start to end node based on the came_from map."""
    total_path = [current_node]
    while current_node in came_from:
        current_node = came_from[current_node]
        total_path.append(current_node)
    return total_path[::-1]  # Reverse the path to start->end direction

def get_neighbors(grid, node):
    """Returns the non-diagonal, non-blocked neighbors of a node."""
    neighbors = []
    directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]  # Up, Down, Left, Right
    for dx, dy in directions:
        x, y = node[0] + dx, node[1] + dy
        if 0 <= x < len(grid) and 0 <= y < len(grid[0]) and grid[x][y] != 1:
            neighbors.append((x, y))
    return neighbors

def bfs(grid, start, end):
    """Performs BFS on the grid from start to end node, returns the path."""
    queue = deque([start])
    came_from = {start: None}

    while queue:
        current = queue.popleft()
        if current == end:
            break
        for neighbor in get_neighbors(grid, current):
            if neighbor not in came_from:
                queue.append(neighbor)
                came_from[neighbor] = current

    return reconstruct_path(came_from, end) if end in came_from else []

def create_new_path_grid(grid, path):
    """Marks the path on the grid by setting the path nodes to 2, optimized for readability and efficiency."""
    path_set = {node for node in path if node}
    new_grid = [[2 if (i, j) in path_set else cell for j, cell in enumerate(row)] for i, row in enumerate(grid)]
    return new_grid

start = (0, 0)
end =  (4, 4)
grid = [
    [0, 0, 0, 0, 0],
    [1, 1, 1, 1, 0],
    [0, 0, 0, 0, 0],
    [0, 1, 1, 1, 1],
    [0, 0, 0, 0, 0]
]

path = bfs(grid, start, end)
new_grid = create_new_path_grid(grid, path)

for row in new_grid:
    print(row)
```