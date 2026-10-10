**Volume 24. Robot Cybersecurity**

# Chapter 01. Robot Cybersecurity Fundamentals

## 01.01. Robot Cybersecurity Threat Landscape 2020s

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

2020년대의 로봇 사이버보안(Robot Cybersecurity) 위협 환경은 로봇 시스템이 독립적으로 동작하는 기계에서 연결된 사이버-물리 플랫폼(Cyber-Physical Platform)으로 발전하면서 빠르게 확대되고 있다. 현대 로봇은 임베디드 제어기(Embedded Controller), 실시간 운영체제(Real-Time Operating System), AI 가속기(AI Accelerator), 센서(Sensor), 무선 통신(Wireless Communication), 클라우드 서비스(Cloud Service), 플릿 관리 소프트웨어(Fleet-Management Software)를 결합한다. 이러한 연결성은 기능을 향상시키지만 물리적 하드웨어에서 원격 인프라까지 이어지는 공격 경로(Attack Path)도 함께 만들어낸다.

기존 정보 시스템(Information System)과 달리 로봇에 대한 성공적인 사이버공격(Cyberattack)은 직접적인 물리적 결과(Physical Consequence)를 초래할 수 있다. 내비게이션 명령(Navigation Command), 액추에이터 설정값(Actuator Setpoint), 안전 파라미터(Safety Parameter), 인지 데이터(Perception Data), 임무 명령(Mission Instruction)을 조작하면 충돌, 장비 손상, 운영 중단 또는 사람과의 위험한 상호작용이 발생할 수 있다. 따라서 로봇 사이버보안은 정보 자산을 보호하는 동시에 물리적 안전(Physical Safety), 결정론적 제어(Deterministic Control), 운영 가용성(Operational Availability)을 유지해야 한다.

소프트웨어 정의 로보틱스(Software-Defined Robotics)로의 전환은 공격 노출 범위를 더욱 확대하였다. 로봇 기능은 임베디드 소프트웨어(Embedded Software), 미들웨어(Middleware), API, 엣지 컴퓨터(Edge Computer), 클라우드 플랫폼(Cloud Platform), 지속적으로 업데이트되는 AI 구성요소에 점차 분산되고 있다. 로보틱스 소프트웨어 아키텍처(Robotics Software Architecture)는 임베디드 시스템, 실시간 소프트웨어, ROS 2 미들웨어, 통신 API, 데이터 인프라, 클라우드-엣지 컴퓨팅(Cloud-Edge Computing), 데브옵스(DevOps), 인지, 계획, 플릿 지능(Fleet Intelligence), 피지컬 AI(Physical AI)를 포함하므로 사이버보안은 단일 하위 시스템의 문제가 아니라 본질적으로 계층 횡단적(Cross-Layer) 문제이다.

네트워크 연결성(Network Connectivity)은 가장 명확하게 드러나는 공격 표면(Attack Surface) 중 하나이다. 이더넷(Ethernet), 와이파이(Wi-Fi), 프라이빗 5G(Private 5G), VPN 연결, 원격 유지보수 인터페이스(Remote Maintenance Interface), 텔레메트리 채널(Telemetry Channel), 플릿 통신 링크(Fleet Communication Link)는 로봇을 비인가 접근, 가로채기, 스푸핑(Spoofing), 재전송 공격(Replay Attack), 서비스 거부(Denial-of-Service), 측면 이동(Lateral Movement)에 노출시킬 수 있다. 공격자가 적절하게 분할되지 않은 로봇 네트워크에 침투하면 기업 인프라에서 운영 기술(Operational Technology) 및 안전 필수 로봇 구성요소까지 공격이 확산될 수 있다.

로봇 미들웨어(Robot Middleware)는 또 하나의 중요한 보안 경계(Security Boundary)를 형성한다. ROS 2와 DDS는 분산 노드(Distributed Node)가 네트워크를 통해 토픽(Topic), 서비스(Service), 액션(Action), 디스커버리 정보(Discovery Information), 제어 데이터(Control Data)를 교환할 수 있도록 한다. 취약한 신원 관리(Identity Management), 잘못 설정된 권한, 노출된 디스커버리 메커니즘, 손상된 인증서 또는 취약한 노드는 비인가 참여자가 로봇 통신을 관찰하거나 조작하도록 만들 수 있다. 따라서 인증(Authentication), 인가(Authorization), 암호화(Encryption), 키 관리(Key Management), 로깅(Logging), 미들웨어 설정을 통합적으로 다루어야 한다.

엣지 AI(Edge AI)는 기존 소프트웨어 공격과 다른 유형의 위협을 발생시킨다. 가치가 높은 인지, 내비게이션, 조작 및 의사결정 모델이 로봇 컴퓨터에 직접 저장될 수 있기 때문에 모델 탈취(Model Theft)와 역공학(Reverse Engineering)은 중요한 지식재산권(Intellectual Property) 위험이 된다. 공격자는 센서 입력을 조작하거나 학습 데이터를 오염시키고, 모델 파일을 바꾸거나 추론 파이프라인(Inference Pipeline)을 악용할 수 있다. 또한 기존 소프트웨어 구성요소가 정상적으로 동작하는 것처럼 보이는 상황에서도 AI 의사결정을 변화시키도록 적대적 입력(Adversarial Input)을 구성할 수 있다.

피지컬 AI(Physical AI)는 학습된 모델이 물리적 환경에서 수행되는 행동에 점점 더 큰 영향을 미치기 때문에 이러한 문제를 더욱 심화시킨다. 적대적 이미지(Adversarial Image), 손상된 관측값(Corrupted Observation), 악의적인 언어 명령(Malicious Language Instruction), 조작된 세계 표현(World Representation)은 로봇이 인식하고 추론하며 실행하는 방식을 변화시킬 수 있다. 따라서 보안 경계는 운영체제와 네트워크를 넘어 모델 레지스트리(Model Registry), 학습 데이터셋(Training Dataset), 멀티모달 입력(Multimodal Input), 추론 파이프라인, 안전 모니터(Safety Monitor), AI 의사결정을 물리적 행동으로 변환하는 메커니즘까지 확장되어야 한다.

클라우드 연결형 플릿(Cloud-Connected Fleet)은 서로 다른 규모의 시스템적 위험(Systemic Risk)을 발생시킨다. 중앙집중형 플릿 관리자(Centralized Fleet Manager)는 다수의 로봇에 임무, 소프트웨어, 지도, 자격증명, 정책 및 설정을 배포할 수 있다. 따라서 높은 권한을 가진 클라우드 계정, 관리 API, 서명 서비스(Signing Service), 플릿 명령 채널(Fleet Command Channel)이 침해되면 하나의 디지털 서비스에 대한 공격이 수많은 물리적 로봇의 동시 노출로 확대될 수 있다. 강력한 신원 및 접근 관리(Identity and Access Management), 공개키 기반구조(PKI), 테넌트 격리(Tenant Isolation), 명령 인증, 암호화, 모니터링 및 사고 대응 통제가 플릿 보안의 기본 요구사항이 된다.

펌웨어(Firmware)와 무선 업데이트(Over-the-Air Update, OTA) 메커니즘은 일반적인 애플리케이션 수준 방어체계보다 하위 계층의 소프트웨어를 변경하기 때문에 특히 민감하다. 공격자는 펌웨어 대체, 악성 업데이트 주입(Malicious Update Injection), 다운그레이드 공격(Downgrade Attack), 서명 키 탈취(Signing-Key Theft), 부트 체인 조작(Boot-Chain Manipulation), 공급망 침해(Supply-Chain Compromise)를 시도할 수 있다. 보안 부팅(Secure Boot), 측정 부팅(Measured Boot), 암호학적 패키지 검증(Cryptographic Package Verification), 롤백 방지(Anti-Rollback), 보호된 키 저장소(Protected Key Storage), 소프트웨어 자재명세서(SBOM), 통제된 업데이트 파이프라인은 장치 시작부터 운영 소프트웨어 배포까지 이어지는 신뢰 체인(Chain of Trust)을 구축한다.

공급망 위험(Supply-Chain Risk) 역시 로봇이 프로세서, 센서, 운영체제, 미들웨어, 컨테이너(Container), 오픈소스 라이브러리(Open-Source Library), AI 프레임워크, 사전학습 모델(Pretrained Model), 서드파티 서비스(Third-Party Service)를 통합하면서 중요성이 커지고 있다. 상위 공급망에서 유입된 취약점은 전체 제품군에 배포될 때까지 발견되지 않을 수 있다. 따라서 사이버보안 프로그램은 구성요소 출처(Component Provenance), 소프트웨어 의존성, 알려진 취약점, 업데이트 책임, 서명 관계(Signing Relationship), 외부 공급업체와 관련된 신뢰 가정(Trust Assumption)을 파악해야 한다.

2020년대의 공격자는 자동화(Automation)의 이점도 활용할 수 있다. 인터넷 규모 스캐닝(Internet-Scale Scanning), 자동화된 취약점 탐색(Automated Vulnerability Discovery), 자격증명 공격(Credential Attack), 악성코드 프레임워크(Malware Framework), AI 지원 정찰(AI-Assisted Reconnaissance)은 노출된 로봇 인프라를 식별하는 데 필요한 노력을 줄일 수 있다. 동시에 이기종 로봇 플릿(Heterogeneous Robot Fleet)은 서로 다른 운영체제, 펌웨어 버전, 컴퓨팅 아키텍처, 네트워크 인터페이스 및 유지보수 일정을 가진 장치로 구성되는 경우가 많아 일관된 보안 강화(Hardening)와 취약점 개선(Vulnerability Remediation)을 더욱 어렵게 만든다.

위협 환경에는 내부자(Insider)와 본래 의도된 범위를 벗어나 사용되는 정상 자격증명(Legitimate Credential)도 포함된다. 엔지니어, 운영자, 공급업체, 유지보수 담당자, 클라우드 관리자 및 자동화 서비스는 로봇 시스템에 강력한 접근 권한을 보유할 수 있다. 탈취된 자격증명이나 과도한 권한(Excessive Privilege)은 기술적 취약점을 악용하지 않고도 경계 방어(Perimeter Defense)를 우회할 수 있다. 따라서 현대 로봇 보안은 명시적 신원(Explicit Identity), 최소 권한(Least Privilege), 분할된 신뢰 경계, 감사 가능한 작업(Auditable Action), 자격증명 순환(Credential Rotation), 지속적 검증(Continuous Verification)에 점점 더 의존한다.

로봇은 시간 의존적인 물리적 작업을 수행하기 때문에 가용성(Availability)은 특별히 중요하다. 서버를 즉시 종료하는 것과 같은 기존 방어 대응은 안전 필수 기동(Safety-Critical Maneuver)을 수행하고 있는 이동 로봇, 매니퓰레이터(Manipulator), 휴머노이드(Humanoid), 무인항공기(UAV)에는 적절하지 않을 수 있다. 보안 메커니즘은 기능 안전(Functional Safety)과 연계되어 탐지, 격리, 성능 저하 운용(Degradation), 비상 정지(Emergency Stopping), 복구 및 서비스 복귀(Return-to-Service) 과정에서 기계가 통제된 물리적 상태를 유지하도록 해야 한다.

사이버보안(Cybersecurity)과 안전(Safety)의 융합은 위험을 평가하는 방식도 변화시킨다. 취약점은 기술적 악용 가능성이나 정보 손실만으로 평가해서는 안 되며, 도달 가능한 물리적 상태(Reachable Physical State), 운영 환경, 로봇의 행동 권한, 환경적 위험, 플릿 규모의 확산 가능성, 독립적인 안전 제어의 효과도 함께 고려해야 한다. 따라서 사이버-물리 위험 평가(Cyber-Physical Risk Assessment)는 디지털 공격 체인(Digital Attack Chain)과 잠재적인 물리적 결과를 서로 분리된 엔지니어링 영역으로 취급하지 않고 하나의 연속된 위험 구조로 연결한다.

효과적인 방어를 위해서는 일회성 보안 설정이 아니라 지속적인 수명주기 관리(Lifecycle Management)가 필요하다. 위협 모델링(Threat Modeling)은 아키텍처 설계 단계에서 시작되며 이후 보안 구현, 코드 및 의존성 분석, 침투 테스트(Penetration Testing), 펌웨어 및 미들웨어 검증, 배포 보안 강화, 모니터링, 취약점 관리, 사고 대응(Incident Response), 보안 업데이트, 최종 폐기(Decommissioning)까지 이어진다. 전체 로봇 사이버보안 체계는 기본 원리와 위협 모델링에서 네트워크, ROS 2, AI, 클라우드, OTA, 보안 테스트, 사고 대응, 피지컬 AI 및 규정 준수(Compliance)까지 포괄적으로 연결되어야 한다.

따라서 2020년대 로봇 사이버보안 위협 환경을 정의하는 가장 중요한 특징은 융합(Convergence)이다. IT 보안(IT Security), 운영 기술 보안(Operational Technology Security), 임베디드 보안(Embedded Security), 네트워크 보안(Network Security), 클라우드 보안(Cloud Security), AI 보안(AI Security), 기능 안전(Functional Safety), 물리적 보호(Physical Protection)가 하나의 기계 안에서 점점 더 긴밀하게 결합되고 있다. 로봇을 보호하려면 공격자가 시스템에 침입할 수 있는지만 확인하는 것이 아니라 디지털 조작이 물리적 행동으로 전환될 때까지 침입이 인지, 추론, 통신, 제어 및 구동(Actuation) 계층을 통해 어떻게 전파될 수 있는지를 이해해야 한다.

## 01.02. CIA Triad for Robot Systems Confidentiality Integrity

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

기밀성(Confidentiality), 무결성(Integrity), 가용성(Availability)은 사이버보안(Cybersecurity)의 기본 모델인 CIA 트라이어드(CIA Triad)를 구성하며, 로봇 시스템에서도 매우 중요한 개념이다. 그러나 로보틱스(Robotics)에서는 소프트웨어, 네트워크, 센서, 액추에이터(Actuator), AI 모델, 물리적 프로세스가 지속적으로 상호작용하는 사이버-물리 환경(Cyber-Physical Environment)을 고려하여 이러한 속성을 해석해야 한다. 따라서 보안 실패는 디지털 정보뿐만 아니라 기계의 물리적 행동에도 영향을 미칠 수 있다.

기밀성(Confidentiality)은 비인가 주체(Unauthorized Entity)에게 정보가 공개되지 않도록 보호한다. 로봇은 운영 지도, 카메라 스트림(Camera Stream), 라이다 포인트 클라우드(LiDAR Point Cloud), 위치추정 데이터(Localization Data), 생산 정보, 사용자 상호작용, 유지보수 기록, 자격증명(Credential), 암호화 키(Cryptographic Key), 독점 AI 모델(Proprietary AI Model)을 지속적으로 처리한다. 이러한 자산이 노출되면 민감한 환경, 지식재산권(Intellectual Property), 운영 절차 또는 공격자가 이후 더욱 정교한 공격을 준비하는 데 활용할 수 있는 정보가 유출될 수 있다.

로봇의 기밀성은 전체 데이터 수명주기(Data Lifecycle)에 걸쳐 유지되어야 한다. 센서 정보는 장치에서 생성되어 ROS 2 또는 DDS와 같은 미들웨어(Middleware)를 통과하고, 엣지 컴퓨터(Edge Computer)에서 처리된 후 플릿 서버(Fleet Server)로 전송되어 최종적으로 클라우드(Cloud) 또는 온프레미스(On-Premise) 인프라에 저장될 수 있다. 따라서 저장 데이터(Data at Rest)와 전송 데이터(Data in Transit)에 적절한 접근 제어와 암호화를 적용해야 하며, 자격증명과 암호학적 자료(Cryptographic Material)는 특히 강력한 저장 및 수명주기 통제가 필요하다.

기밀성은 중요한 물리적 측면도 가지고 있다. 이동 로봇(Mobile Robot), 휴머노이드(Humanoid), 무인항공기(UAV), 서비스 로봇(Service Robot)은 사람, 산업 공정, 제한된 장비 또는 기밀 문서가 존재하는 공간에서 작동할 수 있다. 카메라와 마이크는 로봇의 임무에 필요한 범위를 넘어서는 정보를 의도하지 않게 수집할 수 있다. 따라서 보안 아키텍처(Security Architecture)는 사이버보안 통제와 함께 데이터 최소화(Data Minimization), 보존 정책(Retention Policy), 인가 경계(Authorization Boundary), 통제된 텔레메트리 수집(Controlled Telemetry Collection)을 결합해야 한다.

