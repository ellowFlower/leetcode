# 695. Max Area of Island
The idea is to use dfs for every island and count all 1's within the island. Then return the max count of all islands.

## Code
```go
type coordinates struct {
	row int
	col int
}

func dfs(g [][]int, c coordinates, visited map[coordinates]bool) int {
	rowLen := len(g[0])
	colLen := len(g)
	// do not visit outside grid, 0 and already visited elements
	if c.col < 0 || rowLen == c.col || c.row < 0 || colLen == c.row || g[c.row][c.col] == 0 || visited[c] {
		return 0
	}
	visited[c] = true
	// every time we reach the return we found a new 1 element thus increase the result by one
	return 1 + dfs(g, coordinates{c.row, c.col + 1}, visited) + // right neighbours
		dfs(g, coordinates{c.row, c.col - 1}, visited) + // left neighbours
		dfs(g, coordinates{c.row + 1, c.col}, visited) + // down neighbours
		dfs(g, coordinates{c.row - 1, c.col}, visited) // up neighbours
}

func maxAreaOfIsland(grid [][]int) int {
	visited := make(map[coordinates]bool) // coordinates of all visited 1
	result := 0
	for rowIndex, row := range grid {
		for colIndex := range row {
			// dfs only for 1 which are not visited
			if grid[rowIndex][colIndex] == 1 && !visited[coordinates{row: rowIndex, col: colIndex}] {
				result = max(result, dfs(grid, coordinates{row: rowIndex, col: colIndex}, visited))
			}
		}
	}
	return result
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

```
