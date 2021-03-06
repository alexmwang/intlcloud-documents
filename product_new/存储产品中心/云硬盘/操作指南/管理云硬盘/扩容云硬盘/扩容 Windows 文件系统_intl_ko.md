## 작업 시나리오

[CBS 확장](https://intl.cloud.tencent.com/document/product/362/5747) 완료 후, 확장된 부분의 용량을 기존 파티션 안으로 나누거나 확장된 부분의 용량을 독립된 새로운 파티션으로 포맷합니다.

- 만약 사용자 CBS가 CVM에 연결되어 있고 클라우드 서비스가 정상 운영 상태일 때, 디스크 확장 작업을 진행하는 경우 먼저 [디스크 재스캔]을 진행 하면 확장 후 하드 디스크 공간을 식별할 수 있습니다.
- 만약 사용자 디스크가 마운트 대기 상태/디스크 마운트의 상태이어도 서버가 종료되고 확장 작업이 수행된 경우 확장된 디스크 공간이 자동으로 식별됩니다.

## 전제 조건
>- 확장 파일 시스템 조작이 부적절한 경우 기존 데이터에 영향을 줄 수 있으므로 작업 전에 반드시 수동으로 [스냅샷 생성](https://intl.cloud.tencent.com/document/product/362/5755)에 데이터 백업을 진행하기 권장합니다.
>-파일 시스템을 확장하려면 [인스턴스 재시작](https://intl.cloud.tencent.com/document/product/213/4928) 또는 디스크 재스캔이 필요합니다. 일정 시간 동안 서비스가 중단될 수 있으므로 신중하게 적합한 시간을 선택하십시오.
>
- [CBS 확장](https://intl.cloud.tencent.com/document/product/362/5747) 용량이 있습니다.
- 해당 CBS가 이미 Windows CVM을 Windows에 [마운트](https://intl.cloud.tencent.com/document/product/362/5745)하였고 파일 시스템이 생성되었습니다.
- 확장 예정인 파티션 및 파일 시스템의 Windows CVM에 [로그인](https://intl.cloud.tencent.com/document/product/213/5435)했습니다.

## 작업 순서
>- [CBS 확장](https://intl.cloud.tencent.com/document/product/362/5747) 시 해당 디스크의 마운트가 CVM에 정상 작동 중이면 [디스크 재스캔](#Scaning)하여 CBS를 확장, 식별 후 [볼륨 확장](#Extending)을 진행하십시오.
>- [CBS 확장](https://intl.cloud.tencent.com/document/product/362/5747) 시 해당 디스크가 마운트 대기 상태거나 해당 디스크의 CVM가 마운트 종료 상태면 직접 [볼륨 확장](#Extending)하면 됩니다.
>-본 문서는 Windows Server 2008 운영 체제를 예시로 합니다. 각기 다른 조작 시스템의 확장 조작이 다를 수 있으니. 본 문서는 잠조용으로만 사용하십시오.

<span id="Scaning"></span>
### (옵션) 디스크 재스캔

1. [컴퓨터 관리]를 엽니다.
2. 왼쪽 사이드바에서 [저장]> [디스크 관리]를 선택하십시오.
3. [디스크 관리] 마우스 우클릭하고 [디스크 재스캔]을 선택하십시오. 아래 이미지를 참고하십시오.
4. 스캔 완료 후, 데이터 디스크가 확장 후 크기(해당 예시에서는 스캔 진행 후 데이터 디스트가 원래 10GB에서 50GB로 확장된 것을 식별합니다)가 되었는지 확인합니다. 아래 이미지를 참고하십시오.

<span id="Extending"></span>
### 볼륨 확장

1. 디스크 용량의 아무 공백이나 마우스 우클릭하여 [볼륨 확장]을 선택하십시오.
2. 확장 볼륨 마법사를 따라 볼륨 확장을 완료하십시오. 완료 후 새롭게 생성된 데이터 디스크 용량은 원래 볼륨으로 병합됩니다. 아래 이미지를 참조하십시오.

## 관련 작업
[파티션 및 파일 시스템(Linux) 확장](https://intl.cloud.tencent.com/document/product/362/6738)

