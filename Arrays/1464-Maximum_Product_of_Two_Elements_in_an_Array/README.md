# 1464. Maximum Product of Two Elements in an Array

**LeetCode:** https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array/

## Intuition
Find the two largest numbers in the array and use them to calculate the answer.

## Approach
Traverse the array once while keeping track of the largest and second largest numbers. Then return `(max1 - 1) * (max2 - 1)`.

## Complexity
- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

## Code

```cpp []
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int maxi = INT_MIN;
        int secondMaxi = INT_MIN;

        for (int num : nums) {
            if (num > maxi) {
                secondMaxi = maxi;
                maxi = num;
            } else if (num > secondMaxi) {
                secondMaxi = num;
            }
        }

        return (maxi - 1) * (secondMaxi - 1);
    }
};
```

```java []
class Solution {
    public int maxProduct(int[] nums) {
        int max = Integer.MIN_VALUE;
        int secondMax = Integer.MIN_VALUE;

        for (int num : nums) {
            if (num > max) {
                secondMax = max;
                max = num;
            } else if (num > secondMax) {
                secondMax = num;
            }
        }

        return (max - 1) * (secondMax - 1);
    }
}
```

```python []
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        maxi = float("-inf")
        second_maxi = float("-inf")

        for num in nums:
            if num > maxi:
                second_maxi = maxi
                maxi = num
            elif num > second_maxi:
                second_maxi = num

        return (maxi - 1) * (second_maxi - 1)
```

```csharp []
public class Solution {
    public int MaxProduct(int[] nums) {
        int max = int.MinValue;
        int secondMax = int.MinValue;

        foreach (int num in nums) {
            if (num > max) {
                secondMax = max;
                max = num;
            } else if (num > secondMax) {
                secondMax = num;
            }
        }

        return (max - 1) * (secondMax - 1);
    }
}
```

```go []
import "math"

func maxProduct(nums []int) int {
	maxi := math.MinInt
	secondMaxi := math.MinInt

	for _, num := range nums {
		if num > maxi {
			secondMaxi = maxi
			maxi = num
		} else if num > secondMaxi {
			secondMaxi = num
		}
	}

	return (maxi - 1) * (secondMaxi - 1)
}
```
