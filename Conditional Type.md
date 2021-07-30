### 조건부 타입 (Conditional Types)

타입에도 조건을 줄 수가 있습니다

TypeScript 2.8에서 조건부 타입을 도입했습니다

조건부 타입은 타입 관계 검사로 표현된 조건에 따라

두 가지 가능한 타입 중 하나를 선택합니다

![](<https://images.velog.io/images/feelslikemmmm/post/59f15f5e-5ee0-48d9-afc4-34ed2d04ab7a/carbon%20(82).png>)

위 예시의 타입은 T가 U에 할당될 수 있으면 타입은 X가 되고 그렇지 않다면 타입이 Y가 된다는 것을 뜻합니다.

![](<https://images.velog.io/images/feelslikemmmm/post/f0e2dbe8-a11a-441e-89bd-fa37430f1928/carbon%20(84).png>)

예시처럼 새로운 Type에 Conditional 타입을 사용해서 U를 주면 Type은 X가 됩니다.

조건부 타입 T extends U ? X : Y는 X나 Y로 결정되거나, 혹은 지연됩니다

왜냐하면 조건이 하나 혹은 그 이상의 타입 변수에 의존하기 때문인데요,

T나 U가 타입 변수를 포함할 때, X 또는 Y로 결정되거나 지연될지,

타입 시스템이 T가 항상 U에 할당할 수 있는지에 대해 충분히 정보를 가지고 있는지 여부로 결정됩니다

즉시 결정되는 일부 타입의 예제를 살펴보겠습니다

![](<https://images.velog.io/images/feelslikemmmm/post/2bbcc81c-b989-49b9-963e-54edb66699af/carbon%20(85).png>)

이번에는 중첩 조건부 타입을 사용하는 예제를 살펴봅시다

![](<https://images.velog.io/images/feelslikemmmm/post/0b415b21-2126-4f50-b894-490799aaba1c/carbon%20(87).png>)

위 예시처럼 T 라는 타입이 어떤것이냐에 따라 다른 타입을 지정할 수 있습니다.
