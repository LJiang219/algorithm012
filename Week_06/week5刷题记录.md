# 415. 字符串相加 [每日一题] [求和进位]
1. https://leetcode-cn.com/problems/add-strings/
2. 题目:给定两个字符串形式的非负整数 num1 和num2, 计算它们的和;
+ 注意：
  - num1 和num2 的长度都小于 5100.
  - num1 和num2 都只包含数字 0-9.
  - num1 和num2 都不包含任何前导零。
  - [你不能使用任何 内建的 BigInteger 库]， 也不能直接将输入的字符串转换为整数形式。

4. 思路和代码:
  + 从num1, num2的尾部开始计算, 保存到tmp中
  + 计算当前位置的值: tmp%10得到的余数, 保存到result(string类型)
  + 计算进位, 更新tmp, 将进位添加到下一位数字的相加运算中
  + 索引溢出处理: 循环结束, 根据tmp判断是否有进位, 并在result头部添加进位1
  + 返回result

5. 代码:
```js
  var addStrings = function(num1, num2) {
    let a = num1.length, b = num2.lengt, result ='', tmp = 0;
    while(a || b) {
        // tmp += +num1[--a] + +num2[--b];
        //当前位的和 = 当前位的2个数字(number)的和 + 上一次的进位
        //考虑到 39+1 , 考虑为和为0的情况
        a ? tmp += +num1[--a] : 0;  
        b ? tmp += +num2[--b] : 0; 
        result = tmp % 10 + result;  //计算当前位的值
        if(tmp > 9) tmp = 1; 
        else tmp = 0;
      }
      if(tmp) result = 1 + result;
      return result;
  }
```


6. 刷题记录:

|  时间   | 次数  | 备注  | 
| :---- | :----: | :---- |
| 08.03  |   1  | 


# 207. 课程表
1. https://leetcode-cn.com/problems/course-schedule/
2. 题目;
你这个学期必须选修 numCourse 门课程，记为 0 到 numCourse-1 。
在选修某些课程之前需要一些先修课程。 
例如，想要学习课程 0 ，你需要先完成课程 1 ，我们用一个匹配来表示他们：[0,1]
给定课程总量以及它们的先决条件，请你判断是否可能完成所有课程的学习.
3. 示例:
```
输入: 2, [[1,0]] 
输出: true
解释: 总共有 2 门课程。学习课程 1 之前，你需要完成课程 0。所以这是可能的

```

# 100. 相同的树
1. https://leetcode-cn.com/problems/same-tree/
2. 