### jQuery Traversing
---

<br>

_jQuery Traversing은 HTML 요소를 다른 요소와의 관계를 기반으로 찾는데 사용_
(하나의 선택으로 시작하여 원하는 요소에 도달할 때까지 이동)

<br><br>

>### DOM 탐색

<br>

jQuery는 DOM을 탐색할 수 있는 다양한 메소드 제공하며 탐색 방법의 가장 큰 범주는 트리 탐색

#### Ancestors

__DOM 트리를 탐색하여 요소의 조상을 찾을 수 있음__
(조상 : 부모, 조부모, 증조부모 등)

- `parent()`
__선택된 요소의 직접적인 부모 요소 반환__
(DOM 트리의 단일 레벨을 트래버스)

~~~
$(document).ready(function(){
  $("span").parent(); // <span> 요소의 직접 상위 요소 반환
});
~~~

<br>

- `parents()`
__선택한 요소의 모든 상위 요소를 문서의 루트 요소(<html>)까지 반환__

~~~
$(document).ready(function(){
  $("span").parents(); // <span> 요소의 모든 조상 반환
});

$(document).ready(function(){
  $("span").parents("ul"); // <ul> 요소인 모든 <span> 요소의 모든 조상 반환
});
~~~

<br>

- `parentsUntil()`
__주어진 두 인수 사이에 모든 조상 요소 반환__

~~~
$(document).ready(function(){
  $("span").parentUntil("div"); // <span>, <div> 요소와 <div>요소 사이의 모든 조상 요소 반환
});
~~~

<br><br>

#### Descendants

__DOM 트리를 탐색하여 요소의 자손을 찾을 수 있음__
(자손 : 자식, 손자, 증손자 등)

- `children()`
__선택한 요소의 모든 직계 자식을 반환__
(DOM 트리 아래로 단일 레벨을 탐색)

~~~
$(document).ready(function(){
  $("div").children(); // <div> 요소의 직계 자손인 모든 요소를 반환
});

$(document).ready(function(){
  $("div").children("p.first"); // class 이름이 first인 <p>요소 (즉, <div>의 직계 하위 요소 반환)
});
~~~

<br>

- `find()`
__선택한 요소의 자손 요소를 마지막 자손까지 반환__

~~~
$(document).ready(function(){
  $("div").find("span"); // <div> 자손인 모든 <span> 요소 반환
});

$(document).ready(function(){
  $("div").find("*"); // <div>의 모든 자손 반환
});
~~~

<br><br>

#### Siblings

__DOM 트리에서 옆으로 가로 질러 요소의 형제를 찾음__
(형제는 같은 부모 공유)

- `siblings()`
__선택한 요소의 모든 형제 요소 반환__

~~~
$(document).ready(function(){
  $("h2").siblings(); // <h2>의 모든 형제 요소 반환
});

$(document).ready(function(){
  $("h2").siblings("p"); // <h2>의 형제인 모든 <p> 요소를 반환
});
~~~

<br>

- `next()`
__선택한 요소의 다음 형제 요소 반환__

~~~
$(document).ready(function(){
  $("h2").next(); // <h2>의 다음 형제 반환
});
~~~

<br>

- `nextAll()`
__선택한 요소의 다음 형제 요소 모두 반환__

~~~
$(document).ready(function(){
  $("h2").nextAll(); // <h2>의 다음 형제 요소를 모두 반환
});
~~~

<br>

- `nextUntil()`
__주어진 두 인수 사이에 있는 모든 다음 형제 요소 반환__

~~~
$(document).ready(function(){
  $("h2").nextUntil("h6"); // <h2> 요소와 <h6> 요소 사이의 모든 형제 요소 반환
});
~~~

<br>

- `prev()`
- `prevAll()`
- `prevUntil()`

__prev(), prevAll(), prevUntil() 메소드는 위의 메소드와 동일한방식으로 작동하지만 역방향 기능을 사용__
(이전 형제 요소 반환 - DOM 트리의 형제 요소를 따라 뒤로 이동)

<br><br>

>### Filtering

<br>

- `first()`, `last()`, `eq()` : 요소 그룹에서 위치를 기반으로 특정 요소 선택
- `filter()`, `not()` : 특정 기준과 일치하거나 일치하지 않는 요소 선택

<br>

- `first()`
__지정된 요소의 첫 번쨰 요소 반환__
~~~
$(document).ready(function(){
  $("div").first(); // 첫번째 <div> 요소 선택
});
~~~

<br>

- `last()`
__지정된 요소의 마지막 요소 반환__
~~~
$(document).ready(function(){
  $("div").last(); // 마지막 <div> 요소 선택
});
~~~

<br>

- `eq()`
__선택된 요소의 특정 인덱스 번호를 가진 요소 반환__
~~~
$(document).ready(function(){
  $("p").eq(index); // index번째 <p> 요소 선택
});
~~~

<br>

- `filter()`
__조건을 지정할 수 있음__
(기준과 일치하지 않는 요소는 선택 항목에서 제거되고 일치하는 요소는 반환)
~~~
$(document).ready(function(){
   $("p").filter(".intro"); // 클래스 이름이 intro인 모든 <p>인 요소 반환
});
~~~

<br>

- `not()`
__조건과 일치하지 않는 모든 요소 반환__
(not() 메소드는 filter()와 반대)
~~~
$(document).ready(function(){
  $("p").not(".intro"); // 클래스 이름이 intro가 아닌 모든 <p> 요소 반환
});
~~~
