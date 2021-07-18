## Type Inference

Type Inference는 타입추론이라고 부릅니다.

타입이 어디에서, 어떻게 추론되는지 알아보겠습니다.

### 기본 (Basic)

![](<https://images.velog.io/images/feelslikemmmm/post/fd6863ee-f0fb-49f5-9b30-f2edbfe92f02/carbon%20(61).png>)

변수 basic 의 타입은 number로 추론됩니다.

basic 변수에 타입을 할당하지 않았는데 변수를 정의함과 동시에

3 이라는 숫자를 할당하였기 때문에 자동으로 number 타입이 됩니다

이러한 추론은 변수와 멤버를 초기화하고, 매개 변수의 기본값을 설정하며,

함수의 반환 타입을 결정할 때 발생합니다

대부분의 경우에 타입 추론은 직관적입니다

### 최적 공통 타입 (Best common type)

여러 표현식에서 타입 추론이 발생할 때, 해당 표현식의 타입을 사용하여 "최적 공통 타입"을 계산합니다. 예를 들어,

![](<https://images.velog.io/images/feelslikemmmm/post/79abf8dd-d6cf-4b86-a158-edb43b7281bf/carbon%20(62).png>)

위 예제의 arr 타입을 추론하려면 각 배열 요소들의 타입을 고려해야 하는데요,

여기서 배열의 타입을 고를 수 있는 두 가지 후보가 있습니다

number 와 null 입니다.

최적 공통 타입 알고리즘은 각 후보 타입을 고려하여 모든 후보 타입을 포함할 수 있는 타입을 선택합니다

> arr의 타입이 union 타입으로 추론되었습니다.
> ![](https://images.velog.io/images/feelslikemmmm/post/44e2e61c-3c92-4068-9cd9-5eadfea6e704/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-07-01%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.59.59.png)

후보 타입들로부터 최적 공통 타입을 선택하기 때문에

모든 후보 타입을 포함할 수 있는 상위 타입이 존재하더라도

후보 타입 중 상위 타입이 존재하지 않으면 선택할 수 없습니다 예를들어,

![](<https://images.velog.io/images/feelslikemmmm/post/0a88a58a-722b-4c6e-a738-ac1c22341051/carbon%20(63).png>)

이상적으로는 school 변수가 School[] 타입으로 추론되길 원하지만, 배열 중 School 타입의 객체가 없기 때문에 School을 배열 요소 타입으로 추론하지 않습니다

이를 해결하기 위해서는 모든 후보 타입을 포함하는 상위 타입을 표기해야 합니다

![](<https://images.velog.io/images/feelslikemmmm/post/6d4477b8-473a-4f2e-b6d8-fc1bdec086ec/carbon%20(64).png>)

최적 공통 타입이 존재하지 않는 경우, 위의 arr의 추론 결과와 마찬가지로

(ElementarySchool | MiddleSchool | highSchool)[] 과 같은 유니언 배열 타입입니다

### 문맥상 타이핑 (Contextual Typing)

타입스크립트에서는 경우에 따라 "다른 방향" 에서도 타입을 추론하는데요, 이를 문맥상 타이핑 이라고 합니다

문맥상 타이핑은 표현식의 타입이 해당 위치에 암시될 때 발생합니다

![](<https://images.velog.io/images/feelslikemmmm/post/b60735a7-1af3-44bf-b1bc-b876e4cb6837/carbon%20(65).png>)

여기에서 타입스크립트의 타입 검사는 Window.onmousedown 함수 타입을 사용하여

할당 오른쪽에 함수 표현식의 타입을 추론합니다.

이렇게 했을 때 mouseEvent 매개변수의 타입이 button 프로퍼티는 있지만,

cat 프로퍼티는 없음을 추론할 수 있습니다.

문맥상 타이핑은 많은 경우에 적용됩니다.

일반적인 경우, 함수 호출 인수, 할당의 오른쪽, 타입 단언,

객체 / 배열 리터럴의 멤버, 반환문이 있습니다.

문맥상 타입은 최적 공통 타입의 후보 타입으로도 사용됩니다. 예를 들어:

![](<https://images.velog.io/images/feelslikemmmm/post/ef3f2ccf-8df2-47ee-bf6d-ea227e681800/carbon%20(66).png>)

위 예제에서 최적 공통 타입은 4가지 후보 타입을 가지는데요,

School, ElementarySchool, MiddleSchool, highSchool 이 중,

School 이 최적 공통 타입 알고리즘에 의해 선택됩니다

> 이처럼 자동으로 타입을 지정해주는 간편한 타입 추론은 좋은 것일까요?

타입스크립트가 자동으로 타입을 명시해주지만

위에서 예시로 든 코드들은 사실 무척 간단한 코드이고

실제 작업하는 코드를 작성할때 위 예시처럼 간단하게 작성하는 경우는 없습니다

그렇기 때문에 왠만하면 타입을 정확하게 명시하는 것이 좋습니다

다만 원시 타입 같은 경우에는 타입 추론을 사용할 수 있겠지만

함수에서는 따로 실행되는 코드가 안에서 많이 작성되기 때문에

타입을 명시하는 것이 좋습니다, 물론 void 라면 생략이 가능하지만

따로 return 되는 타입이 있다면 작성하는 습관을 들이는 것이 좋습니다.
