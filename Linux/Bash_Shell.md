### Cursor Shortcuts
```
Ctrl + a  – Go to the start of the command line
Ctrl + e  – Go to the end of the command line

Alt  + b  – Move backward one word (or go to start of word the cursor is currently on)
Alt  + f  – Move forward one word (or go to end of word the cursor is currently on)

Ctrl + k  – Delete from cursor to the end of the command line
Ctrl + u  – Delete from cursor to the start of the command line

# Rarely used...
Ctrl + w  – Delete from cursor to start of word (i.e. delete backwards one word)
Ctrl + y  – Paste word or text that was cut using one of the deletion shortcuts (such as the one above) after the cursor
Ctrl + xx – Move between start of command line and current cursor position (and back again)
Alt  + d  – Delete to end of word starting at cursor (whole word if cursor is at the beginning of word)
Alt  + c  – Capitalize to end of word starting at cursor (whole word if cursor is at the beginning of word)
Alt  + u  – Make uppercase from cursor to end of word
Alt  + l  – Make lowercase from cursor to end of word
Alt  + t  – Swap current word with previous
Ctrl + f  – Move forward one character
Ctrl + b  – Move backward one character
Ctrl + d  – Delete character under the cursor
Ctrl + h  – Delete character before the cursor
Ctrl + t  – Swap character under cursor with the previous one
```

#### Cutting / Pasting
```
# In PuTTy, selecting text with the mouse will automatically copy the content. Right-click will paste onto command prompt 
Ctrl + W : Cut the word before the cursor
Ctrl + K : Cut the part of the line after the cursor
Ctrl + U : Cut the part of the line before the cursor
Ctrl + Y : Paste (y stands for “yank”)
```

#### Bash command history
```
$ history | grep <command>

OR 

# Bash also has a special “recall” mode you can use to search for commands you’ve previously run:
Ctrl+R: Recall the last command matching the characters you provide
Ctrl+O: Run a command you found with Ctrl+R or Press [ESC] then [ENTER]
Ctrl+G: Leave history searching mode OR use [ESC]
```

### Browse through a file quickly
```
$ grep -n port  hive-site.xml # Looking for "port". -n : Prints line numbers
674:      <name>hive.server2.thrift.http.port</name>
694:      <name>hive.server2.thrift.port</name>

cat --number hive-site.xml | more +660 # Shows from line 660 onwards so we can see the beginning of the XML node 
660     ...
...
674        <name>hive.server2.thrift.http.port</name>
675        <value>10001</value>
676      </property>
...
```

### Working With Foreground Processes
```
Ctrl + C : Interrupt (kill) the current foreground process running in in the terminal. Sends the SIGINT signal to the process, which is technically just a request—most processes will honor it, but some may ignore it.
Ctrl + Z : Suspend the current foreground process running in bash. This sends the SIGTSTP signal to the process. To return the process to the foreground later, use the fg process_name command.
Ctrl + D : Close the bash shell. This sends an EOF (End-of-file) marker to bash, and bash exits when it receives this marker. This is similar to running the exit command.
```

### Working With Processes
```
$ command # Followed by [CTRL + Z] suspends it    
bg # Runs the suspended process in background
fg # Brings the background process to the foreground
jobs # Observe the background processes

$ command & # Runs it in the background

# List processes as a Tree
pstree -p # -p : process id, 
```

### Terminal / Screen
```
Ctrl + L : Clear the screen. This is similar to running the “clear” command.
Ctrl + S : Stop all output to the screen. This is particularly useful when running commands with a lot of long, verbose output, but you don’t want to stop the command itself with Ctrl+C.
Ctrl + Q : Resume output to the screen after stopping it with Ctrl+S.
```

### Searching for files
```
find / -name filename123 2>&1 | grep -v denied # Exclude the 'Permission denied' messages

```
###### References:
- [GNU Readline Library](https://tiswww.case.edu/php/chet/readline/readline.html)
- https://www.howtogeek.com/howto/ubuntu/keyboard-shortcuts-for-bash-command-shell-for-ubuntu-debian-suse-redhat-linux-etc/





### Shell script execution
```Shell
$ cat > 1.sh
echo "Hi"
$ cat 1.sh
echo "Hi"
$ ll
total 56
-rw-r--r-- 1 dwh   seacct   10 Jun 21 16:12 1.sh
$ sh 1.sh
Hi
$ ./1.sh
bash: ./1.sh: Permission denied
$ . ./1.sh
Hi
```
- https://superuser.com/questions/176783/what-is-the-difference-between-executing-a-bash-script-vs-sourcing-it/176788#176788 
- https://unix.stackexchange.com/questions/291404/why-does-bashs-source-not-need-the-execution-bit 
 
