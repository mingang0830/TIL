# Chapter 5 Syntax-Directed Translation 요약

--------------------------------------------

* 상속 속성, 합성 속성
  * Syntax-directed definitions 에서는 두 가지 종류의 속성을 사용할 수 있다.<br/>
  파스 트리 노드의 합성 속성은 자식 노드의 속성에서 계산된다.<br/>
  노드에서 상속 속성은 부모 and/or 형제 속성에서 계산된다.<br/><br/>

* 종속성 그래프(Dependency Graphs)
  * 파스 트리 및 SDD 가 주어지면, 우리는 각 파스 트리 노드와 관련된 속성 인스턴스 사이에 엣지를 그려 엣지 선두에 있는 속성의 값이 엣지 후미에 있는 속성의 값으로 계산된다는 것을 나타낸다.
<br/><br/>
* Cyclic Definitions
  * 문제가 있는 SDD 에서는 모든 노드에서 모든 속성을 계산할 수 있는 순서를 지정할 수 없는 일부 파서 트리가 있다.<br/>
이러한 파서 트리는 관련 종속성 그래프에 주기가 있다.<br/>
SDD 에 이런 순환 종속성 그래프가 있는지 여부를 결정하는 것은 어렵다.<br/><br/>

* S-Attributed Definitions 
  * S-Attributed SDD 에서는 모든 특성이 합성된다.<br/><br/>

* L-Attributed Definitions
  * L-Attributed Definitions SSD 에서는 속성을 상속 또는 합성할 수 있다. <br/>
  그러나 파스 트리 노드에서 상속된 속성은 부모의 상속된 속성과 왼쪽에 있는 형제 노드의 속성에만 의존할 수 있다.<br/><br/>

* Syntax Trees
  * syntax tree 의 각 노드는 구문을 나타내며, 자식 노드는 구문의 의미 있는 구성 요소를 나타낸다.<br/>
  
* S-Attributed 구현
  * S-Attributed 정의는 모든 동작이 생산의 마지막에 있는 SDT에 의해 구현될 수 있다.('Postfix' SDT)<br/>
  액션은 바디 내 심볼의 합성 관점에서 생산 헤드의 합성 속성을 계산한다.<br/>
  기본 문법이 LR이라면 이 SDT는 LR 파서 스택에서 구현될 수 있다.<br/><br/>

* SDT 의 left recursion 제거
  * SDT에 side-effects(속성이 계산되지 않음)만 있는 경우, 문법에 대한 표준 left-recursion-elimination 알고리즘은 마치 터미널인 것처럼 동작을 수행할 수 있다.<br/>
속성이 계산될 때 SDT가 postfix SDT인 경우 left recursion 은 여전히 제거할 수 있다.<br/><br/>

* 재귀 하강 파싱에 의한 L-attributed SDD 구현
  * top-down parsable grammar 에 대한 L-attributed 정의가 있으면 backtracking 없이 recursive-descent parser 를 만들어 번역을 구현할 수 있다.<br/>
  상속된 속성은 터미널에 대한 함수의 arguments 가 되며, 합성된 속성은 해당 함수에 의해 반환된다.<br/><br/>

* LL Grammar 에서 L-Attributed SDD 구현 
  * LL Grammar 이 있는 모든 L-Attributed 정의는 parse 와 함께 구현될 수 있다. <br/>
  논터미널에 대해 합성된 속성을 보유하는 레코드는 스택의 논터미널 아래에 위치하며, 논터미널에 대한 상속된 속성은 스택의 해당 논터미널과 함께 저장된다.<br/>
또한 액션 레코드는 적절한 시간에 속성을 계산하기 위해 스택에 배치된다.<br/><br/>

* LL Grammar 에서 L-Attributed SDD 구현, 상향식
  * LL Grammar 이 있는 모든 L-Attributed 정의는 LR grammar 에 대한 번역과 상향식 parse 와 관련하여 수행되는 번역으로 변환할 수 있다.<br/>
grammar transformation 은 상향식 파서의 스택에 나타나고 그 위에 있는 논터미널의 상속된 속성을 스택에서 유지하는 "마커" 논터미널을 도입한다. 합성된 속성은 스택에 있는 논터미널로 유지된다.

