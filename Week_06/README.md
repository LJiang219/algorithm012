学习笔记

## 动态规划: Dynamic programming
1. 定义:
+ "Simplifying a complicated problem by breaking it down into a simpler subproblems"(in a recursive manner);
+ Divide & Conquer + Optimal substructure (分治+ 最优子结构)

2. key:
+ [动态规划] 和 [递归] 或者 [分治] 根本上的区别 (关键是看有无最优子结构)
+ 共性: 找到重复子问题
+ 差异性: 最优子结构, 中途可以淘汰次优解

3. 动态规划的关键点
+ 最优子结构: opt[n]= best_of(opt[n-1], opt[n-2], ...)
+ 储存中间状态: opt[i]
+ 递推公式( 状态转移方程 或者 DP方程)
  - Fib: opt[i] = opt[i-1] + opt[n-2];
  - 二维路径: opt[i,j] = opt[i+1][j] + opt[i][j+1] (且判断a[i,j]是否空地)

### dp 太难, 原则是 先把easy, medim, hardButInterested 练会


