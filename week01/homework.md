
## 简单

### 用 add first 或 add last 这套新的 API 改写 Deque 的代码
### 分析 Queue 和 Priority Queue 的源码


### 删除排序数组中的重复项
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums==null||nums.length<2)
            return nums.length;

        int cur = 0;
        for (int i = 1; i<nums.length;i++ ){
            if(nums[i]!=nums[cur])
                nums[++cur] = nums[i];
        }

        return cur+1;
    }
}

```
### 旋转数组

使用旋转法
```java
class Solution {
    public void rotate(int[] nums, int k) {
        if(k==0 || k % nums.length ==0 )
            return;
        k = k % nums.length;

        rotate(nums,0,nums.length-1);
        rotate(nums,0,k-1);
        rotate(nums,k,nums.length-1);

    }

    private void rotate(int[] nums,int begin,int end){
        while(begin<end){
            int t = nums[end];
            nums[end] = nums[begin];
            nums[begin] = t;
            begin++;
            end--;
        }
    }
}
```
### 合并两个有序链表


### 合并两个有序数组
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {

        int i = m - 1;
        int j = n - 1;
        int cur= n + m-1;

        while(i>=0 && j>=0){
            nums1[cur--]= nums1[i] > nums2[j] ? nums1[i--]:nums2[j--];
        }
    
        while (j >= 0) {
            nums1[cur--] = nums2[j--];
        }
    }
}
```


### 两数之和
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {

        int len = nums.length;
        Map<Integer,Integer> map = new HashMap<>();
        for(int i=0; i<len; i++){
            if(map.containsKey(target - nums[i])){
                return new int[]{i, map.get(target - nums[i])};
            }
            map.put(nums[i], i);
        }

        return new int[]{};
    }
}
```
### 移动零
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int len = nums.length;

        int cur = 0;
        for(int i = 0 ;i<len; i++){
            if(nums[i]!=0){
                nums[cur++] = nums[i];
            }
        }

        while(cur<len){
            nums[cur++] = 0;
        }
    }    
}
```

### 加一
```java
class Solution {
    public int[] plusOne(int[] digits) {

        int len = digits.length;
        for(int i = len-1; i>=0;i--){
            if(digits[i]!=9){
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }

        int[] nums = new int[len+1];
        nums[0] = 1;
        return nums;
    }
}
```

## 中等
## 设计循环双端队列


## 困难
### 接雨水