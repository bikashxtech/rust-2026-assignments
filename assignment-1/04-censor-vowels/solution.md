# Solution notes: Censor vowels in place

## Approach

I iterated over the characters of the input string using the chars() iterator. For each character, I checked whether it was a vowel (either uppercase or lowercase). If it was, I replaced it with '*'; otherwise, I kept the original character.

The transformed characters were collected into a new String, which was then assigned back to the original mutable string using *s = new_string. Although the function modifies the caller's string, it does so by replacing its contents with the newly constructed string, which is the idiomatic and safe approach in Rust.

## Edge cases handled

 Empty input string
 Strings containing only vowels
 Strings containing no vowels
 Mixed uppercase and lowercase vowels
 Digits, punctuation, and whitespace (left unchanged)

## Anything special

Rust strings are UTF-8 encoded, so individual characters cannot be modified directly while iterating with chars(). Instead, a new String is constructed and assigned back to the original variable. This avoids the use of unsafe code and ensures that the string always remains valid UTF-8. The solution runs in **O(n)** time, where n is the length of the input string.
