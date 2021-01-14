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
## JZ5  用两个栈实现队列 :flushed:
`简单` `题目`<br>
*用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。*<br>
<br>
`考点`<br>
栈 队列<br>
栈 先进后出<br>
队列 先进后出<br>
<br>
`代码`<br>
```java
import java.util.Stack;

public class Solution {
    //栈    先进后出
    //队列  先进先出
    Stack<Integer> stack1 = new Stack<Integer>();
    Stack<Integer> stack2 = new Stack<Integer>();
    int size = 0;
    
    public void push(int node) {
        //插入一个元素
        //stack1保存 队列的底部存新插入的，顶部存老的元素
        //可以看作两个竹筒倒豌豆
        while(!stack1.isEmpty()) stack2.push(stack1.pop());
        stack1.push(node);
        while(!stack2.isEmpty()) stack1.push(stack2.pop());
        size ++;
    }
    
    public int pop() {
        //删除队列的首部元素
        if(size == 0) return 0;
        int res = stack1.pop();
        size --;
        return res;
    }
}
```
## JZ7  斐波那契数列 :flushed:
`入门` `题目`<br>
*大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项（从0开始，第0项为0，第1项是1）。n≤39*<br><br>
`考点`<br>
数组<br>
递归<br>
<br>
`代码`<br>
```java
public class Solution {
    public int Fibonacci(int n) {
        if(n == 0) return 0;
        if(n == 1) return 1;
        int res = 0;
        int n_2 = 0;
        int n_1 = 1;
        for(int i=2; i <= n; i++){
            res = n_1 + n_2;
            n_2 = n_1;
            n_1 = res;
        }
        return res;
    }
}
```
```java
public class Solution {
    public int Fibonacci(int n) {
        if(n == 0) return 0;
        if(n == 1) return 1;
        int res = 0;
        int first = 0;
        int second = 1;
        for(int i=2; i<=n; i++){
            res = (first + second) % 1000000007;
            first = second % 1000000007;
            second = res % 1000000007;
        }
        return res % 1000000007;
    }
}
```
