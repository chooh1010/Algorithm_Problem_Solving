### 처음 문제를 보고 생각한 자료구조 및 알고리즘

배열,구현

### 사용된 자료구조 및 알고리즘

배열,구현

### 걸린 시간

5분

### 나의 풀이

```java
class Solution {
    public long[] solution(long x, int n) {
        long[] answer = new long[n];
        for(int i=0;i<n;i++){
            answer[i] = (i+1)*x;
        }
        return answer;
    }
}
```

answer 배열에 조건에 맞게 채웠다.



### 다른사람의 풀이

```java
import java.util.stream.LongStream;
class Solution {
  public long[] solution(int x, int n) {
      return LongStream.iterate(x, i->i+x).limit(n).toArray();
  }
}
```

iterate로 x부터 시작하여 계속 x를 더하는 스트림을 n번 생성해서 배열로 반환한다.