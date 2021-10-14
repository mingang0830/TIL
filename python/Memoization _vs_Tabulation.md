# Memoization vs Tabulation

----------------------------------------------------

## memoization 방식과 tabulation 방식으로 피보나치 수열 구현하기

* ### memoization : Top-Down 접근
~~~
def fib_memo(n, cache):
    if n < 3:
        return 1
        
    # 이미 n번째 피보나치를 계산했으면:
    # 저장된 값을 바로 리턴한다
    if n in cache:
        return cache[n]
    
    # 아직 n번째 피보나치 수를 계산하지 않았으면:
    # 계산을 한 후 cache에 저장
    cache[n] = fib_memo(n - 1, cache) + fib_memo(n - 2, cache)

    # 계산한 값을 리턴한다
    return cache[n]



def fib(n):
    # n번째 피보나치 수를 담는 사전
    fib_cache = {}

    return fib_memo(n, fib_cache)
~~~

* ### tabulation : Botton-Up 접근
~~~
def fib_tab(n):
    # 이미 계산된 피보나치 수를 담는 리스트
    fib_table = [0, 1, 1]

    # n번째 피보나치 수까지 리스트를 하나씩 채워 나간다
    for i in range(3, n + 1):
        fib_table.append(fib_table[i - 1] + fib_table[i - 2])

    # 피보나치 n번째 수를 리턴한다
    return fib_table[n]
~~~

* ### memoization과 tabulation의 공통점
  - 둘 다 중복되는 부분 문제의 비효율을 해결
<br>
* ### memoization과 tabulation의 차이점
  * 일반적으로 memoization은 재귀, tabulation은 반복문을 사용
  
 
