
# Shell Scripting Interview Questions

## 1) List some of the commonly used shell commands?
- ```ls``` - Lists files and directories.
    - ```ls -l``` (detailed list view)
    - ```ls -a``` (shows hidden files)
- ```cd``` - Changes the current directory.
    - ```cd ..``` (move to the parent directory)
- ```pwd``` - Prints the current working directory.
- ```mkdir``` - Creates a new directory.
    - ```mkdir``` dirname
    - ```rmdir``` - Removes an empty directory.
    - ```rmdir``` dirname
- ```rm``` - Removes files or directories.
    - ```rm filename``` (remove file)
    - ```rm -r dirname``` (remove directory recursively)
- ```cp``` - Copies files or directories.
    - ```cp``` source destination
- ```mv``` - Moves or renames files or directories.
- ```touch``` - Creates an empty file.
- ```cat``` - Displays the contents of a file.
    - ```cat file.txt```
- ```less``` - Views file content page by page.
- ```find``` - Searches for files or directories.
    - ```find /path -name filename```


## 2) Write a shell Script to list all processes : 
- ```ps -ef```
- only list process id -> ```ps -ef | awk -F " " '{print $2}'```


## 3) write a script to print only error from a remote log file : 

- we are using ```curl , | , grep ```command to get output
- eg. ```curl url | grep "error"``` 

## 4) Write a shell script to print numbers divided by 3, 5 and not 15 
- script : 
    
    #!/bin/bash
    
for i in {1..50}; do

    if [[ ( $((i % 3)) -eq 0 || $((i % 5)) -eq 0 ) && $((i % 15)) -ne 0 ]]; then

    echo "$i"
    fi

done

## 5) Write a script to print number of 's' in mississippi
- x=mississippi  -> use this as a variable 
- ```grep  -o "s" <<<"$x" | wc -l```

## 6) How will you debug the shell script?
- use ```set -x``` command

## 7) What is crontab in linux? can you provide an example of usage?

## 8) How to open a read only file?
- ```vi -r filename```

## 9) what is the difference between soft and hard link?

## 10) what are some disadvantages of shell Scripting?
- shell Scripting has the following disadvantages :
    - error are frequent and costly, and a single error can alter the command.
    - the execution speed is slow
    - bugs or inadequacies in the language's syntax or implementation 
    - large, complex tasks aren't well suited to it 
    - contrary to other Scripting languages, etc., it provides a minimal data structure 
    - every time a shell command is executed, a new process is launched.


## 11) is bash dynamic or statically typed and why?

## 12) how will you replace multiple occurrences of a string in a file?

## 13) explain about a network troubleshooting utility?
- ```traceroute url or link ```

## 14) how will you sort list of names in a file?

## 15) how will you manage logs of a system that generate huge log files everyday? 
