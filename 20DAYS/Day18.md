# DAY18

## 844.比较含退格的字符串

```java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        char[] sArray=s.toCharArray();
        char[] tArray=t.toCharArray();
        int slow=0,fast=0;
        while(fast<sArray.length){
            if(sArray[fast]!='#'){
                sArray[slow]=sArray[fast];
                slow++;
            }else if(slow>0){
                slow--;
            }
            fast++;
        }
        int sLength=slow;
        slow=0;
        fast=0;
        while(fast<tArray.length){
            if(tArray[fast]!='#'){
                tArray[slow]=tArray[fast];
                slow++;
            }else if(slow>0){
                slow--;
            }
            fast++;
        }
        int tLength=slow;
        if(tLength!=sLength){
            return false;
        }
        for(int i=0;i<sLength;i++){
            if(sArray[i]!=tArray[i]){
                return false;
            }
        }
        return true;
    }
}
```

## 986.区间列表的交集

```java
class Solution {
    public int[][] intervalIntersection(int[][] firstList, int[][] secondList) {
        List<int[]> list=new ArrayList();
        int i=0,j=0;
        while(i<firstList.length && j<secondList.length){
            int x1=firstList[i][0];
            int x2=firstList[i][1];
            int y1=secondList[j][0];
            int y2=secondList[j][1];
            int[] tmp=new int[2];
            tmp[0]=Math.max(x1,y1);
            tmp[1]=Math.min(x2,y2);
            if(tmp[1]>=tmp[0]){
                list.add(tmp);
            }
            if(y2>=x2){
                i++;
            }else{
                j++;
            }
        }
        return list.toArray(new int[list.size()][]);
    }
}
```

## 11.盛最多水的容器

```java
class Solution {
    public int maxArea(int[] height) {
       int i=0;
       int j=height.length-1;
       int maxarea=0;
       while(i<j){
           int area=(j-i)*Math.min(height[j],height[i]);
           maxarea=Math.max(area,maxarea);
           if(height[i]<height[j]){
               i++;
           }else{
               j--;
           }
       }
       return maxarea;
    }
}
```

