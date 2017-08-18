## GoodMorningGit
### Dayly\Weekly commands use of git and github

#### 1.Project
	* Project - information file about dayly/weekly git commands
		* Good commands
		* Morning commands
		* Dayly commands
		* Weekly commands
		* Server commands
	* This project for quick cases working with git and github
	* My story: I frequently use some commands, sometimes I creating git server, and would like have everiting what I use online for reaching from any device.
#### 2.What I use in this project
	* Frameworks : I use Git and Github
	* Links: [GITHUB/EEC_GoodMorningGit](https://github.com/EvilEpicCoder/EEC_GoodMorningGit "GoodMorningGit")
		* Note or star my page.
	* Links: [GITHUB](https://www.github.com "GITHUB")
		* Best place for share.
	* Features: Cool tricks in one place
#### 3. My thoughts
	* Pros and Cons : Easy and dayly, probably you will forget others commands
	* Time consumption: Very cool decreasing time for search, easy to print 
	* What I learned : you must spend time, for increase your productivity!
---
## Good commands

### Morning commands
```
git init
git add .
git commit -m 'commit message'
git remote add origin https://github.com/.git
git push -u origin master
```
#### Dayly commands
#### Weekly commands
#### Server commands
1.Installing Debian server name: gitserver
2.Create user: git
* Install GIT and Apache2, MySQL, PHP7:
```
su *****
$ apt-get install git gitcore gitweb
$ apt-get install apache2 mysql-server mysql-client php7 phpmyadmin
```
* Installing user rights with ssh-keygen on the user computer
* Copy *.pub file to the server `home/git/.ssh/authorizati...` and rename to `autorized-keys`
```
mkdir /var/gitroot
mkdir /var/gitroot/project.git
cd project.git
git --bare init
```
---
Frequently used linux commands reminder
```
cd
mkdir
chmod
chgroup
```
---
* On user compuret 
```
git init
git add .
git commit -m 'initial commit'
git remote add origin //192.168.0.1/project.git
git push master
```
	
