# Git 명령어 정리

### Git 저장소 생성

`git init`  
_$ git init_

- 현재 디렉토리에 git 저장소를 생성
- 해당 디렉토리의 파일들을 git을 통해 버전관리를 할 수 있게 한다
- Github에 레포지토리를 생성하고 `git remote` 명령어를 입력하면 원격 저장소와 로컬 저장소를 연결하여 사용할 수 있다

`git clone`  
_$ git clone (원격 저장소 주소)_

- 이미 생성되어있는 Github의 원격 저장소를 로컬에 복제
- `git remote` 명령어를 따로 사용하지 않아도 원격과 로컬의 저장소가 연결된다

---

### Git에 반영 및 Github에 업로드

`git add(스테이징)`  
_$ git add ._

- 로컬 저장소의 변경 사항을 Github에 반영하기 위해 내용들을 추가(= 스테이징)
- 디렉토리의 모든 변경사항을 스테이징

`git commit(커밋)`  
_$ git commit -m "커밋메세지"_

- 스테이징된 항목들을 Git에 반영

`git push(푸쉬)`  
_$ git push_

- Git에 반영된 변경사항을 Github 원격 저장소에 업로드

---

### 원격 저장소의 변경사항을 로컬 저장소에 반영

`git pull`  
_$git pull (원격저장소 이름) (브랜치 이름)_

- 원격 저장소에 생긴 변경 사항을 로컬 저장소에 반영 하여 최신 상태로 유지(병합)

`git fetch`  
_$git fetch_

- 원격 저장소의 최신 이력 확인
- `git merge`명령어를 추가로 입력하면(변경 사항을 로컬에 반영) 결과적으로 `gitpull`과 같은 기능을 한다

---

### 조회 및 되돌리기

`git status`  
_$ git status_

- 스테이징된 항목 확인

`git log`  
_$ git log_

- Git의 커밋 기록 조회

`git reset`  
_$git reset (커밋번호 앞 6자리) --hard_

- 입력한 커밋번호 이후의 로그를 삭제한 후, 상태를 되돌린다

또는 다음과 같은 옵션을 사용할 수도 있다  
_$git reset (옵션) (파일명)_

- `--soft` : 이전 커밋으로 HEAD를 이동하면서 변경 사항은 유지
- `--mixed(기본값)` : 이전 커밋으로 HEAD를 이동하면서 변경 사항은 유지되지 않고 스테이징 영역으로 변경 사항을 이동
- `--hard` : 이전 커밋으로 HEAD를 이동하면서 변경 사항을 모두 삭제

---

**_reset과 revert의 차이_**

`reset` 특정 commit으로 돌아가고 이후의 commit들은 삭제

`revert` 특정 commit전의 상태로 되돌리면서, 되돌아갔다는 기록을 새로운 commit으로 남김
