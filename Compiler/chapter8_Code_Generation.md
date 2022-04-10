# Chapter8 Code Generation 요약 

--------------------------------------------

* 코드 생성은 컴파일러의 마지막 단계이다.<br/>
코드 생성기는 프론트 엔드 또는 코드 최적화 단계에 의해 생성된 중간 표현을 타겟 프로그램에 매핑한다.<br/><br/>
* 명령어 선택은 각 IR statement 에 대한 target-language instructions 를 선택하는 프로세스다.<br/><br/>
* 레지스터 할당은 레지스터에 보관할 IR values 값을 결정하는 프로세스다.<br/><br/>
* graph coloring 은 컴파일러에서 레지스터 할당을 수행하는데 효과적인 테크닉이다.<br/><br/>
* 레지스터 할당은 주어진 IR value 를 가지고 있어야 하는 레지스터를 결정하는 과정이다.<br/><br/>
* 제타겟 가능한(retargetable) 컴파일러는 여러 명령 집합에 대한 코드를 생성할 수 있는 컴파일러이다.<br/><br/>
* 가상 머신(Virtual Machine)은 자바와 C#과 같은 언어를 위해 만들어진 bytecode 중간 언어의 인터프리터이다.<br/><br/>
* CISC machine 은 비교적 적은 레지스터, 여러 개의 레지스터 클래스, 복잡한 complex addressing modes 를 가진 variable-length 명령어를 가진  일반적인 two-address machine 이다.<br/><br/>
* RISC machine 연산이 이루어지는 레지스터를 많이 가진 일반적인 three-address machine 이다.<br/><br/>
* 기본 블록(basic block)은 제어 흐이 블록의 첫 번째 statement 에서만 들어가고 기본 블록의 마지막 statement 를 제외하고 정지하거나 분기하지 않고 마지막 statement 에서만 나갈 수 있는 연속된 three-address statements 의 최대 시퀀스이다.<br/><br/>
* flow graph 는 그래프의 노드가 기본 블록이고 그래프의 엣지가 블록들 사이에서 어떻게 제어가 흐를 수 있는지를 보여주는 그래픽 표현이다.<br/><br/>
* flow graph 에서 loop 는 loop entry 라고 하는 single entry point 를 가진 강하게 연결된 영역이다.<br/><br/>
* 기본 블록의 DAG(Directed Acyclic Graph) 표현은 DAG의 노드가 블록 내의 statements 를 나타내고 각 자식 노드가 statement 에서 사용된 피연산자의 마지막 definition 인 statement 에 대응하는 directed acyclic graph다.<br/><br/>
* 핍홀 최적화(Peephole optimization)는 일반적으로 sliding window 을 통해 프로그램에 적용할 수 있는 local code-improving transformations 이다.<br/>
  * sliding window 알고리즘 : 일정한 범위를 가지고 있는 것을 유지하면서 이것을 이동 하는것 <br/><br/>
* 명령어 선택은 syntax tree를 tile 해서 사용되는 기계 명령어에 해당하는 트리 패턴인 tree-rewriting 프로세스에 의해 수행될 수 있다.<br/>
우리는 비용을 tree-rewriting rules 와 연관시키고 동적 프로그래밍을 적용하여 유용한 머신 클래스와 표현식에 대한 최적의 타일링을 얻을 수 있다.<br/><br/>
* Ershov number 는 임시 저장 없이 표현식을 평가하는데 필요한 레지스터 수를 나타낸다.<br/><br/>
* spill code 는 레지스터에 다른 값을 저장할 수 있는 공간을 만들기 위한 레지스터의 값을 메모리에 저장하는 명령어 순서이다.<br/>
  * spilling : 현재 실행 중인 프로그램에서 사용할 다른 변수를 위한 공간을 만들기 위해 레지스터 공간에서 주 메모리(RAM)로 변수를 이동시키는 기술
