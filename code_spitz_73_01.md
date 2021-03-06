### 1강: 언어의 기본요소와 흐름 제어

* 프로그래머는
	* 복잡성의 관리가 가능해야
	* ‘모든 프로그램은 변한다.’ 변화에 기민한 코드를 짤 수 있어야

----

* 프로그램이란
: 컴퓨터 메모리에 실행할 수 있도록 적재된 상태  
: 이것을 짜는 행위 -> 프로그래밍  
: 짜는 사람 -> 프로그래머  

* 프로그램의 생명주기
     language code 렝귀지 코드(사람에 친절한 언어): lint time  
-> machine language 머신 렝귀지(컴퓨터가 이해할 코드) : compile time  
-> file 파일(컴파일된)   
-> load 적재(실행을 할 수 있도록)   
-> run 실행 : run time  
-> terminate 종료  
  
각 타임에 에러발견  
이 외에 컨텍스트 에러 -> 프로그램의 내용, 문맥 자체가 에러  
  
이러한 생애주기를 갖는 언어는 모든 코드를 검토, 검사함  
  
* 자바스크립트의 생애주기는,  
렝귀지 코드: lint time -> 파일 -> 적재 -> 머신 렝귀지 -> 실행: run time -> 종료  
  
부분적으로 컴파일 됨, 전체 검사되지 않음.  

---

* 복잡성에 대한 관리의 기본은 ‘격리’

---

* lexical grammer   
	- 제어문자 control character  
	: 한국어, 영어에는 등장하지 않음  
	- 공백문자  
	- 개행문자  
	- 주석  
	- 예약어  
	- 리터럴  
	: 언어에서 정의한 더이상 쪼갤 수 없은 단위, 값을 나타내는 최소한의 표현  
  
-> js 엔진이 코드를 요렇게 나눠서 해석  
  
---
language element  
* statements문  
: 자바스크립트 엔진이 어떻게 해석할 지 알려주는 hint, 실행되면 메모리에서 사라짐, 값으로 환원될 수 없음  
(ruby에서 if는 식 - 문/식은 언어 설계자가 정함)  
	* 공문: 빈 문 (e.g. ;), 인간의 실수 때문에 만들어진 스펙  
	* 식문: 하나의 식은 하나의 문이 됨 (e.g. 3 + 5;)  
	* 제어문:   
	* 선언문: identifier를 선언  
	* 단문: 하나의 문장  
	* 중문:  js는 {} 안의 여러 문장을 한 문장으로 간주    
  
* expression 식 (식, 인 것이다. ‘표현식’이라는 것은 잘못된 번역인 것이다.)  
: 단일한 값으로 수용	  
	* 값식: 하나의 값인 식(e.g. 4;)  
	* 연산식  
	: 연산자를 이용한 식  
		* 연산자의 목적에 따른 분류: 산술연산자, 논리연산자  
		* 연산자가 받아야할 항의 수로 분류:   
			* 단항연산자	  
			* 이항연산자 : 이항연산은 단항연산으로도 쓸 수 있음 (e.g. +3)  
			* 삼항연산   
			* 다항연산: (e.g. ,) a, b, c -> c  
	* 호출식: 함수의 호출도 return하는 하나의 값으로 귀결  
  
-> 값은 메모리에 저장하지 않으면 사라짐  
  
* indentifier 식별자  
	* 기본형(primative type)  
	: 값, 다른 메모리의 주소가 아닌 값, 복사되는 타입의 값, 복사하면 메모리 두 칸을 차지  
	: 자바스크립트의 기본형은 숫자, 문자, 불리언, undefined, null(외의 것은 모두 참조형)  
	* 참조형(reference type): 다른 메모리의 주소를 가리키는 값, 복사하면 하나의 메모리 칸을 씀  
	  
	* 변수: 메모리 주소의 별명, 값(data)의 타입정보를 가짐  
	-> typeof data, data type(자료형,은 오역)  
		: 변수에 들어가는 것은 값과 참조  
	* 상수:  한번 가진 값이 변하지 않음.  

----

노이만 머신이 메모리에 적재된 명령을 순서대로 실행하는 것을 flow라고 부름   
-> 동기화 sync: 적재된 프로그램이 한번에 소비되고 그 실행을 멈출 수 없는 형태, 그 명령을 ‘동기화 명령’이라고 함 

javascript의 흐름도 lr, 위에서 아래로  
할당만은 오른쪽에서 왼쪽으로  
-> 프로그래밍 언어는 수학자들이 만든 인공언어이기 때문  
-> 보편적이지 않은, 연산자 우선순위를 생각하게 되는 코드는 나쁜 코드  
-> 코드는 명시적으로 작성해야함  
  
sync flow 에서   
실행 중에 값에 따라 분기를 하고자 한다면, 노이만 머신의 흐름을 끊어야 함  
-> 이럴 때 쓰이는게 sync flow control(제어문)  
-> 한 세트의 flow: 루틴  
  
sub flow: 다음에 배울거예욥  
: main flow 실행 중 sub flow를 실행하다가 다시 main flow로 오게 하는 등의..  
: 반복적으로 사용하고 싶은 flow의 문/식을 조직화 하는 방법이 flow control  
: 서브루틴. 여러 번 실행 가능.  
: 코루틴 여러 번 실행하고 여러번 flow를 빠져나갈 수 있고, flow 끝까지 가지 않을 수 있는 flow  
-> 현대화 된 프로그래밍 언어에서 등장하는 흐름 제어  

---

제어문에 같은 표현이 여러가지가 존재하는 이유  
: 코드로 복잡한 문제를 표현하고자 하기 때문에  
: 코드를 읽는 사람이 의도를 파악할 수 있도록 하기 위함  

---

(js의 공백은 무한히 쓸 수 있음)  
js의 괄호는 우선순위, 제어문의 조건, 함수의 호출  
  
* if문  
: if문 뒤에 공백도 무한히 쓸 수 있음  
: if문의 문은 옵셔널, 선택적  
	* if문의 구조 
	: if 공백( 식 ) 단문;  
	: if 공백( 식 ) { 중문 }  
	* if else 문 
	: if else문의 문은 mandatory, 필수적. 둘 중 하나는 무조건 실행  
	:if ( 식 ) 문;  else 문;   
	: if ( 식 ) { 중문 } else { 중문 }  
  
-> if문에도 중요도의 의도를 담을 수 있음  

---
