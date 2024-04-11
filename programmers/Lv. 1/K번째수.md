### 처음 문제를 보고 생각한 자료구조 및 알고리즘

배열, 구현

### 사용된 자료구조 및 알고리즘

배열, 구현

### 걸린 시간

25분

### 나의 풀이

```java
import java.util.*;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];
        for(int i=0;i<commands.length;i++){
            int[] arr = new int[commands[i][1]-commands[i][0]+1];
            for(int j=commands[i][0]-1;j<commands[i][1];j++){
                arr[j-commands[i][0]+1]=array[j];
            }
            Arrays.sort(arr);
            answer[i] = arr[commands[i][2]-1];
        }
        return answer;
    }
}
```

배열을 새로 만들어서 범위에 해당하는 값들을 넣은 뒤 정렬을 해서 원하는 값을 구했다.



### 다른사람의 풀이

```java
import java.util.Arrays;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

        for(int i=0; i<commands.length; i++){
            int[] temp = Arrays.copyOfRange(array, commands[i][0]-1, commands[i][1]);
            Arrays.sort(temp);
            answer[i] = temp[commands[i][2]-1];
        }

        return answer;
    }
}
```

Arrays.copyOfRange() 메서드를 써서 범위에 해당하는 값들을 바로 구해서 배열에 넣었고 정렬해서 답을 구했다.

### 

```java
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int n = 0;
        int[] ret = new int[commands.length];

        while(n < commands.length){
            int m = commands[n][1] - commands[n][0] + 1;

            if(m == 1){
                ret[n] = array[commands[n++][0]-1];
                continue;
            }

            int[] a = new int[m];
            int j = 0;
            for(int i = commands[n][0]-1; i < commands[n][1]; i++)
                a[j++] = array[i];

            sort(a, 0, m-1);

            ret[n] = a[commands[n++][2]-1];
        }

        return ret;
    }

    void sort(int[] a, int left, int right){
        int pl = left;
        int pr = right;
        int x = a[(pl+pr)/2];

        do{
            while(a[pl] < x) pl++;
            while(a[pr] > x) pr--;
            if(pl <= pr){
                int temp = a[pl];
                a[pl] = a[pr];
                a[pr] = temp;
                pl++;
                pr--;
            }
        }while(pl <= pr);

        if(left < pr) sort(a, left, pr);
        if(right > pl) sort(a, pl, right);
    }
}
```

직접 퀵정렬 메서드를 구현해서 정렬해서 원하는 값을 구했다.