# 移动0
1. 链接: https://leetcode-cn.com/problems/move-zeroes/

2. 题目: 
给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。
示例:输入: [0,1,0,3,12]; 输出: [1,3,12,0,0]
说明:
+ 必须在原数组上操作，不能拷贝额外的数组。
+ 尽量减少操作次数。

3. 代码片段
```js
function moveZero(nums){
  var j = 0; //记录非0
  for(var i = 0; i < nums.length; i++){
    if(nums[i] != 0) {
      nums[j] = nums[i];
      if( i != j) {
        nums[i] = 0;
      }
      j++;
    }
  }
}
```

4. 刷题记录

|  时间   | 次数  | 
|  :----  | :----:  |
| 07.07  |   2   |
| 07.08  |   1   | 
| 07.09  |   1   | 


# 盛最多水的容器
1. 链接: https://leetcode-cn.com/problems/container-with-most-water/

2. 题目:
(1) 给你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

(2) 说明：你不能倾斜容器，且 n 的值至少为 2。
![avatar](/images/2.jpg)
图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。

(3) 示例：
输入：[1,8,6,2,5,4,8,3,7]
输出：49

3. 代码片段
(1) 片段1: 双循环, 这2个for一定记住
```js
 function getMaxArea(height){
   var max = 0;
   for(var i = 0; i < height.length - 1; i++){
     for(var j = i + 1; j < height.length; j++ ){
       var area = (j - i) * Math.min(height[i], height[j]);
       max = Math.max(max, area);
     }
   }
   return max;
 }
 
```
(2) 片段2: 从外向内移动低矮的柱子
```js
function getMaxArea(height){
  var max = 0; 
  for(var i = 0, j = height.length-1; i < j; ){
    var minHeight = height[i] < height[j] ? height[i++]: height[j++]; 
    var area = (j - i + 1) * minHeight; 
    max = Math.max(max, area)
  }
  return max;
}
```
4. 刷题记录
|  时间   | 次数  | 
|  :----  | :----:  |
| 07.07  |   2   |
| 07.08  |   1   | 
| 07.09  |   1   | 

# 爬楼梯
1. 链接: https://leetcode.com/problems/climbing-stairs/

2. 题目:
(1) 假设你正在爬楼梯。需要 n 阶你才能到达楼顶。
每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？
注意：给定 n 是一个正整数。

(2) 示例 1：
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶

(3) 示例 2：
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶

3. 代码片段
数学归纳法, 找最近重复子问题
第一级台阶: 跨一阶台阶 --- 1:1
第二级台阶: 1阶+1阶 或者 2阶 ---2:2种方法
第三级台阶: 从第二级台阶上面跨一阶上来 或者 从第一级台阶上面跨二阶台阶上来
3: f(1) + f(2) , 因为最后一步不同, 所以不会有重复 --- 3: 3种方法
4: f(2) + f(3)
n: f(n-1) + f(n-2)  最后一步跨1个台阶的走法 + 最后一步跨2个台阶的走法
抽象为 求 斐波拉契数列
(1) 片段1: 
```js
//傻傻的fibory
var climbStairs = function(n) {

}
```

(2) 片段2:

```js
var climbStairs = function(n){
  if(n <= 2 ){
    return n;
  }
  var f1=1, f2=2, f3=3;
  for(var i = 3; i < n+1; i++){
    f3 = f1 + f2;
    f1 = f2;
    f2 = f3;
  }
  return f3;
}
```

4. 刷题记录

|  时间   | 次数  | 
|  :----  | :----:  |
| 07.07  |   2   |
| 07.08  |   1   | 
| 07.09  |   1   | 

# [每日一练] 路径总和
1. 链接: https://leetcode-cn.com/problems/path-sum/
2. 题目:
(1) 给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。
说明: 叶子节点是指没有子节点的节点。
(2) 示例:
给定如下二叉树，以及目标和 sum = 22示例:
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1

返回 true, 因为存在目标和为 22 的根节点到叶子节点的路径 5->4->11->2

(3) 知识点补充
二叉树: 其节点最多只能有2个子节点, 一个是左侧子节点, 另一个是右侧子节点

3. 代码片段
```js
```
4. 刷题记录

|  时间   | 次数  | 
|  :----  | :----:  |
| 07.07  |   1  |
| 07.09  |   1   | 

# 两数之和
1. https://leetcode-cn.com/problems/two-sum/
2. 题目
(1) 
(2) 示例
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

3. 代码片段
(1) 暴力法: 2层循环 时间复杂度: O(n^2)
```jsx
  var twoSum = function(nums, target){
    var res = new Array(2);
    for(var i = 0; i < nums.length - 1; i++) {
      for(var j = i+1; j < nums.length; j++) {
          if(nums[i] + nums[j] == target){
            res[0] = i;
            res[1] = j;
            return res;
          }
      }
    }
    return new Array(0)
  }
```
(2) map

