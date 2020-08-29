学习笔记

## 实战位运算
1. 判断奇偶:
  + x % 2 == 1 --> (x&1)==1;
  + x % 2 == 0 --> (x&1)==0;

2. x >> 1 --> x/2
  + mid = (left+right)/2; --> mid=(left+right)>>1;

3. X=X&(X-1) 清零最低位的1
  + 191. 位1的个数
  + 231. 2的幂

4. X&-X => 得到最低位的1

5. X&~X => 0



## 经典排序算法
推荐: https://www.cnblogs.com/onepixel/p/7674659.html

1. 冒泡排序
```js
function bubbleSort(arr) {
    varlen = arr.length;
    for(vari = 0; i < len - 1; i++) {
        for(varj = 0; j < len - 1 - i; j++) {
            if(arr[j] > arr[j+1]) {        // 相邻元素两两对比
                vartemp = arr[j+1];        // 元素交换
                arr[j+1] = arr[j];
                arr[j] = temp;
            }
        }
    }
    returnarr;
}

```

2. 选择排序（Selection Sort）
```js
function selectionSort(arr) {
    varlen = arr.length;
    varminIndex, temp;
    for(vari = 0; i < len - 1; i++) {
        minIndex = i;
        for(varj = i + 1; j < len; j++) {
            if(arr[j] < arr[minIndex]) {     // 寻找最小的数
                minIndex = j;                 // 将最小数的索引保存
            }
        }
        temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
    returnarr;
} 

```

3. 插入排序（Insertion Sort）
```js
function insertionSort(arr) {
    varlen = arr.length;
    varpreIndex, current;
    for(vari = 1; i < len; i++) {
        preIndex = i - 1;
        current = arr[i];
        while(preIndex >= 0 && arr[preIndex] > current) {
            arr[preIndex + 1] = arr[preIndex];
            preIndex--;
        }
        arr[preIndex + 1] = current;
    }
    returnarr;
}

```

4. 希尔排序（Shell Sort）
```js
  function shellSort(arr) {
    varlen = arr.length;
    for(vargap = Math.floor(len / 2); gap > 0; gap = Math.floor(gap / 2)) {
        // 注意：这里和动图演示的不一样，动图是分组执行，实际操作是多个分组交替执行
        for(vari = gap; i < len; i++) {
            varj = i;
            varcurrent = arr[i];
            while(j - gap >= 0 && current < arr[j - gap]) {
                  arr[j] = arr[j - gap];
                  j = j - gap;
            }
            arr[j] = current;
        }
    }
    returnarr;
  }
```

5. 归并排序（Merge Sort）
```js
  function mergeSort(arr) {
    varlen = arr.length;
    if(len < 2) {
        returnarr;
    }
    varmiddle = Math.floor(len / 2),
        left = arr.slice(0, middle),
        right = arr.slice(middle);
    returnmerge(mergeSort(left), mergeSort(right));
  }
  
  function merge(left, right) {
    varresult = [];

    while(left.length>0 && right.length>0) {
        if(left[0] <= right[0]) {
            result.push(left.shift());
        } else{
            result.push(right.shift());
        }
    }

    while(left.length)
        result.push(left.shift());

    while(right.length)
        result.push(right.shift());

    returnresult;
  }
```

6. 快速排序（Quick Sort） [!!!]
```js
function quickSort(arr, left, right) {
    varlen = arr.length,
        partitionIndex,
        left = typeofleft != 'number'? 0 : left,
        right = typeofright != 'number'? len - 1 : right;
 
    if(left < right) {
        partitionIndex = partition(arr, left, right);
        quickSort(arr, left, partitionIndex-1);
        quickSort(arr, partitionIndex+1, right);
    }
    returnarr;
}
 
function partition(arr, left ,right) {     // 分区操作
    varpivot = left,                      // 设定基准值（pivot）
        index = pivot + 1;
    for(vari = index; i <= right; i++) {
        if(arr[i] < arr[pivot]) {
            swap(arr, i, index);
            index++;
        }       
    }
    swap(arr, pivot, index - 1);
    returnindex-1;
}
 
function swap(arr, i, j) {
    vartemp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}
```

