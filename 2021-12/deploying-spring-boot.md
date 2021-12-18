# 스프링 부트 리눅스 서비스로 deploying

스프링 부트는 linux에 jar 파일을 배포할 때 따로 쉘 스크립트를 작성할 필요도 없다는 것을 알았다...  
매우 대단...

1. 스프링 부트 프로젝트에 다음과 같은 코드를 붙여 넣는다.

- pom.xml
```xml
<plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
    <configuration>
        <executable>true</executable>
    </configuration>
</plugin>
```

- build.gradle
```gradle
bootJar {
  launchScript()
}
```

<br>

2. linux 환경에 jar 파일 심볼릭 링크를 생성한다.
```shell
sudo ln -s <jar file path> /etc/init.d/<jar file name>
```

<br>

이렇게만 하면 모든 준비가 끝난다.

서비스 명령으로 스프링 부트를 실행시킬 수 있다.
```shell
sudo service <jar file name> start
```

---

추가로 실행할 때 추가적으로 전달해야하는 명령어가 있을 경우  
ex) --spring.profiles.active=prod

<br>

vim을 사용해서 jar파일 이름과 똑같은 `.conf`파일을 만든다.
```shell
sudo vim <jar file path>/<jar file name>.conf
```

그리고 해당 내용을 넣어준다.
`RUN_ARGS=--spring.profiles.active=prod`

<br>

이렇게되면 서비스가 실행 될 때 `RUN_ARGS`에 입력한 값이 추가되어 실행되게 된다.  

이 외에도 다양한 옵션들이 존재하며 스프링 부트 공식문서에 설명되어 있다.

<br>

[스프링 부트 공식 문서](https://docs.spring.io/spring-boot/docs/current/reference/html/deployment.html#deployment.installing.nix-services.script-customization.when-written)
