1. 원하는 폴더 이동
   1. `cd [디렉토리]`
   2. 해당 폴더 우클릭 > 터미널 열기
2. `git init` : 초기화
3. `git config --global user.email "메일주소"`
4. `git config --global user.name "유저네임"`
5. 변동 사항 발생
   1. `touch 이름.확장자` : 생성
   2. 파일 수정
6. `git add 이름.확장자` or `git add .`
   1. `git status` : 상태 확인
7. `git commit -m "메세지"` : 로컬 커밋
   1. `git log` or `git log --oneline` : 상태 확인
8. `git push origin master` : 원격 업데이트