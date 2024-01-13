# Ch02. 개략적인 규모 측정

<details>
<summary> 캐시에 대해 설명하시오</summary>

캐시란 장치 간의 속도 차이를 완화하기 위해 사용되는 임시 저장 공간입니다.
</details>

<details>
<summary>캐시 쓰기 전략에는 무엇이 있나?</summary>

1. write-through: 캐시 메모리가 갱신되는 순간 저장소도 함께 갱신한다
2. write-back : 우선 캐시 메모리만 갱신하고, 캐시 블록이 방출될 때 저장소를 갱신한다

</details>

<details>
<summary>캐시 방출 정책에는 무엇이 있나?</summary>

1. FIFO: 가장 처음에 올라온 블록을 방출한다
2. LRU: 가장 오래 전에 사용된 블록을 방출한다
3. LFU: 가장 적은 빈도로 사용된 블록을 방출한다
</details>

<hr />

<details>
<summary>네트워크 latency 구성 요소에 대해 설명하시오.</summary>

1. queueing delay: 라우터 큐에서 패킷이 전송되기를 기다리는 시간
2. transmission delay: 패킷의 모든 비트가 링크로 전송하는 데 소요되는 시간
3. propagation delay: 비트가 링크의 처음부터 목적지까지 도달하는 데 소요되는 시간

</details>

<details>
<summary>디스크 접근 시간은 무엇으로 구성되는가?</summary>

1. seek time: 데이터가 있는 동심원인 실린더에 도달하는 시간
2. rotation time: 데이터가 있는 섹터로 회전하는 시간
3. transfer time: 데이터를 메모리로 전송하는 시간

</details>

<details>
<summary>latency와 throughput의 차이는 무엇인가?</summary>

1. latency: 하나의 작업을 처리하는 데 소요된 시간
2. throughput: 초당 처리한 작업의 수
</details>

<hr />

<details>
<summary>대규모 트래픽을 처리하기 위해 필요한 기술들에 대해 설명하시오.</summary>

1. 애플리케이션 - 캐시, 멀티 프로세싱
2. 네트워크 - 로드 밸런서, CDN
3. 데이터베이스 - 샤딩, 레플리카, 인덱스
</details>

<details>
<summary>고가용성을 확보하기 위한 전략에는 무엇이 있나?</summary>

1. 로드 밸런서를 도입해 정상 동작하는 서버에만 트래픽을 전송한다
2. 데이터베이스 다중화하고 데이터 복사본을 저장해 놓는다
</details>

<details>
<summary>QPS란 무엇인가?</summary>

데이터베이스가 1초 동안 받는 쿼리의 수
</details>


