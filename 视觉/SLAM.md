## SLAM

### 0、数学知识：

- 向量的基础运算

  - 标量乘法
  - 向量加/减法
  - 向量长度
  - 单位向量
  - 向量点乘
  - 向量叉乘

  $$
  \overset{\rightarrow}{a}\times \overset{\rightarrow}{b}=\left( \begin{matrix}
  	\boldsymbol{i}&		\boldsymbol{j}&		\boldsymbol{k}\\
  	a_1&		a_2&		a_3\\
  	b_1&		b_2&		b_3\\
  \end{matrix} \right) =\left( \begin{array}{c}
  	a_2b_3-a_3b_2\\
  	a_3b_1-a_1b_3\\
  	a_1b_2-a_2b_1\\
  \end{array} \right) =\left( \begin{matrix}
  	0&		-a_3&		a_2\\
  	a_3&		0&		-a_1\\
  	-a_2&		a_1&		0\\
  \end{matrix} \right) b\overset{\bigtriangleup}{=}Ab
  $$

其中向量 **a** 与向量 **b** 都是列向量， $A$ 矩阵称为反对称矩阵（Skew-symmetric Matrix），反对称矩阵有 $A^T = -A$ 的性质。

两坐标系之间的变换的数学含义：一个坐标系的单位正交基是 $(e_1, e_2, e_3)$ 经过旋转之后的坐标系的单位正交基是 $(e_1^{'},e_2^{'},e_3^{'})$

，$(a_1,a_2,a_3)$  $(a_1^{'},a_2^{'},a_3^{'})$ 分别是两个坐标系下的同一点坐标，有如下的关系：
$$
\left( \begin{matrix}
	e_1&		e_2&		e_3\\
\end{matrix} \right) \left( \begin{array}{c}
	a_1\\
	a_2\\
	a_3\\
\end{array} \right) =\left( \begin{matrix}
	e_1^{'}&		e_2^{'}&		e_3^{'}\\
\end{matrix} \right) \left( \begin{array}{c}
	a_1^{'}\\
	a_2^{'}\\
	a_3^{'}\\
\end{array} \right)
$$
等式两边左乘 $(e_1^{T},e_2^{T},e_3^{T})^{T}$ 得到 
$$
\left( \begin{matrix}
	e_1^Te_1&		e_1^Te_2&		e_1^Te_3\\
	e_2^Te_1&		e_2^Te_2&		e_2^Te_3\\
	e_3^Te_1&		e_3^Te_2&		e_3^Te_3\\
\end{matrix} \right) \left( \begin{array}{c}
	a_1\\
	a_2\\
	a_3\\
\end{array} \right) =\left( \begin{matrix}
	e_1^Te_1^{'}&		e_1^Te_2^{'}&		e_1^Te_3^{'}\\
	e_2^Te_1^{'}&		e_2^Te_2^{'}&		e_2^Te_3^{'}\\
	e_3^Te_1^{'}&		e_3^Te_2^{'}&		e_3^Te_3^{'}\\
\end{matrix} \right) \left( \begin{array}{c}
	a_1^{'}\\
	a_2^{'}\\
	a_3^{'}\\
\end{array} \right)
$$
其中 $\left( \begin{matrix}
	e_1^Te_1&		e_1^Te_2&		e_1^Te_3\\
	e_2^Te_1&		e_2^Te_2&		e_2^Te_3\\
	e_3^Te_1&		e_3^Te_2&		e_3^Te_3\\
\end{matrix} \right) $ 为**单位矩阵**，因此有 

$$\left( \begin{array}{c}
	a_1\\
	a_2\\
	a_3\\
\end{array} \right) =\left( \begin{matrix}
	e_1^Te_1^{'}&		e_1^Te_2^{'}&		e_1^Te_3^{'}\\
	e_2^Te_1^{'}&		e_2^Te_2^{'}&		e_2^Te_3^{'}\\
	e_3^Te_1^{'}&		e_3^Te_2^{'}&		e_3^Te_3^{'}\\
\end{matrix} \right) \left( \begin{array}{c}
	a_1^{'}\\
	a_2^{'}\\
	a_3^{'}\\
\end{array} \right) \overset{\bigtriangleup}{=}Ra^{'}$$

- R是旋转矩阵有如下两点性质：
  - R是正交的
  - $det(A) = 1$
- 引出李群与李代数 $SO\left( n \right) \ =\ \left\{ R\subset \mathbb{R}^{n\times n}|RR^T=1,\ \det \left( R \right) =1 \right\} $
- Rotation from frame 2 to frame 1 can be written as:

$a_1=R_{12}a_2$ and vise versa: $a_2=R_{21}a_1$ 

其中 $R_{12}=R_{21}^{-1}=R_{12}^{T}$ 

旋转加上平移矩阵得到

$a^{'}=Ra+t$

其次形式为：

$$\left( \begin{array}{c}
	a^{'}\\
	1\\
\end{array} \right) =\left( \begin{matrix}
	\boldsymbol{R}&		\boldsymbol{t}\\
	0^T&		1\\
\end{matrix} \right) \left( \begin{array}{c}
	a\\
	1\\
\end{array} \right) \overset{\bigtriangleup}{=}\boldsymbol{T}\left( \begin{array}{c}
	a\\
	1\\
\end{array} \right)$$， $T^{-1}=\left( \begin{matrix}
	R^T&		-R^Tt\\
	0^T&		1\\
\end{matrix} \right) $



四元素的公式以及推导还是要查查资料的！！

- 四元素（Quaternion）

  **为什么会有四元素这个东西？**

  - 二维平面

    有 $z=x+yi$， 其中 $i$ 是虚数单位

    如下性质：

    ​	乘以 $i$ 就是旋转90度

  - 三维空间

    有 $q=q_0+q_1i+q_2j+q_3k$，其中 $q_0$ 是实数，$i、j、k$ 是虚数单位；

    如下性质：
    $$
    
    $$

### 1、相机类型

- 单目相机：需要其他方法确定深度信息
  - 小孔成像模型

- 双目相机：通过视差确定深度



- 深度相机：激光雷达，发射激光发射回来确定深度

- 其他：Omidirectional, Event Camera

- 多传感器融合：

### 2、状态估计

$\left\{ \begin{array}{l}
	x_k=f\left( x_{k-1},\ u_k,\ w_k \right) 运动方程\\
	z_{k,\ j}=h\left( y_j,\ x_k,\ v_{k,\ j} \right)观测方程\\
\end{array} \right.$



运动：考虑从 $k-1$ 到 $k$ 时刻，一个扫地机器人位置 $x$ 是如何变化的，$u_k$ 是运动传感器的观测数据， $w_k$ 是一个噪声。

观测：假设扫地机器人在 $k$ 时刻在 $x_k$ 位置处探测到某一个路标 $y_j$, 产生了一个观测数据 $z_{k,j}$ ，$v_{k,j}$ 是一个噪声。

#### ①、批量模型

- Give all the measurements

- To estimate all the state variables

  



#### ②、增量模型

### 3、回环检测：

- 纠正一些误差

### 4、mapping：

$\left\{ \begin{array}{l}
	x_k=f\left( x_{k-1},\ u_k,\ w_k \right)\\
	z_{k,\ j}=h\left( y_j,\ x_k,\ v_{k,\ j} \right)\\
\end{array} \right.$

- 运动模型 ​
- 观测模型

