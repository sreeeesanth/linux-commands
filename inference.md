# Linux Command Line Operations & Inferences

## 1. Directory Navigation
In this section, I explored the Linux filesystem hierarchy and practiced moving between directories using absolute and relative paths.

| Command | Resultant Path | Inference / Understanding |
| :--- | :--- | :--- |
| `mkdir ev4` | `/home/sree/ev4` | Created a new directory named `ev4`. |
| `cd ev4` | `/home/sree/ev4` | Changed the working directory to the newly created folder. |
| `mkdir 57` | `/home/sree/ev4/57` | Created a directory labeled with my roll number. |
| `cd 57` | `/home/sree/ev4/57` | Navigated into my specific roll number folder. |
| `cd -` | `/home/sree/ev4` | Returns to the **previous** directory (the "back" button of terminal). |
| `cd -` | `/home/sree/ev4/57` | Toggles back to the roll number directory. |
| `cd .` | `/home/sree/ev4/57` | `.` represents the **current** directory; no movement occurs. |
| `cd ..` | `/home/sree/ev4` | Moves up one level to the **parent** directory. |
| `cd ~` | `/home/sree` | Navigates to the current user's **Home** directory. |
| `cd /` | `/` | Navigates to the **Root** directory (the base of the entire system). |
| `ls -l` | *(Root listing)* | Lists files in root with detailed info (permissions, owner, size). |
| `cd media` | `/media` | Enters the media directory (where external drives are mounted). |
| `cd` | `/home/sree` | Typing `cd` alone always returns the user to the **Home** folder. |
| `pwd` | `/home/sree` | **Print Working Directory**: Confirms the current absolute path. |
| `cd /media` | `/media` | Navigates to media using an **absolute path** from root. |
| `ls -al` | *(List all)* | Lists all files, including **hidden** files (those starting with `.`). |

---

## 2. File and Directory Manipulation
This section demonstrates the lifecycle of files and directories (creation to deletion).

* **Path:** `cd ~/ev4/57`
* `mkdir emptydummy`: Created a folder intended for deletion.
* `mkdir dummy`: Created a second folder.
* `cd dummy` -> `touch file1 file2`: Created two empty files inside `dummy`.
* `ls -l`: Verified both files exist.
* `rm -i file2`: The `-i` flag is **interactive**; it asks for confirmation before deleting. 
* `cd ..`: Moved back to the roll number directory.
* `rmdir emptydummy`: Successfully deleted because the directory was **empty**.
* `rmdir dummy`: **FAILED**. `rmdir` cannot delete directories that contain files.
* `rm -r dummy`: **Recursive delete**. This safely removes the directory and all files inside it.

---

## 3. File Content, Redirection, and Searching

Using `cat` to manipulate text data and `grep` to filter it.

* `cat > file1.txt`: Created file and added: *'My first line'*.
* `cat > file2.txt`: Created file and added: *'Hello Second line'*.
* `cat > file3.txt`: Created file and added: *'Hello line'*.
* `cat file1.txt file2.txt > file_combined.txt`: The `>` operator **overwrites** or creates a new file combining 1 and 2.
* `cat file3.txt >> file_combined.txt`: The `>>` operator **appends** file 3 to the end without deleting existing text.
* `grep -i hello file*`: Searched for "hello" (case-insensitive) in all files starting with "file". 
* `cp file1.txt ~/ev4`: Copied the file to the parent folder.
* `mv file_combined.txt combined`: Renamed the combined file to just `combined`.

---

## 4. File Permissions (`chmod`)

Permissions define who can Read (**r**), Write (**w**), or Execute (**x**) a file.

| Command | Mode | Inference |
| :--- | :--- | :--- |
| `chmod u+x combined` | Symbolic | Added **Execute** permission specifically for the **User** (owner). |
| `chmod g-r combined` | Symbolic | Removed **Read** permission from the **Group**. |
| `chmod 777 combined` | Numeric | Set full permissions (`rwxrwxrwx`) for User, Group, and Others. |

> **Note:** Permissions for directories differ. `x` (execute) on a directory is required to `cd` into it.

---

## 5. User Management and Communication
* `sudo useradd alice`: Created a new user account.
* `sudo passwd alice`: Set/Changed the password for user Alice.
* `write alice`: Initiated a real-time message to Alice (requires both users to be logged in).
* `mesg n`: Command used to block incoming messages from other users.
* `sudo userdel alice`: Removed the user account from the system.
