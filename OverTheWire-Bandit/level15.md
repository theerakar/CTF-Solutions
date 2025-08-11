# OverTheWire Bandit: Level 15 -> 16

## Objective
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

## Solution
1.  This level was a network challenge that required using an encrypted connection (SSL/TLS). A simple tool like `nc` would not work for this.
    
2.  The `openssl` command with the `s_client` subcommand is the correct tool for this task. It acts as a generic SSL/TLS client. The command syntax is `openssl s_client -connect <host>:<port>`.
    
    ```bash
    openssl s_client -connect localhost:30001
    ```
    
3.  After running the command, my terminal established the encrypted connection and displayed a lot of certificate information. It then waited for input. I pasted the password for the current level (`8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`) and pressed Enter.
    
4.  The server responded with "Correct!" and provided the password for the next level.

## The Flag (Password for bandit16)
password16

## Key Learnings
-   Encrypted network connections (SSL/TLS) require special tools like `openssl`.
-   The `openssl s_client` command is used to act as a client and test SSL/TLS services.
-   The `-connect` flag is used to specify the host and port.
-   The output often includes certificate information, which is normal.
