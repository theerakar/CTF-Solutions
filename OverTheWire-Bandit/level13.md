# OverTheWire Bandit: Level 13 -> 14

## Objective
The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`. A private SSH key is provided to log in as `bandit14`.

## Solution
1.  The home directory for `bandit13` is read-only, which prevents `ssh` from saving the host fingerprint and `chmod` from changing key permissions. To work around this, I created a temporary directory and copied the `sshkey.private` file there.
    
    ```bash
    mktemp -d
    # Output: /tmp/tmp.hMqQ7Tg0NN
    cp sshkey.private /tmp/tmp.hMqQ7Tg0NN/
    ```

2.  `ssh` is very strict about the permissions on private key files; they must not be readable by others. I used `chmod 400` on the copied key file to make it read-only for the owner.
    
    ```bash
    chmod 400 /tmp/tmp.hMqQ7Tg0NN/sshkey.private
    ```

3.  The final `ssh` command required several flags to handle all the environmental constraints:
    * `-i <key_path>`: Specifies the path to the private key file.
    * `-p 2220`: Specifies the correct port for the wargame.
    * `-o UserKnownHostsFile=/dev/null`: Bypasses the inability to save the host key to the read-only home directory.
    * `-o StrictHostKeyChecking=no`: Ignores the host key check, which is necessary when using `/dev/null`.

4.  Putting it all together, the final command was:
    
    ```bash
    ssh bandit14@localhost -i /tmp/tmp.hMqQ7Tg0NN/sshkey.private -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -p 2220
    ```
    
    This command successfully logged me in as `bandit14`.

5.  Once logged in, I used `cat` to retrieve the password from the specified file.
    
    ```bash
    cat /etc/bandit_pass/bandit14
    ```

## The Flag (Password for bandit14)
password14

## Key Learnings
-   Using a private SSH key is an alternative to a traditional password for authentication.
-   Private SSH keys have strict permission requirements (`chmod 400`).
-   The `ssh` command has many useful flags (`-i`, `-p`, `-o`) that can be used to bypass specific environmental roadblocks, such as read-only home directories or specific port requirements.
-   When a command fails due to permission issues, a common workaround is to copy the file to a writable location like `/tmp/`.
