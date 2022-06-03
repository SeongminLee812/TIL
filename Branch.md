# Today I learned

## branch
> 버전관리의 꽃
  branch = 나뭇가지

- master에서 뻣어나온 줄기
- 브랜치란 나뭇가지처럼 여러 갈래로 작업 공간을 나누어 독립적으로 작업할 수 있도록 도와주는 Git의 도구
- 브랜치의 목적 : 이전 commit들을 가진 독립적인 공간에서, master브랜치에 영향없이 작업할 수 있도록 함
- master에서 빠져나와 branch에서 실험한 후 이상이 없으면 다시 master branch에 병합함

### branch 명령어
- 브랜치 목록 확인   
`git branch`
- 새로운 브랜치 생성   
`git branch 브랜치 명`
- 브랜치 삭제 1(병합된 브랜치)   
`git branch -d 브랜치명`
- 브랜치 삭제 2(병합되지 않은 것도 강제삭제)   
`git branch -D 브랜치명`
- 브랜치 생성하면서 해당 브랜치로 이동
`git switch -c 브랜치명`

## Branch Merge
> 브랜치를 통해 독립된 작업공간을 만든 이후에는 작업 내용을 master에 반영해야함 <br> 
> 병합은 merge 명령어를 통해 가능함

1. 우선 메인 브렌치(master branch)로 switch 해준다
2. 현재 브랜치에 병합할 브랜치를 입력한다.   
3. `git merge 대상브랜치`

> 이후 `git log --oneline --all --graph` 명령어로 브랜치를 확인할 수 있다.
---
   ---
## Git을 이용한 협업
> 보통 master로 개발하는 것이 아니라 기능별로 branch를 따로 만들어서 개발
### 원격 저장소의 소유권이 있는 경우
> 원격 저장소가 자신의 소유이거나, collaborator로 등록된 경우   
1. 원격 저장소를 로컬 저장소로 clone   
  `git clone URL`
2. 로컬에서 브랜치 생성 후 커밋 등 작업
   `git branch 브랜치명`, `git switch 브랜치명`
3. 원격 저장소에 해당 브랜치를 push
   `git push origin 브랜치명`
   > 이때 master를 push하는 게 아니라, 내가 **2번에서 만든 branch**를 push 하자
4. pull request를 통해 나의 branch를 master에 반영해달라는 요청을 보냄
5. 병합이 완료되면 병합된 원격 저장소의 master 내용을 pull한다.


### Fork를 이용한 경우
1. 해당 원격 저장소에서 우측 상단 fork 클릭해서 내 원격 저장소로 가져오기
2. 내 원격저장소에 저장된 fork repository를 clone하기
3. branch를 생성하고 기능을 구현하기
4. 해당 branch를 1번에서 만든 내 원격 저장소(복제본)에 push하기
`git push origin 브랜치명`
5. pull request를 통해 원본 저장소 관리자에게 반영 여부 요청하기
6. 반영되면 remote add upstream 원본 저장소 url하여 원본 저장소를 연결하고, pull upstream master로 master를 가져오기

