# Increment Operator Variations

The increment operator (++) can be used for accessing an index _and_ incrementing the underlying variable when iterating an array, fx. in a for-loop.

Take the following array:

```c#
var nums = new int[] {1,2,3,4,5};
```

Now imagine that array used in the below "RemoveElement" method, that I recently had to create in a LeetCode task:

```c#
public int RemoveElement(int[] nums, int val) {
        var k = 0;

        for(var i = 0; i < nums.Length; i++) {
            if(nums[i] != val)
            {
                nums[k++] = nums[i];
            }
        }

        return k;
    }
```

Notice that `nums[k++] = nums[i]` at `k = 0` will, in fact, access index 0 of nums and _then_ increment.

There is a counter-part to this - the pre-increment operator. Using `k` from above, the pre-increment operator would be used as `++k`, which would have accessed index 1 of nums at `k = 0`.