7. 堆排序（Heap Sort）
```js
varlen;    // 因为声明的多个函数都需要数据长度，所以把len设置成为全局变量
 
function buildMaxHeap(arr) {   // 建立大顶堆
    len = arr.length;
    for(vari = Math.floor(len/2); i >= 0; i--) {
        heapify(arr, i);
    }
}
 
function heapify(arr, i) {     // 堆调整
    varleft = 2 * i + 1,
        right = 2 * i + 2,
        largest = i;
 
    if(left < len && arr[left] > arr[largest]) {
        largest = left;
    }
 
    if(right < len && arr[right] > arr[largest]) {
        largest = right;
    }
 
    if(largest != i) {
        swap(arr, i, largest);
        heapify(arr, largest);
    }
}
 
function swap(arr, i, j) {
    vartemp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}
 
function heapSort(arr) {
    buildMaxHeap(arr);
 
    for(vari = arr.length - 1; i > 0; i--) {
        swap(arr, 0, i);
        len--;
        heapify(arr, 0);
    }
    returnarr;
}

```

8. 计数排序（Counting Sort）
```js
function countingSort(arr, maxValue) {
    varbucket = newArray(maxValue + 1),
        sortedIndex = 0;
        arrLen = arr.length,
        bucketLen = maxValue + 1;
 
    for(vari = 0; i < arrLen; i++) {
        if(!bucket[arr[i]]) {
            bucket[arr[i]] = 0;
        }
        bucket[arr[i]]++;
    }
 
    for(varj = 0; j < bucketLen; j++) {
        while(bucket[j] > 0) {
            arr[sortedIndex++] = j;
            bucket[j]--;
        }
    }
 
    returnarr;
}
```

9. 桶排序（Bucket Sort）
```js
function bucketSort(arr, bucketSize) {
    if(arr.length === 0) {
      returnarr;
    }
 
    vari;
    varminValue = arr[0];
    varmaxValue = arr[0];
    for(i = 1; i < arr.length; i++) {
      if(arr[i] < minValue) {
          minValue = arr[i];                // 输入数据的最小值
      } elseif(arr[i] > maxValue) {
          maxValue = arr[i];                // 输入数据的最大值
      }
    }
 
    // 桶的初始化
    varDEFAULT_BUCKET_SIZE = 5;            // 设置桶的默认数量为5
    bucketSize = bucketSize || DEFAULT_BUCKET_SIZE;
    varbucketCount = Math.floor((maxValue - minValue) / bucketSize) + 1;  
    varbuckets = newArray(bucketCount);
    for(i = 0; i < buckets.length; i++) {
        buckets[i] = [];
    }
 
    // 利用映射函数将数据分配到各个桶中
    for(i = 0; i < arr.length; i++) {
        buckets[Math.floor((arr[i] - minValue) / bucketSize)].push(arr[i]);
    }
 
    arr.length = 0;
    for(i = 0; i < buckets.length; i++) {
        insertionSort(buckets[i]);                      // 对每个桶进行排序，这里使用了插入排序
        for(varj = 0; j < buckets[i].length; j++) {
            arr.push(buckets[i][j]);                     
        }
    }
 
    returnarr;
}
```

10. 基数排序（Radix Sort）
```js
varcounter = [];
function radixSort(arr, maxDigit) {
  varmod = 10;
  vardev = 1;
  for(vari = 0; i < maxDigit; i++, dev *= 10, mod *= 10) {
      for(varj = 0; j < arr.length; j++) {
          varbucket = parseInt((arr[j] % mod) / dev);
          if(counter[bucket]==null) {
              counter[bucket] = [];
          }
          counter[bucket].push(arr[j]);
      }
      varpos = 0;
      for(varj = 0; j < counter.length; j++) {
          varvalue = null;
          if(counter[j]!=null) {
              while((value = counter[j].shift()) != null) {
                    arr[pos++] = value;
              }
        }
      }
  }
  returnarr;
}
```