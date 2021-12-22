# SerialVersionUID

> 같은 클래스임을 알려주는 식별자 역할을 하는 정적 필드.

Serializable 인터페이스를 구현하면 자동으로 serialVersionUID 정적 필드가 추가된다.  
하지만 serialVersionUID 필드에는 문제가 있다.

---

### 문제
클래스를 재컴파일하게 되면 serialVersionUID의 값이 달라진다.

### 해결방법
클래스에 serialVersionUID 필드를 명시적으로 선언해서 해결한다.

```java
public class Test implements Serializable {
  
  static final long serialVersionUID = 정수값;
  
  // ...
}
```
<br>

serialVersionUID 필드가 명시적으로 선언되어 있을 경우  
컴파일 시에 자동으로 추가되지 않기 때문에 재컴파일해도 serialVersionUID 값이 바뀌지 않게 된다.  
추가로 자바는 ```<JDK 설치 경로>/bin``` 폴더에 serialVersionUID를 자동으로 생성시켜주는 ```serialver.exe```명령어를 제공하고 있다.
