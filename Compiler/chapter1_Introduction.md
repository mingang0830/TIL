# Chapter1 introduction 요약

--------------------------------------------

* 언어 프로세서
    * 통합 소프트웨어 개발 환경은 컴파일러, 인터프리터, 어셈블러, 링커, 로더, 디버거, 프로파일러와 같은 다양한 종류의 언어 프로세서를 포함한다.<br/><br/>

* 컴파일러 단계
    * 컴파일러는 일련의 단계로서 동작하며, 각각의 단계는 소스 프로그램을 하나의 중간 표현에서 다른 중간 표현으로 바꾼다.<br/><br/>

* 기계와 어셈블리어
    * 기계어는 1세대 프로그래밍 언어였고 어셈블리어가 그 뒤를 이었다.
    이 언어들로 프로그래밍하는 것은 시간이 오래걸리고 오류가 발생하기 쉽다.<br/><br/>

* 컴파일러 디자인에서의 모델링
    * 컴파일러 디자인은 이론이 실제에 가장 영향을 미친 분야 중 하나이다.<br/>
    발견된 유용한 모델에는 오토마타, grammars, 정규표현식, 트리 등이 포함된다.<br/><br/>

* 코드 최적화
    * 코드를 정말 "최적화" 할 수는 없지만, 코드를 향상시키는 과학은 복잡하고 매우 중요하다.<br/><br/>

* 고급 언어
    * 시간이 지남에 따라 프로그래밍 언어는 메모리 관리, 유형 일관성 검사 또는 코드 병렬 실행과 같이 이전에 프로그래머에게 맡겼던 작업을 점차적으로 더 많이 맡게 된다.<br/><br/>

* 컴파일러와 컴퓨터 아키텍쳐
    * 컴파일러 기술은 컴퓨터 아키텍처에 영향을 줄 뿐만 아니라 아키텍처의 발전에도 영향을 받는다.<br/>
    아키텍처의 많은 현대적 혁신은 컴파일러가 소스 프로그램에서 하드웨어 기능을 효과적으로 사용할 수 있는 기회를 사용할 수 있는 능력에 달려 있다.<br/><br/>

* 소프트웨어의 생산성과 보안
    * 컴파일러가 코드를 최적화할 수 있도록 하는 동일한 기술은 일반적인 프로그램 버그를 감지하는 것에서부터 프로그램이 "해커"들이 발견한 많은 종류의 침입 중 하나에 취약하다는 것을 발견하는 것까지 다양한 프로그램 분석 작업에 사용될 수 있다.<br/><br/>

* 범위(scope) 규칙
    * x의 선언의 범위는 x의 사용이 이 선언을 참조하는 문맥이다.<br/>
    언어는 프로그램만 보고 선언의 범위를 결정할 수 있는 경우 static scope 또는 lexical scope 를 사용한다. 그렇지 않으면 언어가 dynamic scope 를 사용한다.<br/><br/>

* 환경
    * 메모리의 위치 및 값과의 이름 연관성은 저장 위치에 이름을 매핑하는 environments 와, 값에 위치를 매핑하는 states 로 설명할 수 있다.<br/><br/>

* 블록 구조
    * 블록을 중첩할 수 있는 언어를 블록 구조라고 한다.<br/>
    중첩된 블록 B의 이름인 x는 중간 블록에 다른 x 선언이 없는 경우 둘러싸인 블록 D 의 x 선언 범위에 있다.<br/><br/>

* 파라미터 전달
    * 파라미터는 value 또는 reference 를 통해 호출 프로시저에서 호출자로 전달된다.<br/>
    큰 객체가 value 로 전달될 때, 전달된 value 는 실제로 객체 자체에 대한 reference 이므로 call-by-reference 가 효과적이다.<br/><br/>

*  별칭(Aliasing)
    * 파라미터가 참조에 의해 효과적으로 전달되면 두 개의 formal 파라미터가 동일한 개체를 참조할 수 있다.<br/>
    이러한 가능성은 한 변수를 변경하면 다른 변수도 변경할 수 있도록 한다.<br/><br/>

