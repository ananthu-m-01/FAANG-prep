# Find the Duplicate Number

## 🎯 Problem Summary
Given an array of `n + 1` integers where each integer is in the range `[1, n]`, find the **one repeated number**.

---

## 💡 Approach: Boolean Array as Tracker

**Why Boolean Array?**
- Since numbers are in range `[1, n]`, we can use an array of size `n` to track which numbers we've seen.
- Each index represents a number (index 0 → number 1, index 1 → number 2, etc.)
- If we encounter a number that's already marked `true`, that's our duplicate!

---

## 🔑 Key Insight

| Array Index | Represents Number |
|-------------|-------------------|
| `ans[0]` | Number 1 |
| `ans[1]` | Number 2 |
| `ans[num - 1]` | Number `num` |

When `ans[num - 1]` is already `true` → we've seen `num` before → **duplicate found!**

---

## 🧠 Logic in Simple Words

1. Create a boolean array of size `n` (same as `nums.length`)
2. Loop through each number in the array
3. For each number:
   - Check if `ans[num - 1]` is already `true`
     - **Yes** → This number was seen before → return it
     - **No** → Mark it as seen: `ans[num - 1] = true`
4. Continue until duplicate is found

---

## 📝 Code

```java
class Solution {
    public int findDuplicate(int[] nums) {
        boolean[] ans = new boolean[nums.length];
        
        for(int num : nums){
            if(ans[num - 1]){       // Already seen this number?
                return num;          // Found the duplicate!
            } else {
                ans[num - 1] = true; // Mark as seen
            }
        }
        return 1;  // Fallback (problem guarantees a duplicate exists)
    }
}
```

---

## 🎨 Visual Example

```
Input: [1, 3, 4, 2, 2]
Array size: 5, so boolean array size = 5

Step 1: num=1 → ans[0]=false → mark true  → [T, F, F, F, F]
Step 2: num=3 → ans[2]=false → mark true  → [T, F, T, F, F]
Step 3: num=4 → ans[3]=false → mark true  → [T, F, T, T, F]
Step 4: num=2 → ans[1]=false → mark true  → [T, T, T, T, F]
Step 5: num=2 → ans[1]=true  → DUPLICATE! → return 2

Output: 2
```

---

## ⏱️ Complexity

| Time | Space |
|------|-------|
| O(n) | O(n) |

- **Time**: Single pass through the array
- **Space**: Boolean array of size n

---

## 💭 Note
There's also an **O(1) space** solution using Floyd's Cycle Detection (Tortoise and Hare), but this boolean array approach is simpler and easier to understand for revision!
