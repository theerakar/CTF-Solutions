# OverTheWire Bandit: Level 14 -> 15

## Objective
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Solution
1.  This level was a network challenge. The goal was to connect to a specific port on the local machine and provide the current password to get the next one.
    
2.  The `nc` (netcat) command is a versatile networking tool perfect for this task. The command syntax is `nc <host> <port>`.
    
    ```bash
    nc localhost 30000
    ```
    
3.  After running the command, my terminal connected and waited for input. I then pasted the password for the current level (`MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`) and pressed Enter.
    
4.  The server responded with "Correct!" and provided the password for the next level.

## The Flag (Password for bandit15)
password15

## Key Learnings
-   Basic network connectivity can be tested and exploited using the `nc` command.
-   `localhost` is a special hostname that always refers to the machine you are currently on.
-   A network port is a specific channel on a machine that a service uses to communicate.
-   Some puzzles require interactive input to a running program.
