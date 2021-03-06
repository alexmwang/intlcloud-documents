## 스팟 인스턴스란 무엇입니까?
스팟 인스턴스(Spot)는 CVM의 새 인스턴스 운영 모드로 가장 핵심적인 특징은 할인 판매와 시스템 중단 메커니즘입니다. 일정한 대폭 할인으로 인스턴스를 구매할 수 있지만 시스템은 해당 인스턴스를 자동 회수할 수 있습니다. 스팟 인스턴스를 구매한 후 콘솔 작업, 원격 로그인, 서비스 배치 및 관련 VPC 등 종량제 CVM 인스턴스 사용과 동일합니다.

- 관련 링크: [FAQ>인스턴스 유형> 스팟 인스턴스](https://intl.cloud.tencent.com/document/product/213/17817)
- 관련 링크: [스팟 인스턴스를 어떻게 구매합니까?](https://intl.cloud.tencent.com/document/product/213/17926)

## 현재 단계의 특수 정책
- **고정 비례 할인**: 모든 사양의 스팟 인스턴스는 고정 할인으로 판매됩니다. 동일한 사양 종량제 인스턴스는 20% 가격에 판매되며 소수 유형의 인스턴스는 미세 조정할 수 있습니다.
- **시스템 자동 중단(재고 변동)**: 현재 단계에서 시스템은 시장 가격이 사용자 가격보다 높다는 이유로 중단하지는 않지만 스팟 인스턴스 리소스 재고 부족으로 인해 중단될 수 있습니다. 재고가 부족할 경우 시스템은 할당한 스팟 인스턴스에서 랜덤 회수합니다.
- **전체 리전 시작**: 스팟 인스턴스는 이미 Tencent Cloud의 대부분 리전에 시작되어 있으므로 인스턴스 유형을 지원하여 종량제 모드와 동기화 합니다. 최신 리전 및 인스턴스 유형은 [스팟 인스턴스 - 스팟 인스턴스가 지원하는 리전 및 유형>>](https://intl.cloud.tencent.com/document/product/213/17817)에서 조회하십시오.

## 제품 특징
### I. 가격 대비 고성능
![](https://main.qcloudimg.com/raw/8179ef6629ac0a0b4b9c3c9cd6f80ffa.png)
스팟 인스턴스는 종량제 인스턴스의 할인 가격에 판매되며 최대 90% 할인됩니다.

- **할인 폭도**: 스팟 인스턴스의 가격은 동일한 사양 종량제 인스턴스를 기준으로 할인 판매를 진행하며 할인 구간은 10%~원가입니다.
- **할인 적용 부분**: 할인은 CVM CPU 및 메모리 부분에만 적용되며 시스템 디스크, 데이터 디스크, 대역폭 및 유료 미러 이미지 등 CVM 관련 유료 항목은 인스턴스 할인 영향을 받지 않습니다.
- **가격 변동**: 이 할인율은 일정 기간 동안 안정적이지만 가용존에서 대규모 구매 행위가 발생하면 가격은 변동합니다(현재 단계에서 할인 비율이 80%로 고정됨).

### II. 시스템 중단 메커니즘
![](https://main.qcloudimg.com/raw/a4db964d52400b9a00d3c7e96c0b833d.png)
종량제와 정액 요금제 인스턴스는 사용자가 직접 릴리스하지만 스팟 인스턴스는 시스템 백그라운드에서 중단됩니다. 시스템은 현재 가격 및 리소스 재고량 등 종합적인 상황에 따라 할당된 스팟 인스턴스에 대한 중단 여부를 판단합니다.
![](https://main.qcloudimg.com/raw/824a585f8dfeb1914f4d72ea1eafdb6c.png)
- **가격 원인으로 중단**: 시장 가격이 사용자의 최고 지정 가격보다 큰 경우 인스턴스는 회수될 것입니다(현재 단계에서 시장가격은 고정될 것입니다).
- **재고 원인으로 중단**: 해당 유형 리소스 풀 재고가 전체적으로 부족할 경우 시스템은 부족한 양에 따라 스팟 인스턴스를 회수하고 재고가 복구되면 스팟 인스턴스로 다시 신청할 수 있습니다.

## 시나리오 적용하지 않음
시스템 중단 메커니즘으로 인해 사용자는 인스턴스의 라이프사이클을 완전히 파악할 수 없으므로 안정성 요구가 매우 높은 서비스는 스팟 인스턴스에서 실행하지 않는 것을 권장합니다. 예를 들면 다음과 같습니다.
- 데이터베이스 서비스
- CLB의 온라인 서비스, 웹 사이트 서비스 등을 사용하지 않음
- 분산형 아키텍처의 핵심 제어 노드
- 장시간(10+시간)의 빅 데이터 컴퓨팅 작업

## 적용 시나리오와 업종
### 적용 시나리오
- 빅 데이터 컴퓨팅
- CLB의 온라인 서비스 및 웹 사이트 서비스 사용
- 네트워크 크롤러 서비스
- 다른 세분화 분할 또는 중단 시점에서 다시 시작하는 컴퓨팅 시나리오를 지원

### 적용 업종
- 유전자 시퀀서와 분석
- 약물 정형 분석
- 비디오 트랜스 코딩, 비디오 렌더링
- 금융, 거래 데이터 분석
- 사진과 멀티미디어 처리
- 과학 컴퓨팅(지리, 유체역학 등)

## 제한
- **할당 제한**: CVM 갯수 제한과는 달리 스팟 인스턴스는 사용자의 가용존에 있는 모든 스팟 인스턴스의 vCPU 핵심 수를 합산하여 할당 제한 메트릭으로 사용됩니다. 현재 단계에서 각 계정의 가용존은 최대 50개 vCPU 핵심 합인 스팟 인스턴스를 보유하고 있습니다(신청서 신청을 통해 할당을 높힐 수 있습니다.).
- **작업 제한1**: 스팟 인스턴스는 오르고 내리는 구성을 지원하지 않습니다.
- **작업 제한2**: 스팟 인스턴스는 정액 요금제를 지원하지 않습니다.

## 모범 사례
### I. 작업 분할
- 장시간 세분화 분할하는 작업으로 중단되는 가능성을 감소합니다.
- EMR와 유사하고 분리된 빅 데이터 세트를 사용합니다.

### II. CLB을 통해 온라인과 웹 사이트 서비스의 안정성 보장
- 액세스 레이어는 로드 밸런서, CLB를 사용합니다.
- 백엔드 리소스는 부분 종량제 인스턴스+대량 스팟 인스턴스의 조합 모드를 사용합니다.
- 스팟 인스턴스의 중단 상황을 모니터링하여 CLB에서 중단된 인스턴스를 제거합니다.

### III. 중단 시점에서 재시작하는 컴퓨팅 스케쥴링 모드 지원
- 컴퓨팅 중간 부분 결과를 COS/CFS/NAS 등 영구적인 스토리지 제품에 저장합니다.
- Metadata를 통해 중단되는 인스턴스를 감지하고 2분 보존 기간 동안 컴퓨팅 결과를 저장합니다.
- 스팟 인스턴스가 다시 시작되면 위의 계산을 계속합니다.
