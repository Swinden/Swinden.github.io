---
layout:     post   				    # 使用的布局（不需要改）
title:       Introduction to Linear Algebra学习 				# 标题 
subtitle:   线代学习 #副标题
date:       2023-07-3 				# 时间
categories: Blog
author:     星辰菜鸟 						# 作者
catalog: true 						# 是否归档
tags:								#标签
    - Blog
   - 线性代数
---



# Introduction to Linear Algebra

[TOC]

## 1向量的介绍

### 1.1向量和线性组合



### 1.2长度(模)和点积



### 1.3矩阵

## 2解线性方程组

### 2.1向量和线性方程组

### 2.2消元的概念

### 2.3使用矩阵进行消元

### 2.4矩阵运算规则

### 2.5逆矩阵

### 2.6消元=因式分解：$A = LU$

### 2.7转置和置换





## 3向量空间与子空间

### 3.1向量空间

### 3.2矩阵$A$的零空间：解$Ax=0$和$Rx=0$

### 3.3方程$Ax=b$的完全解

### 3.4线性独立性、基和维数

### 3.5四个子空间的维数



## 4正交性

### 4.1四个子空间的正交性

### 4.2投影

### 4.3最小二乘逼近

### 4.4正交基与施密特正交归一化







## 5行列式

> 1. 行列式$A={\begin{bmatrix}a&b\\ c&d\end{bmatrix}}$ 的值为$ad - bc$。奇异矩阵$A=\begin{bmatrix}a&xa\\ c&xc\end{bmatrix}$的行列式为$0$。
> 2. 行交换会变号：$PA=\begin{bmatrix}0&1\\ 1&0\end{bmatrix}\begin{bmatrix}a&b\\ c&d\end{bmatrix}=\begin{bmatrix}c&d\\ a&b\end{bmatrix}$有$\det PA=bc-ad=-\det A$
> 3. 矩阵$\left[\begin{array}{cc}xa+yA&xb+yB\\ c&d\end{array}\right]$的行列式为$x(ad-bc)+y(Ad-Bc)$。行列式在第一行是线性的，可以由自身得出。
> 4. 消元：$E A={\left[\begin{array}{c}{a}&{b}\\ {0}&{d-{\frac{c}{a}}b}\end{array}\right]}$ $\det EA=a\left(d-\frac{c}{a}b\right)=\text{主元乘积}=\det A$
> 5. 如果A是$n \times  n$的矩阵，那么$1$、$2$、$3$、$4$仍然成立：当A是奇异矩阵时，行列式为$0$；当行交换时，行列式变号；行列式在第一行是线性的，可以由自身得出；行列式等于主元的乘积。对于任意矩阵$B$，总有$\det(BA) = (\det B)(\det A)$和$\det(A^T) = \det A$。这是一个令人惊奇的数字。

### 5.1行列式的性质

----

&emsp;&emsp;方阵的行列式是一个单独的数值。这个数值包含了关于矩阵的大量信息。它可以立即判断矩阵是否可逆。当矩阵$A$不可逆时，行列式为零。当$A$可逆时，$A^{-1}$的行列式为$1/(\det A)$。实际上，行列式还可以导出$A^{-1}$中每个元素的公式。

&emsp;&emsp;这是行列式的一个应用，用于找到逆矩阵、主元和解$A^{-1}b$的公式。对于大型矩阵，我们很少使用这些公式，因为消元法更快。对于一个$2\times 2$的矩阵，其元素为$a$、$b$、$c$、$d$，其行列式$ad - bc$显示了$A^{-1}$随着$A$的变化而变化。请注意行列式的除法！
$$
A=\begin{bmatrix}a&b\\ c&d\end{bmatrix}\quad\text{has inverse}\quad A^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d&-b\\ -c&a\end{bmatrix}
$$
将这些矩阵相乘得到单位矩阵$I$。当行列式为$ad - bc = 0$时，我们被要求除以零，而我们无法这样做——因此A没有逆矩阵。（当$a/c=b/d$时，行是线性相关。这给出了$ad = bc$和$\det A = 0$。）线性相关的行总是导致$\det A = 0$。

&emsp;&emsp;行列式也与主元相关。对于一个$2\times 2$的矩阵，主元是$a$和$d - (c/ a)b$。**主元的乘积就是行列式的值**：
$$
\mathbf{\text{主元乘积}}\quad a\Big(d-\frac{c}{a}b\Big)=ad-bc \quad\mathbf{\text{是}}\quad \det{A}
$$
&emsp;&emsp;经过行交换后，主元变为$c$和$b - (a/ c) d$。这两个新的主元相乘得到$bc - ad$。行交换到$\left[\begin{array}{cc}\mathbf{c}&\mathbf{d}\\ \mathbf{a}&\mathbf{b}\end{array}\right]$改变了行列式的符号。

> 一个$n$行$n$列矩阵的行列式可以通过三种方式来计算：
>
> 1. **pivot formula**(**主元公式**)：将$n$个主元相乘（乘以$1$或$-1$）
>
>    
>
> 2. **"big" formula**：将n!个项相加（乘以1或-1）
>    $$
>    \sum\limits_{{j_1}{j_2} \ldots {j_n}} {{{\left( { - 1} \right)}^{\tau \left( {{j_1}{j_2} \ldots {j_n}} \right)}}{a_{1{j_1}}}{a_{2{j_2}}} \cdots {a_{n{j_n}}}}  = \sum\limits_{{i_1}{i_2}{i_3} \ldots {i_n}} {{{\left( { - 1} \right)}^{\tau \left( {{i_1}{i_2} \ldots {i_n}} \right)}}{a_{{i_1}1}}{a_{{i_2}2}} \cdots {a_{{i_n}n}}}
>    $$
>    
>
> 3. **cofactor formula** (**余子式公式**)：将n个较小的行列式组合起来（乘以1或-1）
>    $$
>    \sum\limits_{j = 1}^n {{a_{ij}}} {A_{ij}} = \sum\limits_{i = 1}^n {{a_{ij}}} {A_{ij}}\quad {A_{ij}} = {( - 1)^{i + j}}{M_{ij}}\quad{M_{ij}}\text{余子式:除去i行j列后的行列式}
>    $$

你可以看到加号"$+$"或减号"$-$"(在$−1$和$1$之间做决策)在行列式中起着重要的作用。这来自于n行n列矩阵的以下规则：

>**当交换两行（或两列）时，行列式的符号会改变。**

单位矩阵的行列式为$+1$。交换两行后，$\det P = -1$。再交换两行，新的排列的行列式为$\det P = +1$。一半的排列是偶排列（$\det P = 1$），一半是奇排列（$\det P = -1$）。从单位矩阵$I$开始，一半的$P$需要进行偶数次交换，一半需要进行奇数次交换。在$2$行$2$列的情况下，$ad$有正号，$bc$有负号——来自行交换：
$$
\det\begin{bmatrix}1&0\\ 0&1\end{bmatrix}=1\quad\text{and}\quad\det\begin{bmatrix}0&1\\ 1&0\end{bmatrix}=-1
$$
&emsp;&emsp;另一个基本规则是线性性质——但首先要提个警告。线性性性质并不意味着$\det(A + B) = \det A+ \det B$。**这是绝对错误的**。即使在$A= I$和$B =I$的情况下，这种线性性质也不成立。错误的规则会说$\det(I + I) = 1 + 1 = 2$。正确的规则是$\det 2I = 2 ^n$。当矩阵乘以$2$时，行列式会乘以$2^n$（而不仅仅是乘以$2$）。

