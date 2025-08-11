# OverTheWire Bandit: Level 9 -> 10

## Objective
The password for the next level is stored in the file `data.txt` in one of the few human-readable strings, preceded by several `==` characters.

## Solution
1.  After logging in as bandit9, I found a file named `data.txt`. Following my new workflow, I first checked its size and type.
    
    ```bash
    ls -lh data.txt
    # Output: 19K
    file data.txt
    # Output: data.txt: data
    ```

2.  The output showed that the file was 19KB and of type `data`, which is not plain text. This meant I couldn't use `cat` and had to use a tool to extract readable strings.

3.  The `strings` command is designed for this. It pulls out all sequences of printable characters from a binary file. I then used a pipeline to send that output to the `grep` command.

4.  The objective said the password was preceded by `==`, so I used `grep` to search for that specific pattern.
    
    ```bash
    strings data.txt | grep "=="
    ```
    
    This command successfully displayed the line containing the password, along with a few other clue lines.

## The Flag (Password for bandit10)
password9

## Key Learnings
-   The `strings` command is essential for working with binary files, as it can extract all the human-readable text.
-   Combining `strings` with `grep` in a pipeline is a powerful technique for searching inside binary files.
