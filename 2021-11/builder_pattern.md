# 빌더패턴

GoF(Gang of Four) 디자인 패턴 중 생성 패턴 중 하나이다.

> 필드 중 필수인 필드가 있다면 롬복의 build 메소드를 Override해서 매개변수로 필수 필드를 입력 받는다.

# java에서의 Builder 패턴

1. 일반적인 builder 패턴
```java
import lombok.Builder;

public class Main {
  public static void main(String[] args) {
    Entity entity = Entity.builder()
      .field1("field1")
      .field2("field2")
      .field3("field3")
      .field4("field4")
      .build();
  }
  
  @Builder
  static class Entity {
    private String field1;
    private String field2;
    private String field3;
    private String field4;
  }
}
```

2. 필수 필드가 있을 경우
```java
import lombok.Builder;

public class Main {
  public static void main(String[] args) {
    String field1 = "field1";
    String field2 = "field2";
    
    Entity entity = Entity.builder(field1, field2)
      .build();
  }
  
  @Builder
  static class Entity {
    // field1, field2가 필수일 경우
    private String field1;
    private String field2;
    private String field3;
    private String field4;
    
    public static EntityBuilder builder(String field1, String field2) {
      return new EntityBuilder()
        .field1(field1)
        .field2(field2);
    }
  }
}
```

