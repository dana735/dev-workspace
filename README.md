# 💻 내 컴퓨터에 개발자용 '작업실' 꾸미기

## 1. 프로젝트 개요 (미션 목표 요약)
- **목적**: GitHub Codespaces 및 Linux 환경을 기반으로 개발에 필요한 기본 터미널 조작, 파일 권한 관리, Docker 컨테이너 빌드·운영, 그리고 Git/GitHub 연동을 수행하고 이를 기술 문서로 기록한다.

---

## 2. 실행 환경
- **OS / 셸**: Linux (GitHub Codespaces) / Bash
- **Docker 버전**: (`docker --version` 결과 기입)
- **Git 버전**: (`git --version` 결과 기입)

---

## 3. 수행 항목 체크리스트
- [x] 터미널 기본 조작 (위치 확인, 파일/디렉토리 생성·이동·삭제 등)
- [x] 파일 및 디렉토리 권한 설정 및 변경 실습 (`chmod`)
- [x] Docker 설치 및 기본 점검 (`docker --version`, `docker info`)
- [x] Docker 기본 운영 명령어 수행 (`docker images`, `docker ps -a`, `docker logs`)
- [x] 컨테이너 실행 실습 (`hello-world`, `ubuntu` 컨테이너 진입 등)
- [x] 기존 Dockerfile 기반 커스텀 이미지 제작 및 빌드/실행 성공
- [ ] 포트 매핑 (`-p`) 및 브라우저 접속 성공 증거 첨부
- [ ] 바인드 마운트 및 Docker 볼륨 영속성 검증
- [x] Git 설정 및 GitHub 연동 완료
- [x] 절대경로 상대경로

---

## 4. 터미널 조작 로그 기록

