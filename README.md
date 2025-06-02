# LeetCodeNote

# Merge Two Sorted Lists - 精簡筆記（Q&A 式）

```csharp
public class Solution {
    public ListNode MergeTwoLists(ListNode list1, ListNode list2) {
        ListNode ans = new ListNode(0);
        ListNode temp = ans;
        while( list1!= null && list2 != null ){
            if(list1.val < list2.val){
                ans.next = list1;
                list1 = list1.next;
            }
            else{
                ans.next = list2;
                list2 = list2.next;
            }
            ans = ans.next;
        }

        if ( list1 != null ){
            ans.next = list1;
        }
        if ( list2 != null ){
            ans.next = list2;
        }

        return temp.next;
    }
}
```

---

## Q1. `ListNode ans = new ListNode(0); ListNode temp = ans;` 是什麼意思？
- 兩個變數一開始指向同一記憶體位址。
- 建立 dummy 節點（ans）並用 temp 保留源頭Node。
- Linked List 是單向的，不能回頭。
- 若指標移動後沒保留開頭參考，就找不到起點 → 回傳錯誤或 null。

---

## Q2. `return ans.next` 為什麼會回傳整串？
因為每個節點都記得「下一個」，從第一個節點開始一路串下去就是整串。

---

## Q3. `ListNode ans = new ListNode(0);` 和 `ListNode temp = new ListNode(0);` 有什麼差別？
- `ans` + `temp = ans`：保留起點，temp 負責移動與串接。
- 單獨 `temp = new ListNode(0);`：沒有保留頭節點，無法回傳整串。

---
