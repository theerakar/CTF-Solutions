# OverTheWire Bandit: Level 5 -> 6

## Objective
The password for the next level is stored in a file somewhere under the `inhere` directory and has all of the following properties: human-readable, 1033 bytes in size, and not executable.

## Solution
1.  After logging in as bandit5, I used `ls inhere/` and `ls -a inhere/` to see a large number of files and directories. Manually checking each one would be inefficient.

2.  The `find` command is the perfect tool for this task as it can search for files based on multiple criteria. I used the following flags to filter the search:
    * `-type f`: To search for only files (not directories).
    * `-size 1033c`: To find files that are exactly 1033 bytes in size. The `c` denotes bytes.
    * `! -executable`: To exclude any files that have the executable permission set. The `!` is a logical NOT.

    The complete command was:
    
    ```bash
    find inhere/ -type f -size 1033c ! -executable
    # Output: inhere/maybehere07/.file2
    ```

3.  The command successfully returned the path to the single file that met all the criteria. I then used the `cat` command to read its contents.

    ```bash
    cat -- inhere/maybehere07/.file2
    ```
    
    The output displayed the password for the next level.

## The Flag (Password for bandit6)
password6

## Key Learnings
-   The `find` command is an extremely powerful tool for locating files based on multiple properties like name, type, size, and permissions.
-   The `-type f`, `-size`, and `! -executable` flags are very useful for complex searches.
