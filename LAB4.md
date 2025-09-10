# File and Backup automation

## **Objective**
The aim of this lab is to create a bash script that automatically finds all `.txt` files in the current folder and copies them into a `backup/` folder.  
Each backup file should have a **timestamp** in its name for easy identification.

---

## **Script: `backup.sh`**
```bash
#!/bin/bash
# Create backup folder if it doesn't exist
mkdir -p backup

# Get current timestamp
timestamp=$(date +"%Y%m%d_%H%M%S")

# Find all .txt files and copy them with timestamp
for file in *.txt; do
    if [ -f "$file" ]; then
        cp "$file" "backup/${file%.txt}_$timestamp.txt"
        echo "Backed up: $file → backup/${file%.txt}_$timestamp.txt"
    fi
done

echo "Backup completed successfully!"
```

## How the Script Works
Create a folder
Uses mkdir -p backup → Makes a backup/ folder if it doesn’t exist.
Generate a timestamp
Uses date +"%Y%m%d_%H%M%S" to get the current date and time.
Find .txt files
Loops through all .txt files in the current folder.
Copy files with new names
Each file is copied into backup/ with the timestamp added.
Display messages
Shows which files were backed up successfully.

### Example run:

1- Make the script executable by 'chmod 777 backup.sh' <br>
2- Make some txt files by 'touch goose.txt' and 'touch fish.txt' <br>
3- Run the script by './backup.sh'

### Output
![alt text](<Screenshot 2025-09-10 at 9.26.44 PM.png>)


# Extra questions1:
## Question 1.) What is the difference between cp, mv and rsync?
### A: `cp` --> It makes a duplicate of the file/folder. The original one stays in place. <br> `mv` --> It moves the file from one place to another and can also rename it. The original is removed from its old location. <br> `rsync` --> It can copy locally or remotely and only copies differences.

## Question 2.) How can you schedule scripts to run auttomatically?
### A: With cronjobs --> `cron` is a  built-in scheduler.