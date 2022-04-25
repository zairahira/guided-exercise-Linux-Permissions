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


<details>
<summary> Show hint
</summary>

Use command `useradd`.

`useradd` creates a new user and adds to the sepcified group.

Syntax: `useradd -G groupname username`

Where `-G` specifies the group.

</details>

<details>
<summary> Show solution
</summary>

`useradd -G dev-team John`

`useradd -G dev-team Bob`

Verify: `cat /etc/group | grep dev-team`

![img](img\step3.PNG)
</details>


--- 

**Step4:  Provide passwords for users John and Bob**


<details>
<summary> Show hint
</summary>


Use command `passwd`

`passwd` creates a password for users.

Syntax: `sudo passwd username`


</details>

<details>
<summary> Show solution
</summary>

`sudo passwd John`

`sudo passwd Bob`

</details>



--- 

**Step5: Create a directory in /home and name it `dev-team`**


<details>
<summary> Show hint
</summary>


Use command `mkdir`

`mkdir` creates a directory.

Syntax: `mkdir directory-name`


</details>

<details>
<summary> Show solution
</summary>

`mkdir /home/dev-team`

Verify:

![img](img\correction.png)


</details>



--- 


**Step6: Change the group ownership of the folder `dev-team`  to group `dev-team`**


<details>
<summary> Show hint
</summary>

Use command `chown`

Syntax: `chown :group-name folder`


</details>

<details>
<summary> Show solution
</summary>

`chown :dev-team /home/dev-team/`

![img](img\step6.PNG)

</details>



--- 

**Step7: Make sure, the permissions of folder `dev-team` allows group members to create and delete files.**


<details>
<summary> Show hint
</summary>

Use command `chmod`

Write permissions allow users and groups to create and delete files.

Syntax: `chmod permissions folder`

</details>

<details>
<summary> Show solution
</summary>

`chmod g+w /home/dev-team/`

![img](img\step7.PNG)

</details>





--- 


**Step8: Ensure that 'others' don't have any access to the files of `dev-team` folder.**


<details>
<summary> Show hint
</summary>

Use command `chmod`

Remove read, write, execute  permissions from 'others' if they exist.

Syntax: `chmod permissions folder`


</details>

<details>
<summary> Show solution
</summary>

`chmod o-rx dev-team `


![img](img\correction2.png)

</details>



--- 

**Step9: Exit the `root` session and switch to `John`**


<details>
<summary> Show hint
</summary>

Use command `exit` to exit the terminal.

Use `su` to switch users.

To confirm current user, use command `whoami`.

Syntax: `su - user`

</details>

<details>
<summary> Show solution
</summary>

`exit`

`su - John `

Verify with command `whoami`.

</details>



--- 


**Step10: Navigate to folder: `/home/dev-team`**


<details>
<summary> Show hint
</summary>

Use command `cd` to switch folders.

Confirm current path with `pwd`.

Syntax: `cd /path/to/folder`


</details>

<details>
<summary> Show solution
</summary>

`cd /home/dev-team`

</details>



--- 


**Step11: Create an empty file in the folder: `/home/dev-team`**


<details>
<summary> Show hint
</summary>

Use command `touch` to create an empty file.

Syntax: `touch filename`

</details>

<details>
<summary> Show solution
</summary>

`touch john-file.txt`

</details>







--- 


**Step12:  Change the group ownership of the created file to `dev-team` and verify.**


<details>
<summary> Show hint
</summary>

Use command `chown` to change ownership.

Syntax: `chown :group file-name`

</details>

<details>
<summary> Show solution
</summary>

`chown :dev-team john-file.txt`

Once group ownership is modified, all members of the group can access this file.

![img](img\step10.PNG)

</details>




--- 


**Step13:  Exit the shell and switch to user `Bob`**


<details>
<summary> Show hint
</summary>

Use command `exit` to exit the terminal.

Use `su` to switch users.

To confirm current user, use command `whoami`.

Syntax: `su - user`

</details>

<details>
<summary> Show solution
</summary>

`exit`

`su - Bob `

Verify the current user with  command `whoami`.

</details>





--- 


**Step14: Navigate to the path `/home/dev-team`**


<details>
<summary> Show hint
</summary>

Use command `cd` to switch folders.

Confirm current path with `pwd`.

Syntax: `cd /path/to/folder`


</details>

<details>
<summary> Show solution
</summary>

`cd /home/dev-team`


</details>





--- 


**Step15: Find out `Bob's` previledges to access `john-file.txt `**


<details>
<summary> Show hint
</summary>


Use command `ls -l` for long listing.

Does group have `rw-` permissions?

Syntax: `ls -l | grep file-name`


</details>

<details>
<summary> Show solution
</summary>

`ls -l | grep john-file.txt`


![img](img\step13.PNG)

</details>



--- 


**Step16: Modify the file `john-file.txt ` while logged in as `Bob`**


<details>
<summary> Show hint
</summary>

Use command `echo` to add some text to the file.

Syntax: `echo "Some text" > >file-name`

This would redirect the quoted text to end of the file.

</details>

<details>
<summary> Show solution
</summary>

`echo "This is Bob's comment" > john-file.txt`

If all the permissions are correctly set, `Bob` would be allowed to edit and save this file. Otherwise you would get an error like this: `Permission denied`.

</details>



--- 












