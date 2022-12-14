# Lab Report 2 - Week 1
**Step 1: Visual Studio Code**  
Since I had already installed VS code during my CSE 11 class, I was able to skip the installation. However in order to install VS code just go to the website, where you will download and install VS code. The final result of openning VS code should be a window similar to the one below.  
![Image](vsCodeAidan.PNG)  

**Step 2: Connecting Remotely**  
In order to connect remotely you must get you class account and then open a new terminal in VS Code. In the terminal type the ssh command which will be similar to  
```ssh accountName@ieng6.ucsd.edu```   

and the terminal will give a prompt to say yes to and then ask for a password. This password should be your UCSD password, however, if this doesn't work you will have to reset your password, which could take up to an hour.  
![Image](cs15l-lab1-part4.PNG)  
The above picture contains messages about the failed password attempts.
![Image](part4-2.PNG)  

**Step 3: Using Commands**  
After successfully connecting remotely, we can run some commands in order to see what files are on the remote computer. Some commands that we can run include ```ls```, ```cp```, ```cp ~```, and ```cat /home/linux/ieng6/cs15lfa22/public/hello.txt```. The ls command displays files and folders in the current directory. The cp command will copy a file. The cat command prints the contents of a file to the screen. In the screenshot below you can see that I ran cat to print out the hello.txt file and other commands.  
![Image](part5-hello.PNG)  

**Part 4: Transferring to Remote Computer**  
To transfer files from the client to the remote computer we will use the scp command. Note: log out of remote computer using ```exit``` command.  
 ```scp fileName accountName@ieng6.ucsd.edu:~/```  

Use the above command with the file you want to transfer. This will prompt you to input your password, at which point the file will then be on your remote computer. 
![Image](part6-1.PNG)  
![Image](part6.PNG)  

**Part 5: Setting SSH Key**  
A SSH key will allow you to access ```ssh``` without having to input a password everytime. In order to create a SSH key enter ```ssh-kegen``` into the command line and it will ask you to enter a file to save the key. The default file is fine, which will look like /Users/yourname/.ssh/id_rsa. This will create the ssh key and save it to the file location above (that twas the command run in the first picture that was cut off at the top). Then transfer the public key to the remote computer using ```scp```. This will be done by logging into the remote computer with ```ssh```  and creating a .ssh directory with the following command ```mkdir .ssh```. From that step you will log out of the remote computer and run ```scp /Users/yourname/.ssh/id_rsa accountName@ieng6.ucsd.edu:~/.ssh/authorized_keys```. This copies the public key to a directory under your account on the remote computer. At this point you should be able to log in using the SSH key without a password.
![Image](part7.PNG)   
![Image](part7login.PNG)  
When attempting to do the ```ssh-add``` for windows I ran into trouble when figuring out where to add the public key and how it would be used to aid in not needing a password.  
![Image](part7-4.PNG)  

**Part 6: Optimization**  
When running the terminal you can use more optimal and efficient commands in order to save time and key strokes. I ran some efficient commands as seen in the picture, such as ```ls``` at the end of ```ssh``` command to see the directory and using semi-colons to run multiple commands.  

![Image](part8.PNG)  
