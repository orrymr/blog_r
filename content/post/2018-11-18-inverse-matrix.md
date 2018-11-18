---
title: inverse matrix
author: ''
date: '2018-11-18'
slug: inverse-matrix
categories: []
draft: true
tags: []
---

# 1. Introduction
In this post __we talk about the__ ___inverse matrix___. We'll talk about what it means for a matrix to be invertible, for it not to be invertible (singular) and how to find a matrix's inverse.

# 2. Invertibility
Let's think about a square matrix, `$A$`. In [a previous post]({{< ref "second-post.md" >}}) we spoke about how __a matrix acts on a vector__. The inverse of `$A$` is `$A^{-1}$`. It undoes what `$A$` did.

If we have a vector `$x$`, and we multiply it by our matrix `$A$`, we get `$Ax$`. If we undo this operation by applying the inverse, we get back to `$x = A^{-1}Ax$`. __The one matrix which always leaves any vector unchanged is the identity matrix, `$I$`; which is why `$A^{-1}A = I$`__.

When matrix `$A$` has an inverse it is said to be _invertible_. However, this is not always the case. When a matrix is not invertible, it is also known as _singular_.

# 3. Non-Invertibility - Singular Matrices
- det = 0 in this case (lose information, can't undo the transformation - it moves all the vectors into a lower dimension)
- rank of 1 - when the output of the matrix multiplication is a line (for next article)
  - rank of 2 - when all the outputs of the matrix mult land in 2-D, then matrix has a rank of 2.
  - etc...

Not all matrices invertible.
  - (like it says at start of chapter) whatever A does, A^-1 undoes. link to post about how a matrix acts on a vector
  
# 4. Inverse of a 2x2 Matrix

# 5. Inverse of a Larger Matrix 