# Chapter6 Intermediate-Code Generation 요약 

--------------------------------------------

* 중간 표현 고르기
  * 중간 표현은 일반적으로 graphical notation 과 three-adress code 의 조합이다.<br/>
  syntax tree 에서과 같이, graphical notation  노드는 구문을 나타내며 , 자식 노드는 하위 구문을 나타낸다.<br/>
  three-adress code 는 x = y op z 형식의 명령어에서 이름을 따왔으며, 명령어당 최대 하나의 연산자를 갖는다.<br/>
  제어 흐름에 대한 추가 연산자가 있다.<br/><br/>

* 표현식 번역
  * 연산이 내장된 표현식은  E -> E1 ope E2 형식의 각 생성에 액션을 붙여 개별 연산의 시퀀스로 풀 수 있다.<br/>
  이 액션은 E1과 E2의 노드가 자식노드인 E 노드를 생성하거나, E1과 E2의 주소에 op를 적용하고 그 결과를 새로운 임시 이름에 넣는 three-address 명령을 만든다.<br/><br/>
  
* 타입 체크
  * E1 op E2 표현식의 타입은 연산자 op와 E1 및 E2의 타입에 따라 결정된다.<br/>
  강제성은 정수를 float 로 변환하는 것과 같은 묵시적 형변환이다.<br/>
  중간 코드는 피연산자 유형과 연산자가 예상하는 타입 간의 정확한 일치를 보장하기 위한 명시적 형변환을 포함한다.<br/><br/>

* 선언을 구현하기 위한 심볼 테이블 사용
  * 선선은 이름의 타입을 지정한다.<br/>
  타입의 너비(width) 는 해당 타입의 이름에 필요한 저장소의 양이다.<br/>
  너비를 사용하여 실행 시 이름의 상대 주소를 데이터 영역의 시작에서 오프셋으로 계산할 수 있다.<br/>
이름의 타입 및 상대 주소는 선언으로 인해 심볼 테이블에 입력되므로, translator 는 이름이 표현식에 나타날 때 해당 이름을 나중에 가져올 수 있다.<br/><br/>
  
* Flatten arrays
  * 빠른 엑세스를 위해 배열 요소들은 연속된 위치에 저장된다.<br/>
  배열은 개별 요소의 1차원 배열로 처리될 수 있도록 평탄화된다.<br/>
  배열의 타입은 배열의 base 에 배열 요소의 상대 주소를 계산하는 데 사용된다.<br/><br/>

* boolean expressions 에 대한 jumping code 생성
  * short-circuit 또는 jumping code 에서 boolean expressions 의 값은 코드가 도달한 위치에 암시된다.<br/>
  jumping code 는 if (B) S 에서와 같이 boolean expressions B 가 일반적으로 제어 흐름에 사용되기 때문에 유용하다.<br/>
  Boolean 값은  t = true 또는 t = false로 점프하여 계산할 수 있다. 여기서 t 는 임시 이름<br/>
  jumps 의 레이블을 사용하여 boolean expression 은 참과 거짓 exits 에 해당하는 레이블을 상속하여 변환할 수 있다.<br/>
  true 상수와 false 상수는 각각 true 및 false exit 로 jump 한다.<br/><br/>

* 제어 흐름을 사용한 statements 구현
  * 뒤(next)의 레이블을 상속하여 statements 를 번역할 수 있다. 여기서 뒤(next)는 이 statements 의 코드 후에 있는 첫번째 명령을 말함<br/>
  조건 S -> if (B) S1 는 S1에 대한 코드 시작을 표시하는 새로운 레이블을 붙이고, B의 참과 거짓 exits 에 각각 새로운 레이블과 S.next를 전달함으로써 번역될 수 있다.<br/><br/>

* 대안, backpatching 사용 
  * backpatching 은 boolean expressions 와 statements 대한 코드를 한 번에 생성하는 기술이다.<br/>
  이 아이디어는 리스트에 있는 모든 점프 명령이 동일한 타겟을 갖는 불완전한 점프 리스트를 유지보수 하는 것이다.<br/>
  타켓이 알려지면 타켓에 대한 정보를 채움으로써 그 목록에 있는 모든 명령들은 완성된다.<br/><br/>

* 레코드 구현
  * 레코드 또는 클래스의 필드 이름은 선언 시퀀스로 처리할 수 있다.<br/>
  레코드 타입은 필드의 타입과 상대 주소를 인코딩한다.<br/>
  심볼 테이블 객체를 이 용도로 사용할 수 있다.
