### Enum Type

![](<https://images.velog.io/images/feelslikemmmm/post/c11a48ac-7ce8-40a5-b602-f1dd8d33e0a7/carbon%20(14).png>)

enum은 자바스크립트에는 없고 타입스크립트에만 있는 타입 입니다

자바와 같은 다른 언어에서는 보통 enum이라는 것이 있는데

예시를 조금 살펴보면 Animal 이라는 enum을 정의했고

안에는 Cat, Dog, Pig 3가지의 아이템이 있습니다

이 Animal과 안에 있는 아이템들은 각각 타입으로 사용할 수 있습니다

value1의 타입은 Animal로 정의했고 value2의 타입은 Animal이 아니라

Animal안에 있는 Cat과 Dog로 정의를 했습니다

그리고 Animal안에 있는 원소는 타입 뿐만 아니라 값으로도 사용할 수 있습니다

value1의 Animal.cat과 value2의 Animal.Dog 처럼 타입이 아니라 값으로 입력할 수 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/208ce4ce-0ce5-46ce-b89d-ee4969b3901c/carbon%20(15).png>)

enum의 첫번째 원소에 값을 할당하지 않으면 자동으로 0이 할당됩니다

enum의 각 원소에는 숫자 또는 문자열을 할당할 수 있는데요

명시적으로 값을 입력하지 않으면 이전 원소에서 1만큼 증가한 값이 할당됩니다

따라서 Pig는 5에서 1만큼 큰 6이 할당 됩니다

![](<https://images.velog.io/images/feelslikemmmm/post/d36dc7d9-a895-4a86-b03d-8018836204f1/carbon%20(16).png>)

위 예시는 이전 예시에서 작성했던 enum 코드를 컴파일 한 결과입니다

자세히 살펴보면 Animal 이라는 변수를 선언해서 객체를 할당하고

그리고 그 안에 값을 넣고 있는 것을 볼 수 있습니다

Cat은 0을 넣고 , Dog는 5를 넣고, Pig는 6을 넣고

그리고 다시 0에는 Cat을 넣고, 5에는 Dog, 6에는 Pig를 넣고 있는데요

이렇게 enum의 각 원소는 이름과 값이 양방향으로 맵핑이 됩니다

![](<https://images.velog.io/images/feelslikemmmm/post/abbb90ed-3b03-4f95-a1a3-99e1c6868944/carbon%20(18).png>)

앞서 살펴본것처럼 enum은 객체로 존재하기 때문에 해당 객체를 런타임에 사용할 수도 있습니다

지금은 dog를 출력하는 코드가 보이고 그 밑에는 Animal이라는 객체의 Dog 속성값을 출력하고 있습니다

사실 첫번째 콘솔로그와 두번째 콘솔로드 모두 같은 행동을 하고 있는 것이고

Animal의 5번 인덱스의 값도 출력을 해보면 5 5 pig가 나오는것을 알 수 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/717354ad-e116-4fe1-bffe-196ca580bf87/carbon%20(19).png>)

enum 아이템의 값은 숫자뿐만 아니라 문자열도 입력할 수 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/57aabdbf-71c6-451b-845a-c3dcf935ad01/carbon%20(20).png>)

enum 객체의 구조를 이해했다면 이런 유틸리티 함수를 작성할 수 있습니다

이 함수는 어떤 enum 객체에 특정 value가 있는지 검사하는 함수 입니다

먼저 enum 객체에서 모든 키를 뽑아낸 다음에 마지막에는 enum 객체 안에 입력된 value가 있는지

검사하고 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/8ab1c33a-4c61-4647-8bb8-c997a61c3acc/carbon%20(21).png>)

enum을 사용하면 컴파일 후에도 enum 객체가 남아있기 때문에 번들 파일의 크기가

불필요하게 커질 수 있습니다 enum 객체에 접근하지 않는다면 굳이 컴파일 후에 객체로 남겨둘 필요는 없겠죠?

const enum 을 사용해서 컴파일 결과에 enum의 객체를 남겨놓지 않을 수 있습니다

![](<https://images.velog.io/images/feelslikemmmm/post/7cbb3c5c-7b61-44d9-9ed6-54731e0c2f2e/carbon%20(22).png>)

이 코드는 이전 코드를 컴파일한 결과입니다

enum 객체는 안보이고 사용한 값만 노출이 되고 있습니다

animal은 0으로 lang은 'ko'로 입력이 됐습니다

이렇게 const enum 을 사용하게 되면 enum 객체를 사용하지 않기 때문에 번들 크기를 줄일 수 있습니다

const emum을 사용하면 앞서 만들어봤던 유틸리티 함수를 사용할 수는 없습니다

이럴때 타입스크립트는 친절하게 에러메세지를 내보내줍니다.
