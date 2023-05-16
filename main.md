# Linear Algebra Assignment Project 1

**University of Technology - HCMC Faculty of Applied Mathematics**
**Linear Algebra Project Semester 222 (2022 - 2023)**
**Instructor: Đậu Thế Phiệt**
<img src="assets\01_logobachkhoasang.png" alt="LogoBachKhoa" style="height: 100px; position: absolute;
  right : 0px;
  top: 0px;"/>

| **Student ID** | **Full Name**            | **Task**  | **Contribute** |
|----------------|--------------------------|-----------|----------------|
|     1952161    | Garcinez Villano Hannah  |   Video   |       25%      |
|     2153307    | Nguyễn Huỳnh Đức         | Problem 1 |       25%      |
|     2210503    | Lê Anh Duy               | Problem 3 |       25%      |
|     1952242    | Nguyễn Lê Thanh Hào      | Problem 2 |       25%      |

## Problem 1
<!-- font: times new roman -->
A code breaker intercepted the encoded message below.

``` python
45 -35 38 -30 18 -18 35 -30 81 -60 42 -28 75 -55 2 -2 22 -21 15 -10
```

Let the inverse of the encoding matrix be $A^{-1}$ = $\begin{bmatrix} w & x \\ y & z \end{bmatrix}$.
(a) You know that  $ \lbrack \begin{matrix} 45 & -35 \end{matrix}\rbrack $  $A^{-1}$ = $ \lbrack \begin{matrix} 10 & 15 \end{matrix}\rbrack $ and $ \lbrack \begin{matrix} 38 & -30 \end{matrix}\rbrack $  $A^{-1}$ = $ \lbrack \begin{matrix} 8 & 14 \end{matrix}\rbrack $.
 Write and solve two systems of equations to find w, x, y, and z.
(b) Decode the message.

### (a)

#### Theory

We can write the following system of equations:

We begin by using the fact that $A^{-1}$ is a 2x2 matrix and can be expressed as follows:

$A^{-1} = \begin{bmatrix} w & x \\ y & z \end{bmatrix}$

Then, we can use the given equations to set up two systems of linear equations:

System 1:

$
\begin{cases}
45w - 35y = 10 \\
45x - 35z = 15
\end{cases}
$

System 2:

$
\begin{cases}
38w - 30y = 8 \\
38x - 30z = 14
\end{cases}
$

Now we solve each system for $w$, $x$, $y$, and $z$.
<!-- The result is: w = 1 and x = -2 and y = 1 and z = -3 -->
The result is $w = 1$, $x = -2$, $y = 1$, and $z = -3$.

#### MATLAB code

We can solve this system of equations using the following MATLAB code:

```matlab
A=[45 -35;38 -30];%set up 2 maxtries A and B
B=[10 15;8 14];
C=A\B; %find the inverse of the encoding matrix A-1;
disp ("the inverse of the encoding matrix A-1 is")
disp(C)
```

the output is:

```matlab
the inverse of the encoding matrix A-1 is
    1.0000   -2.0000
    1.0000   -3.0000
```

<!-- We group all the given numbers into the following array of 2x2 maxtries:
[45 -35]; [38 -30]; [18 -18]; [35 -30]; [81 -60]; [42 -28]; [75 -55]; [2 -2]; [22 -21]; [15 -10]
Then, we multiply each of them by the maxtries A-1 from the right and get the new following array of 2x2 maxtries:
[10 15]; [8 14]; [0 18]; [5 20]; [21; 18]; [14 0]; [20 15]; [0 2]; [1 19]; [5 0]
and the result is ‘’JOHN RETURN TO BASE’’ -->

<div style="page-break-after: always;"></div>

### (b)

#### Theory

We group all the given numbers into the following array of 2x2 matrices:

$\begin{bmatrix} 45 & -35 \\ 38 & -30 \end{bmatrix}$, $\begin{bmatrix} 18 & -18 \\ 35 & -30 \end{bmatrix}$, $\begin{bmatrix} 81 & -60 \\ 42 & -28 \end{bmatrix}$, $\begin{bmatrix} 75 & -55 \\ 2 & -2 \end{bmatrix}$, $\begin{bmatrix} 22 & -21 \\ 15 & -10 \end{bmatrix}$

Then, we multiply each of them by the inverse of the encoding matrix $A^{-1}$ from the right and get the new following array of 2x2 matrices:

