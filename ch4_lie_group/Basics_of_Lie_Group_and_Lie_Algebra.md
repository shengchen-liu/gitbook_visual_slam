# 4.1 Basics of Lie Group and Lie Algebra

## 4.1.1 Group

A group is an algebraic structure of **one set plus one operator**. 
$$
G = (A, \cdot)
$$
Properties:

- Closure
  $$
  \  \forall a_1, a_2 \in A, \  a_1 \cdot a_2 \in A
  $$
  
- Combination
  $$
  \forall a_1, a_2, a_3 \in A, \  (a_1 \cdot a_2) \cdot a_3 = a_1 \cdot ( a_2 \cdot a_3) 
  $$
  
- Unite Element
  $$
  \  \exists a_0 \in A, \  \mathrm{s.t.} \ \forall a \in A, \  a_0 \cdot a = a \cdot a_0 = a
  $$
  
- Inverse Element

$$
 \  \forall a \in A, \  \exists a^{-1} \in A, \  st \  a \cdot a^{-1} = a_0
$$

## 4.1.2 Introduction of the Lie Algebra

Consider an arbitrary rotation matrix $$\mathbf{R}$$

It satisfies:
$$
\mathbf{R}(t) \mathbf{R}(t) ^T = \mathbf{I}
$$
Deriving time on both sides yields:
$$
\dot{\mathbf{R}} (t) \mathbf{R} {(t)^T} + \mathbf{R} (t) \dot{\mathbf{R}} {(t) ^T} = 0.
$$
Move the second term to the right and commute the matrices by using the transposed relation:
$$
\dot{\mathbf{R}} (t) \mathbf{R} {(t)^T} = - \left( \dot{\mathbf{R}} (t) \mathbf{R} {(t)^T} \right)^T
$$
It can be seen that $$\dot{\mathbf{R}} (t) \mathbf{R} {(t)^T}$$ is a *skew-symmetric matrix*, which turns a vector into a skew-symmetric matrix:
$$
{\mathbf{a}^ \wedge } = \mathbf{A} = \left[ {\begin{array}{*{20}{c}}
    0&{ - {a_3}}&{ {a_2}}\\
    { {a_3}}&0&{ - {a_1}}\\
    { - {a_2}}&{ {a_1}}&0
    \end{array}} \right], \quad
{ \mathbf{A}^ \vee } = \mathbf{a}
$$
Since $$\dot{\mathbf{R}} (t) \mathbf{R} {(t)^T}$$ is a skew-symmetric matrix, we can find a 3-D vector $$\pmb{\phi} (t) \in \mathbb{R}^3$$:
$$
\dot{\mathbf{R}} (t) \mathbf{R}(t)^T = \pmb{\phi} (t) ^ {\wedge}
$$
Right multiply with $$\mathbf{R}(t)$$ on both sides, since $$\mathbf{R}(t)$$ is an orthogonal matrix, we have:
$$
\dot{\mathbf{R}} (t) = \pmb{\phi} (t)^{\wedge} \mathbf{R}(t) =
\left[ {\begin{array}{*{20}{c}}
    0&{ - {\phi _3}}&{ {\phi _2}}\\
    { {\phi _3}}&0&{ - {\phi _1}}\\
    { - {\phi _2}}&{ {\phi _1}}&0
    \end{array}} \right] \mathbf{R} (t)
$$
Time derivative of a rotation matrix is just by multiply a $$\phi^ {\wedge}(t)$$ matrix on the left. Consider $$\mathbf{R}(0) = \mathbf{I}$$ , we use the first-order Taylor expansion around $$t=t_0$$ to write $$\mathbf{R}(t)$$ as:
$$
\begin{aligned}
\mathbf{R} \left( t \right) & \approx \mathbf{R} \left( t_0 \right) + \dot {\mathbf{R}} \left( { {t_0}} \right)\left ( {t - {t_0}} \right)\\
&= \mathbf{I} + \pmb{\phi} {\left( { {t_0}} \right)^ \wedge } \left( t \right).
\end{aligned}
$$
We see that $$\pmb{\phi}$$ reflects the derivative of $$\mathbf{R}$$, so it is called the *tangent space* near the origin of $$\mathrm{SO}(3)$$

Solve for the above differential equation for $$\mathbf{R}$$, and with the initial value $$\mathbf{R}(0) = \mathbf{I}$$, we have:
$$
\mathbf{R}(t) = \exp \left( \pmb{\phi}_0^\wedge t \right).
$$

## 4.1.3 The definition of Lie Algebra

Each Lie group has a Lie algebra corresponding to it.

**Definition of Lie Algebra:**

A Lie algebra consists of a **set** $$\mathbb{V}$$, a **scalar field** $$\mathbb{F}$$, and a **binary operation** $$[,]$$. If they satisfy the following properties, then $$(\mathbb{V}, \mathbb{F}, [,])$$ is a Lie algebra, denoted as $$\mathfrak{g}$$.

