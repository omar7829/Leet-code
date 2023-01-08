# Leet-code
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
        
