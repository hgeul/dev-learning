# AWS SAA-C03 8주 학습 계획

## 기준과 운영 방식

- 기준: [AWS SAA-C03 공식 시험 안내](https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03.html), 확인 날짜: 2026-10-13.
- 아래 8주 일정은 공식 시험 범위를 바탕으로 구성한 개인 학습 계획이며 AWS가 제시한 일정은 아니다.
- 주당 6~8시간을 가정한다. 공식 문서 읽기 2시간, 자신의 설명과 질의응답 2시간, 로컬 실습 또는 설계 검토 2~4시간으로 시작하고 이해도에 따라 조정한다.
- 주차가 끝나도 자동 완료하지 않는다. 부족한 항목은 다음 주에 복습하고 [진행 기록](progress.md)에 근거를 남긴다.
- 현재 AWS 리소스 생성·배포는 하지 않는다. 아래 검증 활동은 로컬 실험 또는 문서 기반 설계 검토다. 설계 검토는 실행 실습으로 세지 않으며 로컬 결과도 AWS 동작을 입증하지 않는다.

## 공식 영역과 세부 과제

영역 비중은 채점 대상 시험 내용의 비중이며 학습 시간 비율을 뜻하지 않는다. 과제 설명은 한국어 요약이다.

| 공식 영역 | 비중 | 세부 과제 | 주요 학습 주차 |
| --- | --- | --- | --- |
| 1. 보안 아키텍처 설계 | 30% | 1.1 리소스 접근 제어, 1.2 워크로드·애플리케이션 보안, 1.3 데이터 보안 통제 | 1~3주, 8주 |
| 2. 복원력 있는 아키텍처 설계 | 26% | 2.1 확장성과 느슨한 결합, 2.2 고가용성과 내결함성 | 4~5주, 8주 |
| 3. 고성능 아키텍처 설계 | 24% | 3.1 스토리지, 3.2 탄력적 컴퓨팅, 3.3 데이터베이스, 3.4 네트워크, 3.5 데이터 수집·변환 | 2~6주, 8주 |
| 4. 비용 최적화 아키텍처 설계 | 20% | 4.1 스토리지, 4.2 컴퓨팅, 4.3 데이터베이스, 4.4 네트워크 비용 | 7~8주 |

## 주차별 계획

