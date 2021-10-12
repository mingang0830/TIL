# 딕셔너리 정렬하기

--------------------------------
* ## key를 기준으로 오름차순 정렬
~~~
dict = {'가': 3, 'A': 1, 'a': 2}

sort_dict = sorted(dict.keys())
print(sort_dict)

# 실행결과
['A', 'a', '가']
~~~

* ## key를 기준으로 내림차순 정렬
~~~
dict = {'가': 3, 'A': 1, 'a': 2}

sort_dict = sorted(dict.keys(), reverse=True)
print(sort_dict)

# 실행결과
['가', 'a', 'A']
~~~

* ## value를 기준으로 오름차순 정렬
~~~
dict = {'가': 3, 'A': 1, 'a': 2}

sort_dict = sorted(dict.values())
print(sort_dict)

# 실행결과
[1, 2, 3]
~~~

* ## value를 기준으로 내림차순 정렬
~~~
dict = {'가': 3, 'A': 1, 'a': 2}

sort_dict = sorted(dict.values(), reverse=True)
print(sort_dict)

# 실행결과
[3, 2, 1]
~~~



