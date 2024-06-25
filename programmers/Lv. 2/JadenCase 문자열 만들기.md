### 처음 문제를 보고 생각한 자료구조 및 알고리즘

구현

### 사용된 자료구조 및 알고리즘

구현

### 걸린 시간

30분

### 나의 풀이

```java
class Solution {
    public String solution(String s) {
        char[] arr = s.toCharArray();
        if(Character.isAlphabetic(arr[0])) arr[0]=Character.toUpperCase(arr[0]);
        for(int i=0;i<arr.length-1;i++){
            if(arr[i]==' '&&Character.isAlphabetic(arr[i+1])) {
                arr[i+1]=Character.toUpperCase(arr[i+1]);
            }else if(Character.isAlphabetic(arr[i])&&Character.isAlphabetic(arr[i+1])){
                arr[i+1]=Character.toLowerCase(arr[i+1]);
            }else if(Character.isDigit(arr[i])&&Character.isAlphabetic(arr[i+1])){
                arr[i+1]=Character.toLowerCase(arr[i+1]);
            }
        }
        return String.valueOf(arr);
    }
}
```

첫 글자가 알파벳이면 대문자로 바꿔주었고 빈칸과 알파벳이 연속으로 나오면 대문자로, 알파벳과 알파벳이 연속으로 나오면 소문자로, 숫자와 알파벳이 연속으로 나오면 소문자로 바꿔주었다.

### 다른사람의 풀이

```java
class Solution {
  public String solution(String s) {
        String answer = "";
        String[] sp = s.toLowerCase().split("");
        boolean flag = true;

        for(String ss : sp) {
            answer += flag ? ss.toUpperCase() : ss;
            flag = ss.equals(" ") ? true : false;
        }

        return answer;
  }
}
```

처음 주어진 문자열을 다 소문자로 바꾸고 flag를 둬서 앞이 빈칸일 때만 다음 문자를 대문자로 바꿔주었다.