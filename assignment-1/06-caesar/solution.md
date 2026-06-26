# Solution notes: Caesar cipher

## Approach

I first normalized the shift value using rem_euclid(26) so that both large positive and negative shifts were reduced to an equivalent value within the range 0..26.

Next, I iterated over the input string using the chars() iterator. For each character, I checked whether it was an uppercase or lowercase English letter. If it was, I converted it to its zero-based alphabet index (0–25) by subtracting either 'a' or 'A'. After applying the normalized shift and wrapping around the alphabet using the modulo operator, I converted the result back to a character by adding the appropriate ASCII base.

Characters that were not English letters, such as digits, punctuation, and whitespace, were left unchanged and appended directly to the result string.

## Edge cases handled

 Empty input string
 Zero shift
 Shift equal to 26 (identity transformation)
 Large positive shifts
 Large negative shifts
 Uppercase and lowercase letters
 Non-alphabetic characters (digits, punctuation, and whitespace)

## Anything special

I used rem_euclid(26) instead of the % operator to correctly handle negative shift values. This ensures that shifts such as -1 and -27 wrap around the alphabet as expected. The implementation preserves the case of each letter while leaving all non-letter characters unchanged. The solution runs in **O(n)** time, where n is the length of the input string, and uses **O(n)** additional space for the output string.
