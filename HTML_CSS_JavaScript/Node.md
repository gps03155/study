### Node
---

<br>

>### 노드(Node)

<br>

HTML DOM은 노드(node)라고 불리는 계층적 단위에 정보를 저장하고 있음
(HTML DOM은 이러한 노드들을 정의하고 그들 사이의 관계를 설명해주는 역할)

__HTML 문서의 정보는 노드 트리(node tree)라고 불리는 계층적 구조에 저장__
(노드 트리는 노드들의 집합이며 노드 간의 관계를 보여줌)

- 노드의 종류
W3C HTML DOM  표준에 따르면 HTML 문서의 모든 것은 노드

노드 | 설명
--- | ---
문서 노드(document node) | HTML 문서 전체를 나타내는 노드
요소 노드(element node) | 모든 HTML 요소는 요소 노드이며 속성 노드를 가질 수 있는 유일한 노드
속성 노드(attribute node) | 모든 HTML 요소의 속성은 속성 노드이며 요소 노드에 관한 정보를 가지고 있음(해당 요소 노드의 자식 노드에는 포함되지 않음)
텍스트 노드(text node) | HTML 문서의 모든 텍스트는 텍스트 노드
주석 노드(comment node) | HTML 문서의 모든 주석은 주석 노드

<br><br>

>### 노드로의 접근

<br>

HTML 문서에서 HTML DOM 노드에 접근하는 방법

- getElementsByTagName()
- 노드 간의 관계를 이용

#### getElementsByTagName()
특정 태그 이름을 가지는 모든 요소를 노드 리스트의 형태로 반환

<br>

#### 노드 간의 관계를 이용하여 접근

- parentNode : 부모 노드
- childNodes : 자식 노드 리스트
- firstChild : 첫번째 자식 노드
- lastChild : 마지막 자식 노드
- nextSibling : 다음 형제 노드
- preiousSibling : 이전 형제 노드

<br><br>

>### 노드의 관리

<br>

#### 노드의 추가

- __appendChild()__
새로운 노드를 해당 노드의 자식 노드 리스트(child node list)의 맨 마지막에 추가

~~~
var parent = document.getElementById("list");
var newItem = document.getElementById("item");

parent.appendChild(newItem); // 해당 요소의 맨 마지막 자식 노드로 추가
~~~

<br>

- __insertBefore()__
새로운 노드를 특정 자식 노드 바로 앞에 추가
(기준 자식 노드에 null 값을 전달하면 새로운 노드는 자식 노드 리스트의 맨 마지막 노드로 추가 - appendChild() 메소드와 같은 동작)
  - 새로운 자식 노드 : 자식 노드 리스트(child node list)에 새롭게 추가할 자식 노드 전달
  - 기준 자식 노드 : 새로운 노드를 삽입할 때 기준이 되는 노드로, 이 노드 바로 앞에 새로운 노드 추가

~~~
부모노드.insertBefore(새로운 자식 노드, 기준 자식 노드);

var parent = document.getElementById("list");
var criteriaItem = document.getElementById("criteria");
var newItem = document.getElementById("item");

parent.insertBefore(newItem, criteriaItem); // 해당 노드를 기준이 되는 자식 노드의 바로 앞에 추가
~~~

<br>

- __insertData()__
텍스트 노드의 텍스트 데이터에 새로운 텍스트 추가
  - 오프셋(offset) : 오프셋 값은 0부터 시작하며 기존 텍스트 데이터의 몇 번째 위치부터 추가할지를 전달
  - 새로운 데이터 : 새로이 삽입할 텍스트 데이터 전달

~~~
텍스트노드.insertData(오프셋, 새로운 데이터);

var text = document.getElementById("text").firstChild; // id가 "text"인 요소의 텍스트 노드를 선택

text.insertData(6, "나른한"); // 텍스트 노드의 6번째 문자부터 "나른한" 이라는 텍스트 추가
~~~

<br><br>

#### 노드의 생성

- __createElement()__
새로운 요소 노드 생성

~~~
var criteriaNode = document.getElementById("text");
var newNode = document.createElement("p"); // 새로운 요소 생성

document.body.insertBefore(newNode, criteriaNode);
~~~

<br>

- __createAttribute()__
새로운 속성 노드 생성
(같은 이름의 속성 노드가 이미 존재하면 기존의 속성 노드는 새로운 속성 노드로 대체 - 이미 존재하는 요소 노드에 속성 노드를 생성하고자 할 때에는 `setAttribute()` 메소드 사용)

~~~
var text = document.getElementById("text");
var newAttribute = document.createAttribute("style"); // 새로운 속성 노드 생성

newAttribute.value = "color:red";
text.setAttributeNode(newAttribute); // 해당 요소의 속성 노드로 추가
~~~

<br>

- __createTextNode()__
새로운 텍스트 노드 생성

~~~
var elementNode = document.getElementById("text");
var newText = document.createTextNode("new text"); // 새로운 텍스트 노드 생성

elementNode.appendChild(newText);
~~~

<br><br>

#### 노드의 제거

- __removeChild()__
자식 노드 리스트에서 특정 자식 노드 제거
(성공적으로 노드가 제거되면 제거된 노드 반환 - 노드가 제거될 때에는 제거되는 노드의 모든 자식 노드들도 다같이 제거)

~~~
var parent = document.getElementById("list")
var removedItem = document.getElementById("item");

parent.removeChild(removedItem); // 지정된 요소 삭제
~~~

<br>

- __removeAttribute()__
속성의 이름을 이용하여 특정 속성 노드 제거

~~~
var text = document.getElementById("text");

text.removeAttribute("style"); // 해당 요소의 "style" 속성 제거
~~~

<br><br>

#### 노드의 복제

- __cloneNode()__
기존의 존재하는 노드와 똑같은 새로운 노드를 생성하여 반환

~~~
복제할 노드.cloneNode(자식 노드 복제 여부);

자식 노드 복제 여부
- 전달된 값이 true이면 복제되는 노드의 모든 속성 노드와 자식 노드도 같이 복제하며 false이면 속성 노드만 복제하고 자식 노드는 복제하지 않음

var parent = document.getElementById("list");
var originItem = document.getElementById("item");

parent.appendChild(originItem.cloneNode(true)); // 해당 노드를 복제하여 리스트의 맨 마지막에 추가
~~~
