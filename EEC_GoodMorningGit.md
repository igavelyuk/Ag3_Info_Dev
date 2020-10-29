## GoodMorningGit
### Daily\Weekly commands use of git and github

#### Project
1. Project - information file about daily/weekly git commands (alone mode)
  * [Good commands](#Good-commands)
  * [Morning commands](#Morning-commands)
  * [Daily commands](#Daily-commands)
  * [Weekly commands](#Weekly-commands)
  * [Fork-Update](#Fork-Update)
  * [Server commands](#Server-commands)
2. This project for quick cases working with git and github
3. My story: I frequently use some commands, sometimes I creating git server, and would like have everiting what I use online for reaching from any device.

#### What I use in this project
* Frameworks : I use Git and Github
  * Links: [GITHUB/EEC_GoodMorningGit](https://github.com/EvilEpicCoder/EEC_GoodMorningGit "GoodMorningGit")
   * Note \ star my page.
  * Links: [GITHUB](https://www.github.com "GITHUB")
   * Best place for share.
* Features: Cool tricks in one place

#### My thoughts

* Pros and Cons : Easy and daily, probably you will forget others commands.
* Time consumption: Very cool decreasing time for search, easy to print.
* What I learned : you must spend time, for increase your productivity!
---
#### Good commands <a name="Good-commands"></a>
1. Default user (do not use quotes in names)
  ```bash
  $ git config --global user.name "USERNAME"
  $ git config --global user.email "YOURmailHERE"@gmail.com
  $ git config --global core.editor atom
  $ git config credential.https://github.com "USERNAME"
  $ git config credential.helper store
  $ git push
```
 in the next time will be automaticaly used your login and password
 so you need just to write

  ```bash
  $ git commit -am 'commit update message'
  $ git push
 ```
  -am(_a_ - all files, _m_ -message in command line)
2. Check defaults

 ```bash
  $ git config --list
 ```
#### Morning commands <a name="Morning-commands"></a>
   ```bash
  $ git init
  $ git add .
  $ git commit -m 'commit message'
  $ git remote add origin https://github.com/.git
  $ git config credential.https://github.com.username myusername
  $ git push -u origin master
 ```
#### Daily commands <a name="Daily-commands"></a>
 * Remove specific file

  ```bash
  $ git rm --cached file
  $ git commit --amend -CHEAD
  $ git push
 ```
#### Weekly commands <a name="Weekly-commands"></a>
  * nothing here yet

#### Fork/Update <a name="Fork-Update"></a>
  * Fork on github
  ```bash
  cd GitDir
  mkdir subProjDir
  cd subProjDir
  git clone https://github.com/YourUsername/blablaProject.git
  cd blablaProject
  git remote add origin https://github.com/YourUsername/blablaProject.git
  git remote add upstream https://github.com/ForkedUsername/ForkedblablaProject.git
  ```
  * To check `git remote -v`
  ```bash
  origin https://github.com/YourUsername/blablaProject.git (fetch)
  origin https://github.com/YourUsername/blablaProject.git (push)
  upstream https://github.com/ForkedUsername/ForkedblablaProject.git (fetch)
  upstream https://github.com/ForkedUsername/ForkedblablaProject.git (push)
  ```
  * Reset your git(your changes will be lost)
  ```bash
  git checkout master
  git reset --hard upstream/master
  git merge upstream/master
  ```
#### Server commands <a name="Server-commands"></a>

1. Installing Debian server name: `gitserver`
2. Create user: `git`
   * Install GIT and Apache2, MySQL, PHP7:
  ```bash
  su *****
  $ apt-get install git gitcore gitweb
  $ apt-get install apache2 mysql-server mysql-client php7 phpmyadmin
  ```
3. Installing user rights with `ssh-keygen` on the user computer
  * Copy `*.pub`  file to the server `home/git/.ssh/authorizati...` and rename to `autorized-keys`
  * Init server side git
 ```bash
  $ mkdir /var/gitroot
  $ mkdir /var/gitroot/project.git
  $ cd project.git
  $ git --bare init
```
4. On user computer
  ```bash
  $ git init
  $ git add .
  $ git commit -m 'initial commit'
  $ git remote add origin //192.168.0.1/project.git
  $ git push master
 ```

 #### Server commands (LATEST)</a>
[Original](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-git-server-on-a-vps)
1. SSH to Server
`sudo ssh gweb@192.168.99.81 -p 2245`

2. Log into your VPS, and gain root*:
`su -`

3. Add the Unix user (not necessarily Git user names) to handle the repositories:
`useradd git`

4. If user folder don't exist
`mkhomedir_helper git`

Use the following (as root, or with sudo if not root)
for this to work, folder `/home/username` must not exist.

5. Then give your Git user a password:
`passwd git`

6. On your machine
 - Create the SSH Key Pair `ssh-keygen -C "youremail@mailprovider.com"`  
  - `-C` mean `comment ` use for help `ssh-keygen --help`

7. Add your SSH Key to the Access List (server)
 - `su git`
 - `mkdir ~/.ssh && touch ~/.ssh/authorized_keys`

8. Copy Key from your machine to Server
 - you can use simple Copy
 or
 - cat .ssh/id_rsa.pub | ssh gweb@192.168.99.81 -p 2245 "cat >> ~/.ssh/authorized_keys"

  Thats All folks!

---

Version: `0.7a`
Date: `Haloween 31.10.2017`
