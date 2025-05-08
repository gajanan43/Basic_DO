## Linux OS:<br>
1. Open Source: Linux is freely available and its source code can be modified and distributed.<br>
2. Multiuser and Multitasking: Supports multiple users and runs many tasks simultaneously.<br>
3. Security: Built-in security features like user permissions, firewalls, and encryption.<br>
4. Stability and Reliability: Rarely needs rebooting and is known for long uptimes.<br>
5. Portability: Can run on various hardware platforms (x86, ARM, etc.).<br>
6. Shell and Command Line Interface: Powerful tools for system control and automation.<br>

# Shell Scripting

## 1)Where I am currently?
    pwd                 ->print working directory.

## 2)How to change the directory?
    cd                  ->Change Directory
    ex:-cd Desktop      ->Go to Desktop directory.

## 3)How back to the previous directory?
    cd ..               ->Back to the previous directory
    cd ../..            ->we can back two preivous directory
    cd first/second     ->we can go inside or ahead two next directory

## 4) How to list the files & folders?
    ls                  -> will show all files 
    ls -ltr             -> show files with timestamp

## 5) How to create a file?
    touch file_name     -> create a file

## 6) Difference between vi & touch command: 

- touch command we use in automation.
- vi command we use for write inside the file or in case file dosen't exists then it create and open for write inside the file.
    
## 7) How to write a file in Linux?
    vi file_name        -> will open the file for writing the content

## 8) How to use insert command in linux?

- once you use vi command to open the file then you have to do next steps:
    - press 'esc' key then 'i' for insert
    - after this you can write somthing in your file.
    - after writing the file you need to save the file using 'esc' + ':wq!' for saving the file
    - for reading the content of the file you need to use

## 9)How to read a content of the file
    cat file_name          -> will show all the content of file.

## 10)How to delete a  file or directories(folder)?
    rm file                ->Deletes a file                               
    rm -i file             ->Prompts for confirmation before deleting     
    rm -f file             ->Forces deletion (no prompt)                  
    rm -r folder           ->Recursively deletes a directory and contents 
    rm -rf folder          ->Forcefully deletes a directory (no prompt)   

## 11) How to create folders?
    mkdir folder_name         ->cerate a folder(directory)

## 12) How to check CPU and RAM of a linux machine?

- for RAM you can use ```free``` command
- for CPU you can use ```nproc``` command
- using ```top``` command you can easily identify the processes that are running on your machine

## 13) How to analyze the health of a Node?
-  executing below commands
```df -h``` : Displays disk space usage of file systems in a human-readable format (e.g., GB, MB).

```free -g``` : Shows the system's memory usage (free, used, and total) in gigabytes.

```nproc``` : Outputs the number of processing units (CPU cores) available.

## 14) man command in Linux: 
- man is stands for manual 
- Just suffix any command with man and simply type the command.
- It will give you the detail information of that perticular command
- ex. man touch , man ls

## 15) What is the purpose of --> #!/bin/bash
    #!/                  -> shebang
- bash or sh or ksh or dash this are differnt executables of your shell script 
- executables that run the program 

## 16) Difference between sh , bash , dash and ksh:

- sh --> Original Unix shell, basic and portable.
- bash --> Advanced, user-friendly, and feature-rich shell.
- dash --> Minimal, fast, and optimized for system scripts.
- ksh --> Powerful shell with advanced scripting for enterprises.

## 17) How to execute a shell Script?
- for any executables file we can use 
    
    ```./file_name or sh file_name```

## 18) How to grant permissions in linux?
- using chmod command you can change permissions access mode 
 
 ```chmod 777 file_name```
 -  this each 7 is stands for :
    - 4 -> read
    - 2 -> write 
    - 1 -> execute

## 19) How to check the history of commands?
    history                    ->view all the history

## 20) What is the purpose of shell scripting in devops?
- shell scripting languages, such as bash, are used for automating tasks in devops workflow.
- They provide a command-line interface for interacting with the operating system and executing commands.
- shell scripts use variables to store and manipulate data.

## 21) Good practices in writing a script : 
- always try to mention those things - 
    - Author of script
    - date 
    - purpose of the script
    - version
    - you can also use echo statements to improve your script understanding
    - Developer use ```set -x``` command to run script in debug mode, that helps you to analyze your output follw through your input command.

## 22) What are processes, How to list them and Find process ID?
- processes are nothing but the differnt tasks that are running on the machine.
- using ```ps -ef``` this command you can find process ID.

## 23) grep and pipe commands to filter the ```ps -ef``` output:
- if in case you need to retrive the amazone processes ID then you can use ```ps -ef | grep "amazone"```
- pipe sends the output of the first command to the second command

## 24) IMP interview question on Pipe : 

- if we use ```date | echo"today is "```, why date is not print after echo statement?<br>
ANS :- The ```date``` command does pass its output to the ```pipe```. However, in the command ```date | echo "today is "```, the ```echo``` command does not read from the ```pipe```. ```Pipes``` only work if the command following the ```pipe``` is designed to accept input from the ```pipe```. Since ```echo``` does not read from ```stdin```, it simply prints "today is " and ignores the output of ```date```.

So yes, the ```pipe``` works, but ```echo``` is not using the data passed to it.


## 25) ```awk``` command :

- ```awk``` is a pattern scanning and processing language 
- In simple words getting specific value from the entire row
- ex. ```ps -ef | grep "amazone" | awk -F " " '{print $2}'```


## 26) ```set -e``` and ```set -o pipefail``` : 

- ```set -e ``` is use for detection of the error in your script
- and ```set -o pipefail``` is use for pipefail detect and stop execution of the script.

## 27) How to search error in remote logfile?

- by using ```curl URL``` or ```curl location _of_your_logfile```
- ex. ```curl URL | grep ERROR``` -> will show all error in logfile


## 28) ```wget``` command and use-case : 

- ```wget``` command download the provide file
- ```wget URL_of_logfile``` -> will download this file in current directory

## 29) How to use find command? 

- whenever you go for using ```find``` command through your current directory then it will show you permission denied.  


- for that you have to swich on the root user.
- you can use ```sudo su -``` or ```sudo find / -name file_name```

## 30) if-else in shell scripting : 

- syntax- 
    ->
    
    a=4
    
    b=10

    if [ "$a" -gt "$b"]
    
    then echo "a is greater than b"

    else echo "b is grater than a"

    fi 

- this is how if- else loop syntax looks like

## 31) for loop in shell scripting : 

- syntax-
     
    for i in {1..50}

    do
  
    echo $i
    
    done

- this is how for loop looks like.


## 32) ```trap``` command : 
- this is use for traping signals
- signals are messages used to control or communicate with running programs, like stoping, pausing or restarting them.