4. 刷题记录

|  时间   | 次数  | 备注|
|  :----  | :----: | :----|
| 07.08  |   1  | 暴力法|
| 07.09  |   1  | 暴力法|
| 07.09  |   1  | Map法|

# 三数之和
1. https://leetcode-cn.com/problems/3sum/
2. 题目:
(1) 给你一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有满足条件且不重复的三元组。
注意：答案中不可以包含重复的三元组。

(2) 示例：
```js
  // 给定数组 nums = [-1, 0, 1, 2, -1, -4]，
  // 满足要求的三元组集合为：
  [
    [-1, 0, 1],
    [-1, -1, 2]
  ]
```

3. 代码片段
(1) 代码1: 暴力: 三层for循环 + 去重(去重是个麻烦事>>>)
```js
  var threeSum = (nums) {
    var res = [];
    for(var i = 0; i < nums.length; i++) {

    }
    return res;
  }
```

(2) 代码2: (非常精妙的方法) 排序+双指针
思路: 
+ 数组排序. 
+ 遍历排序后的数组. 
将遍历的每个nums[i]作为固定值, 使用左右指针指向nums[i]后面的两端, 为nums[L]和nums[R]
L = i+1; R = length-1; 
计算三个数的和sum,判断是否为0, 满足则添加进结果集
+ 如果 nums[i] > 0, 则三数之后无法等于0, 结束循环
+ 如果 nums[i] == nums[i-1], 数字重复, 会导致结果重复, 所以跳过
+ 当 sum===0, nums[L]==nums[L+1], 结果重复, 跳过, L++
+ 当 sum===0, nums[R]==nums[R-1], 结果重复, 跳过, R--

```jsx
//参考threeSum.html
var threeSum = function (nums) {
  if(nums == null || len < 3) return res;

  nums.sort((a, b) => a-b);

  for(var i = 0; i < len; i++){

  }


}

```
4. 刷题记录

|  时间   | 次数  | 备注|
|  :----  | :----: | :----|
| 07.08  |   1  | 暴力法|
| 07.09  |   2  | 双指针|

# [每日一练]-跳水板
1. 链接: https://leetcode-cn.com/problems/diving-board-lcci/
2.题目
(1) 你正在使用一堆木板建造跳水板。有两种类型的木板，其中长度较短的木板长度为shorter，长度较长的木板长度为longer。你必须正好使用k块木板。编写一个方法，生成跳水板所有可能的长度。
返回的长度需要从小到大排列。
(2) 示例
输入：
shorter = 1
longer = 2
k = 3
输出： {3,4,5,6}


3. 代码片段
思路:
(1) 考虑边界: 
+ 没有板子, k=0
+ shorter = longer 
(2) 总共k块板子, 有i块shorter, 那么就有(k-i)块longer
 

```js
var divingBoard = function(shorter, longer, k) {
  if(k == 0) {
    return [];
  }
  if(shorter === longer ){
    return [k * shorter]
  }
  const res = [];
  for(let i=0; i<= k; i++){
    res.push(shorter * k + (longer- shorter) * i)
  }
  return res;
}
```

4. 刷题记录

|  时间   | 次数  | 
|  :----  | :----:  |
| 07.08  |   1  |
| 07.09  |   1  |

# 反转链表
1. https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/

2. 解题思路：
要将链表 1 -> 2 -> 3 -> 4 -> Null 反转为 4 -> 3 -> 2 -> 1 -> Null ，需要一个 cur 指针表示当前遍历到的节点；一个 pre 指针表示当前节点的前驱节点；在循环中还需要一个中间变量 temp 来保存当前节点的后驱节点。

3. 算法流程：
(1) 首先 pre 指针指向 Null，cur 指针指向 head；
(2) 当 cur != Null，执行循环。
  + 先将 cur.next 保存在 temp 中防止链表丢失：temp = cur.next
  + 接着把 cur.next 指向前驱节点 pre：cur.next = pre
  + 然后将 pre 往后移一位也就是移到当前 cur 的位置：pre = cur
  + 最后把 cur 也往后移一位也就是 temp 的位置：cur = temp
  + 当 cur == Null，结束循环，返回 pre。

4. 图解流程：
![avatar](/images/reverseList.png)

3. 代码片段
自己画图, 理解. 2个滑动的指针, 一个临时指针
将该指针指向哪里, 就是x.next = 哪里
面包写法: 初始化变量, while循环, 返回变量
```js
  var reverseList = function(head) {
    var pre = null, cur = head, temp;
    while(cur != null) {
      //直到pre走到原链表的末尾(反转链表的头), cur移动到了null,就完成链表的翻转
      //1.暂存指向下一位的指针,方便cur可以找到
      temp = cur.next;
      //2. 局部小反转, 指向下一位的指针 反向指向前面(pre)
      cur.next = pre;
      //3. pre移动到cur
      pre = cur;
      //4. cur移动到下一位(就是开始暂存的指针)
      cur = temp;
    }
    return pre; //返回指向新链表的头的指针, 这个链表已经实现反转
  }
```
4. 刷题记录

