# Solution notes: Character frequency, sorted

## Approach

I used a HashMap<char, u32> to count the frequency of each character in the input string. I iterated over the string using the chars() iterator and, for each character, updated its count in the hash map using the entry() API.

After counting all the characters, I converted the hash map into a Vec<(char, u32)> using into_iter().collect(). Finally, I sorted the vector using a custom comparator. The vector is sorted in descending order of character frequency, and if two characters have the same frequency, they are sorted in ascending alphabetical order.

## Edge cases handled

 Empty input string
 Single-character input
 All characters having the same frequency
 One character occurring more frequently than the others
 Whitespace characters (counted as valid characters)
 Multiple occurrences of characters appearing in different positions within the string

## Anything special

I used Rust's HashMap::entry() API together with or_insert() to update character frequencies efficiently without having to check whether a key already existed. The final sorting was performed using sort_by() with a custom comparator and then() to handle tie-breaking. The solution runs in **O(n + k log k)** time, where n is the length of the input string and k is the number of distinct characters.
