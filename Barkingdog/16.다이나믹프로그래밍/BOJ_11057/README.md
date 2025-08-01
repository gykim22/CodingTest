# 백준 11057번 - 오르막 수

[문제 보러 가기](https://www.acmicpc.net/problem/11057)

## 요약

- 오르막 수는 수의 자리가 오름차순을 이루는 수를 말한다. 이때, 인접한 수가 같아도 오름차순으로 친다.
- 2234와 3678, 11119는 오르막 수이지만, 2232, 3676, 91111은 오르막 수가 아니다.
- 수의 길이 N이 주어졌을 때, 오르막 수의 개수를 구하는 프로그램을 작성, 수는 0으로 시작할 수 있다.

## 핵심 규칙

- 첫째 줄에 N (1 ≤ N ≤ 1,000)이 주어진다.
- 첫째 줄에 길이가 N인 오르막 수의 개수를 10,007로 나눈 나머지를 출력한다.

## 예제 입출력

입력 및 출력 예시는 [문제 링크](https://www.acmicpc.net/problem/11057) 참고.

### 문제풀이

`1. 관찰`

- N이 1인 경우, 0 ~ 9까지 총 10개의 오르막 수가 있을 수 있다.
- N이 2인 경우, 0으로 시작하면 10개의 오르막 수, 1으로 시작하면 9개의 오르막 수 ... 9로 시작하면 1개의 오르막 수가 가능하여 총 55개가 가능하다.
- N이 3인 경우, ...

dp[i][j]는 N = i일때, j로 끝나는 수의 개수이다.

즉, dp[0][0 ~ 9] = 1과 동일하다.

dp[1][j]는 j가 0이면 1씩 증가하는 식으로 처리한다.

즉, dp[2][0] = dp[1][0] = 1, dp[2][1] = dp[1][0] + dp[1][1] = 2 ...  
dp[i][j] = sum(dp[i-1][:j+1])