## Quick Sed Script

A simple Bash script for performing search and replace operations on a target file using `sed`. This script also provides additional features like creating backups, comparing file differences, and searching for occurrences.

### Features
- Search and replace text in a file.
- Search for occurrences of a string in a file.
- Backup the original file before making changes.
- Show differences between the original and modified file.
- Output the final modified file.
- Interactive mode for selecting which lines to modify.

### Usage
```
./quick-sed.sh [options] <search> <replace> <file>
./quick-sed.sh -s <search> <file>
```

#### Options:
| Option | Description |
|--------|-------------|
| `-h`, `--help` | Show help information |
| `-b`, `--backup` | Create a backup of the original file before making changes |
| `-o`, `--output-result` | Output the final modified file content |
| `-c`, `--compare` | Show the differences between the original and modified file |
| `-s`, `--search` | Search for occurrences of a string in the target file |

### Examples
#### Replace text in a file
```sh
./quick-sed.sh hello bye test.txt
```
Replaces all occurrences of `hello` with `bye` in `test.txt`.

If there are multiple occurrences of `hello` in `test.txt`, the user can choose which lines to modify：

```
$ ./quick-sed.sh -o hello bye test.txt
Multiple occurrences of 'hello' found in 'test.txt':
1:hello world
5:hello world
7:hello to you.
Enter the line numbers to modify (comma-separated) or 'all' to replace all:
5
Replaced occurrences in selected lines of 'test.txt'.
Final file content of 'test.txt':
hello world

this is a quck sed script

bye world

hello to you.

bye
```


#### Replace with backup
```sh
./quick-sed.sh -b hello bye test.txt
```
Creates a backup of `test.txt` before making changes.

#### Show differences after replacement
```sh
./quick-sed.sh -c hello bye test.txt
```
Displays the differences between the original and modified file.

#### Search for occurrences of a word
```sh
./quick-sed.sh -s hello test.txt
```
Lists all occurrences of `hello` in `test.txt`.

#### Backup, compare, and output the final file
```sh
./quick-sed.sh -b -c -o hello bye test.txt
```
Creates a backup, shows differences, and outputs the modified file.

### Requirements
- Bash
- sed
- grep
- diff
