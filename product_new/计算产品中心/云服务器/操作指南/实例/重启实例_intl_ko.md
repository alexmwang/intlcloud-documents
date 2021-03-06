## 작업 시나리오

재시작 작업은 CVM 유지 보수에 사용되는 방식으로 인스턴스 재시작은 로컬 컴퓨터의 운영 체제를 재시작하는 것과 같습니다. 본 문서에서는 인스턴스 재시작에 대한 방식을 안내합니다.

## 주의사항
 - **재시작 준비:** 재시작 시간 중에는 인스턴스가 정상적으로 서비스를 제공할 수 없으므로 재시작하기 전 CVM이 서비스 요청을 중단하였는지 확인하십시오.
 - **재시작 작업 방식:** 인스턴스에서 재시작 명령어를 실행하는 것이 아닌(예를 들면 Windows의 재시작 명령 및 Linux의 Reboot 명령), Tencent Cloud에서 제공하는 재시작 작업으로 인스턴스의 재시작을 권장합니다.
 - **재시작 시간:** 일반적으로 재시작 작업은 몇 분 정도 소요됩니다.
 - **인스턴스 물리적 특성:** 인스턴스 재시작은 인스턴스의 물리적 특성을 변경하지 않습니다. 인스턴스의 공인 IP, 개인 IP 및 스토리지의 어떤 데이터도 변경하지 않습니다.
 - **과금 관련:** 인스턴스를 재시작해도 새 인스턴스에 대한 과금이 시작되지 않습니다.

## 작업 순서

사용자는 다음과 같은 방식을 통해 인스턴스를 재시작할 수 있습니다.
- [콘솔을 사용하여 인스턴스 재시작](#consoleRestart)
- [API를 사용하여 인스턴스 재시작](#apiRestart)

<span id="consoleRestart"></span>
### 콘솔을 사용하여 인스턴스 재시작

1. [CVM 콘솔](https://console.cloud.tencent.com/cvm/)에 로그인하십시오.
2. 인스턴스 관리 페이지에서 재시작할 인스턴스 수량에 따라 인스턴스 재시작 방식을 선택하십시오.
 - 단일 인스턴스 재시작: 재시작이 필요한 인스턴스 열에서 [더보기]>[인스턴스 상태]>[재시작]을 클릭합니다. 아래 이미지를 참조하십시오.
 - 여러 개의 인스턴스 재시작: 재시작이 필요한 인스턴스를 선택하고 리스트 상단에서 [재시작]을 클릭하면 일괄적으로 인스턴스를 재시작할 수 있습니다. 인스턴스를 재시작할 수 없는 경우 원인이 표시됩니다. 아래 이미지를 참조하십시오.
> 단일 인스턴스는 다음 방식을 통해 재시작할 수 있습니다.

<span id="apiRestart"></span>
### API 를 사용하여 인스턴스 재시작
[RebootInstances 인터페이스](https://cloud.tencent.com/document/api/213/15742)를 참조하십시오.
