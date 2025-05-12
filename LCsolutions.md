<details>
<summary> <h2>Arrays & Hashing</h2> </summary>
    
### [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)<a name="contains-duplicate"></a>
    
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

### [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)<a name="valid-palindrome"></a>

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

### [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)<a name = "best-time-to-buy-and-sell-stock"></a>

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