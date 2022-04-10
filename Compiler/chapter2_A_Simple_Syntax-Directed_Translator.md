# Chapter2 A Simple Syntax-Directed Translator 요약

--------------------------------------------

![figure2_46.png](figure2_46.png)

* syntax-directed translator 의 시작점은 소스 언어의 문법이다.<br/>
문법은 프로그램의 계층 구조를 설명한다. 이것은 terminals 로 불리는 elementary symbol과, nonterminals 로 불리는 variable symbol 로 정의된다.
이러한 symbol 은 언어 구조를 나타낸다. 문법의 규칙 또는 생성(productions) 은 생성의 머리 또는 왼쪽 부분인 nonterminals 과 생성의 본문 또는 오른쪽 부분인 terminals 로 구성된다.<br/>
하나의 nonterminal 이 start symbol 로 지정된다.<br/><br/>

* translator 을 지정할 때 속성을 프로그래밍 구조에 첨부하는것이 도움이 된다.
속성은 구성과 관련된 수량이다.<br/>
구조들은 grammar symbols로 표현되기 때문에, 속성의 개념은 grammar symbols 로 확장된다.<br/>
속성의 예로는 숫자를 나타내는 teminal num 과 연관된 정수 값, 식별자를 나타내는 terminal id 와 연관된 문자열이 있다.<br/><br/>

* lexical analyzer 는 입력을 한 번에 한 문자씩 읽고 출력으로 토큰 스트림을 생성하는데, 여기서 토큰은 속성 값의 형태로 추가 정보와 함께 터미널 symbol로 구성된다.<br/>
그림 2.46에서 토큰은 < > 사이에 둘러싸인 튜플로 작성된다. 토큰 < id ; "pek" >은 터미널 ID와 문자열 "peek"를 포함하는 심볼 테이블 항목에 대한 포인터로 구성된다.
translator 는 테이블을 사용해서 예약된 단어와 이미 표시된 식별자를 추적한다.<br/><br/>

* 파싱(parsing)은 문법의 시작 심볼로부터 nonterminal 를 반복적으로 대체함으로써 어떻게 terminals 의 문자열 도출할 수 있는지를 알아내는 문제이다.<br/>
개념적으로 파서는 루트가 시작 기호로 레이블링되고, 각 nonleaf 는 생산에 대응하며, 각 leaf 에는 terminal 또는 빈 문자열 ε로 레이블링되는 구문 분석 트리(parser tree)를 구축한다.
<br/>구문 분석 트리는 왼쪽에서 오른쪽으로 읽히는 잎에 있는 터미널의 문자열을 도출한다.<br/><br/>

* 효율적인 파서는 예측 구문 분석이라고 불리는 하향식(루트에서 파싱 트리의 잎까지) 방법을 사용하여 손으로 만들 수 있다.<br/>
예측 파서는 각 nonterminal 에 대한 절차를 가지고 있으며, 절차의 body 는 nonterminal에 대한 생산을 모방하고, 절차의 body 를 통한 흐름의 제어는 입력 스트림에서 하나의 심볼을 보고 명확하게 결정할 수 있다.<br/><br/>

* Syntax-directed translation 은 규칙이나 프로그램 조각을 문법의 제작에 첨부함으로써 이루어진다. <br/>이 챕터에서는 합성 속성만 고려함 - 임의의 노드 x에서 합성된 속성의 값은 x의 자식(있는 경우) 속성에만 의존할 수 있음. 
<br/>syntax-directed definition 은 production에 규칙을 첨부하며, 규칙은 속성 값을 계산한다.<br/>
translation scheme 은 semantic(의미론적) actions 이라 불리는 프로그램 조각을 production bodies 에 내장한다.<br/>
actions 은 syntax analysis 중에 production 에서 사용되는 순서대로 실행된다.<br/><br/>

* syntax analysis 의 결과는 중간 코드라고 불리는 소스 프로그램의 표현이다.<br/> 중간 코드의 두 가지 주요 형태는 그림 2.46에 도시되어 있다.<br/> 추상 구문 트리(abstract syntax tree)는 프로그래밍 구문를 위한 노드를 가지고 있으며, 자식 노드들은 의미 있는 하위 구문을 제공한다.
<br/>대안으로 three-address code 는 각 명령이 single operation 을 수행하는 명령어 시퀀스이다.<br/><br/>

* symbol tables 는 식별자에 대한 정보를 저장하는 데이터 구조이다. <br/>식별자 선언아 분석될 때 심볼 테이블에 정보가 입력된다. semantic action은 식별자가 나중에 사용될 때 심볼 테이블에서 정보를 가져온다.
예를 들어 식에서 인자로 사용할 수 있다.