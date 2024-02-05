The N-Queens problem is a classic puzzle that involves placing N chess queens on an N×N chessboard in such a way that no two queens threaten each other. In other words, no two queens should be in the same row, column, or diagonal.

Here's a Python implementation of the N-Queens problem using a backtracking algorithm:

```python
def solve_nqueens(n):
    def is_safe(board, row, col):
        # Check if it is safe to place a queen at the given position
        for i in range(row):
            if board[i] == col or \
               board[i] - col == i - row or \
               board[i] - col == row - i:
                return False
        return True

    def backtrack(board, row):
        # Base case: all queens have been placed
        if row == n:
            solutions.append(board[:])
            return

        for col in range(n):
            if is_safe(board, row, col):
                board[row] = col
                backtrack(board, row + 1)
                board[row] = -1

    solutions = []
    board = [-1] * n
    backtrack(board, 0)
    return solutions

# Example usage
n = 4
solutions = solve_nqueens(n)
for solution in solutions:
    for row in solution:
        line = ['.'] * n
        line[row] = 'Q'
        print(' '.join(line))
    print()
```

In this implementation, the `solve_nqueens` function takes an integer `n` as input, representing the size of the chessboard and the number of queens to be placed. It uses a recursive backtracking algorithm to find all possible solutions to the N-Queens problem.

The `is_safe` function checks whether it is safe to place a queen at a given position on the board. It verifies that there are no other queens in the same row, column, or diagonal.

The `backtrack` function is the main backtracking algorithm. It iterates over each column in the current row and checks if it is safe to place a queen there. If it is, the queen is placed, and the algorithm proceeds recursively to the next row. If a solution is found, it is added to the `solutions` list. After each recursive call, the queen is removed from the board to explore other possibilities.

Finally, the example usage section demonstrates how to use the `solve_nqueens` function to find and print all the solutions for a 4x4 chessboard.

Note that the N-Queens problem becomes computationally expensive for large values of `n` due to the exponential number of possible solutions. Therefore, the algorithm might take a long time or be impractical for larger board sizes.
