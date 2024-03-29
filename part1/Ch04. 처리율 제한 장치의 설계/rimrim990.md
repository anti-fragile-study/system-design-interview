# Ch04. 처리율 제한 장치의 설계

### 서버의 요청 처리율 제한장치를 어떻게 구성할지 간략하게 설계해보시오

* 처리율 제한 장치를 분산 환경으로 확장한다면, 고려해야 할 문제에는 무엇이 있나?
* 클라이언트의 API 호출 횟수를 제한하기 위한 방법으로는 무엇이 있나?

<details>
<summary><h4>해설</h4></summary>

> 서버의 요청 처리율 제한장치를 어떻게 구성할지 **간략하게** 설계해보시오
* 클라이언트의 모든 요청이 처리율 제한 장치를 거치게 하고, 지정한 처리율을 초과하면 서버로 요청을 전달하지 않는다.
* 처리율을 초과한 요청은 버려지며, API 엔드포인트 별로 처리율을 관리한다
* 응답 헤더 값과 상태 코드를 사용해 사용자에게 요청이 거부되었음을 알린다

> 처리율 제한 장치를 분산 환경으로 확장한다면, 고려해야 할 문제에는 무엇이 있나?
* 여러 서버가 동시에 동일한 데이터에 접근할 때 경쟁 조건 이슈가 발생할 수 있다. 경쟁 조건으로 인해 공유 데이터의 일관성이 깨지게 된다.
* 서버 간 데이터를 동기화해야 한다. 데이터를 동기화하지 않으면 올바르게 동작할 수 없다. 

> 클라이언트의 API 호출 횟수를 제한하기 위한 방법으로는 무엇이 있나?
* 클라이언트 측에 캐시를 구축하여 API 호출 횟수를 줄일 수 있다.
</details>


<br>

### 레디스란 무엇인가?

* 레디스의 정렬 집합 (sorted set) 자료구조란 무엇인가?
* 레디스에 저장된 변수 값을 갱신할 때 경쟁 조건이 발생할 수 있다. 이를 어떻게 해결할 수 있을까?

<details>
<summary><h4>해설</h4></summary>

> 레디스란 무엇인가?
* 키-값 데이터를 저장하고 있는 메모리 저장소입니다. 메모리에 데이터를 저장하기 때문에 하드디스크보다 더 빠른 접근 속도를 갖습니다.

> 레디스의 정렬 집합 (sorted set) 자료구조란 무엇인가?
* 데이터와 스코어를 하나의 묶음으로 저장하는 집합 자료구조이다. 유일한 키 값에 대응되는 데이터와 스코어 묶음을 저장한다.
* 정렬 집합의 요소들은 스코어 값을 기반으로 정렬되며, 사용자는 스코어 값의 범위로 데이터를 조회할 수 있다.

> 레디스에 저장된 변수 값을 갱신할 때 경쟁 조건이 발생할 수 있다. 이를 어떻게 해결할 수 있을까? 
* 레디스는 기본적으로 싱글 스레드로 동작하기 때문에 원자적으로 연산을 처리한다. 그럼에도 여러 클라이언트가 동시에 읽고 갱신하는 작업을 수행한다면 경쟁 조건이 발생한다.
* 경쟁 조건을 해결하기 위해 트랜잭션을 사용한다. 레디스는 트랜잭션 연산을 큐에 저장한 후, 순차적으로 실행해준다

</details>
