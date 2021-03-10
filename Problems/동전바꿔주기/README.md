# 동전 바꿔주기

```
[입력]
첫째 줄에는 지폐의 금액 T(0＜T ≤ 10,000), 둘째 줄에는 동전의 가지 수 k(0＜k ≤ 100), 셋째 줄부터 마지막 줄까지는 각 줄에 동전의 금액 pi(0＜pi ≤ T)와 개수 ni(0＜ni ≤ 1,000)가 주어진다. pi와 ni사이에는 빈칸이 하나씩 있다.
```
```
[출력]
첫째 줄에 동전 교환 방법의 가지 수를 출력한다. 방법이 없을 때는 0을 출력한다.
```


## 소스코드

```
T=int(input())
k=int(input())
L=[[0,0]] 
for i in range(k):
    L.append(list(map(int,input().split())))
L.sort()
dp=[[0]*(T+1) for _ in range(k+1)]
for i in range(k+1):
    dp[i][0]=1

for i in range(1,k+1): #동전종류 1,5,10
    for num in range(L[i][1]+1): #종류별 갯수
        for j in range(T+1): #지폐 금액
            temp=j+num*L[i][0] 
            if temp==0:
                continue
            if temp<T+1:
                dp[i][temp]+=dp[i-1][j]
            else:
                break

print(dp[k][T])

```

