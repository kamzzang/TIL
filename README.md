# Today I learned

## 2020.02.09
### Git basic command
* git init:Initialize repositury
* .git : repository
* git status : working tree status
* git add : add to staging area
* git add . : add all files to staging area
* git commit : create version
* git commit -m "Message"
* git commit -am "Message" : add + commit
* git log : show version
* git log -stat
* git log -p
* git diff
* git checkout commit-ID
* git checkout master

### Change git editor
* git config --global core.editor "nano"

### Reset
* git reset --hard commit-ID
* git reset --soft commit-ID 

### Display log(branch)
* git log --all --grape -- oneline

### Correct coCcommit massage
* git commit --amend  


## 2020.03.12
### Git remote
* git init
* git remote add origin "http adress"
* git pull origin master
* git add *
* git commit -m "Message"
* git push --set-upstream origin master


## 2020.03.20
### pyc compile(pyc_compile.py)  
import py_compile  
py_compile.compile('py file name')

### bat file(2 python versions)  
C:\Anaconda3\python.exe pyc_compile.py  
C:\Anaconda3\envs\python36\python.exe pyc_compile.py