무결성(Integrity)은 정보, 소프트웨어, 명령 및 시스템 상태가 정확하게 유지되고 인가된 메커니즘을 통해서만 변경되도록 보장한다. 로봇 시스템에서 무결성은 손상된 정보가 물리적 행동을 직접 변화시킬 수 있기 때문에 기밀성보다 안전에 더 중요한 경우가 많다. 조작된 속도 명령, 내비게이션 목표(Navigation Goal), 보정 파라미터(Calibration Parameter), 액추에이터 제한값, 지도, 궤적(Trajectory), 안전 설정은 모든 구성요소가 정상적으로 작동하는 상황에서도 로봇이 잘못된 행동을 수행하도록 만들 수 있다.

센서 무결성(Sensor Integrity)은 자율 로봇이 관측 정보로부터 주변 환경에 대한 이해를 구축하기 때문에 특히 중요하다. 위조된 위성항법시스템(GNSS) 신호, 변경된 카메라 이미지, 조작된 라이다 측정값, 손상된 관성측정장치(IMU) 데이터 또는 변조된 위치추정 정보는 인지(Perception)와 계획(Planning)에 영향을 미칠 수 있다. 다중 센서 융합(Multi-Sensor Fusion)도 이 문제를 자동으로 해결하지는 못한다. 손상된 입력이 추정 알고리즘(Estimation Algorithm)을 통해 전파되어 그럴듯하지만 잘못된 물리 세계 표현을 생성할 수 있기 때문이다.

명령 무결성(Command Integrity)은 계산 결과가 물리적 행동으로 전환되는 과정을 보호한다. 운영자, 플릿 관리자(Fleet Manager), 플래너(Planner), AI 에이전트(AI Agent), 클라우드 서비스에서 생성되는 명령은 신뢰할 수 있는 신원과 연결되어야 하며 비인가 변경으로부터 보호되어야 한다. 인증(Authentication), 인가(Authorization), 암호학적 서명(Cryptographic Signing), 메시지 무결성 검증(Message Integrity Verification), 재전송 공격 방지(Replay Protection), 시퀀스 검증(Sequence Validation), 명확하게 정의된 명령 인터페이스는 로봇이 적법하고 인가된 출처의 명령을 실행하도록 지원한다.

소프트웨어 및 펌웨어 무결성(Software and Firmware Integrity)은 이러한 원칙을 전체 실행 스택(Execution Stack)으로 확장한다. 부트로더(Bootloader), 운영체제, 장치 드라이버(Device Driver), ROS 2 노드(Node), 컨테이너(Container), 제어 애플리케이션, AI 모델, 설정 파일, 펌웨어는 승인된 버전과 일치해야 한다. 보안 부팅(Secure Boot), 측정 부팅(Measured Boot), 서명된 소프트웨어 패키지(Signed Software Package), 보호된 업데이트 메커니즘, 해시(Hash), 신뢰할 수 있는 저장소(Trusted Repository), 롤백 방지(Anti-Rollback)는 초기 부팅에서 애플리케이션 실행까지 이어지는 신뢰 체인(Chain of Trust)을 구축할 수 있다.

AI는 추가적인 무결성 요구사항을 발생시킨다. 로봇은 기술적으로는 정상적인 모델을 실행하더라도 오염된 학습 데이터(Poisoned Training Data), 비인가 미세조정(Unauthorized Fine-Tuning), 모델 대체(Model Substitution), 조작된 프롬프트(Manipulated Prompt), 적대적 입력(Adversarial Input)을 통해 모델의 행동 자체가 손상될 수 있다. 따라서 모델 출처(Model Provenance), 데이터셋 거버넌스(Dataset Governance), 서명된 모델 아티팩트(Signed Model Artifact), 보안 모델 로딩(Secure Loading), 추론 모니터링(Inference Monitoring), 독립적인 안전 경계(Independent Safety Boundary)는 피지컬 AI(Physical AI) 시스템에서 기존 무결성 통제를 확장하는 핵심 요소가 된다.

가용성(Availability)은 인가된 사용자와 시스템 구성요소가 필요한 시점에 요구되는 서비스와 자원을 사용할 수 있도록 보장한다. 로봇의 가용성은 지연된 계산이나 통신 자체가 장애와 동일한 결과를 초래할 수 있다는 점에서 일반적인 IT 가용성과 다르다. 몇 초 늦게 응답하는 내비게이션 서비스, 정지된 인지 파이프라인(Perception Pipeline), 사용할 수 없는 안전 제어기(Safety Controller), 혼잡한 명령 채널(Command Channel)은 해당 구성요소가 이후 복구되더라도 위험한 상황을 발생시킬 수 있다.

가용성에 대한 위협에는 서비스 거부 공격(Denial-of-Service Attack), 무선 간섭(Wireless Interference), 네트워크 혼잡(Network Congestion), 자원 고갈(Resource Exhaustion), 소프트웨어 충돌, 랜섬웨어(Ransomware), 클라우드 장애, 인증서 오류, 저장공간 고갈, 악의적인 워크로드 생성(Malicious Workload Generation)이 포함된다. 엣지 AI(Edge AI) 시스템에서는 비정상적인 워크로드로 인해 GPU 또는 메모리 자원이 고갈될 수도 있다. 많은 로봇이 동일한 인증 서비스, 메시지 브로커(Message Broker), 지도 서버 또는 중앙집중형 임무 관리 플랫폼에 의존하는 경우 플릿 아키텍처(Fleet Architecture)는 이러한 문제를 더욱 확대할 수 있다.

따라서 가용성은 복원력(Resilience)과 함께 설계되어야 한다. 로봇에는 이중화된 통신 경로(Redundant Communication Path), 로컬 폴백 동작(Local Fallback Behavior), 워치독(Watchdog), 상태 모니터링(Health Monitoring), 성능 저하 운용 모드(Degraded Operating Mode), 자원 격리(Resource Isolation), 장애조치 서비스(Failover Service), 안전 정지 메커니즘(Safe-Stop Mechanism)이 필요할 수 있다. 중요 기능은 불필요하게 원격 인프라에 의존해서는 안 되며, 클라우드 연결이 사라질 경우 로봇은 예측 불가능한 상태로 진입하는 대신 사전에 정의된 운영 및 안전 정책에 따라 상태를 전환해야 한다.

세 가지 CIA 속성은 서로 밀접하게 연결되어 있으며 때로는 서로 경쟁하기도 한다. 강력한 암호화는 기밀성과 무결성을 보호하지만 계산 지연(Computational Latency)을 증가시킬 수 있다. 적극적인 네트워크 격리(Network Isolation)는 공격 노출을 줄일 수 있지만 진단이나 플릿 협업(Fleet Coordination)을 방해할 수 있다. 높은 가용성을 제공하는 원격 유지보수 인터페이스는 비인가 접근 위험을 증가시킬 수 있다. 따라서 로봇 보안 엔지니어링(Robot Security Engineering)은 임무 중요도, 물리적 결과, 타이밍 요구사항 및 시스템 아키텍처에 따라 CIA 목표 사이의 균형을 조정해야 한다.

각 로봇 자산에는 서로 다른 CIA 우선순위가 적용될 수 있다. 독점 AI 모델이나 민감한 센서 기록에는 기밀성이 가장 중요할 수 있는 반면, 액추에이터 명령, 안전 파라미터, 지도 및 펌웨어에서는 무결성이 우선될 수 있다. 비상 정지 통신(Emergency-Stop Communication), 실시간 제어(Real-Time Control), 위치추정 및 필수 인지 서비스에서는 가용성이 가장 높은 우선순위를 가질 수 있다. 효과적인 보안 아키텍처는 각각의 중요 자산을 식별하고 각 CIA 속성이 상실되었을 때 발생하는 결과를 명확하게 결정한다.

이러한 결과는 순수한 디지털 지표가 아니라 사이버-물리 시나리오(Cyber-Physical Scenario)를 통해 평가되어야 한다. 기밀성 상실은 창고 지도를 노출시킬 수 있고, 지도 무결성 상실은 자율이동로봇(Autonomous Mobile Robot)을 제한 구역으로 유도할 수 있으며, 위치추정 가용성 상실은 동일한 로봇을 정지시킬 수 있다. 동일하거나 유사한 자산이라도 어떤 보안 속성이 손상되는지에 따라 근본적으로 다른 운영 결과가 발생하므로 각각에 적합한 예방 및 복구 통제가 필요하다.

CIA 트라이어드(CIA Triad)는 심층 방어(Defense-in-Depth)와 이후의 로봇 사이버보안 분석을 위한 기반도 제공한다. 네트워크 분할(Network Segmentation), 신원 관리(Identity Management), 보안 ROS 2 통신, 펌웨어 서명(Firmware Signing), 클라우드 보안, AI 모델 보호, 모니터링, 사고 대응(Incident Response), 보안 테스트(Security Testing)는 모두 기밀성, 무결성, 가용성 목표와 연결할 수 있다. 이러한 관계는 하드웨어, 소프트웨어, 네트워크, 클라우드 및 피지컬 AI 계층 전체의 사이버보안 요구사항을 연결하는 공통 언어를 제공한다.

현대 로봇에서 CIA 트라이어드는 궁극적으로 단순한 정보보안 모델(Information-Security Model)이 아니라 사이버-물리 보증 모델(Cyber-Physical Assurance Model)로 해석되어야 한다. 기밀성은 민감한 지식을 보호하고, 무결성은 신뢰할 수 있는 인지와 행동을 유지하며, 가용성은 필요한 기능이 필요한 시점에 제공되도록 보장한다. 이 세 가지 속성은 비인가된 디지털 영향이 허용할 수 없는 물리적 결과로 이어지지 않는 상태에서 로봇이 인지하고, 추론하고, 통신하고, 행동하기 위해 필요한 기본적인 보안 속성을 확립한다.

## 01.03. Attack Surface Analysis HW SW Network Physical

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

로봇 시스템의 공격 표면 분석(Attack Surface Analysis)은 공격자가 플랫폼과 상호작용하거나, 영향을 미치거나, 정보를 추출하거나, 시스템 운영을 방해할 수 있는 모든 지점을 식별하는 과정이다. 기존 컴퓨터 시스템과 달리 로봇은 하드웨어(Hardware), 소프트웨어(Software), 통신 네트워크(Communication Network), 클라우드 서비스(Cloud Service), 센서(Sensor), 액추에이터(Actuator), 주변 물리 환경(Physical Environment)에 걸쳐 공격 표면을 가진다. 따라서 보안 분석은 로봇을 개별 컴퓨터의 집합이 아니라 통합된 사이버-물리 시스템(Cyber-Physical System)으로 분석해야 한다.

하드웨어 공격 표면(Hardware Attack Surface)은 프로세서(Processor), 마이크로컨트롤러(Microcontroller), AI 가속기(AI Accelerator), 메모리 장치, 저장장치, 통신 모듈, 센서, 모터 제어기(Motor Controller), 전력 관리 구성요소에서 시작된다. JTAG, UART, USB 및 유지보수 포트(Maintenance Port)와 같은 디버그 인터페이스(Debug Interface)가 제품 환경에서도 활성화되어 있으면 높은 권한의 접근 경로가 될 수 있다. 이동식 저장장치, 노출된 커넥터 및 제대로 보호되지 않은 내부 버스(Internal Bus) 역시 민감한 데이터나 펌웨어를 추출하거나 변경할 수 있는 경로를 제공할 수 있다.

하드웨어 보안 분석(Hardware Security Analysis)은 부팅 과정(Boot Process)과 장치의 신뢰 루트(Root of Trust)도 고려해야 한다. 공격자가 부트로더(Bootloader)를 교체하거나, 플래시 메모리에 저장된 펌웨어를 변경하거나, 서명 검증(Signature Verification)을 우회하거나, 안전하지 않은 저장장치에서 암호화 키(Cryptographic Key)를 획득할 수 있다면 상위 소프트웨어 계층도 더 이상 신뢰하기 어렵다. 보안 부팅(Secure Boot), 하드웨어 기반 키 저장소(Hardware-Backed Key Storage), 보호된 디버그 인터페이스, 측정 부팅(Measured Boot), 변조 방지 설계(Tamper-Resistant Design)는 지속적인 시스템 침해 가능성을 줄여준다.

센서는 로봇이 외부 세계를 관찰하는 데 의존하기 때문에 독특한 하드웨어 및 물리적 공격 표면(Hardware and Physical Attack Surface)을 형성한다. 카메라, 라이다(LiDAR), 레이더(Radar), 위성항법시스템 수신기(GNSS Receiver), 관성측정장치(IMU), 마이크, 힘 센서(Force Sensor), 엔코더(Encoder), 근접 센서(Proximity Sensor)는 신뢰된 디지털 채널에서만 정보를 받는 것이 아니라 주변 환경에서 직접 정보를 받아들인다. 공격자는 스푸핑(Spoofing), 블라인딩(Blinding), 간섭(Interference), 신호 주입(Signal Injection), 가림(Obstruction), 물리적 위치 변경을 통해 로봇 소프트웨어를 직접 침해하지 않고도 잘못된 관측 결과를 유도할 수 있다.

소프트웨어 공격 표면(Software Attack Surface)은 부트로더, 펌웨어, 운영체제, 장치 드라이버(Device Driver), 미들웨어(Middleware), 로봇 애플리케이션, 라이브러리, 컨테이너(Container), AI 런타임(AI Runtime), 설정 파일 및 관리 유틸리티(Management Utility)에 걸쳐 존재한다. 메모리 손상(Memory Corruption), 안전하지 않은 권한 설정, 취약한 인증, 노출된 서비스, 안전하지 않은 역직렬화(Insecure Deserialization), 명령어 주입(Command Injection), 의존성 취약점(Dependency Flaw), 설정 오류 등이 침입 지점이 될 수 있다. 실행 가능한 구성요소나 높은 권한의 서비스가 추가될 때마다 신뢰하고 유지관리해야 하는 소프트웨어의 범위도 확대된다.

ROS 2와 DDS는 분산 통신 인터페이스(Distributed Communication Interface)를 제공하므로 소프트웨어 공격 표면 분석에 포함되어야 한다. 노드(Node)는 토픽(Topic), 서비스(Service), 액션(Action), 디스커버리 기능(Discovery Function), 파라미터(Parameter) 및 기타 통신 메커니즘을 외부에 제공한다. 적절하게 보호되지 않은 참여자(Participant)는 잘못된 데이터를 발행하거나 민감한 정보를 구독하고, 서비스를 호출하거나 디스커버리 과정을 방해할 수 있다. 따라서 보안 설정은 어떤 신원이 통신할 수 있는지와 각 참여자가 어떤 자원에 접근할 수 있는지를 명확하게 반영해야 한다.

로봇 API(Robot API)는 내부 기능과 외부 시스템 사이에 또 하나의 경계를 형성한다. REST 인터페이스, gRPC 서비스, 웹소켓(WebSocket) 연결, MQTT 브로커(MQTT Broker), 플릿 API(Fleet API), 진단 엔드포인트(Diagnostic Endpoint), 대시보드(Dashboard), 유지보수 도구는 강력한 로봇 기능을 외부에 노출할 수 있다. 인가 범위가 지나치게 넓다면 인증(Authentication)만으로는 충분하지 않다. API 분석에서는 신원, 권한, 입력 검증(Input Validation), 요청 속도 제한(Rate Limit), 세션 처리(Session Handling), 명령 범위(Command Scope), 감사 가능성(Auditability), 클라이언트가 침해되었을 때의 결과를 함께 검토해야 한다.

네트워크 공격 표면(Network Attack Surface)은 유선 이더넷(Ethernet), 와이파이(Wi-Fi), 블루투스(Bluetooth), 셀룰러 통신(Cellular Link), 프라이빗 5G(Private 5G), VPN 연결, 산업용 네트워크(Industrial Network), 원격 접근 채널(Remote Access Channel), 로봇 간 통신(Robot-to-Robot Communication)을 포함한다. 공격자는 노출된 포트, 취약한 프로토콜, 안전하지 않은 라우팅, 잘못 설정된 방화벽, 자격증명 탈취, 스푸핑, 재전송 공격(Replay Attack), 통신 가로채기, 서비스 거부(Denial-of-Service)를 악용할 수 있다. 특히 평면형 네트워크(Flat Network)는 하나의 구성요소 침해가 더 중요한 시스템으로의 측면 이동(Lateral Movement)을 가능하게 할 수 있어 위험하다.

따라서 네트워크 아키텍처(Network Architecture)는 개별 장치뿐만 아니라 보안 구역(Zone), 통신 경로(Conduit), 신뢰 경계(Trust Boundary), 데이터 흐름(Data Flow)을 중심으로 분석해야 한다. 안전 제어(Safety Control), 로봇 관리, AI 데이터 처리, 기업 IT(Enterprise IT), 개발 환경, 클라우드 연결, 게스트 또는 유지보수 접근이 자동으로 동일한 신뢰 수준을 공유해서는 안 된다. 네트워크 분할(Network Segmentation), 접근제어목록(Access-Control List), 방화벽, 암호화 터널(Encrypted Tunnel), 네트워크 접근 제어(Network Access Control), 모니터링은 침입이 전파될 수 있는 범위를 제한할 수 있다.

