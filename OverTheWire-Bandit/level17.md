Bandit Level 17 → Level 18 
Level Goal

The objective of this level was to find the password for Bandit Level 18. This password was located in a file named passwords.new within the home directory, and the key clue was that it was the only line that differed between passwords.old and passwords.new.
Tools Used

    ls: To list files and confirm their presence.

    diff: The primary tool used to compare the two files and identify the changed line.

    ssh: To log into the next level.

Step-by-Step Breakdown

    Confirming File Presence:
    Upon logging into Bandit Level 17, the first step was to list the files in the home directory to confirm the existence of passwords.old and passwords.new.

    ls -l

    This command verified that both required files were present.

    Identifying the Password with diff:
    The core of this level was using the diff command to compare passwords.old and passwords.new. The problem statement indicated that the password was the only line that had changed.

    diff passwords.old passwords.new

    The output clearly showed the difference, for example:

    42c42
    < Vhc9EKhF5JOIiQsrq2hjyvDaALKaGKCh
    ---
    > x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

    This output indicated that line 42 was changed, and the new content (x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO) was the password for Bandit Level 18.

    Logging into Bandit Level 18:
    With the password found, the final step was to log into the next level. A crucial learning point here was understanding the restriction on SSHing from localhost within the Bandit environment.

        First, the user had to exit the current bandit17 SSH session to return to their local machine's terminal.

        From the local terminal, the ssh command was then used with the newly found password:

        ssh bandit18@bandit.labs.overthewire.org -p 2220

        Upon the first connection from the local machine, the SSH client prompted to confirm the authenticity of the host key. Typing yes allowed the connection to proceed.

        Finally, entering the password x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO at the password prompt successfully granted access to Bandit Level 18.

Key Learnings

    File Comparison with diff: A fundamental command-line utility for identifying differences between text files, invaluable in various CTF scenarios.

    Understanding diff Output: Interpreting the format of diff's output to pinpoint changes.

    SSH Restrictions in CTF Environments: Recognizing and overcoming the "Connecting from localhost is blocked" restriction by initiating new SSH sessions from the local machine rather than chaining them within the wargame server. This is a common pattern in wargames to prevent resource abuse.
