# Chapter 3: 3D Rigid Body Motion

## 3.1 Rotation Matrix

### 3.1.1 Points, Vectors and Coordinate Systems

Suppose in linear space, we find a set of base $$ (\mathbf{e}_1,\mathbf{e}_2,\mathbf{e}_3) $$, then, an arbitrary vector $$ \mathbf{a} $$ has a coordinate under this base:
$$
\mathbf{a} = 
\left[ 
{ {\mathbf{e}_1},
{\mathbf{e}_2},
{\mathbf{e}_3} } 
\right]
\left[ \begin{array}{l}
{a_1}\\
{a_2}\\
{a_3}
\end{array} \right] = {a_1}{\mathbf{e}_1} + {a_2}{\mathbf{e}_2} + {a_3}{\mathbf{e}_3}.
$$
**Inner Product**
$$
\mathbf{a} \cdot \mathbf{b} = { \mathbf{a}^T }\mathbf{b} = \sum\limits_{i = 1}^3 { {a_i} {b_i} }  = \left| \mathbf{a} \right|\left| \mathbf{b} \right|\cos \left\langle {\mathbf{a},\mathbf{b}} \right\rangle
$$
The inner product can also describe the projection relationship between vectors.

**Outer Product**
$$
\mathbf{a} \times \mathbf{b} = \left\| {\begin{array}{*{20}{c}}
	\mathbf{e}_1 & \mathbf{e}_2 & \mathbf{e}_3 \\
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
	\end{array}} \right] \mathbf{b} \buildrel \Delta \over = { \mathbf{a}^ \wedge } \mathbf{b}.
$$
The result of the outer product is a vector whose direction is perpendicular to the two vectors, and the length is  $$ \left | \mathbf{a} \right | \left | \mathbf{b} \right | \left \langle { \mathbf {a}, \mathbf {b}} \right \rangle  $$, which is also the area of the quadrilateral of the two vectors.  

From the outer product operations, we introduce the $$^ \wedge$$ operator here, which means writing $$a$$ as a skew-symmetric matrix.
$$
\mathbf{a}^\wedge = \left[ {\begin{array}{*{20}{c}}
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
    {\mathbf{e}_1^T\mathbf{e}_1'} & {\mathbf{e}_1^T\mathbf{e}_2'} & {\mathbf{e}_1^T\mathbf{e}_3'}\\
    {\mathbf{e}_2^T\mathbf{e}_1'} & {\mathbf{e}_2^T\mathbf{e}_2'} & {\mathbf{e}_2^T\mathbf{e}_3'}\\
    {\mathbf{e}_3^T\mathbf{e}_1'} & {\mathbf{e}_3^T\mathbf{e}_2'} & {\mathbf{e}_3^T\mathbf{e}_3'}
    \end{array}} \right]}_{\text{rotation matrix}}\left[ \begin{array}{l}
a_1'\\
a_2'\\
a_3'
\end{array} \right] \buildrel \Delta \over = \mathbf{R} \mathbf{a}'
$$

Special property: rotation matrix is an orthogonal matrix with a determinant of 1.  Conversely, an orthogonal matrix with a determinant of 1 is also a rotation matrix.  So we can define a set of n dimensional rotation matrices as follows:
$$
\mathrm{SO}(n) = \{ \mathbf{R} \in \mathbb{R}^{n \times n} | \mathbf{R R}^T = \mathbf{I}, \mathrm{det} (\mathbf{R})=1 \}
$$
$$\mathrm{SO}(n) $$ refers to the  **special orthogonal group**

Since the rotation matrix is orthogonal, its inverse (i.e., transpose) describes an opposite rotation.
$$
\mathbf{a} '= \mathbf{R}^{-1} \mathbf{a} = \mathbf{R}^{T} \mathbf{a}.
$$

#### Translation Matrix

$$
\mathbf{a} '= \mathbf{R} \mathbf{a} + \mathbf{t},
$$

### 3.1.3 Transform Matrix and Homogeneous Coordinates

$$
\left[\begin{array}{l} 
\mathbf {a} ' \\
1
\end{array} \right] = 
\left[ {\begin{array}{*{20}{c}}
    \mathbf{R}&\mathbf{t}\\
    { {\mathbf{0}^T}}&1
    \end{array}} \right]
\left[ \begin{array}{l}
\mathbf {a} \\
1
\end{array} \right]  \buildrel \Delta \over = \mathbf{T} \left[ \begin{array}{l}
\mathbf {a} \\
1
\end{array} \right]
$$

Suppose we have two transformations: $$\mathbf {R}_ 1, \mathbf {t}_ 1 $$ and $$ \mathbf {R}_ 2, \mathbf {t}_ 2 $$
$$
\tilde{\mathbf{b}} = \mathbf{T}_1 \tilde{\mathbf{a}}, \  \tilde{\mathbf{c}} = \mathbf{T}_2 \tilde{\mathbf{b}} \quad \Rightarrow \tilde{\mathbf{c}} = \mathbf{T}_2 \mathbf{T_1} \tilde{\mathbf{a}}
$$
Note that if homogeneous coordinate transformation is not performed, the matrix multiplication here does not make sense.

The transformation matrix $$ \mathbf{T} $$ has a special structure: the upper left corner is the rotation matrix, the right side is the translation vector, the lower-left corner is $$ \mathbf{0} $$ vector, and the lower right corner is 1. This set of transform matrix is also known as the *special Euclidean group*:
$$
\mathrm{SE}(3) = \left\{ \mathbf{T} = \left[ {\begin{array}{*{20}{c}}
    \mathbf{R} & \mathbf{t} \\
    { {\mathbf{0}^T}} & 1
    \end{array}} \right]
\in \mathbb{R}^{4 \times 4} | \mathbf{R} \in \mathrm{SO}(3), \mathbf{t} \in \mathbb{R}^3\right\} 
$$
Like $$SO(3)$$, the inverse of the transform matrix represents an inverse transformation:
$$
{ \mathbf{T}^{ - 1}} = \left[ {\begin{array}{*{20}{c}}
    { {\mathbf{R}^T}}&{ - {\mathbf{R}^T}\mathbf{t}}\\
    { {\mathbf{0}^T}}&1
    \end{array}} \right]
$$
