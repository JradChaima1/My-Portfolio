## Managing permissions on Linux and Windows
🔐 Linux Users, Groups & Permissions Lab

This lab demonstrates Linux user management, group management, file ownership, and permission control using practical command-line operations.

1. Create Two User Accounts

Two user accounts were created for testing multi-user access control.

<img width="918" height="346" alt="Pasted image 20260603231349" src="https://github.com/user-attachments/assets/53fc8b4c-6e60-46f8-9155-cbacfd55f6d4" />


2. Create Two Groups

Two groups were created to manage file access permissions.

<img width="261" height="141" alt="Pasted image 20260603232051" src="https://github.com/user-attachments/assets/6f972401-72fe-4419-9199-e05ab85934f2" />
<img width="261" height="141" alt="Pasted image 20260603232051" src="https://github.com/user-attachments/assets/fb8bba88-ea8f-49b6-b4a6-659bf7edbb9d" />


3. Add user01 to Admin Group

user01 was added to the admin group to grant elevated privileges.

<img width="262" height="58" alt="Pasted image 20260603232214" src="https://github.com/user-attachments/assets/d7184b7a-46e1-4cdf-85dd-8f654c133eb2" />


4. Verify user01 Group Membership

Confirmed that user01 belongs to the admin group.

<img width="546" height="66" alt="Pasted image 20260603232628" src="https://github.com/user-attachments/assets/57603d64-09c2-4212-abcc-31a2d7a16dac" />


5. Check /etc/group File

Verified group creation by inspecting the system group configuration file.

<img width="196" height="196" alt="Pasted image 20260603232834" src="https://github.com/user-attachments/assets/4ebb07cd-87fa-4174-a33c-1ac6e3375859" />


6. Add user02 to Devs Group

user02 was added to the development group.

<img width="240" height="46" alt="Pasted image 20260603233104" src="https://github.com/user-attachments/assets/f1559908-e6b2-475a-82ca-80da110db859" />

7. Create Files in Different Directories

Created multiple files in different directories to test permission behavior.

<img width="413" height="276" alt="Pasted image 20260603233720" src="https://github.com/user-attachments/assets/4162d193-0792-4b4f-86ed-c5d3bc3c7d74" />


8. Change Ownership of ITprojects

The ownership of the ITprojects directory was changed to demonstrate file ownership control.

<img width="477" height="293" alt="Pasted image 20260603235046" src="https://github.com/user-attachments/assets/ac5cbe31-a0bc-477a-a028-6bdc94e19e48" />


9. Add Execute Permission to File Owner

Execute permission was granted to the file owner.

<img width="453" height="190" alt="Pasted image 20260603235807" src="https://github.com/user-attachments/assets/8aee9ece-0280-4c88-8f26-96b201350f73" />


10. Add Write Permission to Group

Write permission was granted to the group associated with the file.

<img width="449" height="135" alt="Pasted image 20260604000040" src="https://github.com/user-attachments/assets/98ebbecb-6e6e-4891-8d6c-571316dd482e" />


11. Remove Permissions (Group, Others, and Owner)
Removed read permission from group and others
Removed execute permission from user

<img width="490" height="155" alt="Pasted image 20260604000334" src="https://github.com/user-attachments/assets/d2ad0c8d-0ddf-419c-8dc9-5a15042ae77c" />


12. Set Full Permissions (rwx for All)

Granted full permissions using numeric mode:

Read = 4
Write = 2
Execute = 1



<img width="443" height="126" alt="Pasted image 20260604001310" src="https://github.com/user-attachments/assets/ef9708aa-92ad-49ee-baf5-c9c73854f126" />

🔐 Window Permissions Lab

1. Check file permission

<img width="522" height="183" alt="image" src="https://github.com/user-attachments/assets/9ca2c874-abfa-4385-8ad9-375f24e56e0b" />

On this file, the Administrator and System have full permissions, but the User only has Read & Execute permission

2. Deny hp user from reading the file
   
<img width="518" height="129" alt="image" src="https://github.com/user-attachments/assets/cdfad00e-2ff7-4ef9-a7a9-3e31ea3db0be" />
