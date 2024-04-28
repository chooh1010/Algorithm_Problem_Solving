### 처음 문제를 보고 생각한 자료구조 및 알고리즘

DP

### 사용된 자료구조 및 알고리즘

DP

### 걸린 시간

fail

### 나의 풀이

```java
class Solution {
    public long solution(int n) {
        if(n==2) return 3;
        else if(n==4) return 11;
        else if(n%2==1) return 0;
        else{
            long[] dp = new long[n+1];
            dp[2]=3;
            dp[4]=11;
            for(int i=6;i<n+1;i++){
                dp[i] = ((dp[i-2]*4)%1000000007-dp[i-4]%1000000007+1000000007)%1000000007;
            }
            return dp[n];
        }
    }
}
```

DP로 풀어야겠다고 생각했는데 점화식을 생각해내지 못해서 풀지 못했다. 점화식은 dp[i] = dp[i-2]*4-dp[i-4]이다.