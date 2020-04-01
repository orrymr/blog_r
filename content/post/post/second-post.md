---
title: "Of Matrices and Men (pt. 1)"
date: 2017-10-22T20:35:21+02:00
draft: false
tags: ["linear algebra", "18.06", "matrices"]
thumbnailImagePosition: left
thumbnailImage: https://res.cloudinary.com/da1gwmlvj/image/upload/v1585486477/samples/landscapes/nature-mountains.jpg
---

One of the most crucial changes in my viewpoint came when I learned that matrices, much like functions, _act_ on inputs. Until then, a matrix was just a collection of numbers and matrix multiplication was just a mechanical set of rules used to produce another collection of numbers. I knew that the result of matrix multiplication could be a scalar, a vector or another matrix... but I abandoned any further investigations.

<!--more-->

I'm going to assume that the reader is familiar with the mechanics of matrix multiplication. What I'll be talking about is how a matrix affects a vector; in this case, how a matrix transforms a vector into a different vector and that the transformation is encoded in the matrix itself.

An example Prof. Strang uses in his lectures and book is the _difference matrix_. It looks like this:

 \begin{bmatrix}
  1 & 0 & 0 \newline
  -1 & 1 & 0 \newline
  0 & -1 & 1
 \end{bmatrix}
<br>
Now, let's say we have a vector: $ \begin{bmatrix} x_1 \newline x_2 \newline x_3 \end{bmatrix} \in  \mathbb{R}^3$.
Let's say we wish to multiply the above matrix with this vector:
 
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
\\]

We could look at the matrix as the collection of vectors $ \begin{bmatrix} 1 \newline -1 \newline 0 \end{bmatrix}$, $ \begin{bmatrix} 0 \newline 1 \newline -1 \end{bmatrix}$ and $ \begin{bmatrix} 0 \newline 0 \newline 1 \end{bmatrix}$ and then take the linear combination of columns: 
\\[ 
x_1
%
\begin{bmatrix} 
1 \newline 
-1 \newline 
0 
\end{bmatrix}
%
+
%
x_2
%
\begin{bmatrix} 
0 \newline 
1 \newline 
-1 
\end{bmatrix}
%
+
%
x_3
%
\begin{bmatrix} 
0 \newline 
0 \newline 
1 
\end{bmatrix}
\\]

This does give you the correct result. The numbers $x_1$, $x_2$ and $x_3$ multiply the columns which make up the matrix. But we want to change our point of view. We want to see the matrix as a _thing_ which somehow transforms the vector. So... let's finally look at the result of this matrix multiplication:

\begin{bmatrix}
x_1 \newline
x_2 - x_1 \newline
x_3 - x_2 
\end{bmatrix}

There it is. Can you see why we called this matrix a difference matrix? The top difference is $x_1 - x_0 = x_1 - 0 = x_1$.
Let's try this with an example. Let's take a vector with $x_1 = 1$, $x_2= 4$ and $x_3 = 9$ that is:

\\begin{bmatrix}
 1 \newline
 4 \newline
 9
\\end{bmatrix}

The result here is:

\\[
\\begin{bmatrix}
 1 - 0 \newline
 4 - 1 \newline
 9 - 4
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

This matrix will always behave like this - for any vector in $\mathbb{R}^3$. 

Seeing matrix multiplication between a matrix and a vector as a linear combination of vectors (as we did initially) is obviously correct, and yields a correct result. But it's also important to note that matrices are things which operate on vectors. In this case, our difference matrix will take as "input" a vector and as "output" produce a new vector which contains the differences of the "input" vector. (And here I hope to stop my liberal usage of quotes).

This post discussed obtaining the result of matrix multiplication. Next time I'll talk about how to find out which combination of columns give you a certain result (and if that's even possible). Unlike this post, I hope to write it while not jetlagged (and I apologize if this post is slightly incoherent. I'm blaming timezone differences).


















