# 567. Permutation in String

This is also 'sliding window' problem.

There is a fixed length of window which is length of s1.

We are going to move this 'fixed' window to right one index at a time.

```
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        s1_dict = {}
        count_dict = {}
        n = len(s1)

        for char in s1:
            if char not in s1_dict:
                s1_dict[char] = 1
            else:
                s1_dict[char] += 1

        for i in range(len(s2)-n+1):
            for char in s2[i:i+n]:
                if char not in count_dict:
                    count_dict[char] = 1
                else:
                    count_dict[char] += 1

            if count_dict == s1_dict:
                return True
            count_dict = {}

        return False
```

This code works but the time complexity is worse than I expected...

3000 ~ 5500ms

Maybe I can change the method which resets the 'count_dict'.

```
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        s1_dict = {}
        count_dict = {}
        n = len(s1)

        # initialize s1 dict
        for char in s1:
            if char not in s1_dict:
                s1_dict[char] = 1
            else:
                s1_dict[char] += 1

        # initialize count dict
        for char in s2[:n]:
            if char not in count_dict:
                count_dict[char] = 1
            else:
                count_dict[char] += 1

        # check if the first guess is right
        if count_dict == s1_dict:
            return True

        # otherwise, go through the s2
        # basically, erase the old char from count_dict and add new char to count_dict
        for i in range(n,len(s2)):
            if count_dict[s2[i-n]] > 1:
                count_dict[s2[i-n]] -= 1
            else:
                del count_dict[s2[i-n]]
            if s2[i] not in count_dict:
                count_dict[s2[i]] = 1
            else:
                count_dict[s2[i]] += 1

            if count_dict == s1_dict:
                return True

        return False
```

This works perfectly.

80-90ms.

```
Complexity Analysis.

Time Complexity: O(l1+(l2-l1)). Where l1 is the length of string s1 and l2 is the length of string s2.

Space complexity: O(1). Constant Space is used. -> alphabet 26 letters.
```
