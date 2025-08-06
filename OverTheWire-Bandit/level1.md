# OverTheWire Bandit: Level 1 -> 2

## Objective
The password for the next level is stored in a file named `-` located in the home directory.

## Solution
1.  After logging in with the password from the previous level, I ran the `ls` command to list the files in the directory.
    ```bash
    ls
    ```
    The output showed a single file named `-`.

2.  I initially tried `cat -`, but the command line interpreted this as a special character for standard input. The hints in the prompt guided me to search for how to handle special filenames.

3.  To solve this, I used one of two methods to explicitly tell the `cat` command that I wanted to read a file named `-`.
    
    **Method 1: Using the double dash (`--`)**
    ```bash
    cat -- -
    ```
    
    **Method 2: Using the relative path (`./`)**
    ```bash
    cat ./-
    ```
    
    Both commands successfully displayed the password for the next level.

## The Flag (Password for bandit2)
password2

## Key Learnings
-   Filenames that start with a dash (`-`) are treated as special command-line arguments.
-   The double dash (`--`) can be used to signal the end of command options.
-   The `./` syntax can be used to specify that a file is in the current directory.
