---
title: [JS_study] 15장 let, const 키워드와 블록 레벨 스코프
categories: [JS_study]
tags: [js, study] # TAG는 반드시 소문자로 이루어져야함!
---

# 15.1 var 키워드로 선언한 변수의 문제점

ES5까지 변수를 선언할 수 있는 유일한 방법은 `var`키워드를 사용하는 것이었다.

### var 키워드로 선언된 변수의 특징

### 15.1.1 변수 중복 선언 허용

`var`키워드로 선언한 변수는 중복 선언이 가능하다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ab882899-88b8-4055-9362-b466feb13db0/Untitled.png)

### 15.1.2 함수 레벨 스코프

`var`키워드로 선언한 변수는 오로지 함수의 코드 블록만을 지역 스코프로 인정한다.

따라서 함수 외부에서 `var`키워드로 선언한 변수는 코드 블록 내에서 선언해도 모두 전역 변수가된다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/46cfbd66-4324-470f-b309-0fe81ee5ad3a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ce0084d7-3b79-4011-945a-70d359c2964d/Untitled.png)

### 15.1.3 변수 호이스팅

`var`키워드로 변수를 선언하면 변수 호이스팅에 의해 변수 선언문이 스코프의 선두로 끌어 올려진 것처럼 동작한다.

즉, 변수 호이스팅에 의해 `var`키워드로 선언한 변수는 변수 선언문 이전에 참조할 수 있다.

단, 할당문 이전에 변수를 참조하면 언제나 `undefined`를 반환한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/afe8a1fd-dbbc-4dd1-9466-29bb65105d56/Untitled.png)

→ 변수 선언문 이전에 변수를 참조하는 것은, 변수 호이스팅에 의해 에러를 방생시키지는 않지만, 프로그램의 흐름상 맞지 않고, 가독성을 떨어뜨리고, 오류 발생 가능성 있음.

# 15.2 let 키워드

ES6에서 `var`키워드를 보안하기 위해,

새로운 변수 선언 키워드인 `let`, `const`를 도입했다.

### 15.2.1 변수 중복 선언 금지

`let`키워드로 이름이 같은 변수를 중복 선언하면 문법 에러(SyntaxError)가 발생한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa201a6c-994b-4922-ae31-162705646538/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/12f321b0-6621-40cd-9ae8-c8265e90a426/Untitled.png)

### 15.2.2 블록 레벨 스코프

- 블록 레벨 스코프
    - `**let`키워드는 → 블록 레벨 스코프를 따른다.**
    - **블록 레벨 스코프 : 모든 코드 블록을 지역 스코프로 인정한다.**
        - 코드 블록 : 함수, if문, for문, while문, try/catch문
            - `{ }`

`let` 키워드로 선언한 변수는 **모든 코드 블록(함수, if문, for문, while문, try/catch 문 등)을 지역 스코프로 인정하는 블록 레벨 스코프를 따른다.**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e93b8cd8-aeb1-4cbd-8716-a079aa540375/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fe495292-0f19-40c9-b7a5-b7055199a750/Untitled.png)

- 함수 내의 코드 블록은 함수 레벨 스코프에 중첩된다.

### 15.2.3 변수 호이스팅

`let` 키워드로 선언한 변수는 변수 호이스팅이 발생하지 않는 것처럼 동작한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/96439b0a-3f65-4c96-a83b-7c3d907be7fd/Untitled.png)

`**let`키워드로 선언한 변수를 변수 선언문 이전에 참조하면 참조 에러(ReferenceError)가 발생한다.**

- 스코프의 시작 지점부터 초기화 단계 시작 지점(변수 선언문)까지 변수를 참조할 수 없다.

`**let` 키워드로 선언한 변수는 “선언 단계”와 “초기화 단계”가 분리되어 진행된다.**

런타임 이전에 JS엔진에 의해 암묵적으로 선언 단계가 먼저 실행되지만, 초기화 단계는 변수 선언문에 도달했을 때 실행된다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ea71c8fc-86f9-4c00-bdd9-b51565f07db5/Untitled.png)

- `var`
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/811c5ed4-17a6-41a2-b367-cc4c07bdf420/Untitled.png)
    
- `let`
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ab07e54f-afd2-479a-85f5-90c23759805b/Untitled.png)
    

- 스코프의 시작 지점부터 초기화 시작 지점까지 **변수를 참조할 수 없는 구간을 일시적 사각지대(Temporal Dead Zone; TDZ)**라고 부른다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8cffe9da-0b21-41ae-924c-2fbf94388c58/Untitled.png)

`**let`키워드로 선언한 변수도 여전히 호이스팅이 발생**하기 때문에,
참조 에러(ReferenceError)가 발생한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/41579433-ebd9-4a10-8a25-0877a115b7e1/Untitled.png)

- 변수 호이스팅o, 그저 초기화(`undefined`할당)가 되지 않은 것.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1c5ec504-7d84-4fe6-8580-13bec1bb5b37/Untitled.png)

### 15.2.4 전역 객체와 let

- `var`키워드로 선언한 전역 변수, 전역 함수, 그리고 선언하지 않은 변수에 값을 할당한 암묵적 전역은 전역 객체 window의 프로퍼티가된다.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d56d7190-2aab-4839-a99e-faf066b1008d/Untitled.png)
    

전역 객체의 프로퍼티를 참조할 때 window를 생략할 수 있다.

`**let` 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다.**

