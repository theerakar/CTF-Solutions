# OverTheWire Bandit: Level 4 -> 5

## Objective
The password for the next level is stored in the only human-readable file in the `inhere` directory.

## Solution
1.  After logging in as bandit4, I ran `ls inhere/` to list the files in the directory. The output showed ten files named `-file00` through `-file09`.
    
    ```bash
    ls inhere/
    # Output: -file00 -file01 -file02 ... -file09
    ```

2.  I knew from the objective that only one of these files was "human-readable" (plain text). The `file` command is perfect for this, as it determines a file's type. I used a `for` loop to check all the files at once.
    
    ```bash
    for file in inhere/*; do file "$file"; done
    ```
    
    The output showed that most files were `data`, but one stood out:
    
    ```
    ...
    inhere/-file07: ASCII text
    ...
    ```

3.  This confirmed that `-file07` was the correct file. I used the `cat` command with the double dash (`--`) to read its contents.
    
    ```bash
    cat -- inhere/-file07
    ```
    
    The output displayed the password for the next level.

## The Flag (Password for bandit5)
password5

## Key Learnings
-   The `file` command is used to determine the type of a file.
-   A `for` loop can be used to efficiently run a command on multiple files. The syntax `for file in *; do ...; done` is very useful.
