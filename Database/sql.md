## 💡 DDL(데이터 정의 언어, Data Definition Language)
데이터를 정의할 때 사용하는 언어로, 테이블을 만들때 사용하는 create나 테이블을 제거할 때 사용하는 drop 등이 해당한다.

- CREATE : schema, table, view, index를 생성
- ALTER : 테이블에 대한 정의를 변경하는데 사용
- DROP : schema, table, view, index를 삭제

-----
</br>

## 💡 DML(데이터 조작 언어, Data manipulation Language)
데이터베이스에 데이터를 저장할 때 사용하는 언어이다.

- SELECT : 테이블에서 조건에 맞는 데이터를 검색
- INSERT : 테이블에 새로운 데이터를 삽입
- DELETE : 테이블에서 조건에 맞는 데이터를 삭제
- UPDATE : 테이블에서 조건에 맞는 데이터를 변경

-----
</br>


## 💡 DCL(데이터 제어 언어, Data Control Language)
데이터베이스에 대한 접근 권한과 관련된 문법으로, 어느 유저가 데이터베이스에 접근할 수 있는지 권한을 설정한다.

- COMMIT : 명령에 의해 수행된 결과를 실제 물리적 디스크로 저장하고, 데이터베이스 조작 작업이 정상적으로 완료되었음을 관리자에게 알려줌
- ROLLBACK : 데이터베이스 조작 작업이 비정상적으로 종료되었을때, 원래의 상태로 복구함
- GRANT : 데이터베이스 사용자에게 사용 권한을 부여함
- REVOKE : 데이터베이스 사용자의 권한을 취소함

-----
</br>

## 💡 DQL(Data Control Language)
정해진 스키마 내에서 쿼리할 수 있는 언어로, select가 대표적인 DQL에 해당하며, DQL을 DML의 일부로 취급하기도 함

- SELECT : 테이블 내의 데이터를 조회할 때 사용
- WHERE : 테이블에 저장된 데이터 중, 원하는 데이터만 선택적으로 추출할 때 사용
- GROUP BY : 해당값을 그룹화하여 출력한다.
- ORDER BY : 특정 컬럼을 기준으로 순서대로 나열한다.

-----
</br>


## 💡 TCL(Transaction Control Language)
DML을 거친 데이터의 변경사항을 수정하는 언어다.
DCL에서 COMMIT과 ROLLBACK을 따로 TCL로 표현한다.

- COMMIT : 명령에 의해 수행된 결과를 실제 물리적 디스크로 저장하고, 데이터베이스 조작 작업이 정상적으로 완료되었음을 관리자에게 알려줌
- ROLLBACK : 데이터베이스 조작 작업이 비정상적으로 종료되었을때, 원래의 상태로 복구함

-----
</br>
