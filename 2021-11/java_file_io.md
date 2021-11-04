# 자바에서 파일 입출력

자바에서 데이터는 **스트림(stream)** 을 통해 입출력됨

||바이트 기반 스트림|문자 기반 스트림|
|---|---|---|
|최상위 클래스|InputStream<br/>OutputStream|Reader<br/>Writer|
|하위 클래스 접두사<br/>ex)FileInputStream, FileReader|File<br/>Object<br/>Data<br/>Buffered|File<br/>InputStream<br/>OutputStream<br/>Buffered|
|출력 하위 클래스|PrintStream|PrintWriter|


---
## InputStream 예

> InputStream의 read() 메소드의 반환값은 int다.  
> java에서 int는 4바이트지만 byte는 1바이트이므로  
> int 자료형의 끝 1바이트에만 데이터가 들어가있다.
#### 한 바이트씩 읽을 경우
```java
InputStream is = new FileInputStream("/");
int readByte;

while((readByte = is.read()) != -1) {
  // do something
}

is.close()
```

#### 많은 양의 바이트를 읽을 경우
```java
InputStream is = new FileInputStream("/");
int readByteNo;
byte[] readBytes = new byte[100]; // 한번에 읽어들일 바이트 수 정의

while((readByteNo = is.read(readBytes)) != -1) {
  // do something
}

is.close();
```
---
## OutputStream 예
```java
OutputStream os = new FileOutputStream("/test.txt");
byte[] data = "ABC".getBytes();

os.write(data);

os.flush(); // 버퍼에 남아있는 데이터 모두 출력
os.close(); // OutputStream에 할당된 자원 해제
```
---
## Reader
> Reader의 read() 메소드의 반환값은 int다.  
> java에서 int는 4바이트지만 char는 2바이트이므로  
> int 자료형의 끝 2바이트에만 데이터가 들어가있다.  
> >2개의 문자(4바이트)가 들어와도 int 2개

#### 한 문자씩 읽을 경우
```java
Reader reader = new FileReader("/test.txt");
int readData;

while((readData = reader.read()) != -1) {
  // do something
}

reader.close();
```

#### 여러 문자를 읽을 경우
```java
Reader reader = new FileReader("/test.txt");
int readCharNo;
char[] cbuf = new char[2]; // 한번에 읽을 문자 수 정의

while((readCharNo = reader.read(cbuf)) != -1) {
  // do something
}

reader.close();
```
---
## Writer
```java
Writer wirter = new FileWriter("/test.txt");
char[] data = "TEST".toCharArray();

writer.write(data);

writer.flush(); // 버퍼에 남아있는 데이터 모두 출력
writer.close(); // Writer에 할당된 자원 해제
```
