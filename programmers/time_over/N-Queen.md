### 처음 문제를 보고 생각한 자료구조 및 알고리즘

백트레킹

### 사용된 자료구조 및 알고리즘

백트레킹

### 걸린 시간

1시간

### 나의 풀이

```java
class Solution {
    static int answer;
    static int[][] chess;
    static int num;
    static int[] dx = {-1,-1,1,1};
    static int[] dy = {-1,1,-1,1};

    public void DFS(int L){
        if(L==0) answer++;
        else{
            for(int i=0;i<num;i++){
                if(chess[num-L][i]==0){
                    for(int j=0;j<num;j++){
                        chess[num-L][j]++;
                        chess[j][i]++;
                        for(int k=0;k<4;k++){
                            int y = num-L+dy[k]*(j+1);
                            int x = i+dx[k]*(j+1);
                            if(y<num&&y>=0&&x<num&&x>=0) chess[y][x]++;
                        }
                    }
                    DFS(L-1);
                    for(int j=0;j<num;j++){
                        chess[num-L][j]--;
                        chess[j][i]--;
                        for(int k=0;k<4;k++){
                            int y = num-L+dy[k]*(j+1);
                            int x = i+dx[k]*(j+1);
                            if(y<num&&y>=0&&x<num&&x>=0) chess[y][x]--;
                        }
                    }
                }
            }
        }
    }

    public int solution(int n) {
        answer = 0;
        chess = new int[n][n];
        num = n;
        DFS(n);
        return answer;
    }
}
```

2차원 배열 체스판을 만든 뒤 0,0부터 퀸을 놓고 같은 열, 행, 대각선의 값에 1을 더해줬고 다음 행에서는 값이 0인 좌표에 퀸을 놓는 식으로 백트레킹을 사용해서 답을 구했다.

### 다른사람의 풀이

```java
class Solution {
    private static int[] board;
    private static int answer;

    public static int solution(int n) {
        // 배열의 값은 해당 행의 queen이 있는 '열(column)'을 의미함
        board = new int[n];

        backTracking(0, n);

        return answer;
    }

    // depth는 행을 의미함
    private static void backTracking(int depth, int n) {
        if (depth == n) {
            answer++;
            return;
        }
        for (int i = 0; i < n; i++) {
            board[depth] = i; // 해당 depth(행)과 i(열)에 퀸을 놓을 수 있는지 확인
            if (valid(depth)) {
                backTracking(depth + 1, n);
            }
        }
    }

    private static boolean valid(int i) {
        for (int j = 0; j < i; j++) { // 마지막으로 놓여진 것과 이전의 것들을 비교
            if (board[i] == board[j]) return false;
            if (Math.abs(i - j) == Math.abs(board[i] - board[j])) return false;
        }
        return true;
    }
}
```

배열의 값을 해당 행의 열을 의미하게 해서 다음 행에 퀸을 넣었을 때 전의 퀸과 같은 열에 있는지 확인하고 기울기를 비교해서 서로 대각선상에 있는지 확인합니다. 이렇게하면 2차원 배열을 쓰지않고도 답을 구할 수 있습니다.