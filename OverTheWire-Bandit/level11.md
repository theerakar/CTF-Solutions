# OverTheWire Bandit: Level 11 -> 12

## Objective
The password for the next level is stored in the file `data.txt`, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions (ROT13).

## Solution
1.  After logging in as bandit11, I found the file `data.txt`. The objective was clear that the file was encoded with ROT13.

2.  The `tr` command, which stands for "translate," is the perfect tool for character substitution. To decode ROT13, I needed to map the alphabet to a new, shifted alphabet. The first half of the alphabet (A-M) maps to the second half (N-Z), and vice-versa.

3.  I used a pipeline to send the contents of the `data.txt` file to the `tr` command.
    
    ```bash
    cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
    ```

    This command translates every letter in the input, correctly decoding the ROT13 message and displaying the password for the next level.

## The Flag (Password for bandit12)
password12

## Key Learnings
-   The `tr` command is a powerful tool for translating or deleting characters.
-   `tr` is especially useful for simple character ciphers like ROT13. The format `'[set1]' '[set2]'` maps each character in `set1` to its corresponding character in `set2`.