무선 통신(Wireless Communication)은 물리적으로 연결된 인프라를 넘어 공격 표면을 확대한다. 무선 신호가 통제된 운영 영역 밖까지 전달되면 공격자는 시설 내부에 들어오지 않고도 시스템과 상호작용할 수 있다. 인증, 현대적인 암호화, 인증서 기반 장치 신원(Certificate-Based Device Identity), 보안 페어링(Secure Pairing), 간섭 모니터링(Interference Monitoring), 신중하게 통제된 폴백 동작(Fallback Behavior)이 중요하다. 무선 연결의 상실이나 조작은 사이버보안뿐만 아니라 로봇의 가용성(Availability)에도 영향을 줄 수 있기 때문이다.

클라우드 및 플릿 관리 인프라(Cloud and Fleet-Management Infrastructure)는 로봇의 공격 표면을 물리적 기계의 범위를 훨씬 넘어 확장한다. 장치 레지스트리(Device Registry), 신원 서비스(Identity Service), 데이터베이스, 메시지 브로커(Message Broker), 객체 저장소(Object Storage), 텔레메트리 파이프라인(Telemetry Pipeline), 대시보드, 원격 제어 서비스, OTA 플랫폼은 수백 또는 수천 대의 로봇과 통신할 수 있다. 따라서 중앙집중형 서비스가 침해되면 다수의 분산된 물리 시스템에 동시에 영향을 줄 수 있는 높은 파급력의 공격 지점(High-Leverage Attack Point)이 될 수 있다.

피지컬 AI 공격 표면(Physical AI Attack Surface)은 기존 보안 경계에 모델(Model), 데이터셋(Dataset), 프롬프트(Prompt), 멀티모달 입력(Multimodal Input), 추론 엔진(Inference Engine), 모델 레지스트리(Model Registry), AI 에이전트 인터페이스(AI-Agent Interface)를 추가한다. 조작된 입력만으로 AI 시스템이 위험한 결정을 생성하도록 만들 수 있다면 공격자가 운영체제를 직접 침해할 필요가 없을 수도 있다. 적대적 관측(Adversarial Observation), 모델 대체(Model Substitution), 데이터 오염(Data Poisoning), 프롬프트 인젝션(Prompt Injection), 비인가 모델 변경은 AI의 행동 자체를 로봇 보안 표면의 일부로 분석해야 하는 이유를 보여준다.

물리적 공격 표면(Physical Attack Surface)은 외함(Enclosure), 비상 제어 장치(Emergency Control), 충전소(Charging Station), 도킹 인터페이스(Docking Interface), 유지보수 패널, 노출된 케이블, 센서, 액추에이터 및 접근 가능한 컴퓨팅 장비를 포함한다. 물리적으로 접근할 수 있는 공격자는 센서를 분리하고, 비인가 주변장치를 연결하거나, 구성요소를 교체하고, 저장 매체를 복제하거나, 스위치를 조작하고, 기계 시스템에 간섭할 수 있다. 따라서 물리적 보안 통제(Physical Security Control)는 디지털 보호와 분리된 문제가 아니라 이를 보완하는 요소로 설계되어야 한다.

액추에이터(Actuator)는 디지털 명령이 물리적인 힘과 움직임으로 변환되는 최종 사이버-물리 경계(Cyber-Physical Boundary)를 형성한다. 모터, 조향 시스템(Steering System), 매니퓰레이터(Manipulator), 그리퍼(Gripper), 비행 제어면(Flight-Control Surface), 브레이크 및 기타 구동 메커니즘에는 엄격한 명령 권한(Command Authority) 통제가 필요하다. 상위 소프트웨어가 침해된 경우에도 독립적인 제한값, 안전 제어기(Safety Controller), 비상 정지 메커니즘(Emergency-Stop Mechanism), 워치독(Watchdog), 하드웨어 인터록(Hardware Interlock)을 통해 악성 명령이 초래하는 물리적 결과를 줄일 수 있다.

공격 표면 분석에는 공급망 및 수명주기 인터페이스(Supply-Chain and Lifecycle Interface)도 포함되어야 한다. 제조 도구, 개발용 노트북, 소프트웨어 저장소, 서드파티 라이브러리(Third-Party Library), 펌웨어 서명 시스템(Firmware Signing System), 공장 프로비저닝(Factory Provisioning), 유지보수 장비, OTA 인프라, 폐기 절차(Decommissioning Procedure)는 배포 이전 또는 정상 운영이 시작된 이후에도 취약점을 유입시킬 수 있다. 런타임(Runtime)에서 안전한 로봇이라도 개발, 업데이트 또는 서비스 과정이 충분히 보호되지 않으면 침해될 수 있다.

실용적인 공격 표면 분석은 자산(Asset), 인터페이스, 신뢰 경계, 권한, 통신 경로, 물리적 접근 지점, 의존성(Dependency)을 매핑한 다음 침해가 이들 사이에서 어떻게 전파될 수 있는지를 평가한다. 노출된 유지보수 포트가 펌웨어 접근으로 이어지고, 침해된 펌웨어가 자격증명을 노출하며, 탈취된 자격증명이 네트워크 접근을 허용하고, 네트워크 접근이 플릿 서비스 침해로 이어져 다수의 로봇에 영향을 줄 수 있다. 따라서 공격 표면은 서로 독립된 취약점이 아니라 연결된 공격 경로(Attack Path)로 분석해야 한다.

목표는 모든 인터페이스를 제거하는 것이 아니다. 연결성, 센서, API, 원격 유지보수 및 AI 기능은 현대 로보틱스에 필수적이기 때문이다. 대신 불필요한 인터페이스는 제거하고, 필요한 인터페이스는 최소화하며, 권한은 제한하고, 통신은 인증하며, 소프트웨어는 지속적으로 유지관리하고, 물리적 접근은 통제하며, 중요 경계는 독립적으로 모니터링해야 한다. 이러한 접근 방식은 로봇의 전체 수명주기에 걸쳐 심층 방어(Defense-in-Depth), 제로 트러스트(Zero Trust), 위협 모델링(Threat Modeling), 보안 테스트(Security Testing), 사이버-물리 위험 관리(Cyber-Physical Risk Management)를 수행하기 위한 기반을 확립한다.

## 01.04. Cybersecurity Standards IEC 62443 ISO 21434 Overview

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

IEC 62443과 ISO/SAE 21434는 현대 로봇 시스템을 위한 두 가지 중요한 사이버보안(Cybersecurity) 관점을 제공한다. IEC 62443은 산업 자동화 및 제어 시스템 보안(Industrial Automation and Control System Security)에서 출발한 반면, ISO/SAE 21434는 도로 차량(Road Vehicle)을 위한 사이버보안 엔지니어링(Cybersecurity Engineering)을 다룬다. 로봇은 산업 장비, 자율주행 차량, 임베디드 컴퓨터(Embedded Computer), 연결형 장치(Connected Device), 클라우드 관리 플랫폼(Cloud-Managed Platform)의 특성을 복합적으로 가지므로 체계적인 사이버보안 엔지니어링 프로그램을 구축할 때 두 표준의 개념을 모두 유용하게 활용할 수 있다.

IEC 62443는 사이버보안을 자산 소유자(Asset Owner), 시스템 통합자(System Integrator), 제품 공급업체(Product Supplier), 서비스 제공업체(Service Provider)에 걸쳐 공유되는 시스템 수준의 책임(System-Level Responsibility)으로 다룬다. 이러한 관점은 산업용 로봇, 자율이동로봇(Autonomous Mobile Robot), 창고 플릿(Warehouse Fleet), 제조 셀(Manufacturing Cell), 운영 기술(Operational Technology) 환경에서 동작하는 기타 시스템에 매우 적합하다. 보안은 개별 장치 보호만으로 한정되지 않으며 조직 프로세스, 시스템 아키텍처, 구성요소 기능, 수명주기 활동 및 운영 통제가 함께 작동해야 한다.

IEC 62443의 핵심 개념 중 하나는 산업 시스템을 보안 구역(Zone)과 통신 경로(Conduit)로 분리하는 것이다. 보안 구역은 유사한 보안 요구사항을 공유하는 자산을 그룹화하며, 통신 경로는 구역 사이의 통제된 통신을 의미한다. 이를 로보틱스에 적용하면 안전 제어기(Safety Controller), 모션 제어기(Motion Controller), 인지 컴퓨터(Perception Computer), 플릿 서버(Fleet Server), 엔지니어링 워크스테이션(Engineering Workstation), 기업 시스템, 클라우드 서비스, 유지보수 네트워크를 하나의 제한 없는 네트워크에 배치하는 대신 기능, 중요도 및 신뢰 가정(Trust Assumption)에 따라 분리할 수 있다.

이러한 보안 구역 및 통신 경로 모델(Zone-and-Conduit Model)은 불필요한 연결을 제한하고 침해 이후의 측면 이동(Lateral Movement)을 감소시킴으로써 심층 방어(Defense-in-Depth)를 지원한다. 예를 들어 대용량 센서 데이터를 처리하는 인지 컴퓨터가 안전 제어기에 제한 없이 접근할 필요는 없다. 마찬가지로 유지보수용 노트북이 인증된 로봇 제어기와 동일한 권한을 자동으로 가져서는 안 된다. 방화벽, 네트워크 분할(Network Segmentation), 인증된 통신, 접근 정책(Access Policy), 모니터링 게이트웨이(Monitored Gateway)를 통해 의도된 보안 경계를 강제할 수 있다.

IEC 62443는 다양한 공격자 유형과 공격 정교성(Attack Sophistication)에 대한 저항 수준이 증가하는 보안 수준(Security Level) 개념도 제시한다. 적절한 수준은 모든 구성요소에 최고 수준의 보호를 일률적으로 적용하는 것이 아니라 위험(Risk)에 따라 결정된다. 로봇 엔지니어링에서는 각 보안 구역, 시스템 또는 구성요소의 보안 요구사항을 결정하기 전에 침해 결과, 공격자 능력, 노출 수준, 운영 환경 및 기존 보호조치를 평가하도록 한다.

IEC 62443와 관련된 기본 요구사항(Foundational Requirement)은 식별 및 인증 제어(Identification and Authentication Control), 사용 제어(Use Control), 시스템 무결성(System Integrity), 데이터 기밀성(Data Confidentiality), 제한된 데이터 흐름(Restricted Data Flow), 이벤트에 대한 적시 대응(Timely Response to Events), 자원 가용성(Resource Availability)과 같은 주요 보안 목표를 다룬다. 이러한 목표는 로봇 시스템의 장치 신원, 운영자 권한, 명령 무결성, 네트워크 분할, 보안 모니터링, 보호된 텔레메트리(Telemetry), 소프트웨어 무결성 및 서비스 거부(Denial-of-Service) 상황에 대한 복원력과 자연스럽게 연결된다.

IEC 62443는 보안 제품 개발(Secure Product Development)과 수명주기 프로세스(Lifecycle Process)도 강조한다. 사이버보안은 배포 직전에 추가되는 기능이 아니라 요구사항 및 아키텍처 단계부터 시작되어야 한다. 위협 분석(Threat Analysis), 보안 설계, 구현 방법, 취약점 관리(Vulnerability Management), 검증(Verification), 보안 문서화, 패치 프로세스(Patch Process), 유지보수 책임은 제품의 전체 수명주기에 걸쳐 지속되어야 한다. 이는 소프트웨어 의존성과 위협 환경이 계속 변화하는 상황에서 수년 동안 운영되는 로봇에 특히 중요하다.

ISO/SAE 21434는 차량의 전기·전자 시스템(Electrical and Electronic System)과 해당 엔지니어링 수명주기 관점에서 사이버보안을 접근한다. 이 표준의 개념은 분산 전자제어장치(Electronic Control Unit), 센서, 통신 네트워크, 연결 모듈(Connectivity Module), 소프트웨어 중심 기능, 원격 서비스, 안전 관련 제어 동작 등 현대 차량과 유사한 아키텍처 특성을 가진 이동 로봇(Mobile Robot) 및 자율 플랫폼(Autonomous Platform)에 특히 유용하다.

ISO/SAE 21434의 주요 개념 중 하나는 일반적으로 TARA라고 부르는 위협 분석 및 위험 평가(Threat Analysis and Risk Assessment)이다. 엔지니어는 자산(Asset), 피해 시나리오(Damage Scenario), 위협 시나리오(Threat Scenario), 공격 경로(Attack Path)를 식별한 다음 관련 요소를 평가하여 사이버보안 위험과 적절한 위험 처리 방안을 결정한다. 로봇의 자산에는 제어 명령, 위치추정 정보(Localization Information), 센서 데이터, 펌웨어, 암호학적 자격증명(Cryptographic Credential), AI 모델, 임무 정보 또는 침해될 경우 운영적·물리적 결과를 발생시킬 수 있는 통신 채널이 포함될 수 있다.

피해 시나리오는 사이버보안 이벤트를 이해관계자(Stakeholder)에게 중요한 실제 결과와 연결한다. 따라서 침해된 로봇은 단순히 데이터가 변경되었는지 또는 네트워크 서비스에 접근했는지만으로 평가하지 않는다. 엔지니어는 조향(Steering), 제동(Braking), 모션 제어(Motion Control), 내비게이션(Navigation), 인지(Perception), 원격 명령(Remote Command)이 조작되었을 때 어떤 결과가 발생할 수 있는지를 고려한다. 이러한 사이버-물리적 해석(Cyber-Physical Interpretation)은 로봇의 사이버보안 실패가 디지털 침해에서 위험한 물리적 행동으로 전파될 수 있기 때문에 특히 중요하다.

공격 경로 분석(Attack-Path Analysis)은 공격자가 접근 가능한 인터페이스에서 보호 대상 자산까지 어떻게 이동할 수 있는지를 분석한다. 무선 인터페이스가 통신 서비스에 대한 접근을 제공하고, 해당 서비스의 소프트웨어 취약점이 악용되며, 이를 통해 권한 상승(Privilege Escalation)이 발생한 후 최종적으로 제어 기능에 도달할 수 있다. 이러한 공격 과정을 모델링하면 보안이 하나의 방화벽, 비밀번호, 암호화 메커니즘 또는 소프트웨어 구성요소가 아니라 서로 연결된 다수의 방어 장벽에 의존한다는 점을 이해할 수 있다.

ISO/SAE 21434는 개발 과정 전반에 걸친 사이버보안 목표(Cybersecurity Goal), 사이버보안 요구사항(Cybersecurity Requirement), 검증(Verification), 유효성 확인(Validation), 추적성(Traceability)도 강조한다. 상위 수준의 위험 처리 방안은 구현하고 시험할 수 있는 기술적 요구사항으로 변환되어야 한다. 예를 들어 비인가 모션 명령을 방지한다는 로봇 플랫폼 요구사항은 인증된 장치 신원, 인가 정책, 메시지 무결성 보호, 재전송 방지(Replay Prevention), 명령 검증, 모니터링 및 독립적인 안전 제한 조건으로 구체화될 수 있다.

IEC 62443과 ISO/SAE 21434는 모두 제품이 서비스에 투입된 이후에도 취약점과 위협이 계속 변화하기 때문에 수명주기 사이버보안(Lifecycle Cybersecurity)을 강조한다. 소프트웨어 업데이트, 새롭게 발견된 취약점, 변경된 설정, 교체된 구성요소, 서드파티 의존성(Third-Party Dependency), 원격 서비스 및 운영 변경은 최초의 위험 가정을 변화시킬 수 있다. 따라서 로봇 제조업체와 운영자는 운영 수명 전체에 걸쳐 취약점 모니터링, 사고 처리(Incident Handling), 보안 업데이트 메커니즘, 설정 관리(Configuration Management), 사이버보안 유지 프로세스를 운영해야 한다.

두 프레임워크(Framework)는 서로 대체하는 관계가 아니라 상호 보완적이다. IEC 62443는 산업 자동화 환경, 분할된 운영 네트워크, 산업용 구성요소, 자산 소유자와 시스템 통합자 및 공급업체 사이의 관계를 다루는 데 특히 유용하다. ISO/SAE 21434는 차량 중심의 강력한 사이버보안 엔지니어링 수명주기와 체계적인 위협 및 위험 분석 관점을 제공한다. 따라서 이동형 산업 로봇은 공장 및 인프라 수준에서는 IEC 62443 원칙을 활용하면서 플랫폼 수준 위험 엔지니어링에는 ISO/SAE 21434 개념을 활용할 수 있다.

