学习笔记

## 常见DP题目和状态方程

1. 爬楼梯
f(n) = f(n-1) + f(n-2)
f(1) = 1, f(0)=0

2. 不同路径, 无障碍
f(x, y)= f(x-1, y) + f(x, y-1)

63.不同路径II, 有障碍
https://leetcode-cn.com/problems/unique-paths-ii/

参考:
+ https://leetcode-cn.com/problems/unique-paths-ii/solution/jian-dan-dpbi-xu-miao-dong-by-sweetiee/
+ https://leetcode-cn.com/problems/unique-paths-ii/solution/shou-hua-tu-jie-dp-si-lu-by-hyj8/

状态定义: dp[i][j] 表示走到格子(i,j)的方法数

状态转移: 

(i, j) 上有obstacle: dp[i][j] = 0;
(i, j) 上无obstacle: dp[i][j] = dp[i-1, j] + dp[i, j-1]

初始条件:
第1列只有从上边格子走过去这一种走法, i in (0, m)  dp[i][0]=1; 如果 存在obstacle,则为0
第1行只有从左边格子走过去这一种走法, j in (0, n)  dp[0][j]=1; 如果 存在obstacle,则为0


3. 大家劫舍
f(0) = 0
f(1) = nums[0]
f(k) = max{ rob(k-1), nums[k-1] + rob(k-2) }

4. 最小路径和
dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + A[i][j]


5. 股票买卖
参考: https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/solution/yi-ge-fang-fa-tuan-mie-6-dao-gu-piao-wen-ti-by-l-3/

初始状态:
dp[-1][k][0] = dp[i][0][0] = 0 dp[-1][k][1] = dp[i][0][1] = -infinity

状态转移方程:
dp[i][k][0] = max(dp[i-1][k][0], dp[i-1][k][1] + prices[i]) dp[i][k][1] = max(dp[i-1][k][1], dp[i-1][k-1][0] - prices[i])


