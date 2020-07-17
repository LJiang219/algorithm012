学习笔记待续...

# 解题4步法
1. clarification
2. possible solution -> optimal(time & space)
3. code
4. test cases

# 树, 二叉树, 二叉搜索树
1. Linked List 是特殊化的Tree; Tree 是特殊化的Graph
2. 树节点的定义(代码):
+ JavaScript
```js
  export class Node {
    constructor(val) {
      this.val = val;
      this.left = null;
      this.right = null; 
    }
  }
```

3. 二叉树遍历: 通常使用 递归
+ 前序 (Pre-order ): 根-左-右
+ 中序 (In-order): 左-根-右
+ 后序 (Post-order): 左-右-根

4. 代码 show-time
```js
// in, cb, in
inOrderTraverse(node, callback) {
  if(node != null) {
    this.inOrderTraverse(node.left, callback);
    callback(node.val);
    this.inOrderTraverse(node.right, callback);
  }
}

// cb, pre, pre
preOrderTraverse(node, callback) {
  if(node != null) {
    callback(node.val);
    this.preOrderTraverse(node.left, callback);
    this.preOrderTraverse(node.right, callback);
  }
}

// post, post, cb
postOrderTraverse(node, callback) {
  if(node != null) {
    this.postOrderTraverse(node.left, callback);
    this.postOrderTraverse(node.right, callback);
    callback(node.val);
  }
}

```

## 二叉搜索树 Binary Search Tree
二叉搜索树(Ordered Binary Tree) 是指一棵空树或者具有下列性质的二叉树: 
1. 左子树上 <u>所有结点</u> 的值 < root.val ;
2. 右子树上 <u>所有结点</u> 的值 > root.val ;
3. 以此类推: 左右子树也分别为二叉查找树 (这就是 <u>重复性</u> !)

中序遍历: 升序排列

# 堆 heap 

1. Heap: 可以迅速找到一堆数中的最大或者最小值的数据结构
+ 大顶堆(大根堆)
+ 小顶堆(小根堆)

2. 二叉堆性质:
 + 通过完全二叉树来实现(注意: 不是二叉搜索树), 他的根和每个叶子节点都是满的
 + 二叉堆 实现相对容易, 时间复杂度刚刚及格,是堆(优先队列 priority_queue) 的一种简单实现,但是不是最优的实现

3. 二叉堆(大顶) 满足下列性质:
+ 是一棵完全树
+ 树中任意节点的值总是 >= 其子节点的值

3. 二叉堆的实现
+ 数组
+ 父节点和子节点的位置关系: 
  - 索引为i的左孩子的索引 是 (2*i+1);
  - 索引为i的右孩子的索引 是 (2*i+2);
  - 索引为i的父节点的索引 是 floor((i-1)/2);

4. Insert : 
  + 新元素一律先插入到堆的尾部
  + 依次向上调整(和其父节点比较),一直到根节点
  + HeapifyUp
  + O(logN)

5. delete Max 删除堆顶
+ 将堆尾元素替换到顶部
+ 依次从根部向下调整整个堆的结构(一直到堆尾)
+ HeapifyDown

6. 应用
+ 最大堆: 得到一个升序排列的数组
+ 最小堆: 降序
+ 求前 k 大，用小根堆，求前 k 小，用大根堆。 
参考[前k个高频元素]和[最小的k个数]


  