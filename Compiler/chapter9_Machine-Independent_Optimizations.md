# Chapter9 Machine-Independent Optimizations 요약 

--------------------------------------------
* Global Common Subexpressions
  * 중요한 최적화는 두 개의 다른 기본 블록에서 동일한 표현식의 계산을 찾는 것이다.
  하나가 다른 하나에 선행하는 경우, 우리는 처음 계산될 때 결과를 저장하고 이후 발생 시 저장된 결과를 사용할 수 있다.
  * Subexpression(하위 표현식) : 특정 패턴, 표현식을 하나의 항목으로 처리하는 것이다. 이 하위 표현식을 사용하려면 소괄호를 사용해야 한다<br/><br/>

* Copy Propagation(복사 전달)
  * copy statement 인 u = v는 한 변수 v를 다른 변수 u에 할당한다.
  어떤 상황에서는 u의 모든 용도를 v로 대체할 수 있으므로 할당과 u를 모두 제거할 수 있다.<br/><br/>
  
* Code Motion(부호 이동)
  * 또 다른 최적화는 연산이 나타나는 루프 밖으로 이동하는 것이다.
  이 변경은 계산에서 루프를 한 바퀴 돌 때마다 동일한 값을 생성하는 경우에만 정확하다.<br/><br/>

* Induction Variables(유도 변수)
    * 루프가 반복될 때마다 고정된 양만큼 증가 하거나 감소하는 변수이거나 다른 유도 변수의 선형 함수
    * 많은 루프는 유도 변수를 가지고 있는데, 이 변수들은 루프를 한 바퀴 돌 때마다 값의 선형 시퀀스를 갖는다.
  일부는 반복을 세는 데만 사용되며, 종종 제거될 수 있으므로 루프를 도는 데 걸리는 시간을 줄일 수 있다.<br/><br/>

* Data-Flow Analysis(데이터 흐름 분석)
  * 데이터 흐름 분석 스키마는 프로그램의 각 지점에서 값을 정의한다.<br/>
  프로그램의 statements 는 statement 앞의 값과 statement 뒤의 값을 연관시키는 transfer functions 을 가지고 있다.<br/>
  두 개 이상의 선행자가 있는 statement 에는 일치(또는 결합) 연산자를 사용하여 선행자의 값을 조합하여 값을 정의해야 한다.<br/><br/>

* 기본 블록에 대한 데이터 흐름 분석
  * 블록 내에서 데이터 흐름 값의 전파는 일반적으로 매우 간단하기 때문에, 데이터 흐름 방정식은 일반적으로 각 블록에 대해 IN과 OUT라는 두 개의 변수를 가지도록 설정되며, 각각 블록의 시작과 끝의 데이터 흐름 값을 나타낸다.<br/>
  블록에서 statement 에 대한 transfer functions 는 블록 전체에 대한 transfer function 을 얻도록 구성된다.<br/><br/>

* Reaching Definitions
  * Reaching Definitions data-flow framework 에는 하나 이상의 변수에 대한 값을 정의하는 프로그램의 statements 집합인 값이 있다.<br/>
  블록에 대한 transfer function 은 블록에서 확실히 재정의된 변수의 definitions 를 죽이고 블록 내에서 발생하는 변수의 definitions 를 추가("generates(생성)")한다.<br/>
  confluence operator(융합 연산자) 는 합집합인데, definitions 가 만약 어느 포인트의 선행자에 도달하면 definitions 가 포인트에 도달하기 때문이다.<br/><br/>
  
* Live Variables
  * 또 다른 중요한 data-flow framework 는 각 지점에서 live(재정의 전에 사용될) 변수를 계산한다.<br/>
  이 프레임워크는 transfer function 가 backward 로 실행된다는 점을 제외하면 reaching definitions 과 유사하다.<br/>
  변수는 블록에서 정의하기 전에 사용되거나 블록 끝에서 사용되며 블록에서 재정의되지 않는 경우 블록의 시작 부분에서 활성화된다.<br/><br/>

* 사용 가능한 표현식
  * global common subexpressions 을 발견하기 위해, 우리는 각 지점에서 사용 가능한 표현식 - 계산되었으며 마지막 계산 후에 표현식의 argument 가 모두 재정의되지 않은 - 을 결정한다. <br/>
  data-flow framework 는 reaching definitions 비슷하지만 confluence operator 는 결합이 아닌 교차점이다.<br/><br/>

