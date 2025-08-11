 # OverTheWire Bandit: Level 10 -> 11

## Objective
The password for the next level is stored in the file `data.txt`, which contains base64 encoded data.

## Solution
1.  After logging in as bandit10, I found a file named `data.txt`. I checked its size and type, but the objective was explicit that it contained base64 encoded data.

2.  To decode base64, the correct command is `base64` with the `-d` (decode) flag. I needed to feed the contents of `data.txt` into this command.

3.  I used a pipeline to send the output of `cat data.txt` to the `base64 -d` command.
    
    ```bash
    cat data.txt | base64 -d
    ```

    This command successfully decoded the data and displayed the password for the next level.

## My Mistake
I initially made a common mistake and typed `base 64 -d`, which the shell did not recognize as a valid command. The correct command is a single word: `base64`.

## The Flag (Password for bandit11)
password11

## Key Learnings
-   The `base64` command is used for both encoding and decoding data.
-   The `-d` flag is required to perform the decoding.
-   The command is a single word, `base64`, not two separate words.
