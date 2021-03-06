## 第11节 动态规划与编辑距离

这一节主要学习了：动态规划与编辑距离

### 1. 机器学习的局限

如果某个问题存在但不限于以下问题：

1. 缺少数据
2. 缺少标注数据
3. 包含多层推断和决策过程

那么机器学习较难解决。

> 例如：
>
> 背包问题 Knapsack problem、旅行商问题 Travel salesman problem、自动纠错问题 Auto correction

### 2. 动态规划

求解切木头问题：

| 长度 | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 价值 | 1    | 5    | 8    | 9    | 10   | 17   | 17   | 20   | 24   | 30   | 33   |

方法1、普通递归

Best_price(N) = max(P_N, Best_price(N-1) + Best_price(1), Best_price(N-2) + Best_price(2), ..., Best_price(1) + Best_price(N))

方法2、带缓存器的递归

要获取最佳价格的时候，先去缓存中查看有没有，有就直接拿，没有才重新计算。

**这种在计算时不断把中间过程写入缓存，并且不断从缓存中读取的编程方式，即称为动态编程/动态规划**

### 3. 编辑距离

#### 3.1 编辑距离的思想

两个字符串通过Insertion, Deletion, Substitution的编辑操作，得到的操作步骤最短的步骤数

#### 3.2 编辑距离的算法（动态规划）

> **定义：**
>
> ​	对于2个分别巨有长度m，n的字符串X，Y，
>
> ​	我们定义距离D(i, j)为字串X[0:i], Y[0:j]的编辑距离，
>
> ​	那么X和Y之间的编辑距离就是D(M, N)
>
> **初始化：**
>
> ​	D(i, 0) = i
>
> ​	D(0, j) = j
>
> **子问题：**
>
> ​	![](http://latex.codecogs.com/gif.latex?D(i,j)=\min\begin{cases}D(i-1,j)+1\\D(i,j-1)+1\\D(i-1,j-1)+2\quad{if\;{X(i)\;{!=Y(i)}}}\;{else}\;{D(i-1,j-1)}\end{cases})


