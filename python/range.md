# range(a,b) / *(spread operator)

---------------------------------------------
- range(a,b)는 a<= < b   
b까지 포함시키려면 range(a, b+1)
  
-----------------------------------------------
- *(spread operator)
배열, 문자열, 객체 등 반복 가능한 객체 (Iterable Object)를 개별 요소로 분리할 수 있음


    sorted_list = sorted([a, b]) # a, b를 소트
    sorted_list[-1] += 1    # 마지막 인덱스(큰 수)에 +1(a<= <=b로 만들어줌) 
    sum(range(*sorted_list)) # *를 사용하여 값을 분리하고 sum으로 range의 값을 합산


