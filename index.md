# Lab Report 1   Taiki Yoshino (A17492011)

## Installing VSCode
**#Note**  
To download the Visual Studio Code, you should go to this website: https://code.visualstudio.com/ and choose the compatible one with your device (ex. Mac). (However, since I have already downloaded it in the CSE 11, I didn't need to do it this time.) 

<img src="lab-report1-images/vscode-download-image.png" width="75%">

**#Note**  
After you download VSCode and open it, it will take you to this kind of screen.

<img src="lab-report1-images/vscode-home-image.png" width="75%">

## Remotely Connecting
**#Note**  
To use terminal in VSCode, you can click "Terminal" in the menu bar and go on to "New Terminal." Then, the terminal come up from the bottom up. (If you use Windonws devices, one more step is necessary to install git: **git bash**)  

<img src="lab-report1-images/vscode-terminal-image.png" width="75%">

**#Note**  
Next, you are going to use "ssh" in the command. SSH represents Secure Shell, which allow you to access a remote computer. You should type a course-specific account to log in. (I struggled with this process because I forgot to replace the "zz" with my account characters. Also, note that $ originally exists, so you have to write things after it.)  
```  
$ ssh cs15lwi23zz@ieng6.ucsd.edu
```   
After that, you will be required to enter a login password. (This password is the same as using the UCSD account.) As a note, you don't have to worry that the entered characters does not be reflected on the screen; it is because of security reasons. 

<img src="lab-report1-images/vscode-ssh-image.png" width="75%">

If you success in login in, this output will appear.

<img src="lab-report1-images/vscode-loginoutput-image.png" width="75%">

## Run Some Commands
**#Note**   
Now, you can use the terminal as a client of CSE basement which is a server. These are examples to run commands at the terminal.

```  
* pwb : working directory (current directory)
* ls  : name of contents
* cat <file1> <file2>: prints contents of one or more files given by the paths.
* cd  : change directory
* cd ~: Go to home directory
* mkdir: make a new directory
```  

In the example below, I created a new directory called “taiki” using “mkdir” command and moved there using “cd.” I also went back to my home directory using “~.”  
<img src="lab-report1-images/vscode-command-image.png" width="75%">

**#Note**  
To logout the termianl, you can use either of two ways below.

```  
Ctrl-D
Run the command exit
```  

