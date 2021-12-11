https://www.youtube.com/watch?v=oxuRxtrO2Ag&t=2646s

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

<br/>
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
- cd , cd ~ 返回至 /root
- cd rico's\\ folder 反斜線為跳脫字元路徑中含特殊符號例如空白

-------------
<div id="pushdpopd"></div>

`pushd` `popd` into folder and back previous folder


-------------
<div id="file"></div>

`file` determine file type

-------------
<div id="locate"></div>

`locate` locate  reads  one or more databases prepared by updatedb(8) and writes file names matching at least one of the PATTERNs to standard output, one per line.

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
- rm file1 -r  
  - remove directories and their contents recursively
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

- su - cindy