# DAY_8
Odd Even Linked List &amp; Excel Sheet Column Number
# 🧠 Odd Even Linked List – Leetcode #328

This Java solution rearranges a singly linked list so that all nodes at odd indices come first, followed by all nodes at even indices. The relative order of nodes within each group is preserved.

---

## ✅ Problem Description

You are given the `head` of a singly linked list. Rearrange the list so that:

- All **odd-indexed** nodes come first,
- Followed by **even-indexed** nodes.

📝 **Note**: The index refers to the **position in the list**, not the value.

---

## 💡 Intuition

We can solve this problem in-place using **pointer manipulation**. The idea is to separate the list into two:
- One for **odd-positioned nodes**,
- One for **even-positioned nodes**.

Then connect the odd list to the even list at the end.

---

## 🔧 Approach

1. **Edge Case**: If the list has fewer than 3 nodes, return as-is.
2. Initialize:
   - `odd = head`
   - `even = head.next`
   - `temp = even` (to store the start of even list)
3. Traverse while `even` and `even.next` exist:
   - Link odd nodes together.
   - Link even nodes together.
   - Move both pointers forward.
4. Connect the tail of the odd list to the head of the even list.

---

## 📊 Visual Example

**Input:**

1 → 2 → 3 → 4 → 5

Odd: 1 → 3 → 5
Even: 2 → 4

1 → 3 → 5 → 2 → 4

---

## 🧪 Code (Java)

```java
class Solution {
    public ListNode oddEvenList(ListNode head) {
        if(head == null || head.next == null || head.next.next == null) {
            return head;
        }
        ListNode odd = head;
        ListNode even = head.next;
        ListNode temp = even;

        while(even != null && even.next != null) {
            odd.next = odd.next.next;
            even.next = even.next.next;
            odd = odd.next;
            even = even.next;
        }

        odd.next = temp;
        return head;
    }
}
🧠 Complexity
Type	Complexity
Time	O(n)
Space	O(1)





# 📊 Excel Sheet Column Number – Leetcode #171

This Java function converts a given Excel column title (like "A", "AB", or "ZY") into its corresponding column number.

---

## 🧠 Problem Description

Excel columns are labeled alphabetically:

A → 1
B → 2
C → 3
...
Z → 26
AA → 27
AB → 28
...
ZY → 701
ZZ → 702
AAA → 703


You're given a string representing a column title, and you must return its corresponding column number.

---

## 💡 Intuition

This is just like converting a number from **base-26** to decimal, where:
- `'A'` = 1
- `'B'` = 2
- ...
- `'Z'` = 26

Each character contributes its value times a power of 26 depending on its position in the string.

---

## 🔧 Approach

We process each character from left to right:

1. Initialize `result = 0`.
2. For each character `c` in the string:
   - Convert it to a number using `(c - 'A' + 1)`.
   - Multiply the current result by 26 (to shift digits left like base conversion).
   - Add the numeric value of `c` to the result.

This works exactly like converting from base-10 but using base-26.

---

## 🧪 Visual Example

**Input:**
"AB"



**Calculation:**
'A' = 1, 'B' = 2
Result = 1 * 26 + 2 = 28


---

## 🧾 Code (Java)

```java
class Solution {
    public int titleToNumber(String columnTitle) {
        int result = 0;
        for (char c : columnTitle.toCharArray()) {
            result = result * 26 + (c - 'A' + 1);
        }
        return result;
    }
}
📊 Complexity
Type	Complexity
Time	O(n)
Space	O(1)

Where n is the length of the column title string.
