# Lab Report 1   Taiki Yoshino (A17492011)

## Installing VSCode
**#Note**  
To download the VSCode, you should go to this website: https://code.visualstudio.com/ and choose the compatible one with your device(ex. Mac). (However, since I have already downloaded it in the CSE 11, I didn't need to do it this time.) 

![image](lab-report1-images/vscode-download-image.png)

**#Note**  
After you download VSCode and opened it, it will take you to this kind of screen. (I think this page is slightly different from the one I first installed.) 

![image](lab-report1-images/vscode-home-image.png)

## Remotely Connecting
**#Note**  
To use terminal in VSCode, I can click "Terminal" in the menu bar and go on to "New Terminal." Then, the terminal come up from the bottom up. (If you use Windonws devices, one more step is necessary to install git: **git bash**)  

![image](lab-report1-images/vscode-terminal-image.png)

**#Note**  
Next, you are going to use "ssh" in the command. SSH represents Secure Shell, which allow you to access a remote computer. You should type a course-specific account to log in.(I struggled with this process because I forgot to replace the "zz" with my account characters.)  
After that, you will be required to enter a login password. (this password is the same as using the UCSD account.) As a note, you don't have to worry that the entered characters will not be reflected on the screen; it is because of security reasons. 

![image](lab-report1-images/vscode-ssh-image.png)

If you success in login in, this output will appear.

![image](lab-report1-images/vscode-loginoutput-image.png)

## Run Some Commands
**#Note** 
Now, you can edit the file using some commands.

* pwb : working directory (current directory)
* ls  : name of contents
* cat <file1> <file2>: prints contents of one or more files given by the paths.
* cd  : change directory
* cd ~: Go to home directory
* mkdir: make a new directory

In the example below, I created a new directory called “taiki” using “mkdir” command and moved there using “cd.” I also went back to my home directory using “~.”  
![image](lab-report1-images/vscode-command-image.png)

**#Note**  
To logout the page, 
Ctrl-D
Run the command exit