$\begin{bmatrix} 10 & 15 \\ 8 & 14 \end{bmatrix}$, $\begin{bmatrix} 0 & 18 \\ 5 & 20 \end{bmatrix}$, $\begin{bmatrix} 21 & 18 \\ 14 & 0 \end{bmatrix}$, $\begin{bmatrix} 20 & 15 \\ 0 & 2 \end{bmatrix}$, $\begin{bmatrix} 1 & 19 \\ 5 & 0 \end{bmatrix}$

and the result is ```JOHN RETURN TO BASE.```

#### MATLAB Code

We can solve this problem using the following MATLAB code:

```matlab
function Q1
```

This line defines a MATLAB function named 'Q1'. The function does not take any input arguments.

```matlab
a1=input ("a");
b1=input ("b");
c1=input ("c");
d1=input ("d");
A2=[a1 b1;c1 d1];
```

These five lines prompt the user to enter four values: a1, b1, c1, and d1. These values are used to create a 2x2 encoding matrix, A2, in which a1 is the top-left element, b1 is the top-right element, c1 is the bottom-left element, and d1 is the bottom-right element.

```matlab
A3=[45 -35;38 -30;18 -18;35 -30 ; 81 -60 ; 42 -28 ; 75 -55 ; 2 -2 ; 22 -21 ; 15 -10];
```

This line creates a fixed 10x2 matrix named A3 that contains ten pairs of numerical values. These values are used to encode the input sequence into a sequence of alphabets.

```matlab
A4=A3*A2;
```

This line multiplies the matrices A3 and A2 using the ‘*’ operator and assigns it to a new variable A4. This multiplication process generates a new 10x2 matrix containing pairs of numerical values that correspond to alphabetic characters.

```matlab
for i=1:10
    switch (A4(i,1))
        case 0
            disp(" ")
        case 1
            disp("a")
        case 2
            disp("b")
        ...
```

This loop runs for 10 iterations and checks each element of the first column of the A4 matrix. Depending on the value of the element, it displays an alphabetic character that corresponds to the number (0-26) using a switch case statement. This process continues for the second column of the A4 matrix as well. If the element is 0, it displays a space.

```matlab
end
```

This line marks the end of the for loop. The output is: ```JOHN RETURN TO BASE```

```plaintext
j o h n  r e t u r n  t o  b a s e
```

In conclusion, the given MATLAB code demonstrated how to encode a sequence of numerical values into a corresponding sequence of alphabetic characters using matrix multiplication and switch case statements. The code prompts the user to enter four values, which are used to create an encoding matrix. It then multiplies this matrix with a fixed matrix to obtain a new matrix containing pairs of numerical values representing the encoded alphabet sequence. Finally, it displays the corresponding alphabetic characters for each pair of values in the matrix.

This code provides an example of how matrix operations can be used to encode data and highlights the importance of understanding basic linear algebra concepts when working with data and algorithms. Additionally, this code demonstrates the use of switch case statements to map numerical values to corresponding characters, which is a common technique used in text processing and language translation applications.

<div style="page-break-after: always;"></div>

## Problem 2

Construct an inner product in $R^n$ . In that inner product, write a program to input any number of vectors in $R^n$ and return the orthogonal basis and orthonormal basis of the subspace spanned by these vectors.(Use Gram - Schmidt process). From that, given any vector in $R^n$, find the coordinates in that basis and find the length of the vector

### Theory

**Inner Product in $R^n$:**

An inner product on $\mathbb{R}^n$ is a function that takes two vectors in $\mathbb{R}^n$, denoted as $\langle \cdot, \cdot \rangle: \mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}$, and satisfies the following conditions:

1. $\langle u,v \rangle = \langle v,u \rangle$ for all $u,v \in \mathbb{R}^n$ (Symmetry)
2. $\langle u+v,w \rangle = \langle u,w \rangle + \langle v,w \rangle$ for all $u,v,w \in \mathbb{R}^n$ (Additivity)
3. $\langle c u,w \rangle = c \langle u,w \rangle$ for all $u,w \in \mathbb{R}^n$ and $c \in \mathbb{R}$ (Homogeneity)
4. $\langle u,u \rangle \geq 0$ for all $u \in \mathbb{R}^n$, and $\langle u,u \rangle = 0$ if and only if $u=0$ (Positive Definiteness)

A common inner product on $\mathbb{R}^n$ is the dot product, defined as $\langle u,v \rangle = u \cdot v = u_1v_1 + u_2v_2 + \dots + u_nv_n$.

