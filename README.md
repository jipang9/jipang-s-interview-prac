# jipang-s-interview-prac

1. 배열(Array)과 링크드리스트(Linked List) 의 비교 설명

  배열과 링크드리스트는 데이터를 저장하는 자료 구조의 종류 ( 공통점 )
  배열은 선언 시 배열 길이를 선언하기에, 고정된 크기를 갖는다, 링크드리스트는 유동적인 크기 ( 차이점 )
  배열은 메모리 속 연속된 형태로 저장되어있다. 그래서 중간 데이터를 삭제할 때, 해당 공간의 메모리가 낭비된다는 장점 -> 이를 해결하려면 shift와 같은 추가적인 작업 필요 
  링크드리스트는 포인터라는 개념을 통해 서로 연결되어있는 형태로 저장되어있음. 그래서 중간 데이터가 삭제 되더라도, 노드 간 포인터를 이용해 연결만 해주면 됨
  
  접근적 측면에서 바라보면 특정 요소에 접근할 때, 배열의 인덱스를 알 경우 O(1)의 시간 복잡도를 갖지만, 인덱스를 모른다면 O(N)의 시간 복잡도 (Random Access)
                                              링크드리스트는 항상 순차적으로 접근을 해야한다 그래서 O(N) (Sequential Access)

  사용적인 측면에서 바라보면 배열은 링크드리스트에 비애 접근이 용이하기에 데이터의 접근과 관련된 작업을 진행하는 부분에서 이점이 있다.
                           링크드리스트는 배열에 비해 삭제와 삽입과 같은 행위들에 이점이 있어서 이와 같은 작업을 진행하는 부분에 이점이 있다.
  

2. CORS란 무엇이고 어떻게 허용할 수 있나요?
  
   교차 출처 리소스 공유(Cross - Origin - Resource Sharing)이라는 의미를 가진 CORS는 추가 HTTP헤더를 사용해서 한 출처에 실행중인 웹 애플리케이셔닝 다른 출처의 선택한 자원에서 접근    할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제입니다. 
   이를 스프링 내부에서 허용하는 방법은 3가지가 있는데, 
   첫번째로 서블릿 필터(Servlet Filter)를 사용해 커스텀한 CORS를 설정하는 방법, 
   두 번째 방법은 WebMvcConfigure를 구현한 Configuration 클래스를 만들어서 addCorsMappings()를 재정의 해서 해결할 수 있습니다. 
   마지막으로 스프링 시큐리티(Spring Security)에서 CorsCOnfigurationSource를 이용해 Bean으로 등록하고 config에 추가하면 허용이 가능합니다.
   
3. 시간 복잡도와 공간 복잡도가 무엇인지 설명하시오

    시간 복잡도는 특정 문제를 해결하는데 걸리는 시간을 의미 하는데, 연산의 횟수를 세고 처리해야 할 데이터의 수 n에 대한 연산 횟수의 함수 T(n)을 만들어서 계산한다. 
    공간 복잡도는  특정 문제를 해결하는데 얼마나 많은 메모리를 사용하는 지 분석하는 방법이다.
    
4. 사용자 패스워드를 전송하고 보관하는 방법을 설명하시오
    
    내가 생각한 패스워드 보관 방법은 2가지이다. 평문 그대로 저장하거나, 암호화를 적용해서 저장하거나, 평문 그대로 저장하게 된다면 탈취 당할 위험이 매우 높다.
    그래서 일반적으로 후자인 암호화를 적용해서 저장하게 되는데 여러 암호화 방식 중 단방향 해쉬 함수를 사용해서 암호화를 진행한다. 
    입력 받은 평문을 여러 알고리즘을 통해 암호화 하게 되고, 이를 저장하는 방식인데 이 방식 역시 안전하지 못한 단점이 있다. 
    동일한 메시지는 동일한 다이제스트를 얻게 되는데,  다이제스트를 모아 리스트 형태로 만든 것을 레인보우 테이블이라고 한다. 
    그래서 이 테이블에서 패스워드를 유추할 수 있다. 또 무차별 대입 공격(부르트포스)에 노출되어 있는데 시간만 있으면  하나 하나 대입을 통해 찾을 수 있다. 
    그래서 보완하기 위해 키 스트레칭 방식과 솔트 방식을 이용해 암호화의 보안성을 높일 수 있다.
    
