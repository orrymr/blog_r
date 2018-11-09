---
title: "Of Matrices and Men (pt. 2)"
date: 2017-11-22T20:35:21+02:00
draft: false
tags: ["linear algebra", "18.06", "matrices"]
---

In my [last post]({{< ref "second-post.md" >}}) we saw how a matrix could operate on a vector to produce a result:

\\[ 
\begin{bmatrix}
  1 & 0 & 0 \newline
  -1 & 1 & 0 \newline
  0 & -1 & 1
 \end{bmatrix}
%
\\begin{bmatrix}
 1 \newline
 4 \newline
 9
\\end{bmatrix}
%
&#61;
%
\\begin{bmatrix}
1 \newline
3 \newline
5
\\end{bmatrix}
\\]

The matrix used above is a $3 \times 3$ _difference matrix_. The general form for this type of operation is:

\\[
Ax = b
\\]

From the above equation, you can see that vector $b$ is produced by applying matrix $A$ to vector $x$. This $Ax = b$ is pretty much the central equation of linear algebra.

Say you now know what $b$ is and you wish to recover $x$. That is, given $Ax = b$, which is: 

\\[ 
\begin{bmatrix}
  1 & 0 & 0 \newline
  -1 & 1 & 0 \newline
  0 & -1 & 1
 \end{bmatrix}
%
\\begin{bmatrix}
 x_1 \newline
 x_2 \newline
 x_3
\\end{bmatrix}
%
&#61;
%
\\begin{bmatrix}
 b_1 \newline
 b_2 \newline
 b_3
\\end{bmatrix}
\\]

We assume that $b$ is known, and we now wish to retrieve $x$.
We can write out $Ax = b$ as a set of linear equations:

\\[
\begin{equation}
1 \cdot x_1 + 0 \cdot x_2 + 0 \cdot x_3 = b_1 
\end{equation}
\\]
\\[
\begin{equation}
-1 \cdot x_1 + 1 \cdot x_2 + 0 \cdot x_3 = b_2 
\end{equation}
\\]
\\[
\begin{equation}
0 \cdot x_1 -1 \cdot x_2 + 1 \cdot x_3 = b_3
\end{equation}
\\]

And now solving for the $x_i$s:

\\[
\begin{equation}
x_1 = b_1 \qquad
\end{equation}
\\]
\\[
\begin{equation}
x_2 = b_1 + b_2
\end{equation}
\\]
\\[
\begin{equation}
\qquad x_3 = b_1 + b_2 + b_3
\end{equation}
\\]

We were able to solve for the $x_i$s so easily because our matrix $A$ is _lower triangular_. This just means that all the entries above the diagonal entries are equal to $0$. In general, we can recover a unique $x$, given a $b$, if the matrix which produced $b$ is _invertible_. I'll use my next post to discuss invertibility and why it was possible for us to so easily solve for the $x_i$s.
For now, just know that from any vector $b$ produced by the the difference matrix $A$, we can solve for the $x$ which led to it. Let's try $ b = \begin{bmatrix} b_1 \newline b_2 \newline b_3 \end{bmatrix} = \begin{bmatrix} 1 \newline 3 \newline 5 \end{bmatrix} $. This will give us $x = \begin{bmatrix} x_1 \newline x_2 \newline x_3 \end{bmatrix} = \begin{bmatrix} b_1 \qquad \qquad \newline b_1 + b_2 \qquad \newline b_1 + b_2 +b_3 \end{bmatrix}= \begin{bmatrix} 1 \newline 1 + 3 \newline 1 + 3 + 5 \end{bmatrix} = \begin{bmatrix} 1 \newline 4 \newline 9 \end{bmatrix}$. This is in fact correct, and should come as no surprise to anybody who has endured high school algebra.

The cool part comes now. 

From the above, we can write $ \begin{bmatrix} x_1 \newline x_2 \newline x_3 \end{bmatrix} $ as follows: $ \begin{bmatrix} b_1 \qquad \qquad \newline b_1 +b_2 \qquad \newline b_1 + b_2 +b_3 \end{bmatrix} = \begin{bmatrix}
  1 & 0 & 0 \newline
  1 & 1 & 0 \newline
  1 & 1 & 1
 \end{bmatrix}
\begin{bmatrix} b_1 \newline b_2 \newline b_3 \end{bmatrix}
$.

Don't worry too much about exactly _how_ we found the matrix \begin{bmatrix}
  1 & 0 & 0 \newline
  1 & 1 & 0 \newline
  1 & 1 & 1
 \end{bmatrix} (which we'll call $S$), just convince yourself that it is, in fact, the correct matrix to have here. The neat thing about this matrix, is that it's actually a _sum matrix_; as opposed to the _difference matrix_, which is its inverse. There is a nice duality or symmetry going on here. The inverse of the difference matrix is the sum matrix. 

Let's take the result of our initial $Ax = b$, which is $b = \\begin{bmatrix}
 1 \newline
 3 \newline
 5
\\end{bmatrix}. $ Let's then apply the sum matrix to it:

\\[
\begin{bmatrix}
  1 & 0 & 0 \newline
  1 & 1 & 0 \newline
  1 & 1 & 1
 \end{bmatrix}
%
\begin{bmatrix}
 1 \newline
 3 \newline
 5
\end{bmatrix}
%
&#61;
%
%
\begin{bmatrix}
 1 \newline
 4 \newline
 9
\end{bmatrix}
\\]

We get back our original $x = \begin{bmatrix} 1 \newline 4 \newline 9 \end{bmatrix}$.

So, $Ax = b$, and $Sb = x$. 

Pretty cool, right? 

