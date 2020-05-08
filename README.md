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

## 2020.03.28
### json 파일 생성
<pre>
<code>
import json

with open('?????.json', 'w', encoding='utf-8') as make_file:

    json.dump(json_data, make_file, indent="\t")
</code>
</pre>

### json 파일 open
<pre>
<code>
import json

with open('?????.json', 'r') as f:

    admin_info = json.load(f)

print(admin_info)
</code>
</pre>

### 환경변수 불러오기
<pre>
<code>
import os

admin_info_file = os.getenv('NAME')
</code>
</pre>


## 2020.04.02
### Numpy Zero-like
<pre>
<code>
>>> x = np.arange(6)
>>> x = x.reshape((2, 3))
>>> x
array([[0, 1, 2],
       [3, 4, 5]])
>>> np.zeros_like(x)
array([[0, 0, 0],
       [0, 0, 0]])
</code>
</pre>

## 2020.04.12
### Folium Marker icon ref.
 * https://getbootstrap.com/docs/3.3/components/#glyphicons-glyph

## 2020.04.15
### AWS SSH 연결
cmd / powershell 관리자모드로 실행  
ssh -i "AWSKEY.pem" ubuntu@ec2-IP주소.ap-northeast-2.compute.amazonaws.com  
### AWS server 구동
1. python3 application.py : 파이썬 서버 구동
2. Ctrl + Z : 프로세스 중지
3. bg : 백그라운드에서 서버 다시 구동
4. disown -h : 소유권 포기
### 중지
1. netstat -nap | grep {포트 번호}: 특정 포트 번호에서 돌아가는 프로세스를 확인하기
2. kill -9 {프로세스 번호}: 특정한 프로세스를 종료시키기
### 추가
1. jobs : 프로세스 확인
2. fg : 포어그라운드


## 2020.04.16
### KAKAO MAPS API
* Geocoding
<pre>
<code>
url = 'https://dapi.kakao.com/v2/local/search/address.json?query='+addr
headers = {"Authorization": "KakaoAK {Private Key}"}
result = json.loads(str(requests.get(url,headers=headers).text))

if len(result['documents']) !=0:
    match_first = result['documents'][0]['address']
    return float(match_first['y']),float(match_first['x'])
else:
    return None, None
</code>
</pre>


## 2020.05.07
### install python anaconda 32bit envs
* set CONDA_FORCE_32BIT=1
* conda create -n XXXXXXX python=3.7 anaconda

### To activate envs.
* conda activate XXXXXXX
### To deactivate an active envs.
* conda deactivate


## 2020.05.08
### python slacker
<pre>
<code>

from slacker import Slacker

token = 'Slack API Token'
slack = Slacker(token)
slack.chat.post_message('#general', 'Bot test message')

</code>
</pre>
