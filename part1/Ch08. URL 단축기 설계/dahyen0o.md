# Ch08. URL 단축기 설계

### 해시 후 충돌 해소 전략(URL을 단축할 때 해시 함수를 변환된 문자열을 일정한 길이로 잘라 새로운 URL을 만드는 방법)의 장점과 단점은?

* 단점을 보완하는 방법은?

<details>
<summary><h4>해설</h4></summary>

> 해시 후 충돌 해소 전략(URL을 단축할 때 해시 함수를 변환된 문자열을 일정한 길이로 잘라 새로운 URL을 만드는 방법)의 장점과 단점은?
장점
* 단축 URL의 길이가 고정된다.
* 유일성이 보장되는 ID 생성기가 필요하지 않다.
* 새 URL 주소로 다른 URL 주소를 알기 쉽지 않아 보안에 유리하다.

단점
* 충돌이 해소될 때까지 계속 데이터베이스를 거쳐 새로운 문자열을 생성해야 한다.

> 단점을 보완하는 방법은?
* 새 URL을 데이터베이스 대신 `블룸 필터` 를 사용한다.
  * 블룸 필터: 원소가 집합에 속하는지 여부를 검사하는데 사용되는 확률적 자료 구조이다.
  * 블룸 필터에 의해 어떤 원소가 집합에 속한다고 판단된 경우 실제로는 원소가 집합에 속하지 않는 긍정 오류가 발생하는 것이 가능하지만, 반대로 원소가 집합에 속하지 않는 것으로 판단되었는데 실제로는 원소가 집합에 속하는 부정 오류는 절대로 발생하지 않는다는 특성이 있다.

</details>


<br>

### URL을 단축하는 Rest API를 구현했을 때, 응답을 어떻게 구성하면 좋은가?

* 응답 코드에서 301과 302의 차이와, 어떨 때 해당 코드를 사용하면 좋은지 설명하시오.

<details>
<summary><h4>해설</h4></summary>

> URL을 단축하는 Rest API를 구현했을 때, 응답을 어떻게 구성하면 좋은가?
* 헤더의 location에 단축된 URL을 입력하고, 응답 코드는 301 또는 302를 지정하여 새로운 URL로 요청할 것을 알린다.

> 응답 코드에서 301과 302의 차이와, 어떨 때 해당 코드를 사용하면 좋은지 설명하시오.
* 301: Permanently Moved, 해당 URL에 대한 HTTP 요청의 처리 책임이 영구적으로 Location 헤더에 반환된 URL로 이전되었다는 의미다.
* 따라서 브라우저는 이 응답을 캐시해 이후 같은 단축 URL에 대한 요청을 해야할 때 캐시된 원래 URL로 요청을 보낸다.
* 302: Found, 일시적으로 Location 헤더에 반환된 URL로 이전되었다는 의미다.
* 따라서 클라이언트의 요청은 항상 먼저 단축 URL을 통해 보내지고, 이후 원래 URL로 리다이렉션 된다.

</details>
