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

<pre>
<code>
import py_compile  
py_compile.compile('py file name')
</code>
</pre> 

### bat file(2 python versions)  
C:\Anaconda3\python.exe pyc_compile.py  
C:\Anaconda3\envs\python36\python.exe pyc_compile.py


## 2020.03.23
### DataFrame Error Fix
* ValueError: If using all scalar values, you must pass an index  
* [참조](https://rfriend.tistory.com/482)  

<pre>
<code>
import pandas as pd  
df = pd.DataFrame({'col_1': 1, 'col_2': 2})
</code>
</pre>

* add an index
<pre>
<code>
df = pd.DataFrame({'col_1':1, 'col_2':2}, index=[0])
</code>
</pre>  

* use a list instead of scalar values
<pre>
<code>
df = pd.DataFrame({'col_1':[1], 'col_2':[2]})
</code>
</pre>  

* use pd.DataFrame.from_records() with a list
<pre>
<code>
df = pd.DataFrame.from_records([{'col_1':1, 'col_2':2}])
</code>
</pre>  

* use pd.DataFrame.from_dict([]) with a list
<pre>
<code>
df = pd.DataFrame.from_doct([{'col_1':1, 'col_2':2}])
</code>
</pre>


## 2020.03.27
### 동적 변수 생성
<pre>
<code>
data = ["first", "second", "third"]
for name in data:
    for i in range(1,4):
        globals()[name] = [x*i for x in range(3)]
</code>
</pre>
