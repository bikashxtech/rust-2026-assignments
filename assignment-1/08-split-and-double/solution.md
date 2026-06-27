# Solution notes: Split and double

## Approach

I first used Rust's `split_at_mut()` method to split the input vector into two mutable, non-overlapping slices at the given index. This method safely returns two mutable references because the slices cannot overlap.

Next, I iterated over each slice using `iter_mut()`. Since `iter_mut()` yields mutable references to the elements, I doubled each value in place by dereferencing the reference and multiplying it by `2`.

Finally, I returned the two modified mutable slices.

## Edge cases handled

* Empty vector
* Split index at `0` (empty left slice)
* Split index equal to the vector length (empty right slice)
* Single-element vector
* Even and odd-sized vectors
* Invalid split index greater than the vector length (panics automatically through `split_at_mut()`)

## Anything special

I used `split_at_mut()` instead of manually creating two mutable slices. This is the idiomatic and safe way in Rust to obtain two mutable references to different parts of the same vector without violating the borrowing rules. The elements were modified in place using `iter_mut()`, avoiding the need to allocate a new vector. The solution runs in **O(n)** time, where `n` is the number of elements in the vector, and uses **O(1)** extra space.
