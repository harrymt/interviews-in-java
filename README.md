# interviews-in-java
Elements of Programming Interviews in Java


#### Count largest binary gap

```
32 (100000) = 0
9 (1001) = 2
```

```java
class Solution {
    public int solution(int N) {
        
        // The max binary gap
        int max = 0;
        
        // The current binary gap
        int count = 0;
        
        // Has a binary gap
        boolean hasGap = false;
        boolean seenOne = false;
        boolean seenOneThenZero = false;
        
        // Is the bit zero
        boolean isZero = false;
        
        while(N > 0) {
            isZero = 0 == (N & 1);
            
            if (isZero) {
                count++;
                if (seenOne) {
                    seenOneThenZero = true;
                }
            } else {
                if (hasGap && count > max) {
                    max = count;
                }
                
                seenOne = true;
                if (seenOneThenZero) {
                    hasGap = true;
                }
                count = 0;
            }
            
            N >>>= 1;
        }
        if (!hasGap) return 0;
        return max;
    }
}
```