어느 프레임워크도 로봇 아키텍처를 이해하지 않은 상태에서 기계적인 체크리스트(Checklist) 방식으로 적용해서는 안 된다. 고정형 매니퓰레이터(Stationary Manipulator), 창고 자율이동로봇(Warehouse AMR), 실외 검사 로봇(Outdoor Inspection Robot), 휴머노이드(Humanoid), 화물 무인항공기(Cargo UAV)는 서로 다른 인터페이스, 물리적 결과, 통신 의존성 및 공격 기회를 가진다. 표준은 구조화된 프로세스와 보안 개념을 제공하지만 엔지니어링 팀은 실제 자산, 신뢰 경계, 공격 경로, 안전 기능 및 운영 환경에 따라 이를 아키텍처별 보안 통제(Architecture-Specific Security Control)로 변환해야 한다.

피지컬 AI(Physical AI) 시스템에서는 기존 사이버보안 표준을 새롭게 등장하는 AI 특화 위험(AI-Specific Risk)과 연결할 필요가 있다. 신원, 네트워크, 소프트웨어, 펌웨어, 업데이트 및 통신을 보호하기 위한 기존 통제는 여전히 필요하지만 AI 모델은 모델 출처(Model Provenance), 학습 데이터, 적대적 입력(Adversarial Input), 모델 대체(Model Substitution), 추론 무결성(Inference Integrity), AI 에이전트 권한(AI-Agent Authority)과 관련된 추가적인 문제를 발생시킨다. 이러한 위험은 별도의 AI 보안 활동으로 분리하기보다 동일한 수명주기 관리 체계에 통합해야 한다.

로봇 사이버보안 엔지니어링에서 IEC 62443과 ISO/SAE 21434가 제공하는 가장 중요한 가치는 임시방편적인 보호(Ad Hoc Protection)에서 체계적인 보증(Systematic Assurance)으로 전환할 수 있도록 하는 것이다. 보안은 위험 평가, 아키텍처, 요구사항, 구현, 검증, 배포, 모니터링, 취약점 관리 및 유지보수를 연결하는 추적 가능한 프로세스(Traceable Process)가 된다. 이러한 기반은 로봇 전체 수명주기에 걸쳐 제로 트러스트(Zero Trust), 보안 ROS 2 통신, 플릿 보안(Fleet Security), OTA 보호, 사이버보안 테스트, 사고 대응 및 규정 준수 평가(Compliance Assessment)를 수행하기 위한 토대를 제공한다.

## 01.05. Defense in Depth for Robot Architecture [w/Code]

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

심층 방어(Defense in Depth)는 하나의 방어 메커니즘에 의존하는 대신 서로 독립적이고 상호 보완적인 여러 보안 통제(Security Control)를 통해 로봇을 보호하는 사이버보안 아키텍처(Cybersecurity Architecture) 원칙이다. 현대 로봇은 하드웨어, 펌웨어, 운영체제, 미들웨어(Middleware), 네트워크, AI 모델, 클라우드 서비스, 물리적 액추에이터(Physical Actuator)로 구성된다. 각 계층은 장애가 발생하거나 침해될 수 있으므로 하나의 보호 경계가 우회되더라도 보안 기능이 계속 유지되어야 한다.

심층 방어의 핵심 가정은 완벽한 보안 통제는 존재하지 않는다는 것이다. 인증 자격증명(Authentication Credential)은 탈취될 수 있고, 소프트웨어에는 알려지지 않은 취약점이 존재할 수 있으며, 인증서(Certificate)가 잘못 설정되거나 신뢰된 장치가 침해될 수도 있다. 따라서 로봇 아키텍처는 노출된 각각의 인터페이스 뒤에 추가적인 방어 장벽을 배치해야 한다. 공격자가 하나의 경계를 통과하더라도 제한된 권한, 분할된 네트워크, 무결성 검사(Integrity Check), 모니터링, 독립적인 안전 통제(Safety Control)를 추가로 통과해야 한다.

첫 번째 방어 계층은 물리적 하드웨어와 장치의 신뢰 루트(Root of Trust)에서 시작된다. 양산 로봇은 디버그 포트(Debug Port)를 제한하고, 이동식 저장장치를 보호하며, 물리적 유지보수 인터페이스를 통제하고, 적절한 하드웨어 기반 메커니즘을 사용하여 암호학적 자료(Cryptographic Material)를 보호해야 한다. 보안 부팅(Secure Boot)과 측정 부팅(Measured Boot)은 펌웨어와 시스템 소프트웨어가 실행되기 전에 교체되지 않았음을 확인하여 상위 소프트웨어 계층을 위한 신뢰 기반을 구축할 수 있다.

펌웨어 및 운영체제 보호는 다음 방어 계층을 구성한다. 서명된 펌웨어(Signed Firmware), 롤백 방지(Anti-Rollback) 메커니즘, 보호된 업데이트 절차, 최소 권한 서비스(Least-Privilege Service), 강화된 운영체제 설정, 애플리케이션 격리(Application Isolation), 적시 취약점 개선(Timely Vulnerability Remediation)은 지속적인 시스템 침해 가능성을 줄인다. 불필요한 서비스, 기본 계정(Default Account), 개발 유틸리티, 사용하지 않는 네트워크 리스너(Network Listener)는 추가적인 고권한 구성요소가 공격 표면을 확대하므로 제거해야 한다.

신원(Identity)은 또 하나의 핵심적인 방어 경계를 제공한다. 로봇, 운영자, 서비스, 엔지니어링 도구, 클라우드 애플리케이션, 자동화 에이전트(Automated Agent)는 네트워크 위치에만 의존하지 않고 식별 가능한 보안 주체(Security Principal)를 가져야 한다. 강력한 인증(Authentication), 장치 인증서(Device Certificate), 보호된 자격증명, 역할 기반 또는 속성 기반 인가(Role-Based or Attribute-Based Authorization), 가능한 경우 수명이 짧은 자격증명(Short-Lived Credential), 통제된 권한 상승(Controlled Privilege Elevation)은 하나의 신원이 침해되었을 때 전체 시스템 권한까지 자동으로 획득하는 것을 방지한다.

네트워크 분할(Network Segmentation)은 하나의 구성요소 침해가 전체 로봇 환경의 침해로 확대되는 것을 방지한다. 안전 제어(Safety Control), 모션 제어(Motion Control), 인지(Perception), AI 컴퓨팅, 플릿 관리(Fleet Management), 기업 IT(Enterprise IT), 클라우드 접근, 개발 시스템, 유지보수 네트워크를 신뢰 수준과 중요도에 따라 분리할 수 있다. 방화벽, 접근제어목록(Access-Control List), 인증된 게이트웨이(Authenticated Gateway), 암호화 터널(Encrypted Tunnel), 제한된 라우팅(Restricted Routing)을 통해 이러한 보안 구역 사이의 통신 경로를 강제할 수 있다.

ROS 2와 DDS는 네트워크 격리만으로 어떤 노드가 특정 정보를 교환할 수 있는지를 결정할 수 없기 때문에 미들웨어 계층(Middleware Layer)의 방어가 필요하다. 인증은 참여자의 신원을 확인하고, 암호화는 통신을 보호하며, 접근 제어 정책(Access-Control Policy)은 토픽(Topic), 서비스(Service), 액션(Action)에 대한 접근을 제한할 수 있다. 예를 들어 침해된 인지 노드(Perception Node)가 로봇 네트워크에 존재한다는 이유만으로 안전 필수 모션 명령(Safety-Critical Motion Command)을 실행할 권한까지 자동으로 부여받아서는 안 된다.

애플리케이션 수준 통제(Application-Level Control)는 운영체제와 미들웨어 방어 이후에 추가적인 보안 장벽을 제공한다. 로봇 애플리케이션은 명령, 파라미터(Parameter), 센서 메시지, 파일 형식, API 요청, 상태 전환(State Transition)을 사용하기 전에 검증해야 한다. 인가(Authorization)는 상위 게이트웨이에서 이미 수행되었다고 가정하지 말고 보호 대상 작업과 가까운 위치에서 다시 확인해야 한다. 요청 속도 제한(Rate Limiting), 범위 검사(Bounds Checking), 안전한 오류 처리(Secure Error Handling), 명시적인 명령 검증(Command Validation)은 악의적이거나 비정상적인 입력의 영향을 줄인다.

제어 아키텍처(Control Architecture)는 물리적 행동을 독립적으로 제한해야 한다. 계획 애플리케이션(Planning Application)이나 AI 에이전트(AI Agent)가 안전하지 않은 명령을 생성하더라도 하위 제어기는 속도, 가속도, 토크(Torque), 작업공간(Workspace), 지오펜스(Geofence), 액추에이터 제한값을 강제할 수 있다. 안전 제어기(Safety Controller), 워치독(Watchdog), 비상 정지 회로(Emergency-Stop Circuit), 하드웨어 인터록(Hardware Interlock), 독립적인 모니터링 기능은 침해된 디지털 의사결정과 위험한 물리적 움직임 사이에 추가적인 방어 장벽을 형성한다.

피지컬 AI(Physical AI)는 기존 네트워크 보안만으로 제공할 수 없는 추가적인 방어 계층을 필요로 한다. 모델 파일은 로딩 전에 인증되어야 하고, 모델 레지스트리(Model Registry)는 통제된 게시를 강제해야 하며, 학습 또는 적응 파이프라인(Adaptation Pipeline)은 데이터 출처(Data Provenance)를 보존해야 한다. 런타임 모니터링(Runtime Monitoring)은 비정상적인 입력이나 출력을 식별할 수 있으며, 결정론적 안전 제약(Deterministic Safety Constraint)은 학습 정책(Learned Policy), 비전-언어-행동 모델(Vision-Language-Action Model), 자율 AI 에이전트가 제안하는 행동을 제한할 수 있다.

클라우드 및 플릿 시스템(Cloud and Fleet System)은 중앙집중형 인프라가 다수의 로봇에 동시에 영향을 미칠 수 있으므로 자체적인 방어 계층이 필요하다. 장치 신원(Device Identity), 상호 인증(Mutual Authentication), API 인가, 테넌트 격리(Tenant Isolation), 명령 서명(Command Signing), 보호된 데이터베이스, 비밀정보 관리(Secrets Management), 보안 로깅(Security Logging), 관리자 권한 분리(Administrative Privilege Separation)를 통해 플릿 서비스를 보호해야 한다. 플릿 수준의 침해가 다수의 물리 플랫폼으로 확산될 수 있으므로 영향도가 높은 명령에는 더욱 강력한 검증이 필요할 수 있다.

무선 업데이트(Over-the-Air Update, OTA) 아키텍처도 중요한 방어 경계를 형성한다. 업데이트 패키지는 신뢰할 수 있는 저장소에서 제공되고 검증 가능한 디지털 서명(Digital Signature)을 포함하며 설치 전에 검증되어야 한다. 보안 부팅은 이후 시스템 시작 과정에서 설치된 소프트웨어를 검증할 수 있으며, 롤백 방지 메커니즘은 공격자가 취약한 이전 버전을 복원하는 것을 방지한다. 서명 인프라(Signing Infrastructure)와 배포 인프라(Distribution Infrastructure)를 분리하면 업데이트 전달 시스템이 침해되었을 때 발생하는 영향을 추가로 줄일 수 있다.

모니터링(Monitoring)은 심층 방어의 탐지 계층(Detection Layer)을 제공한다. 인증 실패, 예상하지 못한 네트워크 연결, 비정상적인 ROS 2 통신, 비인가 설정 변경, 비정상적인 자원 사용, 펌웨어 검증 실패, AI 추론 이상(AI Inference Anomaly), 의심스러운 플릿 명령은 관찰 가능한 보안 이벤트(Security Event)를 생성해야 한다. 중앙집중형 로깅(Centralized Logging)과 이벤트 상관분석(Event Correlation)은 각각의 로봇이나 하위 시스템을 개별적으로 분석할 때는 정상적으로 보이는 이벤트들이 연결된 공격 과정의 일부임을 발견할 수 있도록 한다.

효과적인 모니터링은 통제된 대응 메커니즘(Response Mechanism)과 연결되어야 한다. 의심스러운 로봇은 네트워크 격리(Network Quarantine), 자격증명 폐기(Credential Revocation), 워크로드 종료(Workload Termination), 성능 저하 운용 모드(Degraded Mode) 전환 또는 통제된 정지(Controlled Stopping)가 필요할 수 있다. 그러나 통신을 갑자기 차단하거나 소프트웨어를 종료하는 행위 자체가 위험을 발생시킬 수 있으므로 대응 조치는 물리적 안전을 고려해야 한다. 따라서 사이버보안 격리(Cybersecurity Containment)와 기능 안전 동작(Functional Safety Behavior)은 아키텍처 설계 단계부터 상호 연계되어야 한다.

복원력(Resilience)과 복구(Recovery)는 예방 및 탐지가 실패한 이후에도 추가적인 방어 계층을 구성한다. 로봇은 신뢰할 수 있는 복구 이미지(Trusted Recovery Image), 보호된 설정 백업(Configuration Backup), 검증된 정상 펌웨어(Known-Good Firmware), 자격증명 교체 절차, 통제된 서비스 복귀(Return-to-Service) 프로세스를 유지해야 한다. 중요 플릿 인프라는 이중화(Redundancy)와 장애조치(Failover)가 필요할 수 있다. 복구는 단순히 시스템 가용성을 회복하는 것뿐만 아니라 신원, 소프트웨어, 설정 및 데이터를 다시 신뢰할 수 있는 상태로 복원해야 한다.

심층 방어는 개발 및 공급망 프로세스(Development and Supply-Chain Process)까지 확장된다. 소스 저장소(Source Repository), 지속적 통합 및 배포 시스템(CI/CD System), 의존성 관리(Dependency Management), 빌드 서버(Build Server), 아티팩트 레지스트리(Artifact Registry), 서명 키(Signing Key), 서드파티 구성요소(Third-Party Component), 엔지니어링 워크스테이션은 배포된 로봇으로 침투하는 경로가 될 수 있다. 코드 검토(Code Review), 소프트웨어 구성 분석(Software Composition Analysis), 소프트웨어 자재명세서 관리(SBOM Management), 보호된 빌드 파이프라인, 서명된 아티팩트, 취약점 추적 및 통제된 릴리스 승인을 통해 배포 이전 단계에서 침해가 유입될 가능성을 줄일 수 있다.

계층화된 보안(Layered Security)의 효과는 각 통제 사이의 독립성(Independence)에 달려 있다. 여러 보안 메커니즘이 동일한 자격증명, 관리자, 네트워크 서비스 또는 침해된 컴퓨터에 모두 의존한다면 다중 방어가 제공하는 실질적인 가치는 제한된다. 따라서 중요 로봇 기능에서는 불필요한 공통 장애 지점(Common Failure Point)을 피해야 한다. 독립적인 안전 제어기, 분리된 서명 기관(Signing Authority), 분할된 관리 경로(Management Path), 독립적인 모니터링 채널은 다른 보안 영역이 실패하더라도 보호 기능을 유지할 수 있다.

심층 방어는 궁극적으로 로봇 사이버보안을 경계 중심 보호(Perimeter Protection)에서 지속적인 침해 억제 및 제한(Continuous Containment) 체계로 전환한다. 목표는 모든 공격을 예방할 수 있다고 가정하는 것이 아니라 하나의 인터페이스가 침해되더라도 인지, 계획, 통신, 펌웨어, 플릿 서비스 또는 구동(Actuation)에 대한 통제권까지 자동으로 확보되지 않도록 하는 것이다. 하드웨어 신뢰, 신원, 네트워크 분할, 미들웨어 보안, 애플리케이션 검증, AI 보호, 모니터링, 안전 제약 및 복구를 결합함으로써 로봇 아키텍처는 사이버 침입과 그로 인해 발생할 수 있는 물리적 결과를 모두 제한할 수 있다.

## 01.06. Zero Trust Architecture for Robot Systems [w/Code]

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

제로 트러스트 아키텍처(Zero Trust Architecture)는 "절대 신뢰하지 말고 항상 검증하라(Never Trust, Always Verify)"는 원칙을 로봇 시스템에 참여하는 모든 신원, 장치, 서비스, 통신 경로 및 워크로드(Workload)에 적용한다. 기존 아키텍처는 로봇 내부나 보호된 네트워크에 존재하는 구성요소를 신뢰할 수 있다고 가정하는 경우가 많다. 제로 트러스트(Zero Trust)는 이러한 가정을 제거하고 동일한 로봇이나 운영 네트워크 내부의 구성요소 사이에서 통신하는 경우에도 접근 권한을 부여하기 전에 명시적인 검증을 요구한다.

