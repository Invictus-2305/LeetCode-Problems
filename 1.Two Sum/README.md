### Introduction
The problem at hand is to find two numbers in an array that add up to a given target. We're required to return the indices of these two numbers. We can assume that there's exactly one solution for each input, and we can't use the same element twice.

### Approach
We can solve this efficiently using a hashmap. We'll iterate through the array, keeping track of each number's index as we go. While iterating, we check if the complement of the current number (i.e., target - current number) exists in the hashmap. If it does, it means we've found the two numbers that sum up to the target. We return the indices of the current number and its complement from the hashmap.

### Python Code
```python
index_mapping = {}

for idx, number in enumerate(nums):
    if target - number in index_mapping:
        return index_mapping[target - number], idx
    index_mapping[number] = idx
```

### C++ Code
```c++
vector<int> twoSum(vector<int>& nums, int target) {
    unordered_map<int, int> index_mapping;
    for (int idx = 0; idx < nums.size(); ++idx) {
        if (const auto it = index_mapping.find(target - nums[idx]);
            it != index_mapping.cend())
            return {it->second, idx};
        index_mapping[nums[idx]] = idx;
    }
    throw;
}
```

### Java Code
```java
Map<Integer, Integer> indexMapping = new HashMap<>();

for (int idx = 0; idx < nums.length; ++idx) {
  if (indexMapping.containsKey(target - nums[idx]))
    return new int[] {indexMapping.get(target - nums[idx]), idx};
  indexMapping.put(nums[idx], idx);
}

throw new IllegalArgumentException();
```

### Time Complexity
- The time complexity of this approach is O(n), where n is the number of elements in the array.
  - The loop through the array takes O(n) time.
  - Each lookup and insertion in the hashmap takes O(1) time on average.
- Thus, the overall time complexity is dominated by the linear iteration through the array.
