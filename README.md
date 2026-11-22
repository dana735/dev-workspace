r
# 💻 내 컴퓨터에 개발자용 ‘작업실’ 꾸미기


## 1. 프로젝트 개요 (미션 목표 요약)

- **목적**: GitHub Codespaces 및 Linux 환경을 기반으로 개발에 필요한 기본 터미널 조작, 파일 권한 관리, Docker 컨테이너 빌드·운영, 그리고 Git/GitHub 연동을 수행하고 이를 기술 문서로 기록한다.

---

## 2. 실행 환경


- **OS / 셸**: Linux (GitHub Codespaces) / Bash
- **Docker 버전**: (`docker --version` 결과 기입)
- **Git 버전**: (`git --version` 결과 기입)

---

## 3. 수행 항목 체크리스트

- [x]  터미널 기본 조작 (위치 확인, 파일/디렉토리 생성·이동·삭제 등)
- [x]  파일 및 디렉토리 권한 설정 및 변경 실습 (`chmod`)
- [x]  Docker 설치 및 기본 점검 (`docker --version`, `docker info`)
- [x]  Docker 기본 운영 명령어 수행 (`docker images`, `docker ps -a`, `docker logs`)
- [x]  컨테이너 실행 실습 (`hello-world`, `ubuntu` 컨테이너 진입 등)
- [x]  기존 Dockerfile 기반 커스텀 이미지 제작 및 빌드/실행 성공
- [x]  포트 매핑 (`p`) 및 브라우저 접속 성공 증거 첨부
- [x]  바인드 마운트 및 Docker 볼륨 영속성 검증
- [x]  Git 설정 및 GitHub 연동 완료
- [x]  절대경로 상대경로

---

## 4. 터미널 조작 기록

#1. 현재 위치 확인

cmd
PS C:-workspace> cd

C:-workspace

powershell pwd

#2. 폴더 생성 (practice)

PS C:-workspace> mkdir scrips

```
디렉터리: C:\Users\USER\dev-workspace

현재 제 저장소(dev-workspace)는 개발 환경을 체계적으로 구축하고 관리하기 위한 작업실 구조로 이루어져 있으며, 핵심 디렉토리와 파일은 다음과 같습니다."

📁 docker-1/ (Docker 디렉토리)

컨테이너 기반의 개발 환경을 구축하고 테스트하기 위한 Docker 관련 설정 및 파일들이 담겨 있는 공간입니다.

📁 scripts/ (스크립트 디렉토리)

개발 및 작업 자동화를 위한 쉘 스크립트나 실행 파일들이 정리되어 관리되는 공간입니다.

📄 README.md (프로젝트 설명서)

'내 컴퓨터에 개발자용 작업실 꾸미기'라는 과제 목표와 프로젝트 개요, 사용법 등을 상세히 기록해 둔 문서입니다.
```

Mode LastWriteTime Length Name
—- ————- —— —-

#3. 목록 확인 (숨김 파일 포함)

PS C:-workspace> dir /a
#(여기에 현재 폴더의 모든 파일과 폴더 목록이 출력됩니다)

#4. scripts 폴더 생성 및 이동

PS C:-workspace> mkdir scripts

C:-workspace>

cd scripts

C:-workspace>cd scripts

C:-workspace>


<img width="941" height="439" alt="image" src="https://github.com/user-attachments/assets/7504ba47-3aa6-4c00-b493-bb2260f24812" />


#5.삭제

PS C:-workspace> rm scripts

PS C:-workspace> dir

#(scripts 폴더가 목록에서 사라진 것을 확인)

#파일있었으면

PS C:-workspace> rm test.txt

PS C:-workspace> dir
(파일이 삭제되어 목록에 아무것도 나타나지 않음)

#명령어 cd.. 상위 폴더 이동후 위 작업 실시

PS C:-workspace> cd ..

PS C:-workspace>

#6. 숨김 파일 포함 목록 확인 (PowerShell에서는 ls -la 대신 ls -Force 사용 권장)

PS C:-workspace> ls -Force

cmd 에서 재실행 rmdir /s/dev-workspace  

<img width="798" height="526" alt="image" src="https://github.com/user-attachments/assets/51fcf17e-ce1d-45e6-a13b-fe411c98bc57" />

dev-workspace 폴더 없어짐

```
# (현재는 비어있으므로 아무것도 나오지 않거나 . 과 .. 만 보입니다)
```

#7. 빈 파일 생성 톅스트 쓰기

리눅스로 옮김

touch test.txt # 빈 파일 생성

ls # 파일 목록 확인

<img width="373" height="101" alt="image" src="https://github.com/user-attachments/assets/28d50b4d-8c60-486c-99b9-6462a4d9d4e6" />