&emsp;&emsp;我们不打算通过公式来定义行列式。最好从它的性质——符号变号和线性性质——开始。这些性质很简单（第5.1节）。它们为公式做好了准备（第5.2节）。然后是应用，包括以下三个方面：

> 1. 行列式给出了$A^{-1}$和$A^{-1}b$（这个公式被称为**克莱默法则**）。
>
>    
>
> 2. 当一个箱子的边界是矩阵$A$的行时，体积为$|\det A|$。
>
>    
>
> 3. 对于$n$个特殊的数$\lambda$，称为**特征值**，矩阵$A-\lambda I$的行列式为零。这是一个非常重要的应用，填充了第6章。

#### 5.1.1行列式的性质包括

行列式具有三个基本性质（规则1、2、3）。通过使用这些规则，我们可以计算任意方阵$A$的行列式。**这个数可以用两种方式表示，$\det A$和$|A|$**。注意：矩阵用方括号表示，行列式用直线表示。当$A$是一个2行2列的矩阵时，规则1、2、3会得出我们期望的答案：
$$
\begin{bmatrix}a&b\\ c&d\end{bmatrix}\quad\text{的行列式是}\quad\begin{vmatrix}a&b\\ c&d\end{vmatrix}=ad-bc
$$
&emsp;&emsp;规则1（最简单的）将$\det I= 1$与单位立方体的体积$1$相匹配。



1. **n行n列的单位矩阵的行列式为1。**
   $$
   \begin{vmatrix}1&0\\ 0&1\end{vmatrix}=1\quad\text{and}\quad\begin{vmatrix}1\\ &\ddots\\ &&1\end{vmatrix}=1.
   $$
   
   
   
2. **当交换两行时，行列式的符号会改变**（符号变号）：
   $$
   \text{Check:}\quad\begin{vmatrix}c&d\\ a&b\end{vmatrix}=-\begin{vmatrix}a&b\\ c&d\end{vmatrix}\quad(\text{both sides equal}\;bc-ad).
   $$


   由于这个规则，我们可以找到任意排列矩阵$P$的行列式$\det P$。只需交换$I$的行，直到达到$P$。然后，对于**偶数**次行交换，$\det P = +1$，而对于**奇数**次行交换，$\det P = -1$。

   &emsp;&emsp;第三个规则必须跳跃到所有矩阵的行列式。

   

   

3. **行列式是每一行分别的线性函数**（其他行保持不变）。

   如果第一行乘以$t$，行列式也乘以$t$。如果第一行相加，行列式也相加。这个规则只适用于其他行不变的情况！注意$c$和$d$保持不变：

   **将第一行乘以任意数$t$，行列式也会乘以$t$。**
   $$
   \begin{vmatrix}ta&tb\\ c&d\end{vmatrix}=t\begin{vmatrix}a&b\\ c&d\end{vmatrix}
   $$

   将矩阵$A$的第一行加到$A'$的第一行上：然后行列式相加。
   $$
   \begin{vmatrix}a+a'&b+b'\\ c&d\end{vmatrix}=\begin{vmatrix}a&b\\ c&d\end{vmatrix}+\begin{vmatrix}a'&b'\\ c&d\end{vmatrix}
   $$
   在第一种情况下，两边都是$tad - tbc$。然后$t$可以因式分解出来。在第二种情况下，两边都是$ad + a' d - bc - b' c$。当$A$为$n$乘$n$的矩阵且**一行发生变化**时，这些规则仍然适用。
   $$
   4={\left|\begin{array}{l l l l}{4}&{8}&{8}\\ {0}&{1}&{1}\\ {0}&{0}&{1}\end{array}\right|}=4{\left|\begin{array}{l l l}{1}&{2}&{2}\\ {0}&{1}&{1}\\ {0}&{0}&{1}\end{array}\right|}\quad{\mathrm{and}}\quad{\left|\begin{array}{l l l}{4}&{8}&{8}\\ {0}&{1}&{1}\\ {0}&{0}&{1}\end{array}\right|}={\left|\begin{array}{l l l}{4}&{0}&{0}\\ {0}&{1}&{1}\\ {0}&{0}&{1}\end{array}\right|}+{\left|\begin{array}{l l l}{0}&{8}&{8}\\ {0}&{1}&{1}\\ {0}&{0}&{1}\end{array}\right|}
   $$
   单独来看，规则3并没有说明这些行列式是多少（$\det A$是4）。

   &emsp;&emsp;通过乘法和加法的组合，我们可以得到一行中的任意线性组合。行交换的规则2可以将该行放到第一行的位置，然后再放回原来的位置。

   &emsp;&emsp;这个规则并不意味着$\det 2I = 2 \det I$。要得到$2I$，我们必须将两行都乘以2，而因子2会在两次计算中都出现：
   $$
   \begin{vmatrix}2&0\\0&2\end{vmatrix}=2^2=4\quad\mathrm{and}\quad\begin{vmatrix}t&0\\0&t\end{vmatrix}=t^2
   $$
   这就像是面积和体积一样。将一个矩形扩大2倍，它的面积增加4倍。将一个$n$维的盒子按比例扩大$t$倍，它的体积增加$t^n$倍。这种联系并非偶然——我们将会看到行列式等于体积。

   &emsp;&emsp;请特别注意规则1-3。它们完全确定了数值$\det A$。我们可以在这里停下来寻找一个$n\times n$行列式的公式（有点复杂）。但我们更愿意逐步进行，因为规则4-10使得行列式的计算更加简单。

   

   

4. **如果矩阵$A$的两行相等，则$\det A = 0$**
   $$
   \text{Equal rows}\quad\text{Check 2 by 2}:\quad\begin{vmatrix}a&b\\a&b\end{vmatrix}=0.
   $$
   规则4可以从规则2推导出来（记住我们必须使用规则而不是2乘2的公式）。交换两个相等的行。行列式$D$应该改变符号。但是$D$也必须保持不变，因为矩阵没有改变。唯一满足$-D = D$的数是$D = 0$——这就是行列式。（注意：在布尔代数中，这种推理会失败，因为$-1 = 1$。然后行列式$D$由规则1、3和4定义。）

   &emsp;&emsp;一个具有两行相等的矩阵没有逆矩阵。规则4表明行列式$\det A = 0$。但是矩阵可以是奇异的，行列式可以为零，而不一定有相等的行！规则5将是关键。我们可以进行行操作（如消元）而不改变行列式$\det A$。

   

   

5. **从一行中减去另一行的倍数不会改变行列式$\det A$**
   $$
   \begin{array}{c}\ell\text{ times row}1\text{ from row 2}\end{array}\quad\begin{vmatrix}a&b\\c-\ell a&d-\ell b\end{vmatrix}=\begin{vmatrix}a&b\\c&d\end{vmatrix}.
   $$
   规则3（线性性质）将左侧分成右侧和另一个项$-\ell \begin{vmatrix}a&b\\a&b\end{vmatrix}$。根据规则4（相等的行），这个额外的项为零。因此，规则5是正确的（不仅适用于$2 \times 2$矩阵）。

   结论：在从矩阵$A$经过常规的消元步骤得到上三角矩阵$U$的过程中，行列式保持不变。因此，$\det A$等于$\det U$。如果我们能够找到上三角矩阵$U$的行列式，就能找到任意矩阵$A$的行列式。每次行交换都会改变符号，因此$\det A$总是等于$\pm \det U$。规则5将问题限定到了上三角矩阵的行列式计算上。

   

   

