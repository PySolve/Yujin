# 카드 구매하기

```
[입력]
첫째 줄에 민규가 구매하려고 하는 카드의 개수 N이 주어진다. (1 ≤ N ≤ 1,000)
둘째 줄에는 Pi가 P1부터 PN까지 순서대로 주어진다. (1 ≤ Pi ≤ 10,000)
```
```
[출력]
첫째 줄에 민규가 카드 N개를 갖기 위해 지불해야 하는 금액의 최댓값을 출력한다.
```


## 소스코드

```
n = int(input())
p = list(map(int, input().split())) 
dp = [0]*(n+1) 
for i in range(1, n+1):
  for j in range(1, i+1): 
    dp[i] = max(dp[i], dp[i-j]+p[j-1]) 
print(dp[n])

```

