# 파티
N개의 숫자로 구분된 각각의 마을에 한 명의 학생이 살고 있다.
N명의 학생이 X번 마을에 모여서 파티를 벌이기로 했다.
마을 사이에는 총 M개의 단방향 도로들이 있고, i번째 길을 지나는데 T의 시간을 소비한다.
학생들이 각자 X번 마을에 오고 가는 최단시간 중, 가장 많은 시간이 소요되는 학생의 시간을 구하라.
```
[입력]
첫째줄에 N, M, X
두번째 줄부터 M+1번째 줄까지 i번째 도로의 시작점, 끝점, 소요시간
```
```
[출력]
n명의 학생들 중 오고 가는데 가장 오래 걸리는 학생의 소요시간
```

## [다익스트라 알고리즘](https://www.crocus.co.kr/546)
- 음의 가중치가 없는 그래프의 한 정점에서 모든 정점까지의 최단거리를 각각 구하는 알고리즘

- 벨만포드 알고리즘 : 특정 정점에 이르는 경로를 선택할 때 각 단계마다 경로 중에서 최솟값을 가지는 경로를 선택하는 알고리즘
- 플로이드 와샬 알고리즘 : 모든 최단 경로를 구하는 방법. 

## 풀이
max(1부터 n번째 마을 각각에서 x로 가기 위한 최소 시간 + x에서 1부터 n번째 각각의 마을로 가는 최소시간)
최소시간은 다익스트라알고리즘으로 구하면 된다.
오고, 가는 시간을 구해야하므로 다익스트라 알고리즘을 두 번씩 돌려주면 된다.

## 소스코드

```
import sys, heapq
INF = sys.maxsize
input = sys.stdin.readline

def di(x):
    hq = []
    heapq.heappush(hq, (0, x)) #처음 시간 0과 출발하는 곳인 x 힙큐 대입
    time = [INF]*(n+1)
    time[x] = 0
    while hq:
        t, b = heapq.heappop(hq)
        if time[b]<t: #작은 시간이므로 
            continue
        for now_t, now_b in doro[b]:
            t_t = t+now_t
            if time[now_b] > t_t: #now_b도시로 가기위한 최소값을 구하기 위해
                time[now_b] = t_t
                heapq.heappush(hq, (t_t, now_b))
    return time

n, m, x = map(int, input().split())
doro = [[] for _ in range(n+1)]

for _ in range(m):
    a, b, t = map(int, input().split())
    doro[a].append((t, b))

res = 0
for i in range(1, n+1):
    go = di(i)[x]
    back = di(x)[i]
    res = max(res, go+back)
print(res)

```


