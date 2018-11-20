---
title: Inverse Matrices - A Primer
author: 'Orry Messer'
date: '2018-11-18'
slug: inverse-matrix
categories: []
draft: true
tags: []
---

# 1. Introduction
In this post __we talk about the__ ___inverse matrix___. We'll talk about what it means for a matrix to be _invertible_. We'll go on to discuss what it means for it _not_ to be invertible - _singular_. Finally, we'll go through how to find a matrix's inverse.

# 2. Invertibility
Let's think about a square matrix, `$A$`. In [a previous post]({{< ref "second-post.md" >}}) we spoke about how __a matrix acts on a vector__. The matrix does something to that vector. 

__The inverse of a matrix undoes what the original matrix did.__ The inverse of `$A$` is `$A^{-1}$`. `$A^{-1}$` undoes what `$A$` did. It's kind of like dividing by a number after multiplying by it.

If we have a vector `$x$`, and we multiply it by our matrix `$A$`, we get `$Ax$`. If we undo this operation by applying the inverse, we get back to `$x = A^{-1}Ax$`. The one matrix which always leaves any vector unchanged is the identity matrix, `$I$`. That is: `$Ix = x$` . __This is why `$A^{-1}A = I$`.__

When matrix `$A$` has an inverse it is said to be _invertible_. However, this is not always the case. __When a matrix is not invertible, it is also known as__ ___singular.___

# 3. Non-Invertibility - Singular Matrices
Not all matrics are invertible. __Matrices which are not invertible are known as__ ___singular.___ This means that there exists no matrix which can undo what the original matrix just did.

Say we are working in two dimensions - a plane. __Most `$2 \times 2$` matrices will move vectors around the `$2 \times 2$` plane.__ They'll either stretch them, or squash them, or even change their direction. But they'll usually always use up all of the plane; the output of that matrix multiplication won't just be limited to a single line on that plane.

But __if the output of a `$2 \times 2$` matrix always lands on a single line, then there is no way to undo that operation.__ We've, in effect, lost some information. 

It's kind of like how `$0$` has no inverse. If we have the number `$10$`, and we multiply it by `$5$`, we get `$50$`. If we want to undo this operation, we multiply by `$5$`'s inverse: `$\frac {1} {5}$` and get back `$50 \times \frac {1} {5} = 10$`. However, if we multiply `$10$` by `$0$`, we get `$0$`. There really isn't much we can do to `$0$` to get back to `$10$`. This is a tenuous analogy at best, as matrices and numbers are different animals. But, hopefully this helps convey _some_ intuition.

# 4. Testing for Singularity
__There are several equivalent conditions which, if met, mean that a matrix is singular.__ Some of these conditions are:
* The matrix's determinant is 0
* The matrix does not have full rank
* The `$n \times n$` matrix does not have all of its pivots.

Discussions about rank and determinants are enough to warrant their own posts (and more), and are beyond the scope of this post. When I do get around to writing those posts, I'll be sure to link this post though.

For now, let's just keep in mind that not all matrices have inverses, and that if the determinant of a matrix is zero, then it doesn't have an inverse.

But if it does have an inverse, let's try out finding it:

# 4. Inverse of a 2x2 Matrix
A `$2 \times 2$` matrix has this form:

\\[ 
 \begin{bmatrix}
  a & b  \newline
  c & d
 \end{bmatrix} 
\\]

If a `$2 \times 2$` matrix is invertible, then its inverse is:

\\[ 
\frac {1} {ad - bc}
\times
 \begin{bmatrix}
  d & -b  \newline
  -c & a
 \end{bmatrix} 
\\]

`$\frac {1} {ad - bc}$` is the determinant of the matrix. If it's zero, then we'd have `$\frac {1} {0}$`. In other words, the inverse wouldn't exist - our matrix would be singular.

Consider the matrix:

\\[ 
A
%
&#61;
%
 \begin{bmatrix}
  1 & 3  \newline
  2 & 7
 \end{bmatrix} 
\\]

According to our formula above, its inverse is:

\\[ 
\frac {1} {1 \times 7 - 3 \times 2}
\times
 \begin{bmatrix}
  7 & -3  \newline
  -2 & 1
 \end{bmatrix} 
%
&#61;
%
\frac {1} {1}
\times
 \begin{bmatrix}
  7 & -3  \newline
  -2 & 1
 \end{bmatrix} 
 %
&#61;
%
 \begin{bmatrix}
  7 & -3  \newline
  -2 & 1
 \end{bmatrix} 
\\]

Let's verify that this is indeed the inverse in two ways. 

We'll multiply the original matrix by the inverse. If we get the identity matrix, then we've done our calculation correctly:


\\[ 
 \begin{bmatrix}
  1 & 3  \newline
  2 & 7
 \end{bmatrix} 
  \begin{bmatrix}
  7 & -3  \newline
  -2 & 1
 \end{bmatrix} 
  %
  &#61;
  %
 \begin{bmatrix}
  1 \times 7 + 3 \times (-2) & 1 \times (-3) + 3 \times 1  \newline
  2 \times 7 + 7 \times (-2) & 2 \times (-3) + 7 \times 1
 \end{bmatrix}
  %
  &#61;
  %
 \begin{bmatrix}
  1 & 0  \newline
  0 & 1
 \end{bmatrix}
\\]


Next, we'll multiply a vector by the original matrix and then the result of that calculation, by the inverse. Let's pick the vector `$ \begin{bmatrix} 1 & 2 \end{bmatrix} ^ {T}$`. We should end up with the original after this:

\\[ 
 \begin{bmatrix}
  1 & 3  \newline
  2 & 7
 \end{bmatrix}
  \begin{bmatrix}
  1 \newline
  2
 \end{bmatrix}
  %
  &#61;
  %
 \begin{bmatrix}
  1 \times 1 + 3 \times 2 \newline
  2 \times 1 + 7 \times 2
 \end{bmatrix}
  %
  &#61;
  %
  \begin{bmatrix}
  7 \newline
  16
 \end{bmatrix}
\\]

Let's now see if the inverse matrix brings  `$ \begin{bmatrix} 7 & 16 \end{bmatrix} ^ {T}$` back to `$ \begin{bmatrix} 1 & 2 \end{bmatrix} ^ {T}$` 

\\[ 
 \begin{bmatrix}
  7 & -3  \newline
  -2 & 1
 \end{bmatrix}
  \begin{bmatrix}
  7 \newline
  16
 \end{bmatrix}
  %
  &#61;
  %
 \begin{bmatrix}
  7 \times 7 + (-3) \times 16 \newline
  (-2) \times 7 + 1 \times 16
 \end{bmatrix}
  %
  &#61;
  %
  \begin{bmatrix}
  1 \newline
  2
 \end{bmatrix}
\\]

So it looks like we've done our calculations correctly!

# 5. Inverse of a Larger Matrix 







