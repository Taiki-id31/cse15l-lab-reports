# Lab Report 1   Taiki Yoshino (A17492011)

## Installing VSCode
**#Note**  
To download the VSCode, I have to go to this website and choose the competible software with my device(ex. Mac).  
(However, since I have already downloaded it in the CSE 11, I didn't need to it this time.) 

![image](lab-report1-images/vscode-download-image.png)

**#Note**  
After I donlowad VSCode and opend it, it took me this home page.  
(I think this page is slightly different from one I first installed.)  

![image](lab-report1-images/vscode-home-image.png)

## Remotely Connecting
**#Note**  
To use terminal in VSCode, I can click "Terminal" in the menu bar and go on to "New Terminal." Then, the terminal come up from the bottom up. (If you use Windonws devices, one more step is necessary to install git)  

![image](lab-report1-images/vscode-terminal-image.png)

**#Note**  
Next, I am goint to access remote commputer using "ssh." SSH represents for Secure Shell, and it allows me to access
You should type course-specific account to log in. (I struggled with this process because I forgot to replace the "zz" to my own account characters.) After that, you will be required to enter log in password.(this password is the same one to use the ucsd's account.) As a note, you don't have to worry about that the entered passowrd will not be reflected to the screen, because of the security reason. 

![image](lab-report1-images/vscode-ssh-image.png)

If you correctly entered password, this output will appear.

![image](lab-report1-images/vscode-loginoutput-image.png)

## Run Some Commands
**#Note** 
Now, you can edit the loggined page using some commands.

* pwb : working directory (current directory)
* ls  : name of contents
* cat <file1> <file2>: prints contens of one or more files given by the paths.
* cd  : change directory
* cd ~: Go to home directory

In the example below, I created a new directory called “taiki” using “mkdir” command and moved there using “cd.” I also went back to my home directory using “~.”  
  
![image](lab-report1-images/vscode-command-image.png)
