## 第九周作业

### 作业1

- 用自己熟悉的编程语言，手写各种初级排序代码，提交到学习总结中。

#### 选择排序

#### 插入排序

#### 冒泡排序

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

#### 堆排序

