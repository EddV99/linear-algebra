
# Table of Contents

1.  [Chapter 1 - Linear Equations](#org11566ec)
    1.  [System of Linear Equations](#orgcf6fd76)
        1.  [What is a Linear Equation?](#orgff976eb)
        2.  [System of Linear Equations (Linear System)](#org2e7b1d7)
        3.  [Solution Format (**not** how to solve them)](#org4cabfd0)
        4.  [Some Properties of Linear Systems](#orgd209427)
    2.  [Matrix Notation](#orgb8daac9)
        1.  [Size of Matrix](#org04cb65c)
    3.  [Solving a Linear System](#org6c0577f)
        1.  [Elementary Row Operations](#org0359655)
        2.  [Example of Solving a Linear System](#org27e6ed9)
    4.  [Existence and Uniqueness of Solution Set](#org3a83126)
        1.  [Two Fundamental Questions of a Linear System](#orgba8be00)
        2.  [How To Check If Linear System is Consistent?](#org810fc54)
    5.  [Row Reduction and Echelon Forms](#orgc20ec13)
        1.  [Echelon Form (Row Echelon Form) & Reduced Echelon Form (Reduced Row Echelon Form)](#org9c59bc3)
        2.  [Row Reduction](#org1cd1ae4)
        3.  [Pivot Positions](#orgba7c2e6)
        4.  [Row Reduction Algorithm](#org25391b6)
        5.  [Checking Existence and Uniqueness (continued&#x2026;)](#orga3c9c75)

Linear Algebra Notes

Textbook: Linear Algebra and Its Applications 5th Edition (David C. Lay,
Steven R. Lay, & Judi J. McDonald)


<a id="org11566ec"></a>

# Chapter 1 - Linear Equations


<a id="orgcf6fd76"></a>

## System of Linear Equations


<a id="orgff976eb"></a>

### What is a Linear Equation?

With variables x<sub>1</sub>, x<sub>2</sub>, &#x2026;, x<sub>n</sub> is an equation in the form:
a<sub>1</sub>x<sub>1</sub> + a<sub>2</sub>x<sub>2</sub> + &#x2026; + a<sub>n</sub>x<sub>n</sub> = b and `coefficients` a<sub>1</sub>, a<sub>2</sub>, &#x2026;, a<sub>n</sub> are real or complex numbers


<a id="org2e7b1d7"></a>

### System of Linear Equations (Linear System)

A system of linear equations are one or more linear equations that deal with the
same variables x<sub>1</sub>, &#x2026;, x<sub>n</sub>

An example of how one might look like:
2x<sub>1</sub> + 3x<sub>2</sub> + 1.4x<sub>3</sub> = 8
x<sub>1</sub>       -   3x<sub>3</sub> = -7


<a id="org4cabfd0"></a>

### Solution Format (**not** how to solve them)

The solution to a system of linear equations is a list (s<sub>1</sub>, s<sub>2</sub>, &#x2026;, s<sub>n</sub>) that
make <span class="underline">each</span> equation true when the solution values s<sub>1</sub>, s<sub>2</sub>, &#x2026;, s<sub>n</sub> are substituted
for x<sub>1</sub>, x<sub>2</sub>, &#x2026;, x<sub>n</sub>, respectively.


<a id="orgd209427"></a>

### Some Properties of Linear Systems

The set of all possible solutions is called the `solution set` of the linear system.

Two linear systems are said to be `equivalent` if they have the same solution set.

A System of Linear Equations has:

1.  No solution, or
2.  Exactly one solution, or
3.  Infinitely many solutions

A linear system is `inconsistent` if no solutions and `consistent` if one or infinitely many.


<a id="orgb8daac9"></a>

## Matrix Notation

We can represent the important information of a linear system in a form called a
`matrix`.

Consider the following linear system:

x<sub>1</sub> - 2x<sub>2</sub> +  x<sub>3</sub> = 0
     2x<sub>2</sub> - 8x<sub>3</sub> = 8
5x<sub>1</sub>      - 5x<sub>3</sub> = 10

Align the `coefficients` of each variable in columns, we create the following
`coefficient matrix`:
```math
\begin{bmatrix}
1 & -2 & 1\\
0 & 2 & -8\\
5 & 0 & -5
\end{bmatrix}
```
If we add the values of the right-hand side of the linear systems, we have the
`augmented matrix` of the system:
```math
\begin{bmatrix}
1 & -2 & 1 & 0\\
0 & 2 & -8 & 8\\
5 & 0 & -5 & 10
\end{bmatrix}
```

<a id="org04cb65c"></a>

### Size of Matrix

Just tells us how many rows and columns there are in a matrix

The coefficient matrix above has 3 rows and 3 columns and is called a 3x3 (read
&ldquo;3 by 3&rdquo;) matrix.

The augmented matrix above has 3 rows and 4 columns, a 3x4 matrix

**Number of rows always comes first**


<a id="org6c0577f"></a>

## Solving a Linear System

Solving a linear system is pretty easy. The basic idea is to take the x<sub>1</sub> term of
one linear equation and eliminate the x<sub>1</sub> terms from the other linear equations.
You do the same with x<sub>2</sub> and so on. In matrix form use an <span class="underline">augmented matrix</span>.


<a id="org0359655"></a>

### Elementary Row Operations

There are three row operations that can be used to help with the algorithm
discussed above. These operations work because they don&rsquo;t change the solution
set.

1.  (`Replacement`) Replace one row by the sum of itself and a multiple of another row

    Example:
    ```math    
    \begin{bmatrix}
    1 & -2 & 1\\\
    0 & 2 & -8\\\
    5 & 0 & -5
    \end{bmatrix}
   ``` 
    Add a multiple of -5 of row 1 to row 3
    
    row 1 \* -5: [-5 10 -5]
    row 3 + (row 1 \* -5): [-5 10 -5] + [5 0 -5] = [0 10 -10]
    
    The matrix becomes
   ```math 
    \begin{bmatrix}
    1 & -2 & 1\\
    0 & 2 & -8\\
    0 & 10 & -10
    \end{bmatrix}
    ```

2.  (`Interchange`) Interchange two rows

   ```math 
    \begin{bmatrix}
    1 & -2 & 1\\
    0 & 2 & -8\\
    5 & 0 & -5
    \end{bmatrix}
    ```
    
    Interchange row 1 and row 3
    The matrix becomes
   ```math 
    \begin{bmatrix}
    5 & 0 & -5\\
    0 & 2 & -8\\
    1 & -2 & 1
    \end{bmatrix}
    ```

3.  (`Scaling`) Multiply all entries in a row by a non-zero constant

   ```math 
    \begin{bmatrix}
    1 & -2 & 1\\
    0 & 2 & -8\\
    5 & 0 & -5
    \end{bmatrix}
   ``` 
    Scale row 1 by 4
    The matrix becomes
```math    
    \begin{bmatrix}
    4 & -8 & 4\\
    0 & 2 & -8\\
    5 & 0 & -5
    \end{bmatrix}
```

<a id="org27e6ed9"></a>

### Example of Solving a Linear System

The Linear System to Solve

x<sub>1</sub> - 2x<sub>2</sub> +  x<sub>3</sub> = 0
     2x<sub>2</sub> - 8x<sub>3</sub> = 8
5x<sub>1</sub>      - 5x<sub>3</sub> = 10

Augmented Matrix Form
```math
\begin{bmatrix}
1 & -2 & 1 & 0\\
0 & 2 & -8 & 8\\
5 & 0 & -5 & 10
\end{bmatrix}
```
`Scale` row 1 by 5
```math
\begin{bmatrix}
5 & -10 & 5 & 0\\
0 & 2 & -8 & 8\\
5 & 0 & -5 & 10
\end{bmatrix}
```
Add (-1 \* row 1) to row 3 (`replacement`)
```math
\begin{bmatrix}
5 & -10 & 5 & 0\\
0 & 2 & -8 & 8\\
0 & 10 & -10 & 10
\end{bmatrix}
```
Add (5 \* row 2) to row 1 (`replacement`)
Add (-5 \* row 2) to row 3 (`replacement`)
```math
\begin{bmatrix}
5 & 0 & -35 & 40\\
0 & 2 & -8 & 8\\
0 & 0 & 30 & -30
\end{bmatrix}
```
`Scale` row 1 by 1/5
`Scale` row 2 by 1/2
`Scale` row 3 by 1/30
```math
\begin{bmatrix}
1 & 0 & -7 & 8\\
0 & 1 & -4 & 4\\
0 & 0 & 1 & -1
\end{bmatrix}
```
Add (7 \* row 3) to row 1 (`replacement`)
Add (4 \* row 3) to row 2 (`replacement`)
```math
\begin{bmatrix}
1 & 0 & 0 & 1\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & -1
\end{bmatrix}
```
We have found the solution set *(1, 0, -1)*. Let&rsquo;s switch back from matrix form to
see another perspective.

x<sub>1</sub>       = 1
   x<sub>2</sub>    = 0
      x<sub>3</sub> = -1

Let&rsquo;s verify by plugging in the solution set in the original linear system

x<sub>1</sub> - 2x<sub>2</sub> +  x<sub>3</sub> = 0
     2x<sub>2</sub> - 8x<sub>3</sub> = 8
5x<sub>1</sub>      - 5x<sub>3</sub> = 10

Remember the solution set is (1, 0, -1), so x<sub>1</sub> = 1, x<sub>2</sub> = 0, and x<sub>3</sub> = -1. We
plug in

(1) - 2(0) +  (-1) = 0
      2(0) - 8(-1) = 8
5(1)       - 5(-1) = 10

Simplify

 0 = 0
 8 = 8
10 = 10

LHS and RHS agree, so this solution is valid

*This is an only solution, we&rsquo;ll see how infinitely many and no solutions look like later*


<a id="org3a83126"></a>

## Existence and Uniqueness of Solution Set


<a id="orgba8be00"></a>

### Two Fundamental Questions of a Linear System

1.  Is the system **consistent**; that is, at least one solution exist?
2.  If solution exists, is it the only one; that is, is the solution unique?


<a id="org810fc54"></a>

### How To Check If Linear System is Consistent?

One way to check for consistency is to put the augmented matrix in a triangular form.
Something like this
```math
\begin{bmatrix}
1 & * & * & * \\
0 & 3 & * & * \\
0 & 0 & 4 & * \\
0 & 0 & 0 & 7
\end{bmatrix}
```
**We will learn more about this form later**

When we have this form we can easily check if it will be solvable or for stuff
that doesn&rsquo;t make sense (in the example above the last row in equation form says
0 = 7), in that case no solution exists and it&rsquo;s inconsistent.


<a id="orgc20ec13"></a>

## Row Reduction and Echelon Forms


<a id="org9c59bc3"></a>

### Echelon Form (Row Echelon Form) & Reduced Echelon Form (Reduced Row Echelon Form)

A <span class="underline">rectangular</span> matrix is in `Echelon Form` if it has these three properties

1.  All nonzero rows are above any rows of all zeros
2.  Each leading entry of a row is in a column to the right of the leading entry
    of the row above it
3.  All entries in a column below a leading entry are zeros

The matrix is in `Reduced Echelon Form` if it also has these additional properties

1.  The leading entry in each nonzero row is 1
2.  Each leading 1 is the only nonzero entry in its column

Echelon Form Examples
    x is any nonzero value
    &diamond; is any value including zero
```math
\begin{bmatrix}
x & \diamond & \diamond & \diamond \\
0 & x & \diamond & \diamond \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}
```
```math
\begin{bmatrix}
x & \diamond & \diamond & \diamond & \diamond & \diamond \\
0 & x & \diamond & \diamond & \diamond & \diamond \\
0 & 0 & 0 & x & \diamond & \diamond \\
0 & 0 & 0 & 0 & x & \diamond \\
0 & 0 & 0 & 0 & 0 & x \\
\end{bmatrix}
```
Reduced Echelon Form
    x is any nonzero value
    &diamond; is any value including zero
```math
\begin{bmatrix}
1 & 0 & \diamond & \diamond \\
0 & 1 & \diamond & \diamond \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}
```
```math
\begin{bmatrix}
1 & 0 & \diamond & 0 & 0 & \diamond \\
0 & 1 & \diamond & 0 & 0 & \diamond \\
0 & 0 & 0 & 1 & 0 & \diamond \\
0 & 0 & 0 & 0 & 1 & \diamond \\
\end{bmatrix}
```

<a id="org1cd1ae4"></a>

### Row Reduction

Any nonzero matrix can be `row reduced` to an echelon form using any of the
elementary row operations

We find that the Reduced Echelon Form we get from row reducing a matrix is
unique, the following theorem follows

`Theorem 1: Uniqueness of the Reduced Echelon Form`
    `Each matrix is row equivalent to one and only one reduced echelon matrix`


<a id="orgba7c2e6"></a>

### Pivot Positions

A `pivot position` in a Matrix *A* is a location in *A* that corresponds to a leading
1 in a reduced echelon form. A `pivot column` is a column that contains the pivot
position.


<a id="org25391b6"></a>

### Row Reduction Algorithm

A four step algorithm to put a matrix into echelon form. After the four steps a
fifth step can be made to put into reduced echelon form.

Step 1: Begin with the left-most nonzero column. This is the pivot column. The
pivot position is at top.

Step 2: Select a nonzero entry in the pivot column as a pivot. If necessary,
interchange rows to move this entry into the pivot position.

Step 3: Use row replacement operations to create zeros in all positions below
the pivot

Step 4: Ignore the row(s) with the current pivot position and above. Repeat
steps 1-3 until no more nonzero rows to modify.

Extra step to put into reduced echelon form

Step 5: Working from the rightmost pivot to upwards and left, create zeros
above each pivot and scale the pivot to be one using elementary row operations.


<a id="orga3c9c75"></a>

### Checking Existence and Uniqueness (continued&#x2026;)

Putting the matrix in echelon form is the perfect tool to check the existence
and uniqueness of a linear system.

Example

The following matrix is in echelon form
```math
\begin{bmatrix}
3 & -9 & 12 & -9 & 6 & 15\\
0 & 2 & -4 & 4 & 2 & -6\\
0 & 0 & 0 & 0 & 1 & 4
\end{bmatrix}
```
*Since we don&rsquo;t see untrue statements like /1 = 0*, we can say that a solution
exists.

From looking at which columns are pivot columns, we know that x<sub>1</sub>, x<sub>2</sub>, & x<sub>5</sub> are
our `basic variables` and x<sub>3</sub> & x<sub>4</sub> are our `free variables`.

Since we have free variables we can immediately say that their are infinitely
many solutions.

We have the following theorem

`Theorem 2: Existence and Uniqueness Theorem`
    `A linear system is consistent if and only if the rightmost column of the`
    `augmented matrix is not a pivot column—that is, if and only if an echelon form`
    `of the augmented matrix has no row of the form`

`[0 ... 0 b]     with b nonzero`

`If a linear system is consistent, then the solution set contains either`
  `(i) a unique solution, when there are no free variables, or`
  `(ii) infinitely many solutions, when there is at least one free variable.`

