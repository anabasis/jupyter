# GIT

## uftrace

## 실습

### Stage 1

- Git bash 실행
- 경로 이동
- 해당폴더를 git초기화
- 편집기로 README.md 파일(commit_1) 만들고 본인 이름 적고나서 add 입력
- 첫 commit하기

```bash
mkdir git-training
cd git-training
git init
git add README.md
git commit -m "Add README file"
```

### Stage 2

- 상태를 확인
- knapsack 알고리즘 문제 파일(commit_2)을 commit할 준비
- 다시한번 상태를 확인해서 1)과 달라졌음
- 준비된 파일을 커밋
- commit 확인

```bash
git status
git add knapsack_problem.pdf
git status
git commit -m "Add knapsack problem PDF"
git log
```

### Stage 3

- 상태를 확인
- 소스코드(commit_3)을 commit 할 목록에 준비
- 다시한번 상태확인
- 준비된 파일을 커밋
- 오류가 난다면 대처(설정하기 -> 그리고 다시 커밋)

```bash
git status
git add packing_knapsack.c
git status
git commit -sm "packing knapsack : Basic code solving this question"
git config user.email '본인메일@gmail.com'
git config user.name '본인이름'
```

### Stage 4

- 소스파일(commit_4) packing_knapsack.c으로 수정후에 diff상태를 확인
- 소스파일(commit_4) commit할 목록에 준비
- 다시한번 상태를 확인해서 1)과 달라졌음
- 준비된 파일을 commit하는데 이번에 -m쓰지 않음(vi 같은 편집하고 :wq로 저장 종료) Commit message는 "packing knapsack : Change Basic Code"
- 방금한 commit을 확인

```bash
git diff
git add packing_knapsack.c
git status
git commit -s
git show
```

### Stage 5

- 상태를 확인하고 현재 브랜치명 master를 확인
- 지금까지한 commit들을 확인
- GITHUB원격저장소 URL을 등록(<http://github.com>켜고 repository 생성)

```bash
git status
git log
```

- GITHUB 원격저장소 등록
- GITHUB 원격저장소(origin)에 PUSH
- GITHUB 열고 확인

```bash
git remote add origin <아까복사한URL>
git push origin master
```

### Stage 6

- 커밋메시지(commit_4)로 수정(vi 수정후 :wq)
- 바로 push(충돌오류발생)
- 강제로 push해서 수정(--force 또는 -f 옵션)
- 다시 GITHUB로 가서 제대로 변경되었는지 확인

```bash
git commit --amend
git push origin master
git push origin master -f
```

### Stage 7(소스변경후 add -> commit -> push)

- 소스파일(commit_5) packing_knapsack.c으로 수정후에 diff상태 확인
- 소스파일(commit_5)을 commit 목록 준비
- 준비된 파일을 commit한다.
- GITHUB 원격저장소(origin)에다가 PUSH

```bash
git diff
git add packing_knapsack.c
git commit -sm "packing knapsack: Rename packing_knapsack to pack_knapsack"
git push origin master
```

### Stage 8(소스변경후 add -> commit -> push)

- 소스파일(commit_6) packing_knapsack.c으로 수정후에 diff상태 확인
- 소스파일(commit_6)을 commit 목록 준비
- 준비된 파일을 commit한다.
- GITHUB 원격저장소(origin)에다가 PUSH

```bash
git diff
git add packing_knapsack.c
git commit -sm "packing knapsack: Input & Output"
git push origin master
```

### Stage 9(파일추가후 add -> commit -> push)

- TEST파일(commit_7) test.sh을 추가후에 상태확인
- TEST파일(commit_7)을 commit 목록 준비
- 준비된 파일을 commit한다.
- GITHUB 원격저장소(origin)에다가 PUSH

```bash
git status
git add test.sh
git commit -sm "packing knapsack: Add test script"
git push origin master
```

### Stage 9(파일추가후 add -> commit -> push)

- TEST파일(commit_8) generator_test_script.py을 추가후에 상태확인
- TEST파일(commit_8)을 commit 목록 준비
- 준비된 파일을 commit한다.
- GITHUB 원격저장소(origin)에다가 PUSH

```bash
git status
git add generator_test_script.py
git commit -sm "packing knapsack: Add test script generator"
git push origin master
```

### Stage 10(마지막수정후 add -> commit -> push)

- 소스파일(commit_9) packing_knapsack.c을 수정후에 diff상태확인
- 소스파일(commit_9)을 commit 목록 준비
- 준비된 파일을 commit한다.
- GITHUB 원격저장소(origin)에다가 PUSH

```bash
git status
git add packing_knapsack.c
git commit -sm "packing knapsack: Implement code to solve this question"
git push origin master
```

## Pull-Request

### Stage 11

- <https://github.com/taeung/git-training>
다른사이트에서 fork해옴
- clone으로 fork한 repo받아오기(<https://github.com/anabasis/git-training-1.git>)
- pull-request 작업할 Branch 따로 생성
- pull_request_test 폴더로 이동
- 프로젝트 폴더를 만들기
- 프로젝트 폴더에 소스 넣기
- 추가된 폴더 통째로 add
- 준비된 파일들 commit
- 내가 fork한 repo와 knapsack 브랜치로 PUSH(주의 master 아님)

```bash
git clone https://github.com/anabasis/git-training-1.git <아까 fork한 repo에서 복사항 URL>
cd git-training-1
git checkout -b knapsack
cd pull_request_test
mkdir junseongcho
#pwd
#git-training-1/pull_reqeust_test/junseongcho
git add packing_knapsack
git commit -sm "test pull request"
git push origin knapsack
```

FETCH, REBASE
REWIND
