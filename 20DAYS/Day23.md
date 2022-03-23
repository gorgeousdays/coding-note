# DAY23

## 78.子集

```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res=new ArrayList<>();
        res.add(new ArrayList<>());
        for(int i=0;i<nums.length;i++){
            int size=res.size();
            for(int j=0;j<size;j++){
                List<Integer> temp=new ArrayList<>(res.get(j));
                temp.add(nums[i]);
                res.add(temp);
            }
        }
        return res;
    }
}
```

## 90.子集II

```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res=new ArrayList<>();
        res.add(new ArrayList<>());
        int left=0,right=1,len=0;
        for(int i=0;i<nums.length;i++){
            if(i!=0 && nums[i]==nums[i-1]){
                left=res.size()-len;
            }
            else{
                left=0;
            }
            right=res.size();
            len=right-left;
            int size=res.size();
            for(int j=left;j<right;j++){
                List<Integer> temp=new ArrayList<>(res.get(j));
                temp.add(nums[i]);
                res.add(temp);
            }
        }
        return res;
    }
}
```

