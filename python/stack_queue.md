# 스택과 큐 파이썬으로 구현

----------------------------------------

 ##  스택
~~~
class Stack:

    def __init__(self):
        self.lst = []

    def input(self, element):
        self.lst.append(element)

    def lifo(self):
        if len(self.lst) == 0:
            return 'List is empty'
        return self.lst.pop()

    def stack_find(self, index):
        if len(self.lst)-1 < index:
            return None
        if index == len(self.lst)-1:
            return self.lst.pop()
        del self.lst[-1]
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
            return self.lst.pop(0)
        del self.lst[0]
        return self.queue_find(index - 1) 