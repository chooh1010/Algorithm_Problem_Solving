### 처음 문제를 보고 생각한 자료구조 및 알고리즘

DFS

### 사용된 자료구조 및 알고리즘

DFS

### 걸린 시간

fail

### 나의 풀이

```java
class Solution {
    public int GCD(int a, int b){
        if(a%b==0) return b;
        else return GCD(b,a%b);
    }

    public int LCM(int[] arr){
        if(arr.length==1) return arr[0];

        int gcd = GCD(arr[0],arr[1]);
        int lcm = (arr[0]*arr[1])/gcd;

        for(int i=2;i<arr.length;i++){
            gcd = GCD(arr[i],lcm);
            lcm = (arr[i]*lcm)/gcd;
        }

        return lcm;
    }

    public int solution(int[] arr) {
        return LCM(arr);
    }
}
```

유클리드 호제법으로 최대공약수와 최소공배수를 구하는 법을 까먹어서 풀지 못했다. 재귀함수를 활용하여 두수를 나눈 나머지값으로 계속 나눠서 나머지가 0이 되는 수를 최대공약수로 구했다. 두 수를 곱한 것을 최대공약수로 나눠서 최소공배수를 구했다.