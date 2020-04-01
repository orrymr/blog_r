---
title: "A Matrix Nullspace (Kernel) Tutorial - Finding the Nullspace"
date: 2018-03-01T20:35:21+02:00
draft: false
tags: ["linear algebra", "18.06", "matrices", "nullspace"]
thumbnailImagePosition: left
thumbnailImage: https://res.cloudinary.com/da1gwmlvj/image/upload/v1585758073/nullspace_sbylpi.png
---


In this article we describe __what the nullspace is__. We go on to explain __how to find the nullspace__.

<!--more-->

<!--toc-->

# Nullspace, Null Space or Kernel?

The _nullspace_ (or _null space_) of a matrix is also known as the _kernel_ of a matrix. __These terms are interchangeable.__ 

The nullspace is a __set of vectors that when multiplied by a matrix returns $0$__ (well, the zero vector).

# How To Find the Nullspace

Have a look at this matrix:

\\[ 
A
%
&#61;
%
 \begin{bmatrix}
  1 & 1 & 2 & 3 \newline
  2 & 2 & 8 & 10 \newline
  3 & 3 & 10 & 13
 \end{bmatrix} 
\\]

We're interested in finding its nullspace: that is, all vectors such that when multiplied by our matrix $A$, return the zero vector, $ \begin{bmatrix} 0 & 0 & 0 \end{bmatrix} ^ {T}$.

I happen to know that $ \begin{bmatrix} -3 & 1 & -2 & 2 \end{bmatrix} ^ {T}$ is one such vector:

\\[
\begin{bmatrix}
  1 & 1 & 2 & 3 \newline
  2 & 2 & 8 & 10 \newline
  3 & 3 & 10 & 13
 \end{bmatrix}
%
\begin{bmatrix}
 -3 \newline
 1 \newline
 -2 \newline
 2
\end{bmatrix}
%
&#61;
%
%
\begin{bmatrix}
 -3 + 1 - 4 + 6 \newline
 -6 + 2 - 16 + 20 \newline
 -9 + 3 - 20 + 26
\end{bmatrix}
%
&#61;
%
\begin{bmatrix}
 0 \newline
 0 \newline
 0
\end{bmatrix}
\\]

If we set $x = \begin{bmatrix} -3 & 1 & -2 & 2 \end{bmatrix} ^ {T}$ , then we can write out the above equation more succinctly: $Ax = 0$

We say that __$x$ is in the nullspace of $A$.__

We're going to look at a __systematic way to find all the vectors in the nullspace.__
We'll do this is by:

1. Using elimination to find our pivots
2. Using back substitution to find our solutions

We can think of this as our two-step recipe to find our nullspace.

## Finding The Pivots

This article isn't about how to do Gaussian elimination on a matrix. I'm going to assume that you already know how to do this. I hope to write an article about this in the future.

Suppose we performed elimination on our matrix $A$, which results in our new $U$:

\\[ 
U
%
&#61;
%
 \begin{bmatrix}
  1 & 1 & 2 & 3 \newline
  0 & 0 & 4 & 4 \newline
  0 & 0 & 0 & 0
 \end{bmatrix} 
\\]

__The cool thing is that $A$ and $U$ have the same nullspace.__ So, if we know that $Ux = 0$, we also know that $Ax = 0$.

Let's suppose that we didn't know that $x = \begin{bmatrix} -3 & 1 & -2 & 2 \end{bmatrix} ^ {T}$ was in the nullspace of the matrix $A$. We know that there is some vector $x = \begin{bmatrix} x_1 & x_2 & x_3 & x_4 \end{bmatrix} ^ {T}$ such that $Ux = 0$ (even if that vector is just $\begin{bmatrix} 0 & 0 & 0 & 0 \end{bmatrix} ^ {T}$). 

Writing this out more explicitly:

\\[ 
\tag{1}
\label{1}
 \begin{bmatrix}
  1 & 1 & 2 & 3 \newline
  0 & 0 & 4 & 4 \newline
  0 & 0 & 0 & 0
 \end{bmatrix} 
 %
 \begin{bmatrix}
  x_1 \newline
  x_2 \newline
  x_3 \newline
  x_4
 \end{bmatrix}
 %
  &#61;
 %
 \begin{bmatrix}
  0 \newline
  0 \newline
  0
 \end{bmatrix}
\\]

According to our recipe for finding the nullspace, we need to find our pivots. __A pivot is simply the first non-zero element in each row of the matrix.__ 

Looking at $U$, the first row has a pivot in the first column, with value $1$. The second row has a pivot in the third column: $4$. The third row does not have a pivot. 

__We call $x_1$ and $x_3$__ ___pivot variables___ since columns 1 and 3 contain pivots. __$x_2$ and $x_4$ are called__ ___free variables___ since columns 2 and 4 have no pivots.

Note that there are 4 variables in total - 2 free variables, and 2 pivot variables. This is because the nullspace vectors are in $\mathbb{R}^4$ in this case, since $A$ (and $U$) are $3 \times 4$ matrices. 

