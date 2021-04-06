## 오르막 수

끝에 오는 수에 대한 DP 표를 작성하면 규칙을 알 수 있다.
<img src= "https://blog.kakaocdn.net/dn/mrzbe/btq10RnvIXi/kjuQ721pgibKsrXYq0Ittk/img.jpg">

위와 같이 num[i] += num[i-1] 이라는 규칙이 보인다.

따라서 끝까지 적용해주면 된다.

```
n = int(input()) 
num = [1]*10 

for i in range(n-1): 
  for j in range(1, 10): 
    num[j] += num[j-1] 

print(sum(num)%10007)

```
