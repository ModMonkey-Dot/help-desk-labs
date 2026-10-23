# 00-Lab-Setup

Setup-Notes

I created this VM so I can practice help desk projects, make notes about what I did, and put the completed projects on GitHub for my resume. After each project, I plan to save my notes and screenshots outside the VM and restore it to a clean checkpoint.

I enabled Hyper-V on my Windows 11 Pro laptop and created a VM named HelpDesk-PC01. I chose Generation 2, assigned 8192 MB of memory, and set it to 4 virtual processors. I used the Default Switch for networking and enabled Secure Boot with the Microsoft Windows template and Trusted Platform Module.

I created a 127 GB dynamically expanding virtual hard disk. I stored the VM files in D:\HelpDeskLab\VMs and downloaded the Windows 11 Enterprise evaluation ISO from Microsoft into D:\HelpDeskLab\ISOs.

So, first, after downloading the ISO file, when I first started the VM up with the ISO file, it gave me an error saying:

1. SCSI DVD (0,1): The boot loader failed.
2. Network Adapter: A boot image was not found.
3. SCSI Disk (0,0): The boot loader did not load an operating system.

It said, “No operating system was loaded. Your virtual machine may be configured incorrectly. Exit and re-configure your VM or click restart to retry the current boot sequence again.”

All I did was reset it and retry it. I ejected the disk, and then I chose the ISO file again and started it up. It ended up working, and Windows Setup started. I do not know exactly what caused the earlier boot error.

During Windows Setup, I selected English (United States), the US keyboard layout, and Install Windows 11. I selected Disk 0 Unallocated Space, which matched the 127 GB virtual disk I created.

After Windows finished installing, I created a local account named LabAdmin and set up its password and security questions. I disabled the optional privacy settings during setup.

Once I reached the desktop, I installed the available Windows updates and checked again until Windows Update said, “You’re up to date.”

The time inside the VM was wrong. I enabled location services, used the automatic time settings, and synced the time. After that, the VM’s time matched my laptop.

I checked the computer name inside Windows and noticed it still had a default DESKTOP name. I renamed it HelpDesk-PC01 to match the name in Hyper-V and restarted the VM.

When I checked the memory, Windows showed 8 GB installed but a smaller amount usable. In Task Manager, it showed 3.1 GB usable and 4.9 GB hardware reserved. I checked the Hyper-V settings and found that Dynamic Memory was enabled.

I shut down the VM, turned off Dynamic Memory, and kept the memory set to 8192 MB. After starting the VM again, Task Manager showed 8 GB usable, about 5.1 GB available, and only 1.1 MB hardware reserved. I learned that Dynamic Memory lets Hyper-V adjust the memory assigned to a VM. I chose fixed memory to keep this lab’s memory allocation consistent.

I opened Windows Security and checked its overview. Virus and threat protection, account protection, firewall and network protection, and app and browser control all showed, “No action needed.”

I shut down the VM and changed its virtual DVD drive to None to disconnect the installation ISO.

With the VM shut down, I created a checkpoint and named it Clean-Baseline. I saved a screenshot in the Screenshots folder inside my setup notes folder and named it Clean-Baseline Checkpoint.

I tested restoring the Clean-Baseline checkpoint, and it worked. The VM is now ready for help desk projects. Before restoring it after each project, I will save my notes and screenshots outside the VM so I can keep them for my GitHub portfolio.
