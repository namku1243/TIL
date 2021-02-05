# Undoing

## 1. add  취소

```bash
$ touch a.txt
$ git add a.txt
$ git status
On branch master
Changes to be committed:
	# unstage하고 싶으면.. 사용해
  (use "git restore --staged <file>..." to unstage)
        new file:   a.txt
```

* 결과

  ```bash
  $ git restore --staged a.txt
  ```

  ```bash
  $ git status
  On branch master
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
          a.txt
  
  nothing added to commit but untracked files present (use "git add" to track)
  
  ```

## 2. working directory 

> **주의** working directory의 내용을 지우면, 되살릴 수는 없다.
>
> 모든 커밋된 내용으로는 돌아갈 수 있다.

```bash
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  # WD에 있는 변경사항들을
  # 버리기 위해서는 사용!
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

```bash
$ git restore a.txt
```

```bash
$ git status
On branch master
nothing to commit, working tree clean
```

## 3. commit 메시지 변경

> **주의** : 공개된 저장소에 PUSH한 경우 변경하지말 것.

```bash
$ git commit -m 'Add d.txt'
# aebed17
[master aebed17] Add d.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 c.txt

$ git commit --amend
# 편집기 창에서 수정후 저장!
# 8120127
[master 8120127] Add c.txt
 Date: Fri Feb 5 17:20:30 2021 +0900
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 c.txt
```

* commit 시 파일이 누락된 경우

  ```bash
  $ touch 1-1.txt
  $ touch 1-2.txt
  $ git add 1-1.txt
  $ git status
  On branch master
  Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
          new file:   1-1.txt
  
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
          1-2.txt
  $ git commit -m 'Add 1'
  ```

  ```bash
  $ git add 1-2.txt # 빠진 파일을 staging area로 이동시키고
  $ git commit --amend
  [master d4db4d9] Add 1
   Date: Fri Feb 5 17:29:40 2021 +0900
   2 files changed, 0 insertions(+), 0 deletions(-)
   create mode 100644 1-1.txt
   create mode 100644 1-2.txt
  
  $ git status
  On branch master
  nothing to commit, working tree clean
  ```

  

## 4. reset vs revert

### reset

* `--hard` : 조심!! 모든 변경사항과 이력을 삭제!
* `--mixed` : 모든 변경사항을 WD까지도 보관
* `--soft` : 모든 변경사항을  Staging area까지, WD까지 보관

```bash
$ git log --oneline
d4db4d9 (HEAD -> master) Add 1
8120127 Add c.txt
f054151 Add a.txt
47bd59b Root

$ git reset --hard 8120127
HEAD is now at 8120127 Add c.txt

$ git log --oneline
8120127 (HEAD -> master) Add c.txt
f054151 Add a.txt
47bd59b Root
```

```bash
$ git revert 8120127
Removing c.txt
[master b04fcf5] Revert "Add c.txt"
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 c.txt

$ git log --oneline
b04fcf5 (HEAD -> master) Revert "Add c.txt"
8120127 Add c.txt
f054151 Add a.txt
47bd59b Root
```













