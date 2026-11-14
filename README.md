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
- [ ]  바인드 마운트 및 Docker 볼륨 영속성 검증
- [x]  Git 설정 및 GitHub 연동 완료
- [x]  절대경로 상대경로

---

## 4. 터미널 조작 로그 기록

# 1. 현재 위치 확인

cmd
PS C:-workspace> cd

C:-workspace

powershell pwd

# 2. 폴더 생성 (practice)

PS C:-workspace> mkdir scrips

```
디렉터리: C:\Users\USER\dev-workspace
```

Mode LastWriteTime Length Name
—- ————- —— —-

# 3. 목록 확인 (숨김 파일 포함)

PS C:-workspace> dir /a
# (여기에 현재 폴더의 모든 파일과 폴더 목록이 출력됩니다)

# 4. scripts 폴더 생성 및 이동

PS C:-workspace> mkdir scripts

C:-workspace>

cd scripts

C:-workspace>cd scripts

C:-workspace>

# 5.삭제

PS C:-workspace> rm scripts

PS C:-workspace> dir

# (scripts 폴더가 목록에서 사라진 것을 확인)

# 파일있었으면

PS C:-workspace> rm test.txt

PS C:-workspace> dir
(파일이 삭제되어 목록에 아무것도 나타나지 않음)

# 명령어 cd.. 상위 폴더 이동후 위 작업 실시

PS C:-workspace> cd ..

PS C:-workspace>

# 5. 숨김 파일 포함 목록 확인 (PowerShell에서는 ls -la 대신 ls -Force 사용 권장)

PS C:-workspace> ls -Force

```
# (현재는 비어있으므로 아무것도 나오지 않거나 . 과 .. 만 보입니다)
```

# 6. 빈 파일 생성 톅스트 쓰기

리눅스로 옮김

touch test.txt # 빈 파일 생성
ls # 파일 목록 확인

echo “Hello, World!” > hello.txt 파일안으로 >
cat 파일 화면 출력 내용 확인
cat hello.txt

echo “I am a linux master” > memo.txt

echo “I love Docker” >> memo.txt

내용 추가 (Append)

cat memo.txt

두줄이 다 나오는지 확인

# 7 .복사 및 폴더 관리 ***중요!

mkdir secret # 1. secret 폴더 만들기

touch secret/my_note.txt # 2. 폴더 안에 파일 만들기

cp secret/my_note.txt backup.txt # 3. 파일을 밖으로 복사

cp -r secret secret_backup # 4. 폴더 전체를 복사 (-r 필수!)

cp -r 폴더 파일 모두 복사

백업 파일 이유
rm -rf secret # 아차! 폴더를 실수로 지웠다!

ls secret # 파일이 없어서 에러 발생

cat backup.txt # 휴, 밖에 복사해둔 파일은 무사하네!

mkdir secret # 폴더 다시 만들고

cp backup.txt secret/my_note.txt # 백업본을 다시 폴더 안으로 복사해서 복구!

# 8.이동 및 삭제

mv backup.txt secret/ # backup.txt를 secret 폴더로 이동

rm test.txt # test.txt 삭제

- rm final.txt # final.txt가 있다면 삭제

## 5. 권한 실습 및 증거 기록

# 실습 파일 및 디렉토리 생성

touch apple.txt

# 변경 전 권한 확인

ls -l apple.txt 644

# 권한 변경

chmod 600 apple.txt

# 변경 후 권한 확인 결과

ls -ld apple.txt

-l (long 길게 파일 세부 상세)

ls -d (directory 내용말고 폴더 자체 정보만 딱)

- rw——- 600

chmod 755 apple.txt

ls -l apple.txt

- rwxr-xr-x

## 6. Docker 설치 및 기본 점검 Dockerfile

# docker –version

버전 표시

docker run hello-world

- **도커 데스크 탑 실행 안해서 에러뜸
실행후

“HELLO from Docker!”

# 이미지 컨테이너 목록 확인및 정리 흔적이 있는가

docker ps -a all

NAME hello-world 컨테이너 STATUS Exited 실행흔적 뜻 잘실행

image

# 이미지 목록 확인

docker images

레지스토리에 hello-world 보임

# 컨테이너 삭제

docker rm [컨테이너_ID] 도커는 아이디 앞 세자리만 해도 됨

docker rm 705 20b a5c 세개 만들어져 있었음

- 이미지 삭제 (설계도)

docker rmi hello-world

docker rmi hello-world my-web-server

ㅇocker system prune 한번에 지우기

확인

docker ps -a

docker images

image

## Dockfile

# 실습용 파일

mkdir my-web-site

cd my-web-site

현재 위치 ~ my-web-site 폴더에 잘 들어옴

간단한 HTML 파일 만들기

echo “” > index.html

# Hello, Docker Build!


ls

cat index.html

파일 내용 화면에 보여달라

cat Dockerfile

도커 파일 보여줘

# 도커파일 작성하기

nano Dockerfile

nano 편집기 빠져 나올때 Ctrl= X

# 1. 베이스 이미지 설정 (가벼운 nginx 서버 사용)

FROM nginx:alpine

# 2. 내가 만든 index.html 파일을 컨테이너 안의 웹 서버 경로로 복사

COPY index.html /usr/share/nginx/html/index.html

저장 Ctrl +0-> Ctrl+ x

# 3.이미지 빌드하기 # 가장중요!!!

docker build -t my-custom-web:1.0 .

- . 꼭!! 현재 폴더 도크 파일 사용하겠다!

# 4.빌드된 이미지 확인

