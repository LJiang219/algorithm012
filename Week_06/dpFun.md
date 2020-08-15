# 不同路径 系列 - 3

## 62. 不同路径 
+ m x n ; 向下或者向右移动一步,达到网格的右下角。问总共有多少条不同的路径
+ base: dp[i][j] = dp[i-1][j] + dp[i][j-1]
+ lower dimension:  cur[j] = cur[j-1] + cur[j]

## 63. 不同路径II
+ 障碍物: 1, 空位置: 0
+ (i, j)上没有obstacle: dp[i][j] = 0
+ (i, j)上有obstacle: dp[i, j] = dp[i - 1, j] + dp[i, j - 1]

# 路径系列 - 3

## 64. 最小路径和 [easy]
+ dp[i][j] 表示从左上角出发到 (i,j) 位置的最小路径和
+ i=0 && j=0:   dp[i][j] = grid[i][j];
+ i!=0 && j==0: dp[i][j] = dp[i-1][j] + grid[i][j];
+ i==0 && j!=0: dp[i][j] = dp[i][j-1] + grid[i][j];
+ i!=0 && j!=0: dp[i][j] = Min(dp[i-1][j], dp[i][j-1]) + grid[i][j]
+ return dp最后一个元素值


## 120. 三角形最小路径和 
+ 三角形，自顶向下的最小路径和,每一步只能移动到下一行中相邻的结点上。
+ 相邻结点：与(i, j) 点相邻的结点为 (i + 1, j) 和 (i + 1, j + 1)
+ dp[i][j] 表示从点 (i, j)(i,j) 到底边的最小路径和
+ 从三角形的最后一行开始递推。
+ 自下而上
+ dp[i][j] = min(dp[i+1][j], dp[i+1][j+1]) + triangle[i][j];
+ dp[j] = Math.min(dp[j], dp[j+1]) + triangle[i][j]

## 1143. 最长公共子序列
+ s1="abcde", s2= "ace"，求两个字符串的公共子序列，答案是“ace”
+ S[i] == T[j], dp[i][j] = dp[i-1][j-1] + 1
+ 否则 dp[i][j] = max(dp[i][j-1],dp[i-1][j])


## 53. 最大子序和
+ 题目:
```
输入: [-2,1,-3,4,-1,2,1,-5,4]
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```
+ code:
```
 sum += num;
 ans = Math.max(ans, sum);
``` 


## 152. 乘积最大子数组
+ 示例:
```
输入: [2,3,-2,4]
输出: 6
解释: 子数组 [2,3] 有最大乘积 6。
```
+ code:
```js
let max = nums[0], min = nums[0], res = nums[0];
for() {
  let tmp = min;
  min = Math.min(nums[i], Math.min(max * nums[i], min * nums[i])); 
  max = Math.max(nums[i], Math.max(max * nums[i], tmp * nums[i])); 
  res = Math.max(res, max);
}

```

# 零钱兑换 系列 - 2

## 322. 零钱兑换
+ dp[i] = Math.min(dp[i], dp[i-coin]+1)

## 518. 零钱兑换 II
+ 
# 打家劫舍 系列 -2

## 198. 打家劫舍 
+ 不能在两间相邻的房屋偷窃
+ code:
```js
  f(k) = 偷 [0..k) 房间中的最大金额
  f(0) = 0
  f(1) = nums[0]
  f(k) = max{ rob(k-1), nums[k-1] + rob(k-2) }
```
## 213. 打家劫舍I
+ 所有的房屋都<u>围成一圈</u>
+ 限制条件，就是头尾相邻，即不能同时偷nums[0]和nums[n-1]
+ code:
```js
  (n === 1) nums[0];
  Math.max(
      robbing(nums.slice(0, n - 1)),
      robbing(nums.slice(1, n))
    );
```
# 跳跃游戏 系列 - 2

## 55. 跳跃游戏
+ 题目: 判断你是否能够到达最后一个位置
+ 示例:
```
输入: [2,3,1,1,4]
输出: true
解释: 我们可以先跳 1 步，从位置 0 到达 位置 1, 然后再从位置 1 跳 3 步到达最后一个位置。

```
+ code:
```js
// nums[i] + i >= pos
// update pos=i
```

## 45. 跳跃游戏II
+ 使用最少的跳跃次数到达数组的最后一个位置
+ code:
```js
for(int i = 0; i < nums.length - 1; i++){
    maxPosition = Math.max(maxPosition, nums[i] + i); 
    //遇到边界，就更新边界，并且步数加一
    if( i == end){
      end = maxPosition;
      steps++;
    }
  }
```

# 距离-平方数 系列 - 2


## 279. 完全平方数
+ 正整数 n，找到若干个 完全平方数（比如 1, 4, 9, 16, ...）使得它们的和等于 n。
+ 组成和的完全平方数的个数最少。
+ dp[i] = MIN(dp[i], dp[i - j * j] + 1); i 表示当前数字，j*j表示平方数
+ code:
```js
for: 1 to n:
  for: 1 to i-j*j>=0
  dp[i] = i;
  dp[i] = MIN(dp[i], dp[i - j * j] + 1)
```

## 221. 最大正方形
+ dp: dp[i][j] = Min(dp[i - 1][j - 1], dp[i - 1][j], dp[i][j - 1]) + 1;

#  312. 戳气球 [hard]
```js
let points = [1, ...nums, 1];
let dp = Array.from(Array(n + 2), () => Array(n + 2).fill(0));

for: i n to 0 (从最后一行, 下向上)
  for: j=i+1 to n+2
    for: k = i+1  to j 在(i, j) 之间选择的k

     dp[i][j] = Math.max(
          dp[i][j],
          points[j] * points[k] * points[i] + dp[i][k] + dp[k][j]
        );

  return dp[0][n + 1];
```