echo “Hello, World!” > hello.txt 파일안으로 >
cat 파일 화면 출력 내용 확인
cat hello.txt

hello.txt> memo.txt

echo “I love Docker” >> memo.txt

<img width="531" height="490" alt="image" src="https://github.com/user-attachments/assets/c06e825d-6f04-41be-8b71-620914d46eb5" />

내용 추가 (Append)

cat memo.txt

두줄이 다 나오는지 확인

#8 .복사 및 폴더 관리 ***중요!

mkdir secret # 1. secret 폴더 만들기

touch secret/my_note.txt # 2. 폴더 안에 파일 만들기

cp secret/my_note.txt backup.txt # 3. 파일을 밖으로 복사

cp -r secret secret_backup # 4. 폴더 전체를 복사 (-r 필수!)

cp -r 폴더 파일 모두 복사

백업 파일 이유
rm -r secret # 아차! 폴더를 실수로 지웠다!

ls secret # 폴더그 없어서 에러 발생

<img width="1021" height="371" alt="image" src="https://github.com/user-attachments/assets/804b3f30-6197-4816-accb-65249d2d72ca" />

ls backup.txt # 휴, 밖에 복사해둔 파일은 무사하네!

mkdir secret # 폴더 다시 만들고

cp backup.txt secret/my_note.txt # 백업본을 다시 폴더 안으로 복사해서 복구!

#9.이동 및 삭제

mv secret-backup secret/ # secret-backup를 secret 폴더로 이동

<img width="856" height="231" alt="image" src="https://github.com/user-attachments/assets/9afb549f-0601-4128-9094-5950d09b25e8" />




## 5. 권한 실습 및 증거 기록

. 권한 비트(r, w, x) 기본 값
리눅스/유닉스 파일 권한(chmod)에서 각 권한은 아래의 2진수(비트) 자릿값에 대응합니다.

r (Read, 읽기): 값 4 (100₂) — 파일 내용을 읽거나 디렉터리 목록을 조회할 수 있는 권한

w (Write, 쓰기): 값 2 (010₂) — 파일 내용을 수정·삭제하거나 디렉터리 안에 파일을 생성·삭제할 수 있는 권한

x (Execute, 실행): 값 1 (001₂) — 파일을 프로그램/스크립트로 실행하거나 디렉터리에 진입(cd 등)할 수 있는 권한

권한 없음(-): 값 0 (000₂)

계산 원리: r(4), w(2), x(1) 중 부여할 권한의 숫자를 서로 더하면 0부터 7까지의 8진수 숫자가 됩니다.

숫자기호의미숫자기호의미
0---없음              4r--읽기
1--x실행              5r-x읽기+실행
2-w-쓰기              6rw-읽기+쓰기
3-wx쓰기+실행         7rwx전체 허용

#실습 파일 및 디렉토리 생성

touch apple.txt

#권한 변경 

chmod 644 apple.txt

#변경 전 권한 확인

ls -l apple.txt 644

<img width="695" height="124" alt="image" src="https://github.com/user-attachments/assets/67b97d9d-ae7f-429b-aeb4-ab7d3e387f03" />

#권한 변경

chmod 600 apple.txt

#변경 후 권한 확인 결과

ls -l apple.txt


-l (long 길게 파일 세부 상세)

ls -d (directory 내용말고 폴더 자체 정보만 딱)

- rw——- 600
- 
<img width="701" height="122" alt="image" src="https://github.com/user-attachments/assets/0877b8e2-3685-4ec0-89ca-5e42361afacc" />

chmod 755 apple.txt

ls -l apple.txt

<img width="717" height="116" alt="image" src="https://github.com/user-attachments/assets/7bfaa798-1add-4e1a-8c72-c72a59dbd759" />

- rwxr-xr-x

## 6. Docker 설치 및 기본 점검 Dockerfile

## 1 docker –version

<img width="910" height="80" alt="image" src="https://github.com/user-attachments/assets/b80917c9-bc71-449c-9252-8d8fca080310" />


버전 표시 info

<img width="457" height="182" alt="image" src="https://github.com/user-attachments/assets/500eac43-c3d9-4521-a0f2-1a3e61898d11" />

Windows PowerShell 환경에서 진행하여 systemctl status docker 대신 docker --version, docker info, docker ps 실행 결과로 도커 버전 및 데몬 작동 상태를 확인·캡처했습니다.

docker run hello-world

- **도커 데스크 탑 실행 안해서 에러뜸
실행후

“HELLO from Docker!”

## 2 이미지 컨테이너 목록 확인및 정리 흔적이 있는가

docker ps -a 

