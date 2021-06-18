# 특정 문자 찾기

---------------------

* find(찾을 문자, 찾기 시작할 위치)
    * find는 문자열중 특정 문자를 찾고 위치를 반환
    * 찾는 문자가 없을 경우 -1 리턴
  

    s = '가나다라 마바사아 자차카타 파하'
    
    s.find('가')
    # 0
    s.find('마')
    # 5
    s.find('가', 5)
    # -1


* startswith(시작하는 문자, 시작 지점)
    * startswith는 문자열이 특정 문자로 시작하는지 여부를 알려줌
    * True 나 False 를 반환
    

    s = '가나다라 마바사아 자차카타 파하'
    
    s.startswith('가')
    # True
    s.startswith('나')
    # False
    s.startswith('나', s.find('나'))
    #True


* endswith(끝나는 문자, 문자열의 시작, 문자열의 끝)
    * endswith는 문자열이 특정 문자로 끝나는지 여부를 알려줌
    * True 나 False 를 반환
    
    
    s = '가나다라 마바사아 자차카타 파하'
    
    s.endswith('하')
    # True
    s.endswith('마')
    # False
    s.endswith('마', 0, 6) # 마의 위치값 + 1 / 문자열 시작 <=  < 문자열 끝
    # True