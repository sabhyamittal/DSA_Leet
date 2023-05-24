#### Reverse Integer
```
class Solution {
public:
    int reverse(int x) {
        int rem=0;
        int sum=0;
        while(x!=0)
        {
            rem=x%10;
            x=x/10;
            if(sum > INT_MAX/10 || sum == INT_MAX/10 && rem > 7){
			return 0 ;
		}
		
		if(sum < INT_MIN/10 || sum == INT_MIN/10 && rem < -8){
			return 0 ;
		}
            sum=(sum*10)+rem;
            
        }
        return sum;
    }
};
```
