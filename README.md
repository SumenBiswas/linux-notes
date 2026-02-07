# Linux File Management Commands

A comprehensive guide to essential Linux file management commands for beginners and intermediate users.

## Table of Contents

- [Introduction](#introduction)
- [Basic Navigation](#basic-navigation)
- [File and Directory Operations](#file-and-directory-operations)
- [File Viewing and Editing](#file-viewing-and-editing)
- [File Search](#file-search)
- [File Permissions](#file-permissions)
- [File Links](#file-links)
- [Advanced Operations](#advanced-operations)
- [Best Practices](#best-practices)

## Introduction

This repository contains detailed explanations and examples of 20 essential Linux file management commands. These commands form the foundation of working with files and directories in any Linux/Unix environment.

## Basic Navigation

### 1. pwd (Print Working Directory)

Displays the full path of your current directory.

```bash
pwd
# Output: /home/username/documents
```

### 2. ls (List)

Lists files and directories in the current or specified directory.

```bash
ls                    # Basic listing
ls -l                 # Detailed listing with permissions
ls -a                 # Show hidden files
ls -lh                # Human-readable file sizes
ls -lt                # Sort by modification time
ls -lR                # Recursive listing
```

### 3. cd (Change Directory)

Navigate between directories.

```bash
cd /path/to/directory    # Navigate to specific path
cd ..                    # Go up one directory
cd ~                     # Go to home directory
cd -                     # Go to previous directory
cd                       # Go to home directory
```

## File and Directory Operations

### 4. mkdir (Make Directory)

Create new directories.

```bash
mkdir newdir                    # Create single directory
mkdir dir1 dir2 dir3           # Create multiple directories
mkdir -p path/to/nested/dir    # Create nested directories
mkdir -m 755 newdir            # Create with specific permissions
```

### 5. rmdir (Remove Directory)

Remove empty directories.

```bash
rmdir dirname              # Remove empty directory
rmdir dir1 dir2 dir3      # Remove multiple empty directories
```

### 6. touch

Create empty files or update timestamps.

```bash
touch newfile.txt                    # Create new file
touch file1.txt file2.txt           # Create multiple files
touch -t 202401011200 file.txt      # Set specific timestamp
```

### 7. rm (Remove)

Delete files and directories.

```bash
rm file.txt                    # Remove file
rm file1.txt file2.txt        # Remove multiple files
rm -r directory               # Remove directory recursively
rm -rf directory              # Force remove without prompts
rm -i file.txt                # Interactive mode (prompts before deletion)
rm *.log                      # Remove all .log files
```

**⚠️ Warning:** Be extremely careful with `rm -rf`, especially as root user.

### 8. cp (Copy)

Copy files and directories.

```bash
cp source.txt destination.txt        # Copy file
cp file.txt /path/to/directory/     # Copy to directory
cp -r sourcedir destdir             # Copy directory recursively
cp -i source.txt dest.txt           # Interactive (prompt before overwrite)
cp -u source.txt dest.txt           # Copy only if source is newer
cp -v source.txt dest.txt           # Verbose mode
```

### 9. mv (Move)

Move or rename files and directories.

```bash
mv oldname.txt newname.txt          # Rename file
mv file.txt /path/to/directory/    # Move file
mv -i source.txt dest.txt          # Interactive mode
mv -u source.txt dest.txt          # Move only if source is newer
mv *.txt /destination/             # Move all .txt files
```

## File Viewing and Editing

### 10. cat (Concatenate)

Display and concatenate file contents.

```bash
cat file.txt                           # Display file contents
cat file1.txt file2.txt               # Display multiple files
cat file1.txt file2.txt > merged.txt  # Merge files
cat > newfile.txt                     # Create file (Ctrl+D to save)
cat -n file.txt                       # Show line numbers
```

### 11. less

View file contents page by page (scrollable).

```bash
less largefile.txt        # View file
less -N file.txt         # Show line numbers
```

**Navigation in less:**
- `Space` or `f` - Forward one page
- `b` - Backward one page
- `/pattern` - Search forward
- `?pattern` - Search backward
- `q` - Quit

### 12. head

Display the first lines of a file.

```bash
head file.txt            # First 10 lines (default)
head -n 20 file.txt      # First 20 lines
head -n -5 file.txt      # All except last 5 lines
head -c 100 file.txt     # First 100 bytes
```

### 13. tail

Display the last lines of a file.

```bash
tail file.txt            # Last 10 lines (default)
tail -n 20 file.txt      # Last 20 lines
tail -f logfile.txt      # Follow file in real-time (Ctrl+C to exit)
tail -F logfile.txt      # Follow file, retry if inaccessible
```

## File Search

### 14. find

Search for files and directories based on various criteria.

```bash
find /path -name "filename.txt"           # Find by name
find . -name "*.log"                      # Find all .log files
find . -type f                            # Find only files
find . -type d                            # Find only directories
find . -size +100M                        # Files larger than 100MB
find . -size -10k                         # Files smaller than 10KB
find . -mtime -7                          # Modified in last 7 days
find . -user username                     # Files owned by user
find . -perm 644                          # Files with specific permissions
find . -name "*.tmp" -delete              # Find and delete
find . -name "*.txt" -exec grep "pattern" {} \;   # Find and execute command
```

### 15. locate

Quickly find files using a pre-built database.

```bash
locate filename              # Find file
locate -i filename          # Case-insensitive search
locate -c filename          # Count matches
updatedb                    # Update locate database (requires root)
```

### 16. grep

Search for patterns within files.

```bash
grep "pattern" file.txt                    # Search in file
grep -i "pattern" file.txt                # Case-insensitive
grep -r "pattern" /directory              # Recursive search
grep -n "pattern" file.txt                # Show line numbers
grep -v "pattern" file.txt                # Invert match (exclude)
grep -c "pattern" file.txt                # Count matches
grep -l "pattern" *.txt                   # List filenames only
grep -w "word" file.txt                   # Match whole word
grep -A 3 "pattern" file.txt              # Show 3 lines after match
grep -B 3 "pattern" file.txt              # Show 3 lines before match
```

## File Permissions

### 17. chmod (Change Mode)

Modify file and directory permissions.

```bash
chmod 755 file.sh                    # rwxr-xr-x
chmod 644 file.txt                   # rw-r--r--
chmod +x script.sh                   # Add execute permission
chmod -w file.txt                    # Remove write permission
chmod u+x file.sh                    # Add execute for user
chmod g-w file.txt                   # Remove write for group
chmod o+r file.txt                   # Add read for others
chmod -R 755 directory              # Recursive permission change
```

**Permission Numbers:**
- `4` = read (r)
- `2` = write (w)
- `1` = execute (x)
- `0` = no permission

**Examples:**
- `7` (4+2+1) = rwx
- `6` (4+2) = rw-
- `5` (4+1) = r-x
- `4` = r--

### 18. chown (Change Owner)

Change file ownership and group.

```bash
chown user file.txt                  # Change owner
chown user:group file.txt           # Change owner and group
chown -R user:group directory       # Recursive change
chown :group file.txt               # Change group only
```

**Note:** Usually requires root privileges.

## File Links

### 19. ln (Link)

Create hard links and symbolic links.

```bash
ln sourcefile hardlink              # Create hard link
ln -s /path/to/file symlinkname    # Create symbolic link
ln -s /path/to/dir linkname        # Link to directory
```

**Difference:**
- **Hard link:** Another name for the same file (same inode)
- **Symbolic link:** A pointer/shortcut to another file

## Advanced Operations

### 20. file

Determine file type.

```bash
file document.pdf              # Identify file type
file *                        # Check all files in directory
file -b image.jpg            # Brief output (no filename)
file -i file.txt             # Show MIME type
```

## Best Practices

### Safety Tips

1. **Always use `-i` flag** with `rm`, `cp`, and `mv` when working with important files
2. **Double-check** before using `rm -rf`
3. **Use tab completion** to avoid typos in file paths
4. **Make backups** before bulk operations
5. **Test commands** on sample files first

### Efficiency Tips

1. **Use wildcards** (`*`, `?`, `[]`) for bulk operations
2. **Combine commands** with pipes (`|`) for powerful operations
3. **Use command history** (`Ctrl+R` to search)
4. **Create aliases** for frequently used commands
5. **Learn keyboard shortcuts** in terminal

### Common Command Combinations

```bash
# Find large files
find . -type f -size +100M -exec ls -lh {} \;

# Search and replace in multiple files
find . -name "*.txt" -exec sed -i 's/old/new/g' {} \;

# Count files in directory
ls -1 | wc -l

# Find duplicate files by size
find . -type f -exec ls -s {} \; | sort -n

# Backup with timestamp
cp important.txt "important_$(date +%Y%m%d_%H%M%S).txt"
```

## Additional Resources

- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/)
- [Linux Command Line Basics](https://www.gnu.org/software/bash/manual/)
- [Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/fhs.shtml)

## Contributing

Feel free to contribute by:
- Adding more examples
- Suggesting best practices
- Reporting errors or unclear explanations
- Adding translations

## License

This documentation is provided as-is for educational purposes.

## Author

Created as a reference guide for Linux file management commands.

---

**Last Updated:** February 2026

**Note:** Always refer to the manual pages (`man command`) for the most comprehensive and system-specific information.
