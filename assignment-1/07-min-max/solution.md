# Solution notes: Minimum and maximum

## Approach

I first checked whether the input slice was empty. If it was, I returned None because there are no values from which to determine a minimum or maximum.

For a non-empty slice, I initialized both the minimum and maximum values to the first element of the slice. Then, I iterated through the remaining elements and compared each value with the current minimum and maximum. If a smaller value was found, I updated the minimum; if a larger value was found, I updated the maximum.

After processing all the elements, I returned the result as Some((minimum, maximum)).

## Edge cases handled

 Empty slice
 Single-element slice
 All elements equal
 Ascending order
 Descending order
 Negative numbers
 Values at the i32 bounds (i32::MIN and i32::MAX)

## Anything special

I used an Option<(i32, i32)> to represent the possibility of an empty input slice. The minimum and maximum values were stored together as a tuple, making the implementation concise and easy to read. The solution traverses the slice only once, resulting in **O(n)** time complexity and **O(1)** extra space.
