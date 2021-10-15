## 💡 PL/SQL(Procedure Language extension to SQL)
SQL을 확장한 절차적 언어이다.

관계형 데이터베이스에서 사용되는 Oracle의 표준 데이터 액세스로, 프로시저 생성자를 SQL과 통합한다.

PL/SQL의 종류는 크게 함수, 프로시저, 트리거로 이루어져 있다.

블록 단위의 실행을 제공하며, 이를 위해 BEGIN과 END를 사용한다. 마지막 라인에 '/'를 입력하면 실행된다.

변수, 상수를 선언할 수 있고, 조건문, 반복문 등의 제어문 또한 사용 가능하다.

### 1) DECLARE (선언부)
:PL/SQL에서 사용하는 모든 변수나 상수를 선언하는 부분이다.

### 2) BEGIN (실행부)
:절차적 형식으로 SQL문을 실행할 수 있도록 절차적 언어의 요소인 제어문, 반복문, 함수 정의 등 로직을 기술할 수 있는 부분이다.

### 3) EXCEPTION (예외 처리부)
:PL/SQL문이 실행 중 발생하는 에러를 처리하는 부분

### 4) END (실행문 종료)

블록내에서는 세미콜론(;)을 사용하여 한 문장씩 처리한다.
<br>
---

## 💡 프로시저
PL/SQL의 한 종류이다. 자주 사용하는 SQL구문을 프로시저로 등록하여 필요할때 마다 쓰는 기술이다.

함수의 경우 반환값이 존재하지만 프로시저는 반환값이 존재하지 않는다.

**사용 예**

```sql
CREATE OR REPLACE PROCEDURE STATISTICS_TRAFFIC_PROC
(
   변수명 IN 타입,
   변수명 IN 타입
)
IS
변수명 타입  := '변수값';

BEGIN

INSERT INTO tbl_statistics_traffic (date_key, R_NAME, section, datetime, TYPE_ONE, TYPE_TWO, TYPE_THREE, SUB_TOTAL)
VALUES (20201001, 경부선, 건천ic-기흥ic, 12343, 234, 23, 12456);
COMMIT;

END tbl_statistics_traffic;

```


프로시저를 실행할 때는 EXEC [프로시저명]을 입력하면 된다.

```sql

EXEC STATISTICS_TRAFFIC_PROC;

```

## 💡 스케줄러
스케줄러는 날짜 또는 시간에 맞춰 어떤 작업을 수행할 지 설정하는 기능이다.

스케줄러를 등록하려면 우선 스케줄러로 실행할 프로시저를 등록해야 한다.

