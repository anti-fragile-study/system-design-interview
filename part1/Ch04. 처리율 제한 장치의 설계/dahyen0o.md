# Ch04. 처리율 제한 장치의 설계

### 처리율 제한 장치(rate limiter)의 장점은 무엇인가?

* 처리율 제한 장치를 구현할 때 고려해야 하는 요소는 무엇인가?

<details>
<summary><h4>해설</h4></summary>

> 처리율 제한 장치(rate limiter)의 장점은 무엇인가?
* DoS(Denial of Service) 공격에 의한 자원 고갈을 방지할 수 있다.
* 비용을 절감한다.
* 서버 과부하를 막는다.

> 처리율 제한 장치를 구현할 때 고려해야 하는 요소는 무엇인가?
* 설정된 처리율을 초과하는 요청은 정확하게 제한한다.
* 처리율 제한 장치 때문에 응답시간이 낮아지지 않도록 주의한다.
* 가능한 적은 메모리를 쓴다.
* 높은 결함 감내성(fault tolerance)를 가져야 한다.
* 등등...
</details>


<br>

### 처리율 제한 알고리즘 중 '누출 버킷 알고리즘'은 무엇인가? 알고리즘에 대해 설명하라.

* 누출 버킷 알고리즘에서 사용하는 두 인자는 무엇인가?
* 누출 버킷 알고리즘의 장/단점은 무엇인가?

<details>
<summary><h4>해설</h4></summary>

> 처리율 제한 알고리즘 중 '누출 버킷 알고리즘'은 무엇인가? 알고리즘에 대해 설명하라.
* 토큰 버킷 알고리즘과 비슷하지만 `요청 처리율` 이 고정되어 있다. FIFO로 구현한다.
1. 요청이 도착하면 큐가 가득 차 있는지 본다. 빈자리가 있는 경우에는 큐에 요청을 추가한다.
2. 큐가 가득 차 있는 경우에는 새 요청은 버린다.
3. 지정된 시간마다 큐에서 요청을 꺼내어 처리한다.

> 누출 버킷 알고리즘에서 사용하는 두 인자는 무엇인가?
* 버킷 크기: 큐 사이즈와 같은 값이다. 큐에는 처리될 항목들이 보관된다.
* 처리율(overflow rate): 지정된 시간당 몇 개의 항목을 처리할지 지정하는 값이다.

> 누출 버킷 알고리즘의 장/단점은 무엇인가?

장점
* 큐의 크기가 제한되어 있어 메모리 사용량 측면에서 효율적이다.
* 고정된 처리율을 갖고 있어 안정적 출력이 필요한 경우에 적합하다.

단점
* 단시간에 많은 트래픽이 몰리는 경우 최신 요청들이 버려질 수 있다.
* 두 개 인자를 올바르게 튜닝하기 까다로울 수 있다.
</details>
