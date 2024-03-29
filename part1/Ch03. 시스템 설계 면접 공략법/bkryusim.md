# Ch03. 시스템 설계 면접 공략법

### 질문

> 시스템을 설계함에 있어서 가장 중요하다고 여기는 부분은 무엇입니까?
* 설계한 시스템이 올바른지 검증하기 위한 방법으로 어떤 것들이 있을까요?

<details>
<summary><h4>해설</h4></summary>

> 시스템을 설계함에 있어서 가장 중요하게 여길 부분은 무엇일까요?
* 가정과 요구사항을 명확하게 하는 것입니다. 항상 정답은 없다는 생각으로 대화를 통해 요구사항을 명확히 하고, 오버엔지니어링을 경계하며 상황을 해결할 수 있는 적절한 설계를 찾아야 합니다.

> 설계한 시스템이 올바른지 검증하기 위한 방법으로 어떤 것들이 있을까요?
* 시스템 요구사항을 구체적 수치로 나타내고, 시스템 전체 처리량을 개략적으로 계산하여 처리 가능한지 확인합니다. 또 여러 edge case들을 파악하여 고려해볼 수 있습니다. 무엇보다 중요한 것은 팀원들과의 소통입니다. 운영을 시작한 후에는 로그와 메트릭을 적절히 구성하여 꾸준히 모니터링하는 노력이 필요합니다.
</details>


<br>

### 질문

> 취업에 성공해 새로운 팀에 합류하게 되었습니다. 팀이 개발하는 서비스의 시스템을 파악하는데, 아무리 생각해 봐도 오버엔지니어링인 것 같습니다. 이런 상황에서 어떻게 해결할지 말해 주세요.
> 오버엔지니어링으로 인해 발생하는 피해, 손해는 어떤 것들이 있을까요?

<details>
<summary><h4>해설</h4></summary>

> 취업에 성공해 새로운 팀에 합류하게 되었습니다. 팀이 개발하는 시스템을 발견했는데, 아무리 생각해 봐도 오버엔지니어링이 적용된 것 같습니다. 이런 상황에서 어떻게 해결할지 말해 주세요.
* 사람마다 다른 답변이 예상됩니다.
* 현재 시스템이 오버엔지니어링인 이유를 구체적 수치로 나타내볼 수 있을 것 같습니다. 시스템의 개략적인 처리량을 계산하고, 실제 발생하는 트래픽과 비교하여 보이면 명확할 것 같습니다. 또 새로운 시스템 설계안을 제시하고 문서화하여 팀원과 공유합니다. 당장 시스템을 다시 바꾸는 것 또한 큰 시간과 비용이 따르기 때문에, 바로 적용할 수는 없겠지만 팀원 모두가 인지해야 언젠가 기회가 왔을 때 바꿀 수 있다고 생각합니다.

> 오버엔지니어링으로 인해 발생하는 피해, 손해는 어떤 것들이 있을까요?
* 핵심 하위 도메인 이외 영역에서 기능적 복잡도가 증가해 핵심 도메인에 집중하지 못해 회사 전체적 성장성이 줄어들게 됩니다. 또한 코드 및 시스템 복잡도 때문에 새로 합류하는 팀원들이 시스템을 이해하기까지 오랜 시간이 걸리고, 일의 능률이 떨어집니다. 그리고 대다수의 경우, 오버엔지니어링된 시스템은 더 많은 시스템 자원을 요구하기 때문에 비용도 더 많이 청구될 수 있습니다. 
</details>
