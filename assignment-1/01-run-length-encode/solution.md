# Solution notes: Run-length encode

## Approach

I iterated over the string using a for loop and checked whether the next character was the same as the current character. If it was, I incremented the count for that character. When the character changed, I pushed the tuple (char, count) into the result vector and started counting the new character.

Before the loop, I used the Option enum to check whether the input string contained at least one character. The expression Some(mut current) matches the first character if it exists; otherwise, chars.next() returns None, and the if let block is skipped. This also handles the empty string case gracefully.

## Edge cases handled

 Empty input string
 Single character
 All identical characters
 All distinct characters
 Multiple consecutive runs
 Whitespace characters

## Anything special

I used Rust's Option enum with the if let Some(mut current) pattern to safely extract the first character without risking a panic. If the input string is empty, chars.next() returns None, so the encoding logic is skipped automatically.
