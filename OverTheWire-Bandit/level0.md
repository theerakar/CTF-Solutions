# OverTheWire Bandit: Level 0 -> 1

## Objective
The password for the next level is stored in a file called `readme` in the home directory. Use this password to log into `bandit1` using SSH.

## Solution
1.  After logging in with the initial password `bandit0`, the first step was to find the `readme` file. The `ls` command is used to list files and directories in the current location.
    
    ```bash
    ls
    # Output: readme
    ```

2.  The output confirmed that a file named `readme` was present. The next step was to read the content of this file to find the password. The `cat` command is used for this purpose.

    ```bash
    cat readme
    # Output: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
    ```
    
    The output displayed the password for the next level.

## The Flag (Password for bandit1)
password1

## Key Learnings
-   The `ls` command is used to list the files and directories in a given loction.
-   The `cat` command is used to display the contents of a file to the terminal.