6. **具有一行全为零的矩阵的行列式为$\det A = 0$**
   $$
   \textbf{Row of zeros}\quad\begin{vmatrix}0&0\\c&d\end{vmatrix}=0\quad\text{and}\quad\begin{vmatrix}a&b\\0&0\end{vmatrix}=0
   $$
   为了进行简单的证明，将某一行加到零行上。行列式不会改变（规则5）。但是矩阵现在有两行相等。所以根据规则4，$\det A = 0$。

   

   

7. **如果矩阵$A$是上（下）三角形矩阵，则行列式$\det A = a_{11}a_{22} \cdots  a_{nn}$，即对角线元素的乘积。**
   $$
   \text{Triangular}\quad\begin{vmatrix}a&b\\0&d\end{vmatrix}=ad\quad\text{and also}\quad\begin{vmatrix}a&0\\c&d\end{vmatrix}=ad
   $$
   假设所有对角线上的元素均非零。通过消元法去除非对角线上的元素！（如果矩阵$A$是下三角矩阵，则从较低的行中减去倍数的每一行。如果矩阵$A$是上三角矩阵，则从较高的行中减去。）根据规则5，行列式不会改变——现在矩阵是对角矩阵：
   $$
   \textbf{Diagonal matrix}\quad\det\begin{bmatrix}a_{11}&&&&0\\&a_{22}&&&\\&&& \ddots &\\&&&&a_{nn}\end{bmatrix}=(a_{11})(a_{22})\cdots(a_{nn})
   $$
   根据规则3，从第一行因式分解出$a_{11}$。然后从第二行因式分解出$a_{22}$。最后从最后一行因式分解出$a_{nn}$。行列式等于$a_{11}\times a_{22}\times \cdots \times a_{nn}\times\det I$。然后应用规则1（最后使用！）得到$\det I = 1$。

   &emsp;&emsp;如果对角线上的元素$a_{ii}$为零怎么办？那么上三角矩阵$A$是奇异的（不可逆的）。消元会产生一行全为零的情况。根据规则5，行列式保持不变，根据规则6，一行全为零意味着$\det A = 0$。我们达到了检验矩阵**奇异或可逆**的重要测试。

   

   

8. **如果矩阵$A$是奇异的（不可逆），则行列式$\det A = 0$。如果矩阵$A$是可逆的，则行列式$\det A \neq 0$。**
   $$
   \textbf{Singular}\quad\begin{bmatrix}a&b\\c&d\end{bmatrix}\quad\text{is singular if and only if}\quad ad-bc=0
   $$
   **证明**       消元过程将矩阵$A$转化为矩阵$U$。如果矩阵$A$是奇异的，则矩阵$U$会有一行全为零。根据规则，$\det A = \det U = 0$。如果矩阵$A$是可逆的，则矩阵$U$的对角线上有主元。非零主元的乘积（使用规则7）得到非零的行列式：
   $$
   \textbf{Multiply pivots}\quad det A=\pm det U=\pm (\textbf{product of the pivots})
   $$
   &emsp;&emsp;这是行列式的第一个公式。MATLAB使用主元的乘积来计算行列式$\det A$。正负号$\pm\det U$取决于行交换的次数是偶数还是奇数：$+1$或$-1$是交换行的置换矩阵$P$的行列式。

   &emsp;&emsp;如果没有进行行交换，置换矩阵$P$为单位矩阵$I$，此时$\det A = \det U$等于主元的乘积。而且，$\det L = 1$。
   $$
   \mathrm{If}\quad PA=LU\quad\mathrm{then}\quad\det P\det A=\det L\det U\quad\mathrm{and}\quad\det A=\pm\det U
   $$
   
   
   
9. **矩阵乘积AB的行列式等于矩阵A的行列式乘以矩阵B的行列式：$\det(AB) = \det(A) \det(B)$与$|AB| = |A|  |B|$。**
   $$
   \text{Product rule}\quad\begin{vmatrix}a&b\\c&d\end{vmatrix}\begin{vmatrix}p&q\\r&s\end{vmatrix}=\begin{vmatrix}ap+br&aq+bs\\cp+dr&cq+ds\end{vmatrix}
   $$
   当矩阵$B$是矩阵$A^{-1}$时，这个规则表明$A^{-1}$的行列式等于$1/\det A$：
   $$
   A\;\text{times}\;A^{-1}\quad AA^{-1}=I\quad\text{so}\quad(\det A)(\det A^{-1})=\det I=1
   $$
   这个乘法规则是迄今为止最复杂的规则。即使是$2\times 2$的情况也需要一些代数运算：
   $$
   |A||B| = (ad - bc)(ps - qr) = (ap + br)(cq + ds) - (aq + bs)(cp + dr) = |AB|
   $$
   对于$n$阶情况，以下是一个简洁的证明：$|AB| = |A||B|$。当$|B|$不为零时，考虑比值$D(A) = {|AB|}/{|B|}$。检查这个比值$D(A)$具有性质1、2、3。那么$D(A)$必须是行列式，我们有$| AB | / | B| = | A |$。很好。

   > **性质1**     （单位矩阵的行列式）如果$A=I$，那么比值$D(A)$变为$|B|/|B|=1$。
   >
   > **性质2**      （符号变号）当交换矩阵$A$的两行时，矩阵$AB$的相同两行也会被交换。因此，$|AB|$改变符号，比值$|AB|/|B|$也改变符号。
   >
   > **性质3**       （线性性质）当将矩阵$A$的第一行乘以$t$时，矩阵$AB$的第一行也会被乘以$t$。这将使行列式$|AB|$乘以$t$。因此，比值$|AB|/|B|$也会乘以$t$。将矩阵$A$的第一行加到矩阵$A'$的第一行上。然后矩阵$AB$的第一行加到矩阵$A'B$的第一行上。根据规则3，行列式相加。除以$|B|$后，比值相加——如所期望的那样。
   >
   > 结论      比值$|AB|/|B|$具有与定义$|A|$相同的三个性质。因此，它等于$|A|$。这证明了乘法规则$|AB| = |A||B|$。当$|B|=0$时是一个单独且简单的情况，因为当$B$是奇异矩阵时，$AB$也是奇异的。那么$|AB| = |A||B|$变为$0=0$。

   

   

10. **转置矩阵$A^T$与矩阵$A$具有相同的行列式**

$$
\textbf{Transpose}\quad\begin{vmatrix}a&b\\c&d\end{vmatrix}=\begin{vmatrix}a&c\\b&d\end{vmatrix}\quad\text{since both sides equal}\quad ad-bc
$$

方程$|A^T| = |A|$在矩阵$A$奇异时变为$0=0$（我们知道$A^T$也是奇异的）。否则，$A$具有常规的因式分解$PA = LU$。对两边进行转置得到$A^T P^T = U^T L^T$。使用规则9进行乘法的证明，可以得到$|A| = |A^T|$：
$$
\text{Compare}\quad\det P\det A=\det L\det U\quad\text{with}\quad\det A^\mathrm{T}\det P^\mathrm{T}=\det U^\mathrm{T}\det L^\mathrm{T}
$$
首先，$det L = det L^T = 1$（两者在对角线上都有1）。其次，$det U = det U^T$（这些上三角矩阵具有相同的对角线元素）。第三，$det P = det P^T$（排列矩阵满足$P^T P = I$，因此根据规则9，$|P^T| |P| = 1$；因此，$|P|$和$|P^T|$都等于1或者都等于-1）。因此，矩阵$L$、$U$、$P$与$L^T$、$U^T$、$P^T$具有相同的行列式值，从而得到$det A = det A^T$。

