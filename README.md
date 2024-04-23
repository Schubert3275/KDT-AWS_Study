## AWS & 클라우드

<details>
<summary>사용 교재</summary>

![](./images/그림과%20실습으로%20배우는%20도커%20&%20쿠버네티스.png)

</details>

### DAY01

---

<details>
<summary> 클라우드 서비스 </summary>

* 클라우드 서비스란?
  * 컴퓨터 사용 정보 처리를 자신이 보유한 PC가 아닌, 인터넷 '너머'에 존재하는 클라우드 사업자 컴퓨터에서 처리하는 서비스
  * 공유 구성이 가능한 컴퓨팅 리소스(네트워크, 서버, 스토리지, 애플리케이션 서비스) 통합 통해 어디서나 간편하게, 요청에 따라 네트워크 통해 접근하는 것이 가능하게 하는 모델
* 온-프레미스 소프트웨어(On-Premises software)
  * 소프트웨어를 서버에 직접 설치에 사용하는 방식 -> 클라우드 환경과 대조됨
  * 클라우드 컴퓨팅 기술이 나오기 전까지 기업 인프라 구축의 일반적인 방식
  * 서버와 기타 H/W 인프라 구축비용 및 유지보수 비용, S/W 라이선스 지불 비용 증가
  * 구축 수개월 이상 걸리고 비용 또한 많이 들어감
* IaaS(Infrastructure as a Service)
  * CPU나 H/W등 컴퓨팅 리소스를 네트워크를 통해 서비스로 제공하는 모델
  * 클라우드 사업자가 보유하는 물리적 서버의 CPU, 메모리, 스토리지 등 하드웨어 자원을 소프트웨어적으로 나누어 사용자에게 제공 -> 자유롭게 스케일 업/다운 가능
  * 물리적 인프라 구축 및 유지보수와 관련된 비용과 복잡성을 상당부분 없애줌
  * 예: Compute Engine, Cloud Storage
* PaaS(Platform as a Service)
  * H/W, S/W, 인프라가 포함된 완전한 클라우드 플랫폼 제공 클라우드 컴퓨팅 형태
  * 애플리케이션 개발 및 실행 환경과 서비스 개발, 배포, 관리 가능한 개발 툴 제공
  * 개발 환경 처음부터 구축하는 것은 많은 시간 소요
  * Java, PHP, Ruby 등 프로그래밍 언어 지원하는 실행 환경/DB 미리 준비되어 제공
  * 예: Cloud Run, App Engine
* SaaS(Software as a Service)
  * 고객이 이미 구축된 소프트웨어에 사용료를 지불하면서 이용하는 형태
  * 클라우드 애플리케이션과 기본 IT 인프라 및 플랫폼을 인터넷 브라우저 통해 최종 사용자에게 제공하는 클라우드 컴퓨팅 형태
  * 서비스 성능은 인터넷 연결 속도에 따라 달라짐 -> 고속 네트워크 하드웨어 투자
  * 고객이 인터넷 통해 앱만 연결하면 제공업체가 다른 모든 작업 수행
  * 예: Google Workspace, iCloud, Google Drive, 네이버MYBOX

</details>
<details>
<summary> 클라우드 컴퓨팅 배포 모델 </summary>

* 퍼블릭 클라우드(Public Cloud)
  * 일반 대중, 개인이나 기업에서 사용하기 위해 프로비저닝된 클라우드 인프라
  * 일반적으로 쓰는 클라우드 형태
  * 수요가 유동적인 기업, Gmail, Office 365 같은 공용 어플리케이션, 에어비앤비, 넷플릭스 등 세계적으로 서비스를 빠르게 확장할 때 적합한 모델
  * 대규모 클라우드 제공업체(AWS, Microsoft, Google) 중 한 곳에 의해 호스팅
  * 인터넷 통해 IT 리소스와 서비스(IaaS, PaaS, SaaS) 제공
  * 장점
    * 물리적 서버 구매, 설치 필요 없음 -> 비용 절약
    * 필요할 때 필요한 만큼 사용 가능함 -> 단순성
    * 서버 운영 및 유지보수 (O&M) 부담 없음 -> 총 소유비용 (TCO) 절감
  * 단점
    * 불특정 다수의 액세스에 대한 무단 액세스 또는 크랙 위험 발생 쉬움
    * 서비스 내용이 미리 정해져 있음 -> 없는 서비스 사용 위한 다른 추가 작업 수행 필요
    * 회사 사정으로 서비스 갑자기 중단될 가능성 있음
    * 중요한 데이터 클라우드에 남아 있으면 손상 발생 가능
