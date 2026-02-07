1. ls - Lists directory contents. Use ls -l for detailed view with permissions and sizes, ls -a to show hidden files, or ls -lh for human-readable file sizes.

2. cd - Changes directory. cd /path/to/directory moves you there, cd .. goes up one level, and cd ~ returns to your home directory.

3. pwd - Prints the current working directory path, showing exactly where you are in the filesystem.

4. mkdir - Creates new directories. mkdir dirname makes one directory, while mkdir -p path/to/nested/dir creates nested directories all at once.

5. rmdir - Removes empty directories. Use rmdir dirname to delete a directory only if it contains nothing.

6. rm - Deletes files and directories. rm file.txt removes a file, rm -r directory recursively deletes a directory and its contents, and rm -f forces deletion without prompts.

7. cp - Copies files and directories. cp source.txt destination.txt copies a file, while cp -r sourcedir destdir recursively copies entire directories.

8. mv - Moves or renames files. mv oldname.txt newname.txt renames a file, and mv file.txt /new/location/ moves it to a different directory.

9. touch - Creates empty files or updates timestamps. touch newfile.txt creates a blank file if it doesn't exist.

10. cat - Displays file contents. cat file.txt shows the entire file, and cat file1.txt file2.txt > combined.txt concatenates multiple files.

11. less - Views file contents one page at a time. less largefile.txt lets you scroll through files using arrow keys and search with /.

12. head - Shows the first lines of a file. head file.txt displays the first 10 lines by default, or head -n 20 file.txt shows the first 20 lines.

13. tail - Shows the last lines of a file. tail file.txt displays the last 10 lines, and tail -f logfile.txt follows a file in real-time, useful for monitoring logs.

14. find - Searches for files and directories. find /path -name "*.txt" finds all .txt files, and find . -type d finds all directories in the current location.

15. locate - Quickly finds files by name using a pre-built database. locate filename searches the entire system faster than find, though you may need to run updatedb first.

16. grep - Searches file contents for patterns. grep "search term" file.txt finds lines containing that term, and grep -r "pattern" /directory searches recursively through directories.

17. chmod - Changes file permissions. chmod 755 script.sh sets specific permissions, or chmod +x file.sh makes a file executable.

18. chown - Changes file ownership. chown user:group file.txt changes both owner and group, requiring root privileges for most operations.

19. ln - Creates links to files. ln -s /path/to/file linkname creates a symbolic link (shortcut), while ln file hardlink creates a hard link.

20. file - Determines file type. file unknown.dat tells you what kind of file something is, regardless of its extension.