**关于列的重要内容**        对于行的每个规则都可以应用于列（只需通过转置，因为$|A| = |A^T|$）。当两列交换时，行列式的符号会改变。一个零列或两个相等的列将使行列式为零。如果将一列乘以$t$，行列式也将乘以$t$。行列式是每一列分别的线性函数。

&emsp;&emsp;好的，我们到此为止。性质的学习已经结束了。接下来我们将找到并使用行列式的显式公式。





#### 5.1.2重点回顾

1. 行列式是通过以下方式定义的：$\det I=1$，符号变号，以及每行中的线性性质。
2. 在进行消元后，行列式 det A 等于$\pm\text{ (product of the pivots)}$。
3. 当且仅当矩阵 A 不可逆时，行列式为零。
4. 两个显著的性质是行列式的乘积规则：$\det(AB) = \det(A) \det(B)$，以及行列式的转置性质：$det(A^T) = det(A)$。

#### 5.1.3实例

**5.1 A**      对矩阵 $A$ 进行这些操作，并计算$ M_1$、$M_2$、$M_3$、$M_4$ 的行列式：

> 在矩阵$M_1$中，将每个$a_{ij}$乘以$(-1)^{i+j}$会产生一个棋盘格的符号模式。
>
> 在矩阵$M_2$中，将矩阵$A$的第一行、第二行和第三行分别从第二行、第三行和第一行中相减。
>
> 在矩阵$M_3$中，将矩阵$A$的第一行、第二行和第三行分别加到第二行、第三行和第一行上。

矩阵$M_1$、$M_2$和$M_3$的行列式与矩阵$A$的行列式之间有何关系？
$$
\begin{bmatrix}a_{11}&-a_{12}&a_{13}\\-a_{21}&a_{22}&-a_{23}\\a_{31}&-a_{32}&a_{33}\end{bmatrix}\quad\begin{bmatrix}\text{row }1-\text{row }3\\\text{row }2-\text{row }1\\\text{row }3-\text{row }2\end{bmatrix}\quad\begin{bmatrix}\text{row }1+\text{row }3\\\text{row }2+\text{row }1\\\text{row }3+\text{row }2\end{bmatrix}
$$
**解答**      这三个行列式分别为$\det A$，$0$和$2\det A$。下面是原因：
$$
M_1=\begin{bmatrix}1\\&-1\\&&1\end{bmatrix}\begin{bmatrix}a_{11}&a_{12}&a_{13}\\a_{21}&a_{22}&a_{23}\\a_{31}&a_{32}&a_{33}\end{bmatrix}\begin{bmatrix}1\\&-1\\&&1\end{bmatrix}\quad\text{so}~\det M_1=(-1)(\det A)(-1).
$$


$M_2$是奇异矩阵，因为它的行相加得到零行。它的行列式为零。

根据第三条规则（逐行的线性性质），可以将$M_3$拆分为八个矩阵：
$$
\left|\begin{array}{c}\text{row}1+\text{row}3\\\text{row}2+\text{row}1\\\text{row}3+\text{row}3\end{array}\right|=\left|\begin{array}{c}\text{row}1\\\text{row}2\\\text{row}3\end{array}\right|+\left|\begin{array}{c}\text{row}3\\\text{row}2\\\text{row}3\end{array}\right|+\left|\begin{array}{c}\text{row}1\\\text{row}1\\\text{row}3\end{array}\right|+\cdots+\left|\begin{array}{c}\text{row}3\\\text{row}1\\\text{row}2\end{array}\right|
$$
除了第一个和最后一个矩阵外，其余矩阵都具有重复的行和零行列式。第一个矩阵是$A$，而最后一个矩阵进行了两次行交换。因此，$\det M_3 = \det A + \det A$。（可以尝试取$A=I$进行验证。）

**5.1 B**     解释如何通过行操作得到这个行列式：
$$
\det\left[\begin{array}{ccc}1-a&1&1\\1&1-a&1\\1&1&1-a\end{array}\right]=a^2(3-a)
$$
**解答**      从第一行和第二行中减去第三行。这将得到以下结果：
$$
\det\left[\begin{array}{ccc}-a&0&a\\0&-a&a\\1&1&1-a\end{array}\right]
$$
&emsp;&emsp;现在将第一列加到第三列，然后将第二列加到第三列。这将得到一个下三角矩阵，对角线上的元素为$-a$，$-a$和$3-a$：$\det = (-a)(-a)(3-a)$

&emsp;&emsp;如果$a=0$或$a=3$，则行列式为零。当$a=0$时，我们得到全为1的矩阵——显然是奇异的。当$a=3$时，每一行的元素相加结果为零——同样是奇异的。数字0和3是全为1的矩阵的特征值。这个例子具有启示意义且非常重要，它引导我们进入第6章。

#### 5.1.4练习5.1

**问题1-12是关于行列式规则的问题。**

1. 如果一个$4\times4$矩阵$\det A=\frac{1}{2}$，求$\det(2A)$、$\det(-A)$、$\det(A^2)$和$\det(A^{-1})$。

   > $\det(2A)= 2^4 \det A = 8$
   >
   > $ \det(−A) = (−1)^4 \det A = \frac{1} {2}$
   >
   > $\det(A^2 ) =\frac {1} {4}$ 
   >
   > $\det(A^{−1} )= 2$

   

   

2. 如果一个$3\times3$矩阵的行列式为$-1$，求$\det\left(\frac{1}{2}A\right)$、$\det(-A)$、$\det(A^2)$和$\det(A^{-1})$。

   > $\det( \frac{1} {2}A) = ( \frac {1} {2} ) ^3 \det A = −\frac {1} {8} $
   >
   >  $\det(−A) = (−1)^3 \det A = 1$
   >
   >  $det(A^2 ) = 1$
   >
   >  $\det(A^{−1} ) = −1.$

   

   

3. 真或假，如果为真则给出原因，如果为假则给出反例：

   > - $I + A$的行列式为$1 + \det A$。
   > - $ABC$的行列式为$|A| |B|  |C|$。
   > - $4A$的行列式为$4 |A|$。
   > - 矩阵$AB - BA$的行列式为零。试试取$A=\begin{bmatrix}0 & 0 \\ 0 & 1\end{bmatrix}$的例子。

   

   > - 错：$\det(I + I)$ is not $1 + 1$ ( $n = 1$除外)
   > - 对：乘积规则可以扩展到 $ABC$（使用它两次）
   > - 错：$\det(4A) = 4^ n \det A$
   > - 错：$A=\begin{bmatrix}0&0\\ 0&1\\ \end{bmatrix},B=\begin{bmatrix}0&1\\ 1&0\\ \end{bmatrix}$$AB-BA=\begin{bmatrix}0&-1\\ 1&0\\ \end{bmatrix}$可逆

   

   

