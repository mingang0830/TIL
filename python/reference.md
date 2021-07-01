# 10까지 중 짝수만 골라 합산
    result = 0
    for i in range(1, 11):
      if i % 2 == 0:
        result += i
    print("sum of even:", result)  # sum of even: 30
# 10까지 중 짝수만 골라 합산, 함께 골라 합산
    sum = 0
    even_sum = 0
    for i in range(1, 11):
      if i % 2 == 0:
        even_sum += i
      sum += i
    print("sum of all: ", sum, " sum of even: ", even_sum)  # sum of all:  55  sum of even:  30
# 10에서 짝 홀수를 따로 담기
    odd = []
    even = []
    for i in range(1, 11):
      if i % 2 == 0:
        even.append(i)
      else:
        odd.append(i)
    print("list of odd: ", odd, " list of even: ",even)
    # list of odd:  [1, 3, 5, 7, 9]  list of even:  [2, 4, 6, 8, 10]

# 2차원 배열 아무것도 안담고 생성(3x3)
    result = []
    for i in range(3):
      inner = []
      for j in range(3):
        inner.append([])
      result.append(inner)
    print("empty lists of second-demension: ", result)
    # empty lists of second-demension:  [[[], [], []], [[], [], []], [[], [], []]]
# 3차원 배열 아무것도 암담고 생성 (3x3x3)
    result = []
    for i in range(3):
      second_dimension = []
      for j in range(3):
        third_dimension = []
        for k in range(3):
          third_dimension.append([])
        second_dimension.append(third_dimension)
      result.append(second_dimension)
    print("empty lists of third-demension: ", result)
    # empty lists of third-demension:  [[[[], [], []], [[], [], []], [[], [], []]], [[[], [], []], [[], [], []], [[], [], []]], [[[], [], []], [[], [], []], [[], [], []]]]
# 함수에서 2개 반환하기
    def return_multiple():
      return 10, "ok"
    print("return 2 values from function: ", return_multiple())
    # return 2 values from function:  (10, 'ok')
# 함수에서 3개 반환하기
    def return_three():
      return 1, "a", []
    print("return 3 values from function: ", return_three())
    # return 3 values from function:  (1, 'a', [])
# 함수에서 유동적으로 parameter 받아 처리하기
    def get_mutiple_params(**kwargs):
      print(kwargs.get('a'))
      print(kwargs.get('b'))
      print(kwargs.get('c', "default value!"))
    print("get any values from parameter: ", get_mutiple_params(a=10, b=2))  # Q: 왜 마지막 출력이 None일까? : 리턴값이 없어서
    #10
    #2
    #default value!
    #get any values from parameter:  None
# dict 순회하여 원하는 value 찾기
    for k, v in {"a": 1, "b": 2, "c": 3}.items():
      if v == 2:
        print("key of value 2: ", k)
        # key of value 2:  b
# dict 키 중 짝수만 골라 key list 구성하기
    result = []
    for key in {1: "a", 2: "b", 3: "c", 4: "d"}:   # 왜 key만 쓸수 있을까 :딕셔너리 내부에 있는 키만 for문의 변수에 들어가기 때문에//dict는 iterate 돌면 key를 반환하도록 구현되어 있음
      if key % 2 == 0:
        result.append(key)
    print("key of only even: ", result)
    # key of only even:  [2, 4]
# list의 index 값의 합과 짝수 list를 구하기
    result = 0
    even = []
    for idx, i in enumerate(range(1, 101)):
      result += idx
      if i % 2 == 0:
        even.append(i)
    print("sum of index: ", result, " list of even: ", even)
    # sum of index:  4950  list of even:  [2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42, 44, 46, 48, 50, 52, 54, 56, 58, 60, 62, 64, 66, 68, 70, 72, 74, 76, 78, 80, 82, 84, 86, 88, 90, 92, 94, 96, 98, 100]
# if-elif-else 대신 dict 활용하기
    input = "b"
    print("get value by input: ", {"a": 1, "b": 2, "c": 3}.get(input))
    # get value by input:  2
# if-elif-else 대신 dict 활용하여 function 호출하기
    def attack():
      return "attack"
    def defense():
      return "defense"
    def ignore():
      return "ignore"
    input = "a"
    print("call func by input: ", {"a": attack, "d": defense, "i": ignore}.get(input)())
    # call func by input:  attack