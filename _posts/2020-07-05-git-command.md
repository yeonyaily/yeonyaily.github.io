---
titl: "git 명령어 정리"
categories:
  - github
---

### git 명령어 정리

#### add, commit
* git add index.html  index2.html  
index.html index2.html파일들을 Staging Area에 추가
* git add *.*  
현재폴더에 있는 모든 파일을 Staging Area에 추가
* git add *.html  
현재폴더의 html형식의 파일만 모두 Staging Area에 추가
* git commit –m “commit msg”  
vi화면이 나오지 않고 바로 “commit msg” 라는 메세지 입력
* git commit -am “commit msg”  
a가 add하겠다는 뜻이므로, add도 하고 “commit msg”라는 메세지도 함께 입력
* git commit  
vi창이 떠서 메세지를 입력할 수 있음
* rebase -i [수정할 커밋의 이전 커밋]  
커밋한 히스토리를 편집 또는 삭제 등의 커밋 수정할 때 사용
"수정할 커밋"~"현재 커밋(HEAD)" 범위에 있는 모든 커밋 리스트 출력
* reword  
커밋 사용 + 커밋 메시지 수정
* edit  
커밋사용 + 작업내용수정 + 커밋 메시지 수정
* squash  
해당 커밋을 이전 커밋과 합침(메시지도 합쳐짐)
* fixup  
해당 커밋을 이전 커밋과 합침
* exec  
각 커밋이 실행된 후 shell 명령어 실행
* drop  
해당 커밋 삭제
#### status, clean
* git status  
git의 현재 정보, 상태를 알려줌
* git clean -f  
untracked 파일을 모두 지울 수 있음
#### log
* git log --pretty=oneline --graph  
왼쪽부분에 어떻게 연결되고 병합되었는 지에 대한 정보를 시각화하여 볼 수 있음
* git log --author=Brandon  
저자 이름을 검색하여, Brandon라는 사람이 남긴 기록만 볼 수 있음
* git log --oneline  
log 제목만 알고 싶을 때, 리스트를 한 라인으로 출력
* reflog  
모든 참조(reference)기록을 확인 (맨 위에가 최근)
#### diff
* git diff  
워킹 디렉터리와 Staging area에서 실재 소스가 어떤 차이가 있는지 비교하는 명령어
* git diff --cached  
Commit 내용과 Staging area 비교하는 명령어
* git diff commit1 commit2  
Commit과 다른 Commit 비교하는 명령어
* git commit --amend  
제일 마지막 Commit 메시지를 수정해주는 명령어(저장: ctrl+o, 나감: ctrl+x)
#### reset (checkout)
* git checkout file1
file1의 이전 수정 상태로 돌려주는 명령어
* git reset --soft HEAD~  
reset의 soft형태로 HEAD이동, 해당파일 staged, WD 파일 보존, Commit하면 원래 상태로 복원가능한 명령어 (첫 번째 단계까지 진행->add가 비어있지 않음)
* git reset HEAD~2  
reset의 mixed형태 -> default형태
* git reset --mixed HEAD~  
reset의 mixed형태로 HEAD이동, 해당파일 unstaged, WD 파일 보존, Commit이 바로 불가능 (두 번째 단계까지 진행 -> add상태가 아닌 unstage상태임)
* git reset --hard HEAD~  
reset의 hard형태로 HEAD이동, 해당파일 unstaged, WD 파일 미보존 (세 번째 단계까지 진행 -> working directory 내용을 삭제)
#### rm
* rm sample.txt  
untrackde file들을 삭제하는 명령어
* git rm sample.txt  
tracked file들을 원격저장소와 로컬저장소에서 모두 삭제하는 명령어
* git rm —cached sample.txt  
tracked file들을 원격저장소에서만 삭제하고 로컬에서는 삭제하지 않는 명령어
#### clone
* git clone “Remote repo URL”  
원격 저장소에서 로컬 저장소로 복제 할 때, 복제해오는 주소의 이름으로 디렉토리 이름을 저장하는 명령어
* git clone “Remote repo URL” abc  
원격 저장소에서 로컬 저장소로 복제 할 때, 복제해오는 주소의 이름이 아닌 abc와 같은 사용자가 정의한 이름으로 디렉토리 이름을 저장하는 명령어
* git clone -b Lab1 “Remote repo URL” abc  
원격 저장소에서 로컬 저장소로 복제 할 때, branch가 여러개있을 때 선택하여 사용하는 명령어
#### remote
* git remote  
현재 연결되어있는 링크를 간단히 보여주는 명령어
* git remote -v  
현재 연결되어있는 링크를 좀 더 자세히 보여주는 명령어
* git remote add origin “remote repo URL”  
연결을 하고 싶을 때, 원격 저장소를 연결해주는 명령어
* git remote remove origin  
현재 연결을 제거하고 싶을 때, remote연결되어 있는 링크를 제거하는 명령어
#### pull, push, fetch
* git pull 사용법  
원격에서 변경된 사항을 가져와서 내 local과 합치는 작업(git pull origine master)
 	1) git pull origine master를 사용하여 pull을 실행한다.
	2) merge화면에서 ctr+o -> ctr x를 하여 저장한다.
	3) 원경 변경사항이 내 로컬에 적용된다.
