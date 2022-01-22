## 💡 개요
Java에서 불변 객체는 클래스의 인스턴스가 생성된 시점부터 내부 상태가 일정하게 유지되는 객체를 말한다.
한번 생성된 객체는 연산자 등의 변경을 시도해도 최초에 생성된 객체가 변하지 않는다.

반대로 가변 객체는 클래스의 인스턴스가 생성된 이후에도 내부 상태 변경이 가능한 객체이다.

두 객체는 멀티 쓰레딩 환경에서 차이를 보이는데, 전자는 멀티 쓰레드 환경에서 안전한 반면에 
후자는 멀티 쓰레드 환경에서 별도의 동기화 처리를 해주어야 한다.

-----
</br>

## 💡 String / StringBuffer / StringBuilder
String 클래스는 대표적인 불변객체이다. String 객체를 생성할 경우, String Pool에서 먼저 객체의 주소값이 생성된다.

반면에 StringBuffer와 StringBuilder 클래스는 가변 객체이다. String 객체는  char[] field라는 내부 value값이 final로 선언되어 있지만,
StringBuffer와 StringBuilder 클래스는 final로 선언되어 있지 않다.

-----
</br>

## 💡 StringBuffer / StringBuilder
StringBuffer클래스는 멀티 쓰레드 환경에서 안전하도록 모든 메서드에 synchronize 처리가 되어있다.
즉 멀티 쓰레드 환경에서 안전하게 사용하기 위해서는 StringBuilder보다는 StringBuffer를 사용해야 한다.

-----
</br>
