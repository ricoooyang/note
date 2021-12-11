# linux basic
<a href="#whoami">`whoami`</a>
<a href="#whatis">`whatis`</a>
<a href="#man">`man`</a>
<a href="#pwd">`pwd`</a>
<a href="#ls">`ls`</a>
<a href="#cd">`cd`</a>
<a href="#pushd">`pushd`</a>
<a href="#popd">`popd`</a>
<a href="#file">`file`</a>
<a href="#locate">`locate`</a>
<a href="#which">`which`</a>
<a href="#history">`history`</a>
<a href="#apropos">`apropos`</a>
<a href="#mkdir">`mkdir`</a>
<a href="#touch">`touch`</a>
<a href="#cp">`cp`</a>
<a href="#mv">`mv`</a>
<a href="#rm">`rm`</a>
<a href="#rmdir">`rmdir`</a>
<a href="#cat">`cat`</a>
<a href="#more">`more`</a>
<a href="#less">`less`</a>
<a href="#nano">`nano`</a>
<a href="#sudo">`sudo`</a>
<a href="#su">`su`</a>
<a href="#users">`users`</a>
<a href="#id">`id`</a>
<a href="#linuxpermission">`linux permission`</a>
<a href="#chmod">`chmod`</a>
<a href="#free">`free`</a>
<a href="#watch">`watch`</a>
<a href="#killall">`killall`</a>
<a href="#usefulshortcut">`useful shortcut`</a>


-------------
<div id="whoami"></div>

`whoami` print effective userid 

-------------
<div id="whatis"></div>

`whatis`
- whatis ls

-------------
<div id="man"></div>

`man` an interface to the system reference manuals
- man man
- man cal
- man ls

-------------
<div id="pwd"></div>

`pwd` print name of current/working directory

-------------
<div id="ls"></div>

`ls` list directory contents
- ls /etc
- ls /etc -a
- ls /etc -al
- ls --help

-------------
<div id="cd"></div>

`cd`
- cd /etc
- cd .. 返回至上層
- cd , cd ~ 返回至 /root (或該user的folder)
- cd rico's\\ folder (反斜線為跳脫字元 cd至“rico's folder”)

-------------
<div id="pushdpopd"></div>

`pushd` `popd` into folder and back previous folder


-------------
<div id="file"></div>

`file` determine file type

-------------
<div id="locate"></div>

`locate` locate  reads  one or more databases prepared by updatedb(8) and writes file names matching at least one of the PATTERNs to standard output, one per line.

- locate adduser

>locate command uses a database to find things,
linux distributions do is they usually set the system up to update the database for locate once a day. if you want to update locate
> >sodo updatedb


-------------
<div id="which"></div>

`which` locate a command

-------------
<div id="history"></div>

`history` show recently issue command

-------------
<div id="apropos"></div>

`apropos` search the manual page names and descriptions


-------------
<div id="mkdir"></div>

`mkdir` create a directory
- mkdir dir1
- mkdir dir1 dir2

-------------
<div id="touch"></div>

`touch` change file timestamps
- touch file1 file2 file3

-------------
<div id="cp"></div>

`cp` copy files and directories
- cp bashrc.bak bashrc

-------------
<div id="mv"></div>

`mv` move (rename) files
- mv bashrc.bak bashrc

-------------
<div id="rm"></div>

`rm` remove files or directories
- rm file1 -r (remove directories and their contents recursively)
- rm --help
- rm file1
- rm file1 file2
- rm file*

-------------
<div id="rmdir"></div>

`rmdir` remove empty directories
- rmdir /rico/* 
   - 底下的空資料夾 將會被移除

-------------
<div id="cat"></div>

`cat` concatenate files and print on the standard output
- cat file1 file2
- cat >> file1
  - append data to file.
  - Ctrl+D 儲存
- cat > file1
  - overwrite file content.

-------------
<div id="more/less"></div>

`more/less` file perusal filter for crt viewing
- more file1 (Space key to next page, Q to leave)
- less file1 (arrow key one line at a time, Space key to next page, Q to leave)
- history | less (Use out put from history command directly put into less program)

-------------
<div id="nano"></div>

`nano` command line text editor
- nano file1
  - Ctrl+O (另存新檔)
  - Ctrl+R (開啟檔案)
  - Ctrl+X (離開)

-------------
<div id="sudo"></div>

`sudo` sudo allows a permitted user to execute a command as the superuser or another user, as specified
     by the security policy.  The invoking user's real (not effective) user ID is used to determine
     the user name with which to query the security policy.

- sudo -s 
- exit

-------------
<div id="su"></div>

`su` The su command is used to become another user during a login session.

- su - cindy (get into cindy's home automatically)
- su cindy (get into cindy's home manually)
- su - (attempt to log you in as a root)
- su (attempt to log you in as a root)
- exit

-------------
<div id="users"></div>

`users` print the user names of users currently logged in to the current host

-------------
<div id="id"></div>

`id` print real and effective user and group IDs

-------------
<div id="linuxpermission"></div>

## Linux Permission

- when you use ls -l, use a long listing format. it will show each file permission information.
- <a href="https://www.youtube.com/watch?v=oxuRxtrO2Ag&list=PLbfiCCN9Jz9AvByif7bScObtuIGdc3XOm&index=1&t=22s">56:40</a>

|symbol|number|meaning|
|----|----|----|
|r|4|read|
|w|2|write|
|x|1|execute|

|user|group|everyone|
|----|----|----|
|rwx|rw|r|
|4+2+1=7|4+2=6|4|

-------------
<div id="chmod"></div>

`chmod` change file mode bits, it allows you to change permission of file.

- chmod +764 file (uses:rwx, group:rw, everyone:r)
- chmod +x file1 (add execute permission to everyone)

-------------
<div id="free"></div>

`free` free  displays  the  total  amount of free and used physical and swap memory in the system, as
well as the buffers and caches used by the kernel. The  information  is  gathered  by  parsing
/proc/meminfo.

- free -h

-------------
<div id="watch"></div>

`watch` execute a program periodically, showing output fullscreen

- watch free -h
- Ctrl+C (leve)

-------------
<div id="killall"></div>

`killall` killall sends a signal to all processes running any of the specified commands.

- killall firefox


-------------
<div id="usefulshortcut"></div>

## useful shortcut on some emulator

- Ctrl+D - signal bash that there is no more input
- Ctrl+L or Ctrl+C - redraw the screen
- Ctrl++ - make text bigger in terminal emulator
- Ctrl+- - make text smaller in terminal emulator


-------

### lab: https://www.katacoda.com/courses/ubuntu/playground
### reference: https://www.youtube.com/watch?v=oxuRxtrO2Ag&t=2646s

-------









