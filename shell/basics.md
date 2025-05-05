# macOS Terminal Basics

## Table of Contents
- [Navigation](#navigation)
- [File Operations](#file-operations)
- [Echo Command](#echo-command)
- [History Management](#history-management)
- [File Permissions](#file-permissions)
- [Searching](#searching)
- [Process Management](#process-management)
- [Redirection and Pipes](#redirection-and-pipes)
- [Useful Utilities](#useful-utilities)
- [macOS Specific Commands](#macos-specific-commands)
- [Terminal Customization](#terminal-customization)
- [Keyboard Shortcuts](#keyboard-shortcuts)

---

## Navigation

### Present Working Directory
Display your current location in the file system:
```shell
pwd
```

### List Files and Directories
List contents of current directory:
```shell
ls
```

Common flags:
- `-l`: Long format with details
- `-a`: Show all files (including hidden)
- `-h`: Human-readable file sizes
- `-t`: Sort by modification time

Combined example:
```shell
ls -lah
```

### Change Directory
Move to another directory:
```shell
cd DIRECTORY_PATH
```

Shortcuts:
- `cd ~`: Go to home directory
- `cd ..`: Go up one directory
- `cd -`: Go to previous directory
- `cd /`: Go to root directory

---

## File Operations

### Create Files
Create an empty file:
```shell
touch FILENAME
```

Create multiple files at once:
```shell
touch file1.txt file2.txt file3.txt
```

### Create Directories
Create a new directory:
```shell
mkdir DIRECTORY_NAME
```

Create nested directories:
```shell
mkdir -p parent/child/grandchild
```

Create nested directories and a file in one command:
```shell
mkdir -p parent/child && touch parent/child/setup.ts
```
This creates the entire directory path `parent/child` and then creates the file `setup.ts` inside it.

### Copy Files/Directories
Copy a file:
```shell
cp SOURCE DESTINATION
```

Copy a directory and its contents:
```shell
cp -r SOURCE_DIR DESTINATION_DIR
```

### Move/Rename Files
Move or rename files:
```shell
mv SOURCE DESTINATION
```

Examples:
```shell
mv file.txt new_location/     # Move file
mv file.txt new_name.txt      # Rename file
```

### Delete Files/Directories
Remove a file:
```shell
rm FILENAME
```

Remove a directory and its contents:
```shell
rm -r DIRECTORY_NAME
```

Force removal without confirmation:
```shell
rm -rf DIRECTORY_NAME
```

### View File Contents
Display entire file content:
```shell
cat FILENAME
```

Display file with pagination:
```shell
less FILENAME
```
(Use `q` to exit, space to page down, `b` to page up)

Display first/last lines of a file:
```shell
head FILENAME       # First 10 lines by default
head -n 20 FILENAME # First 20 lines

tail FILENAME       # Last 10 lines by default
tail -n 20 FILENAME # Last 20 lines
```

---

## Echo Command

The `echo` command is used to display text or variable values in the terminal:

```shell
echo "Hello, world!"
```

Print environment variables:
```shell
echo $HOME         # Displays home directory path
echo $PATH         # Displays executable search path
```

Echo with special characters:
```shell
echo -e "Line 1\nLine 2"   # -e enables interpretation of backslash escapes
```

Echo without newline:
```shell
echo -n "No newline at the end"
```

Echo to file:
```shell
echo "Some text" > file.txt     # Creates or overwrites file
echo "More text" >> file.txt    # Appends to file
```

---

## History Management

### View Command History
View previously executed commands:
```shell
history
```

### Search Command History
Search through history interactively:
- Press `⌘+R` and then type search term
- Press `⌘+R` again to cycle through matches
- Press `Enter` to execute the found command

### Clear History
Clear the terminal screen:
```shell
clear
```
(Shortcut: `⌘+K`)

Clear the history file:
```shell
history -c
```

Delete specific history entry:
```shell
history -d LINE_NUMBER
```

---

## File Permissions

### View Permissions
Check file permissions:
```shell
ls -l FILENAME
```

### Change Permissions
Change file permissions:
```shell
chmod MODE FILENAME
```

Examples:
```shell
chmod 755 script.sh      # rwx for owner, r-x for group and others
chmod +x script.sh       # Add execute permission for everyone
chmod u+w,g-w,o-w file   # Add write for user, remove for group/others
```

### Change Owner
Change file owner:
```shell
chown USER:GROUP FILENAME
```

---

## Searching

### Find Files/Directories
Search for files by name:
```shell
find SEARCH_PATH -name "PATTERN"
```

Examples:
```shell
find . -name "*.txt"              # Find all .txt files in current directory and subdirectories
find /Users -name "document.pdf"  # Find document.pdf in /Users
find . -type d -name "*data*"     # Find directories with "data" in the name
```

### Search File Contents
Search for text in files:
```shell
grep "PATTERN" FILENAME
```

Common flags:
- `-i`: Ignore case
- `-r`: Recursive search
- `-n`: Show line numbers
- `-l`: Show only filenames

Example:
```shell
grep -r "TODO" .                  # Find all TODOs in current directory
```

---

## Process Management

### View Running Processes
View all running processes:
```shell
ps aux
```

View process tree:
```shell
pstree
```

### Kill Processes
Kill a process by PID:
```shell
kill PID
```

Force kill:
```shell
kill -9 PID
```

### Monitor System
Interactive process viewer:
```shell
top
```

Enhanced version (if installed):
```shell
htop
```

---

## Redirection and Pipes

### Redirect Output
Save command output to file:
```shell
command > output.txt     # Overwrite file
command >> output.txt    # Append to file
```

### Redirect Input
Use file as input:
```shell
command < input.txt
```

### Pipe Commands
Send output of one command as input to another:
```shell
command1 | command2
```

Examples:
```shell
ls -la | grep ".txt"     # List only .txt files
ps aux | grep "chrome"   # Show only Chrome processes
```

---

## Useful Utilities

### Word Count
Count lines, words, and characters:
```shell
wc FILENAME
```

### File Information
Display file type:
```shell
file FILENAME
```

### Disk Usage
Check directory size:
```shell
du -sh DIRECTORY
```

Check disk space:
```shell
df -h
```

### Download Files
Download from URL:
```shell
curl -O URL
```

Wget alternative:
```shell
wget URL
```

### Compress/Extract Files
#### Tar Archives
Tar (Tape Archive) is a common Unix/macOS utility for collecting multiple files into a single archive file, while preserving file attributes and directory structure.

Create tar archive:
```shell
tar -cvf archive.tar FILES
```
- `-c`: Create new archive
- `-v`: Verbose (show files being processed)
- `-f`: Specify filename of the archive

Create gzipped tar archive (compressed):
```shell
tar -czvf archive.tar.gz FILES
```
- `-z`: Filter the archive through gzip compression

Extract tar archive:
```shell
tar -xvf archive.tar
tar -xzvf archive.tar.gz
```
- `-x`: Extract files from archive

---

## macOS Specific Commands

### Open Files/Applications
Open files with default application:
```shell
open FILENAME
```

Open applications:
```shell
open -a "APPLICATION_NAME"
```

Open directory in Finder:
```shell
open .
```

### Clipboard Operations
Copy to clipboard:
```shell
echo "text" | pbcopy
```

Paste from clipboard:
```shell
pbpaste > output.txt
```

### Screenshots
Take screenshot (saved to desktop):
```shell
screencapture -c        # Capture to clipboard
screencapture file.png  # Save to file
```

---

## Terminal Customization

### Change Shell
View current shell:
```shell
echo $SHELL
```

View available shells:
```shell
cat /etc/shells
```

Change default shell:
```shell
chsh -s /bin/zsh
```

### Bash Profile
Edit bash profile:
```shell
nano ~/.bash_profile
```

Apply changes:
```shell
source ~/.bash_profile
```

### Zsh Profile (if using zsh)
Edit zsh profile:
```shell
nano ~/.zshrc
```

Apply changes:
```shell
source ~/.zshrc
```

---

## Keyboard Shortcuts

- `⌘+A`: Move cursor to beginning of line
- `⌘+E`: Move cursor to end of line
- `⌘+U`: Delete from cursor to beginning of line
- `⌘+K`: Delete from cursor to end of line
- `⌘+W`: Delete the word before the cursor
- `⌘+C`: Cancel current command
- `⌘+Z`: Suspend current process
- `⌘+D`: Exit current shell (similar to `exit` command)
- `Tab`: Autocomplete commands, filenames, and directories
- `↑/↓`: Navigate through command history