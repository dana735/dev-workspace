# dev-workspace
개발자 작업실 꾸미기 과제

> 본 문서는 도커 및 클라우드 개발환경(GitHub Codespaces)을 활용한 과제 수행 결과 기술 문서입니다.

---

## 1. 프로젝트 개요 및 미션
- 프로젝트 개요: 도커 기반 컨테이너 실행 및 개발 환경 구축 실습
- 과제 미션: 깃허브 저장소를 통한 도커 컨테이너 빌드 및 검증 과정 문서화
- 학습 목표: 
  - 도커 이미지 및 컨테이너 라이프사이클 이해
  - Dockerfile 작성 및 포트/볼륨 바인딩 실습
  - Git / GitHub를 활용한 버전 관리 및 형상 관리

---

## 2. 실행 환경 정보 (Environment)
- OS (Operating System): Linux (GitHub Codespaces 컨테이너 환경)
- Shell: Bash
- Terminal: VS Code Integrated Terminal
- Docker Version: (터미널에서 `docker --version` 입력 후 결과 기입)
- Git Version: (터미널에서 `git --version` 입력 후 결과 기입)

---

## 3. 수행 항목 및 체크리스트
- [x] GitHub 공개(Public) 레포지토리 생성 및 코드스페이스 연결
- [x] 도커(Docker) 기본 명령어 및 버전 확인 완료
- [x] Dockerfile 작성 및 커스텀 이미지 빌드
- [x] 컨테이너 실행 시 포트포워딩 및 볼륨(Volume) 마운트 적용
- [x] Git을 이용한 커밋 및 깃허브 원격 저장소 푸시 완료

---

## 4. 핵심 구현 내용 및 검증 방법
> 각 항목별 수행 명령과 확인 방법을 기술합니다.

### [A] Dockerfile 작성 및 빌드
- 작성 내용: Ubuntu/Python 기반 가볍고 안정적인 베이스 이미지 설정 및 작업 디렉토리 지정
- 실행 명령:
  ```bash
  docker build -t dev-env:latest .
