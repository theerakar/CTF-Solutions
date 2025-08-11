# OverTheWire Bandit: Level 7 -> 8

## Objective
The password for the next level is stored in the file `data.txt` next to the word `millionth`.

## Solution
1.  After logging in as bandit7, I found a file named `data.txt`. I initially tried to read the entire file using `cat`, but the file was extremely large, making it impossible to find the password manually.

2.  The hint from the level description and the list of commands (`grep`) indicated that I needed to search for a specific word.

3.  I used the `grep` command to search for the word `"millionth"` within the `data.txt` file.

    ```bash
    grep "millionth" data.txt
    # Output: millionth         dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
    ```
    This command successfully filtered the massive file and displayed only the line containing the target word, which also included the password.

## The Flag (Password for bandit8)
password8

## Key Learnings
-   The `grep` command is used to search for a specific pattern or word inside a file.
-   When a file is too large to read with `cat`, `grep` is the perfect tool for quickly finding the information you need.
