
# Game Of Life

https://leetcode.com/problems/game-of-life/

- Time: O(mn)
- Space: O(1)


```python
class Solution:
    # Space: O(1)
    # Time: O(mn) two passes
    # How should i bring it down to one pass?
    def gameOfLife(self, board: List[List[int]]) -> None:
        
        # Corner Cases
        if len(board) == 0:
            return
        
        if len(board[0]) == 0:
            return
        
        n, m = len(board), len(board[0])
        
        # Convenience function to get value on board
        # mode = 1, old value is msb
        # mode = 0, whole integer is old value
        def val_at(i, j, mode):
            
            # Outof bounds
            if i < 0 or j < 0 or i >= n or j >= m:
                return 0
            
            # Get old value
            if mode:
                return board[i][j] >> 1
            # Get the whole integer
            else:
                return board[i][j]
            
        # Convenience function to compute
        # new value from old value and number of live neighbors
        def new_val(old, neighbors):
            # If cell is live
            if old:
                if neighbors < 2 or neighbors > 3:
                    return 0
                else:
                    return 1
            # if cell is dead
            else:
                if neighbors == 3:
                    return 1
                else:
                    return 0
            
            
        for i in range(n):
            for j in range(m):
                neighbors = (val_at(i-1, j-1, 1) + 
                val_at(i-1, j, 1) +
                val_at(i-1, j+1, 1) +
                val_at(i, j-1, 1) +
                val_at(i, j+1, 0) +
                val_at(i+1, j-1, 0) +
                val_at(i+1, j, 0) +
                val_at(i+1, j+1, 0))
                
                # Attaching new state of cell
                # as lsb to existing integer
                old = board[i][j]
                board[i][j] = board[i][j] << 1
                board[i][j] += new_val(old, neighbors)
        
        for i in range(n):
            for j in range(m):
                board[i][j] = board[i][j] & 1
        
```
