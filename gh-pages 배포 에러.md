# gh-pages 배포 에러

```
 ! [rejected]        47df240b45d94ea67dd0ef377667e2870e8eba8c -> gh-pages (non-fast-forward)
error: failed to push some refs to 'https://github.com/parkoon/resume-kit.git'
hint: Updates were rejected because a pushed branch tip is behind its remote
hint: counterpart. Check out this branch and integrate the remote changes
hint: (e.g. 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

리모트에 있는 저장소와 로컬에 있는 저장소의 싱크가 맞지 않아 발생하는 이슈라고 한다.

아래 명령어를 실행해준다

```
$ git push origin --delete gh-pages
$ git subtree push --prefix out origin gh-pages
```
