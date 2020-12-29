# 剑指offer
## JZ6  旋转数组的最小数 
`简单`题目：*把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个非递减排序的数组的一个旋转，输出旋转数组的最小元素。NOTE：给出的所有元素都大于0，若数组大小为0，请返回0。* <br>
考点：二分<br>
代码：<br>
```java
class Solution{
  public int minArray(int[] nums){
    //3 4 5 1 2 3 3 3 3
    //首先去掉最末尾重复的部分
    //3 4 5 1 2 
    int n = nums.length - 1;
    if(n < 0) return 0;
    while(n > 0 && nums[n] == nums[0]) n --;
    
    //如果数组没有旋转，则直接返回第一个数
    if(nums[0] <= nums[n]) return nums[0];
    
    //二分
    int l = 0;
    int r = n;
    while(l < r){
      int mid = (l + r) / 2;
      if(nums[mid] < nums[0]) r = mid;
      else l = mid + 1;
    }
    return nums[l]
  }
}
```
