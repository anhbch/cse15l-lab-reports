***
# Week 2 Lab Report 
***
*(This instruction steps are for Macbook. Some steps might be different if you are on Windows)* 
## Installing Visual Studio Code
* Go to the [Vscode website](https://code.visualstudio.com/) and click the download button and follow the steps to install Vscode. 
* After installing, open VScode and you will see this window: 
![Image](photo/Vscode.png)

## Remotely Connecting 
* **Find account:** Look up course-specific account for CSE 15L [here](https://sdacs.ucsd.edu/~icc/index.php). Type your UCSD username and student ID (start with an A) to find your personal account. You will need to reset your password before using your account to connect to the server. 
* **Connect to a remote host:** Using Visual Studio Code to the remote computer using VSCode’s remote option. In VScode:
    1. Open a terminal in VSCode by using Command + `, or using the Terminal → New Terminal menu option.
    2. Use this command to connect to the server: (replace the *ahw* with the letters in your course-specific account)
        ```
        $ ssh cs15lwi22ahw@ieng6.ucsd.edu
        ```
    3. If this is your first time connect to the server, type `yes` to the message and press enter. Then, enter your password. Your terminal window should look like this after it is connected:
    ![Image](photo/loggedin.png)

## Run Some Commands
* After connecting to remote server in your terminal, you can try running different commands. 
* **This is some useful command to try:**
    ```
    cd: change directory 
    ls: listing directory 
    pwd: print working directory
    mkdir: make a new directory
    cp: copy files and directories
    cat: display the content of text files and to   combine several files into one file
    exit: log out of the remote server in your terminal
    ```
    *Sample terminal window for some useful commands:*
    ![Image](photo/commandex3.png)
    ![Image](photo/commandex1.png)
    ![Image](photo/commandex2.png)

## Moving Files with SCP
* **scp:**  copy file(s) from your computer to remote computer. The command is always run from *client* (from your computer, not logged into `ieng6`)
* To try command `scp`:
    1. Create a file on your computer called `WhereAmI.java`.
    2. Run the file by using `javac` and `java` on your computer.
    3. In terminal from the directory where you made this file, use the command: (replace the *ahw* with the letters in your course-specific account)
        ```
        $ scp WhereAmI.java cs15lwi22ahw@ieng6.ucsd.edu:~/
        ```
    4. Then use `ssh` to log into *ieng6* again, you can see the file in your home directory. 
        ![Image](photo/scp.png)

## Setting an SSH Key
* Create an SSH key will let us use `ssh` and `scp` without having to enter your password everytime. 
* Steps to set up **ssh key**:
    * **On your client (your computer without logging into `ieng6`):** Type this command and follow these steps:
        ```
        $ ssh-keygen
        Generating public/private rsa key pair.
        Enter file in which to save the key (/Users/kimanh/.ssh/id_rsa): /Users/kimanh/.ssh/id_rsa
        Enter passphrase (empty for no passphrase): 
        Enter same passphrase again: 
        Your identification has been saved in /Users/kimanh/.ssh/id_rsa.
        Your public key has been saved in /Users/kimanh/.ssh/id_rsa.pub.
        ```
    * Then, copy the public (not the private) key to the .ssh directory of your user account on the server by the following steps:
        1. Type this command to log into your server and enter your password:
            `$ ssh cs15lwi22ahw@ieng6.ucsd.edu`
        2. On server, use command `$ mkdir .ssh` to make a new directory. Then log out of the server.
        3. On the client (your computer), type this command `$ scp /Users/kimanh/.ssh/id_rsa.pub cs15lwi22@ieng6.ucsd.edu:~/.ssh/authorized_keys`
    * After all the steps, you can use `ssh` and `scp` without using your password. Your terminal window will look like this:
        ![Image](photo/sshkey.png)

## Optimizing Remote Running
* Using command in quotes " " at the end of `ssh` will log into the remote server and then directly run the code on the remote server. 
* Use semicolon ; to run multiple commands on the same line. 
* Use the up-arrow on your keyboard to recall the last command that was run. 

*Example using quotes and semicolon to log in and run multiple commands directly on the remote server:*
![Image](photo/optimizeex.png)







