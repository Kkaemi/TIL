## mysqldump를 사용하여 Amazon RDS for MySQL DB 인스턴스로 데이터를 가져올 때

AWS RDS MySQL에 덤프 파일을 import 하게 될 경우  
1227 에러를 만나가 된다.

<br>

```SQL
Error: 1227 SQLSTATE: 42000 (ER_SPECIFIC_ACCESS_DENIED_ERROR) Access denied; you need (at least one of) the %s privilege(s) for this operation.
```

Access Deny 어쩌구라고 하는데...

[AWS에서는 친절하게 이와 관련된 문서가 이미 만들어져 번역까지 되어있다.](https://aws.amazon.com/ko/premiumsupport/knowledge-center/definer-error-mysqldump/)

<br>

### 요약
1. 파라미터 그룹에 log_bin 어쩌구로 시작하는 값을 true로 바꿔준다  
**본인은 이렇게 해도 문제가 해결 안됐음**

2. .sql 파일 안에 `SET`으로 시작하는 SQL을 주석처리 해준다.
