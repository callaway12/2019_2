# 복습문제
* 데이터베이스 설계에서 주된 단계들을 말해 보시오. 각 단계의 목표가 무엇인가? 어느 단계에서 ER 모델이 주로 사용되는가?
    1. 요구분석
        - 어떤 데이터들을 어떻게 분류하고 응용위에 구축할건가
    2. 개념적 데이터베이스 설계
        - 여기서 ER 모델, 
        - 각 데이터들의 제약조건과 관게 생성
    3. 논리적 데이터베이스 설계
        - DBMS 모델에 따른 DB 스키마 생성
    4. 스키마 정제
        - 스키마에 있는 관계들을 분석, 문제점 보완
    5. 물리적 데이터베이스 설계
        - DB설계 성능기준 구축, 에티블 인덱싱
    6. 응용 및 보안설계
        - 보안 
    
* 다음 용어들을 정의하시오: 개체, 개체집합, 애트리뷰트, 키
    - 개체
        + 개체는 각각의 데이터들
        - 다른 *객체*들로부터 구분될 수 있는 객체이다
    - 개체집합
        + 비슷한 개체들끼리의 집합
        - 같은 종류의 개체들을 하나의 집합으로 식별
    - 애트리뷰트
        + 개체들이 갖는 특성들
        - 하나의 개체는 애트리뷰트 집합을 갖는다
        - 주어진 개체 집합에 속한 모든 개체들을 동일한 애트리뷰트들을 갖는다
        - 이것이 같은 종류가 의미하는 것.
    - 키
        + 각 개체들을 구별하는 특성의 최소집합
        - 주어진 집합에 속하는 한 개체를 유일하게 식별하는 값을 갖는 최소개의 애트리뷰트들로 이루어진 집합
* 다음 용어들을 정의하시오: 관계, 관계집합, 기술하는 애트리뷰트
    - 관계
        - 둘 이상의 개체들 사이의 관련성
    - 관계집합
        - 같은 종류의 관계들을 하나의 관계 집합
    - 기술하는 애트리뷰트
        - 관계 집합에서 튀어나온 애트리뷰트
        - 관계에 관한 정보를 기록하기 위해 사용
* 다음의 제약 조건들을 정의하고 각각의 예를 들어보시오: 키 제약조건, 참여 제약조건, 제약개체는 무엇인가? 클래스 계층은 무엇인가? 집단화는 무엇인가? 이러한 ER 모델의 설계 구성자들의 각각을 필요로 하는 예제 시나리오를 만들어 보시오.
    - 키 제약조건
        + 어떤 개체들간의 관계 제약
        + 부서는 한명의 관리자가 필요하다
    - 참여 제약조건
        + 부분참여, 전체참여
        + 각 직원은 적어도 한 부서에서 근무하고 각 부서에는 적어도 한명의 직원이 근무한다.
        + 전체 참여 -> 그래서 굵은 실선
        + 모든 부서는 관리하는 직원이 한명 있다
        + 부분 참여 -> 얇은 실선
    - 제약개체
        + 약개체는 다른 개체의 pk에 의해서만 구분되는 것
        + 보험증권은 그것을 관리하는 직원에 의해서만 
        + 즉, 원 주인 개체가 없어지면 없어지는 개체집합
    - 클래스 계층
        + ISA 관계
        + 직원은 파트타임, 정규직
        + 중첩 제약조건
            - 파트타임 정규직 둘다 하는 사람
        + 포괄 제약조건 
            - 둘다 포함 하지 않는 사람
    - 집단화
        + 개체들의 모임과 관계들의 모임간에 관계를 설정
        + 학생들과 전공 부서들간의 관계를 전체를 관리하는 교수 개체집합
* ER 설계를 할 때 다음의 선택을 위해 무슨 지침들을 사용할 것인가?
    - 애트리뷰트 혹은 개체집합
        + 직원들의 주소를 그냥 직원의 애트리뷰트로 (이경우 그냥 주소가 몽땅 들어감)
        + 직원들과 주소를 관계를 통해 주소 자체를 개체로 (이경우 주소의 디테일하게 국가 시 구 동 등으로 구체화해서 저장하여 어디 도시에 사는 모든 직원들 이렇게 추출이 가능)
    - 개체 혹은 관계집합
        + 부서의 총 예산과 그것을 관리하는 직원을 관게 어트리뷰트 (그 직원이 관리하는 여러 부서의 총 예산을 산정하기 어려움)
    - 이진 혹은 삼진관계, 혹은 집단화 
        + 관계집합과 개체집합을 관련시키는 관계의 존재에 의하여 주로 결정됨
        + 삼진관계와 그 이상의 관계에서 조심해야할 점은 그 관계를 통한 3개 이상의 개체 집합들과의 관계들이 모두 동일해야함,
        + 하나의 프로젝트는 여러 부서에 의해 자금지원을 받을 수 있고 한 부서는 여러 프로젝트들을 자금 지원할 수 있으며 각 자금지원 관계는 한명 이상의 직원들에 의해 감독될 수 있다. 
        + 하지만각 자금지원 관계가 많아야 한 명의 직원에 의해 감독되는 제약조건에는 표현 불가능, -> 집단화를 통해 해결해야함

        