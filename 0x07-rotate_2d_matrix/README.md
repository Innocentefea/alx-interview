To rotate a 2D matrix, you can apply a simple algorithm that involves transposing the matrix and then reversing each row (or reversing each column) of the transposed matrix. This can be done in-place, meaning the original matrix is modified without the need for additional storage.

Here's an example implementation in Python:

```python
def rotate_2d_matrix(matrix):
    n = len(matrix)  # Assuming the matrix is a square matrix
    
    # Transpose the matrix
    for i in range(n):
        for j in range(i, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
    
    # Reverse each row (or column) of the transposed matrix
    for i in range(n):
        matrix[i] = matrix[i][::-1]  # Reverse the row (or column)
    
    return matrix
```

Here's how you can use the `rotate_2d_matrix` function:

```python
# Example input matrix
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

rotated_matrix = rotate_2d_matrix(matrix)
print(rotated_matrix)
```

This will output:

```
[[7, 4, 1],
 [8, 5, 2],
 [9, 6, 3]]
```

The resulting matrix is the original matrix rotated 90 degrees clockwise. You can modify the code if you need a different rotation direction or if your matrix is not square.
