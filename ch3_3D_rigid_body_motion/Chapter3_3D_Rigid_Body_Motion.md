# Chapter 3: 3D Rigid Body Motion

## 3.1 Rotation Matrix

### 3.1.1 Points, Vectors and Coordinate Systems

Suppose in linear space, we find a set of base $$ (\pmb{e}_1,\pmb{e}_2,\pmb{e}_3) $$, then, an arbitrary vector $$ \pmb{a} $$ has a coordinate under this base:
$$
\pmb{a} = 
\left[ 
{ {\pmb{e}_1},
{\pmb{e}_2},
{\pmb{e}_3} } 
\right]
\left[ \begin{array}{l}
{a_1}\\
{a_2}\\
{a_3}
\end{array} \right] = {a_1}{\pmb{e}_1} + {a_2}{\pmb{e}_2} + {a_3}{\pmb{e}_3}.
$$
**Inner Product**
$$
\pmb{a} \cdot \pmb{b} = { \pmb{a}^T }\pmb{b} = \sum\limits_{i = 1}^3 { {a_i} {b_i} }  = \left| \pmb{a} \right|\left| \pmb{b} \right|\cos \left\langle {\pmb{a},\pmb{b}} \right\rangle
$$
The inner product can also describe the projection relationship between vectors.

**Outer Product**
$$
\pmb{a} \times \pmb{b} = \left\| {\begin{array}{*{20}{c}}
	\pmb{e}_1 & \pmb{e}_2 & \pmb{e}_3 \\
	{ {a_1}}&{ {a_2}}&{ {a_3}}\\
	{ {b_1}}&{ {b_2}}&{ {b_3}}
	\end{array}} \right\| = \left[ \begin{array}{l}
{a_2}{b_3} - {a_3}{b_2}\\
{a_3}{b_1} - {a_1}{b_3}\\
{a_1}{b_2} - {a_2}{b_1}
\end{array} \right] = \left[ {\begin{array}{*{20}{c}}
	0&{ - {a_3}}&{ {a_2}}\\
	{ {a_3}}&0&{-{a_1}}\\  
	{-{a_2}}&{ {a_1}}&0  
	\end{array}} \right] \pmb{b} \buildrel \Delta \over = { \pmb{a}^ \wedge } \pmb{b}.
$$
The result of the outer product is a vector whose direction is perpendicular to the two vectors, and the length is  $$ \left | \pmb{a} \right | \left | \pmb{b} \right | \left \langle { \pmb {a}, \pmb {b}} \right \rangle  $$, which is also the area of the quadrilateral of the two vectors.  

From the outer product operations, we introduce the $$^ \wedge$$ operator here, which means writing $$a$$ as a skew-symmetric matrix.
$$
\pmb{a}^\wedge = \left[ {\begin{array}{*{20}{c}}
	0&{-{a_3}}&{ {a_2}}\\  
	{ {a_3}}&0&{ - {a_1}}\\
	{ - {a_2}}&{ {a_1}}&0
	\end{array}} \right].
$$

### 3.1.2 Euclidean Transforms Between Coordinate Systems

The Euclidean transform consists of rotation and translation.

#### Rotation Matrix

$$
\left[ \begin{array}{l}
{a_1}\\
{a_2}\\
{a_3}
\end{array}\right]=\underbrace{\left[{\begin{array}{*{20}{c}}    
    {\pmb{e}_1^T\pmb{e}_1'} & {\pmb{e}_1^T\pmb{e}_2'} & {\pmb{e}_1^T\pmb{e}_3'}\\
    {\pmb{e}_2^T\pmb{e}_1'} & {\pmb{e}_2^T\pmb{e}_2'} & {\pmb{e}_2^T\pmb{e}_3'}\\
    {\pmb{e}_3^T\pmb{e}_1'} & {\pmb{e}_3^T\pmb{e}_2'} & {\pmb{e}_3^T\pmb{e}_3'}
    \end{array}} \right]}_{\text{rotation matrix}}\left[ \begin{array}{l}
a_1'\\
a_2'\\
a_3'
\end{array} \right] \buildrel \Delta \over = \pmb{R} \pmb{a}'
$$

Special property: rotation matrix is an orthogonal matrix with a determinant of 1.  Conversely, an orthogonal matrix with a determinant of 1 is also a rotation matrix.  So we can define a set of n dimensional rotation matrices as follows:
$$
\mathrm{SO}(n) = \{ \pmb{R} \in \mathbb{R}^{n \times n} | \pmb{R R}^T = \pmb{I}, \mathrm{det} (\pmb{R})=1 \}
$$
$$\mathrm{SO}(n) $$ refers to the  **special orthogonal group**

Since the rotation matrix is orthogonal, its inverse (i.e., transpose) describes an opposite rotation.
$$
\pmb{a} '= \pmb{R}^{-1} \pmb{a} = \pmb{R}^{T} \pmb{a}.
$$

#### Translation Matrix

$$
\pmb{a} '= \pmb{R} \pmb{a} + \pmb{t},
$$

### 3.1.3 Transform Matrix and Homogeneous Coordinates

$$
\left[\begin{array}{l} 
\pmb {a} ' \\
1
\end{array} \right] = 
\left[ {\begin{array}{*{20}{c}}
    \pmb{R}&\pmb{t}\\
    { {\pmb{0}^T}}&1
    \end{array}} \right]
\left[ \begin{array}{l}
\pmb {a} \\
1
\end{array} \right]  \buildrel \Delta \over = \pmb{T} \left[ \begin{array}{l}
\pmb {a} \\
1
\end{array} \right]
$$

Suppose we have two transformations: $$\pmb {R}_ 1, \pmb {t}_ 1 $$ and $$ \pmb {R}_ 2, \pmb {t}_ 2 $$
$$
\tilde{\pmb{b}} = \pmb{T}_1 \tilde{\pmb{a}}, \  \tilde{\pmb{c}} = \pmb{T}_2 \tilde{\pmb{b}} \quad \Rightarrow \tilde{\pmb{c}} = \pmb{T}_2 \pmb{T_1} \tilde{\pmb{a}}
$$
Note that if homogeneous coordinate transformation is not performed, the matrix multiplication here does not make sense.

The transformation matrix $$ \pmb{T} $$ has a special structure: the upper left corner is the rotation matrix, the right side is the translation vector, the lower-left corner is $$ \pmb{0} $$ vector, and the lower right corner is 1. This set of transform matrix is also known as the *special Euclidean group*:
$$
\mathrm{SE}(3) = \left\{ \pmb{T} = \left[ {\begin{array}{*{20}{c}}
    \pmb{R} & \pmb{t} \\
    { {\pmb{0}^T}} & 1
    \end{array}} \right]
\in \mathbb{R}^{4 \times 4} | \pmb{R} \in \mathrm{SO}(3), \pmb{t} \in \mathbb{R}^3\right\} 
$$
Like $$SO(3)$$, the inverse of the transform matrix represents an inverse transformation:
$$
{ \pmb{T}^{ - 1}} = \left[ {\begin{array}{*{20}{c}}
    { {\pmb{R}^T}}&{ - {\pmb{R}^T}\pmb{t}}\\
    { {\pmb{0}^T}}&1
    \end{array}} \right]
$$
