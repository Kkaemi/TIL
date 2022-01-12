# 맥 런치패드에서 앱 지우기

맥을 사용할 경우 앱을 삭제했는데도 런치패드에 계속 남아있는 경우가 생겼다.

- select문으로 앱 이름 찾기
```shell
sqlite3 $(find /private/var/folders \( -name com.apple.dock.launchpad -a -user $USER \) 2> /dev/null)/db/db "select * FROM apps;" && killall Dock
```

- delete문으로 앱 삭제하기
```shell
sqlite3 $(find /private/var/folders \( -name com.apple.dock.launchpad -a -user $USER \) 2> /dev/null)/db/db "delete from apps where title='<해당 앱 이름>';" && killall Dock
```
