# OverTheWire Bandit: Level 2 -> 3

## Objective
The password for the next level is stored in a file named `--spaces in this filename--` located in the home directory.

## Solution
1.  After logging in as bandit2, I ran `ls` to list the files in the directory.
    ```bash
    ls
    # Output: --spaces in this filename--
    ```
    
2.  I first attempted to read the file using `cat` with quotes, but the command interpreted the leading dashes as an option, causing it to fail.
    
3.  To solve this, I combined the two key techniques from the previous levels:
    * I used the double dash (`--`) to signal the end of command-line options.
    * I used double quotes (`"`) to treat the entire filename, including the spaces, as a single argument.
    
    The final command was:
    ```bash
    cat -- "--spaces in this filename--"
    ```

    This command successfully displayed the password for the next level.

## The Flag (Password for bandit3)
password3

## Key Learnings
-   Filenames that contain both spaces and leading dashes require special handling.
-   The double dash (`--`) followed by a quoted filename is a robust way to handle such cases.
