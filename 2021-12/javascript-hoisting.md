# 자바스크립트 호이스팅

> **호이스팅이란 자바스크립트에서 함수나 변수의 선언이 맨위로 올라가는 것을 말한다.**

<br>

지금은 사용하지 않는 `var` 키워드를 사용해서 변수를 선언하게될 경우 호이스팅이 일어나게 된다.

```javascript
function sayHi() {
  phrase = "Hello";

  alert(phrase);

  var phrase;
}

sayHi(); // Hello
```

<br>

함수의 선언도 호이스팅된다.

```javascript
sayHi(); // Hello

function sayHi() {
  phrase = "Hello";

  alert(phrase);

  var phrase;
}
```
