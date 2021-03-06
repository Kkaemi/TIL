# 자바스크립트 실행 컨텍스트

> ECMAScript 스펙에 따르면 실행 컨텍스트를 **실행 가능한 코드를 형상화하고 구분하는 추상적인 개념이라고 정의한다.**  
> 좀 더 쉽게 말하자면 실행 컨텍스트는 **실행 가능한 코드가 실행되기 위해 필요한 환경 이라고 말할 수 있겠다.**

<br>

실행 가능한 코드는 아래와 같다.

* 전역 코드 : 전역 영역에 존재하는 코드
* 함수 코드 : 함수 내에 존재하는 코드
* Eval 코드 : eval 함수로 실행되는 코드

> eval 함수는 매개변수로 넣은 문자열을 실행하는 함수이다.  
> ex) `eval('alert("Hello")')`

<br>

---

<br>

### 1. 실행 컨텍스트

|key|type|value|
|:---:|:---:|:---|
|Variable Object|Object|변수, 함수 선언, 함수의 매개변수와 인수 정보<br><br>* 전역 컨텍스트의 경우 Global Object를 가리킨다.<br>* 함수 컨텍스트의 경우 Activation Object를 가리킨다.|
|Scope Chain|Array|중첩된 상위 컨텍스트의 VO들을 리스트 형태로 참조한다.|
|this Value|Object|함수 호출 패턴에 의해 결정된 this value|

> Javascript의 this는 Java의 this와 달리 **함수를 호출할 때 어떻게 호출되었는지에 따라 동적으로 결정된다.**

<br>

---

<br>

### 2. 실행 컨텍스트의 생성 과정

#### 1. 전역 객체 생성
컨트롤이 실행 컨텍스트에 진입하기 이전에 유일한 전역 객체(Global Object)가 생성된다.  
초기 상태의 전역 객체에는 빌트인 객체(Math, String, Array 등)와 BOM, DOM이 설정되어 있다.  
> 전역 객체(Global Object)는 모든 객체의 유일한 최상위 객체를 의미한다.  
> Browser -> window  
> Node.js -> global

전역 객체가 생성된 이후, 전역 코드로 컨트롤이 진입하면 전역 실행 컨텍스트가 생성되고 실행 컨텍스트 스택에 쌓인다.

#### 2. 스코프 체인의 생성과 초기화
#### 3. Variable Instantiation(변수 객체화) 실행
변수의 객체화는 VO에 프로퍼티와 값을 추가하는 것을 의미한다.
변수의 객체화는 반드시 다음과 같은 순서로 프로퍼티와 값을 set한다.
> 1. Function Code인 경우 매개변수(parameter)가 프로퍼티, 인수(argument)가 값으로 설정된다.
> 2. 대상 코드 내의 함수 선언을 대상으로 함수명이 프로퍼티, 함수 객체가 값으로 설정된다. **(함수 호이스팅)**
> 3. 대상 코드 내의 변수 선언을 대상으로 변수명이 프로퍼티, undefined가 값으로 설정된다. **(변수 호이스팅)**

함수 객체는 [[Scopes]]라는 프로퍼티를 가지게 되는데, [[Scopes]]는 실행 컨텍스트 Scope Chain의 VO리스트를 값을 가지고 있다.  
그렇기 때문에 외부 함수의 실행 컨텍스트가 소멸하여도 외부 함수의 실행 환경(AO)은 소멸하지 않고 참조할 수 있다. 이것이 **클로저**이다.

변수 객체 할당은 세분화 시키면 다음과 같은 순서를 가진다.
1. 선언 단계
2. 초기화 단계
3. 할당 단계
`var`키워드로 변수를 할당했을 경우 선언 단계와 초기화 단계가 한번에 이루어지게 되는데 이를 **변수 호이스팅**이라 한다.

#### 4. this value 결정

<br>

출처 : [모던 자바스크립트 Deep Dive](https://poiemaweb.com/js-execution-context)
