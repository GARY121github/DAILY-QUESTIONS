# 724. Find Pivot Index AND 1991. Find the Middle Index in Array

## TIME-COMPLEXITY -> O(n) SPACE-COMPLEXITY -> O(n)

> int[] left = new int[arr.length];
> for(int i = 1 ; i < left.length ; i++){
> left[i] = arr[i-1] + left[i-1];
> }
> int[] right = new int[arr.length];
> for(int i = arr.length-2 ; i >= 0 ; i--){
> right[i] = arr[i+1] + right[i+1];
> }
>  
>       for(int i = 0 ; i < arr.length ; i++){
>           if(left[i] == right[i]){
>               return i;
>           }
>       }
>       return -1;
>

## TIME-COMPLEXITY -> O(N) SPACE-COMPLEXITY -> O(1)
>
>          int sum = 0, leftSum = 0;;
>          for(int num: nums) sum+=num;
>          for(int i=0; i<nums.length; i++){
>              if(leftSum == sum-leftSum-nums[i]) return i;
>              leftSum+=nums[i];
>          }
>          return -1;
>
>
# 1013. Partition Array Into Three Parts With Equal Sum

## TIME-COMPLEXITY -> O(N) SPACE-COMPLEXITY -> O(1)

>
> public boolean canThreePartsEqualSum(int[] arr) {
> int total = 0;
> for(int i : arr){
> total += i;
> }
>
>        if(total%3 != 0){
>            return false;
>        }
>
>        int one_third = total/3 , temp = 0 , count = 0;
>        for(int i = 0 ; i < arr.length ; i++){
>            temp += arr[i];
>            if(temp == one_third){
>                count++;
>                temp = 0;
>            }
>        }
>
>        if(count >= 3)
>        return true;
>
>        return false;
> }
