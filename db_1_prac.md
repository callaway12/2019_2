## 연습문제
* 1.1 운영체제 파일에 데이터를 간단히 저장하는 대신 데이터베이스 시스템을 선택하는 이유는 무엇인가? 어떤 경우에 데이터베이스 시스템을 사용하지 *않는* 것이 타당한가?
    - DB는 보통 너무 큰 덩치여서 메인메모리가 아닌 세컨더리 메모리에 저장이 된다. 디스크나 테이프 등,. OS의 파일에 저장될 수 있고, 혹은 DBMS에 저장될 수 있다.
        + 데이터 독립성
        + 효율적 접근
        + 응용프로그램 개발 시간 단축
        + 데이터 무결성
        + 데이터 보안성
        + 데이터 관리
        + 동시접속
        + crash recovery

* 1.2 논리적 데이터 독립성이 무엇이며 왜 그것이 중요한가?
    - 논리구조에 대한 변화에 유저는 데이터에 영향을 끼치지 않는다. 시설-공개, 시설-비밀, 이렇게 되면 오피스 번호나 이름 이렇게는 공개로 들어가도 연봉은 비밀에 들어가면서 user의 view 에서는 통합하여 보여주는 곳에서는 공개, 비밀 둘다 합쳐서 보여주는데, 이때 비밀이나 공개에서 바뀌는 데이터 값에 대해서 user view에서는 이 관계에 대해 무관하게 언제든지 바뀌어 출력된다.
    Thus, application programs that refer to Students need not be changed when the relation Stu- dents is replaced by the other two relations. The only change is that instead of storing Students tuples, these tuples are computed as needed by using the view definition; this is transparent to the application program.

* 1.3 논리적 데이터 독립성과 물리적 데이터 독립성의 차이점을 설명하시오.
    - 