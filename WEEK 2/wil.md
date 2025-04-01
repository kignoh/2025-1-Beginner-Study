#Issue 만들기    
1. 개발입문 레포지토리로 간 뒤에 issue -> new issue를 누른다.    
2. 이슈 옆에 번호는 몇번재 이슈인지 알려준다.    
    이 번호는 BRANCH NAMING CONVENTION에 쓰일 번호이다.   
3. 이슈를 생성했으니 BRANCH를 만들 차례   
4. git branch - 현재 브랜치 확인하기 / git branch -a : 모든 브랜치 확인하기   
5. git branch를 했을때 *이 붙어있는 branch가 현재 위치의 branch이다.
6. git branch "브랜치이름" : 브랜치 생성하기 / git branch -D "브랜치 이름" : 브랜치 삭제하기 -d여도 된다.
7. 현재 내가 위치한 브랜치를 지우고 싶다면 다른 브랜치로 이동한 후에 해당 브랜치를 지워야한다.
8. git checkout "브랜치 이름" : ""사이에 입력한 브랜치로 이동하기
9. git chechout -b "브랜치이름" : ""에 입력한 브랜치가 새로 생성됨과 동시에 그 브랜치로 이동한다.   
10. git status를 했을때 (untracked files)라고 뜬다면 git add를 해줘야한다. git add .은 모든 untracked file들에 대해서 add를 하는 것이고 git add 옆에 ""안에 파일명을 작성하면 그 파일만 add하는것이다. 이때 내가 전체 폴더 내부에 WEEK2를 만들고 그 내부에 새로운 README.md와 wil.md를 만들고 나서 git add .을 했더니    
On branch docs/1-readme
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   WEEK 2/README.md
        new file:   WEEK 2/wil.md    
위와 같이 출력됐다.    

11. add를 해준 다음 commit을 해준다.   
12. git commit -m "docs : readme 생성" 에서 -m은 별도의 텍스트 편집기를 열지 않고 메세지를 커맨드라인에 직접 지정하는 역할을 한다.   
13. visual studio code 오른쪽 2분할로 된 상자와 돋보기 모양을 누르면 마크다운 형식의 파일을 미리보기 할 수 있다.   
14. 이게 파일을 수정하고 아무것도 안하면 git status를 해도 그냥   
On branch docs/1-readme
nothing to commit, working tree clean   
위와같이만 뜬다. commit을 해야할 것만 같은데 말이지? 이럴때 파일을 한 번 save해주고 다시 git status를 보면 수정하고 save해준 파일이 modified로 빨간색으로 떠있을 것이다.   
15. git add "WEEK 2/README.md" 이와 같이 한다면   
    
On branch docs/1-readme
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory) 
        modified:   WEEK 2/README.md
   
위와 같이 원래는 Changes not staged for commit이라고 떠있고 빨간색 modified가 떠있었다면   
   
On branch docs/1-readme
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   WEEK 2/README.md   
   
Changes to be committed로 변경된 후에 초록색 modified로 달라진다.   
   
디렉토리 내부의 파일을 수정한 이후에는 commit 하기 위해서 항상 add를 해줘야하는거야?


ChatGPT의 말:
11초 동안 Reasoned about git add necessity
네, 기본적으로 Git에서는 수정된 파일을 커밋하기 전에 그 변경사항을 staging area에 추가해야 합니다. 다시 말해,

수정된 파일 → git add → staging area → git commit → local repository
이런 과정을 거치게 됩니다.

다만, 이미 Git이 추적 중인 파일의 변경사항에 한해서는 git commit -a 옵션을 사용하면 자동으로 수정된 파일들을 스테이징 영역에 추가하고 커밋할 수 있습니다.
하지만 새로운 파일이나 선택적으로 일부 변경사항만 커밋하고자 할 때는 반드시 git add로 원하는 파일을 명시적으로 스테이징해야 합니다.   
   
git이 추적 중이라는 파일이 무슨 말이야?


ChatGPT의 말:
10초 동안 Reasoned about Git tracked files
Git이 추적 중인 파일은 Git이 버전 관리 대상으로 이미 추가하여(즉, 이전에 한 번 이상 커밋한) 변경 사항을 계속해서 기록하고 있는 파일을 말합니다.

추적(tracked) 파일:

이미 Git에 의해 관리되고 있는 파일입니다.

이전에 git add와 git commit으로 커밋한 파일로, 이후에 변경된 내용은 Git이 변경 사항으로 인식합니다.

비추적(untracked) 파일:

Git이 아직 관리하지 않는 파일로, 커밋 대상에 포함되지 않습니다.

예를 들어, README.md 파일을 처음 생성하고 git add README.md로 추가한 후 git commit을 하면 이 파일은 추적 상태가 됩니다. 이후 파일을 수정하면 Git은 이 변경 사항을 추적하지만, 새로운 파일이나 추적되지 않은 파일은 별도로 git add를 해줘야 커밋할 수 있습니다.   
   