* Data-Flow 문제의 추상화
  * 이미 언급한 것과 같은 일반적인 Data-Flow 문제는 일반적인 수학적 구조로 표현될 수 있다.<br/>
  값은 semilattice(반격자)의 구성원으로, 이 조합은 융합 연산자이다.<br/>
  Transfer function 는 격자 요소(lattice elements)를 격자 요소에 매핑한다.<br/>
  allowed transfer function 집합은 구성 요서 아래서 닫혀야 하며, identity function 을 포함해야 한다.<br/><br/>

* Monotone Frameworks
  * semilattice 는 a ^ b = a인 경우에만 a <= b 로써 a <= 로 정의되는 괸계를 가진다.<br/>
  Monotone framework 은 각 transfer functions 이 <= 관계를 보존한다는 특성을 갖는다.<br/>
  즉, 모든 lattice element a와 b의 transfer functions f에 대해 a <= b는 f(a) <= f(b)를 의미한다.<br/><br/>

* Distributive Frameworks (분포 프레임워크)
  * 모든 lattice element a와 b의 transfer functions f에 대해 이 프레임워크는 f(a ^ b) = f(a) ^ f(b)의 조건을 만족한다.<br/>
  distributive condition 이 monotone condition 을 의미한다는걸 알 수 있다.<br/><br/>

* 추상적 프레임워크에 대한 반복적 솔루션(Iterative Solution to Abstract Frameworks)
  * 모든 monotone data-flow frameworks 는 iterative algorithm 로 해결할 수 있는데, 
  이 알고리즘에서는 각 블록에 대한 IN 및 OUT 값이 적절하게 초기화되고(프레임워크에 따라 다름) 이러한 변수에 대한 새로운 값이 전송 및 융합 연산을 적용하여 반복적으로 계산된다.<br/>
  이 솔루션은 항상 안전하지만(프로그램이 수행하는 작업을 최적화하는 것이 변경하지 않을 것이라는 것을 암시한다), 프레임워크가 분산되어 있을 경우에만 솔루션이 가장 우수할 것이 확실하다.<br/><br/>

* The Constant Propagation Framework(상수 전파 프레임워크)
  * reaching definitions 과 같은 기본 프레임워크는 분산적이지만, 분산되지 않는 흥미로운 모노톤 프레임워크도 있다.<br/>
하나는 요소가 프로그램 변수에서 상수로 매핑되는 반격자와 "정보 없음" 및 "확실히 상수가 아님"을 나타내는 두 개의 특수 값을 사용하여 상수를 전파하는 것과 관련된다.<br/><br/>

* Partial-Redundancy Elimination(부분 중복 제거)
  * code motion, global common-subexpression elimination 와 같은 많은 유용한 최적화는 부분 중복 제거라고 불리는 단일 문제로 일반화 될 수 있다.<br/>
  필요하지만 포인트의 일부 경로에서만 사용할 수 있는 표현식은 사용할 수 없는 경로를 따라서만 계산된다.<br/>
  이 아이디어를 올바르게 적용하려면 네 가지 다른 데이터 흐름 문제와 기타 작업에 대한 해결책이 필요하다.<br/><br/>

* Dominators
  * flow graph 의 노드는 후자의 모든 경로가 전자를 통과해야 하는 경우 다른 노드를 지배한다.<br/>
  적절한 dominator 은 노드 자체 이외인 dominator 이다.<br/>
  엔트리 노드를 제외한 각 노드는 즉각적인 dominator(다른 모든 적절한 dominator에 지배되는 적절한 dominator 중 하나) 을 가진다.  <br/><br/>

* Flow Graphs 의 깊이 우선 순서
  * Flow Graphs의 깊이 우선 탐색을 수행하면 해당 항목에서 시작하여 깊이 우선 스패닝 트리를 만든다.<br/>
  노드의 깊이 우선 순서는 이 트리의 후위 순회의 리버스다.<br/>
  * 스패닝 트리 :  노드 간 경로가 오직 하나 뿐인 토폴로지
     - 루프 순환(looping, 예: Bridge Loop)이 없는 그래프의 일종
     - 주로, 루프 순환의 방지를 위한 트리 특성을 갖는 그래프<br/><br/>

