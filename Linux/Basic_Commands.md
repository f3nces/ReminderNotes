# Basic Commands

[TOC]

### pwd (Print Working Directory)

Everything in Linux is a file, as you journey deeper into Linux you’ll understand this, but for now just keep that in mind. Every file is organized in a hierarchical directory tree. The first directory in the filesystem is aptly named the root directory. The root directory has many folders and files which you can store more folders and files, etc.

```
/

|-- bin

|   |-- file1

|   |-- file2

|-- etc

|   |-- file3

|   `-- directory1

|       |-- file4

|       `-- file5

|-- home

|-- var
```

The location of these files and directories are referred to as paths. If you had a folder named home with a folder inside of it named pete and another folder in that folder called Movies, that path would look like this: /home/pete/Movies



### cd (Change Directory)

There are two different ways to specify a path, with absolute and relative paths:
+ **Absolute path**: This is the path from the root directory. The root is the head honcho. The root directory is commonly shown as a slash. Every time your path starts with / it means you are starting from the root directory. For example, /home/pete/Desktop.
+ **Relative path**: This is the path from where you are currently in filesystem. If I was in location /home/pete/Documents and wanted to get to a directory inside Documents called taxes, I don’t have to specify the whole path from root like /home/pete/Documents/taxes, I can just go to taxes/ instead.

| Command   | Description                                                  |
| --------- | ------------------------------------------------------------ |
| **cd .**  | Current directory                                            |
| **cd ..** | Parent directory (directory above your current)              |
| **cd ~**  | Home directory (directory defaults to your “home directory") |
| **cd -**  | Previous directory                                           |



### ls (List Directories)

```bash
# List directories and files - current directory by default
ls
ls /home

# Shows all files/directories including the hidden (start with a .)
ls -a

# Shows a detailed list of files in a long format
ls -l

#Recursively list directory contents
ls -R 

# Sort by modification time, newest first
ls -t
```



### touch

Touch allows you the creation of **new empty files** or used to **change timestamps** on existing files and directories
```bash
# Create new file
touch newfile
```



### file

To find out what kind of file a file is, because in Linux, filenames aren’t required to represent the contents of the file
```bash
# Verify file type
file banana.jpg
```



### cat

Short for concatenate, it not only displays file contents but it can combine multiple files and show the output of them
```bash
# Content of 2 files
 cat dogfile birdfile
 
# Content of file with number all output lines
cat -n dogfile
```



### find

Find specific files/folders

```bash
# Find a folder
find /home -type d -name MyFolder

# Find a file from user with 52 kilobytes
find /home -type f -user <name> -size 52k
```

| Flag                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **-name** <name>                                             | Find files based on name                                     |
| **-type** <type>                                             | Type: f -file, d - directory                                 |
| **-user** <name>                                             | Find files based on username                                 |
| **-group** <name>                                            | Find files based on group name                               |
| **-size** <size>                                             | Find files based on size (**c** - bytes, **k** - kilobytes, **M** - megabytes, **G** -gigabytes) |
| **-newermt** [date and time]                                 | Find files modified after a specific date                    |
| **-newermt** [start date range] ! **-newermt** [end date range] | Find files based on date modified                            |
| **-newerat** [start date range] ! **-newerat** [end date range] | Find files based on date accessed                            |




### less

The text is displayed in a paged manner, so you can navigate through a text file page by page

```bash
# Verify file type
less sometext.txt
```

| Command                             | Description                                                  |
| ----------------------------------- | ------------------------------------------------------------ |
| **q**                               | Used to quit out of less and go back to your shell           |
| **Page up, Page down, Up and Down** | Navigate using the arrow keys and page keys                  |
| **g**                               | Moves to beginning of the text file                          |
| **G**                               | Moves to the end of the text file                            |
| **/<search>**                       | You can search for specific text inside the text document. Prefacing the words you want to search with / |
| **h**                               | Help                                                         |



### tar and gzip

```bash
# Compressing files with gzip (can't add multiple files into one archive)
gzip <mycoolfile>

# Decompressing files with gzip
gunzip <mycoolfile.gz>

# Creating archives with tar
#c - create
#v - verbose 
#f - the filename of the tar file has to come after this option
tar cvf mytarfile.tar mycoolfile1 mycoolfile2

# Unpacking archives with tar
#x - extract
#v - verbose
#f - the file you want to extract
tar xvf mytarfile.tar

# Compressing archives with tar and gzip
tar czf myfile.tar.gz

# Uncompressing archives with tar and gzip
tar xzf file.tar
```



### history

History of the commands that you previously entered

```bash
# View History
history

# Execute Previous Command
!<number_from _history>

# Clear up display
clear or Ctrl+L

# Clear history permanently
history -c && history -w
```



### cp

Copy file/folder. If the filename/folder name has spaces then you will need to encase the filename with speech marks such as cp "[filename with spaces]" [directory]

```bash
# Copy command
cp <filename/folder> <directory>
```

| Flag   | Description                                                  |
| ------ | ------------------------------------------------------------ |
| **-r** | Recursively copy the files and directories within a directory |
| **-i** | Prompt before overwriting a file                             |



### mv

Move file/folder or move multiple files/folders simultaneously. Also, can be used to rename file/folder

```bash
# Rename file/folder
mv <old filename/folder> <new filename/folder>

# Move file/folder
mv <filename> <directory>

# Move multiple files/folders simultaneously
mv [file1] [file2] [file3] -t [directory to move to]
```

| Flag   | Description                                                  |
| ------ | ------------------------------------------------------------ |
| **-i** | Prompt before overwriting a file                             |
| **-b** | Make a backup of an overwrited file and it will just rename the old version with a ~ |



### mkdir 

Make a Directory
```bash
# Make a directory
mkdir <directory>

# Make multiple directories at the same time
 mkdir <first_dir> <secon_dir>
 
# Create subdirectories at the same time
mkdir -p <dir/sub_dir/sub_sub_dir
```



### rm

Remove files and directories

```bash
# Remove a file
rm <filename>

# Remove a directory
rmdir <directory>
```

| Flag   | Description                                                  |
| ------ | ------------------------------------------------------------ |
| **-f** | Remove all files, whether they are write protected or not, without prompting the user |
| **-r** | Recursively remove all the files and any subdirectories it may have |
| **-i** | Prompt on whether you want to actually remove the files or directories                             |



### scp

Upload file to a remote machine

```bash
# Upload a file to another machine
scp <filename> <username>@<IP_of_remote_machine>:/<directory_to_upload_to>
```





## Wildcards

A wildcard is a character that can be substituted for a pattern based selection, giving you more flexibility with searches.
- \* the wildcard of wildcards, it's used to represent all single characters or any string.
- ? used to represent one character
- [] used to represent any character within the brackets
```

```