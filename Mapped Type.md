map type은 기존에 있는 타입들을 이용하면서 조금 다른 형태로 변환할 수 있는것을 말한다

![](https://images.velog.io/images/feelslikemmmm/post/258b7983-c126-4863-82be-6d3050bd25b6/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.19.34.png)

Video라는 타입이 있다 title을 가지고 있고 누가 만들었는지 author에 대한 정보도 있다

여기서 Video긴 Video인데 title과 author가 있어도 되고 없어도 되는 그런 타입을 만들고 싶다면 어떻게 할 수 있을까?

![](https://images.velog.io/images/feelslikemmmm/post/e61a0e99-e356-433c-adcb-3dcacd15c1e3/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.21.46.png)

VideoOptional이라는 타입을 새로 정의하고 ? 기호를 사용해서 옵셔널로 정의할 수 있다

![](https://images.velog.io/images/feelslikemmmm/post/ddc26004-ace5-44e0-8380-a15e4643fbfa/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.23.32.png)

이번에는 Video를 readonly타입으로 만들고 싶다면 이렇게 할 수 있다

하지만 Video의 타입을 새로 정의하고 다시 복사하고 이런 귀찮은 동작을 반복해야 할 것이다

또 다른 변경 사항이 생기면 일일이 돌아다니면서 수정을 해줘야 할 것이다

이런 것들을 간편하게 하고 재사용성을 높일 수 있게 하는것이 map type이다

![](https://images.velog.io/images/feelslikemmmm/post/64209238-7d5a-4acc-b235-e66b1efe2178/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.38.42.png)

위 이미지를 예로 들어서 숫자가 들어있는 배열을 map함수를 통해서 다른 결과를 도출해낼 수 있다

이런 것처럼 맵타입을 활용하면 기존의 타입을 다른 형태로 변환할 수 있다

![](https://images.velog.io/images/feelslikemmmm/post/8a6cc12e-eaba-43df-943f-4f792fe38b82/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.43.28.png)

Optional 이라는 타입을 만들었고 Optional은 어떤 종류의 다른 타입도 받아올 수 있는 타입이고

받아오는 타입을 이용해서 map을 이용할수 있도록 P(property)는 받아온 T(type)안의

[]를 이용해서 for in 처럼 key를 돌 수 있도록 만들고

P라는 것은 T가 가지고 있는 key중에 하나의 P라고 정의하고 T가 가지고 있는 P로 타입을정의했다

이것을 한번 활용해보자

![](https://images.velog.io/images/feelslikemmmm/post/c14c7624-6b3f-412a-91c7-0c970755c6fc/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.46.54.png)

VideoOptional 이라는 것은 우리가 정의한 Video타입의 Optional을 이용했다

이제 title, author를 옵셔널로 활용할 수 있다

videoOp는 title만을 쓸 수 있고 author는 사용하지 않아도 된다

혹은 author만 쓰고 title은 사용하지 않아도 된다

혹은 둘다 사용하지 않아도 된다

![](https://images.velog.io/images/feelslikemmmm/post/880f120a-5688-4e13-abf7-7108f14db1ac/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.49.23.png)

대신에 video에 없었던 다른 종류의 타입은 사용할 수 없다

![](https://images.velog.io/images/feelslikemmmm/post/fe220db7-829e-4298-b6c3-1ab250dbdb87/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.51.57.png)

만약 Video가 아닌 Animal이라는 타입이 있다고 가정해보면

한번 만들어둔 Optional을 활용해서 animal을 정의할 수 있다

이렇게 타입 오브젝트 정의 안에서 배열과 같은 기호를 사용하면 키를 빙글 빙글 돌수가 있다

이 문법은 for in과 비슷하다

![](https://images.velog.io/images/feelslikemmmm/post/d6569df2-47f1-4ada-9955-d83ae5eba35f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.55.09.png)

ReadOnly라는 타입을 readonly를 통해서 정의했다

![](https://images.velog.io/images/feelslikemmmm/post/59608385-db38-4f00-bdf6-ff8f4d67790d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.55.39.png)

타입안에 정의된 속성을 바꾸려고 하자 readonly 속성 때문에 바꿀 수 없는 것을 볼 수 있다

이처럼 맵 타입을 이용하면 기존의 타입에서 다른 타입으로 성질을 변화할 수가 있다
