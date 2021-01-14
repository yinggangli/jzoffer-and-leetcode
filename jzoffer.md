# 剑指offer
## JZ6  旋转数组的最小数 :flushed:
`简单` `题目`<br>
*把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个非递减排序的数组的一个旋转，输出旋转数组的最小元素。NOTE：给出的所有元素都大于0，若数组大小为0，请返回0。* <br><br>
`考点`<br>
二分查找，对有序数组排序<br>
非递减排序数组左右的元素大小关系为:array[left] <= array[right] 要找到旋转数组的最小元素，即需要找到数组顺序的分界元素<br><br>
`代码`<br>
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
    return nums[l];//或nums[r]
  }
}
```
## JZ6  旋转数组的最小数 :flushed:
`简单``题目`<br>
*用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。*<br><br>
`考点`<br>
<font color=HotPink>栈 队列</font>
}
