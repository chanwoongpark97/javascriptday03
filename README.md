# JS 스터디 3일차

🤔 : 이번 장에서 가장 중요한 키워드입니다. 데이터 타입 장을 읽고 아래의 단어들을 조금 더 이해하는게 오늘의 목표입니다. 천천히 읽어보시고, 각 조원분들과 적당하게 나눠서 아래의 키워드를 직접 설명해주세요.

> 절대 보기 좋게 정리하려고 하지 마시고, 
정해진 시간에 최대한 많은 내용을 기입하는 방식으로 최대한 많이 작성해주세요!
(Gitbook에서 복사해온 내용을 제외하고, 작성 할 때 마다 본인의 이름을 꼭 적어주세요!)
> 

## 01. ****데이터타입, 실행 컨텍스트**** 생각해볼 것들

---

<aside>
📌 🤔 : 아래의 내용들은 이번 장에서 얻을 수 있는 지식들입니다. 이러한 것들을 배운다고 생각하고 데이터 타입 챕터를 읽어가주세요, 다 읽은 이후에 아래의 질문에 대한 답을 답할 수 있으면 완벽합니다.

</aside>

**데이터 타입**

**1.다른 언어에서는 어떻게 데이터 타입을 정의 할까요?** 

**파이썬 :**

변수의 자료값이 문자열, 숫자인지에 따라 저장 방식이나 계산 방식이 다름. 이런 값의 종류를 자료형, 타입이라고 함

불변형 : none, bool, int, float, complex, str, tuple, / 

가변형 : list, dict ,/function 으로 분류할 수 있음

**자바스크립트 :**

기본 자료형(primitive type): undefined, null, bool, string, number, (Symbol)

참조 자료형(reference type) : Object(array, function,. regexp), (map, set, weakmap, weakset)

**자바** : 

1. 기본형(primitive type) 변수
2. 참조형(reference type) 변수

기본형(primitive type) 변수는 실제 연산에 사용되는 변수입니다.

자바에서는 다음과 같이 8가지 종류의 기본형 변수를 제공하고 있습니다.

- 정수형 : byte, short, int, long
- 실수형 : float, double
- 문자형 : char
- 논리형 : boolean

**2.다른 언어들처럼 데이터 타입을 다룬다면 장단점은 무엇이 있을까요?**

다른 언어들처럼 데이터 타입을 다룬다면 장단점은 무엇이 있을까요?

**C언어**의 경우 변수의 타입을 작성자가 쉽게 구분 할 수 있다.

**파이썬**은 JS에 비하여 숫자형이 좀 더 세분화 되어있음. JS는 number만 가지지만 파이썬은 정수형(int) 실수형(float)로 구분﻿한다.

| 구분 | 파이썬 | 자바스크립트 |
| --- | --- | --- |
| 문자열 자료형 | str | string |
| 리스트 자료형 | list | array |
| 딕셔너리 자료형 | dict | object |
| 불 자료형 | bool | boolean |
| 튜플 자료형 | tuple | Tuple of Typescript |

**3.기본형 데이터와 참조형 데이터를 굳이 왜 구분해서 다룰까요? 혹시 하나의 방식으로 다 다룰수는 없을까요?**

**시스템에서 데이터 관리의 효율성과 정확성을 향상시킬 수 있다.**

값을 변환시킬때에 참조형에 들어가는 값들에 대하여 주소값이 아닌 값 전체를 복사하여 사용하게 되면 용량이 어마무지하게 커지기 때문

**기본형 데이터**는 값을 그대로 할당한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/28c4ae2f-0845-46b5-8650-6140a114550c/Untitled.png)

메모리상에 고정된 크기로 저장되며 원시 데이터 값 자체를 보관하므로

불변적이다. 같은 데이터는 하나의 메모리를 사용한다.(재사용)

**참조형데이터(Reference Type)**

참조 타입은 변수에 할당할때 값이 아닌 데이터의 주소를 저장

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f6c9b9fc-3f7b-4929-b50c-4a9dd8bb908b/Untitled.png)

**4.왜 불변 객체를 이용해야 할까요? 어떤 실수가 있을 수 있을까요?**

const으로 정의된 객체를 불변객체라고 하는데, 사용 목적으로는 원본 데이터의 변경 및 훼손 방지이다. 

객체의 불변성이 중요한 이유는 전역 변수를 지양하는 이유와 비슷하다.

복잡한 코드에 전역 변수가 많을 경우 변수의 값이 변경되었을 때 그 변수를 사용하는 곳에서

의도치 않게 값이 변경될 수도 있고 해당 변수가 어디있는지 추적하기도 어려워진다.

