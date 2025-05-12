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