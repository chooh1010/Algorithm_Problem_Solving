### 처음 문제를 보고 생각한 자료구조 및 알고리즘

배열,구현

### 사용된 자료구조 및 알고리즘

배열,구현

### 걸린 시간

8분

### 나의 풀이

```java
class Solution {
    boolean solution(String s) {
        boolean answer = true;
        s = s.toLowerCase();
        int p=0, y=0;
        for(char x:s.toCharArray()){
            if(x=='p') p++; 
            else if(x=='y') y++;
        }
        if(p!=y) answer = false;
        return answer;
    }
}
```

s를 모두 소문자로 바꾼 뒤 count값을 비교했다.

### 다른사람의 풀이

```java
class Solution {
    boolean solution(String s) {
        s = s.toUpperCase();

        return s.chars().filter( e -> 'P'== e).count() == s.chars().filter( e -> 'Y'== e).count();
    }
}
```

chars() 로 바꿔준 뒤 filter로 조건의 맞는 값을 걸러낸 뒤 count값을 비교했다.