* git push 사용법  
내 local을 원격으로 업로드 하는 작업(git push origine master)
	1) 원하는 repository를 만들고 주소를 복사한다.
	2) local repository를 원격 repository와 연결한다. 
	3) 원격 저장소의 아이디와 비밀번호를 입력한다.
	4) git push origine master을 사용하여 push한다.
* git fetch 와 git pull의 차이  
git fetch는 git pull과 다르게, 원격에서 변경된 사항을 가져오기만 하고 내 local과 합치지는 않음.
#### gitignore
* .gitignore란?  
Ignored File이란, git 저장소에서 관리할 필요가 없는 파일이나 폴더를 말한다.  
주로 컴파일된 파일, 실행시간에 생성된 파일, Hidden file, 개인적인 파일, 실행파일 디렉터리들을 ignored파일에 집어넣어 관리할 필요가 없게 분류 한다.
#### branch
* branch란?  
저장소를 처음 만들때 master라는 기본 branch가 생긴다.  
새로운 작업을 할 때는 master에서 직접하는 것이 이니라, 새로운  branch를 생성하여 작업한 후, master로 merge해야 한다.
* git branch –h  
현재 git branch에서 사용할 수 있는 옵션들을 보여주는 헬프페이지 
* git branch -a  
현재 저장소에 몇개의 원격, 로컬 branch가 있는지 보여주는 명령어 
* git branch  
현재 로컬에 어떤 branch가 있는지 알려주는 명령어
* git branch issue1  
issue1이라는 새로운 branch를 만드는 명령어
* git branch –d issue1  
issue1 branch를 삭제한다. 즉, -d는 branch를 삭제하는 옵션이다.
* git branch issue2  
issue2라는 branch를 만드는 명령어
* git branch –D issue1  
-D는 작업을 하는 도중에 현재 branch를 강제로 삭제하는 옵션
#### checkout
* git checkout issue2  
현재 brand에서 issue2 branch로 이동하는 명령어
* git checkout –b issue1  
issue1이라는 branch를 만들고 동시에 만든 branch로 이동하는 옵션
* git checkout master  
master branch로 이동하는 명령어
#### stash
* git stash  
워킹 디렉토리에서 수정된 완료되지 않은 작업들을 commit하지 않고 임시로 저장해주는 명령어
* git stash save  
git stash 와 같은 역할이며 뒤에 이름을 지정해 줄 수 있는 명령어
* git stash list  
지금가지 각 저장된 branch들을 목록화 해서 보여주는 명령어
* git stash pop  
저장된 stash를 리스트에서 꺼내서 삭제하고 현재 작업상태로 만드는 명령어(default값으로 맨 마지막에 넣은 값을 가짐)
* git stash apply  
pop과는달리 마지막 항목을 꺼낸 후 삭제하지는 않는 명령어
* git stash drop  
해당하는 stash 이름을 삭제하는 명령어
* git stash clear  
모든 리스트를 삭제하는 명령어 
#### merge
* git merge TopicA  
현재 branch에 TopicA라는 branch를 병합하겠다는 명령어
* git merge --no-ff TopicA  
fast forward marge를 하지 않고 no fast forward marge를 하는 명령어
* merge conflict 상황설명  
1) merge.txt라는 file을 vim을 사용하여 생성한다.
2) master branch에 v1을 만든다.
3) newBranch branch에 v2-B를 만든다.
4) master branch에 n2-A를 만든다.
5) v2-B와 v2-A를 merge하게되면 conflict가 발생한다. 
* merge conflict 해결방법  
vi merge.txt 를 사용하여 직접 file에 접근하여 원하는데로 수정하여 저장한다.
그 후에,  다시 git add와 git commit을 하여 v3를 만들어준다.
* merge --squash  
다른 브랜치에 있는 여러 개의 커밋을 하나로 묶어서 병합
* cherry-pick (해쉬키)  
다른 브랜치에 있는 커밋을 선택적으로 내 브랜치에 적용하는 명령어  
git merge를 사용한 충돌을 피할 수 있으며, 해쉬키는 커밋을 다시 한 것이기 때문에 바뀐다.
#### rebase
* rebase  
Marge와는 다른 형태의 병합  
새로운 브랜치의 base를 master의 마지막 commit으로 rebase
1. feature 브랜치로 chackout
2. master 브랜치로 rebase
3. Master 브랜치에서 feature를 병합(fast-forward merge)
즉, 페스트포워드 머지를 하고 싶을 때 사용하는 것
#### revert
* revert?  
commit된 스냅샷을 취소하는 명령어  
중간 이력들이 사라지지 않고 취소한 이력을 현재 이력에 기록하는 명령어  
* revert 와 reset의 차이  
revert는 취소하고자 하는 이력을 현재이력에 기록하여 그전의 중간이력들에 영향을 끼치지 않지만, reset은 내가 취소할 이력을 지정하게 되면 그 이후에 시행된 중간이력들이 모두 삭제되게 되는 차이가 있다.
