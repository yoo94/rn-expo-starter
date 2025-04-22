### props는 interface로 하자

** 타입과의 차이 **

1. 확장(Extend) 방식

- interface는 extends 키워드를 사용하여 확장할 수 있습니다.
- type은 &(intersection) 연산자를 사용하여 여러 타입을 결합할 수 있습니다.

2. 객체와 기타 타입 정의

- interface는 주로 객체 타입을 정의하는 데 사용됩니다.
- type은 객체뿐만 아니라 유니언 타입, 튜플, 맵핑 타입 등을 정의할 수 있습니다.

3. 중복 선언 가능 여부

- interface는 동일한 이름으로 여러 번 선언하면 자동으로 합쳐집니다(Declaration Merging).
- type은 동일한 이름으로 중복 선언할 수 없습니다.
