Error 그리고 다른 언어에서는 보통 Exception이라고 많이 표현한다

Error handling은 보통 3가지 단계로 나눌 수 있다

에러가 발생할 수 있는 부분을 시도(try) 하고

에러가 발생한다면 잡을 수 있고(catch)

에러가 발생하던 발생하지 않던 마무리 단계(finally)로 마무리한다

물론 엄청 심각한 오류라면 앱이 죽는 수도 있다

메모리에 문제가 있거나 복구할 수 없는 심각한 문제같은 경우에 말이다

하지만 우리가 어느 정도 우아하게 처리할 수 있다면 try와 catch를 이용해서 에러를 잡은 다음에

조금 더 의미 있는 에러 메세지를 사용자에게 보여준다던지 아니면 복구하기 위한 노력들을 해볼 수 있다

예제를 통해서 try, catch, finally에 대해서 알아보자

![](https://images.velog.io/images/feelslikemmmm/post/1ec0da23-9d62-462c-a66c-07253dfc749e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.46.21.png)

readFile 함수는 fileName이라는 인자를 받아서 fileName이 없으면 에러를 던지고

fileName이 있다면 file contents 라는 문자열을 리턴하는 함수이다

그리고 readFile이 file을 읽게 되면 항상 닫아야 하는 함수인 closeFile 함수가 있다

![](https://images.velog.io/images/feelslikemmmm/post/3b60fe6a-2cb5-4a49-91cb-9f03081ed0fb/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.49.04.png)

![](https://images.velog.io/images/feelslikemmmm/post/c28fe2aa-eee2-46dc-b7e9-5bced6cb6a34/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.49.16.png)

fileName 변수에 문자열을 할당하고 reaFile함수를 실행시켰다

정상적으로 file contents가 리턴된 것을 볼 수 있다

이번에는 fileName에 조건문에서 설정한 값을 넣고 실행해보자

![](https://images.velog.io/images/feelslikemmmm/post/ae803efa-429c-4f3e-adbd-9208063f1f0c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.50.31.png)

![](https://images.velog.io/images/feelslikemmmm/post/be11923b-eef7-40ef-9487-dc24d8b7ca27/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.52.00.png)

어플이 죽는 상황이 발생했다

이렇게 파일이 존재하지 않는 다는 메세지와 이 에러가 어디에서 발생했는지에 대한 위치 정보와 함께

콜스택까지 보여주는 것을 확인할 수 있었다

readFile처럼 예상할 수 없는 에러가 발생할 수 있는 함수를 사용할 때에는

최대한 에러가 발생할 수 있는 정말 정확한 그 부분에서만 try를 이용해서 감싸주면 된다

![](https://images.velog.io/images/feelslikemmmm/post/359fb1ed-af3e-4edb-85c8-936ee34d7ef4/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.56.27.png)

![](https://images.velog.io/images/feelslikemmmm/post/f41a173b-8804-440d-bdc8-5e651cbeb3c9/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.57.05.png)

에러가 발생할 수 있는 reaFile함수를 try를 통해 감싼 부분에서 실행을 해주고

혹시 에러가 발생한다면 catch를 통해 인자로 e, 혹은 error를 받아서

catch문 안에서 에러를 잡아낼 수 있다 위 코드의 실행값으로 catched가 나온것을 볼 수 있다

아까와 다르게 에러가 발생했음에도 불구하고 어플리케이션이 멈추지않고 끝까지 동작한 것을 알 수 있다

그리고 finally가 있다

아까 우리는 readFile함수를 실행하면 무조건 파일을 닫아야 하는 closeFile이라는 함수를 만들었었다

그 함수를 실행하기 위해서는 finally를 이용하면 된다

finally는 try가 성공하든 실패하든 catch가 호출되든 되지않든 무조건 finally는 호출되게 되어있다

![](https://images.velog.io/images/feelslikemmmm/post/d27d2021-2cfa-47a3-b208-2275343a58e4/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.00.16.png)

![](https://images.velog.io/images/feelslikemmmm/post/56103ff4-e666-4557-b916-283981f4cff8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.00.29.png)

try가 실패했을때 finally가 호출된것을 확인할 수 있고

![](https://images.velog.io/images/feelslikemmmm/post/eb64acf7-ea0d-4bc0-93d1-8adc7777c427/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.01.07.png)

![](https://images.velog.io/images/feelslikemmmm/post/e22b1f4c-c413-4610-8415-7864356d1623/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.01.23.png)

try가 성공했을때도 마찬가지로 finally가 호출된것을 확인할 수 있다

이처럼 내가 무언가를 시도하고 성공하든지 실패하든지 상관없이 무언가를 실행해야 한다면

finally를 사용하면 된다

우리는 여기서 한가지 의문을 가질 수 있다 try, catch와 상관없이 무조건 실행을 한다면

굳이 finally를 사용하지 않고 바깥에서 함수를 호출하면 되는거 아닐까?

이런 의문이 들 수 있다

그렇다면 예시를 통해 한번 알아보자

![](https://images.velog.io/images/feelslikemmmm/post/260c477a-2d83-45ae-95b3-27744acdde20/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.05.33.png)

run이라는 함수안에 아까 우리가 작성한 로직을 넣고 finally는 사용하지 않고

함수 내부에서 closeFile 함수를 실행했다 결과는 어떨까?

![](https://images.velog.io/images/feelslikemmmm/post/17df400a-93de-4836-a0f6-ac628e21c05c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.06.14.png)

의문점을 가졌던거처럼 finally를 사용하지 않아도 똑같은 결과가 나왔다

그런데 catch부분에서 에러가 발생하면 리턴을 시킨다면 어떻게 될까?

![](https://images.velog.io/images/feelslikemmmm/post/f8374c4e-7d24-460c-ada6-31335f6fd4d7/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.07.02.png)

![](https://images.velog.io/images/feelslikemmmm/post/a68e3053-36aa-456d-adb8-c14ccb23332d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.07.17.png)

catch부분에서 에러가 발생한다면 리턴을 시켜주었더니 closeFile 함수가 실행되지 않고

run 함수가 그대로 종료된 결과를 얻을 수 있었다

이처럼 catch안에서 무언가를 처리할때 다른 에러가 발생하거나 리턴이 되거나

이런 경우에는 다른 함수를 사용할 수 없기 때문에 finally안에서 작업을 해야한다

![](https://images.velog.io/images/feelslikemmmm/post/c2495fee-01b8-4b85-b1ec-8c0b8936006f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.08.34.png)

![](https://images.velog.io/images/feelslikemmmm/post/a4ebda82-ab4e-4895-a023-d75b48e80d0d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-29%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.08.45.png)

finally안에서 closeFile을 실행하였더니 catch에서 리턴이 되어도 실행이 된 것을 볼 수 있다
