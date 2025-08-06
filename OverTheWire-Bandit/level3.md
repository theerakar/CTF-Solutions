# OverTheWire Bandit: Level 3 -> 4

## Objective
The password for the next level is stored in a hidden file inside a directory named `inhere`.

## Solution
1.  After logging in as bandit3, I ran the `ls` command and found a directory named `inhere`.
    
    ```bash
    ls
    # Output: inhere
    ```

2.  To check for files inside the directory, I ran `ls inhere/`. This did not show any output, which often indicates that the file is hidden.
    
    ```bash
    ls inhere/
    # (no output)
    ```

3.  I then used the `-a` flag with `ls` to show all files, including hidden ones.
    
    ```bash
    ls -a inhere/
    # Output: .  ..  ...Hiding-From-You
    ```
    
    This revealed a hidden file named `...Hiding-From-You`.

4.  Finally, I used the `cat` command with the full path to the file to display the password.
    
    ```bash
    cat inhere/...Hiding-From-You
    ```
    
    The output displayed the password for the next level.

## The Flag (Password for bandit4)
password4

## Key Learnings
-   `ls -a` is used to list all files, including hidden ones (which start with a dot).
-   To access a file inside a directory, you must specify its path (e.g., `directory/filename`).