<img width="1319" height="176" alt="image" src="https://github.com/user-attachments/assets/6c234732-dd91-4693-881a-e005253b1980" />


NAME hello-world 컨테이너 STATUS Exited 실행흔적 뜻 잘실행

image

## 3 이미지 목록 확인

docker images

<img width="872" height="166" alt="image" src="https://github.com/user-attachments/assets/a9a9a781-4814-43a6-9835-558ef5eea151" />

레지스토리에 hello-world 보임

## 4 컨테이너 삭제

docker rm 컨테이너_ID 도커는 아이디 앞 세자리만 해도 됨

<img width="1287" height="160" alt="image" src="https://github.com/user-attachments/assets/a9f98422-53ed-438c-84c0-fad4937d9e48" />

삭제

<img width="672" height="64" alt="image" src="https://github.com/user-attachments/assets/2ce5eec8-aaf1-4a98-86d0-c399c06b8dd7" />

- 이미지 삭제 (설계도)

docker rmi hello-world
docker images 확인
<img width="1016" height="275" alt="image" src="https://github.com/user-attachments/assets/4c219c72-6d34-49cc-8ca4-408897f03511" />

docker rmi hello-world my-web-server

ㅇocker system prune 한번에 지우기

## 5 컨테이너 삭제 확인

docker ps -a

<img width="892" height="104" alt="image" src="https://github.com/user-attachments/assets/7f35e525-a11a-41ba-be44-5c943e64cc4b" />

docker images

image

## 6 Dockfile

## 1 실습용 파일

mkdir my-web-site

cd my-web-site

현재 위치 ~ my-web-site 폴더에 잘 들어옴

## 2 간단한 HTML 파일 만들기

echo “<h1>Hello,Docker Build!</h1>”> index.html

파일 내용 화면에 보여달라

cat Dockerfile

도커 파일 보여줘

<img width="928" height="85" alt="image" src="https://github.com/user-attachments/assets/c5132b86-4498-4674-8a4b-3cfa1693fa23" />


### 3. 도커파일(Dockerfile) 작성하기

나만의 웹페이지(`index.html`)를 담은 맞춤형 웹 서버 설계도 만들기

1. **편집기 열기:** `nano Dockerfile`메모장 
 
2. **설계도 내용 작성 (편집기 내부에 입력):**
   * `FROM nginx:alpine` : 가벼운 버전의 nginx 웹 서버를 기본 틀로 사용
   * `COPY index.html /usr/share/nginx/html/index.html` : 내 `index.html` 파일을 컨테이너 내부 웹 서버 경로로 복사
   * 
3. **저장 및 종료 단축키:** `Ctrl + s` (저장) ➔ `Enter` (확인) ➔ `Ctrl + X` (나가기)

저장시 다른 이름저장  모든파일 변경 "Docker"
저장 주소가 바탕화면이라  
1.cd ~ 2 cd Desktop 3.Dockerfile 내용확인 4.도커 이미지 빌드



###🛠️ [3. 이미지 빌드하기] & [웹서버 실행] 완벽 정리본

docker build -t my-custom-web:1.0 .

- . 꼭!! 현재 폴더 도크 파일 사용하겠다!

- docker build: 아까 작성한 Dockerfile(설계도)을 바탕으로 이미지를 조립(빌드)하겠다는 뜻입니다.
-
- -t my-custom-web:1.0: 내가 만든 이미지에 이름(my-custom-web)과 버전(1.0)표시(Tag)를 붙여주는 옵션입니다.
-
-     . (마지막 점): "꼭 현재 폴더(.)"에 있는 Dockerfile을 사용해서 빌드하라는 뜻으로, 이 점을 빼먹으면 에러가 납니다!
- 마지막 점 앞에 한칸 띄우기

- <img width="1337" height="421" alt="image" src="https://github.com/user-attachments/assets/0dd28b8a-06de-47cf-a619-0fe2d6e3caf2" />


#4.빌드된 이미지 확인

docker images

image

my-custom-web:1.0 이미지 이름 보이면 성공 web 뒤:1.0이 방금 내가 만든 거 이름

<img width="677" height="85" alt="image" src="https://github.com/user-attachments/assets/f74b51ca-38c6-4a6a-832c-c77df0d5cbc2" />

<img width="556" height="107" alt="image" src="https://github.com/user-attachments/assets/91e4ca8a-6ab1-40bd-be1e-e8414df36767" />



~my-web-site 폴더내 작업 수행인뜻

# 웹서버 실행

# 1. 포트 매핑 및 접속 증거😊

포트 매핑(8080:80): 내 컴퓨터 8080번 문과 컨테이너 안 80번 문을 이어 준 것 → 그래서 브라우저로 들어갈 수 있었고, 그 경로로 접속이 들어온 것입니다.

