### 배열 (Array)

TypeScript는 JavaScript처럼 값들을 배열로 다룰 수 있게 해주는데요, 배열 타입은 두가지 방법으로 사용할 수 있습니다

첫번째는 나타내는 타입 뒤에 [] 를 쓰는 방법입입니다

![](<https://images.velog.io/images/feelslikemmmm/post/90910028-eb13-47f2-a5e6-39d4abe2d6ef/carbon%20(55).png>)

각각 가지고 있는 데이터에 따라서 정해진 타입을 적고 그 뒤에 [] 를 통해서 타입을 지정해줄 수 있습니다

두번째 방법은 제네릭 배열 타입을 사용하는 것인데요,

이 포스팅에서는 간단한 예시만 살펴보고 제네릭은 따로 다루겠습니다.

![](<https://images.velog.io/images/feelslikemmmm/post/7bdee8d6-b740-4555-81d0-e10743a67151/carbon%20(56).png>)

Array 라고 작성하고 <> 기호 안에 타입을 적어주면 됩니다.

readonly 라는 속성을 이용해서 전달 된 인자를 함수 내부에서

변경하지 못하게 타입을 보장할 수 있습니다

오브젝트에서 불변성을 유지하는 것은 매우 중요합니다

그렇기 때문에 readonly 속성이 자주 사용됩니다

제네릭 배열 타입(Array<>)은 readonly를 사용할 수 없기 때문에

일반적으로 첫번째 방법인 타입 뒤에 [] 를 쓰는 방법을 많이 사용합니다

### 튜플 (Tuple)

서로 다른 타입을 함께 가질 수 있는 배열 입니다

튜플 타입을 사용하면, 요소의 타입과 개수가 고정된 배열을 표현할 수 있습니다

단 요소들의 타입이 모두 같을 필요는 없습니다

![](<https://images.velog.io/images/feelslikemmmm/post/db0750aa-096d-4ee8-b3ce-84d09f5d24c0/carbon%20(57).png>)

예시처럼 배열의 각 인덱스에 0번은 string, 1번은 number 타입으로 각 요소마다 다른 타입을 선언할 수 있습니다

그리고 초기화 할때 각 인덱스에 맞는 타입을 넣지 않으면 에러가 발생합니다

![](<https://images.velog.io/images/feelslikemmmm/post/e12d5e14-3520-4d16-a64e-cc564e6d7692/carbon%20(59).png>)

정해진 인덱스에 위치한 요소에 접근하면 해당 타입이 나타나게 됩니다

person[1]은 number 타입이기 때문에 str 메서드를 사용하려고 하면 에러가 발생하는 것을 볼 수 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/9a085f10-7271-485d-9b51-bce747b46eed/carbon%20(60).png>)

정해진 인덱스 외에 다른 인덱스에 있는 요소에 접근하면, 오류가 발생하며 실패합니다.

튜플은 권장되는 사용 방법은 아닙니다

그 이유는 데이터에 접근할 때 인덱스에 접근하는 것은 가독성이 떨어지며 값을 출력하거나

데이터를 정의한 곳으로 가는 것이 아니면 인덱스에 어떤 데이터가 들어있는지 확인하기가 불편하기 때문입니다

튜플을 사용할 수 있는 곳에는 interface나 type alias, class 로 대체해서 사용하는 것이 좋습니다

튜플을 사용할때 obeject의 Destructuring을 사용하면 불편한 방법을 피할수는 있지만

데이터를 사용하는 곳에서 임의의 이름을 지정해서 사용해야 하는 단점이 있습니다
