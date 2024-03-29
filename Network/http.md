## 💡 http 란
http란 서버/클라이언트 모델에 따라 데이터를 주고받기 위한 프로토콜이다.
즉, http는 인터넷에서 하이퍼텍스트를 교환하기 위한 통신 규약으로 80번 포트를 사용하고 있다.

상태를 가지고 있지 않은 stateless 프로토콜이며, method, path, version, header, body 등으로 구성된다.

-----
</br>

## 💡 http의 문제점
- http는 평문 통신이기에, 도청이 가능하다
- 통신 상대를 확인하지 않기 때문에 위장이 가능하다. 상대가 접근 허가된 자인지 확인할 수 없고, 의미없는 request도 수신하여 Dos공격을 방지할 수 없다.
- 완전성을 증명할 수 없기 때문에 변조가 가능하다. 완전성이란 정보의 정확성을 의미한다. request나 response가 발신된 후에 누군가에 의해 변조되더라도 이 사실을 알 수 없다.
- 동일한 클라이언트의 요청에 대해 매번 새로운 연결을 해야 하므로 오버헤드가 발생할 수 있다.

-----
</br>