```bash
# 현재 위치 확인
cd

#폴더 생성
mkdir pracetice

지금 위치: C:\Users\임미정\dev-workspace
cd dev-workspace
# 이동 후:  C:\Users\임미정\dev-workspace

#디렉토리 생성및 이동

 mkdir scripts  
 cd scripts
C:\Users\임미정\dev-workspace\scritps>

# 숨김 파일 포함 목록 확인
ls -la


# 빈 파일 생성 및 내용 확인
touch test.txt
ls

echo "Hello,World!" > hello.txt
ls
cat hello.txt
cat memo.txt
echo "I am a linux master" > memo.txt
cat memo.txt
I am a linux master
echo "I love Docker" >> memo.txt


# 파일 복사, 이름 변경 및 삭제
cp secret/my_note.txt backup.txt
cp -r secret secret_backup 전체
mv my_note.txt secret/
rm final.txt
cat backup.txt



<img width="534" height="258" alt="image" src="https://github.com/user-attachments/assets/fb642413-b6a4-4d15-a388-8480816db2fc" />



##5. 권한 실습 및 증거 기록
'''bash
<img width="265" height="103" alt="image" src="https://github.com/user-attachments/assets/50e7de70-ebae-4cc9-ac68-ffe34445465a" />

# 실습 파일 및 디렉토리 생성
touch apple.txt
ls
chmod 744 test.txt


# 변경 전 권한 확인
ls -l apple.txt

# 권한 변경 (파일: 744, 디렉토리: 755)
chmod 744 apple.yxt
chmod 755 test_dir
# 변경 후 권한 확인 결과
ls -ld apple.txt 

<img width="370" height="86" alt="image" src="https://github.com/user-attachments/assets/0d996472-c144-4259-a79e-612f1afe269d" />


6. Docker 설치 및 기본 점검 Dockerfile
docker --version
docker info

# #Dockfle
# 1. 파이썬이 설치된 가벼운 리눅스를 가져옵니다.
FROM python:3.9-slim

# 2. 가상 컴퓨터 안에 /my_folder라는 폴더를 만듭니다.
RUN mkdir /my_folder

# 3. 아까 우리가 만든 apple.txt를 가상 컴퓨터의 폴더로 복사합니다.
COPY apple.txt /my_folder/apple.txt

# 4. 컴퓨터가 켜지면 apple.txt 내용을 화면에 보여주도록 설정합니다.
CMD ["cat", "/my_folder/apple.txt"]
 
😊실습

Dockerfile 만들기
echo 'FROM alpine' > Dockerfile
echo 'CMD ["echo", "Hello, Docker! I am learning!"]' >> Dockerfile

이미지 빌드업
docker build -t my-first-image .

컨테이너 실행
docker run my-first-image

7. Docker 기본 운영 명령어 및 컨테이너 실행 실습

<img width="366" height="95" alt="image" src="https://github.com/user-attachments/assets/f8c80d8f-0100-49b5-bc38-6b9b2c76810e" />


docker images
docker ps -a
docker run hello-world
docker run -it ubuntu bash

#실행
docker run hello-world
# -it 옵션: 컨테이너와 상호작용(interactive)하고 터미널(tty)을 연결하겠다는 뜻입니다.
docker run -it ubuntu bash
# -d: 백그라운드 실행 (Detached mode)
# -p 8080:80: 내 컴퓨터의 8080 포트를 컨테이너의 80 포트로 연결
docker run -d -p 8080:80 --name my-server nginx

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

8. 기존 Dockerfile 기반 커스텀 이미지 제작
- 선택한 베이스 이미지: NGINX 베이스 이미지 활용
- 빌드 및 실행 명령어:

  docker build -t my-custom-nginx .
  docker run -d -p 80:80 --name custom-web-server my-custom-nginx

9. 포트 매핑 및 접속 증거😊

# -d: 백그라운드 실행 (Detached mode)
# -p 8080:80: 내 컴퓨터의 8080 포트를 컨테이너의 80 포트로 연결
docker run -d -p 8080:80 --name my-server nginx


- -p 80:80 포트 매핑 설정 및 접속 확인
  curl http://localhost:80

<img width="1258" height="314" alt="스크린샷(1) png1" src="https://github.com/user-attachments/assets/a9b901f3-d73f-4827-b0f2-a74d0209b6dd" />

<img width="387" height="168" alt="image" src="https://github.com/user-attachments/assets/7ddb9be6-94df-48c9-ae27-cad74286ca4f" />
<img width="1280" height="1024" alt="image" src="https://github.com/user-attachments/assets/40b5d99d-984d-4f1e-a775-a89c2a3781d1" />


10. 바인드 마운트 반영 + Docker 볼륨 영속성 검증

docker volume create my_data_vol
docker run -d --name vol-test -v my_data_vol:/data nginx

11. Git 설정 및 GitHub 연동 증거

git config --global user.name "임미정"
git config --global user.email "lightview11@naver.com"
git config --list
git clone https://github.com/dana735/dev-workspace.git
,,,bash
git init git시작
git add .
git commit -m "첫 저장"
git remote add origin 저장소주소
git branch -M main
git push -u origin main
이후변경시
git add .파일추가
git commit -m "설명" 저장
git push github 업로드

12. 보안 및 개인정보 보호
민감 정보(토큰, 비밀번호 등) 노출 없음 확인 완료

13. 트러블슈팅
- 문제: Docker 빌드 시 COPY 경로 에러 발생
- 해결: 올바른 디렉토리 경로에서 빌드 명령어 실행

14.절대경로 상대경로
절대경로
/c/Users/lightview117307/Documents
cd..
/c/Users/lightview117307
<img width="266" height="184" alt="image" src="https://github.com/user-attachments/assets/f868a36e-ece6-4a0f-87e5-8ca2d2b2fce3" />



15.명령어

--
## 📝 과제 1 핵심 용어 & 명령어 정리

### 🖥️ 터미널 기본 명령어

| 명령어 | 뜻 | 예시 |
|--------|-----|------|
| `pwd` | 현재 위치 확인 | `pwd` |
| `ls` | 파일 목록 보기 | `ls` |
| `cd` | 폴더 이동 | `cd scripts` |
| `mkdir` | 폴더 만들기 | `mkdir scripts` |
| `touch` | 파일 만들기 | `touch hello.sh` |
| `cat` | 파일 내용 보기 | `cat hello.sh` |

### 🔀 Git 명령어

| 명령어 | 뜻 |
|--------|-----|
| `git init` | 저장소 초기화 |
| `git clone` | 저장소 복사 |
| `git add` | 스테이징 |
| `git commit` | 저장 |
| `git push` | 업로드 |
| `git pull` | 다운로드 |

### 📂 경로 기호

| 기호 | 뜻 |
|------|-----|
| `/` | 루트(최상위) |
| `./` | 현재 폴더 |
| `../` | 상위 폴더 |
| `~` | 홈 폴더 |

---


| 명령어 | 결과 |
|--------|------|
| `rm -rf dev-workspace` | 기존 폴더 삭제 |
| `git clone ...` | GitHub에서 코드 받아오기 ✅ |
| `cd dev-workspace` → `ls` | `README.md`, `scripts/` 폴더 확인 |
| `cd scripts` → `ls` | `hello.sh` 파일 확인 |
| `./hello.sh` | **Hello, World!** 출력 ✅ |

<img width="292" height="126" alt="image" src="https://github.com/user-attachments/assets/edac78ea-3dbf-4a27-b9b2-7c8be204955b" />

