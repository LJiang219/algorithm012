学习笔记

# 深度优先搜索(DFS)

# 广度优先搜索(BFS)

# DFS 代码模板
1. 递归写法:

```js
  const visited  = new Set();
  const dfs = node => {
    if(visited.has(node)) return ;

    visited.add(node);
    dfs(node.left);
    dfs(node.right); 
  }

```

2. 非递归写法:

```js

```

# BFS代码模板

```js
const bfs = (root) => {
  let result = [], queue = [root];
  
  while(queue.length > 0) {
    let level = [], n = queue.length;
    for(let i = 0; i < n; i++){
      let node = queue.pop();
      level.push(node.val);
      if(node.left) queue.unshift(node.left);
      if(node.right) queue.unshift(node.right);
    }
    result.push(level)
  }
  return result;
}
```



# 二分查找
模板:
```js
let left = 0, right = len(array) -1;
while(left <= right) {
  let mid = (left + right) >> 1;
  if(arry[mid] === target) {
    return;
  }else if(array[mid] < target) {
    left = mid + 1;
  }else {
    right = mid - 1;
  }
}
```

# 课后作业
1. 题目:使用二分查找，寻找一个半有序数组 [4, 5, 6, 7, 0, 1, 2] 中间无序的地方
(其实就是找到最小值);

2. 思路: 
这是一个有有序数组, 经过旋转而成的半有序数组. 说明, 被分开的两边也一定是有序的(在这里是升序). 在某处会出现一个拐点 index, 则 arr[index-1] > arr[index] && arr[index+1] > arr[index];
最小值就是这个拐点. [最小值, right]单调递增, 那么[left, 最小值](包括最小值) 就是一个无序数组. 

利用二分查找, 画图比较容易理解:
+ left, right, mid;
+ 如果 arr[mid] > arr[right], [mid, right]是无序数组, 包含拐点, left = mid+1;
+ 如果 arr[mid] < arr[right], [left, mid]是无序数组,这个无序数组必定包含最小值, right=mid;
+ 返回 arr[left]就是最小值, 返回arr[right]也是测试对的
```js
  var findMin = function(arr) {
      let left = 0, right = arr.length -1;
      // 如果是增序, 最小值就是第一个值
      if(arr[right] > arr[left]) return arr[0]; 

     
      //mid分开数组, 分开的两个数组都包含arr[mid], 必有一个是增序的, 另一个是无序的
      //拐点就在这个无序数组中. 返回的arr[left]就是最小值.
      while(left < right) {
        let mid = (left + right) >>> 1;
        if(arr[mid] > arr[right]) {
          //无序数组 [mid, right]
          left = mid + 1;
        }else if(arr[mid] < arr[right]) {
          //无序数组 [mid, right]
          right = mid;
        }
      }
      return arr[left];

    }

```