# Ch06. 키-값 저장소 설계

### 데이터 일관성을 달성하기 위해 사용하는 프로토콜은 무엇인지 설명하시오

* 강한 일관성을 보장하려면 해당 프로토콜을 어떻게 사용해야 할까?
* 결과적 일관성은 무엇이고, 이 때 발생할 수 있는 문제는 무엇인가?

<details>
<summary><h4>해설</h4></summary>

> 데이터 일관성을 달성하기 위해 사용하는 프로토콜은 무엇인지 설명하시오
* 정족수 합의(Quorum Consensus) 프로토콜이다.
* 이 프로토콜은 읽기/쓰기 연산 모두에 일관성을 보장한다.
* 사본 개수 N, 쓰기 연산에 대한 정족수 W, 읽기 연산에 대한 정족수 R을 조절해 응답 지연과 데이터 일관성 사이의 타협점을 찾는다.

> 강한 일관성을 보장하려면 해당 프로토콜을 어떻게 사용해야 할까?
* `W + R > N` 공식을 사용하면 강한 일관성이 보장된다.
* 보통 N=3 & W=R=2 를 사용한다.

> 결과적 일관성은 무엇이고, 이 때 발생할 수 있는 문제는 무엇인가?
* 약한 일관성의 한 형태로, 갱신 결과가 결국에는 모든 사본에 반영되는 모델이다.
* 결과적 일관성을 따를 경우 쓰기 연산이 병렬적으로 발생하면 시스템에 저장된 값의 일관성이 깨질 수 있다.
</details>


<br>

### CAP가 각각 무엇을 의미하고 CAP 정리가 무엇인지 설명하시오.

* CA, AP, CP 시스템을 각각 어느 데이터베이스에서 채택하고 있는가?

<details>
<summary><h4>해설</h4></summary>

> CAP가 각각 무엇을 의미하고 CAP 정리가 무엇인지 설명하시오.
* C는 데이터 일관성(consistency), A는 가용성(availability), P는 파티션 감내(partition tolerance)를 의미한다.
* CAP 정리는 이 세가지 요구사항을 동시에 만족하는 분산 시스템을 설계하는 것은 불가능하다고 얘기한다.

> CA, AP, CP 시스템을 각각 어느 데이터베이스에서 채택하고 있는가?
* CA: 실세계의 분산 시스템에서 파티션 문제가 일어나는 것은 피할 수 없는 일로 여겨지므로, 반드시 파티션 감내가 지켜지도록 설계된다. 따라서 해당 시스템을 실세계에서 사용하지 않는다.
* AP: 카산드라, Dynamo DB
* CP: Redis, Memcached, Mongo DB
</details>
