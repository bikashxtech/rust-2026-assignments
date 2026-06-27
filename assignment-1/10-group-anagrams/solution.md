# Solution notes: Group anagrams

## Approach

I used a `HashMap<String, Vec<String>>` to group words that are anagrams of one another. For each word in the input slice, I first converted it to lowercase to make the grouping case-insensitive. Then, I collected its characters into a `Vec<char>`, sorted them alphabetically, and collected them back into a `String`. This sorted string served as the canonical key for all of its anagrams.

Using the `entry()` API of `HashMap`, I either created a new group for the key or retrieved the existing one, and then appended the original word to that group. After processing all the words, I returned all the groups by collecting the hash map's values into a `Vec<Vec<String>>`.

## Edge cases handled

 Empty input
 Single-word input
 No anagrams
 All words being anagrams
 Case-insensitive grouping
 Words of different lengths
 Preserving the original input order within each anagram group

## Anything special

I used the sorted lowercase version of each word as a canonical representation, ensuring that all anagrams map to the same key. The original words were stored without modification, preserving their original casing and input order within each group. The solution uses the `HashMap::entry()` API for efficient insertion and grouping. If there are `n` words and the maximum word length is `k`, the overall time complexity is **O(n · k log k)** due to sorting the characters of each word.
