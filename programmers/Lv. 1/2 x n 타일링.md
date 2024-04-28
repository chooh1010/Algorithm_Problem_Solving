### 처음 문제를 보고 생각한 자료구조 및 알고리즘

DFS

### 사용된 자료구조 및 알고리즘

DP

### 걸린 시간

30분

### 나의 풀이

```java
class Solution {
    public long solution(int n) {
        if(n==1) return 1;
        else if(n==2) return 2;
        else{
            long[] dp = new long[n+1];
            dp[1] = 1;
            dp[2] = 2;
            for(int i=3;i<n+1;i++){
                dp[i] = (dp[i-1] + dp[i-2])%1000000007;
            }
            return dp[n];
        }
    }
}
```

처음에 DFS로 1과 2로 더해서 n을 만들 수 있는 모든 경우의 수를 구했는데 시간초과가 나서 DP로 피보나치수 점화식을 세워서 풀었다.