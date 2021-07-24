## Constrains

제네릭에 조건을 줄 수 있는 Constrains에 대해서 알아보겠습니다

### 제네릭 제약조건 (Generic Constraints)

특정 타입들로만 동작하는 제네릭 함수를 만들고 싶을 수 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/d9bd09bc-e08a-44c6-b3c5-7f4645d729f8/carbon%20(96).png>)

예제를 살펴보면 arg.length에 접근하려고 했지만 컴파일러는

모든 타입에서 .length 타입을 가지고 있다는 걸 증명할 수 없기 때문에 경고가 발생합니다

현재 any와 같은 모든 타입에서 동작하는 것 대신에

.length 프로퍼티가 있는 모든 타입들에서 작동하는 것으로 제한을 두고 싶다고 예를 들어보겠습니다

현재 우리가 원하는 arg 의 타입은 무엇이든 허용하지만 최소한 .length가 있어야 합니다

그렇게 하려면 T 가 무엇이 될 수 있는지에 대한 제약 조건을 나열해야 하는데요

이를 위해서 우리의 제약 조건을 명시하는 인터페이스를 만들수 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/f01906b0-0731-4c0c-bf64-d0161988af65/carbon%20(98).png>)

Lengthwise 라는 length를 가진 인터페이스를 생성하였구요

extends 키워드로 표현한 인터페이스를 이용해 loggingIdentity 함수에 명시했습니다

loggingIdentity 제네릭 함수는 이제 제한되어 있기 때문에 모든 타입에 대해서는 동작하지 않습니다

![](<https://images.velog.io/images/feelslikemmmm/post/a3ae5119-46c9-4eb2-9b23-f2b55617bbe0/carbon%20(99).png>)

loggingIdentity 함수에 인자로 3을 전달했는데요

number 타입은 .length 속성이 없기 때문에 오류가 발생하게 됩니다

이처럼 제네릭도 조건들을 걸어둠으로써 조금 더 제한적인 범위 내에서 일반화 된 제네릭을 이용할 수 있습니다.
