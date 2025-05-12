<details>
<summary><h1> Arrays & Hashing </h1></summary>
    
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
