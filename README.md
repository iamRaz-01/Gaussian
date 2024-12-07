# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm

1. **Input the number of equations (`n`)**:
   - Read an integer value `n` representing the number of equations.

2. **Initialize matrices and vectors**:
   - Create a matrix `a` of size `n x (n+1)` initialized to zeros to store the augmented matrix.
   - Create a vector `x` of size `n` initialized to zeros to store the solution.

3. **Input the augmented matrix**:
   - For each row `i` (from 0 to `n-1`), input `n+1` values corresponding to the coefficients and constants of the equations.

4. **Perform Gaussian Elimination**:
   - For each pivot row `i`:
     1. **Check for zero pivot**: If `a[i][i]` is `0.0`, exit the program with a divide-by-zero error message.
     2. For each row `j` below the pivot row (`i+1` to `n-1`):
        - Compute the ratio `ratio = a[j][i] / a[i][i]`.
        - Update the row `j` by subtracting `ratio * row i` for each column `k` (from 0 to `n`).

5. **Perform Back Substitution**:
   - Compute the solution vector `x` starting from the last equation:
     1. Set `x[n-1] = a[n-1][n] / a[n-1][n-1]` (solution for the last variable).
     2. For each row `i` (from `n-2` to 0):
        - Set `x[i] = a[i][n]`.
        - Subtract the contributions of already computed variables from `x[i]`.
        - Divide by the pivot element `a[i][i]` to get the value of `x[i]`.

6. **Output the solution**:
   - Print the solution vector `x` with two decimal precision.

## Program:
```python
'''Program to solve a matrix using Gaussian elimination without partial pivoting.
Developed by: Abdul Rasak N  
RegisterNumber: 24002896
'''
import numpy as np
import sys 
n = int(input())
a = np.zeros((n,n+1))
x = np.zeros(n)
for i in range(n):
    for j in range(n+1):
        a[i][j] = float(input())
for i in range(n):
    if a[i][j] ==0.0:
        sys.exit("Divide by zero detected!")
    for j in range(i +1 , n):
        ratio = a[j][i]/a[i][i]
        for k in range(n+1):
            a[j][k] = a[j][k] - ratio * a[i][k]
x[n-1] = a[n-1][n]/a[n-1][n-1]
for i in range(n-2,-1,-1):
    x[i] =a[i][n]
    for j in range(i+1,n):
        x[i] = x[i] - a[i][j] * x[j]
    x[i] = x[i]/a[i][i]
for i in range(n):
    print('X%d = %0.2f'%(i,x[i]),end = " ")
```

## Output:
![image](https://github.com/user-attachments/assets/c095da95-8089-46a4-9770-968e932bfcaa)


## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