로봇 시스템은 이기종 컴퓨팅 환경(Heterogeneous Computing Environment)을 결합하기 때문에 제로 트러스트의 적용 효과가 특히 크다. 마이크로컨트롤러(Microcontroller), 엣지 컴퓨터(Edge Computer), ROS 2 노드(Node), AI 가속기(AI Accelerator), 운영자 콘솔(Operator Console), 플릿 서버(Fleet Server), 엔지니어링 워크스테이션(Engineering Workstation), 클라우드 서비스, 이동형 유지보수 장치가 하나의 운영 시스템에 함께 참여할 수 있다. 어떤 구성요소가 침해되더라도 다른 구성요소에 대한 신뢰가 자동으로 형성되거나 중요 로봇 기능에 제한 없이 접근할 수 있어서는 안 된다.

신원(Identity)은 제로 트러스트 로봇 아키텍처의 핵심 보안 경계(Security Boundary)가 된다. 각각의 로봇, 장치, 소프트웨어 서비스, 운영자, 관리자 및 자동화 에이전트(Automated Agent)는 검증 가능한 신원을 가져야 한다. 장치 인증서(Device Certificate), 암호학적 자격증명(Cryptographic Credential), 워크로드 신원(Workload Identity), 사용자 인증 메커니즘을 활용하면 단순히 요청자의 IP 주소나 물리적인 네트워크 위치가 아니라 누가 또는 무엇이 자원에 대한 접근을 요청하는지를 기준으로 접근 결정을 내릴 수 있다.

인증(Authentication)은 신원을 확인하지만 제로 트러스트에서는 세분화된 인가(Fine-Grained Authorization)도 필요하다. 유효한 신원에는 담당 기능을 수행하는 데 필요한 권한만 부여해야 한다. 인지 노드(Perception Node)는 탐지된 객체 정보를 발행할 수 있지만 모터 제어 파라미터를 자동으로 변경할 수 있어서는 안 된다. 유지보수 엔지니어는 진단 정보에 접근할 수 있지만 플릿 전체에 명령을 실행할 권한까지 가져서는 안 된다. 최소 권한(Least Privilege)은 정상적인 신원이나 신뢰된 구성요소가 침해되었을 때 발생할 수 있는 피해를 제한한다.

상호 인증(Mutual Authentication)은 보호된 정보를 교환하기 전에 양쪽 엔드포인트(Endpoint)가 서로의 신원을 검증하도록 하여 로봇 구성요소 사이의 통신을 강화한다. 이는 로봇-클라우드(Robot-to-Cloud), 로봇-플릿(Robot-to-Fleet), 서비스 간(Service-to-Service), 관리자 연결에서 특히 중요하다. 인증서 기반 인증(Certificate-Based Authentication)과 상호 인증된 암호화 채널은 사칭(Impersonation) 및 중간자 공격(Man-in-the-Middle Attack) 위험을 줄이는 동시에 인가 결정을 위한 더욱 강력한 기반을 제공할 수 있다.

제로 트러스트는 세션 시작 시 한 번 수행하는 판단이 아니라 지속적인 검증(Continuous Verification)을 요구한다. 장치 보안 상태(Device Posture), 소프트웨어 버전, 인증서 상태, 설정 무결성(Configuration Integrity), 네트워크 상황, 사용자 권한 및 관찰된 동작은 운영 중에도 변경될 수 있다. 따라서 접근 정책(Access Policy)은 현재의 보안 상태를 고려할 수 있으며 로봇, 서비스, 계정 또는 엔드포인트가 설정된 신뢰 요구사항을 더 이상 충족하지 못하면 권한을 폐기하거나 제한할 수 있다.

마이크로세그멘테이션(Microsegmentation)은 제로 트러스트 원칙을 네트워크 아키텍처에 적용한다. 안전 제어(Safety Control), 모션 제어(Motion Control), 인지(Perception), AI 추론(AI Inference), 플릿 관리(Fleet Management), 유지보수, 기업 IT(Enterprise IT), 클라우드 연결은 명시적으로 허용된 경로를 통해서만 통신해야 한다. 네트워크 위치만으로 신뢰를 의미해서는 안 된다. 방화벽, 접근 제어 정책, 인증된 게이트웨이(Authenticated Gateway), 서비스 신원(Service Identity), 제한된 라우팅(Restricted Routing)은 하나의 구성요소가 침해된 이후의 측면 이동(Lateral Movement)을 제한할 수 있다.

ROS 2와 DDS에서는 미들웨어 계층(Middleware Layer)에 신원과 인가를 적용하여 이러한 모델을 구현할 수 있다. 노드가 DDS 도메인(DDS Domain)에 참여했다는 이유만으로 모든 토픽(Topic), 서비스(Service), 액션(Action)에 접근할 수 있어서는 안 된다. 보안 정책은 인증된 참여자(Authenticated Participant)가 어떤 토픽을 발행하거나 구독할 수 있는지, 어떤 서비스를 호출하거나 액션을 수행할 수 있는지를 정의할 수 있다. 이를 통해 기존 IP 수준의 네트워크 분할을 넘어 애플리케이션 인식형 접근 제어(Application-Aware Access Control)를 제공할 수 있다.

로봇 API(Robot API)에도 자원별 인가(Resource-Specific Authorization)가 필요하다. REST, gRPC, 웹소켓(WebSocket), MQTT, 플릿 관리 및 유지보수 인터페이스는 서로 매우 다른 물리적 결과를 발생시킬 수 있는 명령을 외부에 제공할 수 있다. 텔레메트리(Telemetry) 읽기, 설정 변경, 소프트웨어 업데이트 시작, 모션 명령, 비상 작업 수행에 동일한 권한을 적용해서는 안 된다. API 게이트웨이(API Gateway)와 애플리케이션 서비스는 명령을 실행하기 전에 신원, 권한, 상황(Context), 요청된 작업을 평가해야 한다.

제로 트러스트는 원격 유지보수(Remote Maintenance) 및 엔지니어링 접근에서 특히 중요하다. 공급업체 노트북, 서비스 도구, VPN 사용자, 임시 유지보수 계정이 경계 인증(Perimeter Authentication)을 통과했다는 이유만으로 광범위한 네트워크 접근 권한을 받아서는 안 된다. 접근은 승인된 로봇, 서비스, 포트, 작업 및 시간 범위로 제한되어야 한다. 높은 권한의 세션(Privileged Session)은 강력하게 인증되고 기록 및 모니터링되어야 하며 운영 목적이 종료되면 세션도 종료되어야 한다.

클라우드 및 플릿 아키텍처(Cloud and Fleet Architecture)는 제로 트러스트를 다수의 분산된 로봇으로 확장한다. 각각의 로봇은 플릿 서비스에 독립적으로 인증해야 하며 플릿 서비스 역시 로봇으로 전송하는 명령에 대해 인증되어야 한다. 하나의 로봇이 침해되더라도 다른 로봇에서 사용할 수 있는 자격증명을 획득해서는 안 된다. 장치별 신원(Per-Device Identity), 격리된 비밀정보(Isolated Secret), 범위가 제한된 인가(Scoped Authorization), 명령 서명(Command Signing), 테넌트 분리(Tenant Separation), 인증서 수명주기 관리(Certificate Lifecycle Management)는 플릿 전체로 침해가 확산될 가능성을 줄인다.

소프트웨어 워크로드(Software Workload) 역시 신뢰된 컴퓨터에서 실행되는 모든 프로세스가 동일한 권한을 가진다고 가정하기보다 각각의 신원을 가진 대상으로 취급해야 한다. 컨테이너(Container), ROS 2 노드, AI 추론 서비스, 텔레메트리 에이전트(Telemetry Agent), 업데이트 클라이언트(Update Client), 안전 관련 애플리케이션은 서로 다른 자격증명과 권한을 가질 수 있다. 워크로드 격리(Workload Isolation)는 침해된 애플리케이션이 다른 서비스를 사칭하거나 관련 없는 데이터 및 제어 인터페이스에 접근하는 능력을 제한한다.

피지컬 AI(Physical AI)는 새로운 제로 트러스트 질문을 제기한다. 인증된 AI 구성요소가 생성한 출력이라면 자동으로 신뢰해야 하는가라는 문제이며, 안전 필수 행동(Safety-Critical Action)에 대해서는 일반적으로 그렇지 않아야 한다. AI 모델은 적대적 입력(Adversarial Input), 오염된 데이터(Poisoned Data), 프롬프트 인젝션(Prompt Injection), 모델 침해(Model Compromise), 예상하지 못한 상황으로 인해 잘못되거나 조작된 출력을 생성할 수 있다. 따라서 AI가 생성한 행동은 액추에이터에 도달하기 전에 인가, 정책, 타당성(Plausibility), 안전 검증(Safety Validation)을 통과해야 한다.

데이터 자체에도 명시적인 신뢰 평가(Explicit Trust Evaluation)가 필요하다. 센서 메시지, 지도, 위치추정 결과(Localization Result), AI 모델, 설정 파일, 펌웨어 패키지, 임무 명령은 인증된 출처에서 생성되었더라도 오래되었거나, 손상되었거나, 재전송되었거나, 악의적으로 변경되었을 수 있다. 무결성 보호(Integrity Protection), 타임스탬프(Timestamp), 시퀀스 검사(Sequence Check), 출처 정보(Provenance Information), 서명(Signature), 스키마 검증(Schema Validation), 일관성 검사(Consistency Check)는 인증된 데이터가 실제 운영에도 적합한지를 판단하는 데 도움을 준다.

제로 트러스트는 보안 부팅(Secure Boot), 펌웨어 서명(Firmware Signing), OTA 보호, 장치 상태 평가(Device Health Assessment)와 통합되어야 한다. 장치가 비인가 소프트웨어를 실행하고 있다면 장치 신원만으로는 충분하지 않다. 접근 결정에는 로봇이 신뢰된 펌웨어로 부팅되었는지, 승인된 설정을 유지하는지, 지원되는 소프트웨어 버전을 사용하는지, 중대한 보안 경고가 발생하지 않았는지에 대한 증거를 포함할 수 있다. 따라서 신원과 플랫폼 무결성(Platform Integrity)은 서로를 보완한다.

모니터링(Monitoring)과 텔레메트리는 지속적인 신뢰 평가에 필요한 피드백을 제공한다. 예상하지 못한 통신 경로, 반복되는 인증 실패, 비정상적인 권한 요청, 비정상적인 ROS 2 트래픽, 설정 변경, 의심스러운 API 호출 또는 이상 AI 동작(Anomalous AI Behavior)은 이전에 신뢰되던 구성요소를 더 이상 신뢰할 수 없음을 나타낼 수 있다. 보안 모니터링은 재인증(Reauthentication), 권한 축소(Privilege Reduction), 자격증명 폐기(Credential Revocation), 네트워크 격리(Network Quarantine), 통제된 운영 성능 저하(Controlled Operational Degradation)를 실행하도록 할 수 있다.

그러나 제로 트러스트는 실시간 제어(Real-Time Control)와 기능 안전(Functional Safety) 요구사항을 준수해야 한다. 마이크로초 또는 밀리초 단위의 제어 루프(Control Loop)에 반복적인 원격 인가 검사를 무분별하게 삽입할 수는 없다. 중요한 로컬 제어 기능에서는 사전에 설정된 신원(Pre-Established Identity), 제한된 권한, 결정론적 정책 집행(Deterministic Policy Enforcement), 로컬에서 사용할 수 있는 자격증명을 활용할 수 있다. 아키텍처는 실시간 동작을 유지하면서 상위 수준의 명령과 신뢰 상태 전환(Trust Transition)이 명시적으로 통제되도록 설계해야 한다.

따라서 로봇 시스템에서 제로 트러스트는 하나의 제품, 방화벽 설정 또는 인증 기술을 의미하지 않는다. 이는 암묵적 신뢰(Implicit Trust)를 신원 기반(Identity-Based), 최소 권한, 지속적으로 평가되는 접근 방식으로 대체하는 아키텍처 원칙이다. 네트워크 분할, 미들웨어 보안, 보안 소프트웨어, 플랫폼 무결성, 모니터링, AI 안전 경계(AI Safety Boundary), 통제된 복구(Controlled Recovery)와 결합하면 제로 트러스트는 하나의 구성요소 침해가 전체 사이버-물리 로봇 시스템(Cyber-Physical Robot System)에 대한 통제 권한 획득으로 확대되는 것을 제한할 수 있다.

## 01.07. Cybersecurity Lifecycle Concept to EOL

![](images/image7.png){width="7.268055555555556in" height="4.845138888888889in"}

![](images/image8.png){width="7.268055555555556in" height="4.845138888888889in"}

사이버보안(Cybersecurity)은 개발 후반부에 추가되는 하나의 기능으로 취급하는 것이 아니라 로봇의 전체 수명주기(Robot Lifecycle)에 걸쳐 관리되어야 한다. 로봇은 개념 및 요구사항 단계에서 시작하여 아키텍처, 구현, 통합, 생산, 배포, 운영, 유지보수를 거쳐 최종적으로 수명 종료(End of Life, EOL)에 이른다. 각 단계에서 보안 가정(Security Assumption)이 변화할 수 있으므로 사이버보안 활동은 초기 개념 단계부터 최종 폐기(Decommissioning)까지 엔지니어링 의사결정과 지속적으로 연결되어야 한다.

개념 단계(Concept Phase)에서는 로봇의 의도된 기능, 운영 환경, 연결성, 자율성, 사용자, 외부 서비스 및 오용으로 발생할 수 있는 물리적 결과를 정의한다. 이러한 특성은 초기 사이버보안 환경(Cybersecurity Context)을 결정한다. 창고 자율이동로봇(Warehouse AMR), 산업용 매니퓰레이터(Industrial Manipulator), 휴머노이드(Humanoid), 무인항공기(UAV)는 서로 다른 공격자와 노출 조건에 직면할 수 있다. 초기 보안 계획에서는 중요 자산을 식별하고 어떤 장애가 안전, 운영, 개인정보, 지식재산권 또는 플릿 가용성(Fleet Availability)에 영향을 미칠 수 있는지를 결정한다.

사이버보안 요구사항(Cybersecurity Requirement)은 기능 요구사항(Functional Requirement) 및 안전 요구사항(Safety Requirement)과 함께 발전해야 한다. 기밀성(Confidentiality), 무결성(Integrity), 가용성(Availability), 인증(Authentication), 인가(Authorization), 보안 통신(Secure Communication), 소프트웨어 무결성, 로깅(Logging), 업데이트 가능성(Updateability), 복구 요구사항에는 명확한 엔지니어링 정의가 필요하다. 또한 중요한 신뢰 경계(Trust Boundary)와 장애 또는 공격 발생 이후 허용 가능한 동작도 요구사항으로 정의해야 한다. 요구사항 엔지니어링 단계에서 보안 목표가 모호하면 이후 일관되게 구현하거나 검증하기 어렵다.

아키텍처 개발(Architecture Development)은 이러한 요구사항을 보안 경계와 기술적 통제(Technical Control)로 변환한다. 엔지니어는 하드웨어 신뢰 루트(Hardware Root of Trust), 장치 신원(Device Identity), 네트워크 구역(Network Zone), 통신 경로, 높은 권한의 서비스, ROS 2 및 DDS 권한, 클라우드 인터페이스, 업데이트 경로, AI 구성요소, 안전 제어 경계(Safety-Control Boundary)를 식별한다. 이 단계에서 심층 방어(Defense in Depth)와 제로 트러스트(Zero Trust) 원칙을 통합하여 하나의 구성요소가 침해되더라도 중요 제어 기능에 자동으로 접근할 수 없도록 설계할 수 있다.

위협 모델링(Threat Modeling)과 사이버-물리 위험 평가(Cyber-Physical Risk Assessment)는 아키텍처 개발과 함께 수행되어야 한다. 구현 방식을 변경하기 어려워지기 전에 자산, 인터페이스, 신뢰 경계, 위협 시나리오(Threat Scenario), 공격 경로(Attack Path), 잠재적 피해를 분석한다. 분석 범위에는 하드웨어, 소프트웨어, 네트워크, 물리적 접근, 공급망 의존성(Supply-Chain Dependency), 클라우드 서비스, AI 모델, 유지보수 인터페이스가 포함되어야 한다. 분석 결과는 보안 요구사항과 우선순위가 설정된 엔지니어링 통제로 변환된다.

구현 단계(Implementation Phase)에서는 보안 개발 관행(Secure Development Practice)을 통해 로봇 소프트웨어와 펌웨어에 취약점이 유입될 가능성을 줄인다. 코드 검토(Code Review), 정적 분석(Static Analysis), 의존성 관리(Dependency Management), 컴파일러 보호 기능(Compiler Protection), 보안 코딩 규칙(Secure Coding Rule), 비밀정보 관리(Secrets Management), 입력 검증(Input Validation), 최소 권한 실행(Least-Privilege Execution)을 일반적인 엔지니어링 워크플로(Engineering Workflow)의 일부로 적용해야 한다. 인증, 암호화, 업데이트 검증, 명령 인가와 같은 보안 필수 기능은 특히 신중한 구현과 검토가 필요하다.

