# 자바 필터 스트림

> 자바에는 다른 스트림과 연결되어 여러 가지 편리한 기능을 제공해주는 스트림이 있다.  
> 이를 **필터 스트림** 혹은 **보조 스트림** 이라고 한다.

|구분|스트림|
|:---:|---|
|문자 변환|InputStreamReader, OutputStreamWriter|
|성능 향상|BufferedInputStream, BufferedReader, BufferedOutputStream, BufferedWriter|
|기본 타입 입출력|DataInputStream, DataOutputStream|
|프린터|PrintStream, PrintWriter|
|객체 입출력|ObjectInputStream, ObjectOutputStream|

### InputStreamReader
- 바이트 입력 스트림 -> 문자 입력 스트림 변경
```java
// 콘솔에서 입력
InputStream is = System.in;
Reader reader = new InputStreamReader(is);

// 파일 입력
FileInputStream fis = new FileInputStream("/test.txt");
Reader reader = new InputStreamReader(fis);
```

### OutputStreamWriter
- 바이트 출력 스트림 -> 문자 출력 스트림 변경
```java
// 문자를 파일로 출력
FileOutputStream fos = new FileOutputStream("/test.txt");
Writer writer = new OutputStreamWriter(fos);

String data = "test";
writer.write(data);

writer.flush();
writer.close();
```