접속 확인: Hello, Docker Build! 화면이 떴다는 것 자체가 포트 매핑과 웹 서버 접속이 정상 동작했다는 뜻입니다.


docker run -d -p 8080:80 –name my-web-container my-custom-web:1.0

docker run: 이미지 기반으로 컨테이너(실행 중인 프로그램)를 띄워라!

-  -d컨테이너 백그라운드 진행 Detached 모드 (백그라운드에서 조용히 실행되도록 함. 터미널을 계속 차지하지 않고 뒤에서 돌아가게 됨)
- 
- p 8080;80
8080번 포트로 들어오는 신호를 컨테이너안 80번{웹기본포트} 포트로 전달
- 포트; 데이터 문 출입구 건물안의 방
- 
- ip: 주소
- -  (크롬 주소창에 localhost:8080을 치면 내가 만든 웹페이지가 뜨게 만드는 핵심 연결고리입니다!)
  -  
 --name my-web-container: 실행될 컨테이너의 이름을 my-web-container라고 지어준다.

 - my-custom-web:1.0: 어떤 이미지를 바탕으로 실행할 것인가? (아까 우리가 위에서 빌드한 그 이미지 이름!)
 -  
- <img width="1295" height="79" alt="image" src="https://github.com/user-attachments/assets/60cb1f84-cbed-4a90-8d83-d63df4e95aad" />


#1 컨테이너 실행확인

docker ps


<img width="1872" height="152" alt="image" src="https://github.com/user-attachments/assets/d88dc3fc-3c8e-44b3-af55-f7854a280477" />

my-web-sever 또는 my-web container 보이면 성공

웹주소창 http://localhost:8080 직접치기

Hello,Docker Build!



<img width="541" height="137" alt="image" src="https://github.com/user-attachments/assets/8db87300-9482-41fe-974c-4054c5b94a7e" />



포트 매핑은 컨테이너를 백업해 주는 기능이 아니라 내 컴퓨터(8080 포트)와 컨테이너 안 웹 서버(80 포트)를 연결해 브라우저로 접속하게 해 주는 통로이고, 지금 띄운 컨테이너는 바인드 마운트나 볼륨 없이 index.html을 이미지 안에 복사(COPY)해 만든 상태라 컨테이너를 지우면 컨테이너 자체는 없어지지만 my-custom-web:1.0 이미지는 그대로 남아서 나중에 언제든 같은 웹 서버를 다시 띄울 수 있다


#  바인드 마운트 컨테이너 실행

바인드 마운트는 내 컴퓨터 폴더(Desktop)와 컨테이너 폴더를 실시간으로 연결해 컨테이너를 지워도 바탕화면 파일이 남고 수정 내용이 바로 반영되는지 보는 방식입니다 

### 현재 위치 확인하기