4. 哪些行交换可以证明这些"反向单位矩阵" $J_3$ 和 $J_4$ 满足 $|J_3| = -1$ 但 $|J_4| = +1$？
   $$
   \det\begin{bmatrix}0&0&1\\0&1&0\\1&0&0\end{bmatrix}=-1\quad\text{but}\quad\det\begin{bmatrix}0&0&0&1\\0&0&1&0\\0&1&0&0\\1&0&0&0\end{bmatrix}=+1
   $$
   

   > 交换第1行和第3行得到 $|J_3| = -1$。交换第1行和第4行，然后交换第2行和第3行得到 $|J_4| = 1$。

   

   

5. 对于$n=5$、$6$、$7$，计算行交换次数以将反向单位矩阵$J_n$排列成单位矩阵$I_n$。为每个大小$n$提出一个规则，并预测$J_{101}$的行列式是$+1$还是$-1$。

   

   > 通过将第1行与第5行互换以及将第2行与第4行互换，可以得到 $|J_5| = 1$。$|J_6| = -1$，$|J_7| = -1$。行列式$1$、$1$、$-1$、$-1$以长度为4的周期重复出现，因此 $|J_{101}|=+1$ 。

   

   

6. 表明如何从规则3推导出规则6（如果一行全为零，则行列式为0）。

   

   > 为了证明规则6，将零行乘以 $t = 2$。行列式乘以2（规则3），但矩阵保持不变。因此 $2 \det(A) = \det(A)$，即 $\det(A) = 0$。

   

   