객체 또한 불변성을 지키지 않고 참조 값을 여러 객체가 공유할 경우 어떤 객체에서

값이 변경 되었을 때 의도치 않게 다른 객체도 값이 변경되며 변경된 곳을 추적하기 어려워진다.

그래서 불변객체는 상태를 바꿀수 없기 때문에 동시에 여러 곳에서 사용하더라도 해당 객체를 사용하는 쪽에서는 안전하게 사용할 수 있기 때문이다.

또 불변 객체에 대해 작업하는 코드는 불변 객체를 사용하는 곳에 영향을 미치는 것을 고려하지 않아도 되고 불변 객체를 복사할 때 객체 전체가 아닌 참조만 복사해  메모리도 아끼고 성능도 향상시킬수 있는 이점이 있다.

**5.왜 자바스크립트에는 undefined와 null이 있을까요?**

undefined : 선언 o, 할당 x이 직접적으로 이뤄지지 않은 변수/인수에 자동으로 할당된다. 자료형이 없는 상태(undefined)

null : 선언 o, 할당 but 빈값을 할당한 상태. 자료형(object)

**실행 컨텍스트**

[자바스크립트 실행 컨텍스트 | 개발자 황준일 (junilhwang.github.io)](https://junilhwang.github.io/TIL/Javascript/Domain/Execution-Context/#_1-%E1%84%80%E1%85%A2%E1%84%82%E1%85%A7%E1%86%B7)

1.실행 컨텍스트는 무엇일까요? 

자바스크립트 코드가 실행되고 연산되는 범위를 나타내는 추상적인 개념.

우리가 코드를 작성하고 실행한다면 실행 컨텍스트(Execution Context) 내부에서 실행되고 있는 것입니다. 즉 **코드들이 실행되기 위한 환경**이자 하나의 박스이자 컨테이너라 볼 수 있음.

2.실행 컨텍스트 객체가 활성화되는 시점에 수집되는 정보는 무엇일까요? 각각 왜 수집할까요?

****A. 변수: 전역 변수, 지역 변수, 매개 변수, 객체의 프로펕****

****B. 함수 선언****

****C. 변수의 유효범위(SCOPE)****

****D. this****

실행 컨텍스트는 다음과 같은 것들을 이용하면 `call stack`에 쌓이게 된다.

- `전역공간`은 자동으로 컨텍스트로 구성된다.
- `함수`를 실행한다.
- `eval()`함수를 실행한다.
- `block`을 만든다 **(ES6+)**

3.호이스팅은 무엇일까요?

코드가 실행하기 전 변수선언/함수선언이 해당 스코프의(선언한 변수의 접근 범위) 최상단으로 끌어 올려진 것 같은 현상을 말한다.

변수/함수의 선언된 구문이 있는 것만 호이스팅의 대상이다. 

var로 선언된 경우에만 적용됨??

4.왜 귀찮게 호이스팅같은 개념이 있을까요?

JS는 순차별 개념이 아니라서 가능한 개념. 

C언어는 실행시키고 나서 선언되지 않은 변수,함수가 발생하면 오류가 생기지만 

java는 객체지향 이기에 실행전 전체변수와 함수들을 확인하고 선언되지 않는 값들을 레퍼런스 오류로 찾아낸다.

5.함수 선언문과 함수 표현식은 어떻게 다를까요?

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/436c131a-79b7-488b-b4f8-d5ce8095c0f4/Untitled.png)

함수 표현식은 정의하자마자 실행됨

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/533bee49-7c7a-4dc6-817b-f813ac41b1e7/Untitled.png)

6.스코프는 무엇일까요?

