# Solution notes: Longest word slice

## Approach

I used Rust's split_whitespace() method to iterate over each word in the input string. This method automatically ignores leading, trailing, and multiple consecutive whitespace characters, so I did not need to handle them manually.

I maintained an Option<&str> to store the longest word found so far. For each word, I compared its length with the current longest word. If it was longer, I updated the stored value. In the case of a tie, I kept the existing word, ensuring that the first longest word was returned.

Finally, I returned the stored Option<&str>. If the input contained no words, the function returned None.

## Edge cases handled

 Empty input string
 Input containing only whitespace
 Single-word input
 Multiple words of different lengths
 Multiple words with the same maximum length (returns the first one)
 Leading, trailing, and multiple consecutive whitespace characters

## Anything special

The function returns a string slice (&str) instead of creating a new String. This avoids unnecessary memory allocation and copying because the returned slice simply borrows from the original input string. The solution runs in **O(n)** time, where n is the length of the input, and uses **O(1)** extra space.
