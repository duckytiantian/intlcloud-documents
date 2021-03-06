[//]: # (chinagitpath:XXXXX)

## 사용자 요구
일부 사용자 비즈니스가 시간 지연에 대해 요구사항이 까다롭거나 비즈니스가 일반 상황에서 반드시 오리진 서버에 직접 접근해야 할 경우, 오리진 서버의 방어 스케줄링 방안과 결합하는 것을 고려하십시오.
해당 방안은 트래픽이 일반 상황에서 오리진 서버에 직접 접근할 수 있는데, 공격을 받은 뒤 신속하게 방어 능력을 구비해야 하는 요구를 총족시킬 수 있습니다.

## 방어 방안
오리진 서버와 결합한 방어 스케줄링 방안은 다음 그림과 같습니다.
>?본 방안은 DNS 서비스 제공업체에 의존하며 모니터링과 스마트 전환 기능을 갖추어야 합니다.

 ![](https://main.qcloudimg.com/raw/25b320a68db4122b83fcf85b5a53843d.png)

## 방안 설명
본 방안은 주로 Anti-DDoS Advanced IP, DNS 모니터링, 클라이언트 오리진 서버의 대외 비즈니스 IP와 오리진 서버 스탠바이 IP로 구성됩니다.
- 일반 상황에서 비즈니스의 도메인 이름을 정상적인 대외 비즈니스 IP에 해석하며, 비즈니스 트래픽이 오리진 서버에 직접 접근합니다. DNS 모니터링은 오리진 서버 비즈니스의 정상 접근 가능 여부를 실시간 모니터링합니다.
- DNS 모니터링이 일반 대외 비즈니스 IP를 접근할 수 없음을 감지하면, 스마트 전환 규칙에 따라 비즈니스 도메인 이름을 Anti-DDoS Advanced IP에 신속하게 해석합니다. Anti-DDoS Advanced IP가 공격 트래픽을 클리닝하고, 정상 비즈니스 트래픽을 오리진 서버의 스탠바이 IP에 포워딩하고 그를 통해 비즈니스 가용성을 보장합니다.
>!지터 등 요소로 야기된 오전환을 피하고 모니터링 효과를 확보하기 위해 수동 전환을 권장합니다.


## 방안 효과
- 일반 상황에서 오리진 서버에 직접 접근하려는 요구를 만족시킵니다.
- 대기시간 요구가 매우 엄격한 비즈니스에 적합합니다.
- 받은 공격이 오리진 서버 방어 능력을 초과하면, Anti-DDoS Advanced IP로 자동 전환하여 방어를 진행할 수 있습니다.

## 권장사항과 주의사항
1. 오리진 서버 스탠바이 IP, Anti-DDoS Advanced IP 포워딩 규칙 등 구성을 사전에 완료해야 합니다.
2. 더 나은 방어 효과를 위해 오리진 서버 스탠바이 IP를 정상적인 비즈니스 IP와 다른 물리적 회선에 분포하길 권장합니다.
3. 주기적으로 방안을 검증하고 연습하며, 세부 사항을 숙지하여 가능한 문제 해결 등을 진행하길 권장합니다.


