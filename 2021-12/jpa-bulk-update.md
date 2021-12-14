# 스프링 데이터 JPA를 사용한 벌크성 수정

- JPA를 사용한 수정 쿼리
```java
@Modifying
@Query(
  "update Product p " +
  "set p.price = p.price * 1.1 " + 
  "where p.stockAmount < :stockAmount"
)
int bulkPriceUp(@Param("stockAmount") String stockAmount);
```

<br>

- ☠ **벌크 연산의 주의점**
> 벌크 연산은 영속성 컨텍스트를 무시하고 DB에 직접 쿼리한다.

따라서 엔티티 조회 후 벌크 연산을 하게되면 영속성 컨텍스트에 존재하는 엔티티와 DB의 값이 ```일치하지 않는 경우```가 생긴다.

<br>

해결방법은 3가지가 있다.
1. EntityManger의 refresh() 메소드 사용
2. 벌크 연산 먼저 실행
3. 벌크 연산 수행 후 영속성 컨텍스트 초기화

가능하면 벌크 연산 먼저 수행하는 것이 좋다.

<br>

※개인적인 의견※
> 하지만 조회가 필요하지 않다면 생기지 않는 문제들이므로  
> 한 트랜잭션에서 벌크 연산만 하게 된다면 고려하지 않아도 되는 문제인 것 같다.
