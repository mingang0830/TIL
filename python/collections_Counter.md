# from collections import Counter : 빈도 수, 최빈값 구하기

------------------------------------------------------
* 빈도 수를 구하는 함수
    

    from collections import Counter

    numbers = [1, 2, 3, 3, 4, 4, 4, 5, 5]
    cnt = Counter(numbers)
    cnt.most_common() # 등장한 횟수를 내림차순으로 튜플형식으로 보여줌
    # [(4, 3), (3, 2), (5, 2), (1, 1), (2, 1)]



* 최빈값을 구하는 함수


    from collections import Counter

    def highest_rank(arr):
        c = Counter(arr)
        m = c.most_common(1) # 최빈값 # 만약 상위 3개를 원하면(3)
        return m[0][0] # 튜플 형식으로 받기 때문에 튜플 안의 제일 첫번째 튜플 중 첫번째 값을 return