docker images

image

my-custom-web:1.0 이미지 이름 보이면 성공 web 뒤:1.0이 방금 내가 만든 거 이름

이미지 ID 1ee~ c8a 두개 아마 도커 파일에 두번 복사되어서 그런듯

~my-web-site 폴더내 작업 수행인뜻

# 웹서버 실행

docker run -d -p 8080:80 –name my-web-container my-custom-web:1.0

- d컨테이너 백그라운드 진행
- p 8080;80
8080번 포트로 들어오는 신호를 컨테이너안 80번{웹기본포트} 포트로 전달
- 포트; 데이터 문 출입구 건물안의 방
- ip: 주소

컨테이너 실행확인

docker ps

image

my-web-sever 또는 my-web container 보이면 성공

웹주소창 http://localhost:8080 직접치기

Hello,Docker Build!

image

- 마무리 정리 컨테이너 끌때
- 멈추기

docker stop my-web-server

- 삭제 이미지는 남음

docker rm my-web-server

#1. 파이썬이 설치된 가벼운 리눅스를 가져옵니다.

FROM python:3.9-slim

#2. 가상 컴퓨터 안에 /my_folder라는 폴더를 만듭니다.

RUN mkdir /my_folder

#3. 아까 우리가 만든 apple.txt를 가상 컴퓨터의 폴더로 복사합니다.

COPY apple.txt /my_folder/apple.txt

#4. 컴퓨터가 켜지면 apple.txt 내용을 화면에 보여주도록 설정합니다.

CMD [“cat”, “/my_folder/apple.txt”]

😊실습

# Dockerfile 만들기

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

# 실행
docker run hello-world
# -it 옵션: 컨테이너와 상호작용(interactive)하고 터미널(tty)을 연결하겠다는 뜻입니다.
docker run -it ubuntu bash
# -d: 백그라운드 실행 (Detached mode)
# -p 8080:80: 내 컴퓨터의 8080 포트를 컨테이너의 80 포트로 연결
docker run -d -p 8080:80 –name my-server nginx

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
    
1. 포트 매핑 및 접속 증거😊

# d: 백그라운드 실행 (Detached mode)

# p 8080:80: 내 컴퓨터의 8080 포트를 컨테이너의 80 포트로 연결

docker run -d -p 8080:80 –name my-server nginx

- p 80:80 포트 매핑 설정 및 접속 확인
curl http://localhost:80

스크린샷(1) png1

image

image

1. 바인드 마운트 반영 + Docker 볼륨 영속성 검증
2. 

docker volume create my_data_vol

docker run -d –name vol-test -v my_data_vol:/data nginx

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

절대경로
/c/Users/lightview117307/Documents
cd..

/c/Users/lightview117307

## 바인드 마운트 및 Docker 볼륨 영속성 검증 터미널 기본 조작 (위치 확인, 파일/디렉토리 생성·이동·삭제 등)

**도커가 없어서 깃허브 코드스페이스 이용

# 바인드 마운트 검증 및 증거

테스트용 HTML 파일 만들기
 (현재 폴더에 index.html 파일을 만듭니다.)

# 현재 경로에 html 폴더를 만들고 컨테이너와 연결

mkdir html

echo "<h1>Hello, Docker Bind Mount!</h1>" > index.html


 
수정 테스트: 내 컴퓨터의 html/index.html 내용을 수정하고 브라우저(localhost:8081)를 새로고침했을 때 내용이 바로 바뀌는지 확인합니다.
증거: 터미널에서 ls html 결과와 브라우저의 수정된 화면을 캡처하세요.


2. Nginx 컨테이너 실행 (바인드 마운트 적용)
이제 이 파일을 도커 컨테이너와 연결해서 실행합니다. 아래 명령어를 통째로 복사하세요.

docker run -d \
  --name my-web \
  -p 8080:80 \
  -v $(pwd)/index.html:/usr/share/nginx/html/index.html \
  nginx

-d: 백그라운드 실행

-p 8080:80: 외부 8080 포트를 컨테이너 80 포트로 연결

-v $(pwd)/index.html:...: 이게 핵심! 현재 폴더의 파일을 컨테이너 내부 파일과 연결(마운트)합니다.

결과 확인하기

명령어를 입력하면 오른쪽 하단에 **"A service is running on port 8080"**이라는 알림창이 뜰 거예요.

Open in Browser 버튼을 클릭하세요.

브라우저 새 탭에 **"Hello, Docker Bind Mount!"**



<img width="571" height="224" alt="스크린샷 2026-11-14 151610" src="https://github.com/user-attachments/assets/267d1819-2286-4db8-96d2-b48e83757336" />


image

15.명령어

## 📝 과제 1 핵심 용어 & 명령어 정리

---

### 🖥️ 터미널 기본 명령어

---

| 명령어 | 뜻 | 예시 |
|——–|—–|——|
|

```
pwd
```

| 현재 위치 확인 |

```
pwd
```

|
|

```
ls
```

| 파일 목록 보기 |

```
ls
```

|
|

```
cd
```

| 폴더 이동 |

```
cd scripts
```

|
|

```
mkdir
```

| 폴더 만들기 |

```
mkdir scripts
```

|
|

```
touch
```

| 파일 만들기 |

```
touch hello.sh
```

|
|

```
cat
```

| 파일 내용 보기 |

```
cat hello.sh
```

|

---

### 🔀 Git 명령어

---

| 명령어 | 뜻 |
|——–|—–|
|

```
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

| 기호 | 뜻 |
|——|—–|
|

```
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