* 프라이빗 클라우드(Private Cloud)
  * 단일 조직 전용 클라우드 환경을 제공하는 클라우드 컴퓨팅 모델
  * 해당 조직의 방화벽 뒤에서 사내 IT팀이 내부적으로 운영
  * 주로 기업이 이용하기 때문에 기업용 클라우드 유형으로 분류
  * 온프레미스 프라이빗 클라우드 -> 자사 전용 클라우드 환경 구축 및 운영 형태
  * 호스티스 프라이빗 클라우드 -> 클라우스 제공업체가 사용자별 환경 제공 형태
  * 장점
    * 조직 인트라넷 또는 사업자 데이터 센터에 구성되며 데이터는 모두 방화벽으로 보호
    * 최고 수준 보안 적용된 클라우드 솔루션
  * 단점
    * 서버와 기타 H/W의 인프라 구축 비용 및 유지보수 비용, S/W 라이선스 지불 비용 증가
* 커뮤니티 클라우드(Community Cloud)
  * 공통 목적 가진 특정 기업들이 클라우드 시스템 형성하여 데이터센터에서 공동 운영 형태
  * 단일 조직이 이용하는 Private Cloud를 몇몇 조직이 같이 공유하는 클라우드
  * 그룹사의 Family들끼지 Public Cloud 장점 수용 / Pirvate Colud 장점 수용
  * 퍼블릭 클라우드와 프라이빗 클라우드의 중간적인 형태
* 하이브리드 클라우드(Hybrid Cloud)
  * 네트워크 연결 통해 하나 이상의 퍼블릭 클라우드 및 프라이빗 클라우드 환경 결합
  * 서로 다른 클라우드 환경 간 데이터와 애플리케이션 공유할 수 있는 클라우드 컴퓨팅 환경
  * 기업의 중요한 데이터는 보안이 보장된 프라이빗 클라우드에 저장
  * 제한없이 클라우드의 인프라를 필요로 하는 기술들은 퍼블릭 클라우드
  * VPN과 Express Connect (P2P 전용 연결)라는 두 가지 방법으로 연결
  * 장점
    * 프라이빗 클라우드와 퍼블릭 클라우드의 장점을 모두 가짐
    * 확장성이 뛰어나고 저장공간이 무제한이며 결제 모델이 유연해 경제적
    * 클라우드 리소스 더 유연하게 사용, 더 강력하게 통제, 보안 철저
  * 단점
    * 사내 하드웨어와 필요한 추가 소프트웨어 및 도구에 계속 투자하고 유지보수
    * IT팀과 비즈니스 사용자 모두에게 새로운 기술 전문성이 필요
    * 클라우드 환경도 복잡
* 멀티 클라우드(Multi Cloud)
  * 다수의 퍼블릭 클라우드 의미
  * 여러 클라우드 공급자의 퍼블릭 클라우드 통합
  * 하이브리드 클라우드 <-> 멀티클라우드 : 개념은 다름!!!

</details>
<details>
<summary> AWS </summary>
<ul>
<details>
<summary> AWS(Amazon Web Services) </summary>

* AWS란?
  * 웹사이트 통해 제공 서비스로 일상에서 이용하는 많은 인터넷 서비스 -> Web Services
  * 컴퓨팅 자원(Computing resources) 빌려 줌으로써 실제 컴퓨터 없이도 컴퓨터 자원 이용할 수 있게 해 주는 서비스
  * 24시간 원격 접속 가능한 서버 통해 컴퓨팅 자원 활용
* AWS 용도 및 특징
  * 실시간 데이터(raw data) 처리
  * 배치 데이터(batch data) 처리
  * 사용자 친화적 -> 누구나 간단하게 구축 가능
  * 저렴한 비용 (GCP, Azure보다 상대적)
  * 민첩성, 즉각적 탄력성
  * 개방성과 유연성
  * 뛰어난 보안
  * 확장성

</details>
<details>
<summary> AWS 제공 서비스/리소스 - Compting Service </summary>

