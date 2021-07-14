#### 판별 유니언 (Discriminated Unions)

이전 포스팅에서 Union Type을 통해서

로그인 성공 결과에 따라 콘솔에 메세지를 출력하는 함수를 예시로 구현했었다

![](https://images.velog.io/images/feelslikemmmm/post/67734b6c-1b7c-4dab-ab78-afbd028e8aed/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-18%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%209.31.24.png)

위 이미지가 해당 예시 코드인데 이 코드를 Discriminated Union 을 통해서 바꿔보자

![](https://images.velog.io/images/feelslikemmmm/post/ee56d7c8-2438-46ce-a8f9-7c893ca7c1ab/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-18%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%209.48.26.png)

SuccessState type 과 FailState 타입에

공통된 property인 result라는 값을 정의해주었다 이렇게 되면 printLoginState 함수에서

state.result를 통해서 state의 공통된 값을 찾아올수가 있다

그리고 state.result의 값이 success이냐 fail이냐에 따라서 원하는 콘솔값을 출력하게 해주었다

이렇게 해서 in 키워드를 써서 구현했을때보다 직관적이고 구분하기 좋은 코드로 바꿀 수 있었다
