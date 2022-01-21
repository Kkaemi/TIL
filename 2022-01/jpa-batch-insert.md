# JPA Batch Insert

<br>

JPA Repository의 saveAll() 메소드로 컬렉션을 저장할 경우 데이터 하나당 insert문이 생성된다.
```sql
insert into table_a(column1, column2) values(?, ?)
insert into table_a(column1, column2) values(?, ?)
insert into table_a(column1, column2) values(?, ?)
```

<br>

JPA에서 Batch Insert를 하기위해서 application.properties(yml) 파일을 수정해줘야 한다.
```properties
// rewriteBatchedStatements 설정
spring.datasource.hikari.data-source-properties.rewriteBatchedStatements=true

// batch_size 설정
spring.jpa.properties.hibernate.jdbc.batch_size=1000
```

한가지 주의 사항이 있는데 JPA Batch Insert는 아이디 생성 전략 중 IDENTITY 전략으로 PK를 생성할 경우 Batch Insert가 적용되지 않는다.
```java
@GeneratedValue(strategy = GenerationType.IDENTITY)
```

<br>

또한 intelliJ 터미널에서 보면 여전히 insert 쿼리가 데이터 개수만큼 만들어지는 것처럼 보이는데
mysql에서 요청된 쿼리 로그를 직접 확인하면 Batch Insert가 된 것을 확인 할 수 있다.
```sql
show variables like 'general_log%'; # general_log_file의 경로 확인
```
