# git 편집기를 vs code로 바꾸기

* git bash에서 기본 편집기는 `vim` 

  * 초보자가 사용하기 불편

* 편집기 설정을 아래와 같이 한다면, visual studio code로 사용할 수 있다.

  ```bash
  $ git config --global core.editor "code --wait"
  ```

* 설정된 옵션을 보기 위해서는 아래의 명령어를 활용한다.

  ```bash
  $ git config --global -l
  user.name=edutak
  user.email=edutak.ssafy@gmail.com
  core.editor=code --wait # 여기 설정!
  ```

  