# Contains Duplicate

## 🎯 Problem Summary
Given an array of integers, return `true` if any value appears **more than once**, otherwise return `false`.

---

## 💡 Approach: Use a HashSet

**Why HashSet?**
- A HashSet stores only **unique values** — it doesn't allow duplicates.
- We can use this property to detect if we've seen a number before.

---

## 🔑 Key Method: `set.add(num)`

| What it does | Return Value |
|--------------|--------------|
| If `num` is **new** → adds it to the set | `true` |
| If `num` **already exists** → does nothing | `false` |

So when `set.add(num)` returns `false`, it means we found a duplicate!

---

## 🧠 Logic in Simple Words

1. Create an empty HashSet
2. Loop through each number in the array
3. Try to add the number to the set
   - If it **fails to add** (returns `false`) → duplicate found → return `true`
   - If it **adds successfully** → continue to next number
4. If loop finishes without finding duplicates → return `false`

---

## 📝 Code

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for(int num : nums){
            if(!set.add(num)){  // add() returns false if already exists
                return true;     // found duplicate!
            }
        }
        return false;  // no duplicates found
    }
}
```

---

## ⏱️ Complexity

| Time | Space |
|------|-------|
| O(n) | O(n) |

- **Time**: We visit each element once
- **Space**: Worst case, we store all elements in the set
