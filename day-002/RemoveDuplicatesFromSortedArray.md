# Remove Duplicates from Sorted Array

## 🎯 Problem Summary
Given a **sorted** array, remove duplicates **in-place** so each element appears only once. Return the number of unique elements.

---

## 💡 Approach: Two Pointer Technique

**Why Two Pointers?**
- Since the array is **sorted**, all duplicates are adjacent to each other.
- We use one pointer (`size`) to track where to place the next unique element.
- We scan through the array and only copy elements that are different from the last unique one.

---

## 🔑 Key Insight

Since the array is sorted:
- If `nums[i] != nums[size-1]` → it's a new unique element
- Copy it to position `size` and increment `size`

---

## 🧠 Logic in Simple Words

1. Initialize `size = 0`, place the first element at position 0 (`nums[size++] = nums[0]`)
2. Loop through the array starting from index 0
3. For each element:
   - If it's **different** from the last unique element (`nums[size-1]`)
   - Copy it to position `size` and increment `size`
4. Return `size` — the count of unique elements

---

## 📝 Code

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int size = 0;
        nums[size++] = nums[0];  // First element is always unique
        
        for(int i = 0; i < nums.length; i++){
            if(nums[i] != nums[size-1]){  // Found a new unique element
                nums[size++] = nums[i];    // Place it at next position
            }
        }
        return size;  // Return count of unique elements
    }
}
```

---

## 🎨 Visual Example

```
Input:  [1, 1, 2, 2, 3]

Step 1: size=1, nums[0]=1        → [1, 1, 2, 2, 3]
Step 2: nums[1]=1, same as nums[0], skip
Step 3: nums[2]=2, different!    → [1, 2, 2, 2, 3], size=2
Step 4: nums[3]=2, same as nums[1], skip
Step 5: nums[4]=3, different!    → [1, 2, 3, 2, 3], size=3

Output: 3 (first 3 elements are unique: [1, 2, 3])
```

---

## ⏱️ Complexity

| Time | Space |
|------|-------|
| O(n) | O(1) |

- **Time**: Single pass through the array
- **Space**: In-place modification, no extra space used