서드파티 및 오픈소스 구성요소(Third-Party and Open-Source Component)에도 자체적인 수명주기 관리가 필요하다. 현대 로봇은 운영체제, ROS 2 패키지, 장치 드라이버(Device Driver), AI 프레임워크, 라이브러리, 컨테이너(Container), 펌웨어 및 공급업체 소프트웨어에 의존한다. 구성요소 버전과 의존성은 인벤토리(Inventory)와 소프트웨어 자재명세서(Software Bill of Materials, SBOM)를 통해 추적할 수 있어야 한다. 알려진 취약점, 라이선스 제약, 공급업체 보안 권고(Supplier Advisory), 업스트림 유지보수 상태(Upstream Maintenance Status)는 개발 및 운영 전체 기간에 걸쳐 지속적으로 파악되어야 한다.

통합 및 검증(Integration and Verification)은 개별 보안 메커니즘이 완전한 로봇 시스템으로 결합되었을 때도 올바르게 작동하는지를 확인한다. 인증, 인가, 암호화 통신, 보안 부팅(Secure Boot), 네트워크 분할(Network Segmentation), 미들웨어 정책(Middleware Policy), API 보호, 펌웨어 검증, 로깅을 실제 운영과 유사한 설정에서 시험해야 한다. 비인가 명령, 비정상 입력(Malformed Input), 유효하지 않은 인증서, 금지된 통신이 적절하게 거부되는지를 확인해야 하므로 부정 시험(Negative Testing) 역시 중요하다.

보안 유효성 확인(Security Validation)은 시험 범위를 현실적인 공격 시나리오까지 확장한다. 취약점 스캐닝(Vulnerability Scanning), 침투 테스트(Penetration Testing), 프로토콜 퍼징(Protocol Fuzzing), 펌웨어 분석, ROS 2 및 DDS 보안 테스트, API 테스트, 적대적 AI 평가(Adversarial AI Evaluation), 레드팀 훈련(Red-Team Exercise)은 일반적인 기능 시험에서 발견하지 못하는 약점을 식별할 수 있다. 사이버보안 유효성 확인에서는 공격 성공 여부뿐만 아니라 모니터링, 격리(Containment), 안전 메커니즘 및 복구 절차가 공격으로 발생하는 물리적 결과를 얼마나 제한하는지도 확인해야 한다.

생산 단계(Production Phase)는 추가적인 신뢰 관계(Trust Relationship)를 형성한다. 빌드 서버(Build Server), 지속적 통합 및 배포 파이프라인(CI/CD Pipeline), 아티팩트 저장소(Artifact Repository), 서명 서비스(Signing Service), 공장 프로비저닝 시스템(Factory Provisioning System), 제조 장비, 엔지니어링 워크스테이션은 양산 로봇에 설치되는 소프트웨어에 영향을 줄 수 있다. 릴리스 아티팩트(Release Artifact)는 승인된 소스 및 빌드 프로세스까지 추적할 수 있어야 한다. 펌웨어 서명, 보호된 키, 통제된 프로비저닝, 설정 기준선(Configuration Baseline), 제조 기록을 통해 개발 단계에서 실제 출하된 하드웨어까지 신뢰를 유지할 수 있다.

배포(Deployment)는 운영 보안 기준선(Operational Security Baseline)을 확립하는 단계이다. 기본 자격증명(Default Credential)을 제거하고, 고유한 장치 신원을 프로비저닝하며, 인증서를 안전하게 설치하고, 불필요한 서비스를 비활성화하며, 네트워크 정책을 적용하고, 승인된 소프트웨어 버전을 기록해야 한다. 로봇은 설치 이후 수동으로 보안을 강화하는 방식에 의존하지 않고 알려진 설정 상태로 서비스에 투입되어야 한다. 플릿 등록(Fleet Registration)과 클라우드 등록(Cloud Enrollment)에서도 명확한 소유권, 인가 및 자격증명 관계를 확립해야 한다.

운영 사이버보안(Operational Cybersecurity)은 배포 이후에도 위협 환경이 고정되지 않기 때문에 지속적인 가시성(Continuous Visibility)에 의존한다. 로그, 인증 이벤트, 네트워크 활동, 소프트웨어 버전, 설정 변경, ROS 2 통신, 자원 사용량, AI 동작, 플릿 명령은 새롭게 발생하는 문제에 대한 증거를 제공할 수 있다. 모니터링은 이상 징후(Anomaly)를 탐지하는 동시에 사이버 사고와 일반적인 소프트웨어, 하드웨어 또는 운영 장애를 구분할 수 있는 충분한 상황 정보(Context)를 제공해야 한다.

취약점 관리(Vulnerability Management)는 제품 출시 이후 지속적으로 수행되는 수명주기 프로세스가 된다. 새롭게 발견된 취약점은 로봇이 서비스에 투입된 지 오랜 시간이 지난 후에도 운영체제, 미들웨어, 라이브러리, 펌웨어, AI 프레임워크, 클라우드 서비스 또는 서드파티 구성요소에 영향을 줄 수 있다. 조직은 취약점 접수(Vulnerability Intake), 영향 분석, 우선순위 결정, 개선(Remediation), 공개(Disclosure), 배포를 위한 프로세스를 운영해야 한다. 위험 평가에서는 악용 가능성뿐만 아니라 발생 가능한 사이버-물리적 결과도 고려해야 한다.

보안 OTA(Secure OTA) 및 유지보수 프로세스는 장기간의 운영 수명 동안 보호 상태를 유지하기 위한 메커니즘을 제공한다. 업데이트는 인증되고 무결성이 보호되며 버전 관리되고 시험되어야 하며, 설치 실패 시 복구할 수 있어야 한다. 롤백 방지(Anti-Rollback) 통제는 알려진 취약점이 존재하는 소프트웨어 버전으로 복원되는 것을 방지할 수 있다. 정상적인 기술자에게 편리한 서비스 인터페이스가 공격자에게도 가치 있는 공격 경로가 될 수 있으므로 유지보수 접근은 강력하게 인증되고 허용 범위가 제한되어야 한다.

사고 대응 및 복구(Incident Response and Recovery) 역시 실제 사고가 발생하기 전에 설계되어야 한다. 조직은 영향을 받은 로봇을 격리하고, 자격증명을 폐기하며, 포렌식 증거(Forensic Evidence)를 보존하고, 긴급 패치를 배포하며, 신뢰된 설정을 복원하고, 장비를 서비스에 복귀시켜도 안전한지를 판단하는 방법을 사전에 정의해야 한다. 하나의 로봇에서 발견된 취약점이 동일한 소프트웨어, 자격증명 또는 인프라를 공유하는 다수의 장치에도 존재할 수 있으므로 플릿 환경에서는 특히 주의가 필요하다.

수명주기 사이버보안(Lifecycle Cybersecurity)은 아키텍처 변경 관리도 포함한다. 새로운 센서, AI 모델, 클라우드 서비스, 무선 기술, 고객 시스템 통합 또는 자율 기능이 추가되면 초기 위협 모델링에서 설정한 가정이 더 이상 유효하지 않을 수 있다. 중요한 변경이 발생하면 보안 검토(Security Review), 갱신된 위험 평가, 회귀 테스트(Regression Testing), 문서 업데이트를 수행해야 한다. 따라서 사이버보안 보증(Cybersecurity Assurance)은 제품 출시 당시의 구성에 고정되는 것이 아니라 로봇의 발전과 함께 지속적으로 변화해야 한다.

수명 종료(End of Life, EOL) 단계에서는 단순히 로봇의 전원을 끄는 것이 아니라 통제된 폐기(Controlled Decommissioning)를 수행해야 한다. 암호화 키, 장치 인증서, 사용자 자격증명, 저장된 지도, 텔레메트리, 독점 모델(Proprietary Model), 로그 및 고객 정보가 퇴역 장비에 남아 있을 수 있다. 자격증명을 폐기하고, 필요한 경우 민감한 저장장치를 안전하게 삭제하며, 클라우드 및 플릿 등록을 제거하고, 소유권 기록을 갱신하여 퇴역 장치가 운영 인프라에 계속 인증할 수 없도록 해야 한다.

지원 종료(Support Termination) 역시 명확하게 전달되어야 한다. 지원되지 않는 로봇은 장기간 지속되는 보안 위험(Security Liability)이 될 수 있기 때문이다. 조직은 최종 소프트웨어 및 펌웨어 지원 기간, 취약점 처리 정책, 마이그레이션 옵션(Migration Option), 지속적인 운영이 더 이상 허용될 수 없는 조건을 정의해야 한다. 시스템을 업그레이드할 수 없는 경우 교체 또는 퇴역할 때까지 네트워크 격리나 기능 제한과 같은 보완 통제(Compensating Control)가 필요할 수 있다.

성숙한 사이버보안 수명주기(Cybersecurity Lifecycle)는 초기 위험 가정에서 요구사항, 아키텍처, 구현, 검증, 배포, 모니터링, 유지보수, 사고 대응 및 수명 종료 의사결정까지 이어지는 지속적인 추적성(Traceability)을 구축한다. 보안 증거(Security Evidence)는 각 단계마다 새롭게 만드는 것이 아니라 전체 수명주기에 걸쳐 축적된다. 사이버보안을 엔지니어링 수명주기로 관리함으로써 로봇 조직은 소프트웨어가 변경되고, 위협이 진화하며, 플릿 규모가 확대되고, 사이버-물리 시스템이 장기간 운영되는 상황에서도 지속적으로 신뢰를 유지할 수 있다.

## 01.08. Security by Design Principles for Robot SW

![](images/image9.png){width="7.268055555555556in" height="7.268055555555556in"}

설계 단계 보안(Security by Design)은 사이버보안(Cybersecurity)을 구현 이후에 추가되는 보호 기능의 집합이 아니라 로봇 소프트웨어 아키텍처(Robot Software Architecture)의 근본적인 속성으로 다루는 것을 의미한다. 보안 요구사항(Security Requirement)은 구성요소, 인터페이스, 데이터 흐름(Data Flow), 권한, 통신 경로 및 장애 동작을 정의하는 과정에서 함께 고려된다. 이러한 접근 방식은 로봇 플랫폼이 통합, 생산 또는 현장 운영 단계에 진입한 이후에는 수정하기 어려운 구조적 보안 취약점을 줄여준다.

설계 단계 보안의 주요 원칙 중 하나는 공격 표면 최소화(Attack Surface Minimization)이다. 로봇 소프트웨어는 의도된 운영에 필요한 서비스, 포트, API, ROS 2 인터페이스, 관리 기능 및 원격 접근 메커니즘만 외부에 노출해야 한다. 개발 도구, 디버그 서비스(Debug Service), 기본 계정(Default Account), 불필요한 네트워크 리스너(Network Listener), 오래되어 더 이상 사용하지 않는 인터페이스는 양산 시스템에서 비활성화하거나 제거해야 한다. 노출되는 기능을 줄이면 취약점이 발생할 수 있는 기회와 장기적인 유지보수 부담을 동시에 감소시킬 수 있다.

최소 권한(Least Privilege)은 모든 소프트웨어 구성요소가 자신의 기능을 수행하는 데 필요한 최소한의 권한만 갖도록 제한한다. 인지 프로세스(Perception Process)는 모터 제어기에 대한 무제한 접근 권한이 필요하지 않으며, 텔레메트리 서비스(Telemetry Service)는 안전 파라미터를 변경할 수 없어야 하고, 일반 운영자가 엔지니어링 권한을 자동으로 상속받아서도 안 된다. 사용자, 프로세스, 컨테이너(Container), ROS 2 노드(Node), 서비스, 클라우드 워크로드(Cloud Workload) 사이에서 권한을 분리하여 하나의 구성요소가 침해되더라도 더 광범위한 시스템 통제 권한까지 자동으로 확보하지 못하도록 해야 한다.

보안 기본 설정(Secure Defaults)은 새롭게 설치되거나 초기화된 로봇이 운영자가 필수적인 보안 통제를 수동으로 활성화하지 않아도 보호된 상태에서 시작하도록 보장한다. 인증(Authentication), 암호화 통신(Encrypted Communication), 제한적인 권한, 로깅(Logging), 인증서 검증(Certificate Validation), 업데이트 검증(Update Verification)은 기본적으로 활성화되어야 한다. 사용하지 않는 인터페이스는 비활성화된 상태를 유지해야 하며, 보안에 민감한 설정은 파라미터가 누락되거나 유효하지 않거나 일관성이 없는 경우 알려진 통제 상태(Known Controlled State)로 전환되도록 설계해야 한다.

서로 다른 책임과 중요도를 가진 소프트웨어 영역 사이에는 명시적인 신뢰 경계(Explicit Trust Boundary)를 설정해야 한다. 모션 제어(Motion Control), 안전 기능(Safety Function), 인지(Perception), AI 추론(AI Inference), 플릿 관리(Fleet Management), 유지보수, 클라우드 연결, 기업 시스템 통합(Enterprise Integration)은 서로를 암묵적으로 신뢰해서는 안 된다. 이러한 경계를 통과하는 인터페이스는 참여자의 신원을 인증하고, 데이터를 검증하며, 인가(Authorization)를 강제하고, 정상적인 상호작용에 필요한 작업만 외부에 제공해야 한다.

입력 검증(Input Validation)은 비정상적인 데이터가 궁극적으로 물리적 행동에 영향을 줄 수 있기 때문에 로봇 소프트웨어에서 특히 중요하다. 네트워크 패킷, ROS 2 메시지, API 요청, 센서 측정값, 설정 파일, 임무 명령(Mission Command), 모델 입력, 업데이트 패키지는 예상된 데이터 유형, 크기, 범위, 구조, 최신성(Freshness), 의미적 유효성(Semantic Validity)을 기준으로 검사해야 한다. 검증은 상위 시스템에 전적으로 의존하기보다 해당 데이터를 실제로 사용하는 구성요소와 가까운 위치에서 수행해야 한다.

로봇 소프트웨어는 완전한 중재(Complete Mediation) 원칙도 적용해야 한다. 보호된 작업이 요청될 때마다 인가를 확인해야 하며 이전에 이루어진 네트워크 연결이나 로그인 이벤트만을 근거로 권한을 가정해서는 안 된다. 안전 파라미터 변경, 모션 명령, 펌웨어 로딩, 지도 수정, AI 모델 배포, 민감한 진단 정보 접근에는 서로 다른 권한이 필요할 수 있다. 보호 대상 작업이 실행되는 시점에 권한을 다시 확인하면 중간 서비스가 침해되었을 때 발생할 수 있는 영향을 줄일 수 있다.

직무 분리(Separation of Duties)는 하나의 계정, 프로세스 또는 하위 시스템이 보안에 민감한 작업의 모든 단계를 통제하지 못하도록 한다. 소프트웨어 개발, 릴리스 승인(Release Approval), 아티팩트 서명(Artifact Signing), OTA 배포, 플릿 관리, 보안 모니터링에는 서로 다른 권한과 책임을 적용할 수 있다. 영향도가 높은 작업에서는 독립적인 승인 또는 검증을 적용하여 하나의 침해된 자격증명이나 관리자만으로 전체 로봇 플릿을 변경할 수 있는 위험을 줄일 수 있다.

소프트웨어 무결성(Software Integrity)은 전체 실행 체인(Execution Chain)에 내재하도록 설계되어야 한다. 부트로더(Bootloader), 펌웨어, 운영체제 구성요소, 컨테이너, 로봇 애플리케이션, 설정 패키지, AI 모델은 사용 전에 식별하고 검증할 수 있어야 한다. 암호학적 해시(Cryptographic Hash), 디지털 서명(Digital Signature), 보안 부팅(Secure Boot), 신뢰할 수 있는 저장소(Trusted Repository), 서명된 아티팩트(Signed Artifact), 통제된 배포 파이프라인(Controlled Deployment Pipeline)은 실행되는 소프트웨어가 공격자에 의해 변경된 대체물이 아니라 승인된 버전과 일치한다는 신뢰를 확립하는 데 도움을 준다.

