index type에 대해서 잘 이해하려면 우선 기본적인 것을 잘 알고 있어야 한다

![](https://images.velog.io/images/feelslikemmmm/post/b426802b-9390-427c-be55-fca7896544cd/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.09.11.png)

우리가 오브젝트의 안에 있는 key의 value를 출력하기 위해서는 두가지 방법이 있다

obj.을 이용해서 출력하거나 obj의 index에 접근하는 것처럼 obj['name'] 접근할 수 있다

이것을 잘 이해하고 있어야 한다

이것처럼 타입도 인덱스를 기반으로해서 타입을 결정할 수 있다

![](https://images.velog.io/images/feelslikemmmm/post/b23abcf4-132c-4e8e-a466-b6cf2ac939eb/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.11.05.png)

Animal이라는 타입이 있다 이 타입은 name(string)과 age(number) 그리고 gender(union)를 가지고 있다

![](https://images.velog.io/images/feelslikemmmm/post/c7eff3e5-c6ec-4d33-8c90-7d669f848ac8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.11.56.png)

Name이라는 타입을 선언하고 Animal에 있는 name이라는 키의 타입을 Name타입에 할당했다

이제 Name 타입은 문자열만 할당이 가능하다

이것들을 활용하면 더 재밌는 것을 해볼 수 있다

![](https://images.velog.io/images/feelslikemmmm/post/cd684470-bd51-44d2-bc4e-8c7dd015f780/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.13.07.png)

Gender라는 타입에 Animal에 있는 gender 키의 타입을 Gender타입에 할당했다

이제 Gender 타입은 male 혹은 female의 타입을 가지게 되었다

![](https://images.velog.io/images/feelslikemmmm/post/b61d0d6a-242e-4518-ac5f-bd7204e5880e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.13.57.png)

keyof Animal을 사용해서 Keys의 타입을 할당했다

이제 Keys는 name 혹은 age 혹은 gender라는 문자열 유니언 타입이 들어가게 된다

![](https://images.velog.io/images/feelslikemmmm/post/5693cbcf-df41-4d5b-9a54-3c218d01b576/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-31%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.15.16.png)

Person 이라는 타입을 정의하고 name은 string 타입 gender에는 Animal의 gender를 줬다

이제 person은 name은 스트링을 사용해야하고 gender는 Animal의 gender와 같은 값인

male과 female 둘 중 하나만 선택할 수 있는 것을 볼 수 있다

이처럼 인덱스 타입을 이용하면 다른 타입에 있는 키에 접근해서 키에 밸류의 타입을

그대로 다시 선언할 수 있다

이것 자체로는 그렇게 쓸모있어 보이지는 않는데 다음 포스팅에서 어떻게 활용할 수 있을지

알아보도록 하자
