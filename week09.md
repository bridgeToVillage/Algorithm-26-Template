## 第九周作业

### 作业1

- 用自己熟悉的编程语言，手写各种初级排序代码，提交到学习总结中。

#### 选择排序

```js
function selectionSort(arr) {
    var len = arr.length;
    var minIndex, temp;
    for(var i = 0; i < len - 1; i++) {
        minIndex = i;
        for(var j = i + 1; j < len; j++) {
            if(arr[j] < arr[minIndex]) {    // 寻找最小的数
                minIndex = j;                // 将最小数的索引保存
            }
        }
        temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
    return arr;
} 
```



#### 插入排序

```js
// javascript
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
    return arr;
}
```



#### 冒泡排序

```js
// javascript
function bubbleSort(arr) {
    var len = arr.length;
    for(var i = 0; i < len - 1; i++) {
        for(var j = 0; j < len - 1 - i; j++) {
            if(arr[j] > arr[j+1]) {       // 相邻元素两两对比
                var temp = arr[j+1];       // 元素交换
                arr[j+1] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}
```



#### 快排代码

```js
// JavaScript
const quickSort = (nums, left, right) => {  
    if (nums.length <= 1) return nums  
    if (left < right) {    
        index = partition(nums, left, right)    
        quickSort(nums, left, index-1)    
        quickSort(nums, index+1, right)  
    }}      
const partition = (nums, left, right) => {  
    let pivot = left, index = left + 1  
    for (let i = index; i <= right; i++) {    
        if (nums[i] < nums[pivot]) {      
            [nums[i], nums[index]] = [nums[index], nums[i]]      
            index++    
        }  
    }  
    [nums[pivot], nums[index-1]] = [nums[index-1], nums[pivot]]  
    return index -1
}
```

#### 归并排序

```js
// JavaScript
const mergeSort = (nums) => {  
    if (nums.length <= 1) return nums  
    let mid = Math.floor(nums.length/2),       
        left = nums.slice(0, mid),       
        right = nums.slice(mid)  
    return merge(mergeSort(left), mergeSort(right))}
const merge = (left, right) => {  
    let result = []  
    while(left.length && right.length) {    
        result.push(left[0] <= right[0] ? left.shift() : right.shift())  
    }  
    while(left.length) 
        result.push(left.shift())  
    while(right.length) 
        result.push(right.shift())  
    return result
}
```



#### 堆排序

```js
// Javascript
function heapSort(arr) {  
    if (arr.length === 0) return;  
    let len = arr.length;  // 建堆  
    for (let i = Math.floor(len / 2) - 1; i >= 0; i--) {    
        heapify(arr, len, i);  }  // 排序  
    for (let i = len - 1; i >= 0; i--) {    
        // 堆顶元素与最后一个互换    
        [arr[0], arr[i]] = [arr[i], arr[0]];    // 对 0 ～ i 的数组建堆    
        heapify(arr, i, 0);  
    }}
function heapify(arr, len, i) {  
    let left = i * 2 + 1;  
    let right = i * 2 + 2;  
    let largest = i;  
    if (left < len && arr[left] > arr[largest]) {    
        largest = left;  
    }  
    if (right < len && arr[right] > arr[largest]) {    
        largest = right;  
    }  
    if (largest !== i) {    
        [arr[i], arr[largest]] = [arr[largest], arr[i]];    
        heapify(arr, len, largest);  
    }
}
```

