# 객체 입출력 보조 스트림

> 자바는 메모리에 생성된 객체를 파일 또는 네트워크로 출력할 수가 있다.  
> 객체는 문자가 아니기 때문에 바이트 기반 스트림으로 출력해야 한다.
> - **직렬화(serialization)** : 자바 객체 -> 바이트
> - **역직렬화(deserialization)** : 바이트 -> 자바 객체

### ObjectInputStream
```java
FileInputStream fis = new FileInputStream("/test.dat");
ObjectInputStream ois = new ObjectInputStream(fis);

객체타입 변수 = (객체타입) ois.readObject(); // 형변환

ois.close();
fis.close();
```
[ObjectInputStream에 대한 설명 (java 11)](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/ObjectInputStream.html)  

---

### ObjectOutputStream
```java
FileOutputStream fos = new FileOutputStream("/test.dat");
ObjectOutputStream oos = new ObjectOutputStream(fos);

oos.writeObject(new Integer(10));

oos.flush();
oos.close();
fos.close();
```
[ObjectOutputStream에 대한 설명 (java 11)](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/ObjectOutputStream.html)