|  时间   | 次数  | 
|  :----  | :----:  |
| 07.09  |   1  |
| 07.10  |   1  | 

# 两两交换链表中的节点
1. https://leetcode-cn.com/problems/swap-nodes-in-pairs/
2. 题目
给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。
你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。
示例:
给定 1->2->3->4, 你应该返回 2->1->4->3.

3. 思路: 
(1) 迭代法: 
在链表的最前面添加一个哨兵(是个节点, 有next指针), 将每个节点想象为一个哨所
每相邻的2个哨所相互交换, 交换一次, 哨兵就会移动到这2点的前一位(比如0, 1),
 直到 哨兵next指向null, 结束循环
就返回哨兵中next指针指向的链表

4. 代码思路
迭代法
(1) 准备工作: 创建2个哨兵, 
一个哨兵负责指向链表(交换之前和交换之后的链表都是又他指向)
另一个哨兵是移动的, 交换一次后, 哨兵移动一个
+ 新建一个哨兵节点 shaob: val=0, next=head
+ 从这个shaob复制一个可以移动的哨兵节点 shao
(2) 初始化 start, end
(3) 改变指针指向
0 -> 2
1 -> 3
2 -> 1
(4) 更新 节点shao (val, next)

5. 刷题记录 ( 有点难,花了1天才理解)
|  时间   | 次数  | 
|  :----  | :----:  |
| 07.10  |   1  | 

# 环形链表
1. https://leetcode-cn.com/problems/linked-list-cycle/submissions/
2. 寻找相遇点的位置(在链表中的Index)
3. 思路: 

联想: 乌龟和兔子 


5. 刷题记录
|  时间   | 次数  | 
|  :----  | :----:  |
| 07.10  |   1  | 

# 环形链表II
1. https://leetcode-cn.com/problems/linked-list-cycle-ii/
2. 思路
龟兔赛跑
(1) 找到[相遇点], 2倍速快跑和1倍速慢跑, 直到相遇(相遇点) [fast == slow]
(2) 2只速度相同的乌龟, 分别从[起始点]->[入环点], 从[相遇点]-> [入环点]
虽然不知道具体的距离是多少, 但是当他们相遇的时候, 就是 [入环点]


![avatar](/images/detectCycle.png);
5. 刷题记录 
|  时间   | 次数  | 
|  :----  | :----:  |
| 07.10  |   1  | 

# 有效的括号
1. https://leetcode-cn.com/problems/valid-parentheses/
2. 思路: 入栈
(1) len%2 !=0, return false, 一定是偶数个符合
(2) 遇到左括号, 一律入栈
(3) 遇到右括号, 将栈顶元素拿出,与右括号做比较
如果不匹配则返回false(说明不是有效的括号)
如果匹配, 则继续循环

3. 代码片段:
4. 刷题记录 
|  时间   | 次数  | 
|  :----  | :----:  |
| 07.10  |   1  | 

# 柱状图中最大的矩形(栈的想法不太容易)
1. https://leetcode-cn.com/problems/largest-rectangle-in-histogram/
2. 思路: 
(1) 暴力法: 意思遍历柱形高度, 对于每一个高度分别向两边扩散, 
求出求出以当前高度为矩形的最大宽度多少。
![avatar](/images/rectArea.png)
+ 遍历每个柱子, 当前柱子 heights[i] 的高度不变,获取当前高度下, 最大宽度
+ 以当前的柱子向左找, 找到高度比其小的, 继续向左找, 直到找到高度比当前大的 
+ 以当前的柱子向右找, 找到高度比其小的, 继续向右找, 直到找到高度比当前大的 
+ 高度*最大宽度
(2) 分治法: 略懂
(3) 单调栈: 完全没有懂
4. 刷题记录 
|  时间   | 次数  | 备注|
|  :----  | :----:  |
| 07.10  |   1  | 定高,找最大宽, 暴力|

# 旋转数组
1. https://leetcode-cn.com/problems/rotate-array/
2. 思路:
3. 代码片段
(1) 暴力法
(2) %运算(巧妙)
(3) 环状替换(实在是很难想到), 觉得自己很傻[越学越傻]
![avatar](/images/rotate.png)

4. 刷题记录
|  时间   | 次数  | 备注|
|  :----  | :----:  |
| 07.10  |   1  | 暴力法|
| 07.10  |   1  | %运算 |

# 加1
1. https://leetcode-cn.com/problems/plus-one/

2. 刷题记录

|  时间   | 次数  | 
|  :----  | :----:  |
| 07.10  |   1  | 