* EC2 (Elastice Compute Cloud)
  * AWS에서 가장 기본적 널리 쓰이는 인프라
  * 물리 환경의 컴퓨터처럼 컴퓨팅 리소스 제공하는 서비스
  * 컴퓨팅 파워의 규모 자유자재로 변경 가능
  * 가상머신으로 제공 -> 인스턴스(Instance)라 함
  * 안전성 위해 리전(Reion)과 가용 영역(Availability Zone)에 걸쳐 배포
* Auto Scaling
  * 트래픽 따라 EC2 인스턴스들 자동 확장/ 제거 서비스
  * 특정 트래픽 초과 시 자동 EC2 인스턴스 생성
  * 트래픽 감소 시 생된된 EC2 인스턴스 삭제
* Lambda(Serverless Computing)
  * 모든 유형의 애플리케이션이나 백엔드 서비스에 대한 코드를 별도의 관리 없이 실행하는 서비스
  * 사용자는 서버 걱정없이 코드만으로 서비스 실행
  * serverless 아키텍쳐 구현에 사용
  * 서버 및 운영 체제 유지 보수, 용량 프로비저닝 및 자동 확장, 코드 모니터링 및 로깅과 같은 컴퓨팅 리소스의 모든 관리를 자체적으로 수행
  * Lambda 사용하는 언어 중 하나로 코드 제공만 하면 됨
* Lightsail
  * 주어진 리소스 옵션(Ubuntu, Node, Lamp stack, Nginx, WordPress, Django. etc) 중 하나 택하여 단일 가상 서버를 쉽게 설정
  * 프로젝트를 빠르게 시작하는 데 필요한 가상머신, SSD기반 스토리지, 데이터 전송, DNS관리, 정적IP가 포함
* WorkSpaces
  * 데스크톱 가상화 서비스로 사내 PC 가상화로 구성
  * 문서 및 데이터 개인 PC 보관하지 않고 서버 보관 관리
  * 하드웨어 인벤토리, OS 버전 및 패치, 가상 데스크톱 인프라(VDI)를 관리하는 복잡성 제거, PC 제공 전략 간소화
* ECS (EC2 Container Service)
  * 클라우드 서버인 EC2를 Docker 컨테이너로 관리 가능하도록 나온 서비스
  * 고도로 안전하고, 안정적이고, 확장 가능한 방식
* EB (Elastice Beanstalk)
  * Java, .NET, PHP, Node.js, Python, Ruby, Go, Docker를 사용하여 Apache, Nginx, Passenger, IIS와 같은 친숙한 서버에서 개발된 웹 애플리케이션 및 서비스를 간편하게 배포 조정할 수 있는 서비스
  * 간단한 서비스 배포용으로 사용
  * 코드 업로드 하면 용량 프로비저닝, 로드 밸런싱, AutoScaling부터 시작하여 애플리케이션 상태 모니터링에 이르기까지 자동 처리
  * Heroku와 비슷한 PaaS 같은 서비스. 정확히 PaaS는 아니지만 앱을 배포하는 점에 있어서 더 수월한 서비스
  * Lightsail과 비슷한 범주

</details>
<details>
<summary> AWS 제공 서비스/리소스 - Networking Service </summary>

* VPC(Virtual Private Cloud)
  * 클라우드 가상 네트워크 구축 서비스
  * IP 주소 범위 선택, 서브넷 생성, 라우팅 테이블 및 네트워크 게이트웨이 구성 등 가상 네트워킹 환경 완벽하게 제어할 수 있고, VPC에서 IPv4와 IPv6를 모두 사용하여 리소스와 애플리케이션에 안전하고 쉽게 액세스할 수 있음
* Route53
  * Domain Name System (DNS) 도메인 관리/설정 서비스 (이름만 색다르지 보통 웹서버의 dns 구성과 같다.)
  * 도메인 이름 구매/관리, 도메인에 대한 DNS 설정 자동으로 구성
  * 사용자를 AWS외부 인프라로 전달하는 서비스 가능
  * EC2 인스턴스, Elastic 로드 밸런서, S3 저장소 등 AWS 서비스 인프라에 효과적으로 연결
