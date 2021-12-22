### Serializable
> 자바는 Serializable 인터페이스를 구현한 클래스만 직렬화 할 수 있도록 제한하고 있다.

<br>

객체를 직렬화 하면 필드만 직렬화된다.  
**생성자, 메소드는 직렬화 되지 않음.**  
**예외)** static, transient 키워드가 붙은 필드

```java
public class Test implements Serializable {

  // 직렬화 가능
  public int field1;
  protected int field2;
  int field3;
  private int field4;
  
  // static, transient 키워드가 붙은 필드는 직렬화에서 제외
  public static int field5;
  transient int field6;
}
```
