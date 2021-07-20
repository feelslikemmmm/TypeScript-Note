이제까지 공부했던 기본 타입들을 이용해서 계산기 함수를 만들어보자

![](https://images.velog.io/images/feelslikemmmm/post/a8ed9957-a362-465a-a109-9396ebf3c9bf/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-19%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.38.07.png)

계산을 해주는 calculate 라는 함수는 우선 5가지의 케이스를 첫번째 인자로 받고

두번째 세번째 인자로는 첫번째 인자의 케이스에 따라서 계산해서 결과값을 리턴해준다

그렇다면 어떻게 타입스크립트를 통해 calculate 함수를 정의할 수 있을까

우선 5가지의 케이스를 union type을 이용해서 타입으로 정의해준다

![](https://images.velog.io/images/feelslikemmmm/post/aef4f08c-8bb8-4e7d-b538-8b12b07c3be1/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-19%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.39.54.png)

그 후 calculate 함수를 선언하고 첫번째 인자는 command 이 인자의 타입은

앞에서 정의했던 Command가 될 것이고 두번째 세번째 인자는 number 타입이다

그리고 두번쨰 세번째 인자를 각 케이스별로 계산해서 리턴해주는 값 또한 number 이다

그렇게 함수를 정의해주고 함수 내부에서는 각 케이스에 따라 다른 결과 값을 주기 위해서

Swich 문을 활용했다

![](https://images.velog.io/images/feelslikemmmm/post/42d5dc68-2aeb-4490-afb7-e3608fe6190d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-19%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.40.15.png)

calculate 함수를 실행해보자

![](https://images.velog.io/images/feelslikemmmm/post/fe430360-badf-4e83-8287-49b191a20933/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-19%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.42.17.png)

원하는 결과 값이 출력된 것을 알 수 있다
