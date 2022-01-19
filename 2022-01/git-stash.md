# git stash 명령어

아직 마무리하지 않은 작업을 스택에 잠시 보관할 때 사용

`git stash`
- 작업을 스택에 저장

<br>

`git stash list`
- 여러번 stash한 경우 stash 목록 확인

<br>

`git stash apply [stash 이름]`
- stash 이름 옵션을 추가할 경우 해당 이름의 stash 불러오기
- 옵션이 없을 경우 가장 최근 stash 불러오기

<br>

`git stash drop [stash 이름]`
- stash 제거
- 옵션을 추가할 경우 해당 이름의 stash 제거

<br>

`git stash pop`
- apply 후 drop
- 스택의 pop과 비슷하다고 생각하면 될 듯

<br>

```shell
// 가장 최근의 stash를 사용하여 패치를 만들고 그것을 거꾸로 적용한다.
git stash show -p | git apply -R
// stash 이름(ex. stash@{2})에 해당하는 stash를 이용하여 거꾸로 적용한다.
git stash show -p [stash 이름] | git apply -R
```
- 실수로 잘못 stash 적용한 것을 되돌리고 싶으면 위의 명령어를 이용한다.
