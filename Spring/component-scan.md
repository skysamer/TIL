## 💡 component-scan 개요
component-scan이란, bean으로 등록 될 준비를 마친 클래스들을 스캔하여, bean으로 등록해주는 것이다.
@Contorller, @Service, @Repository, @Component 어노테이션을 붙인 클래스들이 빈으로 등록 될 준비가 딘다.

component-scan은 기본적으로 @Component 어노테이션을 bean 등록 대상으로 포함한다.
@Controller나 @Service 어노테이션은 @Component를 포함하고 있기 때문에 이 어노테이션도 자동으로 인식된다.

<br>
---

## 💡 사용방법
component-scan을 사용하는 방법은 xml 파일에 설정하는 방법과, 자바파일안에서 설정하는 방법이 있다.

~~~xml
<context:component-scan base-package="com.ex.domain"/> 
~~~
다음과 같이 xml 파일에 설정하고, base package를 적어주면 클래스들을 스캔하여 빈으로 등록한다.
등록된 패키지를 포함하여 하위의 패키지안에 있는 클래스들이 모두 등록된다.

특정한 객체만 빈으로 등록하여 사용하고 싶다면 **include-filter**나 **exclude-filter**를 통해 설정할 수 있다.

~~~xml
<context:component-scan base-package="com.ex.domain">
    <context:exclude-filter type="annotation" 
        expression="org.springframework.stereotype.Controller"/>
</context:component-scan>
~~~

<br>
---

## 💡 동작과정
component-scan 설정을 파싱한다
base-package에 설정한 패키지를 기준으로
componentScanAnnotationParser가 스캔하기 위한 설정을 파싱한다.

                         ⬇
                          
base-package 설정을 바탕으로 모든 클래스를 로딩한다

                         ⬇
                          
ClassLoader가 로딩한 클래스들을 BeanDefinition으로 정의한다.

                         ⬇

정의를 토대로 빈을 생성한다.

<br>
---
