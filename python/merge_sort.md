# 합병 정렬

----------------------------------
~~~
def merge(list1, list2):
    merged_list = []

    i = 0
    j = 0

    while i < len(list1) and j < len(list2):
        if list1[i] > list2[j]:
            merged_list.append(list2[j])
            j += 1
        else:
            merged_list.append(list1[i])
            i += 1   
    merged_list = merged_list + list1[i:] + list2[j:]
    return merged_list


# 합병 정렬
def merge_sort(my_list):
    mid = len(my_list) //2
    lst1 = my_list[:mid]
    lst2 = my_list[mid:]
    
    if len(my_list) < 2:
        return my_list
    else:
        return merge(merge_sort(lst1),merge_sort(lst2))
~~~