* Classification of Edges(엣지 분류)
  * 깊이 우선 스패닝 트리를 구성할 때 flow graph 의 모든 엣지는 세 그룹으로 나눌 수 있다.
    * advancing edges(순행 간선) 조상에서 적절한 자손으로 가는 것
    * retreating edges(역행 간선) 자손에서 조상으로 가는 것
    * cross edges(교차 간선)
  중요한 특성은 트리에서 모든 교차 간선이 오른쪽에서 왼쪽으로 간다는 것이다.<br/>
  또 다른 중요한 특성은 이러한 엣지들 중 retreating edges 만이 깊이 우선 순서에 따라 tail보다 낮은 head를 가지고 있다는 것이다.<br/><br/>

* Back Edge(역 간선)
  * Back Edge 는 head 가 tail 을 지배하는 것을 말한다.<br/>
  flow graph에 대해 어떤 깊이 우선 스패닝 트리가 선택되었는지에 관계없이 모든  back edge는 retreating edges이다.<br/><br/>

* 축소 가능한 flow graph
  * 모든 retreating edge 가 어떤 깊이 우선 스패닝 트리를 선택했는지에 관계 없이 back edge 일 경우, flow graph 는 축소 가능하다고 말한다.<br/>
  대부분의 flow graph 는 축소 가능하다; control-flow statement 만이 일반적인 루프 형성 및 분기 statements 인 경우 확실하게 축소 가능하다.<br/><br/>

* Natural Loops 
  * Natural Loops 는 집합에 있는 모든 노드를 지배하는 헤더 노드를 가진 노드 집합으로, 해당 노드에 들어가는 적어도 하나의 back edge 를 가지고 있다.<br/>
  back edge 가 주어지면, 엣지의 헤드를 거치지 않고 엣지의 꼬리에 도달할 수 있는 모든 노드를 취함으로써 natural loop 를 구성할 수 있다.<br/>
  서로 다른 헤더를 가진 두 개의 natural loop는 서로 분리되거나 한 루프가 다른 루프로 완전히 포함된다; 이 사실은 natural loop 로 간주되는 한 중첩루프의 계층에 대해 말 할 수 있게 한다.<br/><br/>

* 깊이 우선 순서는 반복 알고리즘(iterative algorithm)을 효율적으로 만든다
  * 반복 알고리즘은 비순환 경로를 따라 정보가 충분히 전달되는 한 몇 번의 패스를 필요로 한다. 즉, 사이클은 아무것도 추가하지 않는다.<br/>
    깊이 우선 순서에 따라 노드를 방문하면, 정보를 앞으로 전파하는 데이터 흐름 프레임워크(예:reaching definitions)는
  정보를 앞으로 전달하면 모든 비순환 경로에서 2 + 가장 많은 수의 retreating edges 만큼 수렴한다.<br/>
  깊이 우선 순서의 리버스(후위 순회)로 방문할 경우 live variable 같은 backward-propagating frameworks 마찬가지다.<br/><br/>

* Region
  * 리전은 리전의 모든 노드를 지배하는 헤더 h를 가진 노드와 엣지의 집합이다.<br/>
  리전에 있는 h 이외의 노드의 이전 노드도 리전에 있어야 한다.<br/>
  리전 엣지는 헤더에 들어가는 일부 또는 전체를 제외하고 리전의 노드 사이를 이동하는 모든 것이다.<br/><br/>

* Regions and Reducible Flow Graphs
  * 축소 가능한 flow graph 는 리전의 계층구조로 parse 될 수 있다.<br/>
  이러한 리전은 헤더로 들어가는 모든 엣지를 포함하는 loop regions 또는 헤더로 들어가는 엣지가 없는 body regions 이다.<br/><br/>

* Region-Based Data-Flow Analysis
  * Data-Flow Analysis 에 대한 반복적인 접근의 대안은 리전 계층을 위아래로 작동하고, 각 리전의 헤더에서 해당 리전의 각 노드로 transfer functions 을 계산하는 것이다.<br/><br/>

* Region-Based Induction Variable Detection(리전 기반 유도 변수 감지)
  * Region-Based analysis 의 중요한 application 은 루프 주변 횟수의 affine(선형) function 값을 갖는 loop region 의 각 변수에 대한 공식을 계산하려고 시도하는 데이터 흐름 프레임워크에 있다.<br/><br/>

