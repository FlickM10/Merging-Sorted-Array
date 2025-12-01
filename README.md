# Merge Two Sorted Arrays – O(1) Extra Space

In-place merge of two sorted arrays when the destination array has sufficient capacity at the end.

### Problem
Given two sorted integer arrays `arr1` (length `m+n`) and `arr2` (length `n`):
- First `m` elements of `arr1` contain valid sorted data
- Last `n` positions of `arr1` are unused (reserved)
- `arr2` contains `n` sorted elements

Merge `arr2` into `arr1` such that `arr1` becomes fully sorted, using only constant extra space.

### Algorithm – Two-Pointer from the End

```text
Initialize:
    p1 ← m-1                    (last valid element of arr1)
    p2 ← n-1                    (last element of arr2)
    write_pos ← m+n-1           (last position of arr1)

While p2 ≥ 0:
    if p1 ≥ 0 and arr1[p1] > arr2[p2]:
        arr1[write_pos] ← arr1[p1]
        p1 ← p1 - 1
    else:
        arr1[write_pos] ← arr2[p2]
        p2 ← p2 - 1
    write_pos ← write_pos - 1
```
## Why merge backwards?

Forward merge would overwrite elements still needed.

Backward merge uses the reserved empty space first.

No element is read before it has been safely placed.

### Complexity

Time:   O(m + n)

Space:  O(1) extra memory

#### Key Insight
Comparing and placing the largest remaining element at each step guarantees correctness while avoiding any need for auxiliary storage.
This is the optimal solution for constant-space merging of sorted data.