* Direct Connect
  * 기존 On-Premise의 인프라와 AWS간 연결을 쉽게 설정할 수 있는 클라우드 서비스 솔루션
  * 전용선을 구성하여 낮은 지연 시간으로 데이터 및 정보를 공유할 수 있게 하는 서비스 제공
  * AWS-On-Premise를 연결하는 전용 네트워크 선 서비스
* ELB(Elastic Load Balancing)
  * 접속량이 많을 경우 L4 서비스(load balancing) 트래픽을 분산해주는 역활을 하여 고가용성 서비스 구축 서비스
  * 들어오는 애플리케이션 트래픽을 Amazon EC2 인스턴스, 컨테이너, IP 주소, Lambda 함수와 같은 여러 대상에 자동 분산

</details>
<details>
<summary> AWS 제공 서비스/리소스 - Storage Service </summary>

* ColudFront
  * 데이터, 동영상, 애플리케이션 및 API를 전 세계 고객에게 안전하게 전송하는 고속 글로벌 콘텐츠 전송 네트워크(CDN) 서비스
  * AWS의 CDN(Content Delivery Network, 콘텐츠 전송 네트워크)
  * S3, EC2, Elastic Load Balancing, Route 53 등과 같은 AWS 서비스와 통합 운영
  * 리전에 상관없이 엣지 로케이션 기준으로 가장 가까운 곳에서 파일 캐시를 가져오기 때문에 속도도 빠르며 비용도 EC2 혹은 S3로 서비스를 제공하는것 보다 더 저렴
* Transit Gateway
  * VPC 및 계정 연결 손쉽게 확장
  * VPC와 온프레미스 네트워크 단일 게이트웨이에 연결 지원 서비스
* S3 (Simple Storage Service)
  * 정적 파일 스토리지 서비스 (사진, 비디오, 문서 등 또는 frontend 코드, Lambda 함수 코드 해당)
  * 사용자는 URL을 통해 파일을 사용
  * 다른 유저들의 액세스를 컨트롤할 수 있는 기능 제공
  * HTTP 프로토콜과 연동되어 정적 사이트 호스팅
  * CloudFront 구성하면 S3에 저장된 정적 파일이 CDN을 통해 더 효율적으로 빠르게 보급되는 장점
* EBS (Elastic Block Store)
  * EC2 인스턴스에 장착하여 사용할 수 있는 가상 저장 장치 (HDD 나 SSD 처럼 가상 컴퓨터에 장착한 저장장치)
  * EC2 인스턴스 제공 기본 용량보다 더 사용해야 할 때, 운영체제 중단시키지 않고 자유롭게 늘리고 싶을 때, 영구적인 데이터 보관 필요할 때, RAID 등의 고급 기능 필요할 때 사용
  * EC2에 설치된 OS에서 그냥 일반적인 하드디스크 또는 SSD처럼 인식되어 원하는 크기로 만들 수 있고, 성능 (IOPS)또한 원하는 수치로 설정할 수 있으며 사용자가 삭제하기 전까지 데이터가 안전하게 유지
  * EBS를 연결하여 EBS에 파일을 저장한다면 EC2 인스턴스와 관계 없이 영구적으로 보관이 가능
* Glacier
  * 데이터 보관, 백업 및 아카이브를 위한 스토리지 서비스
  * 저장에만 특화되어있는 저렴한 스토리지 서비스
  * 거의 무제한으로 데이터를 저장 가능
  * 저장하고 꺼내는데 3시간-5시간 걸린다는 특징
  * S3에서 -> Glacier로 백업을 자동 생성하도록 설정 가능
  * 스토리지 비용이 저렴하며 데이터에 밀리초 만에 액세스해야 할 필요가 없다면 이 제품 사용
* Storage Gateway
  * On-Premise에 있는 데이터를 클라우드로 저장 보관하기 위한 게이트웨이 연결 서비스
* Snowball
  * Import/Export 서비스를 통해 대량의 데이터를 AWS로 이전할 때 네트워크로 전송하지 않고 디스크나 스토리지에 저장하여 물리적으로 전달하고 이를 업로드 하여 주는 서비스
  * 대량의 데이터를 AWS로 업로드 할 때 유용

</details>
<details>
<summary> AWS 제공 서비스/리소스 - Database Service </summary>

* RDS(Relational DB Service)
  * 관계형 데이터베이스 이용할 수 있는 서비스
  * DB 설정, 패치, 백업 등 시간 소모적인 관리 작업 처리
  * RDBMS 클라우드 서비스 : Amazon Aurora, MySQL, MariaDB, PostgreSQL, Oracle, SQL Server등을 지원