비밀정보(Secret)는 일반적인 설정 데이터처럼 취급해서는 안 된다. 비밀번호, API 토큰, 개인 키(Private Key), 인증서, 서명 자격증명(Signing Credential), 클라우드 비밀정보(Cloud Secret)는 보호된 생성, 저장, 배포, 교체(Rotation), 폐기(Revocation), 삭제 과정을 필요로 한다. 하드코딩된 자격증명(Hard-Coded Credential)은 동일한 비밀정보가 여러 로봇에 확산될 수 있기 때문에 장기간 지속되는 취약점을 만든다. 장치별 신원(Device-Specific Identity)과 적절하게 보호된 키 저장소(Key Storage)는 개별 장치가 침해되었을 때 발생하는 영향을 줄여준다.

메모리 및 프로세스 격리(Memory and Process Isolation)는 소프트웨어 결함이 악용되었을 때 침해가 다른 영역으로 확산되는 것을 제한한다. 운영체제 권한, 컨테이너 격리(Container Isolation), 샌드박싱(Sandboxing), 메모리 보호 메커니즘(Memory-Protection Mechanism), 제한된 시스템 호출(Restricted System Call), 권한 프로세스와 비권한 프로세스의 분리를 통해 하나의 침해된 애플리케이션이 관련 없는 서비스를 통제하는 것을 방지할 수 있다. 안전 필수 및 보안 필수 기능은 광범위한 권한이나 복잡한 외부 인터페이스를 가진 대규모 소프트웨어 구성요소에 불필요하게 의존하지 않아야 한다.

안전한 오류 처리(Secure Error Handling) 역시 중요한 아키텍처 요구사항이다. 소프트웨어는 유효하지 않은 상태를 거부하면서도 자격증명, 내부 경로, 암호학적 자료(Cryptographic Material), 과도한 진단 정보를 비인가 사용자에게 노출해서는 안 된다. 동시에 보안 장애는 인가된 모니터링 시스템에서 관찰할 수 있어야 한다. 인증 오류, 무결성 검증 실패, 정책 위반(Policy Violation), 예상하지 못한 상태 전환(State Transition)은 공격자에게 도움이 되는 정보를 제공하지 않으면서도 유용한 감사 증거(Audit Evidence)를 생성해야 한다.

보안 로깅(Security Logging)과 관측 가능성(Observability)은 사고 발생 이후에 추가하는 것이 아니라 배포 이전부터 설계되어야 한다. 로봇 소프트웨어는 보안과 관련된 인증 이벤트, 권한 변경, 설정 수정, 소프트웨어 업데이트, 정책 위반, 주요 명령 활동을 기록해야 한다. 로그에는 타임스탬프(Timestamp), 무결성 보호(Integrity Protection), 통제된 접근, 충분한 상황 정보(Context)가 포함되어야 하며 이를 통해 플릿 모니터링, 사고 조사(Incident Investigation), 포렌식 분석(Forensic Analysis), 분산 구성요소 간 이벤트 상관분석(Event Correlation)을 지원할 수 있어야 한다.

안전 장애 동작(Fail-Safe Behavior)은 로봇의 물리적 특성을 고려해야 한다. 소프트웨어 보안 장애가 통제되지 않은 움직임이나 또 다른 위험을 발생시키는 갑작스러운 시스템 종료로 자동 연결되어서는 안 된다. 구성요소는 인증 상실, 손상된 메시지, 사용할 수 없는 클라우드 서비스, 유효하지 않은 센서 데이터, 무결성 검사 실패에 대한 안전한 대응을 정의해야 한다. 운영 상황에 따라 명령 거부, 기능 저하(Functional Degradation), 하위 시스템 격리 또는 통제된 안전 상태(Controlled Safe State) 진입과 같은 대응이 적용될 수 있다.

피지컬 AI(Physical AI) 소프트웨어는 설계 단계 보안을 모델과 지능형 에이전트(Intelligent Agent)까지 확장한다. 모델 출처(Model Provenance), 서명된 모델 아티팩트, 통제된 모델 로딩(Controlled Model Loading), 학습 데이터 거버넌스(Training-Data Governance), 프롬프트 및 멀티모달 입력 검증(Multimodal Input Validation), 추론 모니터링(Inference Monitoring), 제한된 행동 인터페이스(Constrained Action Interface)를 아키텍처에 포함해야 한다. AI 모델이나 에이전트가 인증되었다는 이유만으로 AI 출력이 결정론적 안전 통제(Deterministic Safety Control)를 우회해서는 안 되며, 생성된 행동은 정책과 물리적 안전 제한을 계속 적용받아야 한다.

보안 업데이트 가능성(Secure Updateability)은 복잡한 로봇이 전체 수명 동안 취약점 없이 유지될 것이라고 가정할 수 없기 때문에 그 자체가 하나의 설계 요구사항이다. 소프트웨어 아키텍처는 인증된 OTA 패키지, 무결성 검증, 통제된 설치, 버전 관리, 롤백 복구(Rollback Recovery), 필요한 경우 롤백 방지(Anti-Rollback)를 지원해야 한다. 안전하게 업데이트할 수 없는 구성요소는 장기간의 현장 배포 과정에서 관리 가능한 취약점을 영구적인 보안 위험(Security Liability)으로 전환시킬 수 있다.

설계 단계 보안은 검증 가능성(Verifiability)도 요구한다. 보안 요구사항은 엔지니어링 팀이 인증, 인가, 격리, 무결성 보호, 오류 처리, 업데이트 메커니즘, 장애 대응이 의도한 대로 동작하는지를 시험할 수 있도록 표현되어야 한다. 자동화된 보안 회귀 테스트(Automated Security Regression Testing)는 소프트웨어가 변경되더라도 이러한 보안 속성을 유지하도록 지원할 수 있다. 따라서 아키텍처 결정에서는 보안 통제를 구현할 수 있는지만 고려할 것이 아니라 그 동작을 반복적으로 입증할 수 있는지도 함께 고려해야 한다.

궁극적으로 설계 단계 보안(Security by Design)은 사이버보안을 일반적인 로봇 소프트웨어 엔지니어링(Robot Software Engineering)의 일부로 만든다. 공격 표면 감소, 최소 권한, 보안 기본 설정, 명시적인 신뢰 경계, 검증, 격리, 무결성 보호, 관측 가능성, 안전한 장애 처리, 보안 업데이트 가능성은 아키텍처 전체에서 서로를 보완한다. 이러한 원칙을 구현 이전부터 확립하면 이후의 심층 방어(Defense in Depth), 제로 트러스트(Zero Trust), 침투 테스트(Penetration Testing), 사고 대응(Incident Response), 규정 준수(Compliance)를 더욱 강력하고 유지관리 가능한 기반 위에서 수행할 수 있다.

## 01.09. Cyber Physical Risk Assessment Framework

![](images/image10.png){width="7.268055555555556in" height="7.268055555555556in"}

사이버-물리 위험 평가(Cyber-Physical Risk Assessment)는 디지털 침해(Digital Compromise)를 물리적 세계에서 발생하는 결과와 연결하여 사이버보안 위험(Cybersecurity Risk)을 평가한다. 로봇 시스템에서는 소프트웨어, 네트워크, 센서 또는 AI 구성요소에 대한 공격이 움직임, 힘, 내비게이션, 인지 또는 사람과의 상호작용을 변화시킬 수 있기 때문에 기존 정보보안 분석만으로는 충분하지 않다. 따라서 효과적인 프레임워크(Framework)는 사이버 위협을 운영 환경의 노출 수준, 물리적 동작, 안전 영향 및 임무 결과와 함께 평가해야 한다.

평가는 시스템 경계(System Boundary)와 운영 상황(Operational Context)을 정의하는 것에서 시작한다. 엔지니어는 로봇 플랫폼, 온보드 컴퓨터(Onboard Computer), 센서, 액추에이터(Actuator), 통신 링크, ROS 2 또는 DDS 미들웨어(Middleware), 플릿 인프라(Fleet Infrastructure), 클라우드 서비스, 유지보수 시스템, 운영자 및 외부 의존성을 식별한다. 동일한 플랫폼이라도 격리된 연구실에서 운용되는 경우와 작업자, 차량, 기계 또는 공공 인프라 주변에서 운용되는 경우 취약점으로 인한 위험이 크게 달라질 수 있으므로 운영 환경도 함께 고려해야 한다.

자산 식별(Asset Identification)은 무엇을 보호해야 하며 그것이 왜 중요한지를 정의한다. 로봇 자산에는 펌웨어, 제어 소프트웨어, 암호학적 자격증명(Cryptographic Credential), 센서 스트림(Sensor Stream), 지도, 위치추정 결과(Localization Estimate), 임무 계획(Mission Plan), AI 모델, 안전 파라미터, 액추에이터 명령, 플릿 서비스 및 운영 데이터가 포함된다. 자산의 가치는 기밀성(Confidentiality)만으로 평가해서는 안 된다. 조작이나 손실이 자율 동작에 직접적인 영향을 주거나 중요 기능의 운영을 방해할 수 있다면 무결성(Integrity)과 가용성(Availability)이 더욱 중요할 수 있다.

다음으로 이러한 자산 주변의 신뢰 경계(Trust Boundary)와 공격 표면(Attack Surface)을 매핑한다. 무선 인터페이스, 이더넷 포트(Ethernet Port), 클라우드 API, ROS 2 토픽(Topic), DDS 서비스(Service), 유지보수 포트, 이동식 저장장치, 디버그 인터페이스(Debug Interface), 업데이트 메커니즘, 센서, 충전소 및 물리적 접근 지점이 침입 경로를 제공할 수 있다. 각 인터페이스는 누가 접근할 수 있는지, 어떤 권한을 노출하는지, 어떠한 보호 기능이 존재하는지, 경계가 침해되면 추가로 어떤 구성요소에 접근할 수 있는지를 기준으로 평가해야 한다.

위협 시나리오(Threat Scenario)는 공격자가 이러한 인터페이스를 악용하여 보호 대상 자산에 영향을 미치는 방법을 설명한다. 자격증명 탈취, 비인가 명령 주입, 펌웨어 변경, 센서 정보 스푸핑(Spoofing), 무선 통신 방해, 플릿 서비스 침해, AI 모델 교체 또는 유지보수 접근 권한 악용 등이 이에 포함될 수 있다. 심각한 로봇 보안 사고는 여러 시스템 경계를 연속적으로 통과하는 과정에서 발생하는 경우가 많으므로 시나리오는 개별 취약점이 아니라 현실적으로 가능한 일련의 공격자 행동을 표현해야 한다.

공격 경로 분석(Attack-Path Analysis)은 최초 침입 지점에서 최종적인 사이버-물리적 영향까지의 연결 과정을 분석한다. 공격자는 취약한 원격 서비스를 통해 침입하고, 엣지 컴퓨터(Edge Computer)에서 권한을 상승시킨 다음, ROS 2 통신 권한을 획득하고, 내비게이션 데이터를 조작하여 최종적으로 로봇의 움직임에 영향을 줄 수 있다. 이러한 단계를 매핑하면 공격을 중단할 수 있는 중간 통제 수단을 파악할 수 있으며, 발견된 모든 취약점이 곧바로 로봇에 대한 직접적인 통제 권한을 제공한다고 잘못 가정하는 것을 방지할 수 있다.

피해 시나리오(Damage Scenario)는 기술적 침해를 이해관계자(Stakeholder)에게 의미 있는 실제 결과로 변환한다. 조작된 위치추정 정보는 경로 이탈을 발생시킬 수 있고, 잘못된 인지 정보는 위험한 장애물 회피 동작을 유발할 수 있으며, 손상된 안전 파라미터는 허용 속도를 증가시킬 수 있고, 서비스 거부(Denial of Service)는 생산 플릿을 정지시킬 수 있다. 결과에는 인명 피해, 장비 손상, 생산 손실, 환경 영향, 개인정보 노출, 지식재산 손실, 규제 위반 또는 임무 수행 능력 저하 등이 포함될 수 있다.

발생 가능성 평가(Likelihood Assessment)는 공격자의 능력과 시스템의 노출 수준을 모두 고려해야 한다. 인터넷에 노출된 클라우드 서비스, 광범위하게 배포된 무선 인터페이스, 재사용되는 자격증명, 알려진 취약점, 쉽게 접근할 수 있는 유지보수 포트는 공격 가능성을 높일 수 있다. 반대로 높은 수준의 전문지식, 특수 장비, 물리적 근접성, 암호학적 보호, 네트워크 분할(Network Segmentation), 모니터링, 독립적인 안전 통제가 요구된다면 공격 가능성은 낮아질 수 있다. 분석에서는 이론적으로 가능한 공격과 현실적으로 실행 가능한 공격 경로를 구분해야 한다.

영향 평가(Impact Assessment)는 침해가 발생하는 시점의 로봇 물리 상태도 고려해야 한다. 동일한 악성 명령이라도 로봇 속도, 적재물(Payload), 사람과의 거리, 운용 고도, 매니퓰레이터 힘(Manipulator Force), 환경 조건 또는 주변 장비에 따라 서로 다른 결과를 발생시킬 수 있다. 따라서 사이버-물리 위험은 항상 고정된 심각도 값(Severity Value)으로 표현할 수 있는 것이 아니며, 운영 상황과 시스템이 보유한 잠재적 에너지 또는 행동 권한(Action Authority)을 함께 고려해야 한다.

안전(Safety)과 사이버보안 분석은 서로 상호작용해야 하지만 동일한 분야로 취급해서는 안 된다. 기능 안전(Functional Safety)은 전통적으로 결함과 예측 가능한 장애로 인해 발생하는 위험을 다루는 반면, 사이버보안은 공격자의 의도적인 조작을 고려한다. 사이버공격은 의도적으로 안전 장애와 유사한 조건을 만들거나 안전 메커니즘에서 사용하는 가정을 우회할 수 있다. 위험 정보(Hazard Information)를 공유하고 분석을 조정하면 사이버보안 통제가 안전 관련 기능을 보호해야 하는 지점을 식별하는 데 도움이 된다.

위험 평가(Risk Evaluation)는 발생 가능성과 영향을 결합하여 어떤 시나리오에 위험 처리가 필요하며 통제를 얼마나 긴급하게 구현해야 하는지를 결정한다. 조직은 정성적 분류(Qualitative Category), 수치 기반 점수, 위험 매트릭스(Risk Matrix), 시나리오 기반 방법을 사용할 수 있지만 점수 산정 모델은 이해 가능하고 추적할 수 있어야 한다. 공격자 능력, 노출 수준, 물리적 결과 또는 기존 보호조치에 대한 가정을 설명할 수 없다면 정밀한 수치 점수도 제한적인 가치만 가진다.

위험 처리(Risk Treatment)는 유해한 물리적 결과가 발생하기 전에 공격 경로를 차단할 수 있는 통제를 우선해야 한다. 강력한 신원 관리, 최소 권한(Least Privilege), 네트워크 분할, 보안 부팅(Secure Boot), 서명된 펌웨어(Signed Firmware), ROS 2 접근 제어, 센서 타당성 검사(Sensor Plausibility Check), 보호된 API, 명령 검증(Command Validation), 모니터링 및 독립적인 안전 제한은 공격의 서로 다른 단계에서 방어 장벽을 제공할 수 있다. 하나의 예방 메커니즘이 실패하거나 우회되더라도 위험을 계속 통제할 수 있으므로 심층 방어(Defense in Depth)가 중요하다.

제안된 통제를 적용한 이후에는 잔여 위험(Residual Risk)을 평가해야 한다. 서명된 명령은 비인가 변경을 방지할 수 있지만 인가되었으나 침해된 서비스가 안전한 명령을 생성한다는 것을 보장하지는 않는다. 네트워크 분할은 측면 이동(Lateral Movement)을 제한할 수 있지만 인가된 구역 내부의 악성 동작을 완전히 제거하지는 못한다. 따라서 잔여 위험 분석은 어떠한 유해 시나리오가 여전히 가능한지, 추가적인 탐지, 격리(Containment), 안전 또는 복구 조치가 필요한지를 평가해야 한다.

피지컬 AI(Physical AI)는 학습 모델(Learned Model)이 기존 소프트웨어 취약점 분석에 적합하지 않은 장애 및 공격 유형을 추가하기 때문에 평가 프레임워크의 범위를 확장한다. 적대적 관측(Adversarial Observation), 오염된 데이터셋(Poisoned Dataset), 모델 대체(Model Substitution), 프롬프트 인젝션(Prompt Injection), 안전하지 않은 에이전트 계획(Unsafe Agent Planning), 예상하지 못한 일반화(Unexpected Generalization)는 기존 코드 취약점을 악용하지 않고도 로봇의 의사결정을 변경할 수 있다. 따라서 모델 출처(Model Provenance), 추론 모니터링(Inference Monitoring), 제한된 행동 공간(Constrained Action Space), 정책 집행(Policy Enforcement), 결정론적 안전 경계(Deterministic Safety Boundary)를 사이버-물리 위험 처리에 포함해야 한다.