**즉, `window.foo`와 같이 접근할 수 없다.**

**(`let`전역 변수는 보이지 않는 개념적인 블록 내에 존재하게 된다.**

- 블록 : 전역 렉시컬 환경의 선언적 환경 레코드)
    - 선언적 환경 레코드
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/df691b08-5515-4e6a-981c-62caa903867b/Untitled.png)
        
        (전역)실행 컨택스트 생성 → (전역)렉시컬 환경 생성 → (전역)객체 환경 레코드, 선언적 환경 레코드 / this 바인딩 / 외부 참조 → 실행 
        → 함수 만나면 함수 실행 컨택스트를 생성하고, 실행하게됨.
        

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8d4becee-52f7-4975-b019-3d4021e3a188/Untitled.png)

# 15.3 const 키워드

`const` 키워드는 상수를 선언하기 위해 사용한다.

반드시 상수 선언을 위한 것은 x

- `let` 키워드와 대부분 동일

### 15.3.1 선언과 초기화

`**const`키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다.**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6bbaa101-2ddc-47bb-9a54-0a10e6ee8493/Untitled.png)

![초기화하지 않을 경우 SyntaxError 발생](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/01f06249-8af6-490b-8fcd-c6739ebdb0bf/Untitled.png)

초기화하지 않을 경우 SyntaxError 발생

- `let` 키워드로 선언한 변수와 마찬가지로 **블록 레벨 스코프를 가지며, 변수 호이스팅이 발생하지 않는 것처럼 동작한다.**
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cedddf72-afa4-45a4-895a-d15563e4da5e/Untitled.png)
    

### 15.3.2 재할당 금지

`var`, `let` 키워드로 선언한 변수는 재할당이 자유로우나,

`**const`키워드로 선언한 변수는 재할당이 금지된다.**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/574e85f1-3dcb-4dc6-9fd8-d706a8298dd0/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a5f34ca3-1901-44d4-a74d-115af67477a3/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2eafc3c7-755d-4c7c-b410-04fc05451a0e/Untitled.png)

### 15.3.3 상수

`**const`키워드로 선언한 변수에 원시 값을 할당한 경우 변수 값을 변경할 수 없다.**

- **재할당을 할 수 없기 때문.**
- **이러한 특징을 이용해 `const`키워드를 상수를 표현하는 데 사용하기도 한다.**

변수의 상대 개념은 상수는 재할당이 금지된 변수를 의미한다.

상수도 값을 저장하기 위한 메모리 공간이 필요하므로 변수라고 할 수 있다.

단, 변수는 언제든지 재할당을 통해 변수 값을 변경하룻 있지만,
상수는 재할당이 금지된다.

- 상수는 상태 유지와 가독성, 유지보수의 편의를 위해 적극적으로 사용해야한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/98e2db06-32d4-4ac8-8f76-ee3e6b6cafbf/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2d49965f-3141-4580-8207-c2b9122684d3/Untitled.png)

- 세율을 상수로 정의하면 값의 의미를 쉽게 파악할 수 있고, 고정값으로 사용할 수 있다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3de4eb19-83e6-4c97-af2a-b597abba38d8/Untitled.png)

- 일반적으로 상수의 이름은 대문자로 선언해 상수임을 명확히 나타낸다.
- 여러 단어로 이루어진 경우 `_`(언더스코어)로 구분해서 스네이크 케이스로 표현하는 것이 일반적이다.

### 15.3.4 const 키워드와 객체

`**const`키워드로 선언된 변수에 객체를 할당한 경우 값을 변경할 수 있다.**

**변경 가능한 값인 객체는 재할당 없이도 직접 변경이 가능하기 때문이다.**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bd6bff68-d1ec-43e1-83e3-d44dd4ca8e3a/Untitled.png)

- const로 선언된 변수 → 재할당 x. 값 변경o.
    - 객체는 변경 가능한 값이다.
    - const로 선언된 변수의 경우 → 변수의 값을 바꾸면, 기존 주소에 있던 값이 변경(재할당)되는 것이 아니라, → 새로운 주소에 값을 할당해서, 그 값을 이용하게된다.
        - let으로 재할당을 할 경우, 처음에 할당해 주었던 값은 아예 삭제되어 버린다.
        - const 변수 값은 주소에 남아있음.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7a2f5ec3-e4e2-4d62-81e4-f76c7a92c475/Untitled.png)
    

# 15.4 var VS let VS const

**변수 선언에서는 기본적으로 `const`를 사용하고,**

`**let`은 재할당이 필요한 경우에 한정해서 사용하는 것이 좋다.**

- **ES6를 사용한다면 `var`키워드는 사용하지 않는다.**
- **재할당이 필요한 경우에 한정해 `let` 키워드를 사용한다.**
    - **이때 변수의 스코프는 최대한 좁게 만든다.**
- **변경이 발생하지 않고 읽기 전용으로 사용하는(재할당이 필요 없는 상수) 원시 값과 객체에는 `const`키워드를 사용한다.**
    - `**const`키워드는 재할당을 금지하므로 `var`, `let`키워드보다 안전하다.**

변수를 선언하는 시점에는 재할당이 필요할지 잘 모르는 경우가 많다.

그리고 객체는 의외로 재할당하는 경우가 드물다.

따라서 **변수를 선언할 때는 일단 `const` 키워드를 사용하자.**

**반드시 재할당이 필요하다면 그때 `const`키워드를 `let`키워드로 변경해도 결코 늦지 않다.**