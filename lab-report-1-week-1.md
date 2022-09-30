# Lab Report 1 Week 1
Hi, CSE 15L students. This is a tutotial about how to set up for remote access to the CSE lab computers.

---

>Step 1: Look up for the course-specific account on **ieng6**

[Click here to look up your acocunt](https://sdacs.ucsd.edu/~icc/index.php)

If you want to read a tutorial for resetting your password [click here](https://docs.google.com/document/d/1hs7CyQeh-MdUfM9uv99i8tqfneos6Y8bDU0uhn1wqho/edit).

>Step 2: Download Visual Studio Code

[Click here to download VSC](https://code.visualstudio.com/)


After VSC installed, open your VSC, and it should look like this:

![image](lab-report-1-week-1-folder/openVSC.png)

>Step 3: Install OpenSSH Client

[Click here for installing OpenSSH](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui)

OpenSSH allows us to connect our computer to other computers.

**ieng6** already has installed OpenSSH server.

>Step 4: Connect remotely to **ieng6**

Open a terminal in VSC, and then type in "ssh" and your account:

```
$ ssh cs15lfa22po@ieng6.ucsd.edu
```
My personal account is: cs15lfa22po, which is different to yours.

After that, type in your password, then you will see some thing like this:

![image](lab-report-1-week-1-folder/connectToieng6.png)

Now, you have successfully connected to **ieng6**!

>Step 5: Try some commands

Try run some commands in both **your computer** and the **remote computer**.

* `cd ~`
* `cd`
* `cd -`
* `ls`
* `ls -lat`
* `ls <directory>`
* `cp <directory>`
* `cat <directory>`

This was what is shown when I ran `ls -lat`:
![image](lab-report-1-week-1-folder/runSomeCommands.png)

>Step 6: 
