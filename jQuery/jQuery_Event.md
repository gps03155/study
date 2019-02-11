### jQuery Event
---

<br>

_jQuery는 HTML 페이지의 이벤트에 응답하도록 설정_

<br>

>### jQuery 이벤트 메소드

<br>

jQuery에서 대부분의 DOM 이벤트는 동등한 jQuery 메소드를 가짐

#### $(document).read()

__HTML 문서가 완전히 로드될 때 함수를 실행할 수 있게 함__

<br>

#### click()

__사용자가 HTML 요소를 클릭할 때 실행__

~~~
$("p").click(function(){
    // 클릭 이벤트 처리 로직
});
~~~

<br>

#### dblclick()

__사용자가 HTML 요소를 두 번 클릭할 때 실행__

~~~
$("p").dblclick(function(){
  // 더블클릭 이벤트 처리 로직
});
~~~

<br>

#### mouseenter()

__마우스 포인터가 HTML 요소에 들어갈 때 실행__

~~~
$("p").mouseenter(function(){
  // mouseenter 이벤트 처리 로직
});
~~~

<br>

#### mouseleave()

__마우스 포인터가 HTML 요소를 벗어날 때 실행__

~~~
$("p").mouseleave(function(){
  // mouseleave 이벤트 처리 로직
});
~~~

<br>

#### mousedown()

__마우스 버튼을 누른 상태에서 마우스가 HTML 요소 위에 있을 때 실행__

~~~
$("p").mousedown(function(){
  // mousedown 이벤트 처리 로직
});
~~~

<br>

#### mouseup()

__마우스 버튼을 놓을 때 마우스가 HTML 요소 위에 있을 때 실행__

~~~
$("p").mouseup(function(){
  // mouseup 이벤트 처리 로직
});
~~~

<br>

#### hover()

__마우스가 HTML 요소에 들어가거나 마우스가 HTML 요소를 떠날 때 실행__
(`mouseenter()` 및 `mouseleave()` 메소드의 조합)

~~~
$("p").hover(function(){
  // mouseenter 이벤트 처리 로직
},
function(){
  // mouseleave 이벤트 처리 로직
});
~~~

<br>

#### focus()

__form 필드에 포커스가 있을 때 실행__

~~~
$("input").focus(function(){
  // focus 이벤트 처리 로직
});
~~~

<br>

#### blur()

__form 필드가 포커스를 잃을 때 실행__

~~~
$("input").blur(function(){
  // blur 이벤트 처리 로직
});
~~~

<br>

#### on()

__선택한 요소에 대해 하나 이상의 이벤트 처리기 연결__

~~~
1. <p> 요소에 클릭 이벤트 연결
$("p").on("click", function(){
  // click 이벤트 처리 로직
});

2. <p> 요소에 여러 이벤트 처리기 연결
$("p").on({
  mouseenter: function(){
    // mouseenter 이벤트 처리 로직
  },
  mouseleave: function(){
    // mouseleave 이벤트 처리 로직
  },
  click: function(){
    // click 이벤트 처리 로직
  }
});
~~~

<br><br>

>### jQuery 콜백 함수

<br>

effect가 완료되지 않은 경우에도 다음 코드 줄을 실행할 수 있기 때문에 오류 방지를 위해 콜백 함수 사용

콜백함수는 현재 effect가 끝난 후에 실행
`$(selector).hide(속도, 콜백)`

~~~
// effect가 완료된 후 콜백 함수 실행

$("button").click(function(){
  $("p").hide("slow", function(){
      alert("hide complete");
    });
});
~~~

<br><br>

>### jQuery 메소드 체이닝 (Method Chaining)

<br>

__단일 구문 내에서 동일한 요소에 대해 여러 jQuery 메소드 실행__

- 메소드 체이닝을 사용하면 브라우저는 같은 요소를 두번 이상 찾을 필요가 없음
- 여러 함수를 한 줄에 사용함으로써 코드를 간결화 시킴

~~~
$("p").css("color", "red").slideUp(2000).slideDown(2000);
~~~