| 주차 | 학습 목표·주요 개념 | 공식 과제 | 직접 설명할 질문 | 검증 활동과 남길 근거 |
| --- | --- | --- | --- | --- |
| 1주 | 리전·AZ, 공동 책임 모델, IAM 정책·역할·STS, 최소 권한, MFA, IAM Identity Center, Organizations·SCP와 다중 계정 | 1.1 | 사용자와 역할은 언제 구분하며, SCP와 IAM 정책은 어떻게 함께 작용하는가? | 가상 백엔드의 접근 요구와 최소 권한 정책 예시를 작성하고 허용·거부 예상 및 공식 근거를 노트에 기록. 실제 권한 검증은 미실행으로 표시 |
| 2주 | CIDR·서브넷·라우팅, IGW·NAT, SG·NACL, VPC 엔드포인트·PrivateLink, 피어링·Transit Gateway, VPN·Direct Connect, Route 53·CloudFront·Global Accelerator, WAF·Shield·Cognito·GuardDuty | 1.2, 3.4 | 외부 요청과 프라이빗 서버의 외부 연결은 어떤 경로를 거치며, SG와 NACL은 무엇이 다른가? | 로컬 CIDR 계산 코드의 경계값 검증. 가상 VPC 통신 경로와 허용·차단 조건을 별도 설계 노트로 작성 |
| 3주 | S3·EBS·EFS·FSx 선택, 성능·내구성, 버전 관리·복제·수명 주기, KMS·키 정책, TLS·ACM, Secrets Manager, 데이터 분류·보존·백업·Macie | 1.3, 3.1 | 객체·블록·파일 스토리지의 선택 기준과 저장·전송 중 암호화의 차이는 무엇인가? | 로컬 파일의 백업·복원 후 해시 비교. 요구사항별 스토리지와 보안 통제 선택 이유 기록; AWS 암호화·복제는 미검증으로 표시 |
| 4주 | EC2 인스턴스 선택, ALB·NLB·GWLB, Auto Scaling과 지표, Lambda, API Gateway, ECS·EKS·Fargate, SQS·SNS·EventBridge·Step Functions, 무상태·느슨한 결합 | 2.1, 3.2 | 트래픽 급증 시 어떤 지표로 확장하며, 큐 도입 후 중복·실패는 어떻게 처리하는가? | 로컬 생산자·소비자 코드에 재시도와 중복 입력을 넣어 멱등성 검증. 서버리스·컨테이너·EC2 비교와 한계를 기록 |
| 5주 | 다중 AZ·리전, 장애 조치, RDS·Aurora, Multi-AZ·읽기 복제본, DynamoDB 접근 패턴·용량, ElastiCache·RDS Proxy, 서비스 할당량·스로틀링, CloudWatch·X-Ray, RTO·RPO와 DR 전략 | 2.2, 3.3 | 읽기 확장과 장애 복구는 어떻게 다르며, 주어진 RTO·RPO에 어떤 DR 전략이 맞는가? | 로컬 DB의 인덱스 전후 실행 계획 비교. 가상 AZ 장애 시나리오와 백업·복원, 파일럿 라이트, 웜 스탠바이, 액티브-액티브 비교 기록 |
| 6주 | 배치·스트리밍 수집, Kinesis·Data Firehose, Glue·EMR·Athena·Redshift, Lake Formation, DataSync·Storage Gateway·Transfer Family, DMS와 이관, CSV·Parquet | 3.5, 3.1, 3.3 | 수집 지연·처리량·보안·스키마 요구에 따라 어떤 파이프라인과 이관 방식을 고르는가? | 합성 CSV의 로컬 변환·집계 코드로 행 수와 집계값 보존 검증. AWS 수집·변환 구성은 설계 근거만 기록 |
| 7주 | S3 계층·검색·요청 비용, 구매 옵션·Spot·Reserved Instances·Savings Plans, 적정 용량·서버리스, DB 용량·백업 비용, NAT·엔드포인트·AZ·리전 간 전송, Cost Explorer·Budgets·비용 배분 태그 | 4.1~4.4 | 동일한 가용성·성능 조건에서 어떤 비용 요소가 선택을 바꾸는가? | 공식 가격 페이지의 리전·조회일·사용량 가정으로 비용 비교표 작성. 로컬 계산식 검증; 비용 도구나 리소스 생성은 하지 않음 |
| 8주 | 네 영역 통합 설계, 공식 시험 범위 재점검, 시나리오 문제 풀이, 오답 분석과 취약 항목 재설명 | 1.1~1.3, 2.1~2.2, 3.1~3.5, 4.1~4.4 | 하나의 백엔드 설계가 보안·가용성·성능·비용 요구를 충족하는 이유와 대안의 단점은 무엇인가? | 가상 서비스 아키텍처와 대안 비교 작성. 문제별 선택·배제 이유를 직접 설명하고 노트·실습 근거로 진행 표 갱신 |

## 매주 남길 기록

1. `notes/`에 학습한 개념, 자신의 설명, 피드백, 공식 문서 URL·확인 날짜, 미해결 질문을 기록한다.
2. 실행 코드가 있으면 `labs/`에 목적, 환경, 실행 명령, 예상 결과, 검증 절차, 실제 결과와 정리 방법을 함께 기록한다.
3. `progress.md`에서 해당 주차를 갱신한다. 주차 안의 이해도가 다르면 항목별 행을 나눠 기록한다.
4. 개념 설명의 근거와 실행 검증의 근거를 별도로 연결한다. 실습이 계획된 항목은 실행 결과를 사용자가 검증하기 전까지 완료하지 않는다.

## 공식 참고 자료

- [SAA-C03 시험 안내와 영역 비중](https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03.html)
- [영역 1: 보안](https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03-domain1.html)
- [영역 2: 복원력](https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03-domain2.html)
- [영역 3: 성능](https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03-domain3.html)
- [영역 4: 비용](https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03-domain4.html)
- [시험 범위 내 서비스 목록](https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/saa-03-in-scope-services.html)
- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [AWS 서비스별 공식 문서](https://docs.aws.amazon.com/)
- [AWS 공식 가격](https://aws.amazon.com/pricing/)

서비스 목록은 변경될 수 있고 시험 내용을 전부 열거한 목록이 아니다. 매주 해당 서비스의 공식 문서를 함께 읽고 시험 응시 전 최신 안내를 다시 확인한다.
