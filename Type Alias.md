타입스크립트가 아름답고 강력한 이유는 첫번째로 Type Alias가 가능하기 때문인데요,

Type Alias는 타입 별칭이라고 부릅니다

타입 별칭을 이용하게 되면 기본적인 타입 정의부터 시작해서

굉장히 복잡하고 재밌는 타입들을 정의해 볼수가 있습니다

### 타입 별칭 (Type Aliases)

타입 별칭은 타입의 새로운 이름을 만듭니다. 타입 별칭은 때때로 인터페이스와 유사합니다만,

원시 값, 유니언, 튜플 그리고 손으로 작성해야 하는 다른 타입의 이름을 지을 수 있습니다.

![](<https://images.velog.io/images/feelslikemmmm/post/167d0b12-7f35-4f8d-a6fb-6faf3c078cb9/carbon%20(67).png>)

Str이라는 타입을 정의하고 문자열로 정의했습니다

userId 변수에 Str 타입을 선언하고 숫자를 값으로 할당하면 에러가 발생합니다

타입 별칭은 실제로 새로운 타입을 만드는 것은 아닙니다

그 타입을 나타내는 새로운 이름을 만드는 것이죠,

원시 타입은 물론이고 오브젝트 타입도 정의해줄 수 있습니다

원시 값의 별칭을 짓는 것은 문서화의 형태로 사용할 수 있긴 하지만, 사실 별로 유용하지 않습니다.

인터페이스처럼 타입 별칭은 제네릭이 될 수 있는데요

![](<https://images.velog.io/images/feelslikemmmm/post/4057091f-3149-42d6-b6f4-546057b5b65b/carbon%20(68).png>)

위 예시처럼 타입 매개 변수를 추가하고 별칭 선언의 오른쪽에 사용하면 됩니다

![](<https://images.velog.io/images/feelslikemmmm/post/3eb0056e-0798-4eb9-8c74-c66e181dcc68/carbon%20(69).png>)

프로퍼티 안에서 자기 자신을 참조하는 타입 별칭을 가질 수 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/ec060d33-e663-4075-b2de-1b734e808ab3/carbon%20(70).png>)

교차 타입과 같이 사용하면, 아주 놀라운 타입을 만들 수 있습니다.

![](<https://images.velog.io/images/feelslikemmmm/post/22e8079d-3b44-4eee-b7d7-556e6d2a7581/carbon%20(71).png>)

하지만, 위처럼 타입 별칭을 선언의 오른쪽 이외에 사용하는 것은 불가능합니다.

### 인터페이스 vs 타입 별칭 (Interfaces vs. Type Aliases)

위에서 언급한것처럼, 타입 별칭은 인터페이스와 같은 역할을 할 수 있는데요,

약간의 미묘한 차이가 있습니다

첫번째로는 인터페이스는 어디서나 사용할 수 있는 새로운 이름을 만들 수 있습니다

하지만 타입 별칭은 새로운 이름을 만들 수 없습니다

오류 메시지는 별칭 이름을 사용하지 않습니다.

![](<https://images.velog.io/images/feelslikemmmm/post/fb34b006-40d0-4ea6-ba55-7dd746b6e502/carbon%20(72).png>)

위 예시에서 interfaced에 마우스를 올리면 Interface를 반환한다고 보여주지만 aliased는 객체 리터럴 타입을 반환한다고 보여줍니다.

> TypeScript의 이전 버전에서, 타입 별칭은 extend 하거나 implement 할 수 없었습니다 (다른 타입을 extend/implement 할 수도 없습니다).
> 2.7 버전부터, 타입 별칭은 교차 타입을 생성함으로써 extend 할 수 있습니다.
> 예: type Cat = Animal & { purrs: true }.

소프트웨어의 이상적인 특징은 확장에 개방되어 있기 때문에, 가능하면 항상 타입 별칭보다 인터페이스를 사용해야 한다고 합니다

반면에, 만약 인터페이스로 어떤 형태를 표현할 수 없고 유니언이나 튜플 타입을 사용해야 한다면, 일반적으로 타입 별칭을 사용한다고 합니다.
