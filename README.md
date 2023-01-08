# Leet-code
#**Median of two sorted array(LEET CODE)**
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        a = nums1 + nums2
        a.sort()
        x=0
        y=0
        if len(a)%2==1:
            x = (len(a)//2)
            y = a[x]
        else:
            x = len(a)//2
            y = (a[x]+a[x-1])/2
        return y
        
-----------------------------------------------------------------------------------------------
        
**Longest Substring Without Repeating Characters**
    def lengthOfLongestSubstring(self, s):
        test = ""
        max_length = 0
        if len(s) == 0 or len(s) == 1:
            return len(s)
        
        for c in s:
            if c in test:
                test = test[test.index(c)+1:]
            test = test + c
            if max_length < len(test):
                max_length = len(test)
        return max_length
    
-----------------------------------------------------------------------------------------------        
        
**Add Two Numbers**
class Solution(object):
    def addTwoNumbers(self, l1, l2):
       head = None
       temp = None
       carry = 0
       while l1 is not None or l2 is not None:
          sum_value = carry
          if l1 is not None:
                sum_value += l1.val
                l1 = l1.next
          if l2 is not None:
                sum_value += l2.val
                l2 = l2.next
          node = ListNode(sum_value % 10)
          carry = sum_value // 10
          if temp is None:
                temp = head = node
          else:
                temp.next = node
                temp = temp.next
       if carry > 0:
            temp.next = ListNode(carry)
       return head
       
-----------------------------------------------------------------------------------------------  
       
**Two Sum**
from typing import List

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        result = []
        index_map = {}
        for i, n in enumerate(nums):
            difference = target - n
            if difference in index_map:
                result.append(i)
                result.append(index_map[difference])
                break
            else:
                index_map[n] = i
        return result

------------------------------------------------------------------------------------------------

**Palindrome Number**
class Solution:
    def isPalindrome(self, x: int) -> bool:
    # Base condition
        if x < 0:
            return False
    # Store the number in a variable
        number = x
    # This will store the reverse of the number
        reverse = 0
        while number:
            reverse = reverse * 10 + number % 10
            number //= 10
        return x == reverse

------------------------------------------------------------------------------------------------

**Roman to integer**
class Solution:
    def romanToInt(self, s: str) -> int:
        a=0
        for i in range(len(s)):
            if s[i]=='I':
                a=a+1
            elif s[i]=='V':
                a=a+5
            elif s[i]=='X':
                a=a+10
            elif s[i]=='L':
                a=a+50
            elif s[i]=='C':
                a=a+100
            elif s[i]=='D':
                a=a+500
            else:
                a=a+1000
        if 'IV' in s:
            a=a-2
        if 'IX' in s:
            a=a-2
        if 'XL' in s:
            a=a-20
        if 'XC' in s:
            a=a-20
        if 'CD' in s:
            a=a-200
        if 'CM' in s:
            a=a-200
        return a
        
----------------------------------------------------------------------------------------------------------------------------------

**MyAToi(string to integer)**
class Solution:
    def myAtoi(self, s: str) -> int:
        if not s:
            return 0
        n = len(s)
        if n == 0:
            return 0
        i = 0
        while s[i] == ' ':
            i += 1
            if i == n:
                return 0
        sign = -1 if s[i] == '-' else 1
        if s[i] in ['-', '+']:
            i += 1
        res, flag = 0, (2**31 - 1) // 10
        while i < n:
            if not s[i].isdigit():
                break
            c = int(s[i])
            if res > flag or (res == flag and c > 7):
                return 2**31 - 1 if sign > 0 else - (2**31)
            res = res * 10 + c
            i += 1
        return sign * res 
