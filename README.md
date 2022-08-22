# leetcode-11-array-two-pointers

1） bruce force：

      class Solution:
          def maxArea(self, height: List[int]) -> int:
              maxArea = 0
              minHeight = height[0]
              for i in range(len(height)-1):
                  for j in range(i+1,len(height)):
                      minHeight = min(height[i], height[j])
                      area = (j-i) * minHeight
                      maxArea = max(maxArea, area)
                      # print(area)
              return maxArea
              
2）two pointers

      class Solution:
          def maxArea(self, height: List[int]) -> int:
              maxArea = 0
              l = 0
              r = len(height) - 1
              while l < r:
                  area = (r-l) * min(height[l], height[r])
                  maxArea = max(maxArea, area)
                  # normal situation, only type the equation

                  if height[l] < height[r]:
                      l += 1
                  elif height[l] > height[r]:
                      r -=1
                  # narrow down to find a higher height, from both sides
                  else:
                      r +=1
                  # if l = r, u can choose either side to narrow, this one could also be l += 1
              return maxArea
