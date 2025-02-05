# Backup Script with 7-Day Rotation and Cron Job

This script automates the process of backing up files and managing backup file rotation for the last 7 days. It accepts two arguments: the source directory to back up and the backup directory where the backup will be stored. The script creates a zip archive of the source directory, names the backup with a timestamp, and saves it in the specified backup directory.

The script also implements backup rotation, ensuring that only the 7 most recent backups are kept, and automatically deletes older backups beyond the 7 most recent ones.

Additionally, the script can be scheduled to run automatically every day using a cron job, making it an efficient solution for regular backups without manual intervention.

## Features:
1. **Backup Creation**: Backs up a specified source directory into a timestamped zip file.
2. **Backup Rotation**: Keeps only the 7 most recent backups and deletes older ones.
3. **Cron Job Support**: Can be scheduled to run automatically at specified intervals (e.g., every day at midnight).
4. **Efficient Storage Management**: Automatically deletes backups older than 7 days.

Usage:
Clone or Download the Repository:

You can either clone the repository using Git or download the script file directly.

**Make the Script Executable:** Ensure the script is executable by running the following command in your terminal:

bash
Copy
Edit
chmod +x backup_script.sh

**Run the Script Manually** Execute the script using the following syntax:

bash
Copy
Edit
./backup_script.sh <source_directory> <backup_directory>
<source_directory>: The path to the directory you wish to back up.
<backup_directory>: The path to the directory where the backups will be stored.

Example:

bash
Copy
Edit
./backup_script.sh /home/user/data /home/user/backups

This command will create a backup of /home/user/data and save it to /home/user/backups, with the backup file named using the current timestamp.

------------------------------------------------------------------------

# Setting Up Automatic Backups with Cron:

To automate the backup process, you can schedule the script to run at a specific interval using cron jobs.

### Open the Crontab: Run the following command to edit your cron jobs:

bash
Copy
Edit
crontab -e

### Add the Cron Job: Add the following line to schedule the script to run every day at midnight:

bash
Copy
Edit
0 0 * * * /path/to/backup_script.sh /path/to/source_directory /path/to/backup_directory
Replace /path/to/backup_script.sh, /path/to/source_directory, and /path/to/backup_directory with the actual paths on your system.
Example Cron Job: To run the backup every day at midnight, you could add:

bash
Copy
Edit
0 0 * * * /home/user/scripts/backup_script.sh /home/user/data /home/user/backups
Save and Exit:

If you're using nano, save and exit by pressing CTRL+X, then Y to confirm, and Enter to save.
If you're using vim, press Esc, then type :wq and press Enter.
Verify the Cron Job: To ensure the cron job has been added correctly, you can list your cron jobs with:

bash
Copy
Edit
crontab -l
How the Script Works:
Backup Creation: The script creates a zip archive of the source directory, naming the backup with a timestamp (e.g., backup_2025-02-05-00-00-00.zip), and saves it to the specified backup directory.

Backup Rotation: The script checks the backup directory for existing backups and keeps only the 7 most recent ones. Older backups are deleted.

Cron Job: By setting up a cron job, the script can run automatically at scheduled intervals, ensuring that backups are created regularly without manual intervention.
