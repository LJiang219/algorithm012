学习笔记

## 字典树和并查集

### Trie树(字典树)
1. 定义

2. Trie树代码模板
```js

 class Trie{
   constructor() {
     this.root = {};
     this.endOfWord = "$";
   }

   insert(word) {
     let node = this.root;
     for(let ch of word) {
       node[ch] = node[ch] || {};
       node = node[ch];
     }
     node[this.endOfWord] = this.endOfWord;
   }

   search(word) {
     let node = this.root;
     for(let ch of word) {
       if(!node[ch]) return false;
       node = node[ch];
     }
     return node[this.endOfWord] === this.endOfWord;
   }

   startsWith(word) {
     let node = this.root;
     for(let ch of word) {
       if(!node[ch]) return false;
       node = node[ch];
     }
     return true;
   }
 }

 let trie = new Trie();
 console.log(trie.insert("apple"));
 console.log(trie.search("apple"));
 console.log(trie.search("app"));
 console.log(trie.startsWith("app"));
 console.log(trie.insert("app"));
 console.log(trie.search("app"));
```

### 并查集(Union-Find)
+ 解决的问题: 你和他是不是朋友的问题
+ 试用场景:
+ 考题特点: 比较死板, 没有dp等考查灵活, 记住Template
+ 基本操作:  
  - makeSet(s) : 建立一个新的并查集, 其中包含s个单元素集合
  - unionSet(x,y) : 把元素x和y所在的集合合并, 要求x和y所在的集合不相交, 如果相交则不合并.
  - find(x) : 找到元素x所在的集合的代表, 该操作也可以用于判断两个元素是否位于同一个集合, 只要将他们各自的代表比较一下就可以了. 

+ template code
```js
// JavaScript
class unionFind {
  constructor(n) {
    this.count = n;
    this.parent = new Array(n);
    for (let i = 0; i < n; i++) {
      this.parent[i] = i;
    }
  }

  find(p) {
    let root = p;
    while (parent[root] !== root) {
      root = parent[root];
    }
    // 压缩路径
    while (parent[p] !== p) {
      let x = p;
      p = this.parent[p];
      this.parent[x] = root;
    }
    return root;
  }

  union(p, q) {
    let rootP = find(p);
    let rootQ = find(q);
    if (rootP === rootQ) return;
    this.parent[rootP] = rootQ;
    this.count--;
  }
}

```

