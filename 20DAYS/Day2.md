# DAY2

## 977.有序数组的平方

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        //由于数组有序,采用双指针
        int[] ans = new int[nums.length];
        int k=nums.length-1;
        int left=0,right=nums.length-1;
        while(left<=right){
            if(nums[left]*nums[left]>nums[right]*nums[right]){
                ans[k--]=nums[left]*nums[left];
                left++;
            }
            else{
                ans[k--]=nums[right]*nums[right];
                right--;
            }
        }
        return ans;   
        
        /*
        直接排序 效率低下
        int[] ans = new int[nums.length];
        for(int i=0;i<nums.length;i++){
            ans[i]=nums[i]*nums[i];
        }
        Arrays.sort(ans);
        return ans;
        */
    }
}
```

## 189.轮转数组

```java
class Solution {
    public void rotate(int[] nums, int k) {
        //轮转 保存变量temp 不另开辟空间
        int start=-1;
        k = k % nums.length;
        int times=gcd(k,nums.length);
        while(times!=0){
            start++;
            int cur=nums[start];
            int cur_index=start;
            do{
                int next_index=(cur_index+k)%nums.length;//2
                int next=nums[next_index];//3
                nums[next_index]=cur;//
                cur=next;
                cur_index=next_index;
            }while(cur_index!=start);

            times--;
        }

        /* 另外开辟空间
        int[] ans=new int[nums.length];
        for(int i=0;i<=nums.length-1;i++){
            ans[(k+i)%nums.length]=nums[i];
        }
        System.arraycopy(ans, 0, nums, 0, nums.length);
        */

        /* 使用翻转操作
        k=k%nums.length;
        reverse(nums,0,nums.length-1);
        reverse(nums,0,k-1);
        reverse(nums,k,nums.length-1);
        */
    }

    /*
    public void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start += 1;
            end -= 1;
        }
    }
    */
    
    public int gcd(int x, int y) {
        return y > 0 ? gcd(y, x % y) : x;
    }
}
```

