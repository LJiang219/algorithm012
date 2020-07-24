学习笔记

week3 主要内容: 递归 + 回溯(backtrack)

# 递归模板
1. 模板
  + recursiont terminator 递归终结条件 (递归终结者)
  + process logic in current level 处理当前层逻辑
  + drill down 下探到下一层
  + reverse the current level status if needed  *清理当前层(比如全局变量等)


JavaScript
```js
 // JavaScript
const recursion = (level, params) =>{
   // recursion terminator
   if(level > MAX_LEVEL){
     process_result
     return 
   }
   // process current level
   process(level, params)
   //drill down
   recursion(level+1, params)
   //clean current level status if needed
   
}
```

2. 思维:
+ 不要人肉递归 (最大误区)
+ 找到最近最简方法, 将其拆解成可重复解决的问题( 重复子问题)
+ 数学归纳法思维

# 回溯: 
+ 模板(参考做过的练习):

```js
  var xxx = function(nums) {
    let res = []; //一个放置结果的数组
    let path = []; //某条路径(结果), res = [path, path,...]

    //递归(其中的参数根据具体题目)
    function _helper(start,path) {
      //结束递归条件, 在回溯的题目中经常在这里 把符合条件的path 放入 res中
      if(条件 path.length == nums.length) {
        res.push(path);
        return;
      }

      //for循环中的递归, 具体还是要看题目, 有的需要去重
      for(let i = start; i < nums.length; i++) {
        //1.push
        path.push(nums[i]);

        //2.递归(下一层)
        _helper(i+1, [...path]);
        // _helper(i+1, path.slice());

        //3.pop
        path.pop();
      } 
    }


    _helper(0, path); //运行辅助函数(递归)

    return res;
  }

```
