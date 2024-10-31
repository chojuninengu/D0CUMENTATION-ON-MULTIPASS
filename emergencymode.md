# 	   HOW TO SOLVE THE ISSUE OF YOUR LINUX ENTERING EMERGENCY MODE
  WHAT IS EMERGENCY MODE

  Emergency mode in Linux is a minimal environment that allows you to troubleshoot and recover a system that is unable to boot properly due to critical issues, such as filesystem corruption, misconfigured services, or hardware failures. When a Linux system cannot boot into its normal operating mode, it may automatically drop into emergency mode, typically indicated by a prompt where you can enter commands.
WHY IS YOUR LINUX IN EMERGENCY MODE
    Linux may enter emergency mode for several reasons, typically related to critical system failures or issues that prevent the operating system from booting normally. Here are some common causes:
1. Filesystem Corruption
       If the filesystem is corrupted, the system may fail to mount essential partitions. This can happen due to improper shutdowns, hardware failures, or disk errors.

2. Failed Services
       Critical services that must start during the boot process may fail. If these services are necessary for the system to function (e.g., filesystem mount services or networking), the system might drop  into emergency mode.

3. Misconfigured Configuration Files
        Errors in configuration files (such as /etc/fstab, which contains filesystem mount information) can prevent the system from mounting filesystems correctly.

4. Missing or Corrupted Kernel Modules
        If essential kernel modules are missing or corrupted, the system may not boot correctly, leading to emergency mode.

5. Hardware Issues
        Problems with hardware components (e.g., a failing hard drive, memory issues, or unsupported hardware) can prevent the system from booting normally.

6. Inadequate Disk Space
        If the root filesystem runs out of space, it can cause various services to fail, leading to an inability to boot properly.

7. Improper Updates or Package Installations
        Updates or installations that interfere with core system components or libraries can prevent successful booting.

8. Corrupted Bootloader Configuration
        Issues with the bootloader (e.g., GRUB) configuration can prevent the system from starting normally.

# Conclusion
Emergency mode is a protective measure that allows users to address serious problems without risking further damage to the system. By entering this mode, administrators can troubleshoot issues, run diagnostics, and perform repairs to restore normal functionality.
# HOW TO SOLVE THE EMERGENCY MODE


![alt text](<WhatsApp Image 2024-10-31 at 11.29.40 AM.jpeg>)
	FIRSTLY 
 * In the emergency mode ,you will see the issue listed at the begining line(in my case,/dev/nume0n1p2:recovering journal,/dev/nume0n1p2:clean)
     from here,you need to enter recovery mode
     to enter recovery mode ,you need to hold the poweroff button till the machine goes off
     turn on the machine,immidiately it comes on,you hold down the **shift button** it will take you here
![alt text](<WhatsApp Image 2024-10-31 at 11.47.02 AM.jpeg>)
select the advance obtion to continue
then take the desired name of your system in recovery mode 
* NB:TAKE THE LATEST VERSION IN RECOVERY MODE
after that you will enter here
    ![alt text](<WhatsApp Image 2024-10-31 at 11.29.42 AM-2.jpeg>)
# CONGRATS ,YOU ARE NOW AT THE RECOVERY MODE MEN
* you will see options like  {(resume)(clean)(dpkg)(fsck)(grub)}
* you can use the resume to get to the recovery mode interface-
* you can use the clean to free up space in your linux distro
* you can use the dpkg to check damaged packages
* you can use the fsck to check  and repair the filesystem and checks disk issues

* in resume,you will enter your login display
* you then put your password to enter
* open your terminal

**type** in the following commands
  ```sudo mount -a``` to see if checks errors in the fstab
* do ```sudo nano /etc/fstab``` for editing
* checkout for any error in the file( in my case ,the device name wasn't specified)
* so i ran the command *lsblk* to check the name of the partition to correct    * the error in the fstab file
 * i had this in my case (/dev/nvme0n1p2)
 * then do ```sudo mount -a ```  if you get no output, the error in the fstab is  * *solved*
 * then reboot normally(init 6,reboot,systemctl reboot)
 * CONGRATS,YOUR ISSUE HAS BEEN SOLVE
* If your machine freezes on reboot or just shows a dark screen do the following
 * YOU NEED TO CHECK YOUR **GRUB CONGIGURATION FILE**
  * use the command ```sudo nano /etc/default/grup```
 * In my case, i had ```(acpi=off)```
 * delete the link containing  the ``acpi=off``
 * then do `sudo grub-update`
 * finally do `init 6`
 * # YOU ARE DONE THANKYOU FOR YOUR TIME