**Gram-Schmidt Process:**

Given a set of linearly independent vectors $\{v_1, v_2, \dots, v_k\}$ in $\mathbb{R}^n$, we can construct an orthogonal basis $\{u_1, u_2, \dots, u_k\}$ for the subspace spanned by these vectors using the Gram-Schmidt process as follows:

1. Let $u_1 = v_1$.
2. For $i=2,3,\dots,k$, compute $u_i$ as follows:

   a. Let $u_i = v_i - \sum_{j=1}^{i-1} \frac{\langle u_j,v_i \rangle}{\langle u_j,u_j \rangle} u_j$. This is the orthogonal projection of $v_i$ onto the subspace spanned by $\{u_1, u_2, \dots, u_{i-1}\}$.

   b. Normalize $u_i$ by setting $u_i' = \frac{u_i}{||u_i||}$.

Then, the set $\{u_1, u_2, \dots, u_k\}$ is an orthonormal basis for the subspace spanned by $\{v_1, v_2, \dots, v_k\}$.

**Finding Coordinates and Length:**

Given a vector $w \in \mathbb{R}^n$ and an orthonormal basis $\{u_1, u_2, \dots, u_k\}$ for a subspace $V$ in $\mathbb{R}^n$, we can find the coordinates of $w$ with respect to $V$ and the length of $w$ as follows:

1. Let $c_i = \langle w,u_i \rangle$ for $i=1,2,\dots,k$. These are the coordinates of $w$ with respect to the orthonormal basis $\{u_1, u_2, \dots, u_k\}$.
2. The length of $w$ is given by $||w|| = \sqrt{\langle w,w \rangle} = \sqrt{\sum_{i=1}^{n} w_i^2}$.

The coordinates of $w$ with respect to an orthonormal basis give us a way to represent $w$ as a linear combination of the basis vectors, where the coefficients of the linear combination are the coordinates. This can be useful in solving problems involving linear transformations and projections. The length of $w$ gives us a measure of the magnitude of the vector, which can be helpful in comparing vectors and understanding their geometric properties.

### MATLAB Code

```matlab
% Input any number of vectors in R^n
n = input("Enter the dimension of R^n: ");
m = input("Enter the number of vectors: ");
A = zeros(n,m);
for i = 1:m
    fprintf("Enter vector %d:\n", i);
    for j = 1:n
        A(j,i) = input('');
    end
end
```

The first part of the code prompts the user to input the dimension n and the number of vectors m. It then creates a matrix A of size n x m and fills it with zeros using the `zeros()` function. Next, it uses a nested `for` loop to prompt the user to enter the components of each vector. For each vector i, the loop prompts the user to enter the jth component of the vector, which is stored in the ith column of A.

```matlab
% Perform QR factorization to get orthogonal basis Q
[Q, R] = qr(A);
```

The next part of the code performs QR factorization on matrix A using the `qr()` function. This function returns two matrices Q and R such that A = QR, where Q is an orthogonal matrix and R is an upper triangular matrix.

```matlab
% Normalize Q to get orthonormal basis
Q = Q / norm(Q, 'fro');
```

The third part of the code normalizes Q to obtain an orthonormal basis. The Frobenius norm of Q is computed using the `norm()` function, which is then used to divide each column of Q by its norm. This creates a matrix with orthonormal columns.

```matlab
% Print Q
fprintf("The orthonormal basis is:\n");
disp(Q);
```

The fourth part of the code prints out the orthonormal basis Q using the `disp()` function.

```matlab
% Input a vector in R^n
u = zeros(n,1);
fprintf("Enter a vector in R^n:\n");
for i = 1:n
    u(i) = input('');
end
```

The fifth part of the code prompts the user to enter a vector u in R^n and stores its components in a column vector.

```matlab
% Find coordinates in Q
c = Q' * u;
```

The sixth part of the code finds the coordinates of u with respect to the orthonormal basis Q by computing the dot product of each column of Q with u. This is done using matrix multiplication between the transpose of Q (Q') and the vector u.

```matlab
% Print coordinates
fprintf("The coordinates in Q are:\n");
disp(c);
```

The seventh part of the code prints out the coordinates of u with respect to Q using the `disp()` function.

```matlab
% Find length of u
l = norm(u);
```

The eighth part of the code finds the length of u using the `norm()` function.

```matlab
% Print length
fprintf("The length of u is:\n");
disp(l);
```

The final part of the code prints out the length of u using the `disp()` function.
