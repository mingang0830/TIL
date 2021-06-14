# 리스트 값들의 길이에 따라서 정렬하기

---------------------------

* 오름차순 정렬


    def sort(list):
        list2 = sorted(list, key=len)
        return list2


    def sort(list):
        list.sort(key=len)
        return list


* 내림차순 정렬
  

    def sort(list):
        list2 = sorted(list, key=len, reverse=True)
        return list2


    def sort(list):
        list.sort(key=len, reverse=True)
        return list