5. 스택, 큐에 대해 설명해주실 수 있을까요?

    스택과 큐는 선형 자료구조의 종류입니다. 그러나 자료를 담고, 빼내는 부분에 있어서 명확한 차이를 보입니다. 우선 스택 경우엔 LIFO인 후입선출의 구조를 갖고 있습니다. 
    그래서 가장 최근에 들어온 데이터가 가장 먼저 나가게 되며 주로 출력 순서가 입력 순서의 역순으로 이루어져 있는 영역에서 주로 사용합니다.
    큐는 스택과 다르게 FIFO인 선입선출의 구조를 갖고 있습니다. 
    이는 가장 먼저 들어간 데이터가 가장 먼저 나간다는 의미를 갖는데 순차적인 작업이나 실행/사용하기 위해 대기 시킬 때 주로 사용합니다.
    
6.  DI와 IoC에 대해 아는 만큼 설명해주실 수 있을까요?
    
    DI는 의존성 주입 혹은 의존관계 주입이라는 의미를 갖고 있는데, 다른 프레임워크와 차별화 된 Spring의 기능입니다. 
    이는 객체를 직접 생성하는 것이 아니라 외부에서 생성한 후 주입 시키는 방식을 말하는데, Bean 정보를 바탕으로 의존관계를 컨테이너가 자동으로 연결해주는 것입니다. 
    그래서 모듈간 결합도도 낮아지고 유연성이 높아지는 장점이 있습니다. 이 의존성 주입에는 3가지 방법이 있는데 생성자 주입, Setter주입, Interface 주입이 있습니다.
    IoC는 제어의 역전이라는 뜻을 가집니다. 필드에 관한 제어권을 외부로 넘기는 것인데, 역할과 책임의 분리를 통해 객체 지향이 추구하는 원칙을 잘 지키고자 IoC가 필요합니다. 
    이를 통해서 응집도는 높이고 결합도는 낮추며 변경에 유연한 코드가 작성가능하기 때문입니다
    
    
7. hibernate란?

    하이버 네이트는 자바(Java)를 위한 ORM 프레임워크 입니다. 이 하이버 네이트는 JPA의 구현체로 JPA 인터페이스를 구현하며 내부적으로 JDBC API를 사용합니다. 

    hibernate의 장점은 다음과 같습니다.

    - 생산성
        - SQL문을 직접 사용하지 않고, 메서드 호출을 이용한 쿼리문 수행, 이로 인해서 개발자의 생산성이 향상됩니다 ( 왜? 직접 쿼리를 짜지않아도 되니까 )
    - 유지보수
        - 컬럼이 변경되거나 관련 작업에 관한 SQL의 수행을 대신 해줍니다. 그래서 유지보수가 쉬워집니다.
    - 특정 벤더에 종속적이지 않는다 ( 특정 DB에 종속적이지 않다는 말 )
    - JPA는 추상화된 데이터 접근 계층을 제공해서 특정 벤더에 종속적이지 않습니다.
    - 설정파일에 DB만 알려주면 사용가능 하다는 점.
    - 이로인해 재사용성이 늘어났다.
    - 패러다임 불일치
        - 객체와 RDB 사이의 패러다임 불일치를 해결할 수 있습니다.

   hibernate의 단점은 다음과 같습니다.

    - DB를 설계할 수 있는 능력이 필요함
    - 복잡한 쿼리나 통계에 필요한 쿼리는 Native SQL로 작성해야하는 경우가 생김 ( 메서드 호출만으로 완벽하게 데이터를 가지고오지 못함, 그래서 JPQL 지원 및 NativeQuery 지원)
    - 메서드 호출을 통해 SQL을 사용해서 직접 SQL을 작성하는 것보다 성능상으로 좋지 못함

    일단 하이버 네이트를 사용할 경우 객체에 비즈니스 책임을 위임할 수 있습니다.
    객체를 불러올 때 연관된 객체를 같이 들고와서 SQL에 의존적이지 않은 개발이 가능하다. 이말은 SQL 중심이 아닌 객체 중심의 개발이 가능하다.
    
8. call by reference란 무엇이고 보통 어떻게 쓰이나요?

    Call by reference는 참조에 의한 호출을 말합니다. 함수가 호출될 때, 메모리 공간 안에서는 함수를 위한 별도의 임시 공간이 만들어 지는데, 이 공간은 함수가 종료되면 사라집니다. 
    함수를 호출 할 때 인자로 전달되는 변수의 레퍼런스를 전달하는데 함수 안에서 인자 값이 변경되면 argument로 전달된 객체의 값도 변경됩니다. 
    자바에서는 새롭게 지역 변수를 만들어서 값만 복사하고 할당하기에 Call by value 즉 값에 의한 참조를 기본으로 하고있습니다.
    
