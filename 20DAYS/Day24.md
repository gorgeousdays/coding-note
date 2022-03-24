# DAY24

## 47. 全排列 II

```java
class Solution {
    List<List<Integer>> res=new ArrayList<>();
    List<Integer> temp=new ArrayList<>();
    public List<List<Integer>> permuteUnique(int[] nums) {
        boolean[] used=new boolean[nums.length];
        Arrays.fill(used,false);
        Arrays.sort(nums);
        backTrack(nums,used);
        return res;
    }
    public void backTrack(int[] nums,boolean[] used){
        if(temp.size()==nums.length){
            res.add(new ArrayList<>(temp));
            return;
        }
        for(int i=0;i<nums.length;i++){
            if(i>0&&nums[i]==nums[i-1]&&used[i-1]==false){
                continue;
            }
            if(used[i]==false){
                used[i]=true;
                temp.add(nums[i]);
                backTrack(nums,used);
                temp.remove(temp.size()-1);
                used[i]=false;
            }
        }
    }
}
```

## 39.组合总和

```java
class Solution {
    List<List<Integer>> res=new ArrayList<>();
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        Arrays.sort(candidates);
        backTrack(candidates,target,0,new ArrayList<Integer>());
        return res;
    }
    public void backTrack(int[] candidates,int target,int i,ArrayList<Integer> temp){
        if(target<0){
            return;
        }
        if(target==0){
            res.add(new ArrayList<>(temp));
            return;
        }
        for(int left=i;left<candidates.length;left++){
            temp.add(candidates[left]);
            backTrack(candidates,target-candidates[left],left,temp);
            temp.remove(temp.size()-1);

        }
    }
}
```

## 40. 组合总和 II

```java
class Solution {
    List<List<Integer>> res=new ArrayList<>();
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        backTrack(candidates,target,0,new ArrayList<Integer>());
        return res;
    }
    public void backTrack(int[] candidates,int target,int i,ArrayList<Integer> temp){
        if(target<0){
            return;
        }
        if(target==0){
            res.add(new ArrayList<>(temp));
            return;
        }
        for(int left=i;left<candidates.length;left++){
            if(left>i && candidates[left]==candidates[left-1]){
                continue;
            }
            temp.add(candidates[left]);
            backTrack(candidates,target-candidates[left],left+1,temp);
            temp.remove(temp.size()-1);

        }
    }
}
```

