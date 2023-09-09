### Useful Notations

![image-20230902043612425](asset/image-20230902043612425.png)

![image-20230902043728632](asset/image-20230902043728632.png)

![image-20230902043743513](asset/image-20230902043743513.png)

![image-20230902045239407](asset/image-20230902045239407.png)

### Matrix: intro

#### View from operator

![week1](week1.jpg)



#### Examples

![image-20230904000044264](asset/image-20230904000044264.png)

![image-20230904000053756](asset/image-20230904000053756.png)

![image-20230904000116224](asset/image-20230904000116224.png)

![image-20230904000629281](asset/image-20230904000629281.png)

![image-20230904000641150](asset/image-20230904000641150.png)

#### Views of matrix multiplication

![image-20230909043542374](asset/image-20230909043542374.png)

![image-20230909043603539](asset/image-20230909043603539.png)

![image-20230909043615893](asset/image-20230909043615893.png)

![image-20230909043627282](asset/image-20230909043627282.png)

### Matrix: essentials

#### Invertibility

We should try to avoid the matrix inversion since it's time-consuming. Even computing the inverse of the blocked matrix is hard:

![image-20230909043918487](asset/image-20230909043918487.png)

And there is another important inversion lemma:

![image-20230909044022435](asset/image-20230909044022435.png)

If the C is an identity matrix, this equation could be simplified a lot.

And other properties:

1. For unitary matrix A, we have $A^{-1}=A'$.
2. $det(A) = \frac{1}{det(A')}.$

### Orthogonality

orthonormal of vectors: $<x,y>=y'x=1$.

orthonormal vectors: $x'x=1$.

![image-20230909044542149](asset/image-20230909044542149.png)

![](asset/image-20230909044555676.png)

And we have Cauchy-Schwarz inequality.

Orthogonal matrix: $Q^TQ=QQ^T=I$.

#### determinant

![image-20230909091041630](asset/image-20230909091041630.png)

The determinant is for the square matrix.

The determinant is non-zero -> the matrix is invertible.

![image-20230909091858950](asset/image-20230909091858950.png)

![image-20230909092531377](asset/image-20230909092531377.png)

![image-20230909092547136](asset/image-20230909092547136.png)

### Eigenvalue

Motivation: convenient for computing: $Av=\lambda v$.

Background: invariant sub-space.

![image-20230910053118503](asset/image-20230910053118503.png)

Gram Matrix: Given $X\in F^{M\times N}, X'X$ is the Gram matrix and $XX'$ (outer-product) is the covariance matrix or scatter matrix.

 For a matrix, vector  V that satisfies $Av=\lambda v$ is called an eigenvector.

And there comes a good property: $AV=V\Lambda$, where $\Lambda=Diag\{\lambda_1,...,\lambda_N\}$.

![image-20230910060815705](asset/image-20230910060815705.png)

 ![image-20230910061135955](asset/image-20230910061135955.png)

It's convenient for computing.

### Trace

![image-20230910061551245](asset/image-20230910061551245.png)
