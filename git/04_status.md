# git 상태

```bash
$ git status
On branch master
# 커밋될 변경사항
# staging area 
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
  		# 수정됨
        modified:   123.txt
        # 이름변경
        renamed:    b.hwp -> c.hwp

# staged(커밋을 위해서)되지 않은 변경사항
# working directory
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
  		# 삭제됨
        deleted:    a.pptx

# 트래킹이 되지 않는 파일
# 일반적으로 새로 만든 파일.. 
# Working directory
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        image.bmp


```

