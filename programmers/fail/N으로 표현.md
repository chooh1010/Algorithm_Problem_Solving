### 처음 문제를 보고 생각한 자료구조 및 알고리즘

dp

### 사용된 자료구조 및 알고리즘

dp

### 걸린 시간

fail

### 나의 풀이

```java
import java.util.*;

class Solution {
    public int solution(int N, int number) {
        List<Set<Integer>> dp = new ArrayList<>();
        
        dp.add(new HashSet<>());
        for(int i=1;i<=8;i++){
            Set<Integer> current = new HashSet<>();
            int connectedNumber = 0;
            
            for(int j=0;j<i;j++){
                connectedNumber = connectedNumber*10 + N;
            }
            
            current.add(connectedNumber);
            
            for(int leftCount = 1;leftCount<i;leftCount++){
                int rightCount = i - leftCount;
                for(int left:dp.get(leftCount)){
                    for(int right:dp.get(rightCount)){
                        current.add(left + right);
                        current.add(left - right);
                        current.add(left * right);
                        
                        if(right!=0) current.add(left / right);
                    }
                }
            }
            
            if(current.contains(number)) return i;
            
            dp.add(current);
        }
        return -1;
    }
}
```

처음에 dp를 생각했는데 number가 1일때 부터를 dp에 넣어서 풀려고해서 풀지 못했다. dp에 N값이 1부터 8일때를 넣어서 했어야 했다. HashSet으로 중복을 없애고 NN 이런 수인 connectedNumber을 추가하고 N을 4개 사용해서 만드는 경우는 1개 + 3개, 2개 + 2개, 3개 + 1개 사용결과를 합해서 구하므로 left, right로 나눠서 각 set의 숫자들을 꺼내서 연산해서 넣어주었다.