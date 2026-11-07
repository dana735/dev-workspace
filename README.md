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


---

## 4. 터미널 조작 로그 기록
```bash
# 현재 위치 확인
pwd

# 숨김 파일 포함 목록 확인
ls -la

# 디렉토리 생성 및 이동
mkdir workspace
cd workspace

# 빈 파일 생성 및 내용 확인
touch test.txt
echo "Hello Codespaces" > test.txt
cat test.txt

# 파일 복사, 이름 변경 및 삭제
cp test.txt test_backup.txt
mv test_backup.txt final.txt
rm final.txt

**5. 권한 실습 및 증거 기록**

```bash
# 실습 파일 및 디렉토리 생성
touch test_file.txt
mkdir sample_dir

# 변경 전 권한 확인
ls -l test_file.txt

# 권한 변경 (파일: 744, 디렉토리: 755)
chmod 744 test_file.txt
chmod 755 sample_dir

# 변경 후 권한 확인 결과
ls -ld test_file.txt sample_dir

# 변경 전 권한 확인
ls -l test_file.txt

# 권한 변경 (파일: 744, 디렉토리: 755)
chmod 744 test_file.txt
chmod 755 sample_dir

# 변경 후 권한 확인 결과
ls -ld test_file.txt sample_dir


6. Docker 설치 및 기본 점검
```bash
docker --version
docker info

## 7. Docker 기본 운영 명령어 및 컨테이너 실행 실습
```bash
docker images
docker ps -a
docker run hello-world
docker run -it ubuntu bash

## 8. 기존 Dockerfile 기반 커스텀 이미지 제작
- **선택한 베이스 이미지**: NGINX 베이스 이미지 활용
- **빌드 및 실행 명령어**:
  ```bash
  docker build -t my-custom-nginx .
  docker run -d -p 80:80 --name custom-web-server my-custom-nginx


## 9. 포트 매핑 및 접속 증거
- `-p 80:80` 포트 매핑 설정 및 접속 확인
  ```bash
  curl http://localhost:80

## 10. 바인드 마운트 반영 + Docker 볼륨 영속성 검증
```bash
docker volume create my_data_vol
docker run -d --name vol-test -v my_data_vol:/data ngin

## 11. Git 설정 및 GitHub 연동 증거
```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
git config --global init.defaultBranch main
git config --list

## 12. 보안 및 개인정보 보호
- 민감 정보(토큰, 비밀번호 등) 노출 없음 확인 완료

## 13. 트러블슈팅
- **문제**: Docker 빌드 시 `COPY` 경로 에러 발생
- **해결**: 올바른 디렉토리 경로에서 빌드 명령어 실행



