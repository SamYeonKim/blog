---
title: Top K Frequent Elements
tags: [LeetCode, Java]
categories : [LeetCode]
toc: true
toc_sticky: true
author_profile: false
classes: wideleft
---

# Problem

Given a non-empty array of integers, return the k most frequent elements.

## Example 1

```swift
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

## Example 2

```swift
Input: nums = [1], k = 1
Output: [1]
```

## Note

* You may assume `k` is always valid, $$1 \le k \le$$ number of unique elements.
* Your algorithm's time complexity **must be** better than O(n log n), where n is the array's size.

# My Answer

* `nums`를 정렬하자.
* `nums`를 순회하면서, 마지막 확인 했던 값과 다른값이거나 마지막 값일 경우에 결과리스트에 어떻게 넣을지 확인하자.
* 너무 복잡하다. 좀 더 간단하게 풀어야 한다.

```java
class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        HashMap<Integer, Integer> hashmap = new HashMap<>();
        List<Integer> result = new ArrayList<>();
        
        Arrays.sort(nums);
        
        int last_checked_number = nums[0];
            
        for(int idx=0; idx < nums.length; idx++) {
            int n = nums[idx];
            
            hashmap.put(n, hashmap.getOrDefault(n, 0) + 1);                
            
            if ( last_checked_number != n || idx == nums.length-1) {
                int size = result.size();                                
                
                int frequent = hashmap.get(last_checked_number);

                int target_idx=-1;
                for(int i = size-1; i>= 0; i--) {
                    int prev_freqent = hashmap.get(result.get(i));

                    if ( prev_freqent > frequent )
                        break;

                    target_idx = i;
                }

                if ( target_idx >= 0 ) {
                    result.add(target_idx, last_checked_number);
                } else if ( size < k ) {
                    result.add(last_checked_number);
                }
                last_checked_number = n;                
            }            
        }
        
        if ( result.size() < k )  {
            result.add(last_checked_number);
        }

        return result.subList(0, k);
    }
}
```

