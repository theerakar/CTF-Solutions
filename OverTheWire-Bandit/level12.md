# OverTheWire Bandit: Level 12 -> 13

## Objective
The password for the next level is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed.

## Solution
1.  Since the home directory is not writable, I first created a temporary working directory to perform the file manipulations. This is a good practice to avoid clutter.
    
    ```bash
    mktemp -d
    # Output: /tmp/tmp.DD5m3KvLsD
    cd /tmp/tmp.DD5m3KvLsD
    cp /home/bandit12/data.txt .
    ```

2.  The `data.txt` file was a hexdump. I used `xxd` with the `-r` flag to reverse the hexdump and saved the output to a new file.
    
    ```bash
    xxd -r data.txt > compressed_file
    ```

3.  From here, the solution was an iterative process of identifying the file type and using the correct tool to decompress or extract its contents. I used a loop of `file` and the appropriate command based on the output.
    
    * `file compressed_file` -> `gzip compressed data`
    * Used `zcat compressed_file > new_compressed_file` to decompress it.
    * `file new_compressed_file` -> `bzip2 compressed data`
    * Used `bzip2 -df new_compressed_file` to decompress it.
    * `file new_compressed_file.out` -> `POSIX tar archive (GNU)`
    * Used `tar -xf new_compressed_file.out` to extract the next file.
    * `file data8.bin` -> `gzip compressed data`
    * Used `zcat data8.bin > new_file` to decompress it.
    * `file new_file` -> `ASCII text`

4.  Once the file was finally identified as `ASCII text`, I used `cat` to read the contents and find the password.
    
    ```bash
    cat new_file
    ```

## The Flag (Password for bandit13)
password12

## Key Learnings
-   Multi-step puzzles require patience and a systematic approach.
-   The `mktemp -d` command is a safe and convenient way to create temporary working directories.
-   The `xxd -r` command is used to reverse a hexdump.
-   `file` is the most important tool for this kind of challenge; it tells you what to do next.
-   The decompression commands (`gzip`, `bzip2`, `tar`) often have flags like `-d` (decompress), `-f` (force), and `-x` (extract) that are essential for handling these files. `zcat` is a great alternative to `gzip -d` when filenames are tricky.
