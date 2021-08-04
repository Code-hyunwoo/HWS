# :boom: Workshop

---

​				

## 	 :fire:  Bootstrap

- 트위터에서 시작된 오픈소스 프론트엔드 라이브러리

- 웹 페이지에서 많이 쓰이는 요소 거의 전부를 내장하고 있음

- 별도의 디자인을 할 시간이 크게 줄어들고, 

- 여러 웹 브라우저를 지원하기 위한 크로스 브라우징에 불필요한 시간을 사용하지 않도록 함

- One source multi use

  ​																		

  ​																						

  **Normalize CSS**

> Gentle solution

-  브라우저 중 하나가 불일치 한다면 차이가 있는 브라우저를 수정한다.

- 경우에 따라 IE 또는 EDGE는 수정 할 수 없는 경우가 있는데, 

- 이럴때는 IE 또는 EDGE의 스타일을 나머지 브라우저에  맞춘다

  ​																						

  **Reset CSS**

> Aggressive solution

- 브라우저의 기본 스타일이 전혀 필요없다는 방식으로 접근한다.

- 따라서 브라우저의 user agent와 함께 제공되는 모든 스타일을 재설정한다.

- 문제점은 너무나 많은 선택자가 엉켜있고, 불필요한 오버라이드가 많이 발생하여 디버깅 시 제대로 못읽음

  ​																		

  ### :smile: CDN

> Content Delivery Network

- 컨텐츠(CSS, JS, Image 등)을 효율적으로 전달하기 위해, 
  여러 노드에 가진 네트워크에 데이터를 제공하는 시스템

- 서버와 사용자 사이의 물리적 거리를 줄여 컨텐츠 로드 지연을 최소화

- 분산 된 서버로 이루어진 플랫폼

  - 전 세계 사용자들이 로딩 시간을 늦추지 않고 동일한 품질의 컨텐츠를 사용할 수 있음

- 외부 서버를 활용함으로써 본인 서버의 부하가 적어짐

  ​																	

  ### Responsive Web Design

- 다양한 화면 크기를 가진 디바이스들이 등장함에 따라 등장

- 반응형 웹은 별도의 기술 이름이 아닌 웹 디자인에 대한 접근 방식

- 반응형 레이아웃 작성에 도움이 되는 사례들의 모음 등을 기술하는데 사용되는 용어

  ​													

### Grid system

- Bootstrap Grid system은 flexbox로 제작됨

- **container, rows, column**은 컨텐츠를 배치하고 정렬

- 12개의 column,  6개의 grid breakpoints

  ​																					

#### row

-  columns의 wrapper

#### gutters

- grid 시스템에서 반응적으로 공간을 확보하고 컨텐츠를 정렬하는 데 사용되는 column 사이의 padding

#### col, col-*

- column class는 row 당 가능한 12개 중 사용하려는 columns 수를 나타냄

- columns 너비는 백분율로 설정되므로 항상 부모요소를 기준으로 유동적으로 크기가 조정됨

- 오직 columns만 row의 바로 하위 자식일 수 있음

  ​																

#### Grid breakpoints

- 다양한 디바이스에서 적용하기 위해 특정 px조건에 대한 지점을 정해두었는데 이를 breakpoints라고 함
- bootstrap은 대부분의 크기를 정의하기 위해 em 또는 rem을 사용하지만 px은 grid breakpoints에 사용

- **xs , sm ,  md , lg , xl , xxl**

  ​								

  ​												

#### offset

- 지정한 만큼의 column 공간을 무시하고 다음 공간부터 컨텐츠를 적용

#### Nesting(중첩)

- row > col-*>row>col- 의 방식으로 중첩 사용 가능