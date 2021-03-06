# Data-Structures
---
## Sorting Algorithms - time complexity

| Algorithm| Best|Average|Worst|
|:---------|:----|:----|:----|
|Selection Sort| O(n^2)|O(n^2)|O(n^2)|
|Bubble Sort| O(n) |O(n^2) | O(n^2)|
|Insertion Sort| O(n) |O(n^2) | O(n^2)|
|Heap Sort| O(nlog(n)) |O(n(log(n)) | O(nlog(n))|
|Quick Sort| O(nlog(n)) |O(n(log(n)) | O(n^2)|
|Merge Sort| O(n(log(n)) |O(n(log(n)) | O(n(log(n))|
|Bucket Sort| O(n+k) |O(n+k) | O(n^2)|
|Radix sort| O(nk)| O(nk) | O(nk)|

### Bubble Sort
---
```python
def bubble_sort(arr):
    n=len(arr)
    for i in range(n):
        swapped=False
        for j in range(n-i-1):
            if arr[j]>arr[j+1]:
                arr[j],arr[j+1]=arr[j+1],arr[j]
                swapped=True
        if swapped==False:
            break

arr=[8,9,1,2,3,10]
bubble_sort(arr)
print(arr)
```
> Best case Time Complexity is O(n) -- occurs when the array already sorted <br />
> Worst Case Time complexity is O(n^2)  -- occures when the array is reverse sorted

### Insertion sort
---
```python
def insertion_sort(arr):
    for i in range(1,len(arr)):
        key=arr[i]
        j=i-1
        while j>=0 and key<arr[j]:
            arr[j+1]=arr[j]
            j-=1
        arr[j+1]=key
    
arr=[5,1,4,2,8]
insertion_sort(arr)
print(arr)
```
### Merge Sort

``` python
def mergeSort(arr):
    if len(arr)>1:
        mid=len(arr)//2
        L=arr[:mid]
        R=arr[mid:]
        
        mergeSort(L)
        mergeSort(R)
        
        i=k=j=0
        
        while i<len(L) and j<len(R):
            if L[i]<=R[j]:
                arr[k]=L[i]
                i+=1
            else:
                arr[k]=R[j]
                j+=1
            k+=1
        while i<len(L):
            arr[k]=L[i]
            i+=1
            k+=1
        
        while j<len(R):
            arr[k]=R[j]
            j+=1
            k+=1


arr=[15,8,9,10,2,5,3]

mergeSort(arr)
print(arr)
```
---

### reverse the words in a string
```python
x='jagadeeswar 300'
y=list(x)
y.reverse()
z=''.join(y)
print(z)
```
---

### reverse the string
```python
x='Hello, World!'
y=list(x)
y.reverse()
z=''.join(y)
print(z)
```
### Remove Consecutive Duplicates
For a given string(str), remove all the consecutive duplicate characters.
``` python
def removeConsecutiveDuplicates(string) :
   ans=string[0]
   seen=string[0]
   for x in string[1:]:
       if x != seen:
           ans+=x
           seen=x
   return ans

string = 'abcbbadd'

ans = removeConsecutiveDuplicates(string)

print(ans)
```
### reverse each word in a string
The task is to implement a function so as to print the sentence such that each word in the sentence is reversed.

```python
def reverseEachWord(string) :
    z=string.split(' ')
    ans=''
    for x in z:
       y=list(x)
       y.reverse()
       ans+=''.join(y)+' '
    return ans


string="Welcome to github"
ans=reverseEachWord(string)
print(ans)
```
---
### Binary Search
> worst case timecomplexity - log(n) and best case time complexity - O(1)
``` python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        length=len(nums)
        l=0
        r=length-1
        while l<=r:
            mid=(l+r)//2
            if nums[mid]==target:
                return mid
            elif target<nums[mid]:
                r=mid-1
            else:
                l=mid+1
        return -1
```
#### Bad version (using binary search)
>problem: You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which returns whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

explanation:
Input: n = 5, bad = 4
Output: 4
Explanation:
call isBadVersion(3) -> false
call isBadVersion(5) -> true
call isBadVersion(4) -> true
Then 4 is the first bad version.

```python
class Solution:
    def firstBadVersion(self, n):
        low=1
        high=n
        result=n
        while low<=high:
            mid=(low+high)//2
            
            if isBadVersion(mid):
                result=mid
                high=mid-1
            else:
                low=mid+1
        return result
 ```
