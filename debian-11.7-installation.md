---
marp: true
---

# Installation procedure

This guide describes how to do a fresh installation of Debian 11.

---

# Choose graphical install

Select a language: `English`

Select your location: `United Kingdom`

Configure the keyboard: `Norwegian`

---

# Network

Hostname: For example  `debian-vg2-arvid` (use your own-name)

Domain name: `kuben.it`

---

# Users and passwords

1. First you have to select a proper password for the `root` account. The `root` user on a Linux system is equivalent to the `administrator` account on a Windows system. Please choose **a proper password that you will remember!** 
2. Now you will create a new user acc ount. First you have to enter the `full name` of the user, but instead just enter your desired username here, so the full name and the username will be identical. I will enter `arvidj` here as the full name.
3. Enter the same for username, I will enter `arvidj` here also.
4. Make a nice password for your new user-account and **write it down immediately!**

Now you will have 2 users on your system: 1 root user which has full administrator rights, and 1 normal user 

---

**Important!** when you do input a root-password in addition to a user-password, the `sudo` tool will not be installed by default, and you will have to install it by first switching to root by running `su root` and inputting the **password for the root-user**, then running `apt install sudo`. You can now use both `su` and `sudo` to run commands with superuser privileges, whatever your prference may be.

There are **2 ways to use the `sudo`-tool:**

1. running a single command as root by typing `sudo <command>`. This is nice if you only have to do one or two commands, but if you need to more it can be tiresome.
2. If you know you will need root-privileges to run many commands in a row, or just want to have a command prompt as root, you can use `sudo -i` where -i stands for *interactive*.
3. In both of the previous commands you will be asked for your password. This is ofcourse the password to the current user you are logged in as, not the root user.

The other way to enter the command line as root is by using the `su` comamnd which stands for *switch user*, by typing `su - <target user account>` which usually will be `su - root`. **Important! You must use that proper format with su space dash space root for it to work, or you will not have the proper path variable when you enter as root, which can lead to important binaries missing from the path like useradd ** 

---

# Partition disks

1. Choose `Guided - use entire disk`
1. Choose the default disk that comes next `SCSI (0.....bla bla)`
2. Choose `All files in the partition (recommended for new users)
3. Choose `Finish partitioning and write changes to disk`, then `Continue`
4. Choose `Yes`to write changes to disk.

---

# Configure the package manager

1. Scan extra installation media? `No`
2. Debian archive mirror country: `Norway`
3. Debian archive mirror: `ftp.uio.no`
4. HTTP Proxy: `blank` (dont write anything)

---

# Select and install software

1. Configuring popularity contest: `No`

## Software to install

The following should be selected:

 - :white_check_mark: Debian desktop environment (if you want to include the graphical user interface).
    - **Warning! If you don't include this, only commandline based administration will be possible. Recommended for all new users.**
- :white_check_mark: GNOME
- :white_check_mark: Standard system utilities

---

# Install GRUB boot loader

1. Installing GRUB boot loader to primary harddrive? `Yes`
1. Device for boot loader installation: Choose the partition that was created, usually called something like  `/dev/sda .....`

---

# Finish the installation

1. Congratulations, you are now finished with the installation process!
1. Reboot

---

# Documentation

1. Document your new installation with a nice markdown-formatted technical sheet

## Users

|Username|Password|
|--|--|
arvidj|SuperPassword22@11
root|R00t@Secr3t112233
