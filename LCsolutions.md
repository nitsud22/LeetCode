<details>
<summary> <h2>Arrays & Hashing</h2> </summary>
    
### [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)
    
```python    
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        dict_a = {}

        for number in nums:
            if number not in dict_a:
                dict_a[number] = 1
            else:
                return True
        
        return False
```
</details>

<details>
<summary> <h2>Two Pointers</h2> </summary>

### [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        L = 0
        R = len(s) - 1

        while L < R:
            while L < R and s[L].isalnum() == False:
                L += 1
            while L < R and s[R].isalnum() == False:
                R -= 1
            if s[L].lower() == s[R].lower():
                L += 1
                R -= 1
            else:
                return False
        return True
```

</details>

<details>
<summary> <h2>Sliding Window</h2> </summary>

### [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        left = 0
        right = 1
        maxProfit = 0

        while right < len(prices):                          #right pointer is the one that iterates through the list
            if prices[left] < prices[right]:
                profit = prices[right] - prices[left]       #find the profit created if left pointer price is lower than right pointer price
                maxProfit = max(maxProfit, profit)          #chooses the bigger number as the max profit
            else:
                left = right                                #the right pointer is lower price than left, so new lowest price is found
            right += 1                                      #always increment the right pointer so it goes through array
        
        return maxProfit
```
</details>

<details>
<summary> <h2>Stack</h2></summary>

### [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)

```python
class Solution:
    def isValid(self, s: str) -> bool:
        dict_A = {')':'(','}':'{',']':'['}
        stack = []

        for char in s:                            
            if char not in dict_A:                      #if the character is not a key, add to stack
                stack.append(char)
            elif stack and stack[-1] == dict_A[char]:   #else if the stack is not empty and the top of the stack is a pair, pop from stack
                stack.pop()
            else:                                       #not in dict, stack is empty, or the top is not pair, return False
                return False
    
        
        if len(stack) == 0:
            return True
        else:
            return False
```

### Time Complexity

> O(n) — You only iterate through the string once.

### Space Complexity

> O(n) — Stack could store all opening brackets in the worst case.
</details> 

<details>
<summary> <h2>Binary Search</h2></summary>

### [Binary Search](https://leetcode.com/problems/binary-search/description/)

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        L = 0
        R = len(nums) - 1
        while L <= R:                                   #unitl both pointers converge and include the loop where both pointers are the same value
            M = (L + R) // 2
            if nums[M] == target:                       #each loop we want to check if it is the target num first, so we can skip the other lines of code if it is.
                return M
            elif nums[M] > target:                      #move right pointer if the checked middle value if greater than target num
                R = M - 1
            else:                                       #move left pointer if the checked middle is less than target num
                L = M + 1
        return -1

```

### Time Complexity

> O(logn) - You cut the possible iterations in half each loop

### Space Complexity

> O(1) - Uses 3 integers as extra space, L, M, R

</details> 

<details>
<summary> <h2>Linked List</h2></summary>

### [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/description/)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        curr = head
        prev = None

        while curr:
            temp = curr.next    #temp node set as the curr nodes next node to be used to traverse forward
            curr.next = prev    #curr node points to previous node, changing the direction of the list
            prev = curr         #prev node set as the current node
            curr = temp         #curr becomes the next node
            
        return prev   
```

I have a pretty tough time on linked lists