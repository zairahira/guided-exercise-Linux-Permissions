**Step1: Switch to root user.**
Sitch to root user so that we have the rights to create new users and groups.

<details>
<summary> Show hint
</summary>

Use the `sudo` command with flag `i`.
If you have the root password, you can login using that as well.
If you do not have `root` access, use the commands with  appending`sudo`.
</details>

<details>
<summary> Show solution
</summary><br>

`sudo - i`

![img](img\step1.PNG)

</details>

--- 

**Step2: Create a group `dev-team`**
Sitch to root user so that we have the rights to create new users and groups.

<details>
<summary> Show hint
</summary><br>

Use the `groupadd` command.

Syntax: `groupadd group-name`

</details>

<details>
<summary> Show solution
</summary><br>


` groupadd dev-team`

</details>

--- 

**Step3: Create two new users John and Bob and them to group `dev-team`**

hint: use command useradd
useradd creates a new user and adds to the sepcified group.

syntax: `useradd -G groupname username`

where `-G` specifies the group.


solution:
`useradd -G dev-team John`

`useradd -G dev-team Bob`

Verify: `cat /etc/group | grep dev-team`

![img](img\step3.PNG)
--- 

**Step4:  Provide passwords for users John and Bob**

hint: use command `passwd`
passwd creates a password for users.

syntax: `sudo passwd username`


solution:
`sudo passwd John`

`sudo passwd Bob`

--- 

**Step5: Create a directory in /home and name it `dev-team`**

hint: use command `mkdir`
mkdir creates a directory.

syntax: `mkdir directory-name`


solution:
`mkdir /home/dev-team`

Verify:

![img](img\step5.PNG)

--- 


**Step6: Change the group ownership of the folder `dev-team`  to group `dev-team`**

hint: use command `chown`

syntax: `chown :group-name folder`


solution:
`chown :dev-team /home/dev-team/`

![img](img\step6.PNG)

--- 

**Step7: Make sure, the permissions of folder `dev-team` allows group members to create and delete files.**

hint: use command `chmod`
write permissions allow users to create and delete files.

syntax: `chmod permissions folder`


solution:
`chmod g+w /home/dev-team/`

![img](img\step7.PNG)


--- 


**Step8: Ensure that 'others' don't have any access to the files of `dev-team` folder.**

hint: use command `chmod`
Remove read, write, execute  permissions from 'others'.

syntax: `chmod permissions folder`


solution:
`chmod o-x dev-team `


![img](img\step8.PNG)
--- 

**Step9: Exit the `root` session and switch to `John`**

hint: use command `exit` to exit the terminal.
use `su` to switch users.
To confirm current user, use command `whoami`.

syntax: `su - user`


solution:
`exit`

`su - John `

verify with command `whoami`.

--- 


**Step10: Navigate to folder: `/home/dev-team`**

hint: use command `cd` to switch folders.
confirm current path with `pwd`.

syntax: `cd /path/to/folder`


solution:
`cd /home/dev-team`

--- 


**Step11: Create an empty file in the folder: `/home/dev-team`**

hint: use command `touch` to create an empty file.

syntax: `touch filename`


solution:
`touch john-file.txt`



--- 


**Step12:  Change the group ownership of the created file to `dev-team` and verify.**

hint: use command `chown` to change ownership.

syntax: `chown :group file-name`


solution:
`chown :dev-team john-file.txt`

Once group ownership is modified, all members of the group can access this file.

![img](img\step10.PNG)
--- 


**Step13:  Exit the shell and switch to user `Bob`**

hint: use command `exit` to exit the terminal.
use `su` to switch users.
To confirm current user, use command `whoami`.

syntax: `su - user`


solution:
`exit`

`su - Bob `

verify the current user with  command `whoami`.

--- 


**Step14: Navigate to the path `/home/dev-team`**

hint: use command `cd` to switch folders.
confirm current path with `pwd`.

syntax: `cd /path/to/folder`


solution:
`cd /home/dev-team`


--- 


**Step15: Find out `Bob's` previledges to access `john-file.txt `**

hint: use command `ls -l` for long listing.
Does group have rw- permissions?

syntax: `ls -l | grep file-name`


solution:
`ls -l | grep john-file.txt`


![img](img\step13.PNG)


--- 


**Step16: Modify the file `john-file.txt ` while logged in as `Bob`**

hint: use command `echo` to add some text to the file.


syntax: `echo "Some text" > >file-name`
This would redirect the quoted text to end of the file.

solution:
`echo "This is alice's comment" > john-file.txt`

If all the permissions are correctly set, `Bob` would be allowed to edit and save this file. Otherwise you would get an error `Permission denied`.

--- 













<details>
<summary> Show hint
</summary><br>
-- summary
</details>

<details>
<summary> Show solution
</summary><br>
--solution

</details>

--- 

