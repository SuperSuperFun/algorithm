### 1.Two Sum
#### Examples
```
Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] returnVal = null;
        for(int i=0;i<nums.length-1;i++) {
            for(int j=i+1;j<nums.length;j++) {
                if(nums[i] + nums[j] == target) {
                    returnVal =  new int[]{i, j};
                    break;
                }
            }
        }
        return returnVal;
    }
}
```



### 2.Reverse Integer
#### Examples
```
Input: 123
Output:  321
or
Input: -123
Output: -321
or
Input: 120
Output: 21
Note:
Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. 
For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.
```
```
class Solution {
    public int reverse(int x) {
        int retVal = 0;
        if(x>0) {
            while(x%10 == 0) {
                x = x/10;
            }
            retVal = divide(x);
        } else if(x<0) {
            x = Math.abs(x);
            while(x%10 == 0) {
                x = x/10;
            }
            retVal = divide(x)*(-1);
        } else {
            retVal = 0;
        }
        return retVal;
        
    }
    
    public int divide(int x) {
        int result = 0;
        int left = 0;
        long retVal = 0;
        while(x>0) {
            if(retVal>Integer.MAX_VALUE || retVal<Integer.MIN_VALUE) {
                retVal = 0;
                break;
            }
            if(x<10) {
                retVal += x;
                break;
            }
            result = x/10;
            left = x%10;
            x = result;
            retVal = (retVal+=left)*10;
        }
        return (int)retVal;
    }
}
```
