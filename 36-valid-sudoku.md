# 36. Valid Sudoku

The 3 given rules to make a sudoku valid are:
1. Each row must contain the digits 1-9 without repetition.
2. Each column must contain the digits 1-9 without repetition.
3. Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.

These rules can be translated into having no duplicates within a row, column, and a 3x3 box. The implementation loops through the sudoku board and uses 3 seperate data structures to save the visited values per row, column, and box. If a newly visited value is already in one of the data structures, false is returned. If it was possible to go through the whole board, true is returned.  

To group values of one 3x3 box together, the indexes of the values are divided by 3 and rounded down to the next integer value. 

## Code
```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        boxes = defaultdict(set) # key: (row // 3, col // 3), value: value
        rows = defaultdict(set) # key: row number, value: value
        cols = defaultdict(set) # key: col number, value: value
        
        for row in range(9):
            for col in range(9):
                if (board[row][col] != "."
                 and (board[row][col] in boxes[(row // 3, col // 3)]
                 or board[row][col] in rows[row]
                 or board[row][col] in cols[col])):
                    return False
                boxes[(row // 3, col // 3)].add(board[row][col])
                rows[row].add(board[row][col])
                cols[col].add(board[row][col])
        
        return True
```