* DynamoDB
  * 어떠한 규모에서도 10ms 미만 성능 제공하는 key-value 형태의 NoSQL 데이터베이스 서비스
  * 데이터 규모와 관계없이 데이터 저장 및 검색, 어떤 수준의 요청 트래픽이라도 처리할 수 있는 데이터베이스 테이블을 생성할 수 있음
* ElasticCache
  * Database Caching 서비스
  * Memcached, Redis 호환 지원
* DocumentDB
  * MongoDB와 호환되는 데이터베이스를 쉽게 설정, 운영 및 조정할 수 있는 데이터베이스 서비스

</details>
<details>
<summary> AWS 제공 서비스/리소스 - Management Tools </summary>

* CloudWatch
  * AWS 서비스들을 모니터링, 알람 받는 설정들 할 수 있는 서비스
  * 특정 금액 초과할 경우 알람을 받거나 EC2의 CPU 사용률등의 알람
* CloudFormation
  * AWS 서비스 생성 및 배포 자동화 템플릿 서비스
  * 다양한 서비스들을 이용하여 아키텍쳐 구현시 미리 만들어놓은 템플릿(JSON)을 이용하여 생성, 직접 템플릿 작성하여 관리 가능
* IAM
  * Identity and Access Management 약자
  * AWS 리소스 액세스 안전하게 제어할 수 있는 서비스
  * 사용자 및 애블리케이션별 제어 권한 설정

</details>
<details>
<summary> AWS 제공 서비스/리소스 - Analytics Platform </summary>

* Kinesis
  * 대량의 데이터를 저장 분류할 수 있는 서비스
  * 다양한 규모의 스트리밍 데이터를 비용 효율적 처리할 수 있는 기능
* Redshift
  * 효율적으로 비용 및 데이터 분석할 수 있는 빠르고 확장 가능한 데이터 웨어하우스
  * 기계학습, 다량 병렬 쿼리 실행, 고성능 디스크의 열 기반 스토리지를 사용하여 다른 데이터 웨어하우스 보다 10배 빠른 성능 제공
  * 몇백 GB부터 페타바이트 규모 이상의 데이터 세트에 최적화
* EMR
  * Elastic MapReduce
  * 저장된 대량 데이터를 분류하고 분석하여 필요한 정보 추출 서비스

</details>
<details>
<summary> AWS 제공 서비스/리소스 - Application Service </summary>

* CloudSearch
  * 검색서비스로 손 쉽게 중요 정보를 모바일로 전달
  * SWF: 워크플로우 서비스
  * SQS: 큐서비스 활용한 대량 데이터 제공 서비스
* SES (Simple Email Services)
  * 외부로 대량의 메일을 발송하는 서비스
* Elastice Transcoder
  * 동영상을 인코딩 할 수 있는 서비스

</details>
<details>
<summary> AWS 제공 서비스/리소스 - AWS 가격정책 </summary>

* On-Demand
  * 기본적 사용하는 과금 방식, 사용한 시간 만큼 비용 지불하는 형태
* Reserved
  * 일정 기간 인스턴스 사용 약속하고, 그에 대한 할인 적용받는 방식
* Spot
  * 입찰 방식의 사용방법, 사용자가 입찰 가격을 제시해놓으면 아마존에서 남는 인스턴스들에 대해서 Spot 가격 책정
  * 가격이 입찰가격 내로 들어오면 인스턴스 기동되는 방식
  * 입찰 가격이 넘어가면 자동으로 Spot Instance는 다시 종료
  * 항상 실행시키는 업무가 아닌 특정 작업 배치 돌릴 서버용도 사용 적합

</details>
<details>
<summary> AWS 글로벌 인프라 </summary>

* 글로벌 서비스
  * 한국 미국 영국 상관없이 전세계에서 공통적으로 사용하는 인프라
* 구성
  * 리전(Region)
  * 가용영역(AZ, Availability Zones)
  * 엣지 로케이션(Edge Location)
  * 리전 엣지 캐시(Regional Edge Cache)

</details>
</ul>
</details>

---

| 파일명 | 내용 |
| ------ | ---- |
| ``     |      |
