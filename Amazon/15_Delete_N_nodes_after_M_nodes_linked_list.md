# 15. Delete N nodes after M nodes of a linked list
## GFG(Geeks For Geeks)
### Prompt:
Given a linked list, delete N nodes after skipping M nodes of a linked list until the last of the linked list.

```java
class Solution
{
    static void linkdelete(Node head, int M, int N)
    {
        // your code here
        int n=1,m=N;
       Node tem=head;
       while(tem!=null){
           if(n==M){
               Node p=tem;
               while(p!=null&&m-->0){
                   p=p.next;
               }
               if(p!=null)
               tem.next=p.next;
               else tem.next=p;
               n=0;
               m=N;
           }
           n++;
           tem=tem.next;
       }
    }
}

```
