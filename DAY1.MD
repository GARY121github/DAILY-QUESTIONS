# 724. Find Pivot Index AND 1991. Find the Middle Index in Array

## TIME-COMPLEXITY -> O(n) SPACE-COMPLEXITY -> O(n)

```java
    int[] left = new int[arr.length];

    for(int i = 1 ; i < left.length ; i++){
        left[i] = arr[i-1] + left[i-1];
    }

    int[] right = new int[arr.length];

    for(int i = arr.length-2 ; i >= 0 ; i--){
        right[i] = arr[i+1] + right[i+1];
    }
    for(int i = 0 ; i < arr.length ; i++){
        if(left[i] == right[i]){
            return i;
        }
    }
    return -1;
```

## TIME-COMPLEXITY -> O(N) SPACE-COMPLEXITY -> O(1)

```java
    int sum = 0, leftSum = 0;;
    for(int num: nums) sum+=num;
    for(int i=0; i<nums.length; i++){
        if(leftSum == sum-leftSum-nums[i]) return i;
        leftSum+=nums[i];
    }
    return -1;
```

# 1013. Partition Array Into Three Parts With Equal Sum

## TIME-COMPLEXITY -> O(N) SPACE-COMPLEXITY -> O(1)

```java
    public boolean canThreePartsEqualSum(int[] arr) {
        int total = 0;
        for(int i : arr){
            total += i;
        }

        if(total%3 != 0){
            return false;
        }

        int one_third = total/3 , temp = 0 , count = 0;
        for(int i = 0 ; i < arr.length ; i++){
            temp += arr[i];
            if(temp == one_third){
                count++;
                temp = 0;
            }
        }

        if(count >= 3)
        return true;

        return false;
    }
```

# 1232. Check If It Is a Straight Line

## TIME-COMPLEXITY -> O(N) SPACE-COMPLEXITY -> O(1)

```java
class Solution {
    public boolean checkStraightLine(int[][] coordinates) {
        int x0 = coordinates[0][0],
            x1 = coordinates[1][0],
            y0 = coordinates[0][1],
            y1 = coordinates[1][1];

        for(int i = 1; i < coordinates.length; i++){
            int yi = coordinates[i][1];
            int xi = coordinates[i][0];

            if ((y1-y0)*(xi-x1) != (yi-y1)*(x1-x0)) {
                return false;
            }
        }

        return true;

}}
```

# 122. Best Time to Buy and Sell Stock II

## TIME-COMPLEXITY -> O(N) SPACE-COMPLEXITY -> O(1)

```java
class Solution {
    public int maxProfit(int[] prices) {
        int profit = 0;
        for(int i = 0; i < prices.length-1; i++){
            if(prices[i] < prices[i+1]){
                profit += prices[i+1] - prices[i];
            }
        }

        return profit;
    }
}
```

# 75. Sort Colors

## TIME-COMPLEXITY -> O(N) SPACE-COMPLEXITY -> O(1)

```java
class Solution {
    public void sortColors(int[] nums) {
        int lo = 0;
        int hi = nums.length - 1;
        int index = 0;

        while(index <= hi){
            if(nums[index] == 0){
                nums[index] = nums[lo];
                nums[lo] = 0;
                lo++;
            }
            if(nums[index] == 2){
                nums[index] = nums[hi];
                nums[hi] = 2;
                hi--;

                index--;
            }
            index++;
        }

    }
}
```
