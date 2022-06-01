# Given a string s, find the length of the longest substring without repeating characters.

So I am going to use sliding window method. It is basically move the range of answer until the end of the list.

I use 'left' and 'right' pointers.

'right' pointer moves one step at a time.

'left' pointer change its index to hashmap[s[right]]+1.

```
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        hashmap = {}
        left = 0
        maximum = 0

        for right in range(len(s)):
            if s[right] not in hashmap:
                hashmap[s[right]] = right
                maximum = max(maximum, right - left + 1)
            else:
                left = hashmap[s[right]] + 1
                hashmap[s[right]] = right
                maximum = max(maximum, right - left + 1)
        return maximum

```

The case s = "abba" is not working.


```
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        hashmap = {}
        left = 0
        maximum = 0

        for right in range(len(s)):
            if s[right] not in hashmap:
                hashmap[s[right]] = right
                maximum = max(maximum, right - left + 1)
            else:
                left = max(left, hashmap[s[right]] + 1)
                hashmap[s[right]] = right
                maximum = max(maximum, right - left + 1)
        return maximum

```

The 'left' pointer should be maximum of hashmap[s[right]] + 1 and itself.

It works!

```
Complexity Analysis

Time complexity : O(n).
Index 'right' will iterate n times.

Space complexity (HashMap) : O(min(m,n)).
We need O(k) space for checking a substring has no duplicate characters, where k is the size of the Set.
The size of the Set is upper bounded by the size of the string n and the size of the charset/alphabet m.
```
