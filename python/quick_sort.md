# 퀵 정렬

--------------------------
~~~
# 두 요소의 위치를 바꿔주는 함수
def swap_elements(my_list, index1, index2):
    my_list[index1],my_list[index2] = my_list[index2],my_list[index1]
    return my_list

# 퀵 정렬에서 사용되는 파티션 함수
def partition(my_list, start, end):
    b = start
    for i in range(start, end):
        if my_list[i] < my_list[end]:
            swap_elements(my_list, i, b)
            b += 1
    swap_elements(my_list, b, end)
    return b

# 퀵 정렬    
def quicksort(my_list, start=0, end=None):
    if end == None:
        end = len(my_list) - 1

    # base case
    if end - start < 1:
        return

    # my_list를 두 부분으로 나누어주고,
    # partition 이후 pivot의 인덱스를 리턴받는다
    pivot = partition(my_list, start, end)

    # pivot의 왼쪽 부분 정렬
    quicksort(my_list, start, pivot - 1)

    # pivot의 오른쪽 부분 정렬
    quicksort(my_list, pivot + 1, end)
~~