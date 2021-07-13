### 유니언 타입 (Union Types)

Union Type은 타입을 구성할 수 있는 방법 중 하나인데요

쉽게 말하면 or 라고 생각할 수 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/57017803-a529-4a61-b505-45c2b4853ea9/carbon%20(75).png>)

padLeft의 인자 padding의 타입을 | 기호를 이용해서 string, number, boolean 으로 정의 했습니다

모든 가능한 케이스 중에 발생할 수 있는 단 하나를 담을 수 있는 타입을 만들때 이 유니언 타입을 사용합니다

### 공통 필드를 갖는 유니언 (Unions with Common Fields)

유니언 타입인 값이 있으면, 유니언에 있는 모든 타입에 공통인 멤버들에만 접근할 수 있습니다.

![](<https://images.velog.io/images/feelslikemmmm/post/192e63ad-7724-4676-ac7d-055c2b546305/carbon%20(77).png>)

만약 값이 A | B 인 타입을 갖고 있으면, 확신할 수 있는 것은

그 값이 A 와 B 둘 다 가지고 있는 멤버들을 가지고 있다는 것 뿐인데요,

위 예시에서 Bird 는 fly 라는 멤버를 가지고 있습니다

그리고 아래 변수 pet은 Bird 혹은 Fish 타입이 지정되어 있습니다

이 시점에서 pet 변수가 Bird인지 Fish인지 아직 알 수가 없습니다

Bird 와 Fish의 공통 멤버인 layEggs는 호출이 가능하지만

Bird 와 Fish가 각각 가지고 있는 멤버는 호출이 불가능합니다

그래서 pet.swim()을 호출하려고 하면 에러가 발생합니다

> pet.swim()을 호출하자 에러가 발생하는 모습
> ![](https://images.velog.io/images/feelslikemmmm/post/a28169a3-f979-40dc-be9f-9cfb6f917afa/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-07-01%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.14.57.png)

### 유니언 구별하기 (Discriminating Unions)

유니언을 사용하는데 있어서 일반적인 기술은 타입스크립트가 현재 가능한 타입 추론의 범위를 좁혀나가게 해줄 수 있는 리터럴 타입을 갖는 단일 필드를 사용하는 것인데요,

하나의 공통 필드를 가지고 있는 세 가지의 유니언을 만들어보겠습니다
![](<https://images.velog.io/images/feelslikemmmm/post/13a4b048-251d-49f6-9b10-e09ce81a9883/carbon%20(78).png>)

위 loading, failed, success 3가지 타입은

모두 state 라는 공통 필드를 가지고 있고, 타입마다 각자의 필드도 가지고 있습니다

그리고 이 3가지 타입을 모두 가지고 있는 NetworkState 타입이 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/10f09a28-440e-43e4-a359-aa6bad412aaa/carbon%20(79).png>)

위 예시에서 netWorkStatus 함수안에서 state.code 부분은 에러가 발생하게 됩니다

그 이유는 3가지의 타입 중 어떤 타입으로 결정될지 코드를 작성하는 시점에서는 알수가 없기 때문입니다

그 아래 코드처럼 switch 문을 사용해서

각 케이스 별로 유니언 타입을 좁혀나가는 방법을 사용할 수 있습니다
