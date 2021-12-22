# 어노테이션

> 어노테이션(Annotation)은 메타데이터(metadata)라고 볼 수 있다.
> - 메타데이터란 어플리케이션이 처리해야할 데이터가 아니라, 컴파일 과정과 실행 과정에서 코드를 어떻게 컴파일하고 처리할 것인지를 알려주는 정보이다.

<br>

어노테이션은 다음과 같은 용도로 사용된다.
> 1. 컴파일러에게 코드 문법 에러를 체크하도록 정보를 제공  => ex) ```@Override```
> 2. 소프트웨어 개발 툴이 빌드나 배치 시 코드를 자동으로 생성할 수 있도록 정보를 제공  
> 3. 실행 시(런타임 시) 특정 기능을 실행하도록 정보를 제공  
> 4. 빌드 시 자동으로 XML 설정 파일 생성
> 5. 배포를 위해 JAR 압축 파일 생성
> 6. 실행 시 클래스의 역할 정의

---

### 사용자 정의 어노테이션 만들기

```java
@Target({ElementType.Type, ElementType.FIELD, ElementType.METHOD})
@Retention(RetentionPolicy.RUNTIME)
public @interface CustomAnnotation {
  String value(); default "-"; // 기본 엘리먼트
  int el(); default 5; // 엘리먼트 선언
}
```

이렇게 정의한 어노테이션은 다음과 같이 사용할 수 있다.

```java
@CustomAnnotation
public class Test {
  
  @CustomAnnotation("test")
  private int field;
  
  // @CustomAnnotation("test") => @Target 어노테이션에 CONSTRUCTOR가 없어서 적용 안됨
  public Test() {
  }
  
  // el 엘리먼트에 값을 줄 경우
  @CustomAnnotation(value = "test", el = 2)
  public void method() {
  }
}
```

<br>

- 어노테이션 적용 대상

|ElementType 열거 상수|적용 대상|
|:---|:---|
|TYPE|클래스, 인터페이스, 열거 타입|
|ANNOTATION_TYPE|어노테이션|
|FIELD|필드|
|CONSTRUCTOR|생성자|
|METHOD|메소드|
|LOCAL_VARIABLE|로컬 변수|
|PACKAGE|패키지|

<br>

- 어노테이션 유지 정책

|RetentionPolicy 열거 상수|설명|
|:---|:---|
|SOURCE|소스상에서만 어노테이션 정보를 유지한다. 소스 코드를 분석할 때만 의미가 있으며, 바이트 코드 파일에는 정보가 남지 않는다.|
|CLASS|바이트 코드 파일까지 어노테이션 정보를 유지한다. 하지만 리플렉션을 이용해서 어노테이션 정보를 얻을 수 없다.|
|RUNTIME|바이트 코드 파일까지 어노테이션 정보를 유지하면서 리플렉션을 이용해서 런타임 시에 어노테이션 정보를 얻을 수 있다.|

> - **리플렉션(Reflection)이란?**  
> 
> 런타임 시에 클래스의 메타데이터를 얻는 기능을 말한다.  
> ex) 클래스의 필드, 생성자, 메소드, 적용된 어노테이션에 대한 정보를 알아내는 것.
