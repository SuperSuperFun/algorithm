### 1.Reverse Integer
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