- 참조 대상 식별자(Identifier : 함수, 변수의 이름과 같이 어떤 대상을 다른 대상과 구분하여 식별할 수 있는 유일명)을 찾아내기 위한 규칙
- 변수는 (전역) 또는 ("함수" 코드블록, 그냥 코드블록(if, for, while, try/catch)에 선언될 수 있는데, 어디에 선언되었느냐에 따라 본인이 유효하게 사용될 수 있는 범위를 갖는다.

7.스코프는 왜 중요할까요?

스코프는 같은 식별자 이름이 충돌되지 않고, 프로그램 전체에서 하나의 존재로서만 사용되도록 하기 위함이다.

JS : 변수 선언, 그 유효범위가 함수 {} 안에만 되는것, 일반 {} 내이든 외이든 상관없는 것

02. ****데이터타입, 실행 컨텍스트**** KeyWord

---

<aside>
📌 🤔 : 이번 장에서 가장 중요한 키워드입니다. 데이터 타입 장을 읽고 아래의 단어들을 조금 더 이해하는게 오늘의 목표입니다. 천천히 읽어보시고, 각 조원분들과 적당하게 나눠서 아래의 키워드를 직접 설명해주세요.

</aside>

**데이터 타입**

기본형 :  바로 값을 그대로 할당

참조형 : 값이 저장된 주소값을 할당 및 참조,

불변성 : 일부러 바꾸지 않는 한 안 바뀌는 변수의 특징, 할당된 자료값을 보호하기 위해 선언하기도 함 

메모리 주소 : 변수에 대한 데이터값이 저장된 공간의 주소

식별자 : 변수명

변수 : 데이터를 저장할 때 쓰이는 ‘이름이 붙은 저장소’ 

가변값 : 값이 변하는 변수의 특징

불변 객체 : 

객체 내부 프로퍼티 변경(값 변경), 새로운 객체를 만들어 재할당 or 도구 활용하여 불변성 확보

```
               "객체에 변화를 가해도 원본이 남아야 하는경우

```

얕은 복사 : 바로 아래 단계의 값만 복사함. 주소 값을 복사한다는 의미

깊은 복사 : 내부의 모든 값들을 하나하나 찾아서 전부 복사함, 실제 값을 새로운 메모리 공간에 복사

undefined : 선언 o, 할당 x이 직접적으로 이뤄지지 않은 변수/인수에 자동으로 할당된다. 자료형이 없는 상태(undefined)

null : 선언 o, 할당 but 빈값을 할당한 상태. 자료형(object)

```jsx
//복사가 제대로 됐다 = 객체랑 원본이  따로논다 // 별도로 움직인다
  // 복사가 제대로 안됐다 = 객체 원본 같이 논다
```

스택 :  ****프로그램이 실행 중인 위치를 추적하고 함수를 실행할 때 변수와 다른 리소스의 상태를 기억할 수 있게 해주는 기능**(후입선출 식으로 계산) : Last in First OUT : LIFO**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a034f59e-dcb3-460e-8e58-f984826ef43d/Untitled.png)

큐 ****(Queue)****

- 데이터를 집어넣을 수 있는 선형(linear) 자료형이다.
- 먼저 집어넣은 데이터가 먼저나온다. 선입선출함
- 데이터를 집어넣는 enqueue, 데이터를 추출하는 dequeue등의 작업을 할 수 있다.
- 큐는 **순서대로 처리해야 하는 작업을 임시로 저장해두는 버퍼(buffer)**로서 많이 사용됩니다.
- **선입선출: FIRST IN FIRST OUT : FIFO**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e5eb262d-655f-47bc-a8a9-9d3321dc4094/Untitled.png)

전역 컨텍스트 : 프로그램의 모든 코드, 동작 환경을 포함하는 전역 환경이다. 프로그램 (혹은 페이지)가 종료 될 때 까지 유지된다.

콜스택 : 컴퓨터 프로그램에서 현재 실행 중인 서브루틴에 관한 정보를 저장하는 스택 자료구조
**코드의 실행 순서를 관리하는 역할**도 하며, 기존 스택과는 큰 차이는 없음

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd7b8265-a027-4a5c-8d49-4b3fed1df4f8/Untitled.png)

```jsx
var helloWorld = function helloWorld() {
    console.log('Hello World!');
  }
  
  var helloJavascript = function hellowJavascript() {
    console.log("Hello Javascript")
  }
  
  var helloWorldAndJavascript = function hellowWorldAndJavascript() {
    console.log('==== Hello World And JavaScript 시작합니다! ====');
    helloWorld();
    helloJavascript();
    console.log('==== Hello World And JavaScript 끝났습니다! ====');
  }
  
  var helloWorldAndHelloJavascriptTwice = function helloWorldAndHelloJavascriptTwice() {
    console.log('==== Hello World And JavaScript Twice 시작합니다! ====');
    helloWorld();
    helloJavascript();
    helloWorldAndJavascript();
    console.log('==== Hello World And JavaScript Twice 끝났습니다! ====');
  } 
  
  
  helloWorldAndHelloJavascriptTwice();
```

