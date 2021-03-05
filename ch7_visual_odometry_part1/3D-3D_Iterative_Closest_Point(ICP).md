# 3D-3D: Iterative Closest Point (ICP)

Suppose we have a set of matched 3D points:
$$
P = \{ p_1, ..., p_n \}, P' = \{p_1', ..., p_n' \}
$$
Now we need to find an Euclidean transformation $$R, t$$, which makes:
$$
\forall i,p_i = Rp'_i + t
$$
This problem can be solved by Iterative Closest Point (ICP).

## 1. Linear Algebra (SVD)

### 1.1 Error term for the point $$i$$

$$
e_i = p_i - (RP_i' + t)
$$

### 1.2 Least square problem to find R,t by minimization of sum of the squared errors

$$
\min_{R, t} = \frac{1}{2}\sum_{i=1}^n ||(p_i - (Rp_i' + t))||_2^2
$$

## 2. Non-linear optimization

Express the poses in Lie algebra, the objective function:
$$
\min_\xi = \frac{1}{2} \sum_{i = 1}^n || (p_i -\exp (\xi ^\wedge)p'_i)||_2^2
$$
The derivative of a single error term using the Lie algebra perturbation model:
$$
\frac{\part e}{\part \delta \xi} = - (\exp(\xi ^\wedge)p'_i)^\odot
$$
