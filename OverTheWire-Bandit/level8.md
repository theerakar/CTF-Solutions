# OverTheWire Bandit: Level 8 -> 9

## Objective
The password for the next level is stored in the file `data.txt` and is the only line of text that occurs only once.

## Solution
1.  After logging in as bandit8, I found the file `data.txt`. I checked its size using `ls -lh` and determined it was too large to read manually.

2.  The objective of finding the "unique" line suggested using the `uniq` command. However, `uniq` only works on adjacent lines. To use it effectively, I first needed to sort the file to group all identical lines together.

3.  I used a command pipeline to first sort the file and then pass the output to `uniq`.
    * `sort data.txt`: This command sorted all the lines in the file alphabetically and sent the output to the standard output.
    * `|`: The pipe symbol redirects the output of the `sort` command as the input for the next command.
    * `uniq -u`: This command receives the sorted data and, with the `-u` flag, prints only the lines that are not duplicated.

    The complete command was:
    
    ```bash
    sort data.txt | uniq -u
    ```
    
    This command successfully displayed the single unique line, which was the password for the next level.

## The Flag (Password for bandit9)
password9

## Key Learnings
-   The `|` (pipe) symbol is used to send the output of one command to the input of another. This is a fundamental concept in the command line.
-   The `sort` command is often used as a prerequisite for `uniq` when dealing with unsorted data.
-   The `uniq -u` command is a powerful way to find unique lines in a file.
