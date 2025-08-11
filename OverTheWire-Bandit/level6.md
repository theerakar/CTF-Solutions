# OverTheWire Bandit: Level 6 -> 7

## Objective
The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, and 33 bytes in size.

## Solution
1.  After logging in as bandit6, the goal was to find a file with specific properties anywhere on the server. Manually searching would be impossible.

2.  The `find` command is the ideal tool for this, as it can search the entire file system. To search the entire server, I started the search from the root directory `/`. I used the following flags to filter the search based on the level's objective:
    * `-user bandit7`: To find files owned by the user `bandit7`.
    * `-group bandit6`: To find files owned by the group `bandit6`.
    * `-size 33c`: To find files that are exactly 33 bytes in size.

3.  The command `find / -user bandit7 -group bandit6 -size 33c` would generate many "Permission denied" errors. To suppress these errors and only see the successful result, I added `2>/dev/null`.

    The complete command was:
    
    ```bash
    find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
    # Output: /var/lib/dpkg/info/bandit7.password
    ```

4.  The command successfully returned the absolute path to the correct file. I then used `cat` on that path to display the password.

    ```bash
    cat /var/lib/dpkg/info/bandit7.password
    ```

    The output displayed the password for the next level.

## The Flag (Password for bandit7)
password7

## Key Learnings
-   The `find` command can search the entire file system by starting the search from `/`.
-   The `-user` and `-group` flags are used to filter files based on their owner.
-   `2>/dev/null` is used to redirect command errors to a "black hole," preventing them from cluttering the terminal.
