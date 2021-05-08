# Documenting my first ever code on linked list insertion and deletion operations using Python


```
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None
        
    def insertAtEnd(self, data):
        h = self.head
        if h is None:
            temp = Node(data)
            self.head = temp
        else:
            while h.next != None:
                h = h.next
            temp = Node(data)
            h.next = temp
    
    def insertAtBeginning(self, data):
        h = self.head
        temp = Node(data)
        temp.next = h
        self.head = temp
    
    def displayList(self):
        h = self.head 
        while h is not None: 
            print (h.data, end = " -> ")
            h = h.next
        print("None")
        
    def insertAfter(self, insertAfter, data):
        h = self.head
        while h != None and h.data != insertAfter:
            h = h.next
        if h is None:
            print('{} is not present in list'.format(insertAfter))
        else:
            temp = Node(data)
            temp.next = h.next
            h.next = temp
    def getNthDataNode(self, n):
        h = self.head
        N = 0
        while h!= None:
            h = h.next
            N += 1
        if N == 0:
            print('List is Empty')
        else:
            if n > N:
                print('out of bounds')
            else:
                p = self.head
                for i in range(n - 1):
                    p = p.next
                print('Node at position {} is {}'.format(n, p.data))
            
    def deleteAtEnd(self):
        h = self.head
        if h is None:
            print('Empty List, cannot delete')
        else:
            count = 0
            while h.next != None:
                h = h.next
                count += 1
            h = self.head
            for i in range(count - 1):
                h = h.next
            h.next = None
            
    def deleteAtStart(self):
        h = self.head
        if h is None:
            print('Empty List, cannot delete')
        else:
            self.head = h.next
            
    def deleteAfter(self, key):
        h = self.head
        if h is None:
            print('Empty List, cannot delete')
        else:
            previousNode = 0
            while h != None and h.data != key:
                h = h.next
            if h is None:
                print('{} not found in the list'.format(key))
            else:
                previousNode = h
                if previousNode.next is None:
                    print('the list terminates at {}'.format(key))
                else:
                    h = h.next
                    previousNode.next = h.next
            
    def deleteBefore(self, key):
        h = self.head
        if h is Node:
            print('Empty List, cannot delete')
        elif h.data == key:
            print('No element found before {}'.format(key))
        else:
            jumps = 0
            previousNode = 0
            while h != None and h.data != key:
                h = h.next
                jumps += 1
            if h is None:
                print('{} not found in the list'.format(key))
            else:
                p = self.head
                if jumps == 1:
                    self.head = p.next
                else:
                    for i in range(jumps - 2):
                        p = p.next
                    previousNode = p
                    p = p.next
                    previousNode.next = p.next


if __name__ == '__main__':
    myList = LinkedList()
    myList.displayList()
    
    myList.insertAtEnd(1)
    myList.displayList()
    
    myList.insertAtEnd(2)
    myList.displayList()
    
    myList.insertAtBeginning(3)
    myList.displayList()
    
    myList.insertAtBeginning(4)
    myList.displayList()
    
    myList.insertAtBeginning(5)
    myList.displayList()
    
    myList.insertAtEnd(6)
    myList.displayList()
    
    myList.insertAfter(6, 7)
    myList.displayList()
    
    myList.getNthDataNode(4)
    
    myList.deleteAtEnd()
    myList.displayList()
    
    myList.deleteAfter(1)
    myList.displayList()
    
    myList.deleteBefore(1)
    myList.displayList()
```
### Output:

```
None
1 -> None
1 -> 2 -> None
3 -> 1 -> 2 -> None
4 -> 3 -> 1 -> 2 -> None
5 -> 4 -> 3 -> 1 -> 2 -> None
5 -> 4 -> 3 -> 1 -> 2 -> 6 -> None
5 -> 4 -> 3 -> 1 -> 2 -> 6 -> 7 -> None
Node at position 4 is 1
5 -> 4 -> 3 -> 1 -> 2 -> 6 -> None
5 -> 4 -> 3 -> 1 -> 6 -> None
5 -> 4 -> 1 -> 6 -> None
```
