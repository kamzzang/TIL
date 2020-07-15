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


## 2020.05.18
### pandas string
<pre>
<code>
# 공백 제거
df['email_strip']  = df['email'].str.strip()  # 앞 뒤 공백을 제거
df['email_lstrip'] = df['email'].str.lstrip() # 앞 공백을 제거
df['email_rstrip'] = df['email'].str.rstrip() # 뒤 공백을 제거

# split(): 구분자를 기준으로 n개로 나눈다, expand=True이면 여러 컬럼, False이면 1개 컬럼에 리스트
df[['email_split_1', 'email_split_2']] = df['email'].str.split('@', n=1, expand=True)

# 치환
df['email_lower']      = df['email'].str.lower()      # 모두 소문자로 변경
df['email_upper']      = df['email'].str.upper()      # 모두 대문자로 변경
df['email_capitalize'] = df['email'].str.capitalize() # 앞문자 대문자로 변경
df['email_title']      = df['email'].str.title()      # 단위별 앞문자 대문자로 변경
df['email_swapcase']   = df['email'].str.swapcase()   # 소문자는 대문자, 대문자는 소문자로 변경 

# 입력 패턴 또는 글자를 대체, 예제에서는 .을 _로 변경
df['email_replace']    = df['email'].str.replace(pat='.', repl='_', regex=False)

# 문자열의 위치(인덱스)
df['email_find']    = df['email'].str.find(sub='.')           # 왼쪽부터 sub값 검색후 위치반환
df['email_findall'] = df['email'].str.findall(pat='[a-zA-Z]') # 찾은 모든 값 반환
df['email_rfind']   = df['email'].str.rfind(sub='.')          # 오른쪽부터 sub값 검색후 위치반환
df['email_index']   = df['email'].str.index(sub='.')          # 왼쪽부터 sub값 검색후 위치반환
df['email_rindex']  = df['email'].str.rindex(sub='.')         # 오른쪽부터 sub값 검색후 위치반환

# 길이 반환
df['email_len']   = df['email'].str.len()              

# 구성 확인
df['email_isalnum']   = df['email'].str.isalnum()   # 알파벳 또는 숫자로만 구성 여부
df['email_isalpha']   = df['email'].str.isalpha()   # 알파벳으로만 구성 여부
df['email_isdecimal'] = df['email'].str.isdecimal() # 숫자문자로만 구성 여부
df['email_isdigit']   = df['email'].str.isdigit()   # 숫자문자로만 구성 여부
df['email_islower']   = df['email'].str.islower()   # 소문자로만 구성 여부
df['email_isnumeric'] = df['email'].str.isnumeric() # 숫자문자로만 구성 여부
df['email_isspace']   = df['email'].str.isspace()   # 공백(Whitespace)으로만 구성 여부
df['email_istitle']   = df['email'].str.istitle()   # TitleCase형태로 구성 여부
df['email_isupper']   = df['email'].str.isupper()   # 대문자로만 구성 여부

# 문자열 패턴
df['email_startswith'] = df['email'].str.startswith(pat='h')     # 좌측값이 입력패턴과 일치 여부
df['email_endswith']   = df['email'].str.endswith(pat='com')     # 우측값이 입력패턴과 일치 여부
df['email_contains']   = df['email'].str.contains(pat='kr', regex=False) # 값 중 패턴포함 여부
df['email_match']      = df['email'].str.match(pat='[a-zA-Z@.]') # 입력패턴과 일치 여부
</code>
</pre>


## 2020.05.19
### OS Module
<pre>
<code>
# 파일 목록 얻기
glob.glob(wildcard) # 유닉스 경로명 패턴 스타일로 파일 목록을 얻을 수 있다.
os.listdir(path) # 지정된 디렉토리의 전체 파일 목록을 얻을 수 있다.
dircache.listdir(path) # os.listdir(path)와 동일한 파일 목록을 전달한다.

# 디렉토리 다루기
os.chdir(path) #작업하고 있는 디렉토리 변경
os.getcwd() # 현재 프로세스의 작업 디렉토리 얻기

# 파일 이름 다루기
os.path.abspath(filename) # 파일의 상대 경로를 절대 경로로 바꾸는 함수
os.path.exists(filename) # 주어진 경로의 파일이 있는지 확인하는 함수
os.curdir() # 현재 디렉토리 얻기
os.pardir() # 부모 디렉토리 얻기
os.sep() # 디렉토리 분리 문자 얻기