## Using Back Substitution to Find our Nullspace

Now that we know what our pivots are, we want to find our _special solutions_. Special solutions are vectors in our nullspace which will eventually __help us find all the vectors in our nullspace__. 

__We will have as many special solutions as we have free variables.__ In this case, we have 2 free variables, so we will have 2 special solutions. The way we find the special solutions is by _back substitution_. 

Before we get to what back substition is, let's rewrite equation $(\ref{1})$ as a set of equations, instead of its matrix form:

\\[ 
x_1 + x_2 + 2x_3 + 3x_4 = 0
\\]

\\[ 
4x_3 + 4x_4 = 0
\\]

We want to find values for $x_1$, $x_2$, $x_3$ and $x_4$ which satisfy the above set of equations. 

__Since $x_2$ and $x_4$ are free variables, we can give them any values we wish__ - they are _free_ variables, after all! The simples choice for our free variables is ones or zeroes. 

Let's set $x_2 = 1$ and $x_4 = 0$:


\\[ 
x_1 + (1) + 2x_3 + 3(0) = 0
\\]

\\[ 
4x_3 + 4(0) = 0
\\]

which gives: 

\\[ 
\label{2}
\tag{2}
x_1 + 1 + 2x_3 = 0
\\]

\\[ 
\label{3}
\tag{3}
x_3 = 0
\\]

Great! __We now know that $x_3 = 0$__ (and we have values for $x_2$ and $x_4$ ). All that's left is for us to find $x_1$

__Now, let's use back substitution to plug $x_3 = 0$ into equation ($\ref{2}$):__

\\[ 
x_1 + 1 + 2(0) = 0
\\]

so 

\\[ 
x_1 = -1
\\]

We now have our first special solution:

\\[
\begin{bmatrix}
 x_1 \newline
 x_2 \newline
 x_3 \newline
 x_4
\end{bmatrix}
%
&#61;
%
\begin{bmatrix}
 -1 \newline
 1 \newline
 0 \newline
 0
\end{bmatrix}
\\]

Setting $x_2 = 1$ and $x_4 = 0$ gave us our first special solution. __We need to find our second special solution.__ The easiest way to do this is to set $x_2 = 0$ and $x_4 = 1$. Using the same procedure as we did for the first special solution we find our second special solution:

\\[
\begin{bmatrix}
 -1 \newline
 0 \newline
 -1 \newline
 1
\end{bmatrix}
\\]

Since we had 2 free variables, we get 2 special solutions:

\\[ 
\begin{bmatrix} 
  -1 \newline 
  1 \newline 
  0 \newline 
  0 
\end{bmatrix}, 
\begin{bmatrix} 
  -1 \newline 
  0 \newline 
  -1 \newline 
  1 
\end{bmatrix}
\\]

These two special solutions are __in the nullspace of $U$ and therefore also $A$__. This means that if you multiply the matrix $A$ or $U$ by these vectors, you will get the zero vector.

Crucially - ___every combination of our special solutions is in the nullspace___. 

So, the complete solution is:

\\[ 
x
%
&#61;
%
 x_2
 %
\begin{bmatrix}
 -1 \newline
 1 \newline
 0 \newline
 0
\end{bmatrix}
%  
+
%
 x_4
 %
\begin{bmatrix}
 -1 \newline
 0 \newline
 -1 \newline
 1
\end{bmatrix}
%
&#61;
%
\begin{bmatrix}
 -x_2 - x_4 \newline
 x_2 \newline
 -x_4 \newline
 x_4
\end{bmatrix}
\\]

What does this actually mean? It means that __we can pick our free variables $x_2$ and $x_4$ however we wish, and we will get a valid solution in response.__

For example let's pick: $x_2=1$ and $x_4 = 2$. So:

\\[
\begin{bmatrix}
 -x_2 - x_4 \newline
 x_2 \newline
 -x_4 \newline
 x_4
\end{bmatrix}
%
&#61;
%
\begin{bmatrix}
 -3 \newline
 1 \newline
 -2 \newline
 2
\end{bmatrix}
\\]

which was my example at the beginning of the article.

## Another Example

Say now I wish to find the nullspace of

\\[
U
%
&#61;
%
 \begin{bmatrix}
  1 & 5 & 7 \newline
  0 & 0 & 9 \newline
 \end{bmatrix} 
\\]

The second column contains our free variable. Since there is only __one free variable, there will only be one special solution__.

We need to back substitute $x_2 = 1$ (no need to set zeroes this time, as there is only one free variable).

Then
\\[
9x_3 = 0
\\]

gives

\\[
x_3 = 0
\\]

and 

\\[
x_1 + 5x_2 = 0
\\]

so

\\[
x_1 = -5
\\]

since 

\\[
x_2 = 1
\\]

So, 
\\[
x
%
&#61;
%
x_2
%
 \begin{bmatrix}
  -5 \newline
  1 \newline
  0
 \end{bmatrix} 
\\]

The nullspace in this case is a line in $\mathbb{R}^3$. It contains multiples of the special solution.