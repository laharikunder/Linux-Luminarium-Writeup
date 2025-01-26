# Linux Luminarium Writeup

## Introduction
Linux Luminarium is all about exploring system processes, file manipulation, and privilege escalation. 

---

## Challenge 1: Finding a Specific Keyword
### Aim:
- To Search through a directory of files to find a specific keyword.

### Steps:
1. Open the terminal and navigate to the directory where the files are stored:
   ```bash
   cd /path/to/directory
2. Use the grep command to search for the keyword:
   ```bash
   grep -r "KEYWORD" .
- The -r flag tells grep to search recursively through all subdirectories.
3. If the output is too long, you can filter it:
   ```bash
   grep -r "KEYWORD" . | head -n 10
- This shows only the first 10 results.


## Challenge 2: Identifying a Running Process
### Aim:
- To find a specific process that’s running on the system.

### Steps:
1. Use the ps command to list all running processes:
   ```bash
   ps aux
2. Command used to filter the output with grep to find the process which is required:
   ```bash
   ps aux | grep PROCESS_NAME
3. In order to to stop the process, note its Process ID (PID) and run:
   ```bash
   kill -9 <PID>
- -9 forcefully terminates the process without cleaning up.


## Challenge 3: Escalating Privileges
### Aim:
- To exploit a sudo permission to access restricted files.
### Steps:
1. To check what commands can be run with sudo:
   ```bash
   sudo -l
2. A command like less with sudo is used to read any file. For example:
   ```bash
   sudo less /path/to/restricted/file
3. Commands like less will enable us to escalate to a root shell.
4. Once inside the less pager, type ! followed by the command that we want to execute.
- For example, to spawn a root shell:
   ```bash
   !/bin/bash
