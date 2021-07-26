타입스크립트는 0.8버전을 시작으로 급속도로 많은 버전들이 나오기 시작했다

그래서 초창기에는 type alias와 type으로도 줄여서 말했는데

type과 interface는 많이 달랐고 interface가 할 수 있는 것이 더 많았다

그래서 예전부터 배웠던 사람들은 interface를 여기저기서 마구마구 사용하는 경우가 있다고 하는데

이렇게 모든곳에 interface를 쓰는것은 좋지않다고 한다

type과 interface는 엄연히 다르고 성격과 특징도 다르기 때문이다

많은 곳에서 type과 interface를 교체해서 사용할 수는 있지만 interface를 난발하기 보다는

정확하게 type과 interface가 어떻게 다른지 어떤곳에서 type을 사용하고

어떤곳에서 interface를 사용하는게 맞는지 정확하게 알고 사용하는것이 중요하다

구현 사항에 초점을 두고 알아보자

### Type과 interface 공통 구현 사항

![](https://images.velog.io/images/feelslikemmmm/post/da1bdf51-c685-4b74-b52f-29ae459f506e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-30%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.39.23.png)

PositionType 이라는 type과 PositionInterface라는 interface가 있다

두가지는 굉장히 동일한 것을 묘사하고 있다 둘 다 가능한 것을 알아보자

![](https://images.velog.io/images/feelslikemmmm/post/108f13f3-4ef2-4ae8-a5a1-a0c441129315/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-30%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.40.42.png)

두가지 다 오브젝트를 정의하고 타입을 할당할 수 있다

![](https://images.velog.io/images/feelslikemmmm/post/5077a06b-8cea-49a7-aac8-a68fea6f50f1/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-30%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.41.56.png)

두가지 다 클래스를 구현할 수 있다

![](https://images.velog.io/images/feelslikemmmm/post/5c655023-895e-47bc-a4cf-50c00968da06/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-30%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.43.14.png)

두가지 모두 확장이 가능하다

인터페이스는 상속을 통해서 확장을 할 수 있고

타입은 인터섹션을 이용해서 두가지를 묶은 타입을 만들 수 있다

### Type과 interface 단일 구현 사항

사실 예전 타입스크립트에서는 지원되지 않는 것이 많았다고 한다

우선 현재 버전에서도 지원하지 않는 것에 대해서 알아보자

바로 인터페이스에서만 결합이 가능하다는 점이다

![](https://images.velog.io/images/feelslikemmmm/post/87ccf1fe-3566-4a7f-b790-ecee7a2d4807/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-30%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.48.05.png)

같은 이름의 PositionInterface를 만들고 내부에 z라는 인자를 추가했다

![](https://images.velog.io/images/feelslikemmmm/post/9b006c23-5ad6-458f-9e8c-406900085c4c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-30%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.48.40.png)

![](https://images.velog.io/images/feelslikemmmm/post/09b96833-fd95-4a11-9e9e-5102b6d5e6f7/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-30%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.48.56.png)

이제는 obj2에 z라는 인자를 넣어야지만 사용이 가능한 것을 볼 수 있다

이처럼 PositionInterface 타입을 받는 곳에서는 항상 x,y,z처럼 결합된 것을

모두 사용해야 한다

타입은 이렇게 할 수 있는 방법이 없다 대신 타입만 가능한 것이 있다

![](https://images.velog.io/images/feelslikemmmm/post/fc888ac2-3540-4ddd-9fd4-359cac48a3b6/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-30%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.52.19.png)

name이라는 string 속성과 age라는 number 속성을 가진 Person이라는 타입이 있다

또 다른 타입 Name을 Person에 있는 name의 value를 타입으로 지정할 수 있다

조금 더 활용성이 높은 타입을 선언하고 사용할 수 있다

NumberType이라는 새로운 타입도 만들 수 있고

UnionType도 만들 수 있다 이런것은 inferface로는 절대 구현할 수 없다

타입과 인터페이스 언뜻 보면 매우 비슷해보이지만 이런 차이점이 있다

이런 차이점은 타입스크립트에서 새로운 버전이 나올때마다 계속해서 변경이 되어져 왔다

사실 초창기 버전에는 타입과 인터페이스가 할 수 있는것이 많이 달랐는데

갈수록 비슷해지고 있다. 이렇게 구현 사항에서의 차이점을 알아보았다
