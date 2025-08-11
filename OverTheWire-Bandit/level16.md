# OverTheWire Bandit: Level 16 -> 17

## Objective
The goal was to find a server listening on a port between 31000 and 32000, determine if it used SSL/TLS, and submit the current password to get the next-level credentials.

## Solution
1.  First, I used `nmap` to scan the specified port range on `localhost` to find any open ports.
    ```bash
    nmap -p 31000-32000 localhost
    ```
    This identified several open ports: `31046`, `31518`, `31691`, `31790`, and `31960`.

2.  Next, I systematically tested each port with `nc` and `openssl s_client`. I discovered that some ports were non-SSL, and some were SSL, but they all just echoed back my input, even the correct password.

3.  The final successful approach was to use the `socat` command, which is a more powerful networking tool. By piping the password into the command, I could connect non-interactively and handle the SSL handshake correctly.
    ```bash
    echo kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx | socat - openssl:localhost:31790,verify=0
    ```
    - The `echo` command pipes the password to `socat`.
    - `openssl:localhost:31790` specifies the host, port, and that it's an SSL connection.
    - `verify=0` is crucial because the server uses a self-signed certificate.

4.  The output from this command was "Correct!" followed by the private key for the next level.

## The Flag (Password for bandit17)
The password is the entire RSA Private Key block. To use this to log in to the next level, you must save it to a file.

1.  Navigate to a temporary directory.
    ```bash
    cd /tmp
    ```

2.  Create a file and paste the entire key, then press `Ctrl+D`.
    ```bash
    cat > bandit17_key
    ```

3.  Set the correct permissions for the private key file.
    ```bash
    chmod 600 bandit17_key
    ```

4.  Use the key to log in to the next level.
    ```bash
    ssh -i bandit17_key bandit17@localhost -p 2220
    ```