플릿 규모 시스템(Fleet-Scale System)에서는 상관 위험(Correlated Risk)과 시스템적 위험(Systemic Risk)을 분석해야 한다. 한 대의 로봇에 영향을 주는 취약점은 관리 가능한 수준으로 보일 수 있지만 동일한 취약점이 수천 대의 로봇에 공유되면 광범위한 운영 중단을 발생시킬 수 있다. 공통 자격증명, 중앙집중형 플릿 서비스, 공유 OTA 인프라, 동일한 소프트웨어 이미지 및 공통 AI 모델은 위험 집중(Concentration Risk)을 발생시킬 수 있다. 따라서 평가는 개별 로봇의 피해뿐만 아니라 여러 로봇이 동시에 침해되는 상황도 검토해야 한다.

위험 평가는 최종 점수만 산출하는 것이 아니라 추적 가능한 엔지니어링 결과(Traceable Engineering Output)를 생성해야 한다. 위협 시나리오는 영향을 받는 자산, 피해 시나리오, 보안 요구사항, 구현된 통제, 검증 증거(Verification Evidence), 담당 책임자 및 승인된 잔여 위험과 연결되어야 한다. 이러한 추적성(Traceability)을 확보하면 소프트웨어, 하드웨어, 운영 환경 또는 규제 요구사항이 변경되었을 때 특정 통제가 왜 존재하는지와 최초 의사결정이 어떠한 가정에 기반했는지를 엔지니어링 팀이 이해할 수 있다.

이 프레임워크는 로봇의 전체 수명주기(Robot Lifecycle)에 걸쳐 지속적으로 운영되어야 한다. 새로운 취약점, 소프트웨어 업데이트, 추가 센서, 변경된 네트워크 아키텍처, 새로운 AI 모델, 클라우드 마이그레이션(Cloud Migration), 운영 사고, 서로 다른 환경으로의 배포는 기존의 위험 가정을 무효화할 수 있다. 중요한 변경이 발생하면 초기 개발 단계에서 수행한 평가에 영구적으로 의존하지 말고 공격 경로, 발생 가능성, 영향, 통제 및 잔여 위험을 다시 평가해야 한다.

성숙한 사이버-물리 위험 평가 프레임워크(Cyber-Physical Risk Assessment Framework)는 궁극적으로 사이버보안 엔지니어링을 로봇의 물리적 임무(Physical Mission)와 연결한다. 이는 단순히 시스템이 해킹될 수 있는지를 묻는 것이 아니라 침해가 인지(Perception), 추론(Reasoning), 통신(Communication), 제어(Control)를 통해 어떻게 전파되어 최종적으로 물리적 행동에 영향을 미치는지를 분석한다. 자산, 위협, 공격 경로, 운영 상황, 결과, 보안 통제 및 잔여 위험을 연결함으로써 조직은 실제 세계에서 허용할 수 없는 결과를 방지하는 능력을 기준으로 사이버보안 조치의 우선순위를 결정할 수 있다.

## 01.10. Robot Cybersecurity Organization and Roles

![](images/image11.png){width="7.268055555555556in" height="7.268055555555556in"}

로봇 사이버보안(Robot Cybersecurity)은 보안 엔지니어링(Security Engineering)을 소프트웨어, 하드웨어, 안전, 운영, 제조 및 제품 관리와 연결하는 조직 구조를 필요로 한다. 취약점은 임베디드 펌웨어(Embedded Firmware), ROS 2 통신, 클라우드 인프라(Cloud Infrastructure), AI 모델, 유지보수 프로세스 또는 공급업체 구성요소에서 발생할 수 있으므로 사이버보안을 한 명의 전문가에게만 맡길 수 없다. 명확한 책임 체계를 구축하면 로봇의 전체 수명주기(Robot Lifecycle)에 걸쳐 보안 관련 의사결정을 일관되고 체계적으로 조정할 수 있다.

경영진(Executive Leadership)은 위험 허용 수준(Risk Appetite), 조직적 책임, 투자 우선순위 및 상향 보고 권한(Escalation Authority)을 정의하여 사이버보안 거버넌스(Cybersecurity Governance)를 확립한다. 경영진이 개별적인 기술적 결정을 직접 수행할 필요는 없지만, 사이버보안 조직이 충분한 자원을 확보하고 안전하지 않은 제품 관련 의사결정에 이의를 제기할 수 있는 독립성을 갖도록 보장해야 한다. 중대한 잔여 위험(Residual Risk), 해결되지 않은 심각한 취약점, 플릿 전체의 보안 노출에는 경영진 검토와 공식적인 위험 수용(Formal Risk Acceptance)을 위한 명확한 절차가 마련되어야 한다.

로봇 사이버보안 책임자(Robot Cybersecurity Leader) 또는 제품 보안 관리자(Product Security Manager)는 전체 보안 프로그램을 조정한다. 이 역할은 조직의 정책을 엔지니어링 활동으로 전환하고, 사이버보안 계획을 유지하며, 위협 모델링(Threat Modeling)과 위험 평가(Risk Assessment)를 조정하고, 보안 요구사항을 추적하며, 해결되지 않은 위험을 모니터링한다. 또한 개발팀을 운영, 사고 대응(Incident Response), 규정 준수(Compliance), 공급업체 및 경영진과 연결하여 사이버보안 관련 의사결정이 조직 경계에 따라 분절되지 않도록 한다.

보안 아키텍트(Security Architect)는 로봇과 이를 지원하는 인프라의 기술적 보안 구조를 정의한다. 신뢰 경계(Trust Boundary), 보안 구역(Security Zone), 통신 경로(Communication Conduit), 신원 모델(Identity Model), 높은 권한의 인터페이스, 암호학적 메커니즘(Cryptographic Mechanism), 모니터링 요구사항을 식별한다. 이러한 작업은 온보드 컴퓨팅(Onboard Computing), ROS 2와 DDS, 무선 네트워크, 플릿 시스템(Fleet System), 클라우드 서비스, OTA 인프라, 유지보수 인터페이스 및 피지컬 AI(Physical AI) 구성요소를 포괄하면서 안전 및 실시간 제약조건과도 일치해야 한다.

소프트웨어 및 펌웨어 엔지니어(Software and Firmware Engineer)는 보안 아키텍처에서 정의한 여러 통제를 실제로 구현한다. 이들의 책임에는 보안 코딩(Secure Coding), 입력 검증(Input Validation), 인증 통합(Authentication Integration), 인가 적용(Authorization Enforcement), 비밀정보 처리(Secrets Handling), 소프트웨어 무결성(Software Integrity), 보안 통신, 오류 처리 및 업데이트 지원이 포함된다. 보안 책임은 구현이 완료된 이후 별도의 보안팀에 전적으로 넘기는 것이 아니라 일반적인 개발 과정에 통합되어야 한다.

하드웨어 및 임베디드 시스템 엔지니어(Hardware and Embedded-System Engineer)는 소프트웨어만으로 제공할 수 없는 보안 속성을 담당한다. 보안 부팅(Secure Boot), 하드웨어 신뢰 루트(Hardware Root of Trust), 보호된 키 저장소(Protected Key Storage), 디버그 인터페이스 통제(Debug-Interface Control), 펌웨어 검증, 장치 신원(Device Identity), 변조 대응(Tamper Consideration), 보안 프로비저닝(Secure Provisioning)은 하드웨어 아키텍처에 의존한다. 하드웨어 경계의 취약점은 상위 계층에서 구현된 보안 메커니즘을 무력화할 수 있으므로 이러한 엔지니어는 소프트웨어팀과 긴밀하게 협력해야 한다.

네트워크 및 인프라팀(Network and Infrastructure Team)은 로봇, 플릿 서비스, 기업 시스템 및 클라우드 환경 사이의 통신을 보호한다. 이들의 책임에는 네트워크 분할(Network Segmentation), 방화벽 정책(Firewall Policy), 보안 원격 접근(Secure Remote Access), 인증서 인프라(Certificate Infrastructure), 네트워크 모니터링, 무선 보안 및 복원력 있는 연결(Resilient Connectivity)이 포함된다. 일반적인 기업용 보안 통제를 운영 제약조건에 대한 이해 없이 적용하면 실시간 통신을 방해할 수 있으므로 로봇 특유의 트래픽과 타이밍 요구사항을 이해해야 한다.

기능 안전(Functional Safety)팀과 사이버보안팀은 특히 긴밀한 협력 관계를 필요로 한다. 안전 엔지니어(Safety Engineer)는 결함과 장애로 발생하는 위험을 분석하고, 사이버보안 엔지니어는 의도적인 조작과 적대적 행동을 분석한다. 사이버공격은 무작위 장애와 동일한 물리적 위험을 발생시키거나 안전 메커니즘에서 사용하는 가정을 의도적으로 무력화할 수 있다. 공동 위험 검토(Shared Hazard Review)와 조정된 요구사항을 통해 보안 통제가 새로운 위험을 발생시키지 않으면서 안전 필수 기능(Safety-Critical Function)을 보호하도록 해야 한다.

AI 및 로봇 자율성팀(AI and Robotics Autonomy Team)은 로봇이 학습 기반 인지(Learned Perception), 파운데이션 모델(Foundation Model), 비전-언어-행동 모델(Vision-Language-Action Model) 또는 자율 에이전트(Autonomous Agent)를 사용하는 경우 중요한 보안 이해관계자가 된다. 이들의 책임은 모델 정확도를 넘어 모델 출처(Model Provenance), 데이터셋 무결성(Dataset Integrity), 통제된 배포, 적대적 강건성(Adversarial Robustness), 추론 모니터링(Inference Monitoring), 행동 제약(Action Constraint)까지 확장된다. 물리적 행동에 영향을 미칠 수 있는 AI 생성 의사결정은 인가, 정책 집행(Policy Enforcement), 독립적인 안전 경계(Independent Safety Boundary)의 적용을 계속 받아야 한다.

데브섹옵스팀(DevSecOps Team)은 보안을 개발 및 릴리스 파이프라인(Release Pipeline)에 통합한다. 소스 저장소(Source Repository), CI/CD 시스템, 의존성 스캐너(Dependency Scanner), 빌드 환경(Build Environment), 아티팩트 레지스트리(Artifact Registry), 컨테이너 이미지(Container Image), 소프트웨어 자재명세서(Software Bill of Materials, SBOM), 서명 인프라(Signing Infrastructure)를 보호하고 모니터링해야 한다. 자동화된 보안 테스트는 소프트웨어가 양산 로봇에 도달하기 전에 취약한 의존성, 안전하지 않은 설정, 유출된 비밀정보 및 정책 위반을 식별하여 개발 후반의 수동 검토에 대한 의존도를 줄일 수 있다.

보안 검증 및 침투 테스트팀(Security Verification and Penetration-Testing Team)은 구현된 보안 통제가 현실적인 공격에 저항할 수 있다는 독립적인 증거를 제공한다. 이들은 외부에 노출된 서비스, API, ROS 2 및 DDS 설정, 무선 인터페이스, 펌웨어, 업데이트 메커니즘, 클라우드 서비스 및 물리적 유지보수 인터페이스를 평가한다. 개발팀은 의도하지 않게 예상된 시스템 동작을 중심으로 시험할 수 있으므로, 예상하지 못한 조합과 공격자가 통제하는 조건을 탐색하기 위해서는 독립적인 검증이 중요하다.

제품 보안 사고 대응팀(Product Security Incident Response Team)은 배포 이후 발견되는 취약점과 실제 사이버보안 사고를 관리한다. 이들은 취약점 보고를 접수하고, 심각도를 평가하며, 격리(Containment)를 조정하고, 포렌식 조사(Forensic Investigation)를 지원하며, 개선 조치(Remediation)를 준비하고, 영향을 받는 이해관계자와 소통한다. 침해된 로봇을 격리하거나 연결을 비활성화하거나 긴급 업데이트를 적용하는 행위 자체가 물리적 운영에 영향을 줄 수 있으므로 로봇 보안 사고에서는 운영팀 및 안전팀과의 협력이 필요하다.

보안 운영팀(Security Operations Team)은 배포된 로봇과 인프라 전반에 걸쳐 지속적인 모니터링을 수행한다. 인증 실패, 비정상적인 네트워크 활동, 예상하지 못한 ROS 2 통신, 설정 변경, 소프트웨어 무결성 실패, 의심스러운 플릿 명령, 비정상적인 자원 사용은 시스템 침해의 징후일 수 있다. 탐지된 이벤트가 자동 경고(Automated Alerting)에서 기술 조사 및 운영 대응으로 효율적으로 전달될 수 있도록 모니터링 책임에는 명확한 상향 보고 기준(Escalation Criteria)이 포함되어야 한다.

제조 및 프로비저닝팀(Manufacturing and Provisioning Team)도 중요한 사이버보안 책임을 담당한다. 이들은 펌웨어를 설치하고, 장치 신원을 프로비저닝하며, 암호화 키(Cryptographic Key)를 주입하고, 인증서를 설정하며, 초기 소프트웨어 기준선(Software Baseline)을 구축할 수 있다. 따라서 공장 시스템은 보안 신뢰 체인(Security Chain of Trust)의 일부가 된다. 프로비저닝 장비와 서명 자료(Signing Material)에 대한 접근은 제한되고 감사 가능해야 하며, 필요한 경우 일반적인 제조 작업과 분리되어야 한다.

공급망 및 조달 기능(Supply-Chain and Procurement Function)은 외부 구성요소와 공급업체에서 유입되는 보안 위험을 관리하는 데 도움을 준다. 계약에서는 취약점 공개(Vulnerability Disclosure)에 대한 요구사항, 업데이트 지원 기간, 구성요소 인벤토리(Component Inventory), 보안 문서, 사고 통보 책임 등을 정의할 수 있다. 서드파티 펌웨어, 라이브러리, 센서, 통신 모듈 및 클라우드 서비스에서는 로봇의 운영 수명 동안 새로운 취약점이 발생할 수 있으므로 공급업체 위험(Supplier Risk)은 조달 이후에도 지속적으로 관리되어야 한다.

로봇 운영자와 유지보수 담당자(Robot Operator and Maintenance Personnel)는 보안 조직의 운영 계층을 구성한다. 이들에게는 명확하게 정의된 권한, 안전한 유지보수 절차, 자격증명 관리 방법, 비정상적인 동작을 보고할 수 있는 절차가 필요하다. 운영자가 정교한 사이버공격을 직접 진단할 필요는 없지만 로봇이 예상하지 못한 행동을 하거나, 반복적으로 연결을 상실하거나, 명령을 거부하거나, 설명되지 않는 설정 변경을 보이는 경우 중요한 관찰 정보를 제공할 수 있다.

거버넌스(Governance)는 이러한 역할 전반에 걸쳐 명시적인 책임 할당(Responsibility Assignment)을 요구한다. 보안 요구사항에는 담당자가 있어야 하고, 검증 활동에는 책임 있는 검토자가 지정되어야 하며, 취약점에는 개선 담당자가, 잔여 위험에는 지정된 수용 권한자(Acceptance Authority)가 존재해야 한다. 책임 매트릭스(Responsibility Matrix)는 누가 개발하고, 승인하고, 검증하고, 운영하고, 모니터링하고, 대응하는지를 명확히 하는 데 도움을 줄 수 있지만 책임성(Accountability)은 단순한 문서화가 아니라 실제 엔지니어링 권한과 연결되어야 한다.

교차 기능 보안 검토(Cross-Functional Security Review)는 조직 간 정렬을 지속적으로 유지하기 위한 메커니즘을 제공한다. 아키텍처 변경, 새로운 연결 기능, AI 모델 업데이트, 공급업체 교체, 주요 소프트웨어 릴리스, 새롭게 발견된 취약점, 서로 다른 환경으로의 배포에는 보안, 안전, 소프트웨어, 하드웨어, 운영 및 제품팀의 참여가 필요할 수 있다. 정기적인 검토를 수행하면 로봇과 운영 환경이 변화하는 과정에서 기존 사이버보안 가정이 더 이상 유효하지 않게 되는 문제를 방지할 수 있다.

성숙한 로봇 사이버보안 조직(Robot Cybersecurity Organization)은 중앙집중형 거버넌스와 추적성(Traceability)을 유지하면서 보안 책임을 조직 전체에 분산한다. 엔지니어는 자신이 설계하는 구성요소의 보안을 책임지고, 전문 보안팀은 아키텍처, 검증, 모니터링, 사고 대응에 필요한 전문성을 제공하며, 경영진은 조직 차원의 위험 의사결정을 책임진다. 이러한 역할이 명확한 요구사항, 상향 보고 경로, 검증 증거 및 수명주기 프로세스를 통해 연결될 때 사이버보안은 일회성 규정 준수 활동이 아니라 지속적인 엔지니어링 역량으로 자리 잡을 수 있다.
