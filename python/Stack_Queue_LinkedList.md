# 스택, 큐, 연결리스 파이썬으로 구현

----------------------------------------

 ##  스택
~~~
class Stack:

    def __init__(self):
        self.lst = []
        self.top = -1

    def input(self, element):
        self.lst.append(element)
        self.top += 1

    def lifo(self):
        if len(self.lst) == 0:
            return 'List is empty'
        result = self.lst.pop()
        self.top -= 1  # a -= 2  // a = a - 2
        return result

    def stack_find(self, index):
        if self.top < index:
            return None
        if index == self.top:
            return self.lifo()
        self.lifo()
        return self.stack_find(index)
~~~

## 큐
~~~
class Queue:
    def __init__(self):
        self.lst = []

    def input(self, element):
        self.lst.append(element)

    def fifo(self):
        if len(self.lst) == 0:
            return 'List is empty'
        return self.lst.pop(0)

    def queue_find(self, index):
        if len(self.lst) == 0:
            return None
        if index == 0:
            return self.fifo()
        self.fifo()
        return self.queue_find(index - 1)

~~~

## 연결 리스트
~~~
class Node:

    def __init__(self, data):
        self.data = data
        self.next = None


class LinkedList:

    def __init__(self):
        self.head = None
        self.tail = None

    def append(self, data):
        new_node = Node(data)

        if self.head is None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node

    def __str__(self):
        res_str = ""
        iterator = self.head
        while iterator is not None:
            res_str += f"{iterator.data} "
            iterator = iterator.next
        return res_str
~~~