- Closure (封闭性): 

  $$\forall \mathbf{X}, \mathbf{Y} \in \mathbb{V}; [\mathbf{X}, \mathbf{Y}] \in \mathbb{V}$$

- Bilinear Composition (双线性) : 

  $$\forall \mathbf{X},\mathbf{Y},\mathbf{Z} \in \mathbb{V}; a,b \in \mathbb{F }$$

  $$[a\mathbf{X}+b\mathbf{Y}, \mathbf{Z}] = a[\mathbf{X}, \mathbf{Z}] + b [ \mathbf{Y}, \mathbf{Z} ], \quad [\mathbf{Z}, a \mathbf{X}+b\mathbf{Y}] = a [\mathbf{Z}, \mathbf{X} ]+ b [\mathbf{Z},\mathbf{Y}]$$

- Reflexive (自反省): (Reflexive means that an element operates with itself results in zero)
  $$
  \forall \mathbf{X} \in \mathbb{V}; [\mathbf{X},\mathbf{X}] = \mathbf{0}
  $$
  
- Jacobi Identity (雅克比等价性)

$$
\forall \mathbf{X},\mathbf{Y},\mathbf{Z} \in \mathbb{V}; [\mathbf{X}, [ \mathbf{Y},\mathbf{Z}] ] + [\mathbf{Z}, [\mathbf{X},\mathbf{Y}] ] + [\mathbf{Y}, [\mathbf{Z}, \mathbf{X}]] =\mathbf{0}
$$

The binary operations $$[,]$$$ are called *Lie brackets*

## 4.1.4 Lie Algebra $$\mathfrak{so}(3)$$

The Lie algebra corresponding to $$\mathrm{SO}(3)$$ is a vector defined on $$\mathbb{R}^3$$, which we will denote as $$\pmb{\phi}$$.
$$
\pmb{\varPhi} = \pmb{\phi}^{\wedge} = \left[ {\begin{array}{*{20}{c}}
    0&{ - {\phi _3}}&{ {\phi _2}}\\
    { {\phi _3}}&0&{ - {\phi _1}}\\
    { - {\phi _2}}&{ {\phi _1}}&0
    \end{array}} \right] \in \mathbb{R}^{3 \times 3}.
$$
Lie bracket:
$$
[\pmb{\phi}_1, \pmb{\phi}_2] = \left( \mathbf{ \varPhi }_1 \mathbf{ \varPhi }_2 - \mathbf{ \varPhi }_2 \mathbf{ \varPhi }_1 \right)^\vee.
$$
Since the vector $$\pmb{\phi}$$ is one-to-one with the skew-symmetric matrix, we say the elements of $$\mathfrak{so}(3)$$ are three-dimensional vectors or three-dimensional skew-symmetric matrices, without any ambiguity:
$$
\mathfrak{so}(3) = \left\{ \pmb{\phi} \in \mathbb{R}^3 \ \text{or}\  \pmb{\varPhi} = \pmb{\phi^\wedge} \in \mathbb{ R}^{3 \times 3} \right\}.
$$
**$$\mathfrak{so}(3)$$ are just a set of 3D vectors that can express the derivative of the rotation matrix.** Its relationship to $\mathrm{SO}(3)$ is given by the exponential map:
$$
\mathbf{R} = \exp ( \pmb{\phi}^\wedge ).
$$

## 4.1.5 Lie Algebra $$\mathfrak{se}(3)$$

 Similar to $$\mathfrak{so}(3)$$, $$\mathfrak{se}(3)$$ is located in the $$\mathbb{R}^6$$ space:
$$
\mathfrak{se}(3) = \left\{ { \pmb{\xi} = \left[ \begin{array}{l}
    \pmb{\rho} \\
    \pmb{\phi}
    \end{array} \right]
    \in { \mathbb{R}^6} ,
    \pmb{\rho} \in { \mathbb{R}^3}, \pmb{\phi} \in \mathfrak{so} \left( 3 \right),{ \pmb{\xi} ^ \wedge } = \left[ {\begin{array}{*{20}{c}}
        { { \pmb{\phi} ^ \wedge }}& \pmb{\rho} \\
        { {\mathbf{0}^T}}&0
        \end{array}} \right] \in { \mathbb{R}^{4 \times 4}}} \right\}
$$
The first three dimensions are  'translation part' which is denoted as $$\pmb{\rho}$$;  the second part is a rotation part $$\pmb{\phi}$$, which is essentially a $$\mathfrak{so}(3)$$ element

$$ \mathfrak{se}(3) $$ as a 'vector consisting of a translation plus a $$\mathfrak{so}(3)$$ element'

Lie bracket:
$$
[ \pmb{\xi}_1, \pmb{\xi}_2 ] = \left( \pmb{\xi}_1^\wedge \pmb{\xi}_2^\wedge -\pmb{\xi}_2^ \wedge \pmb{\xi}_1^\wedge \right) ^\vee.
$$
