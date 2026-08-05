# Linked List方法论

## 快慢指针
- 检测环
- 找中间节点
- 找倒数第k个节点（让快指针先走k步，当快指针走到None时，慢指针正好是倒数第k个节点）

## 反转链表
- 头插法
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        pre = None
        p = head
        while p is not None:
            temp = p.next
            p.next = pre
            pre = p
            p = temp
        return pre
```

## 创建虚拟的头节点(dummy node)
- 避免因为改变head而导致返回错误
```Python
def question(head):
    h = ListNode(-1)
    h.next = head
    p = h.next
    # tracing through p
```

## 链表的拼接和断开
- 在处理尾指针时，要注意最后指向None
- 在拼接时，如果被删除的Node后面还需要使用，新建一个temp_node保存被删除的node
- 在操作链表时，一定要小心节点的顺序。因为链表的每个节点都只知道“下一个节点”，如果你在修改 next 的时候顺序弄错，就可能：
  - 丢失节点 —— 指针改了，后面的节点就找不到了。
  - 形成环 —— 指针指回前面，链表永远走不完。


## 增加/删除节点
- 在增加或者删除节点时，需要找到增加/删除节点的前一个节点，并把它和要增加和删除节点的后一个相连


