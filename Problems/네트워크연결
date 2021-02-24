# 네트워크 연결 

크루스칼 알고리즘을 이용해 푸는 문제이다.
크루스칼 알고리즘이란, 탐욕적인 방법을 이용하여 네트워크의 모든 정점을 최소 비용으로 연결하여 최적 해답을 구하는 것이다.
1) 최소 비용의 간선으로 구성됨
2) 사이클을 포함하지 않음


## Kruskal 알고리즘의 동작 

```
1. 그래프의 간선들을 가중치의 오름차순으로 정렬한다. 
2. 정렬된 간선 리스트에서순서대로 사이클을 형성하지 않는 간선을 선택한다.
3. 해당 간선을 현재의 MST(최소 비용 신장 트리)의 집합에 추가한다.
![](https://gmlwjd9405.github.io/images/algorithm-mst/kruskal-example2.png)

```

## 소스코드

```
import sys
input = sys.stdin.readline
def find(x):
    if check[x]==x:
        return x
    check[x]=find(check[x])
    return check[x]

n = int(input())
m = int(input())
arr = [list(map(int, input().split())) for _ in range(m)]
arr = sorted(arr, key=lambda x:x[2])
check = [i for i in range(0, n+2)]
ans = 0

for a in arr:
    x, y, w = a
    if find(x)==find(y):
        continue
    else:
        ans+=w
        x, y = find(x), find(y)
        check[x]=y
print(ans)
```

## References 

[1] 크루스칼 알고리즘 (https://gmlwjd9405.github.io/2018/08/29/algorithm-kruskal-mst.html)