<[자바스크립트 실행 컨텍스트 | 개발자 황준일 (junilhwang.github.io)](https://junilhwang.github.io/TIL/Javascript/Domain/Execution-Context/#_1-%E1%84%80%E1%85%A2%E1%84%82%E1%85%A7%E1%86%B7)>

Variable Environment, 

- 현재 컨텍스트 내의 식별자(변수)들에 대한 정보
- 외부 환경 정보
- **선언 시점의 LexicalEnvironment의 스냅샷(변경사항 반영 X)**

VariableEnvironment에 담기는 내용은 LexicalEnvironment와 같지만, **최초 실행 시의 스냅샷을 유지**한다. 실행 컨텍스트를 생성할 때 VariableEnvironment에 정보를 먼저 담은 다음, 이를 복사해서 LexicalEnvironment를 만든다.

주로 활용하는 것은 LexicalEnvironment이다. 즉, VariableEnviroment는 스냅샷 유지를 목적으로 사용한다.

Lexical Environment(식별자, 변수정보 관련 외부환경 모음)

- 처음에는 VariableEnvironment와 같음
- **변경 사항이 실시간으로 반영됨**
- 

LexicalEnvironment의 내부에는 **environmentRecord**와 **outerEnvironmentReference**로 구성돼 있다.

- **environmentRecord로 인하여 호이스팅이 발생한다.**
- **outerEnvironmentReference로 인하여 스코프와 스코프체인이 형성된다.**

**environmentRecord**

현재 컨텍스트와 관련된 코드의 식별자 정보들이 저장된다.

- 매개변수 식별자
- 함수 자체
- 함수 내부의 식별자

차이점 : ES6에서 한가지 차이점이 생기는데, VariableEnvironment는 변수 var만 저장하고 LexicalEnvironment는 함수 선언과 변수(let과 const) 바인딩을 저장합니다

스코프체인 : 변수와 함수가 정의되고 액세스할 수 있는 범위의 계층 구조, 변수와 함수를 사용할 때 이름 충돌과 예기치 않은 결과를 피하는 데 도움이 되므로 JavaScript에서 중요

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a1644a5c-852a-45cd-bda0-cef2b0adff50/Untitled.png)

호이스팅 : 변수, 함수의 선언부가 최상단으로 끌어올려지는 현상을 이야기한다. 자바스크립트 컴파일러가 선언과 구현(실행)을 별도로 처리하기 때문이다.

## 03. ****데이터타입, 실행 컨텍스트**** Questions

---

<aside>
📌 Questions에 대한 답은 팀원분들과 함께 작성해주세요, 내용을 작성하는데 필요한 개념이나 단어들을 모르는 팀원이 없도록 서로 설명해가며 작성해야합니다. 최종적으로 제출한 답변에 있는 개념이나 단어는 모두가 알고 있어야 합니다.

</aside>

데이터 타입

1.타입을 지정하는 언어는 어떠한 언어가 있는지 확인해보고 해당 언어들과 자바스크립트의 방식의 장단점을 조사해주세요, 가능하다면 실제 케이스를 찾아보고 대답해주세요

- 위 참조

2.변수와 식별자는 어떻게 다를까요?

변수 : '변할 수 있는 데이터', 변경 가능한 데이터가 담길 수 있는 공간

식별자 : '변수명', 해당 공간의 이름, 변수, 함수, 클래스 또는 기타 프로그래밍 구조에 주어진 이름

3.기본형과 참조형은 자바스크립트에서 어떻게 다르고 어떻게 구현되어 있나요?

- 위 참조

4.불변 객체에 대해서 알게된 만큼 작성해주세요

 "객체에 변화를 가해도 원본이 남아야 하는경우

불변 객체 : 

5.얕은 복사와 깊은 복사는 어떠한 차이점이 있으며, 그렇다면 각각의 복사는 어떠한 장단점이 있을까요?

1) 

**얕은 복사가 된 겉의 nest 부분은 원본을 바꿔도 객체에는 적용이 안되는데**

**얕은 복사가 되지 않아 깊은 복사를 해야 하는 안의 nest 부분(중괄호 같은걸로 한번 더 엮어진 행렬이나 array)은 원본을 바꾸면 객체도 같이 바뀜**

2) 

**깊은** **복사(Deep Copy)**는 '실제 값'을 새로운 메모리 공간에 복사하는 것을 의미하며,

**얕은** **복사(Shallow Copy)**는 '주소 값'을 복사한다는 의미입니다.

실행 컨텍스트(관련 정보수집 후 콜스택처럼 실행과정을 모아놓은거라고 생각하면 되나??)

1.우리가 실행 컨텍스트를 제대로 이해하지 못한다면 어떤 문제가 일어날까요?

= 호이스팅이 원하는대로 안될 수 있다. 

= 원하는 순서대로?  내부 함수 실행이 안될 수 있다. (콜스택예시 참조)

= 오류를 찾는 게 어려워질 수 있다. 

2.우리가 스코프를 제대로 이해하지 못한다면 어떤 문제가 일어날까요?

= 변수값을 원하는대로 얻지 못한다. 

= 원래 선언한 변수값이 수정될 수도 있다. 

= 원하는 순서대로 코드가 실현되도록 하는데 있어 구현을 제대로 못할 수 있다.