7. 求解旋转和反射矩阵的行列式：
   $$
   Q=\begin{bmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{bmatrix}\quad\text{and}\quad Q=\begin{bmatrix}1-2\cos^2\theta&-2\cos\theta\sin\theta\\-2\cos\theta\sin\theta&1-2\sin^2\theta\end{bmatrix}
   $$
   

   > 旋转的情况下，$\det(Q) = \cos^2\theta+\sin^2\theta = 1$
   >
   > 
   >
   > 反射的情况下，$\begin{align*}
   > \det(Q) &=1-2\sin^2\theta - 2\cos^2\theta +4\sin^2\theta \cos^2\theta-4\cos^2\theta \sin^2\theta\\&=1 - 2\sin^2\theta - 2\cos^2\theta \\& = -1
   > \end{align*}$

   

   

8. 证明每个正交矩阵（$Q^TQ = I$）的行列式为1或-1。

   > - 利用乘积规则$|AB| = |A||B|$和转置规则$|Q| = |Q^T|$。
   > - 只使用乘积规则。如果$|\det(Q)| > 1$，则$\det(Q^n) = (\det(Q))^n$会发散。那么我们如何知道这种情况不会发生在$Q^n$上呢？

   

   > $Q^TQ = I$ ⇒ $|Q^T| |Q| = |Q|^2 = 1$ ⇒ $|Q| = \pm1$；$Q^n$ 保持正交，因此其行列式在 $n \to \infty$ 时不会无限增大。

   

   

9. 这些矩阵的行列式是0、1、2还是3？
   $$
   A=\begin{bmatrix}0&0&1\\1&0&0\\0&1&0\end{bmatrix}\quad B=\begin{bmatrix}0&1&1\\1&0&1\\1&1&0\end{bmatrix}\quad C=\begin{bmatrix}1&1&1\\1&1&1\\1&1&1\end{bmatrix}.
   $$
   

   > 通过两次行交换得到 $\det A = 1$。通过将第1行和第2行从第3行减去，然后将第1列和第2列从第3列减去，得到 $\det B = 2$。尽管 $C = A + B$，但由于行相等，得到 $\det C = 0$。

   

   

10. 如果矩阵A的每行元素相加等于零，请解方程$Ax = 0$以证明$\det(A) = 0$。如果这些元素相加等于一，请展示$\det(A - I) = 0$。这是否意味着$\det(A) = 1$？

    

    > 如果每一行的元素相加等于零，则向量 $(1, 1, \ldots, 1)$ 属于零空间：奇异矩阵 $A$ 的行列式为零（列之和为零，因此它们线性相关）。如果每一行的元素相加等于$1$，则矩阵 $A - I$ 的行相加结果为零（不一定意味着 $\det A = 1$）。

    

    

11. 假设$CD = -DC$，并找出这种推理的错误之处：取行列式得到 $|C||D| = -|D||C|$。因此，$|C| = 0$或$|D| = 0$。其中一个或两个矩阵必须是奇异的。（这是不正确的。）

    

    > $CD = -DC$ ⇒ $\det CD = (-1)^n \det DC$，而不仅仅是 $- \det DC$。如果 $n$ 是偶数，则 $\det CD = \det DC$，我们可以得到可逆的 $CD$。

    

    

12. 一个$2\times 2$矩阵的逆矩阵似乎具有行列式等于1的特性：
    $$
    \det A^{-1}=\det\frac{1}{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}=\frac{ad-bc}{ad-bc}=1
    $$
    这个计算有什么问题？正确的 $\det A^-1$ 是多少？

    

    > $\det(A^{-1})$ 在每一行上都被 $ad - bc$ 除了两次（每一行一次）。这样可以得到 $\det A^{-1} = \frac{ad - bc}{(ad - bc)^2} = \frac{1}{ad - bc}$。

    

    

    **第13至27题使用规则计算特定行列式。**

    

    

13. 将矩阵$A$化为上三角矩阵$U$，并计算行列式$\det A$，它等于主元的乘积：
    $$
    A=\begin{bmatrix}1&1&1\\1&2&2\\1&2&3\end{bmatrix}\quad A=\begin{bmatrix}1&2&3\\2&2&3\\3&3&3\end{bmatrix}
    $$
    

    > 主元为 $1$、$1$、$1$ ，行列式为 $1$
    >
    > 主元为$ 1$、$-2$、$-3/2$ ，行列式为 $3$

    

    

14. 通过应用行操作将矩阵$A$转化为上三角矩阵$U$，计算其行列式。
    $$
    \det\begin{bmatrix}1&2&3&0\\2&6&6&1\\-1&0&0&3\\0&2&0&7\end{bmatrix}\quad\text{and}\quad\det\begin{bmatrix}2&-1&0&0\\-1&2&-1&0\\0&-1&2&-1\\0&0&-1&2\end{bmatrix}
    $$
    

    > $\det(A) = 36$
    >
    > 而$4\times 4$的二次差分矩阵的行列式为$5$。

    

    

15. 使用行操作简化并计算这些行列式：
    $$
    \det\begin{bmatrix}101&201&301\\102&202&302\\103&203&303\end{bmatrix}\quad\text{and}\quad\det\begin{bmatrix}1&t&t^2\\t&1&t\\t^2&t&1\end{bmatrix}
    $$
    

    > 第一个行列式为0
    >
    > 第二个行列式为 $1 - 2t^2 + t^4 = (1 - t^2)^2$。

    

    

16. 计算秩一矩阵和反对称矩阵的行列式：
    $$
    A=\begin{bmatrix}1\\2\\3\end{bmatrix}\begin{bmatrix}1&-4&5\end{bmatrix}\quad\text{and}\quad A=\begin{bmatrix}0&1&3\\-1&0&4\\-3&-4&0\end{bmatrix}
    $$
    

    > 奇异的秩一矩阵行列式为0。反对称矩阵 K 也具有 $\det K = 0$（参见 #17）：一个奇数阶的反对称矩阵 K，例如阶数为3。

    

    

17. 一个反对称矩阵满足$A^T = -A$。在第16题中用$a$、$b$、$c$代替$1$、$3$、$4$，表明$|A| = 0$。给出一个行列式为1的$4\times 4$的例子。

    

    > 任意一个3×3的反对称矩阵 K，有 $\det(K^T) = \det(-K) = (-1)^3\det(K)$。这等于 $-\det(K)$。但是，总是有 $\det(K^T) = \det(K)$。因此，对于$3×3$的矩阵，我们必须有 $\det(K) = 0$。

    

    

18. 使用行操作展示$3\times 3$的"Vandermonde行列式"为：
    $$
    \det\begin{bmatrix}1&a&a^2\\1&b&b^2\\1&c&c^2\end{bmatrix}=(b-a)(c-a)(c-b)
    $$
    

    >$\left|\begin{array}{ccc}1&a&a^2\\ 1&b&b^2\\ 1&c&c^2\end{array}\right|=\left|\begin{array}{ccc}1&a&a^2\\ 0&b-a&b^2-a^2\\ 0&c-a&c^2-a^2\\ \end{array}\right|=\left|\begin{array}{ccc}b-a&b^2-a^2\\ c-a&c^2-a^2\\ \end{array}\right|$（为了得到$2×2$的矩阵，通过列操作消去第1行中的$a$和$a^2$）——从第2列和第3列中减去$a$和$a^2$与第1列的乘积。从$2\times 2$矩阵中提取出$(b - a)$和$(c - a)$的公因子：
    >
    >$(b-a)(c-a)\left|\begin{array}{cc}1&b+a\\ 1&c+a\end{array}\right|=(b-a)(c-a)(c-b)$

    

    

19. 计算$ U$ 和 $U^{-1}$ 的行列式和 $U^2$ 的行列式：
    $$
    U=\begin{bmatrix}1&4&6\\0&2&5\\0&0&3\end{bmatrix}\quad\text{and}\quad U=\begin{bmatrix}a&b\\0&d\end{bmatrix}
    $$
    

    > 对于上三角矩阵，只需将对角线上的元素相乘：$\det(U) = 6$，$\det(U^{-1}) = \frac{1}{6}$，$\det(U^2) = 36$。对于2×2矩阵：$\det(U) = ad$，$\det(U^2) = a^2d^2$。如果 $ad \neq 0$，则 $\det(U^{-1}) = \frac{1}{ad}$。

    

    

20. 假设您同时执行两个行操作，从矩阵 $A$ 到矩阵 $B$，其中 $B$ 是通过应用两个行操作得到的。
    $$
    \begin{bmatrix}a&b\\c&d\end{bmatrix}\quad\text{to}\quad\begin{bmatrix}a-Lc&b-Ld\\c-la&d-lb\end{bmatrix}
    $$
    找到第二个行列式。它是否等于 $ad - be$？

    

    > $\det\begin{bmatrix}a-Lc&b-Ld\\\\c-\ell a&d-\ell b\end{bmatrix}$ 化简为 $(ad-bc)(1-L\ell)$。如果同时进行两次行操作，行列式会发生变化。

    

    

21. *行交换*：将矩阵A的第一行加到第二行，然后从第一行减去第二行。然后将第一行加到第二行，并将第一行乘以$-1$，得到矩阵$B$。哪些规则可以显示出：
    $$
    \det B=\left|\begin{array}{cc}c&d\\a&b\end{array}\right|\quad\text{equals}\quad-\det A=-\left|\begin{array}{cc}a&b\\c&d\end{array}\right|
    $$
    

    这些规则确实可以替代行列式定义中的规则2。

    

    > 我们可以使用问题中的三个消元步骤交换行，然后将第1行乘以-1。因此，规则5和规则3得出规则2。（由于规则4和规则3得出规则5，它们也得出规则2。）

    

    

22. 从 $ad - bc$ 出发，计算 $A$、$A^-1$ 和 $A - \lambda I$ 的行列式：
    $$
    A=\begin{bmatrix}2&1\\1&2\end{bmatrix}\quad\text{and}\quad A^{-1}=\dfrac{1}{3}\begin{bmatrix}2&-1\\-1&2\end{bmatrix}\quad\text{and}\quad A-\lambda I=\begin{bmatrix}2-\lambda&1\\1&2-\lambda\end{bmatrix}
    $$
    有哪两个数 $ \lambda$ 使得 $det(A - \lambda I) = 0$？对于每个数 $\lambda$，写出矩阵 $A- \lambda I$——这个矩阵不应该是可逆的。

    

    > $\det(A) = 3$
    >
    > $\det(A^{-1}) = \frac{1}{3}$
    >
    > $\det(A - \lambda I) = \lambda^2 - 4\lambda + 3$。当λ = 1和λ = 3时，$\det(A - \lambda I) = 0$。这些（奇异！）矩阵分别是：
    > $$
    > A-I=\left[\begin{array}{cc}1&1\\ 1&1\\ \end{array}\right]\quad\text{and}\quad A-3I=\left[\begin{array}{rr}-1&1\\ \\ 1&-1\\ \end{array}\right]
    > $$
    >
    > 
    >
    > 注意：你可以解释这就是为什么行列式先于特征值的原因。将$λ = 1$和$λ = 3$确定为矩阵A的特征值。

    

    

23. 从 $A=\left[\begin{array}{cc}4&1\\ 2&3\end{array}\right]$ 中计算 $A^2$、$A^{-1}$、$A - \lambda I$ 及其行列式。哪两个数 $\lambda$ 使得 $\det(A -\lambda I) = 0$？

    

    > $A = \begin{bmatrix}4 & 1 \\ 2 & 3\end{bmatrix}$ 的行列式为 $\det(A) = 10$
    >
    > $A^2 = \begin{bmatrix}18 & 7 \\ 14 & 11\end{bmatrix}$，$\det(A^2) = 100$
    >
    > $A^{-1} = \frac{1}{10}\begin{bmatrix}3 & -1 \\ -2 & 4\end{bmatrix}$，它的行列式为 $\det(A^{-1})=\frac{1}{10}$。
    >
    > 当 $λ = 2$ 或 $λ = 5$ 时，$\det(A - λI) = λ^2 - 7λ + 10 = 0$，这些是特征值。

    

    

24. 通过消元将矩阵 $A$ 变为上三角矩阵 $U$，则有 $A = LU$。
    $$
    A=\begin{bmatrix}3&&3&&4\\6&&8&&7\\-3&&5&&-9\end{bmatrix}=\begin{bmatrix}1&&0&&0\\2&&1&&0\\-1&&4&&1\end{bmatrix}\begin{bmatrix}3&&3&&4\\0&&2&&-1\\0&&0&&-1\end{bmatrix}=LU
    $$
    求解矩阵 $L$、$U$、$A$、$U^{-1} L^{-1}$ 以及 $U^{-1} L^{-1} A$ 的行列式。

    

    > 这里有 $A = LU$，其中 $\det(L) = 1$ 且 $\det(U) = -6$（为主元的乘积），因此 $\det(A) = -6$。$\det(U^{-1}L^{-1}) = -\frac{1}{6} = \frac{1}{\det(A)}$，而 $\det(U^{-1}L^{-1}A)$ 等于 $\det(I) = 1$。

    

    

25. 如果矩阵$A$的第$i$行第$j$列的元素为$i\times j$，证明$\det(A) = 0$（$A=\begin{bmatrix}1\end{bmatrix}$除外）。

    

    > 当矩阵 $A$ 的第 $i$ 行第 $j$ 列的元素为 $ij$ 时，由于第2行是第1行的两倍，因此 $\det(A) = 0$。

    

    

26. 如果矩阵$A$的第$i$行第$j$列的元素为$i+j$，证明$\det(A) = 0$（$n=1$或$2$除外）。

    

    > 当矩阵 $A$ 的第 $i$ 行第 $j$ 列的元素为 $i + j$ 时，由于第3行减去第2行等于第2行减去第1行，因此矩阵 $A$ 是奇异的，即 $\det(A) = 0$。

    

    

27. 通过行变换计算这些矩阵的行列式：
    $$
    A=\begin{bmatrix}0&a&0\\0&0&b\\c&0&0\end{bmatrix}\quad\text{and}\quad B=\begin{bmatrix}0&a&0&0\\ 0&0&b&0\\ 0&0&0&c\\ d&0&0&0\end{bmatrix}\quad\text{and}\quad C=\begin{bmatrix}a&a&a\\a&b&b\\a&b&c\end{bmatrix}
    $$

    > 通过消元操作计算得到的行列式为：
    >
    > $\det(A) = abc$，
    >
    > $\det(B) = -abcd$，
    >
    > $\det(C) = a(b - a)(c - b)$。

    

    

28. 真或假（如果是真的，请给出理由；如果是假的，请给出一个$2\times2$的例子）：

    

    > - 如果矩阵 $A$ 不可逆，那么矩阵 $AB$ 也不可逆。
    > - 矩阵 $A$ 的行列式始终等于其主元的乘积。
    > - 矩阵 $ A - B$ 的行列式等于 $\det A - \det B$。
    > - 矩阵 $AB$ 和 $BA$ 具有相同的行列式。

    

    > - 正确：$\det(AB) = \det(A) \det(B) = 0$ 
    > -  错误：行交换会导致行列式的负号，而不是主元的乘积。
    > - 错误：当 $A = 2I$ 且 $B = I$ 时，$A−B = I$，但行列式的结果是 $2^n - 1 \neq 1$。
    > - 正确：$\det(AB) = \det(A) \det(B) = \det(BA)$。

    

    

    

29. 这个关于投影矩阵行列式为 1 的证明有何问题？
    $$
    P=A(A^{\mathrm{T}}A)^{-1}A^{\mathrm{T}}\quad\mathrm{so}\quad|P|=|A|\frac{1}{|A^{\mathrm{T}}}\frac{1}{||A|}|A^{\mathrm{T}}|=1
    $$
    

    > 由于 A 是矩形矩阵，所以 $\det(A^TA) \neq (\det A^T)(\det A)$：这些行列式是未定义的。实际上，如果 A 是"高瘦"矩阵（$m > n$），那么 $\det(A^TA)$ 是由 A 的所有 $n × n$ 子矩阵 B 的行列式的平方之和。

    

    

30. （微积分问题）证明 $\ln(\det A)$ 的偏导数给出了 $A^{-1}$！
    $$
    f(a,b,c,d)=\ln(ad-bc)\quad\text{leads to}\quad\begin{bmatrix}\partial f/\partial a&\partial f/\partial c\\\partial f/\partial b&\partial f/\partial d\end{bmatrix}=A^{-1}
    $$
    
    
    
    > $f = \ln(ad - bc)$的导数是：
    > $$
    > \begin{bmatrix}\partial f/\partial a&\partial f/\partial c\\\partial f/\partial b&\partial f/\partial d\end{bmatrix}=\begin{bmatrix}\dfrac{d}{ad-bc}&\dfrac{-b}{ad-bc}\\\dfrac{-c}{ad-bc}&\dfrac{a}{ad-bc}\end{bmatrix}=\dfrac{1}{ad-bc}\begin{bmatrix}d&-b\\\\-c&a\end{bmatrix}=A^{-1}
    > $$
    > 
    
    
    
    
    
31. （MATLAB）希尔伯特矩阵 **hilb**($n$) 的第 $i$ 行第 $j$ 列元素等于 $1/(i + j - 1)$。打印出 **hilb**(1), **hilb**(2), ... ,**hilb**(10) 的行列式。希尔伯特矩阵很难处理！**hilb**(5) 的主元是什么？

    

    > 希尔伯特行列式分别为$1$，$8 \times 10^{-2}$，$4.6 \times 10^{-4}$，$1.6 \times 10^{-7}$，$3.7 \times 10^{-12}$，$5.4 \times 10^{-18}$，$4.8 \times 10^{-25}$，$2.7 \times 10^{-33}$，$9.7 \times 10^{-43}$，$2.2 \times 10^{-53}$。主元是行列式的比值，因此第10个主元接近$10^{-10}$。希尔伯特矩阵在数值上具有困难（病态条件）。请参见图7.1和第8.3节。

    

    

32. （MATLAB）对于 n = 50、100、200、400，**rand**(n) 和 **randn**(n) 的 typcial 行列式值是多少？（在 MATLAB 中，“Inf”代表什么意思？）

    

    > **rand**(n)生成的典型行列式值为$10^6$、$10^{25}$、$10^{79}$、$10^{218}$，对应于$n = 50$、$100$、$200$、$400$。**randn**(n)使用正态分布生成的行列式值为$10^{31}$、$10^{78}$、$10^{186}$、**$+\infty$**意味着大于等于$2^{1024}$。MATLAB允许的最大值为$1.999999999999999 \times 2^{1023} \approx 1.8 \times 10^{308}$，但再增加一个9就会得到$+\infty$！

    

    

33. （MATLAB）找出一个由 1 和 -1 组成的 $6 × 6$ 矩阵的最大行列式值。

    

    > 我现在了解到，对于由1和-1构成的矩阵，最大化行列式是**哈达玛德问题**（1893年）：可以参考Brenner在《美国数学月刊》第79卷（1972年）626-630的文章。Neil Sloane精彩的整数序列在线百科全书（**research.att.com/∼njas**）中包含了当问题转化为由0和1构成的矩阵时，针对小规模n的解法（以及更多参考资料）。这个序列A003432从$n = 0$开始，为1、1、1、2、3、5、9。然后，对于大小为n的矩阵，1和-1的最大行列式是$2^{n−1}$乘以大小为n−1的0和1矩阵的最大行列式（因此，在序列**A003433**中，当n = 6时，(32)(5) = **160**）。
    >
    > 为了将6行6列的1和-1问题减小为5行5列的0和1问题，将六行乘以±1以确保第一列中有+1。然后将第一行从第二行到第六行相减，得到一个5行5列的子矩阵S，其中元素为-2和0。然后将S除以-2。
    >
    > 这里是一个高级的MATLAB代码，用于找到行列式最大为48的1和-1矩阵：
    >
    > ```matlab
    > for n = 5: 
    > 
    > n = 5; p = (n − 1)ˆ2; A0 =ones(n); maxdet= 0;
    > for k = 0 : 2ˆp − 1 
    > Asub = rem(floor(k. ∗ 2.ˆ(−p + 1 : 0)), 2); A = A0; A(2 : n, 2 : n) = 1 − 2∗ reshape(Asub, n − 1, n − 1);
    > if abs(det(A)) > maxdet, maxdet = abs(det(A)); maxA = A; 
    > end 
    > end 
    > ```
    >
    >
    > 输出结果：$\max A = \begin{gathered}\begin{matrix}{1}&{1}&{1}&{1}&{1}\\{1}&{1}&{1}&{-1}&{-1}\\{1}&{1}&{-1}&{1}&{-1}\\{1}&{-1}&{1}&{1}&{-1}\\{1}&{-1}&{-1}&{-1}&{1}\\\end{matrix}\end{gathered}$       $\max\det = 48$

    

    

34. 如果你已知 $\det A = 6$，那么矩阵 $B$ 的行列式是多少？
    $$
    \text{From}\quad\det A=\left|\begin{matrix}\text{row}1\\\text{row}2\\\text{row}3\end{matrix}\right|=6\quad\text{find} \quad B=\left|\begin{matrix}\text{row}3+\text{row}2+\text{row}1\\\text{row}2+\text{row}1\\\text{row}1\end{matrix}\right|
    $$
    



> 通过行变换将矩阵B化简为$[row3；row2；row1]$。然后，$\det B = -6$（由于行的排列顺序为A的奇排列）。





### 5.2排列和余子式

> 1. $2\times 2$的情况下，行列式$ad - bc$中有$2!$个带有正负号的项**而对于$n\times n$的情况，$\det A$会添加$n!$个带有正负号的项。**
> 2. 对于n = 3的情况，$\det A$会添加$3!=6$个项。其中两个项是$+a_{12}a_{23}a_{31}$和$-a_{13}a_{22}a_{31}$。**每个项中的行1、2、3和列1、2、3分别出现一次**。
> 3. 那个负号是因为列的顺序3、2、1需要进行一次交换才能恢复为1、2、3。
> 4. 这六个项包括$+a_{11} a_{22}a_{33} -a_{11} a_{23}a_{32} = a_{11} (a_{22}a_{33} - a_{23}a_{32}) = a_{11} (\text{余子式} C_{11})$。
> 5. 总是有$\det A = a_{11}C_{11} + a_{12}C_{12} + \ldots + a_{1n}C_{1n}$。余子式是大小为$n - 1$的行列式。



&emsp;&emsp;计算机通过选主元来计算行列式。本节介绍了另外两种计算方法。一种是使用所有$n!$个排列的"大公式"。另一种是使用大小为$n - 1$的行列式的"余子式公式"。最好的例子是我最喜欢的4乘4矩阵：

$$
A=\begin{bmatrix}2&-1&0&0\\-1&2&-1&0\\0&-1&2&-1\\0&0&-1&2\end{bmatrix} \quad \text{的行列式为} \quad\det A = 5。
$$
我们可以用三种方法找到这个行列式的值：**选主元法**、**大公式法**和**余子式法**。

> 1. 选主元的乘积为$2 \cdot \frac{3}{2} \cdot \frac{4}{3} \cdot \frac{5}{4}$。化简后得到5。
>
> 2. 在方程（8）中的"大公式"有4! = 24个项。只有五个项是非零的：
>    $$
>    \det A = 16 - 4 - 4 - 4 + 1 = 5$
>    $$
>    这里的16来自于A的对角线上的$2 \cdot 2 \cdot 2 \cdot 2$。那么$-4$和$+1$是从哪里来的呢？当你找到这五个项时，就能理解方程（8）了。
>
> 3. 第一行中的数值2、-1、0、0分别与其他行中的余子式4、3、2、1相乘。这给出了$2 \cdot 4 - 1 \cdot 3 = 5$。这些余子式是3乘3的行列式。余子式使用了与第一行中的元素所在列和行不重复的行和列。==每个行列式中的每一项都会使用到每一行和每一列一次==。

#### 5.1.1主元公式（Pivot Formula）



当消元得到$A = LU$时，主元$d_1, \ldots, d_n$位于上三角矩阵U的对角线上。如果没有行交换，则**将这些主元相乘**即可得到行列式的值：
$$
\det A=(\det L)(\det U)=(1)(d_{1}d_{2}\cdots d_{n})
$$
这个计算行列式的公式在5.1节中出现过，还考虑了行交换的可能性。此时引入了一个置换矩阵$P$使得$PA = LU$。置换矩阵$P$的行列式为$-1$或$+1$。
$$
(\det P)(\det A)=(\det{L})(\det{U})\quad\mathrm{~gives~}\quad\det A=\pm(d_1d_2\cdots d_n)
$$


**例1**

进行一次行交换可以得到主元4、2、1以及那个重要的负号。
$$
A=\begin{bmatrix}0&0&1\\0&2&3\\4&5&6\end{bmatrix}\quad PA=\begin{bmatrix}4&5&6\\0&2&3\\0&0&1\end{bmatrix}\quad\det A=-(4)(2)(1)=-8
$$
行交换的次数是奇数（即一次交换），这意味着$\det P = -1$。

&emsp;&emsp;下一个例子没有行交换。这可能是我们将其分解为$LU$形式时的第一个矩阵（当它是$3\times 3$的时候）。值得注意的是，我们可以直接推广到$n\times n$的情况。主元给出了行列式的值。我们还将看到行列式如何给出主元。



**例2**

这个三对角矩阵A的第一个主元是$2$，$\frac{3}{2}$，$\frac{4}{3}$。接下来是$\frac{5}{4}$，$\frac{6}{5}$，最后是$\frac{n+1}{n}$。对这个$n\times n$的矩阵进行分解，可以揭示其行列式：
$$
\begin{bmatrix}2&-1\\-1&2&-1\\&-1&2&\cdot&\\&&\cdot&\cdot&-1\\&&&-1&2\end{bmatrix}=\begin{bmatrix}1\\-\frac{1}{2}&1\\&-\frac{2}{3}&1\\&&\cdot&\cdot\\&&&\frac{n-1}{n}&1\end{bmatrix}\begin{bmatrix}2&-1\\&\frac{3}{2}&-1\\&&\frac{4}{3}&-1\\&&&\cdot&\cdot\\&&&\frac{n+1}{n}&1\end{bmatrix}
$$
主元位于U矩阵（最后一个矩阵）的对角线上。当$2$、$\frac{3}{2}$、$\frac{4}{3}$和$\frac{5}{4}$相乘时，分数会相互抵消。$4\times 4$矩阵的行列式为$5$。$3\times 3$矩阵的行列式为$4$。因此n乘n矩阵的行列式为$n+1$。

























































### 5.3克莱默法则、逆矩阵和体积



## 6特征值和特征向量

### 6.1特征值的介绍

### 6.2对角化矩阵

### 6.3微分方程组

### 6.4对称矩阵

### 6.5正定矩阵

## 7奇异值分解（SVD）

### 7.1线性代数在图像处理中的应用

### 7.2奇异值分解中的基和矩阵

### 7.3主成分分析（通过奇异值分解实现的PCA）

### 7.4奇异值分解的几何性质

## 8线性变换

### 8.1线性变换的概念

### 8.2线性变换的矩阵

### 8.3寻找一个好的基的搜索







## 9复向量和复矩阵

### 9.1复数

### 9.2共轭转置矩阵和幺正矩阵

### 9.3快速傅里叶变换（FFT）



## 10应用领域

### 10.1图和网络

### 10.2工程中的矩阵

### 10.3马尔可夫矩阵、人口和经济

### 10.4线性规划

### 10.5傅里叶级数：函数的线性代数表示

### 10.6计算机图形学

### 10.7密码学中的线性代数

## 11数值线性代数

### 11.1高斯消元法的实践

### 11.2范数和条件数

### 11.3迭代方法和预处理器

## 12概率与统计中的线性代数

### 12.1均值、方差和概率

### 12.2协方差矩阵和联合概率

### 12.3多元高斯分布和加权最小二乘法
