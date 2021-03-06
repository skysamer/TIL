## 1. IoC(Inversion of Control) 개요
스프링은 **제어의 역행(IoC, Inversion of Control)** 을 통해 애플리케이션을 구성하는 객체 간 낮은 결합도를 유지한다.

IoC가 적용되기 전에는 애플리케이션 수행에 필요한 객체의 생성이나 객체와 객체 사이의 의존관계를 개발자가 직접 자바 코드로 처리했었다. 
이런 상황에서는 의존관계에 있는 객체를 변경할 때, 반드시 자바 코드를 수정해야 한다.

하지만 IoC가 적용되면 객체 생성을 자바 코드로 직접 처리하는 것이 아니라 컨테이너가 대신 처리한다.
또한, 객체와 객체 사이의 의존관계 역시 컨테이너가 처리한다.
결과적으로 소스에 의존관계가 명시되지 않으므로 결합도가 떨어져서 유지보수가 편리해진다.

-----
</br>

## 2. IoC 컨테이너
컨테이너는 특정 객체의 생성과 관리를 담당하며 객체 운용에 필요한 다양한 기능을 제공한다.
컨테이너는 일반적으로 서버 안에 포함되어 배포 및 구동된다.
애플리케이션 운용에 필요한 객체를 생성하고 객체 간의 의존관계를 관리한다는 점에서 스프링도 일종의 컨테이너라고 할 수 있다.

컨테이너는 자신이 관리할 클래스들이 등록된 XML 설정 파일을 로딩하여 구동한다.
그리고 클라이언트의 요청이 들어오는 순간 XML 설정 파일을 참조하여 객체를 생성하고, 객체의 생명주기를 관리한다.

기존의 자바 기반으로 애플리케이션을 개발할 때, 객체를 생성하고 객체들 사이의 의존관계를 처리하는 것에 대한 책임은 
전적으로 개발자에게 있었다.

하지만 제어의 역행이라는 것은 이런 일련의 작업들을 컨테이너로 처리하는 것을 의미한다.
따라서 제어의 역행을 이용하면 소스에서 객체 생성과 의존관계에 대한 코드가 사라져 결과적으로 낮은 결합도의 컴포넌트를 구현할 수 있다.

대부분 IoC 컨테이너는 각 컨테이너에서 관리할 객체들을 위한 별도의 설정 파일이 있다.

-----
</br>

## 3. bean 설정
객체 생성을 위한 클래스를 등록할 때, bean 엘리먼트를 이용하게 된다.
<bean> 엘리먼트를 사용하는데 클래스 하나당 하나의 bean 설정이 필요하다.

bean 엘리먼트에서 중요한 것이 class 속성값이다. 여기에 패키지 경로가 포함된 전체 클래스 경로를 지정해야 한다.
이후에 객체를 변경할 때는 bean 엘리먼트에 작성되어 있는 클래스 경로만 변경하면 된다.
  
스프링 컨테이너는 bean 저장소에 해당하는 XML 설정 파일을 참조하여 bean의 생명주기를 관리하고 여러 가지 서비스를 제공한다.
스프링 설정 파일 이름은 beans를 루트 엘리먼트로 사용해야 한다.
  
-----
</br>

## 3. DI(의존성 주입)
스프링 프레임워크의 가장 중요한 특징은 객체의 생성과 의존관계를 컨테이너가 자동으로 관리한다는 점이다.
이것이 IoC의 핵심원리이기도 하다. 

스프링이 IoC를 지원하는 형태 중 하나인 dependency Injection은 객체 사이의 의존관계를 
스프링 설정 파일에 등록된 정보를 바탕으로 컨테이너가 자동으로 처리해준다.

-----
</br>



