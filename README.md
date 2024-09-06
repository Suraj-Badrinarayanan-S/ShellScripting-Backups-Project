This Bash script automates the process of backing up a specified directory and maintains a rotation of the last three backups to prevent excessive disk usage. 

Features:

        Backup Creation:

                The script takes two arguments: a source directory to back up and a destination directory where the backup will be stored.
                A ZIP file is generated, containing the contents of the source directory. This file is named using the current date and time, ensuring unique names for each backup.
                If the backup is created successfully, a confirmation message is displayed.


        Backup Rotation:

                The script checks the destination directory for existing backup files. If more than three backups are found, the oldest ones are deleted, keeping only the most recent three backups.
                This process ensures that older backups are automatically removed, limiting the storage to just the last three backups.

To run the script, execute the following command: 

        ./backup.sh <source-path> <backup-path>

