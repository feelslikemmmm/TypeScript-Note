지금까지 정리한 타입을 활용해서 로딩 상태를 표시해보자

![](https://images.velog.io/images/feelslikemmmm/post/96cc90be-2604-42f5-8f1a-93245d68817d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-19%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.59.18.png)

우선 타입은 LoadingState , SuccessState, FailState가 있다

그리고 ResourceLoadState라는 unionType의 타입이 있는데

ResourceLoadState는 위 3개의 타입 중 하나의 타입으로 결정되는 타입이다

printLoginState라는 로그인 상태에 따라 각각 다른 결과를 출력하는 함수를 만들어볼건데

state가 loading 일 경우에는 콘솔에 Loading..을

state가 success 일 경우에는 presponse.body의 메세지를

state가 fail 일 경우에는 reaseon의 메세지를 출력해보자

![](https://images.velog.io/images/feelslikemmmm/post/d4457a62-6a54-4591-af58-282397aececd/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-19%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.05.39.png)

인자로 state를 받고 그 state의 타입은 ResourceLoadState로 정의해주었고

Switch문을 통해서 3가지의 타입의 state값을 기준으로 케이스를 나눴다

이 함수를 실행해보면

![](https://images.velog.io/images/feelslikemmmm/post/9db4f37a-333b-4b01-8b3c-e45ddd8846a1/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-19%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.06.38.png)

결과 값이 잘 출력되는 것을 볼 수 있다
