# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
 * Forward Elimination:
   * Pivot Selection: Identify the pivot element in the current column (the largest absolute value below the diagonal).
   * Row Swapping: If necessary, swap rows to bring the pivot element to the diagonal position.
   * Elimination: Use row operations to eliminate elements below the pivot in the current column.
 * Backward Substitution:
   * Solve for the last variable: Starting from the last equation, solve for the last variable.
   * Back-substitute: Substitute the value of the last variable into the previous equation and solve for the second-to-last variable.
   * Repeat: Continue back-substituting until all variables are solved.
 * Check for Inconsistency:
   * If at any point during the elimination process, a row reduces to [0 0 ... 0 | non-zero], the system is inconsistent and has no solution.
 * Check for Infinite Solutions:
   * If a row reduces to [0 0 ... 0 | 0], the system is dependent and has infinitely many solutions.

## Program:
```
/*
Program to find the solution of a matrix using Gaussian Elimination.
Developed by:kamesh s
RegisterNumber:24006280
*/
```
import numpy as np
import sys

# Reading number of unknowns
n = int(input())

# Making numpy array of n x n+1 size and initializing 
# to zero for storing augmented matrix
a = np.zeros((n,n+1))

# Making numpy array of n size and initializing 
# to zero for storing solution vector
x = np.zeros(n)

# Reading augmented matrix coefficients
for i in range(n):
    for j in range(n+1):
        a[i][j] = float(input())

# Applying Gauss Elimination
for i in range(n):
    if a[i][i] == 0.0:
        sys.exit('Divide by zero detected!')
        
    for j in range(i+1, n):
        ratio = a[j][i]/a[i][i]
        
        for k in range(n+1):
            a[j][k] = a[j][k] - ratio * a[i][k]

# Back Substitution
x[n-1] = a[n-1][n]/a[n-1][n-1]

for i in range(n-2,-1,-1):
    x[i] = a[i][n]
    
    for j in range(i+1,n):
        x[i] = x[i] - a[i][j]*x[j]
    
    x[i] = x[i]/a[i][i]

# Displaying solution
for i in range(n):
    print('X%d = %0.2f' %(i,x[i]), end = ' ')

## Output:
![Screenshot 2024-12-17 154525](https://github.com/user-attachments/assets/8ee35cdd-f72d-4acb-a11d-74ea7101d605)

![gaussian elimination]()


## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