# 경로명 분리하기
os.path.basename(filename) # 파일명만 추출
os.path.dirname(filename) # 디렉토리 경로 추출
os.path.split(filename) # 경로와 파일명을 분리
os.path.splitdrive(filename) # 드라이브명과 나머지 분리 (MS Windows의 경우)
os.path.splitext(filename) # 확장자와 나머지 분리
</code>
</pre>


## 2020.05.21
### datetime
<pre>
<code>
import datetime
 
now = datetime.datetime.now()
print(now)          # 2018-07-28 12:11:32.669083

nowDate = now.strftime('%Y-%m-%d')
print(nowDate)      # 2018-07-28
 
nowTime = now.strftime('%H:%M:%S')
print(nowTime)      # 12:11:32
 
nowDatetime = now.strftime('%Y-%m-%d %H:%M:%S')
print(nowDatetime)  # 2018-07-28 12:11:32
</code>
</pre>


## 2020.06.02
### Class member variable
<pre>
<code>
A. dir
class Obj:
    def __init__(self):
        self.x = 9
obj=Obj()
print( dir(obj) )
>>> ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'x']

B. __dict__
print(obj.__dict__)
>>> {'x': 9}

</code>
</pre>

### 변수 존재 확인
1. Try / Exception
<pre>
<code>
try : 
     thevariable
exception NameError :
     print('The variablle wasn't defined'_
else :
     print('It is defined') 
</code>
</pre>     
2. variable
<pre>
<code>
if 'myVar' in locals(): # local variable 일 경우
if 'myVar' in globals(): # global variable 일 경우
if  hasattr(obj,'attr_name') : # obj name이 존재할 경우
</code>
</pre>    

## 2020.06.08
### AWS EC2 ubuntu 유저 생성(pem 파일없이 패스워드 사용 접속)
sudo useradd -s /bin/bash -m -d /home/mckam -g root USERNAME

sudo passwd USERNAME
PASSWORD

sudo chmod u+w /etc/sudoers

sudo nano /etc/sudoers
USERNAME ALL=(ALL:ALL) ALL

sudo nano /etc/ssh/sshd_config
PasswordAuthentication yes

sudo service ssh restart

ssh USERNAME@IP ADRESS
PASSWORD


## 2020.06.23
### Pandas DataFrame 중복제거
<pre>
<code>
df.drop_duplicates([A, B], keep='first') # A, B : 중복 여부 기준 Columns
</code>
</pre> 
### Pandas DataFrame index 초기화
<pre>
<code>
df.reset_index(drop=True)
</code>
</pre> 


## 2020.06.27
### 리스트형 내에서의 임의의 외부 숫자 위치 확인
<pre>
<code>
A = [1,4,6,7]
num = 5

A.append(num)
A.sort()
pos = A.index(num)
A.remove(num)
</code>
</pre>


## 2020.06.29
### 파일 실행
<pre>
<code>
import os

os.startfile(filename)
</code>
</pre>


## 2020.07.13
### 구글스프레드시트 주식 데이터 받기
### GOOGLEFINANCE
* KOSPI 지수 10일 데이터 =GOOGLEFINANCE("KRX:KOSPI", "price", Today()-10, Today(), "DAILY")  
* KOSDQ 지수 20일 데이터 =GOOGLEFINANCE("KOSDAQ:KOSDAQ", "price", Today()-20, Today(), "DAILY")  
* KOSPI 종목 현재가 =GOOGLEFINANCE("KRX:035720")  
* KOSDAQ 종목 현재가 =GOOGLEFINANCE("KOSDAQ:258790")


## 2020.07.14
### SQLite3 데이터 중복 제거
* "DELETE FROM ??? WHERE rowid NOT IN  (SELECT Max(rowid) FROM ??? GROUP BY TITLE order by TITLE)"
* "DELETE FROM Holiday WHERE rowid NOT IN  (SELECT Max(rowid) FROM Holiday GROUP BY Holiday order by Holiday)"


## 2020.07.15
### SQLite3 DataFrame 저장
* df.to_sql('table', conn, if_exists='replace', index=False)
