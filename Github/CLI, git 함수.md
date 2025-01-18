# CLI / git 함수

<br/>

## CLI 함수
### `.`
- 현재 디렉토리 (폴더)
### `..`
- 상위 디렉토리
### `cd [디렉토리]`
- 폴더 이동 (change directory)
### `touch [파일이름.확장자]`
- 파일 생성
### `ls`
- 현재 디렉토리 내부 파일/폴더 출력
### `mkdir [디렉토리이름]`
- 새 디렉토리 생성
### `rm [파일이름]`
- 파일 삭제
- 디렉토리 삭제는 -r 옵션 추가

<br/>

## git 함수
### `git init`
- 로컬 저장소 설정(초기화)
- ***git 로컬 저장소 안 git 로컬 저장소 만들기 x, 관리 안됨***
### `git config --global user.eamil "메일주소"`
### `git config --global user.name "유저네임"`
- commit 작성자 정보 입력
- global : 전역변수 설정, 재입력 x
### `git add [파일이름]`
- 변경사항 있는 파일 staging area 추가
- `git add .`으로 현재 디렉토리 전부 업데이트 가능
### `git commit -m "메세지"`
- staging area에 있는 파일들을 저장소에 기록
- 해당 시점 변경 "메세지"를 통해 설명
### `git status`
- 현재 로컬 저장소 파일 상태 확인
### `git log`
- commit history 확인
- `git log --oneline`으로 한 줄 확인 가능
### `git global -l`
- git global 설정 정보 확인
### `git remote add origin remote_repo_url`
- 로컬 저장소에 원격 저장소 추가
- `origin` : 로컬 저장소 이름 (관례, 변경 가능)
- `remote_repo_url` : 원격 저장소 주소(위치)
- 로컬 저장소 하나에 여러 원격 저장소 추가 가능
### `git push origin master`
- 원격 저장소에 commit 목록을 업로드
- `origin` : 위의 연결시 설정한 저장소 이름.
- `master` : 연결할 브랜치 이름. 기본값
### `git pull origin master`
- 원격 저장소 변경 사항 받아옴 (업데이트)
### `git clone remote_repo_url`
- 원격 저장소 전체 복제 (다운로드)
- clone받은 프로젝트는 이미 `git init`된 상태
### `git remote -v`
- 현재 로컬 저장소 저장 원격 저장소 목록 보기
### `git remote rm 원격_저장소_이름`
- 현재 로컬 저장소에 등록된 원격 저장소 삭제
---
## `git commit --amend` : commit 수정하기
1. commit 실수 발생
2. `git log --oneline`으로 commit hash 값 확인 (맨 앞의 영어+숫자)
3. `git commit --ammend` 입력
4. Vim 에디터 실행
   1. `ESC` : 명령어 >> 수정 모드
   2. 키보드로 커서 이동 후 `i` : insert 모드
   3. 텍스트 수정
   4. `ESC` : 수정 >> 명령어 모드
   5. `:wq` : 저장하고 종료 (write and quit)
   6. `git log --oneline`로 확인
- 내용 변경, 새 hash 값으로 변경
- ***다른 commit이 발생함!***
---
## `revert` vs `reset` : commit 없애기
### `git revert <commit id>`
- 특정 commit을 없애는 commit
- `commit id` : `git log --oneline`으로 확인
- 재설정, 단일 commit 실행 취소하는 새 commit
### `git reset [옵션] <commit id>`
- 되돌리기, 시계 감기
- 특정 commit 복귀 후 이후 commit 모두 삭제
- 삭제한 commit을 어떻게 하냐? > `[옵션]`
1. `--soft`
- 삭제된 commit > staging area 남김
- 다음 commit에 포함
2. `--mixed` (기본값)
- 삭제된 commit > working directory 남김
- 다음 commit에 포함 x
3. `--hard`
- 삭제된 commit 기록 x
---
## git undoing : 뒤로감기
### `git retore <file>` : modified 상태 파일 되돌리기
- working directory 수정 사항 취소
- 원래 파일 덮어씀, 수정 사라짐
## staging area 파일 되돌리기
### `git rm --cached`
- git에 한번도 commit이 발생하지 않은 경우
### `git restore --staged`
- git에 한번이라도 commit이 발생한 경우