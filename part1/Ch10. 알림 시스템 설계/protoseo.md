# Ch10. 알림 시스템 설계

> 우리는 각 iOS, 안드로이드 핸드폰에서 사용할 수 있는 앱을 개발하는 회사입니다. 최근 앱 사용자들에게 공지를 위한 푸시 알림을 보내야 하는 요구사항이 생겼는데, 각 OS에 푸시 알림을 보내기 위하 필요한 컴포넌트들은 어떤 것들이 있을까요?

* 그렇다면, 푸시 알림을 보내기 위해 수집해야 하는 정보들에는 어떤 것들이 있을까요?
* 우리 앱의 사용자가 많이 늘어서, 해당 알림 시스템에 부하가 너무 몰려서 알림이 제대로 발송되지 않는 문제가 발생하는 경우 어떻게 해결할 수 있을까요?

<details>
<summary><h4>해설</h4></summary>

> 우리는 각 iOS, 안드로이드 핸드폰에서 사용할 수 있는 앱을 개발하는 회사입니다. 최근 앱 사용자들에게 공지를 위한 푸시 알림을 보내야 하는 요구사항이 생겼는데, 각 OS에 푸시 알림을 보내기 위하 필요한 컴포넌트들은 어떤 것들이 있을까요?
* iOS 같은 경우 알림 제공자, APNS, iOS 단말이 있을 것이고, 안드로이드의 경우 알림 제공자, FCM, 안드로이드 단말이 있을 수 있다.

> 그렇다면, 푸시 알림을 보내기 위해 수집해야 하는 정보들에는 어떤 것들이 있을까요?
* APNS, FCM에서 푸시 알림을 보내기 위해서 꼭 필요한 정보로는 단말 토큰이 필요할 수 있다. 그 외에 필요하다고 생각하는 추가적인 정보들을 선택적으로 수집할 수 있다.

> 우리 앱의 사용자가 많이 늘어서, 해당 알림 시스템에 부하가 너무 몰려서 알림이 제대로 발송되지 않는 문제가 발생하는 경우 어떻게 해결할 수 있을까요?
* 다양한 방법이 있을 수 있다. 먼저 알림 시스템 서버를 확장하고, APNS와 FCM과 같은 제 3자 제공 서비스 전에 메시지 큐를 사용해서 시스템 컴포넌트 사이의 강한 결합을 끊을 수 있다. 또한 데이터베이스와 캐시를 알림 시스템의 주 서버에서 분리할 수 있다.

</details>
<br>

> 분산 환경에서 운영될 알림 시스템을 설계할 때 안정성을 확보하기 위해 고려해봐야 할 것들은 어떤 것들이 있을까요?

* 알림 전송 시스템에서 알림이 소실되지 않도록 하기 위해서 어떤 방법을 사용할 수 있을까요?
* 분산 시스템 특성 상 가끔은 같은 알림이 중복되어 전송될 수 도 있는데, 알림 중복 전송 방지 로직을 간단하게 설명해주세요.

<details>
<summary><h4>해설</h4></summary>

> 분산 환경에서 운영될 알림 시스템을 설계할 때 안정성을 확보하기 위해 고려해봐야 할 것들은 어떤 것들이 있을까요?
* 데이터 손실 방지, 알림 중복 전송 방지를 고려해야 한다.

> 알림 전송 시스템에서 알림이 소실되지 않도록 하기 위해서 어떤 방법을 사용할 수 있을까요? 
* 알림 데이터를 데이터베이스에 보관하고 재시도 메커니즘을 구현해야 한다. 전송에 실패한 알림은 다시 큐에 넣고 지정된 횟수만큼 재시도한다.

> 분산 시스템 특성 상 가끔은 같은 알림이 중복되어 전송될 수 도 있는데, 알림 중복 전송 방지 로직을 간단하게 설명해주세요.
* 보내야 할 알림이 도착하면 그 이벤트 ID를 검사하여 이전에 본 적이 있는 이벤트인지 살핀다. 중복된 이벤트라면 버리고, 그렇지 않다면 알림을 발송한다.

</details>