PowerShell 프롬프트가 C:\Users\lightview117307\Desktop>처럼 Desktop 폴더로 되어 있는지 확인해 주세요. (다른 경로라면 cd ~\Desktop을 먼저 입력

### 바인드 마운트로 웹 컨테이너 띄우기

1. 포트 매핑 과정 연결  run은 컨테이너 띄우기 
* 
docker run -d -p 8080:80 --name my-bind-web -v "${PWD}:/usr/share/nginx/html" nginx:alpine

<img width="941" height="286" alt="image" src="https://github.com/user-attachments/assets/103da4a8-aaee-424b-9d66-79969a093bb9" />

컨테이너 ID가 한 줄 나오면 성공!

### 브라우저에서 기존 화면 확인하기

크롬이나 엣지 주소창에 http://localhost:8080(또는 [http://127.0.0.1:8080](http://127.0.0.1:8080))을 입력하고 Enter.


 
"<h1>Bind Mount Works!</h1>" | Out-File -FilePath .\index.html -Encoding utf8

그다음 브라우저에서 http://localhost:8080을 새로고침(F5)했을 때 Bind Mount Works!가 뜨면 바인드 마운트 반영 검증 완료입니다!


404 Not Found가 뜨는 건 도커 엔진이 고장 나서라기보다, 지금 연결된 폴더(또는 컨테이너의 웹 경로)에 index.html 파일이 없거나 비어 있어서 웹 서버가 파일을 못 찾았다는 뜻.

아까는 Hello, Docker Build!가 나왔을까
my-custom-web:1.0 이미지 안에는 처음에 Hello, Docker Build!가 담긴 index.html이 복사되어 들어가 있음.

바인드 마운트 없이 my-custom-web:1.0으로 띄우면 이미지 안에 들어 있던 파일 그대로 화면에 보여줍니다.  포트 매핑 -p 8080:80은 백업이 아니라 내 컴퓨터 포트와 컨테이너 포트를 연결해 주는 통로
왜 지금은 Not Found가 떴을까?
바인드 마운트(-v ...:/usr/share/nginx/html)를 걸면, 이미지 안의 파일 대신 내 컴퓨터 폴더(Desktop) 안의 파일을 바라보게 됩니다.

만약 Desktop 폴더에 index.html이 없거나, 명령어를 수정·입력하는 과정에서 파일이 제대로 만들어지지 않았거나 내용이 비어버리면 Nginx가 보여줄 페이지가 없어서 404 Not Found가 떠요.

 [***이럴때는
 1.Desktop 폴더에 index.html을 다시 제대로 만들기
 
"<h1>Bind Mount Works!</h1>" | Out-File -FilePath .\index.html -Encoding utf8

2.파일이 잘 생겼는지 확인하기

type .\index.html


<h1>Bind Mount Works!</h1>가 화면에 찍히면 파일이 정상 생성]



### Desktop 폴더에 index.html을 다시 제대로 만들기

index.html 내용 바꾸고 확인하기

 바인드 마운트 자료 연결 과정임

"<h1>Bind Mount Works!</h1>" | Out-File -FilePath .\index.html -Encoding utf8

그다음 브라우저에서 http://localhost:8080을 새로고침(F5)했을 때 Bind Mount Works!가 뜨면 바인드 마운트 반영 검증 완료입니다!


### 파일이 잘 생겼는지 확인

type .\index.html

<img width="316" height="32" alt="image" src="https://github.com/user-attachments/assets/ab4e9e7a-a185-4ac6-b08b-3656c4b36159" />

<h1>Bind Mount Works!</h1>가 화면에 찍히면 파일이 정상 생성된 것입니다.

그다음 브라우저에서 http://localhost:8080을 새로고침(F5)해 보세요.

<img width="379" height="155" alt="image" src="https://github.com/user-attachments/assets/e5aea479-5638-4bf9-ac38-ce88fc4e5076" />


만약 my-bind-web 컨테이너가 아직 안 떠 있는 상태라면, 먼저 docker run -d -p 8080:80 --name my-bind-web -v "${PWD}:/usr/share/nginx/html" nginx:alpine으로 띄운 뒤에 확인하시면 됩니다.

### 바인드 마운트 없을 때 (my-custom-web:1.0 단독 실행): 이미지 안에 구워져 들어간 index.html을 그대로 보여줍니다.

### 바인드 마운트 있을 때 (-v 폴더:/usr/share/nginx/html): 내 컴퓨터 폴더가 컨테이너의 웹 폴더를 덮어쓰듯 연결되므로, 내 컴퓨터에서 index.html을 고치거나 지우면 웹 화면도 그 상태에 맞춰 바로 바낌

이미지(Image): 앱을 찍어낸 원본 틀·설계도 같은 거라서 컨테이너를 지워도 기본적으로 남아 있음.

데이터(Data): 컨테이너가 돌아가면서 생기는 기록이나 파일, 바뀐 내용 같은 거라서 컨테이너를 지우면 함께 지워질 수 있는 것.

볼륨(Volume): 그 데이터를 컨테이너와 따로 떼어 도커가 관리하는 저장 공간에 보관해 줘서, 컨테이너를 지우고 새로 만들어도 데이터가 살아남게 해 주는 장치

# 도커 볼륨 영속성 확인하기

### 볼륨 만들기

docker volume create my-web-vol

### 볼륨을 연결해서 컨테이너 띄우기

docker run -d -p 8080:80 --name my-vol-web -v my-web-vol:/usr/share/nginx/html nginx:alpine

### 볼륨 쪽(index.html)에 테스트 문구 남기기

docker exec my-vol-web sh -c 'echo "<h1>Volume Data Survived!</h1>" > /usr/share/nginx/html/index.html'

### 컨테이너 삭제 후 새 컨테이너로 다시 연결하기

docker rm -f my-vol-web-2
docker run -d -p 8080:80 --name my-vol-web-2 -v my-web-vol:/usr/share/nginx/html nginx:alpine

<img width="557" height="108" alt="image" src="https://github.com/user-attachments/assets/2417b0e7-8e85-48fb-9bf7-4dbad43a30eb" />

http://localhost:8080)를 새로고침(F5)했을 때 아까 넣었던 Volume Data Survived!가 그대로 보이면 볼륨 영속성 검증 성공


ㅇ<img width="299" height="122" alt="image" src="https://github.com/user-attachments/assets/f59d9f9a-b3fa-445b-bc6b-5c8fb316587e" />




## 세 가지 핵심 개념 한눈에 보기
Dockerfile(도커파일): 요리 레시피예요. "어떤 기본 환경(nginx:alpine) 위에 어떤 파일(index.html)을 넣고 어떻게 실행할지" 적어 둔 텍스트 설명서입니다.

이미지(Image): 레시피를 보고 실제로 만들어 둔 완성된 요리 패키지(설계도·틀)예요. 한 번 만들어 두면 변하지 않고, 이 이미지로 똑같은 앱 환경을 여러 번 찍어낼 수 있습니다. (my-custom-web:1.0 같은 것)

컨테이너(Container): 이미지를 실제로 실행한 살아 있는 프로그램(실행 중인 상자)이에요. 브라우저(localhost:8080)에 화면을 띄워 주는 주체가 바로 이 컨테이너이고, 지우면 실행 상태가 끝나며 그 안에만 있던 임시 데이터도 함께 사라질 수 있습니다.

한 줄로 비유하면
Dockerfile = 붕어빵 만드는 설명서

이미지 = 붕어빵 틀(원본)

컨테이너 = 실제로 구워져서 손님에게 나가는 따뜻한 붕어빵(실행 실체)

처음엔 이렇게 레시피(Dockerfile) → 틀(이미지) → 실물(컨테이너) 순서

## 볼륨(Volume) vs 바인드 마운트(Bind Mount)
볼륨(Volume): 도커가 직접 관리하는 전용 저장 공간이에요. 내 컴퓨터 바탕화면이나 특정 폴더를 직접 건드리지 않고 도커 엔진이 공간을 맡아서 관리하므로, 컨테이너를 지우고 새로 만들어도 데이터를 안전하게 이어 붙일 때 잘 씁니다.

바인드 마운트(Bind Mount): 내 컴퓨터의 실제 폴더(Desktop 등)와 컨테이너 폴더를 직접 1:1로 이어 붙이는 방식이에요. 내 컴퓨터에서 파일을 수정하거나 지우면 컨테이너 쪽에서도 즉시 반영되기 때문에, 작업하면서 결과를 바로바로 확인하고 싶을 때 편리합니다.

한 줄로 비유하면
볼륨 = 도커가 따로 마련해 둔 안전 금고(컨테이너가 바뀌어도 데이터 보관용)

바인드 마운트 = 내 컴퓨터 폴더와 컨테이너 폴더를 연결한 직통 통로(내 폴더 수정이 바로 반영)

볼륨(Volume) = 안전성(데이터 영속성) — 컨테이너가 바뀌거나 지워져도 데이터를 도커 관리 공간에 안전하게 남기는 것

바인드 마운트(Bind Mount) = 편리성(실시간 반영) — 내 컴퓨터 폴더에서 고친 내용이 바로바로 반영되어 작업 속도와 편의성을 높이는 것


바인드 마운트가 꼭 필요한 이유
수정할 때마다 다시 만들 필요가 없어요
바인드 마운트 없이 이미지 안에 파일을 복사해 넣었다면, 글자 하나나 코드를 고칠 때마다 이미지를 새로 빌드(docker build)하고 컨테이너를 다시 띄워야 해요. 바인드 마운트를 쓰면 내 폴더(Desktop 등)에서 고친 내용이 바로 이어지니 작업 속도가 훨씬 빨라집니다.

내 눈으로 직접 관리하는 파일을 바로 쓸 수 있어요
내가 VS Code나 메모장 등으로 바탕화면·작업 폴더에서 직접 만들고 수정하는 파일을 컨테이너가 그대로 읽어가기 때문에, 내 작업 파일과 실행 결과가 따로 놀지 않습니다.

초기 설정 파일이나 테스트 자료를 편하게 넣을 수 있어요
웹페이지 파일(index.html), 설정 파일, 테스트용 데이터처럼 내 컴퓨터에 이미 있는 자료를 컨테이너 안으로 빠르게 연결해 써 볼 때 유용합니다.

반대로 볼륨이 더 나은 때는 언제일까요?
내 컴퓨터 폴더에서 실시간으로 고치는 것보다, 컨테이너가 돌아가면서 쌓이는 데이터(DB 저장 내역, 업로드 파일 등)를 지워지지 않게 안전하게 보관하는 것이 목적일 때는 볼륨을 쓰는 게 더 알맞습니다.










컨테이너(붕어빵)만 지웠을 뿐, 원본 설계도인 이미지(붕어빵 틀)는 그대로 남아 있어서 언제든 다시 만들 수 있다는 뜻


😊실습

# Dockerfile 만들기

3️⃣ : 편집기(nano) 안 쓰고 한 줄씩 Dockerfile 만들기 (😊실습)맨 아래 😊실습 부분은 아까처럼 nano 메모장을 열지 않고, 터미널에서 바로 echo 명령어를 이용해 Dockerfile을 뚝딱 만들어내는 방법입니다.    (컨테이너가 켜지면 "Hello, Docker! I am learning!"이라고 인사말을 출력하게 만드는 초간단 설계도입니다.)   


echo ‘FROM alpine’ > Dockerfile

echo ‘CMD [“echo”, “Hello, Docker! I am learning!”]’ >> Dockerfile

이미지 빌드업

docker build -t my-first-image .

컨테이너 실행

docker run my-first-image

1. Docker 기본 운영 명령어 및 컨테이너 실행 실습

image

docker images
docker ps -a
docker run hello-world
docker run -it ubuntu bash


docker ps 확인
docker stop my-server
docker rm my-server
docker run hello-world
docker run -it ubuntu bash
docker ps
docker run -it ubuntu /bin/bash 접속
mkdir my_study
ls
cd study
pwd
ls
mkdir study
ls
cd my_study
pwd
ls
##발자취
history
exit 우분투애서 윈도우로

mv memo.txt secret/❤

1. 기존 Dockerfile 기반 커스텀 이미지 제작
- 선택한 베이스 이미지: NGINX 베이스 이미지 활용
- 빌드 및 실행 명령어:
    
    docker build -t my-custom-nginx .
    docker run -d -p 80:80 –name custom-web-server my-custom-nginx
    


# 2. 바인드 마운트 반영 + Docker 볼륨 영속성 검증
 
docker volume create my_data_vol

docker run -d –name vol-test -v my_data_vol:/data nginx

아래쪽에 정리

# Git 설정 및 GitHub 연동 증거

1. Git 기본 설정 확인

git config –list

git config –global user.name “이름”

git config –global user.email “이메일”

2.GitHub 원격 저장소 연동 확인

git remote -v

origin https://github.com/사용자명/저장소명.git (fetch)
origin https://github.com/사용자명/저장소명.git (push)

1. 연결 상태 테스트 (Push/Pull)

git status

현재 변경된 파일이 있는지, 로컬 브랜치가 원격 브랜치(origin/main 등)와 동기화되어 있는지 알려줍니다.

not a git repository” 에러가 뜨나요?

해당 폴더에서 git init을 하지 않았거나, Git 설정이 시작되지 않은 상태입니다.

git remote -v를 쳤는데 아무것도 안 나오나요?

git remote add origin [저장소주소] 명령어로 GitHub 저장소를 연결해 주어야 합니다.

git config –global user.name “dana735”

git config –global user.email “lightview11@naver.com”

git config –list

git clone https://github.com/dana735/dev-workspace.git


git init git시작

git add .

git commit -m “첫 저장”

git remote add origin 저장소주소

git branch -M main

git push -u origin main

이후변경시

git add .파일추가

git commit -m “설명” 저장

git push github 업로드

1. 보안 및 개인정보 보호
2. 
민감 정보(토큰, 비밀번호 등) 노출 없음 확인 완료

3. 트러블슈팅
- 문제: Docker 빌드 시 COPY 경로 에러 발생
- 
- 해결: 올바른 디렉토리 경로에서 빌드 명령어 실행

## 절대경로 상대경로

1. 절대 경로 (Absolute Path)
정의: 최상위 루트(Root, /) 폴더부터 목적지까지 모든 경로를 다 적는 방식입니다.
특징: 내가 현재 어느 폴더에 있든 상관없이 항상 같은 곳을 가리킵니다.
예시 (Linux/Codespaces):
/workspaces/my-project/html/index.html
/usr/share/nginx/html (컨테이너 내부 경로)

3. 상대 경로 (Relative Path)
정의: '현재 내가 있는 위치(Current Working Directory)'를 기준으로 목적지를 찾는 방식입니다.
특징: 내가 어디에 있느냐에 따라 가리키는 곳이 달라집니다.
주요 기호:
. : 현재 폴더 (예: ./index.html)
.. : 상위 폴더 (한 단계 위로)
예시:
html/index.html (현재 폴더 안에 있는 html 폴더의 index.html)
../README.md (내 위치보다 한 단계 위에 있는 파일)

5. 한눈에 비교하기
구분	절대 경로 (Absolute)	상대 경로 (Relative)

시작점	최상위 루트 (/)	현재 위치 (./)

장점	어디서 실행해도 정확하고 명확함	경로가 짧고 폴더 이동 시 유연함

단점	경로가 길어서 복잡함	현재 위치가 바뀌면 경로가 깨짐

비유	"서울특별시 강남구 ... 101호"	"여기서 오른쪽으로 가서 첫 번째 집"


$(pwd)의 역할: 이 명령어는 **"현재 내 위치의 절대 경로"**를 자동으로 뽑아주는 도구입니다.
도커의 규칙: 도커의 -v 옵션은 호스트(내 컴퓨터) 쪽 경로를 적을 때 절대 경로를 쓰는 것을 권장(혹은 필수)합니다.
그냥 html:/...이라고 적으면 도커는 "이게 폴더 이름인가? 아니면 도커 볼륨 이름인가?" 하고 헷갈려 합니다.
그래서 $(pwd)/html (즉, /workspaces/repo/html)처럼 확실한 주소를 주는 것입니다.

🌟 꿀팁

터미널에서 pwd라고 입력해 보세요. 지금 당신이 서 있는 곳의 절대 경로가 나타납니다!



dex.html


# 절대 경로를 사용하여 연결 (pwd는 현재 경로)

docker run -d -p 8081:80 -v $(pwd)/html:/usr/share/nginx/html --name bind-test nginx

수정 테스트: 내 컴퓨터의 html/index.html 내용을 수정하고 브라우저(localhost:8081)를 새로고침했을 때 내용이 바로 바뀌는지 확인





*한번 더 연습

docker run -d \
  --name my-web \
  -p 8080:80 \
  -v $(pwd)/index.html:/usr/share/nginx/html/index.html \
  nginx

-d: 백그라운드 실행

-p 8080:80: 외부 8080 포트를 컨테이너 80 포트로 연결

-v $(pwd)/index.html:...: 이게 핵심! 현재 폴더의 파일을 컨테이너 내부 파일과 연결(마운트)합니다.

결과 확인하기

명령어를 입력하면 오른쪽 하단에 **"A service is running on port 8080"**이라는 알림창

Open in Browser 버튼을 클릭하세요.

8080 포트 옆에 지구본 모양 아이콘

브라우저 새 탭에 **"Hello, Docker Bind Mount!"**



<img width="571" height="224" alt="스크린샷 2026-11-14 151610" src="https://github.com/user-attachments/assets/267d1819-2286-4db8-96d2-b48e83757336" />

---

<img width="578" height="115" alt="스크린샷 2026-11-14 163917" src="https://github.com/user-attachments/assets/bade37ee-91bb-4551-ae11-c3c90b1a409e" />

---


<img width="858" height="166" alt="스크린샷 2026-11-14 164011" src="https://github.com/user-attachments/assets/61b2c80f-0b96-44df-9a4c-1790ce4d6e79" />

---

실시간 동기화: docker run을 다시 실행하지 않고도, 호스트(Codespaces)의 파일만 수정했는데 컨테이너 속 웹사이트가 즉시 바뀌었습니다.

개발 효율성: 소스 코드를 수정할 때마다 이미지를 새로 빌드하거나 컨테이너를 껐다 켤 필요가 없다는 것을 직접 확인

바인드 마운트의 장점: 도커 컨테이너를 중지하거나 새로 만들지 않아도, 내 컴퓨터(Codespaces)의 html/index.html 파일만 수정하면 웹사이트 내용이 즉시 바뀐다.




### 🖥️ 터미널 기본 명령어

| 현재 위치 확인 |

```
pwd

| 파일 목록 보기 |


ls


| 폴더 이동 |

```
cd 

폴더 만들기

mkdir


touch


| 파일 만들기 |

```
touch hello.sh


cat
```

| 파일 내용 보기 |

```
cat hello.sh
```

### 🔀 Git 명령어


git init
```

| 저장소 초기화 |
|

```
git clone
```

| 저장소 복사 |
|

```
git add
```

| 스테이징 |
|

```
git commit
```

| 저장 |
|

```
git push
```

| 업로드 |
|

```
git pull
```

| 다운로드 |

---

### 📂 경로 기호

---


/
```

| 루트(최상위) |
|

```
./
```

| 현재 폴더 |
|

```
../
```

| 상위 폴더 |
|

```
~
```

| 홈 폴더 |

---

| 명령어 | 결과 |
| --- | --- |
| `rm -rf dev-workspace` | 기존 폴더 삭제 |
| `git clone ...` | GitHub에서 코드 받아오기 ✅ |
| `cd dev-workspace` → `ls` | `README.md`, `scripts/` 폴더 확인 |
| `cd scripts` → `ls` | `hello.sh` 파일 확인 |
| `./hello.sh` | **Hello, World!** 출력 ✅ |

![명령어 참고 이미지](https://github.com/user-attachments/assets/edac78ea-3dbf-4a27-b9b2-7c8be204955b)
