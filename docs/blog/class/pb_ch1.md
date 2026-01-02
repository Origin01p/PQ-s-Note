---
title: 第1章 随机事件与概率
---
## 1.意义

- 研究对象：随机现象
- 概率论研究：随机现象的模型（概率分布）
- 数理统计研究：随机现象的数据收集，处理，统计推断

## 2.术语

- **样本空间**：一切可能的结果的集合，记为 $\Omega$ 或 $S$。其中元素 $\omega$ 称作样本点。分为离散（有限或可列个）及连续（不可列无限）。
- **随机事件** :  样本空间中某些样本点组成的子集，简称事件。包含：基本事件（单元素集），必然事件（最大子集/本身），不可能事件（空集 $\varnothing$）。
- **随机变量** ：表示随机现象结果的变量，常用大写字母 $X, Y, Z, \ldots$ 表示。

## 3.关系及运算

**事件间的关系：**

 - 包含（$A \subset B$）
 - 相等（$A = B$）
 - 互不相容（$A \cap B = \varnothing$）
  
 **运算：**

- 并（和）：$A\bigcup B$
- 差：$A-B$ 或 $A \backslash B$
- 对立（补）：$\bar{A}$ 或 $A^c$
  
**运算规则：**

- 交换律：$A \cup B = B \cup A,\quad A \cap B = B \cap A$
- 结合律：$(A \cup B) \cup C = A \cup (B \cup C),\quad (A \cap B) \cap C = A \cap (B \cap C)$
- 分配律：$A \cap (B \cup C) = (A \cap B) \cup (A \cap C),\quad A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
- 对偶律（德摩根公式）：$\overline{A \cup B} = \bar{A} \cap \bar{B},\quad \overline{A \cap B} = \bar{A} \cup \bar{B}$

## 4.引申

**事件域**（Event Field / σ-algebra）：$\Omega$ 的子集类 $\mathcal{F}$，满足：

>  1. $\Omega \in \mathcal{F}$；
   2. 若 $A \in \mathcal{F}$，则 $\bar{A} \in \mathcal{F}$；
   3. 若 $A_n \in \mathcal{F} (n=1,2,\ldots)$，则 $\bigcup_{n=1}^{\infty} A_n \in \mathcal{F}$。

- $\mathcal{F}$ 是由基本子集经过可列次并、交、补运算生成的集合类。
- 常见的：Borel域（Borel σ-algebra），由实数集 $\mathbb{R}$ 上所有开区间生成的σ代数，记为 $\mathcal{B}(\mathbb{R})$。

**分割（Partition）**：若事件 $A_1, A_2, \ldots, A_n$ 互不相容（即 $A_i \cap A_j = \varnothing, i \neq j$），且 $\bigcup_{i=1}^{n} A_i = \Omega$，则它们构成 $\Omega$ 的一个分割。

## 5.概率的发展脉络

**发展脉络：**

- 历史时期：古典定义，几何定义，频率定义，主观定义。
- 现代基础：**公理化定义**（Kolmogorov，苏联）

**公理化定义（Kolmogorov）：**

设 $\Omega$ 为样本空间，$\mathcal{F}$ 为事件域，若定义在 $\mathcal{F}$ 上的集合函数 $P: \mathcal{F} \to \mathbb{R}$ 满足：

（1）非负性：$\forall A \in \mathcal{F},\ P(A) \ge 0$；

（2）正则性：$P(\Omega) = 1$；

（3）可列可加性：若 $A_1, A_2, \ldots$ 两两互斥（$A_i \cap A_j = \varnothing, i \neq j$），则 $P\left( \bigcup_{i=1}^{\infty} A_i \right) = \sum_{i=1}^{\infty} P(A_i)$。

则称 $P$ 为概率测度，$P(A)$ 为事件 $A$ 的概率。

**性质（由公理可推导）：**

- 有限可加性：若 $A_1, \ldots, A_n$ 两两互斥，则 $P\left( \bigcup_{i=1}^{n} A_i \right) = \sum_{i=1}^{n} P(A_i)$。
- 单调性：若 $A \subset B$，则 $P(A) \le P(B)$。
- 加法公式：$P(A \cup B) = P(A) + P(B) - P(A \cap B)$。对于多个事件有容斥原理。
- 连续性：若事件序列 $\{A_n\}$ 单调（如 $A_n \uparrow A$ 或 $A_n \downarrow A$），则 $\lim_{n \to \infty} P(A_n) = P(\lim_{n \to \infty} A_n)$。

（注：在大多数教科书中频率对于可列可加性的介绍过于模糊。）

## 6.确定概率的方法

**频率方法确定概率：**

- 大量重复实验统计频率：$P(A) \approx \frac{n_A}{n}$，其中 $n$ 为总试验次数，$n_A$ 为 $A$ 发生的次数。

**古典方法确定概率：**

- 在有限样本的随机现象中，每个样本等可能（$\Omega$ 中样本点有限且等概）。
- 概率计算公式：$P(A) = \frac{|A|}{|\Omega|} = \frac{A\text{包含的样本点数}}{\text{样本点总数}}$。
- 应用模型：抽样模型（如彩票问题）、盒子模型（如生日问题，统计物理中的模型）。

**几何方法确定概率：**

- 适用于样本空间 $\Omega$ 为可度量的几何区域，且样本点落入子区域 $A$ 的可能性与 $A$ 的测度（长度、面积、体积）成正比，而与形状位置无关。
- 概率计算公式：$P(A) = \frac{\mu(A)}{\mu(\Omega)}$，其中 $\mu(\cdot)$ 表示几何测度。
- 经典问题：会面问题、蒲丰投针问题（蒙特卡罗方法的雏形）。

**主观方法确定概率：**

- 贝叶斯学派观点：概率是主体根据已有经验对事件发生的可能性做出的个人信念度量的判断。
- 应用场景：气象预报，经验总体预估。

（**注**：关于贝叶斯学派和频率学派的有关文章可见）

## 7.条件概率

**定义：**
在事件 $B$ 发生（$P(B)>0$）的条件下，事件 $A$ 发生的概率，记为 $P(A|B)$。其定义为：
$$
P(A|B) = \frac{P(A \cap B)}{P(B)}
$$

**实用公式：**

- 乘法公式：$P(A \cap B) = P(B)P(A|B) = P(A)P(B|A)$。可推广至多个事件。
- 全概率公式：若 $B_1, B_2, \ldots, B_n$ 是 $\Omega$ 的一个分割，且 $P(B_i)>0$，则对任意事件 $A$ 有：
$$P(A) = \sum_{i=1}^{n} P(B_i)P(A|B_i)$$
- 贝叶斯公式（逆概率公式）：在全概率公式的条件下，有： 

$$
P(B_j|A) = \frac{P(B_j)P(A|B_j)}{\sum_{i=1}^{n} P(B_i)P(A|B_i)},\quad j=1,2,\ldots,n
$$

## 8.独立性问题

- 两个事件 $A$ 与 $B$ 独立定义为：$P(A \cap B) = P(A)P(B)$。当 $P(B)>0$ 时，等价于 $P(A|B)=P(A)$。
- 多个事件的相互独立与两两独立。

（待续）