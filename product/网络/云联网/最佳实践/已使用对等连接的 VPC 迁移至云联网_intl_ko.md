사용자의 VPC가 이미 피어링 연결을 사용하였을 경우, 다음 절차에 따라 CCN에 마이그레이션할 수 있습니다. 
1. CCN 인스턴스 1개를 생성합니다.
2. 이미 피어링 연결을 사용한 VPC를 해당 CCN과 연결합니다.
3. CCN 라우팅 테이블을 검사합니다.
4. VPC의 서브넷 라우팅 테이블에서 피어링 연결 라우팅을 사용 중지하고 CCN 라우팅을 사용합니다.

## 작업 예시
VPC1과 VPC2가 피어링 연결을 통해 상호 연결이 생성되었으며, 이제는 CCN에 마이그레이션하여 기타 VPC와 전체 네트워크 상호 연결을 구현해야 합니다.
- VPC1(광저우): 192.168.0.0/16, 서브넷 A: 192.168.0.0/24, 서브넷 B: 192.168.1.0/24
- VPC2(상하이): 10.0.0.0/16, 서브넷 C: 10.0.0.0/24, 서브넷 D: 10.0.1.0/24.

![](https://main.qcloudimg.com/raw/7ab512f4414898d6488fd60d3d1cf16a.png)
다음 절차를 따르십시오.
1. CCN 인스턴스 1개를 생성합니다(이미 있을 경우 생성할 필요 없음). 작업 세부 정보는 [CCN 인스턴스 생성](https://cloud.tencent.com/document/product/877/18752)을 참조하십시오.
2. VPC1, VPC2를 대응하는 CCN 인스턴스와 연결합니다. 작업 세부 정보는 [네트워크 인스턴스 연결](https://cloud.tencent.com/document/product/877/18747)을 참조하십시오.
3. 연결 후, 해당 CCN 인스턴스의 라우팅 테이블에서 대상이 VPC1, VPC2인 각 서브넷의 라우팅 전략을 볼 수 있습니다(이 예시에 4개의 라우팅 전략이 있으며, 각각 서브넷 A, B, C, D를 지향함).
![그림 설명](https://main.qcloudimg.com/raw/39de66b68b8a761ec0f8b888116e0df1.png)
4. 각각 VPC1과 VPC2의 각 서브넷의 라우팅 테이블에 진입하며, 라우팅 상황을 조회(CCN 라우팅은 기본적으로 서브넷 라우팅 테이블에 배포하지만 반드시 효력이 발생하지는 않음)하고 라우팅 사용 중지와 사용을 통해 마이그레이션을 완료합니다.

## 상황 설명
- 상황 1: CCN이 자동 배포한 라우팅이 기존 피어링 연결과 충돌이 발생하지 않았을 경우, CCN 라우팅이 이미 적용되었음을 나타냅니다. 이때 기존 피어링 연결 라우팅을 사용 중지하기만 하면 됩니다.
 ![그림 설명](
https://main.qcloudimg.com/raw/f25bfe0d73627404a6b081203baf4bc1.png)
- 상황 2: CCN이 자동 배포한 라우팅이 기존 피어링 연결과 중첩 충돌이 발생할 경우, CCN 라우팅은 기본적으로 무효하여 바로 사용할 수 없습니다. 우선 다음 홉이 피어링 연결인 라우팅 전략을 [사용 중지]하고 다음 홉이 해당 CCN인 라우팅 전략을 [활성화]합니다.
>**주의:**
>작업을 사용 중지하면 비즈니스가 일시적으로 중단될 수 있습니다. 회복 시간은 CCN 라우팅을 활성화한 시간에 따라 결정됩니다.

 ![그림 설명](https://main.qcloudimg.com/raw/de6869e6e4c07181574a0d88bbfdd685.png)
- 상황 3: CCN이 자동 배포한 라우팅이 기존 피어링 연결과 포함 충돌이 발생할 경우, CCN 라우팅은 기본적으로 무효합니다. 단, 다음 홉이 CCN인 라우팅 전략을 [활성화]할 수 있으며, 활성화 후 최장 마스크 매칭 원칙에 따라 포워딩합니다. 마이그레이션 후 기존 피어링 연결을 더는 사용하지 않을 경우, 기존 다음 홉이 피어링 연결인 라우팅 전략을 [사용 중지]하는 것이 좋습니다.
 ![그림 설명](https://main.qcloudimg.com/raw/5cfd481eed906ccf1e2aa7ca2cc16e11.png)

