### ECMAScript
---

<br>

>### ECMAScript란?

<br>

__자바스크립트를 이루는 코어(Core)스크립트 언어__

- 웹 환경에서만 호스트되는 언어가 아니며 웹 환경은 ECMA스크립트가 호스트되는 환경들 중 하나
- ECMAScript 호스트 환경은 ECMAScript 실행환경이 구현되어있고 각각 그 환경에 알맞은 확장성을 가지고 있음
- 다양한 환경에서 운용될 수 있게 확장성을 가지고 있기 때문에 사용처가 웹 환경으로 국한되어있지 않음


<br>

#### ECMAScript가 생긴 이유

_다양한 웹 브라우저에서 자바스크립트가 공통되게 잘 작동하기 위해 표준 규격이 필요 = "ECMAScript Standard"라 불리는 스크립트 표준이 만들어짐_

자바스크립트는 ECMA스크립트와 BOM(Browser Object Model)과 DOM(Document Object Model)의 1개의 코어와 2개의 모델로 이루어짐

두 스크립트는 비슷한 뜻으로 자주 사용되나 차이가 존재

<br><br>

>### ECMAScript에 속하는 것

<br>

- 언어 문법 (파싱 규칙, 키워드 , 흐름제어, 오브젝트 리터럴 초기화 등)
- 에러 처리 방법 (throw, try/catch, 사용자 정의 에러 등)
- 타입 (boolean, number, string, function, object)
- 전역 오브젝트 (parseInt, parseFloat, decodeURI, encodeURI 등)
- 프로토타입을 기반으로한 상속 구조
- built-in 오브젝트 및 함수 (JSON, Math, Array.prototype methods, Object introspecition methods 등)
- Strict mode

<br><br>

>### 정리

<br>

#### 자바스크립트

__자바스크립트는 웹페이지와 상호작용할 수 있도록 디자인된 스크립트언어__

- ECMAScript - ECMA-262에서 정의하는 ECMAScript 핵심 기능 제공
- 문서 객체 모델 DOM - 웹 페이지 콘텐츠를 조작하는 메소드와 인터페이스 제공
- 브라우저 객체 모델 BOM - 브라우저와 상호작용하는 메소드와 인터페이스 제공

<br>

#### ECMAScript

- 다른 언어에 비해 매우 높은 자유도
- 자유도가 낮은 다른 프로그래밍 언어들이 구현하기 힘든 기능들을 자바스크립트로 구현가능
