# Литкоды
## Первая задача
###  Add Two Numbers
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

```python3
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        n = True
        newl1 = ''
        newl2 = ''
        while n:
            if l1 != None and l2 != None:
                newl1 += str(l1.val)
                newl2 += str(l2.val)
                l1 = l1.next
                l2 = l2.next
            elif l2 != None and l1 == None:
                newl2 += str(l2.val)
                l2 = l2.next
            elif l1 != None and l2 == None:
                newl1 += str(l1.val)
                l1 = l1.next
            else:
                n = False
        nstr1 = newl1[::-1]
        nstr2 = newl2[::-1]
        num = str(int(nstr1) + int(nstr2))[::-1]
        head = ListNode(int(num[0]))
        current = head
        num = num[1:]
        for i in range(len(num)):
            current.next = ListNode(int(num[i]))
            current = current.next
        return head
```
![задача 1](https://github.com/Taymurazzzz/web_docs/blob/main/docs/assets/images/leet1.PNG?raw=true)
## Вторая задача
### Longest Substring Without Repeating Characters
Given a string *s*, find the length of the longest substring without duplicate characters.
```python3
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        n = True
        k = 0
        numlist = []
        strcounter = ''
        if len(s) == 0:
            return 0
        while n:
            if s[k] not in strcounter:
                strcounter += s[k]
                if k == len(s) - 1:
                    numlist.append(len(strcounter))
                    n = False
                k += 1
            else:
                k = s.find(s[k]) + 1
                s = s[k:]
                k = 0
                numlist.append(len(strcounter))
                strcounter = ''
        if len(numlist) == 0:
            return 0
        else:
            return max(numlist)
```
![задача 2](https://github.com/Taymurazzzz/web_docs/blob/main/docs/assets/images/leet2.PNG?raw=true)
