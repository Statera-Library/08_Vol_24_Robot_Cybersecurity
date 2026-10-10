**Volume 24. Robot Cybersecurity**


# Chapter 04. ROS2 and DDS Security

##  

## 04.01. ROS2 DDS Security Threat Surface Analysis

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

ROS 2 introduces a distributed communication architecture in which robot software components interact through nodes, topics, services, actions, parameters, and discovery mechanisms. DDS provides the underlying data-centric communication model for many ROS 2 deployments. This flexibility improves modularity and scalability, but it also creates a broad security threat surface because communication may cross processes, computers, networks, and administrative trust boundaries. Volume_24_Robot_Cybersecurity

Threat-surface analysis begins by identifying every ROS 2 participant that can produce, consume, discover, or modify information. Nodes are particularly important because each node may publish sensor data, subscribe to commands, expose services, execute actions, or modify parameters. A compromised node can therefore become an internal attack platform, allowing an adversary to observe data flows, impersonate legitimate components, inject messages, or influence downstream robot behavior.

DDS discovery is another critical exposure point. Participants must locate one another and exchange information describing available communication endpoints before normal data exchange occurs. If discovery traffic is insufficiently protected, an unauthorized participant may learn the structure of the robotic system, including topic names, communication relationships, and active endpoints. Such reconnaissance can provide information needed for subsequent spoofing, interception, denial-of-service, or targeted manipulation.

ROS 2 topics form a major attack surface because they frequently carry continuous operational information such as sensor observations, localization estimates, trajectories, velocity commands, actuator states, diagnostics, and AI inference results. Unauthorized subscribers may compromise confidentiality, while malicious publishers may threaten integrity by introducing fabricated or modified data. For physical robots, corrupted topic data can propagate from software communication into unsafe physical actions.

Services and actions introduce additional risks because they represent request-response and goal-oriented control interfaces rather than passive data streams. An attacker capable of invoking sensitive services could trigger configuration changes, reset components, alter operating modes, or request privileged functions. Action interfaces can be even more consequential when they initiate navigation, manipulation, inspection, docking, or other long-running behaviors that directly affect the physical state of the robot.

Parameters should also be treated as security-sensitive configuration assets. ROS 2 parameters can influence controller gains, perception thresholds, planner behavior, communication settings, safety limits, and application logic. Unauthorized parameter modification may not resemble a conventional network attack, yet it can subtly alter system behavior. Attackers may exploit such changes to degrade performance, disable safeguards, create unstable behavior, or prepare conditions for a later physical attack.

The DDS communication layer expands the analysis beyond application-level ROS 2 interfaces. DDS participants, domains, publishers, subscribers, DataWriters, DataReaders, discovery traffic, transport interfaces, and Quality of Service settings collectively create multiple paths through which an adversary may interact with the system. Threat modeling must therefore consider not only ROS 2 source code but also middleware configuration, DDS implementation behavior, network exposure, and deployment topology.

Identity is central to this threat surface. Without trustworthy participant identity, a robotic system may be unable to distinguish legitimate software from an attacker imitating an authorized node or DDS participant. Spoofing can become especially dangerous when malicious endpoints use names, topics, or communication patterns that resemble trusted components. Strong authentication is consequently required before communication privileges can be meaningfully associated with a participant.

Authorization addresses a different question: what should an authenticated participant be allowed to do? A legitimate perception node, for example, may require permission to publish detected objects but should not automatically receive permission to issue motion commands. Excessive permissions increase the blast radius of compromise. ROS 2 and DDS security architecture should therefore apply least privilege to publishing, subscribing, service interaction, and other communication operations.

Confidentiality threats arise when robot communication contains information that should not be observable by unauthorized parties. Camera streams, maps, localization data, production information, operator commands, mission plans, and telemetry may reveal sensitive operational context. Passive network monitoring can therefore be significant even when an attacker never modifies a packet. Encryption and secure key management are needed where exposure of communication content creates unacceptable risk.

Integrity and authenticity are generally even more important for control-related traffic. A robot may make decisions based on data received from numerous distributed components, and a forged message can appear structurally valid while containing dangerous information. Protecting message integrity helps detect unauthorized modification, while origin authentication establishes confidence in the source. These controls become critical when data influences navigation, manipulation, safety monitoring, or autonomous decision making.

Availability must be analyzed alongside confidentiality and integrity because robotics communication is often time-sensitive. Flooding discovery traffic, creating excessive participants, publishing at abnormal rates, exhausting middleware resources, or interfering with network transport can delay or prevent legitimate communication. Even when no data is stolen or altered, latency and packet loss may destabilize control loops, interrupt perception pipelines, trigger emergency behavior, or make autonomous missions unavailable.

Quality of Service configuration introduces security implications because reliability, durability, history depth, deadline, liveliness, and resource behavior affect how DDS handles communication. Poorly selected settings may amplify resource exhaustion or permit unexpected persistence of data. Security review should therefore examine QoS not merely as a performance concern but as part of resilience engineering, particularly for systems where high-rate sensors and safety-critical command channels share computational and network resources.

Trust boundaries are essential for organizing the threat analysis. Boundaries may exist between safety control and AI workloads, robot and fleet infrastructure, trusted and untrusted networks, containers, host operating systems, edge computers, remote operators, cloud services, and third-party software. Every communication path crossing such a boundary should be examined for authentication, authorization, confidentiality, integrity, replay resistance, availability, monitoring, and recovery requirements.

Deployment configuration can significantly change the actual threat surface. A development robot operating on an isolated laboratory network presents different risks from an AMR fleet connected through industrial Wi-Fi, a humanoid connected to edge AI servers, or a remotely managed field robot. Security analysis must therefore model real interfaces, ports, middleware implementations, network routes, remote-management channels, containers, credentials, certificates, and dependencies rather than treating ROS 2 security as a middleware-only problem.

The operating system and software supply chain extend the boundary further. A correctly protected DDS session cannot compensate for a compromised host, stolen private key, malicious ROS package, vulnerable dependency, or unauthorized container image. Attack paths may originate below ROS 2 and subsequently inherit the privileges of legitimate middleware participants. Host hardening, package provenance, credential protection, secure deployment, patch management, and runtime monitoring must consequently complement communication security.

Threat analysis should also consider insiders and already-compromised components. Authentication can prevent unknown participants from joining a protected environment, but it cannot guarantee that authenticated software remains trustworthy. If one authorized node is compromised, its existing permissions may be abused. Fine-grained access control, separation of privileges, behavioral monitoring, audit logging, credential rotation, and rapid revocation help limit lateral movement and reduce the consequences of such compromise.

A practical ROS 2 and DDS threat model should ultimately connect each exposed asset to plausible threat actors, attack paths, security controls, and physical consequences. The objective is not simply to enumerate network vulnerabilities but to understand how cyber manipulation can propagate through middleware into perception, planning, control, and actuation. This framing is consistent with the broader volume structure, which progresses from threat modeling and network security into ROS 2/DDS protection, testing, incident response, and compliance. Volume_24_Robot_Cybersecurity

The resulting analysis provides the foundation for subsequent security engineering. Identified risks can be translated into SROS2 certificate policies, DDS authentication and encryption, topic and service access controls, trusted node identities, audit mechanisms, cryptographic key lifecycle management, vulnerability remediation, penetration testing, and compliance evidence. These controls correspond directly to the security progression defined for the ROS 2 and DDS chapter. Volume_24_Robot_Cybersecurity

ROS 2는 로봇 소프트웨어 구성요소가 노드(Node), 토픽(Topic), 서비스(Service), 액션(Action), 파라미터(Parameter), 디스커버리 메커니즘(Discovery Mechanism)을 통해 상호작용하는 분산 통신 아키텍처(Distributed Communication Architecture)를 제공한다. DDS(Data Distribution Service)는 많은 ROS 2 배포 환경에서 기반이 되는 데이터 중심 통신 모델(Data-Centric Communication Model)을 제공한다. 이러한 유연성은 모듈성과 확장성을 향상시키지만, 통신이 프로세스, 컴퓨터, 네트워크 및 관리상의 신뢰 경계(Trust Boundary)를 넘을 수 있기 때문에 광범위한 보안 위협 표면(Security Threat Surface)을 형성한다.

위협 표면 분석(Threat-Surface Analysis)은 정보를 생성, 소비, 탐색 또는 변경할 수 있는 모든 ROS 2 참여자(Participant)를 식별하는 것에서 시작한다. 노드(Node)는 센서 데이터를 발행하고, 명령을 구독하며, 서비스를 제공하고, 액션을 실행하거나 파라미터를 변경할 수 있기 때문에 특히 중요하다. 침해된 노드는 내부 공격 플랫폼(Internal Attack Platform)이 되어 공격자가 데이터 흐름을 관찰하고, 정상 구성요소를 사칭하며, 메시지를 주입하거나 하위 로봇 동작에 영향을 미칠 수 있다.

DDS 디스커버리(DDS Discovery)는 또 다른 핵심 노출 지점이다. 참여자들은 정상적인 데이터 교환이 이루어지기 전에 서로를 검색하고 사용 가능한 통신 엔드포인트(Communication Endpoint)에 관한 정보를 교환해야 한다. 디스커버리 트래픽(Discovery Traffic)이 충분히 보호되지 않으면 비인가 참여자가 토픽 이름, 통신 관계 및 활성 엔드포인트를 포함한 로봇 시스템의 구조를 파악할 수 있다. 이러한 정찰(Reconnaissance) 정보는 이후의 스푸핑(Spoofing), 가로채기(Interception), 서비스 거부(Denial-of-Service) 또는 표적 조작(Targeted Manipulation)에 활용될 수 있다.

ROS 2 토픽(Topic)은 센서 관측값, 위치 추정값, 궤적, 속도 명령, 액추에이터 상태, 진단 정보 및 AI 추론 결과와 같은 연속적인 운영 정보를 전달하기 때문에 주요 공격 표면을 형성한다. 비인가 구독자(Unauthorized Subscriber)는 기밀성(Confidentiality)을 침해할 수 있으며, 악의적인 발행자(Malicious Publisher)는 위조되거나 변조된 데이터를 주입하여 무결성(Integrity)을 위협할 수 있다. 물리적 로봇(Physical Robot)에서는 손상된 토픽 데이터가 소프트웨어 통신 계층에서 실제로 위험한 물리적 행동으로 전파될 수 있다.

서비스(Service)와 액션(Action)은 단순한 데이터 스트림이 아니라 요청-응답(Request-Response) 및 목표 지향적 제어(Goal-Oriented Control) 인터페이스를 제공하기 때문에 추가적인 위험을 발생시킨다. 민감한 서비스를 호출할 수 있는 공격자는 구성 변경, 구성요소 초기화, 운용 모드 변경 또는 권한이 필요한 기능을 실행할 수 있다. 액션 인터페이스는 내비게이션, 조작, 검사, 도킹과 같이 로봇의 물리적 상태에 직접 영향을 주는 장시간 동작을 시작할 수 있기 때문에 더욱 심각한 결과를 초래할 수 있다.

파라미터(Parameter) 역시 보안에 민감한 구성 자산(Security-Sensitive Configuration Asset)으로 취급해야 한다. ROS 2 파라미터는 제어기 게인(Controller Gain), 인식 임계값, 플래너 동작, 통신 설정, 안전 한계 및 애플리케이션 로직에 영향을 줄 수 있다. 비인가 파라미터 변경은 전형적인 네트워크 공격처럼 보이지 않을 수 있지만 시스템 동작을 미묘하게 변경할 수 있다. 공격자는 이러한 변경을 통해 성능을 저하시키거나 안전장치를 비활성화하고, 불안정한 동작을 발생시키거나 이후의 물리적 공격을 위한 조건을 조성할 수 있다.

DDS 통신 계층(Communication Layer)은 분석 범위를 애플리케이션 수준의 ROS 2 인터페이스보다 더욱 확장한다. DDS 참여자(Participant), 도메인(Domain), 발행자(Publisher), 구독자(Subscriber), 데이터라이터(DataWriter), 데이터리더(DataReader), 디스커버리 트래픽 및 전송 인터페이스(Transport Interface), 서비스 품질(Quality of Service, QoS) 설정은 공격자가 시스템과 상호작용할 수 있는 다양한 경로를 형성한다. 따라서 위협 모델링(Threat Modeling)은 ROS 2 소스 코드뿐 아니라 미들웨어 설정, DDS 구현 동작, 네트워크 노출 및 배포 토폴로지(Deployment Topology)까지 고려해야 한다.

신원(Identity)은 이러한 위협 표면의 핵심 요소이다. 신뢰할 수 있는 참여자 신원이 없다면 로봇 시스템은 정상적인 소프트웨어와 허가된 노드 또는 DDS 참여자를 사칭하는 공격자를 구분하지 못할 수 있다. 악의적인 엔드포인트가 신뢰받는 구성요소와 유사한 이름, 토픽 또는 통신 패턴을 사용할 경우 스푸핑(Spoofing)은 특히 위험해질 수 있다. 따라서 통신 권한을 참여자에게 의미 있게 연결하기 위해서는 먼저 강력한 인증(Authentication)이 필요하다.

인가(Authorization)는 인증된 참여자가 무엇을 수행하도록 허용할 것인가라는 별도의 문제를 다룬다. 예를 들어 정상적인 인식 노드(Perception Node)는 검출된 객체 정보를 발행할 권한이 필요하지만, 그렇다고 해서 자동으로 모션 명령을 발행할 권한까지 가져야 하는 것은 아니다. 과도한 권한은 침해 발생 시 피해 범위(Blast Radius)를 확대한다. 따라서 ROS 2 및 DDS 보안 아키텍처는 발행, 구독, 서비스 상호작용 및 기타 통신 작업에 최소 권한 원칙(Principle of Least Privilege)을 적용해야 한다.

기밀성 위협(Confidentiality Threat)은 로봇 통신에 비인가 주체가 관찰해서는 안 되는 정보가 포함될 때 발생한다. 카메라 스트림, 지도, 위치 데이터, 생산 정보, 운영자 명령, 임무 계획 및 텔레메트리(Telemetry)는 민감한 운영 상황을 노출할 수 있다. 따라서 공격자가 패킷을 직접 변경하지 않더라도 수동적 네트워크 모니터링(Passive Network Monitoring)은 심각한 위협이 될 수 있다. 통신 내용의 노출이 허용할 수 없는 위험을 발생시키는 경우 암호화(Encryption)와 안전한 키 관리(Secure Key Management)가 필요하다.

무결성(Integrity)과 진위성(Authenticity)은 일반적으로 제어 관련 트래픽에서 더욱 중요하다. 로봇은 다수의 분산 구성요소로부터 수신한 데이터를 기반으로 의사결정을 수행하며, 위조된 메시지는 구조적으로 정상적인 것처럼 보이면서도 위험한 정보를 포함할 수 있다. 메시지 무결성 보호(Message Integrity Protection)는 비인가 변경을 탐지하는 데 도움을 주며, 출처 인증(Origin Authentication)은 데이터 송신자의 신뢰성을 확보한다. 이러한 제어는 데이터가 내비게이션, 조작, 안전 모니터링 또는 자율 의사결정에 영향을 주는 경우 특히 중요하다.

가용성(Availability)은 로봇 통신이 시간에 민감한 경우가 많기 때문에 기밀성 및 무결성과 함께 분석해야 한다. 디스커버리 트래픽 폭주, 과도한 참여자 생성, 비정상적인 속도의 데이터 발행, 미들웨어 자원 고갈 또는 네트워크 전송 방해는 정상적인 통신을 지연시키거나 차단할 수 있다. 데이터가 탈취되거나 변경되지 않더라도 지연시간과 패킷 손실은 제어 루프를 불안정하게 만들고, 인식 파이프라인을 중단시키며, 비상 동작을 유발하거나 자율 임무를 수행할 수 없게 만들 수 있다.

서비스 품질(Quality of Service, QoS) 설정 역시 보안상의 영향을 가진다. 신뢰성(Reliability), 지속성(Durability), 히스토리 깊이(History Depth), 데드라인(Deadline), 라이블리니스(Liveliness) 및 자원 동작은 DDS가 통신을 처리하는 방식에 영향을 준다. 부적절하게 설정된 QoS는 자원 고갈(Resource Exhaustion)을 증폭시키거나 예상하지 못한 데이터 지속성을 허용할 수 있다. 따라서 보안 검토에서는 QoS를 단순한 성능 문제가 아니라 복원력 엔지니어링(Resilience Engineering)의 일부로 검토해야 하며, 특히 고속 센서와 안전 필수 명령 채널이 연산 및 네트워크 자원을 공유하는 시스템에서는 더욱 중요하다.

신뢰 경계(Trust Boundary)는 위협 분석을 체계적으로 구성하기 위한 핵심 개념이다. 안전 제어(Safety Control)와 AI 워크로드, 로봇과 플릿 인프라, 신뢰 네트워크와 비신뢰 네트워크, 컨테이너, 호스트 운영체제, 엣지 컴퓨터, 원격 운영자, 클라우드 서비스 및 서드파티 소프트웨어 사이에 각각 경계가 존재할 수 있다. 이러한 경계를 통과하는 모든 통신 경로는 인증, 인가, 기밀성, 무결성, 재전송 공격 방지(Replay Resistance), 가용성, 모니터링 및 복구 요구사항 측면에서 검토해야 한다.

배포 구성(Deployment Configuration)은 실제 위협 표면을 크게 변화시킬 수 있다. 격리된 실험실 네트워크에서 동작하는 개발용 로봇은 산업용 Wi-Fi를 사용하는 AMR 플릿, 엣지 AI 서버에 연결된 휴머노이드 또는 원격 관리되는 현장 로봇과 서로 다른 위험을 가진다. 따라서 보안 분석은 ROS 2 보안을 단순한 미들웨어 문제로 취급하지 않고 실제 인터페이스, 포트, 미들웨어 구현, 네트워크 경로, 원격 관리 채널, 컨테이너, 자격증명(Credential), 인증서(Certificate) 및 의존성을 모델링해야 한다.

운영체제(Operating System)와 소프트웨어 공급망(Software Supply Chain)은 보안 경계를 더욱 확장한다. 적절하게 보호된 DDS 세션도 침해된 호스트, 탈취된 개인 키(Private Key), 악성 ROS 패키지, 취약한 의존성 또는 비인가 컨테이너 이미지의 위험을 보완할 수는 없다. 공격 경로는 ROS 2보다 하위 계층에서 시작된 후 정상적인 미들웨어 참여자의 권한을 그대로 상속할 수 있다. 따라서 호스트 하드닝(Host Hardening), 패키지 출처 검증(Package Provenance), 자격증명 보호, 안전한 배포, 패치 관리(Patch Management), 런타임 모니터링(Runtime Monitoring)이 통신 보안과 함께 적용되어야 한다.

위협 분석에서는 내부자(Insider)와 이미 침해된 구성요소도 고려해야 한다. 인증은 알려지지 않은 참여자가 보호된 환경에 진입하는 것을 방지할 수 있지만, 인증된 소프트웨어가 계속 신뢰할 수 있는 상태로 유지된다는 것을 보장하지는 않는다. 하나의 허가된 노드가 침해되면 기존 권한이 공격에 악용될 수 있다. 세분화된 접근 제어(Fine-Grained Access Control), 권한 분리(Separation of Privileges), 행동 모니터링, 감사 로깅(Audit Logging), 자격증명 순환(Credential Rotation), 신속한 권한 폐기(Revocation)는 횡적 이동(Lateral Movement)을 제한하고 침해로 인한 영향을 줄이는 데 도움이 된다.

실용적인 ROS 2 및 DDS 위협 모델(Threat Model)은 궁극적으로 노출된 각 자산을 잠재적인 위협 행위자(Threat Actor), 공격 경로(Attack Path), 보안 통제(Security Control), 물리적 결과(Physical Consequence)와 연결해야 한다. 목적은 단순히 네트워크 취약점을 나열하는 것이 아니라 사이버 조작이 미들웨어를 통해 인식(Perception), 계획(Planning), 제어(Control), 구동(Actuation)으로 어떻게 전파될 수 있는지를 이해하는 것이다. 이러한 관점은 위협 모델링과 네트워크 보안에서 ROS 2/DDS 보호, 테스트, 사고 대응 및 규정 준수로 확장되는 전체 로봇 사이버보안 체계와 연결된다.

이러한 분석 결과는 이후의 보안 엔지니어링(Security Engineering)을 위한 기반을 제공한다. 식별된 위험은 SROS2 인증서 정책(Certificate Policy), DDS 인증 및 암호화, 토픽 및 서비스 접근 제어, 신뢰할 수 있는 노드 신원, 감사 메커니즘(Audit Mechanism), 암호화 키 수명주기 관리(Cryptographic Key Lifecycle Management), 취약점 개선(Vulnerability Remediation), 침투 테스트(Penetration Testing), 규정 준수 증적(Compliance Evidence)으로 구체화할 수 있다. 이러한 통제는 ROS 2와 DDS를 단순한 통신 미들웨어가 아니라 로봇의 사이버-물리 보안 경계(Cyber-Physical Security Boundary)로 보호하기 위한 체계적인 보안 구조를 형성한다.

##  

## 04.02. SROS2 Certificate Setup and Policy Config [w/Code]

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

SROS2 provides the security tooling used to configure ROS 2 communication on top of the security capabilities available through DDS. Its purpose is to associate ROS 2 nodes with cryptographic identities and explicit communication permissions rather than allowing every discovered participant to communicate freely. Certificate setup and policy configuration therefore convert the logical ROS 2 graph into an enforceable security architecture based on authenticated identities and authorized interactions.

A secure deployment normally begins with a dedicated security keystore that contains the trust material required by the ROS 2 system. The keystore establishes the administrative foundation from which individual node identities can be created and managed. It should be treated as security-critical infrastructure because compromise of its signing material could allow an attacker to create apparently legitimate identities and undermine trust throughout the protected ROS 2 environment.

The root of trust is represented through certificate authority material used to establish confidence in participant identities and security artifacts. Node certificates should be generated through a controlled process rather than copied informally between systems. Private keys require stronger protection than public certificates because possession of a node\'s private key may enable impersonation. File permissions, secure storage, deployment controls, backup procedures, and access auditing should therefore be incorporated into certificate lifecycle management.

Each protected ROS 2 node should receive an identity that corresponds clearly to its intended software role and deployment context. A navigation node, perception node, safety monitor, actuator interface, and fleet gateway should not share a generic identity merely for operational convenience. Distinct identities make authorization more precise, simplify auditing, and allow credentials belonging to one compromised component to be revoked or replaced without unnecessarily affecting unrelated components.

SROS2 security enclaves provide a practical mechanism for organizing security artifacts around ROS 2 participants. An enclave associates runtime processes with the certificates, keys, governance information, and permission rules required for secure DDS participation. Designing enclave boundaries requires architectural judgment because overly broad grouping weakens isolation, while excessive fragmentation can make credential administration difficult. Boundaries should generally follow meaningful software roles and trust relationships.

Authentication establishes whether a participant possesses a trusted identity, but it does not determine which ROS 2 resources that participant may use. Policy configuration addresses this second requirement. Security policies should describe legitimate communication relationships for topics, services, and actions so that authenticated participants receive only the privileges required for their functions. This separation between identity and permission is fundamental to implementing least-privilege ROS 2 communication.

A useful policy design process begins with the expected ROS 2 graph. Engineers identify nodes and their required publishers, subscribers, service clients, service servers, action clients, and action servers. These intended relationships are transformed into access-control rules rather than granting unrestricted graph access. The chapter structure specifically places certificate and policy configuration before detailed topic and service access control, node identity, auditing, and key management, reflecting this progression from trust establishment to operational enforcement. Volume_24_Robot_Cybersecurity

Topic permissions deserve careful attention because ROS 2 systems often contain communication channels with very different security consequences. A diagnostic node may legitimately subscribe to system status while having no reason to publish velocity commands. A perception component may publish object detections but should not modify actuator commands. Explicit publish and subscribe permissions prevent a compromised component from automatically converting its legitimate network presence into unrestricted control of the ROS 2 graph.

Services require similar restrictions because invoking a service can produce an immediate state change. Configuration services, lifecycle transitions, resets, calibration functions, map operations, and device-management interfaces may carry privileges substantially greater than ordinary telemetry topics. Policies should therefore distinguish service clients from service servers and grant access according to operational need. Authentication alone must never be interpreted as permission to invoke every discoverable function.

ROS 2 actions also require policy awareness because their communication behavior involves multiple underlying interactions supporting goals, feedback, status, cancellation, and results. Security configuration must account for the communication resources used by these higher-level interfaces rather than considering only obvious application topic names. Failure to represent complete communication dependencies can produce policies that either expose unnecessary resources or unexpectedly prevent legitimate robot functions during deployment.

Policy generation should be followed by deliberate review rather than immediate production deployment. Automatically observed communication can help identify required permissions, but an observed graph may include temporary debugging nodes, development tools, accidental dependencies, or overly permissive behavior. Treating every observed interaction as permanently authorized can encode development-time exposure into production security. Generated policies should therefore be interpreted as candidates that require architectural and security review.

DDS governance and permissions concepts provide the enforcement foundation beneath SROS2. Governance defines broader security behavior for DDS domains and communication, while permissions determine what authenticated participants are allowed to access. Together with identity credentials, these artifacts allow DDS security mechanisms to evaluate whether communication should proceed. Consistency between ROS 2 names, enclave identities, DDS security artifacts, and actual runtime configuration is essential for predictable enforcement.

Certificate deployment must also account for the physical distribution of robot computing resources. Credentials may be installed across embedded computers, industrial PCs, edge AI systems, containers, fleet gateways, and operator workstations. Copying one universal credential to every device simplifies deployment but creates a large compromise domain. Device- or role-specific identities reduce this exposure and support selective revocation, although they require disciplined provisioning and lifecycle automation.

Runtime security configuration should fail safely when expected trust material is missing or invalid. Allowing a production robot to silently revert from protected communication to unsecured operation defeats the purpose of certificate-based security. Deployment procedures should explicitly determine whether security is enabled, whether the expected keystore and enclave are available, whether certificates remain valid, and whether policy artifacts correspond to the software configuration being launched.

Certificate expiration and replacement must be considered during initial setup rather than after deployment. Robots may operate for years, while certificates and cryptographic policies require periodic renewal. A certificate that expires unexpectedly can interrupt communication just as effectively as a network failure. Operational planning should therefore coordinate validity periods, renewal windows, credential distribution, rollback procedures, and maintenance schedules with fleet availability and safety requirements.

Revocation is equally important when a private key, device, or software environment is suspected of compromise. The security architecture should make it possible to remove trust from the affected identity without rebuilding the entire fleet security configuration. This requirement reinforces the value of unique identities and narrowly scoped permissions. Shared credentials make revocation disruptive because disabling one compromised identity may simultaneously disable many otherwise trustworthy robot components.

Private-key handling should minimize opportunities for extraction. Keys stored as ordinary files can potentially be copied by users, malware, or compromised processes with sufficient host privileges. SROS2 configuration should therefore be complemented by operating-system access controls, restricted administrative privileges, encrypted storage where appropriate, secure provisioning, and hardware-backed protection when available. Middleware security cannot compensate for unrestricted access to the cryptographic secrets on which authentication depends.

Testing should verify both permitted and prohibited communication. A successful security test does not merely confirm that authorized nodes still exchange data; it also demonstrates that unauthorized publishers, subscribers, service clients, and other participants are rejected according to policy. Negative testing is essential because configuration mistakes frequently appear as permissions that are broader than intended rather than obvious functional failures.

Operational diagnostics must distinguish security failures from ordinary ROS 2 communication problems. Authentication rejection, permission denial, certificate problems, enclave mismatches, discovery failures, and network faults may initially appear similar to operators because nodes simply fail to communicate. Logging and audit collection should therefore preserve enough security context to identify why access was rejected without exposing private keys or other sensitive credential material.

Development and production environments should maintain separate trust domains whenever practical. Reusing production certificates in development laboratories, simulation systems, developer laptops, or continuous-integration environments expands the locations from which production identities can be stolen. Separate certificate authorities, keystores, enclaves, and policies reduce this exposure while allowing security configurations to be tested before controlled promotion into production environments.

SROS2 certificate and policy management ultimately forms the identity and authorization foundation for secure ROS 2 operation. Properly designed certificates establish who a participant is, while policies constrain what that participant can communicate. Combined with protected keys, carefully defined enclaves, least-privilege permissions, controlled provisioning, validation, renewal, revocation, and auditing, these mechanisms transform ROS 2 from an implicitly cooperative communication environment into a controlled security domain suitable for connected robotic systems.

SROS2는 DDS가 제공하는 보안 기능을 기반으로 ROS 2 통신을 구성하기 위해 사용되는 보안 도구(Security Tooling)를 제공한다. 그 목적은 검색된 모든 참여자가 자유롭게 통신하도록 허용하는 대신, ROS 2 노드(Node)를 암호학적 신원(Cryptographic Identity) 및 명시적인 통신 권한(Communication Permission)과 연결하는 것이다. 따라서 인증서 설정(Certificate Setup)과 정책 구성(Policy Configuration)은 논리적인 ROS 2 그래프(Graph)를 인증된 신원과 허가된 상호작용에 기반한 실제 집행 가능한 보안 아키텍처(Security Architecture)로 변환한다.

안전한 배포(Secure Deployment)는 일반적으로 ROS 2 시스템에 필요한 신뢰 자료(Trust Material)를 저장하는 전용 보안 키스토어(Security Keystore)를 구축하는 것에서 시작한다. 키스토어는 개별 노드의 신원을 생성하고 관리하는 관리 기반을 형성한다. 키스토어의 서명 자료(Signing Material)가 침해되면 공격자가 정상적으로 보이는 신원을 생성하여 보호된 ROS 2 환경 전체의 신뢰를 훼손할 수 있으므로, 키스토어는 보안 핵심 인프라(Security-Critical Infrastructure)로 취급해야 한다.

신뢰 루트(Root of Trust)는 참여자 신원과 보안 산출물에 대한 신뢰를 설정하는 데 사용되는 인증 기관(Certificate Authority, CA) 자료를 통해 구성된다. 노드 인증서(Node Certificate)는 시스템 간에 비공식적으로 복사하는 방식이 아니라 통제된 프로세스를 통해 생성해야 한다. 개인 키(Private Key)를 보유하면 해당 노드를 사칭할 수 있으므로 개인 키는 공개 인증서보다 강력하게 보호해야 한다. 따라서 파일 권한, 안전한 저장소, 배포 통제, 백업 절차 및 접근 감사(Access Auditing)를 인증서 수명주기 관리(Certificate Lifecycle Management)에 포함해야 한다.

보호되는 각 ROS 2 노드는 의도된 소프트웨어 역할과 배포 환경을 명확하게 나타내는 신원(Identity)을 가져야 한다. 내비게이션 노드(Navigation Node), 인식 노드(Perception Node), 안전 모니터(Safety Monitor), 액추에이터 인터페이스(Actuator Interface), 플릿 게이트웨이(Fleet Gateway)가 운영 편의성만을 위해 하나의 일반적인 신원을 공유해서는 안 된다. 서로 다른 신원을 사용하면 인가(Authorization)를 더욱 정밀하게 적용하고 감사를 단순화하며, 하나의 구성요소가 침해되었을 때 관련 없는 구성요소에 영향을 주지 않고 해당 자격증명(Credential)을 폐기하거나 교체할 수 있다.

SROS2 보안 엔클레이브(Security Enclave)는 ROS 2 참여자를 중심으로 보안 산출물을 구성하기 위한 실용적인 메커니즘을 제공한다. 엔클레이브는 런타임 프로세스를 안전한 DDS 참여에 필요한 인증서, 키, 거버넌스 정보(Governance Information), 권한 규칙(Permission Rule)과 연결한다. 지나치게 넓은 그룹화는 격리성을 약화시키고 지나친 세분화는 자격증명 관리를 어렵게 만들기 때문에 엔클레이브 경계를 설계할 때는 아키텍처적 판단이 필요하다. 일반적으로 경계는 의미 있는 소프트웨어 역할과 신뢰 관계(Trust Relationship)를 따라 설정해야 한다.

인증(Authentication)은 참여자가 신뢰할 수 있는 신원을 보유하고 있는지를 확인하지만, 해당 참여자가 어떤 ROS 2 자원을 사용할 수 있는지를 결정하지는 않는다. 정책 구성(Policy Configuration)은 이러한 두 번째 요구사항을 처리한다. 보안 정책(Security Policy)은 토픽(Topic), 서비스(Service), 액션(Action)에 대한 정상적인 통신 관계를 정의하여 인증된 참여자에게 자신의 기능을 수행하는 데 필요한 권한만 부여해야 한다. 이러한 신원과 권한의 분리는 최소 권한 기반 ROS 2 통신을 구현하는 핵심 원칙이다.

효과적인 정책 설계(Policy Design)는 예상되는 ROS 2 그래프에서 시작한다. 엔지니어는 노드와 해당 노드에 필요한 발행자(Publisher), 구독자(Subscriber), 서비스 클라이언트(Service Client), 서비스 서버(Service Server), 액션 클라이언트(Action Client), 액션 서버(Action Server)를 식별한다. 이후 이러한 의도된 관계를 무제한적인 그래프 접근 권한이 아니라 접근 제어 규칙(Access-Control Rule)으로 변환한다. 이러한 과정은 신뢰를 먼저 설정한 후 세부적인 토픽 및 서비스 접근 제어와 운영 단계의 보안 집행으로 발전하는 구조를 형성한다.

토픽 권한(Topic Permission)은 ROS 2 시스템이 서로 다른 보안 영향을 가진 다양한 통신 채널을 포함하기 때문에 신중하게 설정해야 한다. 진단 노드(Diagnostic Node)는 시스템 상태를 정상적으로 구독할 수 있지만 속도 명령을 발행할 이유는 없다. 인식 구성요소(Perception Component)는 객체 검출 결과를 발행할 수 있지만 액추에이터 명령을 변경해서는 안 된다. 명시적인 발행 및 구독 권한은 침해된 구성요소가 정상적인 네트워크 접근 권한을 이용하여 ROS 2 그래프 전체를 무제한으로 제어하는 것을 방지한다.

서비스(Service) 역시 호출 자체가 즉각적인 상태 변화를 발생시킬 수 있기 때문에 유사한 제한이 필요하다. 구성 서비스(Configuration Service), 수명주기 전환(Lifecycle Transition), 초기화, 보정(Calibration), 지도 관련 기능 및 장치 관리 인터페이스(Device-Management Interface)는 일반적인 텔레메트리 토픽보다 훨씬 높은 권한을 가질 수 있다. 따라서 정책은 서비스 클라이언트와 서비스 서버를 구분하고 운영상 필요한 범위에 따라 접근을 허용해야 한다. 인증되었다는 사실만으로 검색 가능한 모든 기능을 호출할 권한이 있다고 해석해서는 안 된다.

ROS 2 액션(Action)도 목표(Goal), 피드백(Feedback), 상태(Status), 취소(Cancellation), 결과(Result)를 지원하는 여러 하위 통신 상호작용을 포함하기 때문에 정책 관점에서 고려해야 한다. 보안 구성은 명확하게 보이는 애플리케이션 토픽 이름만 고려하는 것이 아니라 이러한 상위 수준 인터페이스가 사용하는 통신 자원 전체를 반영해야 한다. 전체 통신 의존성을 표현하지 못하면 불필요한 자원을 노출하거나 실제 배포 과정에서 정상적인 로봇 기능을 예상치 못하게 차단하는 정책이 만들어질 수 있다.

정책 생성(Policy Generation) 이후에는 즉시 운영 환경에 배포하는 대신 의도적인 검토 과정을 수행해야 한다. 실제로 관찰된 통신을 이용하면 필요한 권한을 식별할 수 있지만, 관찰된 그래프에는 임시 디버깅 노드(Debugging Node), 개발 도구, 의도하지 않은 의존성 또는 지나치게 허용적인 동작이 포함될 수 있다. 관찰된 모든 상호작용을 영구적으로 허용하면 개발 단계의 노출이 운영 보안 정책에 그대로 반영될 수 있다. 따라서 생성된 정책은 아키텍처 및 보안 검토가 필요한 후보 정책으로 취급해야 한다.

DDS 거버넌스(DDS Governance)와 권한(Permissions) 개념은 SROS2 하위에서 보안 집행의 기반을 제공한다. 거버넌스는 DDS 도메인과 통신에 적용되는 보다 광범위한 보안 동작을 정의하고, 권한은 인증된 참여자가 접근할 수 있는 자원을 결정한다. 이러한 보안 산출물은 신원 자격증명(Identity Credential)과 결합되어 DDS 보안 메커니즘이 특정 통신의 허용 여부를 판단하도록 한다. 예측 가능한 보안 집행을 위해서는 ROS 2 이름, 엔클레이브 신원, DDS 보안 산출물 및 실제 런타임 구성 사이의 일관성이 필수적이다.

인증서 배포(Certificate Deployment)는 로봇 컴퓨팅 자원이 물리적으로 분산되어 있다는 점도 고려해야 한다. 자격증명은 임베디드 컴퓨터(Embedded Computer), 산업용 PC(Industrial PC), 엣지 AI 시스템(Edge AI System), 컨테이너(Container), 플릿 게이트웨이 및 운영자 워크스테이션(Operator Workstation)에 설치될 수 있다. 모든 장치에 하나의 공통 자격증명을 복사하면 배포는 단순해지지만 침해 범위가 크게 확대된다. 장치별 또는 역할별 신원을 사용하면 이러한 노출을 줄이고 선택적인 폐기를 지원할 수 있지만 체계적인 프로비저닝(Provisioning)과 수명주기 자동화가 필요하다.

런타임 보안 구성(Runtime Security Configuration)은 필요한 신뢰 자료가 없거나 유효하지 않을 경우 안전하게 실패(Fail Safely)하도록 설계해야 한다. 운영 중인 로봇이 보호된 통신에서 비보안 통신으로 조용히 전환하도록 허용하면 인증서 기반 보안의 목적이 사라진다. 따라서 배포 절차에서는 보안 활성화 여부, 예상된 키스토어와 엔클레이브의 존재 여부, 인증서의 유효성, 정책 산출물이 실행되는 소프트웨어 구성과 일치하는지를 명시적으로 확인해야 한다.

인증서 만료(Certificate Expiration)와 교체는 배포 이후가 아니라 초기 설정 단계부터 고려해야 한다. 로봇은 수년간 운용될 수 있지만 인증서와 암호화 정책(Cryptographic Policy)은 주기적으로 갱신해야 한다. 예상하지 못한 인증서 만료는 네트워크 장애와 마찬가지로 통신을 중단시킬 수 있다. 따라서 운영 계획은 인증서 유효기간, 갱신 기간(Renewal Window), 자격증명 배포, 롤백 절차(Rollback Procedure), 유지보수 일정을 플릿 가용성(Fleet Availability) 및 안전 요구사항과 연계해야 한다.

개인 키, 장치 또는 소프트웨어 환경이 침해된 것으로 의심될 경우 폐기(Revocation) 역시 중요하다. 보안 아키텍처는 플릿 전체의 보안 구성을 다시 구축하지 않고도 영향을 받은 신원에 대한 신뢰를 제거할 수 있어야 한다. 이러한 요구사항은 고유한 신원과 좁게 제한된 권한의 중요성을 더욱 강화한다. 공유 자격증명을 사용하면 하나의 침해된 신원을 비활성화할 때 정상적인 여러 로봇 구성요소까지 동시에 사용할 수 없게 될 수 있으므로 폐기 과정이 복잡해진다.

개인 키 처리(Private-Key Handling)는 키가 추출될 가능성을 최소화해야 한다. 일반 파일로 저장된 키는 충분한 호스트 권한을 가진 사용자, 악성코드 또는 침해된 프로세스에 의해 복사될 수 있다. 따라서 SROS2 구성은 운영체제 접근 제어, 제한된 관리자 권한, 필요한 경우 암호화 저장소(Encrypted Storage), 안전한 프로비저닝 및 사용 가능한 경우 하드웨어 기반 보호(Hardware-Backed Protection)와 결합해야 한다. 미들웨어 보안만으로는 인증의 기반이 되는 암호학적 비밀정보에 대한 무제한 접근을 보완할 수 없다.

테스트(Testing)는 허용된 통신뿐만 아니라 금지된 통신까지 검증해야 한다. 성공적인 보안 테스트는 승인된 노드가 정상적으로 데이터를 교환하는지만 확인하는 것이 아니라, 비인가 발행자, 구독자, 서비스 클라이언트 및 기타 참여자가 정책에 따라 실제로 거부되는지를 입증해야 한다. 구성 오류는 명확한 기능 장애보다 의도한 것보다 넓은 권한으로 나타나는 경우가 많기 때문에 부정 테스트(Negative Testing)는 필수적이다.

운영 진단(Operational Diagnostics)은 보안 장애와 일반적인 ROS 2 통신 문제를 구분할 수 있어야 한다. 인증 거부(Authentication Rejection), 권한 거부(Permission Denial), 인증서 문제, 엔클레이브 불일치, 디스커버리 실패(Discovery Failure), 네트워크 장애는 노드 간 통신이 이루어지지 않는다는 점에서 운영자에게 비슷하게 보일 수 있다. 따라서 로깅(Logging)과 감사 수집(Audit Collection)은 개인 키나 기타 민감한 자격증명 자료를 노출하지 않으면서 접근이 거부된 이유를 식별할 수 있을 정도의 보안 컨텍스트(Security Context)를 보존해야 한다.

가능한 경우 개발 환경(Development Environment)과 운영 환경(Production Environment)은 서로 분리된 신뢰 도메인(Trust Domain)을 유지해야 한다. 운영용 인증서를 개발 실험실, 시뮬레이션 시스템, 개발자 노트북 또는 지속적 통합(Continuous Integration, CI) 환경에서 재사용하면 운영 신원이 탈취될 수 있는 위치가 증가한다. 별도의 인증 기관, 키스토어, 엔클레이브 및 정책을 사용하면 이러한 노출을 줄이는 동시에 보안 구성을 검증한 후 통제된 절차를 통해 운영 환경으로 승격할 수 있다.

SROS2 인증서 및 정책 관리(Certificate and Policy Management)는 궁극적으로 안전한 ROS 2 운영을 위한 신원 및 인가 기반을 형성한다. 적절하게 설계된 인증서는 참여자가 누구인지를 확립하고, 정책은 해당 참여자가 수행할 수 있는 통신을 제한한다. 보호된 키, 신중하게 정의된 엔클레이브, 최소 권한 정책, 통제된 프로비저닝, 검증, 갱신, 폐기 및 감사와 이러한 메커니즘을 결합하면 ROS 2를 암묵적으로 상호 신뢰하는 통신 환경에서 연결형 로봇 시스템(Connected Robotic System)에 적합한 통제된 보안 도메인(Controlled Security Domain)으로 전환할 수 있다.

##  

## 04.03. DDS Security Plugin Authentication and Encrypt [w/Code]

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

The DDS Security plugin architecture provides the middleware-level mechanisms that protect communication between authenticated DDS participants. In ROS 2 deployments, these mechanisms operate beneath the node and application layers, allowing security controls to be applied directly to discovery and data exchange. Authentication establishes participant identity, while cryptographic protection preserves confidentiality and integrity as information moves across potentially untrusted networks.

DDS Security is commonly structured around interoperable security functions rather than a single monolithic protection mechanism. Authentication, access control, cryptographic protection, logging, and data tagging can be handled as distinct security capabilities. This separation allows middleware implementations to enforce security at appropriate stages of participant discovery and communication while preserving the distributed, data-centric architecture on which ROS 2 communication depends.

Authentication begins when DDS participants attempt to establish trusted communication. Instead of accepting another participant merely because it appears within the same DDS domain, the security layer validates cryptographic identity credentials. Certificates and associated private keys allow participants to demonstrate possession of trusted identities. This changes discovery from an implicitly trusted process into one in which identity can be verified before sensitive communication relationships are established.

Public key infrastructure provides the trust framework supporting certificate-based authentication. A participant presents credentials associated with a trusted certificate authority, while cryptographic verification determines whether those credentials belong to an accepted trust domain. The security of this process depends not only on certificate validation but also on protection of private keys, trustworthy certificate issuance, appropriate validity periods, and controlled replacement or revocation when credentials become compromised.

Mutual authentication is especially important in robotic systems because trust must normally be established in both directions. A controller should verify the identity of a sensor or planning participant, while that participant should also verify the controller with which it communicates. Mutual verification reduces opportunities for rogue middleware participants, impersonated nodes, unauthorized diagnostic tools, or compromised computers to join a DDS environment and interact with legitimate robot components.

The authentication handshake must also resist replay and impersonation attempts. An attacker should not be able to capture a previous authentication exchange and reuse it to establish a fraudulent session. Cryptographic challenges, signed information, session-specific values, and validated identity material help bind an authentication exchange to legitimate participants. Authentication failures should terminate trust establishment rather than silently permitting communication through an unsecured fallback path.

Once identities have been authenticated, access-control mechanisms determine whether communication between those identities is permitted. Authentication answers who the participant is, whereas authorization determines which domains, topics, partitions, or communication operations it may use. This distinction is critical because a valid certificate should not provide unrestricted middleware access. A compromised but authenticated participant must remain constrained by permissions associated with its intended operational role.

Cryptographic protection provides confidentiality and integrity for DDS communication after trust relationships have been established. Encryption prevents unauthorized observers from reading protected data, while integrity mechanisms allow receivers to detect unauthorized modification. These protections are particularly important for robot traffic carrying actuator commands, localization information, maps, sensor observations, mission instructions, safety states, AI outputs, and other information capable of influencing autonomous physical behavior.

DDS security can protect communication at different scopes depending on middleware configuration and operational requirements. Protection may apply to discovery-related exchanges, metadata, or application data carried between DataWriters and DataReaders. Selecting appropriate protection requires understanding which information is sensitive and which communication paths cross untrusted boundaries. Encrypting application payloads while leaving sensitive discovery information unnecessarily exposed may still reveal valuable architectural intelligence to an attacker.

Discovery protection deserves special attention because DDS relies on distributed discovery to identify participants and endpoints. Unprotected discovery traffic may reveal participant existence, endpoint relationships, topic information, and communication patterns even when application payloads are encrypted. Protecting discovery therefore reduces reconnaissance opportunities and makes it more difficult for unauthorized systems to map the structure of the robot\'s middleware environment before attempting a targeted attack.

Encryption introduces key-management requirements beyond participant identity certificates. Secure communication depends on cryptographic material being generated, distributed, derived, used, and replaced without exposing secret values. Long-lived static keys increase the consequences of compromise, while poorly coordinated key changes can interrupt robot communication. Key lifecycle design must therefore balance cryptographic security with the availability and timing requirements of distributed robotic applications.

The protection mode selected for DDS traffic should reflect the consequences of disclosure and manipulation. Some telemetry may require integrity protection without strong confidentiality, while mission data, proprietary sensor information, or remotely issued commands may justify encryption as well. Applying identical protection to every traffic class can unnecessarily consume computing and network resources, so security architecture should classify communication according to risk rather than treating all DDS traffic uniformly.

Performance is a significant consideration because authentication and encryption consume CPU time, memory, bandwidth, and sometimes additional communication exchanges. High-rate cameras, LiDAR streams, joint states, control commands, and AI pipelines may generate substantial DDS traffic. Security evaluation should measure throughput, latency, jitter, discovery time, and processor utilization under realistic workloads to ensure that cryptographic protection does not violate real-time or safety-related timing requirements.

Hardware acceleration can reduce the cost of cryptographic operations when supported by the target computing platform. Nevertheless, performance optimization must not weaken security by disabling authentication or encryption on critical channels merely to meet timing objectives. A better approach is to classify data, isolate critical communication paths, select suitable algorithms and protection scopes, and validate the complete system under representative computational and network loads.

Configuration consistency is another major operational requirement. Participants must agree on compatible security expectations, trust anchors, certificates, permissions, and cryptographic behavior. A certificate signed by an unexpected authority, an incorrect security domain, mismatched permissions, or inconsistent protection requirements may prevent discovery or data exchange. Such failures can resemble ordinary middleware or network problems, making security-aware diagnostics essential during integration and field operation.

Security logging should record significant authentication and cryptographic events without exposing secret material. Failed identity verification, rejected participants, permission violations, invalid certificates, unexpected security configurations, and repeated handshake failures can provide early evidence of attack or configuration drift. These events should be correlated with ROS 2, host, network, and fleet monitoring data so that operators can distinguish malicious activity from certificate expiration, deployment errors, or software defects.

Fail-secure behavior is particularly important for production robots. If required authentication or cryptographic configuration cannot be loaded, a security-sensitive participant should not automatically continue through unprotected DDS communication. Such fallback behavior can transform a configuration mistake into a security bypass. Deployment validation should confirm that protected participants reject insecure peers and that failures lead to defined degraded, isolated, or safe operating states.

Testing must include adversarial cases rather than confirming only successful encrypted communication. Engineers should verify rejection of untrusted certificates, invalid signatures, expired credentials, unauthorized participants, altered protected traffic, incompatible permissions, and attempts to communicate without required protection. Tests should also evaluate recovery after credential renewal or communication interruption, ensuring that security controls remain effective throughout normal maintenance and abnormal conditions.

DDS Security must ultimately be integrated with the broader ROS 2 security architecture rather than treated as an isolated encryption feature. The chapter structure places DDS authentication and encryption after SROS2 certificate and policy configuration and before topic/service access control, node identity, audit logging, key rotation, vulnerability remediation, penetration testing, and compliance mapping. This reflects a layered progression from identity establishment toward complete lifecycle security. Volume_24_Robot_Cybersecurity

When properly configured, DDS Security creates a protected middleware trust fabric for distributed robotic software. Authentication determines which participants can establish trusted relationships, authorization restricts what those participants may access, and cryptographic protection safeguards communication against observation and manipulation. Combined with disciplined certificate management, secure key handling, monitoring, testing, and fail-secure deployment, these controls substantially reduce the middleware attack surface of connected ROS 2 robots.

DDS 보안 플러그인 아키텍처(DDS Security Plugin Architecture)는 인증된 DDS 참여자(Participant) 간의 통신을 보호하는 미들웨어 수준의 메커니즘(Middleware-Level Mechanism)을 제공한다. ROS 2 배포 환경에서 이러한 메커니즘은 노드(Node)와 애플리케이션 계층(Application Layer) 아래에서 동작하며, 디스커버리(Discovery)와 데이터 교환에 직접 보안 통제를 적용할 수 있도록 한다. 인증(Authentication)은 참여자의 신원을 확인하고, 암호학적 보호(Cryptographic Protection)는 잠재적으로 신뢰할 수 없는 네트워크를 통해 정보가 이동하는 동안 기밀성(Confidentiality)과 무결성(Integrity)을 유지한다.

DDS 보안(DDS Security)은 일반적으로 하나의 단일한 보안 메커니즘이 아니라 상호운용 가능한 보안 기능(Interoperable Security Function)을 중심으로 구성된다. 인증(Authentication), 접근 제어(Access Control), 암호학적 보호(Cryptographic Protection), 로깅(Logging), 데이터 태깅(Data Tagging)은 서로 구분된 보안 기능으로 처리할 수 있다. 이러한 분리를 통해 미들웨어 구현체는 ROS 2 통신의 기반이 되는 분산형 데이터 중심 아키텍처(Distributed Data-Centric Architecture)를 유지하면서 참여자 디스커버리와 통신의 적절한 단계에서 보안을 집행할 수 있다.

인증(Authentication)은 DDS 참여자들이 신뢰할 수 있는 통신을 설정하려고 할 때 시작된다. 보안 계층은 다른 참여자가 동일한 DDS 도메인(Domain)에 존재한다는 이유만으로 이를 허용하지 않고 암호학적 신원 자격증명(Cryptographic Identity Credential)을 검증한다. 인증서(Certificate)와 연결된 개인 키(Private Key)를 사용하면 참여자는 신뢰할 수 있는 신원을 보유하고 있음을 증명할 수 있다. 이를 통해 디스커버리는 암묵적으로 신뢰되는 과정에서 민감한 통신 관계가 형성되기 전에 신원을 검증하는 과정으로 전환된다.

공개 키 기반구조(Public Key Infrastructure, PKI)는 인증서 기반 인증(Certificate-Based Authentication)을 지원하는 신뢰 프레임워크(Trust Framework)를 제공한다. 참여자는 신뢰할 수 있는 인증 기관(Certificate Authority, CA)과 연결된 자격증명을 제시하고, 암호학적 검증을 통해 해당 자격증명이 허용된 신뢰 도메인(Trust Domain)에 속하는지 판단한다. 이 과정의 보안은 인증서 검증뿐만 아니라 개인 키 보호, 신뢰할 수 있는 인증서 발급, 적절한 유효기간, 자격증명이 침해되었을 때 통제된 교체 및 폐기(Revocation)에 의존한다.

상호 인증(Mutual Authentication)은 일반적으로 양방향으로 신뢰를 설정해야 하는 로봇 시스템에서 특히 중요하다. 제어기(Controller)는 센서 또는 계획 참여자(Planning Participant)의 신원을 검증해야 하며, 해당 참여자 역시 자신이 통신하는 제어기의 신원을 검증해야 한다. 상호 검증은 악성 미들웨어 참여자, 노드 사칭, 비인가 진단 도구 또는 침해된 컴퓨터가 DDS 환경에 참여하여 정상적인 로봇 구성요소와 상호작용할 가능성을 줄여준다.

인증 핸드셰이크(Authentication Handshake)는 재전송 공격(Replay Attack)과 사칭(Impersonation) 시도에도 대응해야 한다. 공격자가 이전의 인증 교환 과정을 캡처한 후 이를 재사용하여 위조된 세션을 설정할 수 없어야 한다. 암호학적 챌린지(Cryptographic Challenge), 서명된 정보(Signed Information), 세션별 값(Session-Specific Value), 검증된 신원 자료를 사용하면 인증 교환을 정상적인 참여자와 연결할 수 있다. 인증에 실패하면 비보안 통신 경로로 조용히 전환하는 대신 신뢰 설정 과정을 종료해야 한다.

신원이 인증된 이후에는 접근 제어 메커니즘(Access-Control Mechanism)이 해당 신원 간의 통신 허용 여부를 결정한다. 인증은 참여자가 누구인지를 확인하는 반면, 인가(Authorization)는 해당 참여자가 어떤 도메인, 토픽(Topic), 파티션(Partition) 또는 통신 작업을 사용할 수 있는지를 결정한다. 유효한 인증서를 보유했다는 사실이 무제한적인 미들웨어 접근 권한을 의미해서는 안 되므로 이러한 구분은 매우 중요하다. 침해되었지만 정상적으로 인증된 참여자도 원래의 운영 역할에 할당된 권한으로 제한되어야 한다.

암호학적 보호(Cryptographic Protection)는 신뢰 관계가 설정된 이후 DDS 통신의 기밀성과 무결성을 제공한다. 암호화(Encryption)는 비인가 관찰자가 보호된 데이터를 읽는 것을 방지하고, 무결성 메커니즘(Integrity Mechanism)은 수신자가 비인가 변경을 탐지할 수 있도록 한다. 이러한 보호는 액추에이터 명령, 위치 정보, 지도, 센서 관측값, 임무 명령, 안전 상태, AI 출력과 같이 자율적인 물리적 행동에 영향을 줄 수 있는 정보를 전달하는 로봇 트래픽에서 특히 중요하다.

DDS 보안은 미들웨어 구성과 운영 요구사항에 따라 서로 다른 범위의 통신을 보호할 수 있다. 보호 대상에는 디스커버리 관련 정보 교환, 메타데이터(Metadata), 데이터라이터(DataWriter)와 데이터리더(DataReader) 사이에서 전달되는 애플리케이션 데이터 등이 포함될 수 있다. 적절한 보호 범위를 선택하려면 어떤 정보가 민감한지, 어떤 통신 경로가 신뢰할 수 없는 경계를 통과하는지 이해해야 한다. 애플리케이션 페이로드만 암호화하면서 민감한 디스커버리 정보를 불필요하게 노출하면 공격자에게 중요한 아키텍처 정보를 제공할 수 있다.

DDS는 참여자와 엔드포인트(Endpoint)를 식별하기 위해 분산 디스커버리(Distributed Discovery)에 의존하므로 디스커버리 보호(Discovery Protection)는 특별한 주의가 필요하다. 보호되지 않은 디스커버리 트래픽은 애플리케이션 페이로드가 암호화되어 있더라도 참여자의 존재, 엔드포인트 관계, 토픽 정보 및 통신 패턴을 노출할 수 있다. 따라서 디스커버리를 보호하면 정찰(Reconnaissance) 기회를 줄이고, 비인가 시스템이 표적 공격을 시도하기 전에 로봇 미들웨어 환경의 구조를 파악하기 어렵게 만들 수 있다.

암호화(Encryption)는 참여자의 신원 인증서와 별도로 키 관리(Key Management) 요구사항을 발생시킨다. 안전한 통신을 위해서는 비밀 값이 노출되지 않도록 암호학적 자료를 생성, 배포, 파생, 사용 및 교체해야 한다. 장기간 유지되는 정적 키(Static Key)는 침해되었을 때 피해를 확대하며, 제대로 조정되지 않은 키 변경은 로봇 통신을 중단시킬 수 있다. 따라서 키 수명주기 설계(Key Lifecycle Design)는 암호학적 보안과 분산 로봇 애플리케이션의 가용성 및 시간 요구사항 사이의 균형을 고려해야 한다.

DDS 트래픽에 적용되는 보호 모드(Protection Mode)는 정보 노출 및 조작으로 발생할 수 있는 결과를 고려하여 선택해야 한다. 일부 텔레메트리(Telemetry)는 강력한 기밀성보다 무결성 보호가 더 중요할 수 있으며, 임무 데이터, 독점적인 센서 정보 또는 원격 명령은 암호화까지 요구할 수 있다. 모든 트래픽에 동일한 보호 수준을 적용하면 불필요하게 연산 및 네트워크 자원을 소비할 수 있으므로 보안 아키텍처는 모든 DDS 트래픽을 동일하게 취급하기보다 위험도에 따라 통신을 분류해야 한다.

인증과 암호화는 CPU 시간, 메모리, 대역폭 및 경우에 따라 추가적인 통신 교환을 필요로 하므로 성능(Performance)은 중요한 고려사항이다. 고속 카메라, 라이다(LiDAR) 스트림, 관절 상태(Joint State), 제어 명령 및 AI 파이프라인은 상당한 양의 DDS 트래픽을 생성할 수 있다. 보안 평가는 실제 운용 환경과 유사한 워크로드에서 처리량(Throughput), 지연시간(Latency), 지터(Jitter), 디스커버리 시간 및 프로세서 사용률을 측정하여 암호학적 보호가 실시간 또는 안전 관련 시간 요구사항을 위반하지 않는지 확인해야 한다.

대상 컴퓨팅 플랫폼에서 지원하는 경우 하드웨어 가속(Hardware Acceleration)을 통해 암호학적 연산 비용을 줄일 수 있다. 그러나 성능 최적화를 이유로 중요한 통신 채널의 인증이나 암호화를 비활성화하여 보안을 약화시켜서는 안 된다. 더 적절한 방법은 데이터를 분류하고, 중요한 통신 경로를 격리하며, 적절한 알고리즘과 보호 범위를 선택하고, 대표적인 연산 및 네트워크 부하에서 전체 시스템을 검증하는 것이다.

구성 일관성(Configuration Consistency) 역시 중요한 운영 요구사항이다. 참여자들은 호환 가능한 보안 요구사항, 신뢰 앵커(Trust Anchor), 인증서, 권한 및 암호학적 동작에 대해 일관된 구성을 가져야 한다. 예상하지 못한 인증 기관이 서명한 인증서, 잘못된 보안 도메인, 일치하지 않는 권한 또는 서로 다른 보호 요구사항은 디스커버리나 데이터 교환을 차단할 수 있다. 이러한 장애는 일반적인 미들웨어 또는 네트워크 문제처럼 보일 수 있기 때문에 시스템 통합 및 현장 운영 과정에서는 보안을 고려한 진단(Security-Aware Diagnostics)이 필수적이다.

보안 로깅(Security Logging)은 비밀 자료를 노출하지 않으면서 중요한 인증 및 암호화 관련 이벤트를 기록해야 한다. 신원 검증 실패, 거부된 참여자, 권한 위반, 유효하지 않은 인증서, 예상하지 못한 보안 구성 및 반복적인 핸드셰이크 실패는 공격 또는 구성 드리프트(Configuration Drift)의 초기 증거가 될 수 있다. 이러한 이벤트는 ROS 2, 호스트, 네트워크 및 플릿 모니터링 데이터와 연계하여 운영자가 악의적인 활동과 인증서 만료, 배포 오류 또는 소프트웨어 결함을 구분할 수 있도록 해야 한다.

안전한 실패 동작(Fail-Secure Behavior)은 운영 환경의 로봇에서 특히 중요하다. 필요한 인증 또는 암호화 구성을 불러올 수 없는 경우 보안에 민감한 참여자가 자동으로 보호되지 않은 DDS 통신을 계속해서는 안 된다. 이러한 폴백 동작(Fallback Behavior)은 단순한 구성 오류를 보안 우회(Security Bypass)로 전환할 수 있다. 따라서 배포 검증 과정에서는 보호된 참여자가 비보안 피어(Insecure Peer)를 거부하는지 확인하고, 장애 발생 시 정의된 성능 저하 상태(Degraded State), 격리 상태(Isolated State) 또는 안전 상태(Safe State)로 전환되는지 검증해야 한다.

테스트(Testing)는 암호화 통신의 성공 여부만 확인하는 것이 아니라 적대적 상황(Adversarial Case)을 포함해야 한다. 엔지니어는 신뢰할 수 없는 인증서, 유효하지 않은 서명, 만료된 자격증명, 비인가 참여자, 변조된 보호 트래픽, 호환되지 않는 권한 및 필수 보안 기능 없이 통신하려는 시도가 실제로 거부되는지 확인해야 한다. 또한 자격증명 갱신이나 통신 중단 이후의 복구 과정도 평가하여 정상적인 유지보수 및 비정상적인 상황에서도 보안 통제가 지속적으로 효과를 유지하는지 검증해야 한다.

DDS 보안(DDS Security)은 독립적인 암호화 기능으로 취급하는 것이 아니라 더 광범위한 ROS 2 보안 아키텍처와 통합해야 한다. 전체 구조에서는 SROS2 인증서 및 정책 구성 이후 DDS 인증 및 암호화를 적용하고, 이후 토픽 및 서비스 접근 제어, 노드 신원, 감사 로깅, 키 순환(Key Rotation), 취약점 개선(Vulnerability Remediation), 침투 테스트(Penetration Testing), 규정 준수 매핑(Compliance Mapping)으로 확장한다. 이는 신원 확립에서 완전한 수명주기 보안(Lifecycle Security)으로 발전하는 계층적 보안 구조를 의미한다.

적절하게 구성된 DDS 보안은 분산 로봇 소프트웨어를 위한 보호된 미들웨어 신뢰 구조(Protected Middleware Trust Fabric)를 형성한다. 인증은 어떤 참여자가 신뢰 관계를 설정할 수 있는지 결정하고, 인가는 해당 참여자가 접근할 수 있는 범위를 제한하며, 암호학적 보호는 통신이 관찰되거나 조작되는 것을 방지한다. 체계적인 인증서 관리, 안전한 키 처리, 모니터링, 테스트 및 안전한 실패 기반 배포와 이러한 통제를 결합하면 연결형 ROS 2 로봇(Connected ROS 2 Robot)의 미들웨어 공격 표면(Middleware Attack Surface)을 크게 줄일 수 있다.

##  

## 04.04. ROS2 Topic Service Access Control Policy [w/Code]

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Access control in ROS 2 defines which authenticated participants are permitted to publish, subscribe, request, or provide specific communication resources. Authentication alone confirms identity but does not establish operational authority. A secure robot therefore requires explicit authorization policies that restrict each node to the topics, services, and actions necessary for its assigned function, reducing the consequences of compromised or misconfigured software.

Topic access control should distinguish publishing rights from subscription rights because the security consequences are fundamentally different. A localization node may publish pose estimates while consuming sensor observations, whereas a motor-control node may subscribe to velocity commands without permission to generate localization data. Separating these privileges prevents authenticated participants from using legitimate network membership to perform communication operations outside their intended responsibilities.

The principle of least privilege should guide policy construction. Each node receives only the permissions required to perform its defined task, and unnecessary communication paths remain denied. Broad wildcard permissions can simplify early development but significantly increase the attack surface in production. If a node is compromised, narrowly scoped permissions limit lateral movement by preventing the attacker from immediately publishing to or subscribing from unrelated ROS 2 resources.

Command topics require particularly strict controls because unauthorized publication can directly influence physical behavior. Velocity, trajectory, actuator, docking, manipulation, flight-control, and emergency-state messages may cause immediate changes in robot motion. Policies should limit publication of such information to specifically authorized control components while allowing only justified subscribers. Safety-critical communication should be separated from diagnostic, visualization, and general application traffic whenever practical.

Sensor topics present a different security profile. Camera images, LiDAR point clouds, radar observations, joint states, localization information, and environmental maps may need to be consumed by several perception and planning components. However, unrestricted subscription can expose operationally sensitive information, while unauthorized publication can inject fabricated observations. Policies should therefore address both confidentiality of sensor streams and integrity of the data used for autonomous decision making.

Service access control is essential because services commonly trigger discrete operations rather than continuously distributing state. A service request may reset hardware, change configuration, load a map, clear internal state, activate a component, or initiate calibration. An authenticated node should not automatically be allowed to invoke every visible service. Client and server permissions should instead reflect the exact operational relationships defined by the robot architecture.

Lifecycle-related services deserve additional protection because they can change whether important ROS 2 components are configured, active, inactive, or shut down. Unauthorized lifecycle transitions may disable perception, navigation, safety monitoring, or control functions without modifying ordinary application data. Access policies should therefore restrict lifecycle management to trusted orchestration or supervisory components and prevent unrelated nodes from manipulating critical component states.

Actions introduce a more complex authorization problem because ROS 2 actions use several underlying communication interactions to exchange goals, feedback, status, cancellation requests, and results. A policy must represent the complete communication behavior required by an authorized action client and server. Incomplete rules can break legitimate execution, while overly broad rules can expose cancellation or goal interfaces to participants that should only observe operational status.

Namespace design can support scalable access-control policy. Robot systems frequently organize resources according to subsystem, robot identifier, application, or operational role. Well-structured namespaces make it easier to express permissions for navigation, perception, manipulation, diagnostics, safety, or fleet functions. Poor naming conventions can force policies to depend on broad patterns, increasing the possibility that newly introduced resources unintentionally inherit excessive privileges.

Policy design should begin from an explicitly documented communication model rather than from unrestricted runtime discovery alone. Engineers should identify expected publishers, subscribers, service clients, service servers, action clients, and action servers for every protected component. The resulting graph can then be converted into authorization relationships. Observed runtime traffic remains useful for validation, but it should not automatically define what production software is permitted to access.

Default-deny behavior provides a strong foundation for production authorization. Communication should be permitted when a policy explicitly grants the required operation and rejected when no corresponding authorization exists. This approach differs from permissive configurations in which unknown communication is implicitly accepted. Default deny reduces accidental exposure when new nodes, topics, or services appear and forces architectural changes to pass through an intentional security review.

Wildcard rules should be used cautiously. Patterns can simplify management for large fleets or families of similarly named resources, but they may also grant access to future topics or services that did not exist when the policy was reviewed. A wildcard intended for diagnostic information, for example, could unintentionally include a later-added administrative interface. Policy reviews should therefore evaluate both currently matched resources and plausible future namespace expansion.

Different trust levels should be reflected in authorization boundaries. Safety controllers, autonomous planners, AI inference nodes, operator interfaces, fleet gateways, maintenance tools, and development utilities do not require identical privileges. Separating these roles limits the ability of a compromised lower-trust component to influence higher-criticality functions. This is particularly important when experimental AI software and deterministic safety or motion-control software operate within the same ROS 2 environment.

Multi-robot deployments require additional isolation. Nodes belonging to one robot should not automatically gain access to another robot\'s internal topics or control services merely because both systems share network infrastructure or a DDS environment. Robot-specific namespaces, identities, enclaves, and permissions can establish logical separation. Fleet-level components should receive cross-robot access only for the functions required for coordination, monitoring, mission assignment, or maintenance.

Access control must remain consistent with DDS Security permissions because ROS 2 communication is ultimately represented through middleware entities and resources. Application-level intentions need to map correctly to the DDS authorization model used by the selected ROS 2 middleware implementation. Differences between logical ROS 2 names and underlying communication resources must be considered during policy generation and testing to prevent either unintended denial or excessive authorization.

Policy changes should follow controlled configuration-management procedures. Adding a sensor, replacing a planner, introducing a new service, or changing namespaces may require authorization updates. Informal modifications can create configuration drift between software and security policy. Version-controlled policy artifacts, review workflows, automated validation, and deployment traceability allow teams to determine which permissions were active for a particular robot software release.

Testing should verify both positive and negative authorization behavior. Authorized publishers and subscribers must communicate successfully, while unauthorized attempts should be rejected. The same principle applies to service and action interfaces. Negative tests are especially valuable because an excessively permissive rule may not produce a visible functional failure. Security validation must deliberately attempt prohibited operations to demonstrate that policy boundaries are actually enforced.

Authorization failures should generate useful audit information. Repeated attempts to publish to restricted command topics, subscribe to protected sensor streams, invoke privileged services, or manipulate actions may indicate software defects, policy drift, or malicious activity. Audit records should identify the relevant participant and denied operation without exposing sensitive cryptographic material, allowing security monitoring systems to correlate middleware events with host and network telemetry.

Emergency and degraded-operation scenarios require deliberate policy design rather than unrestricted bypass mechanisms. Recovery controllers or safety supervisors may need exceptional permissions during faults, but those privileges should be assigned to predefined trusted identities. Creating a general security bypass for emergencies can become a persistent attack path. Exceptional authorization should remain narrow, auditable, testable, and compatible with the robot\'s defined safe-state behavior.

The chapter structure places topic and service access control after SROS2 certificate configuration and DDS authentication and encryption, followed by node identity, audit logging, key management, vulnerability remediation, penetration testing, and compliance mapping. This sequence reflects the dependency between trusted identity, protected communication, fine-grained authorization, and lifecycle security within the ROS 2 security architecture. Volume_24_Robot_Cybersecurity

Effective ROS 2 access-control policy transforms middleware connectivity into explicitly governed communication. Nodes are permitted to exchange only the information and commands required by their roles, while unauthorized interactions are rejected even when participants can reach the same network. Combined with strong identity, DDS cryptographic protection, auditing, configuration management, and continuous testing, least-privilege authorization limits compromise propagation and protects cyber-physical robot behavior.

ROS 2의 접근 제어(Access Control)는 인증된 참여자(Authenticated Participant)가 특정 통신 자원에 대해 발행(Publish), 구독(Subscribe), 요청(Request) 또는 제공(Provide)할 수 있는 권한을 정의한다. 인증(Authentication)은 신원을 확인할 뿐 운영 권한(Operational Authority)까지 부여하지 않는다. 따라서 안전한 로봇은 각 노드를 할당된 기능에 필요한 토픽(Topic), 서비스(Service), 액션(Action)으로 제한하는 명시적인 인가 정책(Authorization Policy)을 필요로 하며, 이를 통해 침해되거나 잘못 구성된 소프트웨어의 영향을 줄일 수 있다.

토픽 접근 제어(Topic Access Control)는 발행 권한(Publishing Right)과 구독 권한(Subscription Right)을 구분해야 한다. 두 권한은 보안 측면에서 근본적으로 다른 결과를 발생시키기 때문이다. 위치추정 노드(Localization Node)는 센서 관측값을 소비하면서 위치 추정값을 발행할 수 있고, 모터 제어 노드(Motor-Control Node)는 위치 데이터를 생성할 권한 없이 속도 명령을 구독할 수 있다. 이러한 권한 분리를 통해 인증된 참여자가 정상적인 네트워크 구성원이라는 이유만으로 자신의 책임 범위를 벗어난 통신 작업을 수행하는 것을 방지할 수 있다.

최소 권한 원칙(Principle of Least Privilege)은 정책 구성의 기본 원칙이 되어야 한다. 각 노드에는 정의된 작업을 수행하는 데 필요한 권한만 부여하고 불필요한 통신 경로는 허용하지 않아야 한다. 광범위한 와일드카드 권한(Wildcard Permission)은 초기 개발을 단순화할 수 있지만 운영 환경에서는 공격 표면(Attack Surface)을 크게 증가시킨다. 노드가 침해되더라도 세밀하게 제한된 권한을 적용하면 공격자가 관련 없는 ROS 2 자원에 즉시 데이터를 발행하거나 구독하는 것을 방지하여 횡적 이동(Lateral Movement)을 제한할 수 있다.

명령 토픽(Command Topic)은 비인가 발행이 물리적 동작에 직접 영향을 줄 수 있으므로 특히 엄격하게 통제해야 한다. 속도, 궤적, 액추에이터, 도킹, 조작, 비행 제어 및 비상 상태 메시지는 로봇 움직임을 즉시 변경할 수 있다. 정책은 이러한 정보의 발행 권한을 명시적으로 허가된 제어 구성요소로 제한하고, 정당한 필요성이 있는 구독자에게만 접근을 허용해야 한다. 가능한 경우 안전 필수 통신(Safety-Critical Communication)은 진단, 시각화 및 일반 애플리케이션 트래픽과 분리해야 한다.

센서 토픽(Sensor Topic)은 서로 다른 보안 특성을 가진다. 카메라 영상, 라이다(LiDAR) 포인트 클라우드, 레이더 관측값, 관절 상태(Joint State), 위치 정보 및 환경 지도는 여러 인식 및 계획 구성요소에서 사용해야 할 수 있다. 그러나 제한 없는 구독은 운영상 민감한 정보를 노출할 수 있으며, 비인가 발행은 조작된 센서 관측값을 주입할 수 있다. 따라서 정책은 센서 스트림의 기밀성(Confidentiality)과 자율 의사결정에 사용되는 데이터의 무결성(Integrity)을 모두 고려해야 한다.

서비스 접근 제어(Service Access Control)는 서비스가 지속적으로 상태를 배포하는 대신 개별적인 작업을 실행하는 경우가 많기 때문에 필수적이다. 서비스 요청(Service Request)은 하드웨어 초기화, 구성 변경, 지도 로딩, 내부 상태 삭제, 구성요소 활성화 또는 보정(Calibration)을 실행할 수 있다. 인증된 노드라고 해서 검색 가능한 모든 서비스를 자동으로 호출할 수 있어서는 안 된다. 대신 클라이언트(Client)와 서버(Server)의 권한은 로봇 아키텍처에서 정의된 정확한 운영 관계를 반영해야 한다.

수명주기 관련 서비스(Lifecycle-Related Service)는 중요한 ROS 2 구성요소를 구성됨(Configured), 활성(Active), 비활성(Inactive) 또는 종료(Shutdown) 상태로 변경할 수 있으므로 추가적인 보호가 필요하다. 비인가 수명주기 전환(Lifecycle Transition)은 일반적인 애플리케이션 데이터를 변경하지 않고도 인식, 내비게이션, 안전 모니터링 또는 제어 기능을 비활성화할 수 있다. 따라서 접근 정책은 수명주기 관리를 신뢰할 수 있는 오케스트레이션(Orchestration) 또는 감독 구성요소(Supervisory Component)로 제한하고 관련 없는 노드가 중요 구성요소의 상태를 조작하지 못하도록 해야 한다.

액션(Action)은 목표(Goal), 피드백(Feedback), 상태(Status), 취소 요청(Cancellation Request), 결과(Result)를 교환하기 위해 여러 하위 통신 상호작용을 사용하므로 더욱 복잡한 인가 문제가 발생한다. 정책은 허가된 액션 클라이언트(Action Client)와 액션 서버(Action Server)가 필요로 하는 전체 통신 동작을 표현해야 한다. 불완전한 규칙은 정상적인 실행을 방해할 수 있고, 지나치게 광범위한 규칙은 운영 상태만 관찰해야 하는 참여자에게 취소 또는 목표 인터페이스를 노출할 수 있다.

네임스페이스 설계(Namespace Design)는 확장 가능한 접근 제어 정책을 지원할 수 있다. 로봇 시스템은 흔히 하위 시스템, 로봇 식별자, 애플리케이션 또는 운영 역할을 기준으로 자원을 구성한다. 체계적인 네임스페이스는 내비게이션, 인식, 조작, 진단, 안전 또는 플릿 기능에 대한 권한을 표현하기 쉽게 만든다. 반대로 잘못된 명명 규칙(Naming Convention)은 정책이 광범위한 패턴에 의존하도록 만들어 새롭게 추가된 자원이 의도하지 않게 과도한 권한을 상속할 가능성을 높인다.

정책 설계(Policy Design)는 제한 없는 런타임 디스커버리(Runtime Discovery)만을 기반으로 하는 것이 아니라 명시적으로 문서화된 통신 모델(Communication Model)에서 시작해야 한다. 엔지니어는 보호되는 각 구성요소의 예상 발행자(Publisher), 구독자(Subscriber), 서비스 클라이언트(Service Client), 서비스 서버(Service Server), 액션 클라이언트 및 액션 서버를 식별해야 한다. 이후 이러한 그래프(Graph)를 인가 관계(Authorization Relationship)로 변환할 수 있다. 관찰된 런타임 트래픽은 검증에 유용하지만 운영 소프트웨어에 허용되는 접근 범위를 자동으로 정의해서는 안 된다.

기본 거부(Default-Deny) 동작은 운영 환경의 인가를 위한 강력한 기반을 제공한다. 정책에서 필요한 작업을 명시적으로 허용한 경우에만 통신을 허가하고, 해당 인가 규칙이 존재하지 않는 경우에는 통신을 거부해야 한다. 이는 알려지지 않은 통신을 암묵적으로 허용하는 허용적 구성(Permissive Configuration)과 다르다. 기본 거부 방식은 새로운 노드, 토픽 또는 서비스가 등장했을 때 발생할 수 있는 우발적인 노출을 줄이고 아키텍처 변경이 의도적인 보안 검토(Security Review)를 거치도록 한다.

와일드카드 규칙(Wildcard Rule)은 신중하게 사용해야 한다. 패턴 기반 규칙은 대규모 플릿이나 유사한 이름을 사용하는 자원군의 관리를 단순화할 수 있지만, 정책 검토 당시에는 존재하지 않았던 미래의 토픽이나 서비스에까지 접근 권한을 부여할 수 있다. 예를 들어 진단 정보를 대상으로 설정한 와일드카드가 이후 추가된 관리 인터페이스(Administrative Interface)까지 의도하지 않게 포함할 수 있다. 따라서 정책 검토에서는 현재 일치하는 자원뿐만 아니라 향후 네임스페이스 확장 가능성까지 평가해야 한다.

서로 다른 신뢰 수준(Trust Level)은 인가 경계(Authorization Boundary)에 반영해야 한다. 안전 제어기(Safety Controller), 자율 플래너(Autonomous Planner), AI 추론 노드(AI Inference Node), 운영자 인터페이스(Operator Interface), 플릿 게이트웨이(Fleet Gateway), 유지보수 도구 및 개발 유틸리티는 동일한 권한을 필요로 하지 않는다. 이러한 역할을 분리하면 낮은 신뢰 수준의 구성요소가 침해되었을 때 높은 중요도의 기능에 영향을 줄 가능성을 제한할 수 있다. 이는 실험적인 AI 소프트웨어와 결정론적 안전 또는 모션 제어 소프트웨어가 동일한 ROS 2 환경에서 동작할 때 특히 중요하다.

다중 로봇 배포(Multi-Robot Deployment)에서는 추가적인 격리(Isolation)가 필요하다. 두 시스템이 동일한 네트워크 인프라 또는 DDS 환경을 공유한다는 이유만으로 한 로봇에 속한 노드가 다른 로봇의 내부 토픽이나 제어 서비스에 자동으로 접근해서는 안 된다. 로봇별 네임스페이스, 신원(Identity), 엔클레이브(Enclave), 권한(Permission)을 사용하여 논리적 분리를 구성할 수 있다. 플릿 수준 구성요소에는 조정, 모니터링, 임무 할당 또는 유지보수에 필요한 기능에 한해서만 로봇 간 접근 권한을 부여해야 한다.

ROS 2 통신은 궁극적으로 미들웨어 엔티티(Middleware Entity)와 자원을 통해 표현되므로 접근 제어는 DDS 보안 권한(DDS Security Permission)과 일관성을 유지해야 한다. 애플리케이션 수준에서 정의한 통신 의도는 선택된 ROS 2 미들웨어 구현체가 사용하는 DDS 인가 모델(Authorization Model)에 정확하게 매핑되어야 한다. 논리적인 ROS 2 이름과 하위 통신 자원의 차이를 정책 생성 및 테스트 과정에서 고려하여 의도하지 않은 접근 거부 또는 과도한 인가를 방지해야 한다.

정책 변경(Policy Change)은 통제된 구성 관리(Configuration Management) 절차를 따라야 한다. 센서 추가, 플래너 교체, 새로운 서비스 도입 또는 네임스페이스 변경에는 인가 정책 업데이트가 필요할 수 있다. 비공식적인 변경은 소프트웨어와 보안 정책 사이의 구성 드리프트(Configuration Drift)를 발생시킬 수 있다. 버전 관리되는 정책 산출물, 검토 워크플로(Review Workflow), 자동화된 검증(Automated Validation), 배포 추적성(Deployment Traceability)을 적용하면 특정 로봇 소프트웨어 릴리스에서 어떤 권한이 활성화되어 있었는지 확인할 수 있다.

테스트(Testing)는 긍정적 인가 동작(Positive Authorization Behavior)과 부정적 인가 동작(Negative Authorization Behavior)을 모두 검증해야 한다. 허가된 발행자와 구독자는 정상적으로 통신할 수 있어야 하며, 비인가 통신 시도는 거부되어야 한다. 동일한 원칙을 서비스 및 액션 인터페이스에도 적용해야 한다. 지나치게 허용적인 규칙은 명확한 기능 장애를 발생시키지 않을 수 있으므로 부정 테스트가 특히 중요하다. 보안 검증은 금지된 작업을 의도적으로 시도하여 정책 경계가 실제로 집행되고 있음을 입증해야 한다.

인가 실패(Authorization Failure)는 유용한 감사 정보(Audit Information)를 생성해야 한다. 제한된 명령 토픽에 데이터를 발행하거나, 보호된 센서 스트림을 구독하거나, 권한이 필요한 서비스를 호출하거나, 액션을 조작하려는 반복적인 시도는 소프트웨어 결함, 정책 드리프트(Policy Drift) 또는 악의적인 활동을 의미할 수 있다. 감사 기록(Audit Record)은 민감한 암호학적 자료를 노출하지 않으면서 관련 참여자와 거부된 작업을 식별하여 보안 모니터링 시스템이 미들웨어 이벤트를 호스트 및 네트워크 텔레메트리와 연계할 수 있도록 해야 한다.

비상 및 성능 저하 운용 시나리오(Emergency and Degraded-Operation Scenario)는 제한 없는 우회 메커니즘이 아니라 의도적인 정책 설계를 필요로 한다. 복구 제어기(Recovery Controller) 또는 안전 감독기(Safety Supervisor)는 장애 상황에서 예외적인 권한을 필요로 할 수 있지만, 이러한 권한은 사전에 정의된 신뢰할 수 있는 신원에 할당해야 한다. 비상 상황을 이유로 일반적인 보안 우회(Security Bypass)를 만들면 지속적인 공격 경로가 될 수 있다. 예외적 인가는 제한적이고 감사 가능하며 테스트 가능해야 하고 로봇의 정의된 안전 상태(Safe-State) 동작과 호환되어야 한다.

전체 구조에서는 SROS2 인증서 구성(Certificate Configuration)과 DDS 인증 및 암호화(Authentication and Encryption) 이후 토픽 및 서비스 접근 제어를 배치하고, 이어서 노드 신원(Node Identity), 감사 로깅(Audit Logging), 키 관리(Key Management), 취약점 개선(Vulnerability Remediation), 침투 테스트(Penetration Testing), 규정 준수 매핑(Compliance Mapping)으로 확장한다. 이러한 순서는 ROS 2 보안 아키텍처에서 신뢰할 수 있는 신원, 보호된 통신, 세분화된 인가(Fine-Grained Authorization), 수명주기 보안(Lifecycle Security) 사이의 의존 관계를 반영한다.

효과적인 ROS 2 접근 제어 정책(Access-Control Policy)은 단순한 미들웨어 연결성을 명시적으로 통제되는 통신 구조로 전환한다. 노드는 자신의 역할에 필요한 정보와 명령만 교환하도록 허용되며, 참여자들이 동일한 네트워크에 접근할 수 있더라도 비인가 상호작용은 거부된다. 강력한 신원 관리, DDS 암호학적 보호(Cryptographic Protection), 감사, 구성 관리 및 지속적인 테스트와 최소 권한 기반 인가를 결합하면 침해 확산을 제한하고 사이버-물리 로봇 동작(Cyber-Physical Robot Behavior)을 보호할 수 있다.

##  

## 04.05. ROS2 Node Identity and Mutual Auth mTLS [w/Code]

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Node identity is a fundamental security property in ROS 2 because distributed components must know which participants can be trusted before exchanging operational data or commands. A node name alone is not a secure identity because names can be reproduced by unauthorized software. Secure identity therefore requires cryptographic credentials that bind a participant to an independently verifiable trust relationship rather than relying only on logical ROS 2 naming.

ROS 2 security builds this identity model on the capabilities provided by DDS Security and SROS2. Certificates, private keys, trust anchors, enclaves, and permission artifacts collectively establish the security context in which a participant operates. The chapter structure places node identity after certificate configuration, DDS authentication and encryption, and topic/service access control, reflecting the relationship between identity establishment and authorization enforcement. Volume_24_Robot_Cybersecurity

A cryptographic node identity should correspond to a meaningful software or operational role. Navigation, perception, manipulation, safety supervision, hardware control, fleet communication, and maintenance components should not automatically share one generic credential. Distinct identities allow security policies to associate permissions with specific responsibilities and make it possible to isolate, revoke, or investigate one participant without treating the entire robot as a single security principal.

Public key infrastructure provides a practical foundation for establishing these identities. A trusted certificate authority issues or signs certificates representing approved participants, while each participant retains the corresponding private key. During authentication, possession of the private key demonstrates that the participant controls the credential associated with its certificate. Trust in the certificate authority then allows other participants to evaluate whether that identity belongs to an accepted security domain.

Identity verification must include more than checking whether a certificate exists. The certificate chain, issuing authority, validity period, expected identity information, cryptographic signature, and relevant security configuration must be validated before trust is established. Expired, malformed, untrusted, or otherwise invalid credentials should cause authentication to fail. A secure deployment must avoid fallback behavior that silently permits unsecured communication when identity verification cannot be completed.

Mutual authentication extends this principle by requiring both communication participants to authenticate each other. In a one-sided trust model, one endpoint may prove its identity while accepting the other without equivalent verification. Mutual authentication prevents this imbalance. A control component verifies the identity of the participant supplying information, while the supplying participant verifies that it is communicating with an authorized and trusted consumer or controller.

The term mutual TLS, or mTLS, describes the broader security pattern in which both sides of a connection present and validate cryptographic identities. ROS 2 communication over DDS does not simply become conventional application-level TLS between every pair of nodes; DDS Security provides its own participant authentication and cryptographic mechanisms. Nevertheless, the mTLS concept is useful for expressing the requirement that trust should be bidirectional rather than based on unilateral endpoint authentication.

This distinction is important when designing heterogeneous robot architectures. ROS 2 and DDS traffic may coexist with HTTPS, gRPC, cloud APIs, fleet gateways, telemetry services, or management interfaces that actually use TLS or mTLS. The same identity architecture can apply consistent trust principles across these boundaries while allowing each protocol to use its appropriate security mechanism. Identity should therefore be designed at the system level rather than independently for each communication technology.

Mutual authentication reduces the risk of participant impersonation. Without cryptographic verification, malicious software could adopt the name of a trusted planner, sensor interface, diagnostic node, or controller and attempt to participate in normal communication. A trusted name is insufficient because software-controlled identifiers can be copied. Authentication binds trust to possession of protected cryptographic material, making simple name duplication inadequate for establishing a legitimate security identity.

Authentication also supports stronger authorization because access-control decisions require a trustworthy principal. A policy that states which node may publish a command topic has little security value if an attacker can freely claim that node\'s identity. Once cryptographic authentication establishes the participant, permissions can reliably determine which topics, services, actions, domains, or other middleware resources that participant is authorized to use.

Identity granularity should match the required containment boundary. Assigning one credential to an entire robot may simplify provisioning, but compromise of that credential can expose every privilege associated with the machine. More granular identities for critical components can reduce this blast radius. However, excessive fragmentation increases certificate, key, and policy management complexity, so identity boundaries should reflect meaningful differences in privilege, criticality, and trust.

Containers and multi-process systems require particular attention because logical ROS 2 nodes may share the same host or execution environment. Host-level trust should not automatically imply that every process deserves identical middleware privileges. Enclaves and appropriately scoped credentials can separate security responsibilities even when components execute on the same computer. This becomes important when safety-critical software operates beside AI, visualization, development, or third-party components.

Private-key protection determines the practical strength of cryptographic identity. If malware or an unauthorized administrator can copy a participant\'s private key, the attacker may impersonate that participant even though the authentication protocol itself remains cryptographically sound. File permissions, restricted privilege, encrypted storage, secure provisioning, hardware-backed key storage, and controlled backup procedures should therefore be considered part of node identity protection.

Identity provisioning must be controlled from development through production. Credentials should not be manually copied between robots without traceability, nor should development identities be reused across production fleets for convenience. Provisioning processes should establish which device or software component received each identity, when it was issued, which trust domain signed it, and which permissions were associated with it. Automation can reduce human error when fleet scale increases.

Certificate validity periods introduce an operational dependency between security and availability. Shorter validity periods reduce the useful lifetime of stolen credentials but require reliable renewal mechanisms. Longer periods reduce maintenance frequency but increase exposure if credentials are compromised. Renewal should occur before expiration and should be tested under realistic robot operating conditions so that identity maintenance does not unexpectedly interrupt discovery, control, or fleet connectivity.

Revocation and credential replacement are necessary when a robot is lost, a computer is replaced, a private key is exposed, or a software environment becomes untrusted. Unique identities make targeted response possible because administrators can remove trust from one participant without invalidating unrelated systems. Shared credentials make incident containment significantly more disruptive and can force large portions of a fleet to undergo simultaneous credential replacement.

Multi-robot systems should prevent identity collisions and unintended cross-robot trust. A participant belonging to one robot should not gain access to another robot merely because both use similar node names or software packages. Robot-specific identities, namespaces, enclaves, and authorization rules can maintain separation, while fleet services can be granted explicitly defined cross-robot privileges for monitoring, mission coordination, maintenance, or orchestration.

Authentication events should be observable through security logging. Repeated failed handshakes, unknown certificate authorities, expired credentials, identity mismatches, unexpected participants, and unusual authentication attempts may indicate configuration problems or active reconnaissance. Logs should preserve enough information for investigation while avoiding exposure of private keys, session secrets, or unnecessary sensitive certificate data.

Testing should verify successful mutual authentication as well as deliberate failure cases. Trusted participants should establish protected communication, while participants using untrusted, expired, altered, or incorrectly assigned credentials should be rejected. Tests should also examine certificate renewal, participant restart, network interruption, credential replacement, and recovery so that authentication remains reliable throughout the operational lifecycle rather than only during initial deployment.

Node identity ultimately provides the trusted principal on which the rest of ROS 2 authorization depends. Certificates and protected private keys establish cryptographic identity, mutual authentication verifies trust in both directions, and access policies convert that identity into controlled communication privileges. Combined with secure provisioning, renewal, revocation, logging, and negative testing, this approach limits impersonation and creates stronger trust boundaries for distributed cyber-physical robot software.

노드 신원(Node Identity)은 분산된 구성요소가 운영 데이터나 명령을 교환하기 전에 어떤 참여자(Participant)를 신뢰할 수 있는지 확인해야 하므로 ROS 2에서 기본적인 보안 속성(Security Property)이다. 노드 이름(Node Name)은 비인가 소프트웨어가 동일한 이름을 재사용할 수 있기 때문에 그 자체로 안전한 신원이 될 수 없다. 따라서 안전한 신원은 논리적인 ROS 2 이름에만 의존하지 않고 참여자를 독립적으로 검증 가능한 신뢰 관계(Trust Relationship)에 연결하는 암호학적 자격증명(Cryptographic Credential)을 필요로 한다.

ROS 2 보안(Security)은 DDS 보안(DDS Security)과 SROS2가 제공하는 기능을 기반으로 이러한 신원 모델(Identity Model)을 구축한다. 인증서(Certificate), 개인 키(Private Key), 신뢰 앵커(Trust Anchor), 엔클레이브(Enclave), 권한 산출물(Permission Artifact)은 참여자가 동작하는 보안 컨텍스트(Security Context)를 종합적으로 구성한다. 전체 구조에서는 인증서 구성, DDS 인증 및 암호화, 토픽 및 서비스 접근 제어 이후 노드 신원을 배치하며, 이는 신원 확립(Identity Establishment)과 인가 집행(Authorization Enforcement) 사이의 관계를 반영한다.

암호학적 노드 신원(Cryptographic Node Identity)은 의미 있는 소프트웨어 또는 운영 역할과 대응해야 한다. 내비게이션(Navigation), 인식(Perception), 조작(Manipulation), 안전 감독(Safety Supervision), 하드웨어 제어(Hardware Control), 플릿 통신(Fleet Communication), 유지보수 구성요소가 하나의 일반적인 자격증명을 자동으로 공유해서는 안 된다. 서로 다른 신원을 사용하면 보안 정책을 특정 책임과 연결할 수 있으며, 로봇 전체를 하나의 보안 주체(Security Principal)로 취급하지 않고 개별 참여자를 격리, 폐기 또는 조사할 수 있다.

공개 키 기반구조(Public Key Infrastructure, PKI)는 이러한 신원을 설정하기 위한 실용적인 기반을 제공한다. 신뢰할 수 있는 인증 기관(Certificate Authority, CA)은 승인된 참여자를 나타내는 인증서를 발급하거나 서명하고, 각 참여자는 해당 인증서에 대응하는 개인 키를 보유한다. 인증 과정에서 개인 키의 소유를 증명함으로써 참여자가 인증서와 연결된 자격증명을 실제로 통제하고 있음을 입증한다. 이후 인증 기관에 대한 신뢰를 통해 다른 참여자는 해당 신원이 허용된 보안 도메인(Security Domain)에 속하는지를 판단할 수 있다.

신원 검증(Identity Verification)은 단순히 인증서의 존재 여부를 확인하는 것 이상을 포함해야 한다. 신뢰를 설정하기 전에 인증서 체인(Certificate Chain), 발급 기관(Issuing Authority), 유효기간, 예상된 신원 정보, 암호학적 서명(Cryptographic Signature), 관련 보안 구성을 검증해야 한다. 만료되었거나 잘못 구성되었거나 신뢰할 수 없거나 기타 이유로 유효하지 않은 자격증명은 인증 실패로 처리해야 한다. 안전한 배포 환경에서는 신원 검증을 완료할 수 없을 때 비보안 통신을 자동으로 허용하는 폴백 동작(Fallback Behavior)을 방지해야 한다.

상호 인증(Mutual Authentication)은 양쪽 통신 참여자가 서로를 인증하도록 요구함으로써 이러한 원칙을 확장한다. 단방향 신뢰 모델(One-Sided Trust Model)에서는 하나의 엔드포인트(Endpoint)가 자신의 신원을 증명하는 반면 상대방은 동등한 검증 없이 허용될 수 있다. 상호 인증은 이러한 불균형을 방지한다. 제어 구성요소는 정보를 제공하는 참여자의 신원을 확인하고, 정보를 제공하는 참여자 역시 자신이 허가되고 신뢰할 수 있는 소비자 또는 제어기와 통신하고 있는지를 확인한다.

상호 TLS(Mutual TLS, mTLS)라는 용어는 연결 양쪽이 암호학적 신원을 제시하고 검증하는 광범위한 보안 패턴(Security Pattern)을 의미한다. DDS를 사용하는 ROS 2 통신이 모든 노드 쌍 사이에서 일반적인 애플리케이션 수준 TLS로 단순히 전환되는 것은 아니며, DDS 보안은 자체적인 참여자 인증 및 암호학적 메커니즘을 제공한다. 그럼에도 mTLS 개념은 신뢰가 단방향 엔드포인트 인증에 의존하는 것이 아니라 양방향으로 설정되어야 한다는 요구사항을 표현하는 데 유용하다.

이러한 차이는 이기종 로봇 아키텍처(Heterogeneous Robot Architecture)를 설계할 때 중요하다. ROS 2 및 DDS 트래픽은 HTTPS, gRPC, 클라우드 API(Cloud API), 플릿 게이트웨이(Fleet Gateway), 텔레메트리 서비스(Telemetry Service), 관리 인터페이스(Management Interface)와 함께 존재할 수 있으며, 이러한 인터페이스는 실제 TLS 또는 mTLS를 사용할 수 있다. 동일한 신원 아키텍처는 각 프로토콜이 적절한 보안 메커니즘을 사용하도록 하면서 이러한 경계 전체에 일관된 신뢰 원칙을 적용할 수 있다. 따라서 신원은 각각의 통신 기술별로 독립적으로 설계하기보다 시스템 수준에서 설계해야 한다.

상호 인증은 참여자 사칭(Participant Impersonation)의 위험을 줄인다. 암호학적 검증이 없다면 악성 소프트웨어가 신뢰받는 플래너(Planner), 센서 인터페이스(Sensor Interface), 진단 노드(Diagnostic Node) 또는 제어기(Controller)의 이름을 사용하여 정상적인 통신에 참여하려고 시도할 수 있다. 소프트웨어로 제어되는 식별자는 복제할 수 있으므로 신뢰받는 이름만으로는 충분하지 않다. 인증은 보호된 암호학적 자료의 소유 여부와 신뢰를 연결하여 단순한 이름 복제만으로는 정상적인 보안 신원을 확립할 수 없도록 한다.

인증(Authentication)은 접근 제어 결정에 신뢰할 수 있는 보안 주체가 필요하기 때문에 더욱 강력한 인가(Authorization)를 지원한다. 특정 노드가 명령 토픽(Command Topic)을 발행할 수 있다고 정의하는 정책도 공격자가 해당 노드의 신원을 자유롭게 주장할 수 있다면 보안 가치가 거의 없다. 암호학적 인증을 통해 참여자의 신원이 확립되면 권한(Permission)을 사용하여 해당 참여자가 사용할 수 있는 토픽(Topic), 서비스(Service), 액션(Action), 도메인(Domain) 또는 기타 미들웨어 자원을 신뢰성 있게 결정할 수 있다.

신원 세분성(Identity Granularity)은 요구되는 격리 경계(Containment Boundary)에 맞추어야 한다. 하나의 로봇 전체에 하나의 자격증명을 할당하면 프로비저닝(Provisioning)은 단순해지지만 해당 자격증명이 침해될 경우 시스템과 연결된 모든 권한이 노출될 수 있다. 중요 구성요소에 더욱 세분화된 신원을 적용하면 이러한 피해 범위(Blast Radius)를 줄일 수 있다. 그러나 지나친 세분화는 인증서, 키 및 정책 관리의 복잡성을 증가시키므로 신원 경계는 권한, 중요도 및 신뢰 수준의 의미 있는 차이를 반영해야 한다.

컨테이너(Container)와 다중 프로세스 시스템(Multi-Process System)은 논리적인 ROS 2 노드들이 동일한 호스트 또는 실행 환경을 공유할 수 있기 때문에 특별한 주의가 필요하다. 호스트 수준의 신뢰가 모든 프로세스에 동일한 미들웨어 권한을 자동으로 부여한다는 의미가 되어서는 안 된다. 엔클레이브와 적절하게 제한된 자격증명을 사용하면 구성요소가 동일한 컴퓨터에서 실행되는 경우에도 보안 책임을 분리할 수 있다. 이는 안전 필수 소프트웨어(Safety-Critical Software)가 AI, 시각화, 개발 또는 서드파티 구성요소와 함께 실행되는 경우 특히 중요하다.

개인 키 보호(Private-Key Protection)는 암호학적 신원의 실질적인 강도를 결정한다. 악성코드 또는 비인가 관리자가 참여자의 개인 키를 복사할 수 있다면 인증 프로토콜 자체가 암호학적으로 안전하더라도 공격자는 해당 참여자를 사칭할 수 있다. 따라서 파일 권한(File Permission), 제한된 권한(Restricted Privilege), 암호화 저장소(Encrypted Storage), 안전한 프로비저닝(Secure Provisioning), 하드웨어 기반 키 저장소(Hardware-Backed Key Storage), 통제된 백업 절차를 노드 신원 보호의 일부로 고려해야 한다.

신원 프로비저닝(Identity Provisioning)은 개발 단계에서 운영 단계까지 통제되어야 한다. 자격증명을 추적성 없이 로봇 사이에서 수동으로 복사해서는 안 되며, 편의성을 이유로 개발용 신원을 운영 플릿(Production Fleet) 전체에서 재사용해서도 안 된다. 프로비저닝 프로세스는 어떤 장치 또는 소프트웨어 구성요소가 각각의 신원을 부여받았는지, 언제 발급되었는지, 어떤 신뢰 도메인이 서명했는지, 어떤 권한이 연결되었는지를 명확하게 설정해야 한다. 플릿 규모가 증가하면 자동화를 통해 사람의 실수를 줄일 수 있다.

인증서 유효기간(Certificate Validity Period)은 보안과 가용성(Availability) 사이에 운영상의 의존 관계를 만든다. 짧은 유효기간은 탈취된 자격증명을 사용할 수 있는 기간을 줄이지만 신뢰할 수 있는 갱신 메커니즘(Renewal Mechanism)을 요구한다. 긴 유효기간은 유지보수 빈도를 줄이는 대신 자격증명이 침해되었을 때 노출 기간을 증가시킨다. 갱신은 만료 전에 이루어져야 하며, 신원 유지보수로 인해 디스커버리, 제어 또는 플릿 연결이 예기치 않게 중단되지 않도록 실제 로봇 운용 조건에서 테스트해야 한다.

로봇이 분실되거나 컴퓨터가 교체되거나 개인 키가 노출되거나 소프트웨어 환경을 더 이상 신뢰할 수 없게 된 경우에는 폐기(Revocation)와 자격증명 교체(Credential Replacement)가 필요하다. 고유한 신원을 사용하면 관련 없는 시스템의 신뢰를 무효화하지 않고 하나의 참여자에 대한 신뢰만 제거할 수 있으므로 표적화된 대응(Targeted Response)이 가능하다. 반대로 공유 자격증명은 사고 격리(Incident Containment)를 훨씬 어렵게 만들고 플릿의 많은 부분에서 동시에 자격증명을 교체하도록 만들 수 있다.

다중 로봇 시스템(Multi-Robot System)은 신원 충돌(Identity Collision)과 의도하지 않은 로봇 간 신뢰(Cross-Robot Trust)를 방지해야 한다. 하나의 로봇에 속한 참여자가 유사한 노드 이름이나 소프트웨어 패키지를 사용한다는 이유만으로 다른 로봇에 접근할 수 있어서는 안 된다. 로봇별 신원, 네임스페이스(Namespace), 엔클레이브, 인가 규칙(Authorization Rule)을 사용하여 분리를 유지할 수 있으며, 플릿 서비스에는 모니터링, 임무 조정, 유지보수 또는 오케스트레이션에 필요한 명확하게 정의된 로봇 간 권한만 부여할 수 있다.

인증 이벤트(Authentication Event)는 보안 로깅(Security Logging)을 통해 관찰할 수 있어야 한다. 반복적인 핸드셰이크 실패(Handshake Failure), 알려지지 않은 인증 기관, 만료된 자격증명, 신원 불일치, 예상하지 못한 참여자 및 비정상적인 인증 시도는 구성 문제 또는 적극적인 정찰(Reconnaissance)을 나타낼 수 있다. 로그는 조사에 필요한 충분한 정보를 보존하면서 개인 키, 세션 비밀정보(Session Secret) 또는 불필요하게 민감한 인증서 데이터가 노출되지 않도록 해야 한다.

테스트(Testing)는 정상적인 상호 인증의 성공뿐만 아니라 의도적인 실패 상황도 검증해야 한다. 신뢰할 수 있는 참여자는 보호된 통신을 설정할 수 있어야 하며, 신뢰할 수 없거나 만료되었거나 변조되었거나 잘못 할당된 자격증명을 사용하는 참여자는 거부되어야 한다. 또한 인증서 갱신, 참여자 재시작, 네트워크 중단, 자격증명 교체 및 복구를 테스트하여 인증이 초기 배포 시점뿐만 아니라 전체 운영 수명주기(Operational Lifecycle) 동안 안정적으로 유지되는지 확인해야 한다.

노드 신원은 궁극적으로 ROS 2의 나머지 인가 체계가 의존하는 신뢰할 수 있는 보안 주체(Trusted Principal)를 제공한다. 인증서와 보호된 개인 키는 암호학적 신원을 확립하고, 상호 인증은 양방향으로 신뢰를 검증하며, 접근 정책(Access Policy)은 이러한 신원을 통제된 통신 권한으로 변환한다. 안전한 프로비저닝, 갱신, 폐기, 로깅 및 부정 테스트(Negative Testing)를 결합하면 사칭 위험을 제한하고 분산 사이버-물리 로봇 소프트웨어(Distributed Cyber-Physical Robot Software)를 위한 더욱 강력한 신뢰 경계(Trust Boundary)를 구축할 수 있다.

##  

## 04.06. ROS2 Audit Log Collection and Analysis [w/Code]

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

Audit logging provides the evidence needed to understand security-relevant activity across a distributed ROS 2 system. Authentication, authorization, DDS communication, node execution, operating-system events, and network behavior can each reveal different parts of an incident. A useful audit architecture therefore collects events from multiple layers and preserves enough context to reconstruct who performed an operation, what resource was affected, when it occurred, and whether it succeeded.

ROS 2 audit collection should begin with events associated with participant identity and authentication. Successful and failed authentication attempts, rejected certificates, unknown trust anchors, expired credentials, enclave mismatches, and unexpected participants can indicate configuration problems or hostile activity. Recording these events allows operators to distinguish normal discovery failures from attempts by unauthorized software to enter the protected DDS communication environment.

Authorization events provide another critical source of evidence. Attempts to publish to restricted topics, subscribe to protected data, invoke privileged services, or interact with unauthorized actions should be recorded when the middleware exposes the necessary information. Repeated denials can reveal compromised nodes, incorrectly deployed policies, or reconnaissance activity in which an attacker probes the ROS 2 graph to identify accessible communication resources.

Audit records should preserve participant identity rather than relying only on node names or IP addresses. Node names can be duplicated, while network addresses may change because of DHCP, containers, mobile robots, or dynamic infrastructure. Where possible, events should be correlated with cryptographic identity, security enclave, host identity, process information, robot identifier, and relevant ROS 2 resource names to create a stronger attribution chain for later investigation.

Time synchronization is essential because distributed robotic systems generate events across many processors and network devices. Without consistent timestamps, investigators may be unable to determine whether an authentication failure preceded a command anomaly or whether a network event occurred before a node restarted. Hosts, edge computers, gateways, and monitoring infrastructure should therefore maintain sufficiently accurate time synchronization and preserve timestamp provenance when logs are aggregated.

Application logs remain important even when middleware security logging is enabled. A ROS 2 node may authenticate correctly and possess legitimate permissions while still behaving abnormally because of compromise, software defects, or malicious input. Logs describing lifecycle transitions, configuration changes, command acceptance, safety-state changes, unexpected restarts, and application errors can reveal misuse that authentication and access-control records alone cannot identify.

DDS and middleware events should be correlated with host-level telemetry. Process creation, service startup, privilege changes, file access, certificate modifications, container events, system authentication, and resource exhaustion may explain why ROS 2 behavior changed. A participant that suddenly begins producing unauthorized requests, for example, may correspond to a newly launched process or altered executable on the host rather than an external DDS participant.

Network monitoring adds another layer of visibility. Connection patterns, multicast behavior, discovery traffic, bandwidth anomalies, packet loss, interface changes, firewall events, and communication with unexpected addresses can provide context for ROS 2 incidents. Encrypted DDS traffic limits payload inspection by design, so metadata and endpoint behavior become increasingly important for detecting scanning, denial-of-service activity, abnormal discovery, or unexpected communication paths.

Centralized log collection is valuable in robot fleets because local logs may be unavailable after a device failure, compromise, theft, or storage corruption. Robots can forward selected security events to an edge collector, fleet server, or security information and event management platform. Centralization also allows events from multiple robots to be compared, making coordinated attacks or repeated authentication failures across the fleet easier to identify than through isolated device inspection.

Collection architecture must account for intermittent connectivity. Mobile robots, outdoor systems, and remote platforms may temporarily lose access to central infrastructure. Local buffering can preserve important events until connectivity returns, but storage capacity and retention limits must be controlled. Priority should be given to security-critical records so that high-volume diagnostic or sensor logging does not overwrite authentication, authorization, configuration, or incident evidence.

Log integrity is as important as log availability. An attacker who compromises a robot may attempt to delete or modify records that reveal the intrusion. Append-oriented storage, cryptographic integrity checks, restricted write permissions, remote forwarding, and protected retention can make evidence manipulation more difficult. Audit systems should also detect unexplained logging gaps because sudden silence from an active robot can itself represent a security-relevant event.

Sensitive information must not be exposed through audit collection. Private keys, passwords, session secrets, complete authentication tokens, or unnecessary confidential payloads should never be written to ordinary logs. Certificates and identifiers may also require careful handling depending on operational policy. Logging should capture enough information for attribution and analysis while applying minimization principles so that the monitoring system does not become a new repository of high-value secrets.

Event normalization improves analysis when different ROS 2 middleware implementations, operating systems, containers, and security components produce incompatible log formats. Common fields such as timestamp, robot identifier, host, participant identity, node, enclave, event category, affected resource, result, severity, and correlation identifier allow centralized tools to process heterogeneous records. Normalization also simplifies searches across fleets and supports reusable detection rules.

Correlation converts individual records into security information. One denied topic publication may result from a configuration mistake, while hundreds of denied publications followed by a lifecycle transition and abnormal network traffic may indicate compromise. Analysis should combine authentication failures, authorization denials, node restarts, certificate changes, network anomalies, and safety events within meaningful time windows to identify patterns that would remain invisible in isolated logs.

Baseline behavior can support anomaly detection because production robots often exhibit relatively predictable communication relationships. Operators can characterize normal participants, topic interactions, service usage, authentication frequency, restart patterns, and network destinations. Deviations from this baseline do not automatically prove an attack, but they can prioritize investigation when a new participant appears, a node begins accessing unusual resources, or communication volume changes unexpectedly.

Alerting should reflect operational and physical consequences rather than treating every security event equally. A failed attempt to publish an actuator command is generally more significant than an isolated denial involving a low-risk diagnostic topic. Detection logic should consider resource criticality, participant identity, repetition rate, robot operating state, and correlated events. This reduces alert fatigue while emphasizing behavior capable of affecting safety, mission execution, or fleet availability.

Audit retention requirements should reflect incident-response and compliance needs. Some events may need to remain available long enough to investigate attacks discovered weeks after they occurred, while continuous debugging logs may require much shorter retention. Storage policies should distinguish security audit evidence from ordinary operational telemetry and define retention duration, archival protection, access privileges, deletion procedures, and evidence-preservation requirements.

Access to the audit system itself requires strict control. Logs may reveal robot architecture, software identities, operational schedules, network relationships, and security failures. Only authorized personnel and services should be able to search, export, modify, or delete security records. Administrative actions performed within the logging platform should also be audited so that investigators can determine who accessed evidence or changed monitoring and retention configurations.

Incident response depends on the ability to preserve relevant evidence. When suspicious behavior is detected, selected logs should be protected from normal rotation or deletion and associated with an incident timeline. Authentication records, authorization failures, host events, network observations, configuration history, and software versions can then be analyzed together. Preserving provenance and timestamps supports root-cause analysis and helps distinguish the initial intrusion from subsequent effects.

Audit functionality should be tested just like authentication and access control. Security teams should deliberately generate failed authentication attempts, denied topic access, unauthorized service requests, certificate problems, node restarts, and other representative events, then verify that the expected records reach the collection system. Testing should also examine buffering, forwarding failure, clock errors, storage exhaustion, log rotation, and recovery after temporary network loss.

Within the chapter structure, audit collection follows certificate configuration, DDS authentication and encryption, access-control policy, and node identity, while preceding cryptographic key management, vulnerability remediation, penetration testing, and compliance mapping. This position reflects its role as the observability layer that verifies and records the behavior of previously established ROS 2 security controls. Volume_24_Robot_Cybersecurity

Effective ROS 2 audit analysis transforms distributed security events into evidence about the cyber-physical system as a whole. By correlating identity, authorization, middleware, host, network, and application information, operators can detect abnormal behavior, investigate incidents, validate policy enforcement, and support recovery. Protected timestamps, centralized collection, integrity controls, appropriate retention, and tested detection logic make logging an active security capability rather than a passive debugging mechanism.

감사 로깅(Audit Logging)은 분산 ROS 2 시스템 전반에서 보안 관련 활동(Security-Relevant Activity)을 이해하는 데 필요한 증거를 제공한다. 인증(Authentication), 인가(Authorization), DDS 통신, 노드 실행(Node Execution), 운영체제 이벤트(Operating-System Event), 네트워크 동작은 각각 사고의 서로 다른 부분을 보여줄 수 있다. 따라서 효과적인 감사 아키텍처(Audit Architecture)는 여러 계층에서 이벤트를 수집하고 누가 어떤 작업을 수행했는지, 어떤 자원이 영향을 받았는지, 언제 발생했는지, 성공 여부가 무엇인지 재구성할 수 있는 충분한 컨텍스트를 보존해야 한다.

ROS 2 감사 수집(Audit Collection)은 참여자 신원(Participant Identity) 및 인증과 관련된 이벤트에서 시작해야 한다. 성공 및 실패한 인증 시도, 거부된 인증서, 알려지지 않은 신뢰 앵커(Trust Anchor), 만료된 자격증명(Credential), 엔클레이브 불일치(Enclave Mismatch), 예상하지 못한 참여자는 구성 문제 또는 적대적 활동을 나타낼 수 있다. 이러한 이벤트를 기록하면 운영자는 일반적인 디스커버리 실패(Discovery Failure)와 비인가 소프트웨어가 보호된 DDS 통신 환경에 진입하려는 시도를 구분할 수 있다.

인가 이벤트(Authorization Event)는 또 다른 중요한 증거 자료를 제공한다. 제한된 토픽(Topic)에 데이터를 발행하거나, 보호된 데이터를 구독하거나, 권한이 필요한 서비스(Service)를 호출하거나, 허가되지 않은 액션(Action)과 상호작용하려는 시도는 미들웨어가 필요한 정보를 제공하는 경우 기록해야 한다. 반복적인 거부는 침해된 노드, 잘못 배포된 정책 또는 공격자가 접근 가능한 통신 자원을 식별하기 위해 ROS 2 그래프(Graph)를 탐색하는 정찰 활동(Reconnaissance Activity)을 나타낼 수 있다.

감사 기록(Audit Record)은 노드 이름이나 IP 주소에만 의존하지 않고 참여자 신원을 보존해야 한다. 노드 이름은 중복될 수 있으며 네트워크 주소는 DHCP, 컨테이너(Container), 이동형 로봇 또는 동적 인프라로 인해 변경될 수 있다. 가능한 경우 이벤트를 암호학적 신원(Cryptographic Identity), 보안 엔클레이브(Security Enclave), 호스트 신원(Host Identity), 프로세스 정보, 로봇 식별자 및 관련 ROS 2 자원 이름과 연계하여 이후 조사에서 더욱 강력한 귀속 체계(Attribution Chain)를 구성해야 한다.

분산 로봇 시스템은 여러 프로세서와 네트워크 장치에서 이벤트를 생성하므로 시간 동기화(Time Synchronization)가 필수적이다. 일관된 타임스탬프(Timestamp)가 없으면 조사자는 인증 실패가 명령 이상보다 먼저 발생했는지 또는 네트워크 이벤트가 노드 재시작보다 앞서 발생했는지 판단하지 못할 수 있다. 따라서 호스트, 엣지 컴퓨터(Edge Computer), 게이트웨이 및 모니터링 인프라는 충분히 정확한 시간 동기화를 유지하고 로그가 통합될 때 타임스탬프 출처(Timestamp Provenance)를 보존해야 한다.

애플리케이션 로그(Application Log)는 미들웨어 보안 로깅이 활성화된 경우에도 중요하다. ROS 2 노드는 정상적으로 인증되고 합법적인 권한을 보유하면서도 침해, 소프트웨어 결함 또는 악성 입력으로 인해 비정상적으로 동작할 수 있다. 수명주기 전환(Lifecycle Transition), 구성 변경, 명령 수락, 안전 상태 변경, 예상하지 못한 재시작 및 애플리케이션 오류를 기록하는 로그는 인증 및 접근 제어 기록만으로는 식별할 수 없는 오용을 발견하는 데 도움을 줄 수 있다.

DDS 및 미들웨어 이벤트(Middleware Event)는 호스트 수준 텔레메트리(Host-Level Telemetry)와 연계해야 한다. 프로세스 생성, 서비스 시작, 권한 변경, 파일 접근, 인증서 수정, 컨테이너 이벤트, 시스템 인증 및 자원 고갈(Resource Exhaustion)은 ROS 2 동작이 변경된 원인을 설명할 수 있다. 예를 들어 참여자가 갑자기 비인가 요청을 생성하기 시작했다면 외부 DDS 참여자보다 호스트에서 새롭게 실행된 프로세스 또는 변경된 실행 파일이 원인일 수 있다.

네트워크 모니터링(Network Monitoring)은 또 다른 가시성 계층을 제공한다. 연결 패턴, 멀티캐스트 동작(Multicast Behavior), 디스커버리 트래픽, 대역폭 이상, 패킷 손실, 인터페이스 변경, 방화벽 이벤트 및 예상하지 못한 주소와의 통신은 ROS 2 사고에 대한 추가적인 컨텍스트를 제공할 수 있다. 암호화된 DDS 트래픽은 설계상 페이로드 검사를 제한하므로 스캐닝, 서비스 거부(Denial-of-Service), 비정상 디스커버리 또는 예상하지 못한 통신 경로를 탐지하기 위해 메타데이터와 엔드포인트 동작(Endpoint Behavior)이 더욱 중요해진다.

중앙 집중식 로그 수집(Centralized Log Collection)은 장치 장애, 침해, 도난 또는 저장소 손상 이후 로컬 로그를 사용할 수 없을 수 있기 때문에 로봇 플릿(Robot Fleet)에서 중요하다. 로봇은 선택된 보안 이벤트를 엣지 수집기(Edge Collector), 플릿 서버(Fleet Server) 또는 보안 정보 및 이벤트 관리(Security Information and Event Management, SIEM) 플랫폼으로 전달할 수 있다. 중앙 집중화는 여러 로봇의 이벤트를 비교할 수 있게 하여 개별 장치 검사만으로는 파악하기 어려운 플릿 전반의 조직적 공격이나 반복적인 인증 실패를 식별하는 데 도움을 준다.

수집 아키텍처(Collection Architecture)는 간헐적인 연결(Intermittent Connectivity)을 고려해야 한다. 이동형 로봇, 실외 시스템 및 원격 플랫폼은 중앙 인프라와의 연결을 일시적으로 잃을 수 있다. 로컬 버퍼링(Local Buffering)은 연결이 복구될 때까지 중요한 이벤트를 보존할 수 있지만 저장 용량과 보존 한계(Retention Limit)를 통제해야 한다. 대용량 진단 또는 센서 로그가 인증, 인가, 구성 또는 사고 증거를 덮어쓰지 않도록 보안 핵심 기록(Security-Critical Record)에 우선순위를 부여해야 한다.

로그 무결성(Log Integrity)은 로그 가용성(Log Availability)만큼 중요하다. 로봇을 침해한 공격자는 침입 사실을 보여주는 기록을 삭제하거나 변경하려고 시도할 수 있다. 추가 기록 중심 저장소(Append-Oriented Storage), 암호학적 무결성 검사(Cryptographic Integrity Check), 제한된 쓰기 권한, 원격 전달 및 보호된 보존 기능을 사용하면 증거 조작을 어렵게 만들 수 있다. 감사 시스템은 설명되지 않는 로깅 공백(Logging Gap)도 탐지해야 하며, 동작 중인 로봇에서 갑자기 로그가 중단되는 현상 자체가 보안 관련 이벤트가 될 수 있다.

감사 수집 과정에서 민감한 정보(Sensitive Information)가 노출되어서는 안 된다. 개인 키(Private Key), 비밀번호, 세션 비밀정보(Session Secret), 완전한 인증 토큰(Authentication Token) 또는 불필요한 기밀 페이로드를 일반 로그에 기록해서는 안 된다. 운영 정책에 따라 인증서와 식별자 역시 신중하게 처리해야 할 수 있다. 로깅은 귀속 및 분석에 필요한 충분한 정보를 기록하면서 최소화 원칙(Minimization Principle)을 적용하여 모니터링 시스템 자체가 고가치 비밀정보의 새로운 저장소가 되지 않도록 해야 한다.

이벤트 정규화(Event Normalization)는 서로 다른 ROS 2 미들웨어 구현체, 운영체제, 컨테이너 및 보안 구성요소가 호환되지 않는 로그 형식을 생성하는 경우 분석을 개선한다. 타임스탬프, 로봇 식별자, 호스트, 참여자 신원, 노드, 엔클레이브, 이벤트 범주, 영향을 받은 자원, 결과, 심각도(Severity), 상관관계 식별자(Correlation Identifier)와 같은 공통 필드를 사용하면 중앙 도구가 이기종 기록을 처리할 수 있다. 정규화는 플릿 전체 검색을 단순화하고 재사용 가능한 탐지 규칙(Detection Rule)을 지원한다.

상관 분석(Correlation)은 개별 기록을 보안 정보로 변환한다. 한 번의 거부된 토픽 발행은 구성 오류일 수 있지만 수백 번의 발행 거부 이후 수명주기 전환과 비정상 네트워크 트래픽이 발생했다면 침해를 의미할 수 있다. 분석 과정에서는 인증 실패, 인가 거부, 노드 재시작, 인증서 변경, 네트워크 이상 및 안전 이벤트를 의미 있는 시간 범위(Time Window) 내에서 결합하여 개별 로그만으로는 확인하기 어려운 패턴을 식별해야 한다.

기준 동작(Baseline Behavior)은 운영 로봇이 비교적 예측 가능한 통신 관계를 나타내는 경우가 많으므로 이상 탐지(Anomaly Detection)를 지원할 수 있다. 운영자는 정상적인 참여자, 토픽 상호작용, 서비스 사용, 인증 빈도, 재시작 패턴 및 네트워크 목적지를 특성화할 수 있다. 이러한 기준에서 벗어난다고 해서 자동으로 공격을 의미하는 것은 아니지만 새로운 참여자가 등장하거나 노드가 비정상적인 자원에 접근하기 시작하거나 통신량이 갑자기 변경되는 경우 조사 우선순위를 높일 수 있다.

경보(Alerting)는 모든 보안 이벤트를 동일하게 처리하기보다 운영 및 물리적 결과를 반영해야 한다. 액추에이터 명령을 발행하려는 실패한 시도는 일반적으로 위험도가 낮은 진단 토픽과 관련된 단일 접근 거부보다 중요하다. 탐지 로직(Detection Logic)은 자원의 중요도, 참여자 신원, 반복 빈도, 로봇 운용 상태 및 연관 이벤트를 고려해야 한다. 이를 통해 경보 피로(Alert Fatigue)를 줄이면서 안전, 임무 수행 또는 플릿 가용성에 영향을 줄 수 있는 동작을 우선적으로 처리할 수 있다.

감사 보존 요구사항(Audit Retention Requirement)은 사고 대응(Incident Response)과 규정 준수(Compliance) 요구를 반영해야 한다. 일부 이벤트는 발생 후 수주가 지나 발견된 공격을 조사하기 위해 장기간 보존해야 할 수 있지만 지속적으로 생성되는 디버깅 로그는 훨씬 짧은 보존 기간을 적용할 수 있다. 저장 정책은 보안 감사 증거(Security Audit Evidence)와 일반 운영 텔레메트리를 구분하고 보존 기간, 아카이브 보호, 접근 권한, 삭제 절차 및 증거 보존 요구사항을 정의해야 한다.

감사 시스템 자체에 대한 접근 역시 엄격하게 통제해야 한다. 로그는 로봇 아키텍처, 소프트웨어 신원, 운영 일정, 네트워크 관계 및 보안 실패에 관한 정보를 노출할 수 있다. 허가된 인력과 서비스만 보안 기록을 검색, 내보내기, 수정 또는 삭제할 수 있어야 한다. 로깅 플랫폼 내부에서 수행된 관리 작업(Administrative Action) 역시 감사하여 조사자가 누가 증거에 접근했거나 모니터링 및 보존 구성을 변경했는지 확인할 수 있도록 해야 한다.

사고 대응은 관련 증거를 보존할 수 있는 능력에 의존한다. 의심스러운 동작이 탐지되면 선택된 로그를 일반적인 순환(Log Rotation)이나 삭제로부터 보호하고 사고 타임라인(Incident Timeline)과 연결해야 한다. 이후 인증 기록, 인가 실패, 호스트 이벤트, 네트워크 관측, 구성 이력 및 소프트웨어 버전을 함께 분석할 수 있다. 출처(Provenance)와 타임스탬프를 보존하면 근본 원인 분석(Root-Cause Analysis)을 지원하고 초기 침입과 이후 발생한 영향을 구분하는 데 도움을 준다.

감사 기능(Audit Functionality)은 인증 및 접근 제어와 마찬가지로 테스트해야 한다. 보안 팀은 실패한 인증 시도, 거부된 토픽 접근, 비인가 서비스 요청, 인증서 문제, 노드 재시작 및 기타 대표적인 이벤트를 의도적으로 생성한 후 예상된 기록이 수집 시스템에 도달하는지 검증해야 한다. 또한 버퍼링, 전달 실패, 시계 오류, 저장 공간 고갈, 로그 순환, 일시적인 네트워크 단절 이후의 복구까지 테스트해야 한다.

전체 구조에서 감사 수집(Audit Collection)은 인증서 구성, DDS 인증 및 암호화, 접근 제어 정책, 노드 신원 이후에 위치하며, 암호학적 키 관리(Cryptographic Key Management), 취약점 개선(Vulnerability Remediation), 침투 테스트(Penetration Testing), 규정 준수 매핑(Compliance Mapping)에 앞선다. 이러한 위치는 앞서 구축된 ROS 2 보안 통제의 동작을 검증하고 기록하는 관찰 가능성 계층(Observability Layer)으로서 감사 기능이 수행하는 역할을 반영한다.

효과적인 ROS 2 감사 분석(Audit Analysis)은 분산된 보안 이벤트를 사이버-물리 시스템(Cyber-Physical System) 전체에 대한 증거로 변환한다. 신원, 인가, 미들웨어, 호스트, 네트워크 및 애플리케이션 정보를 상관 분석함으로써 운영자는 비정상 동작을 탐지하고, 사고를 조사하며, 정책 집행을 검증하고, 복구를 지원할 수 있다. 보호된 타임스탬프, 중앙 집중식 수집, 무결성 통제, 적절한 보존 정책 및 검증된 탐지 로직을 결합하면 로깅은 수동적인 디버깅 메커니즘이 아니라 능동적인 보안 기능(Active Security Capability)이 된다.

##  

## 04.07. ROS2 Cryptographic Key Management Rotation [w/Code]

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

Cryptographic key management is a foundational requirement for secure ROS 2 communication because authentication, integrity protection, and encryption ultimately depend on secret key material remaining trustworthy. Certificates can identify participants, but compromised private keys may allow attackers to impersonate legitimate components. Key management therefore covers generation, provisioning, storage, use, renewal, rotation, revocation, backup, recovery, and secure destruction throughout the robot lifecycle.

A ROS 2 deployment may contain several categories of cryptographic material associated with SROS2 and DDS Security. Identity private keys support participant authentication, certificate authority keys establish trust, and session or communication keys protect data exchanges. These materials have different lifetimes and exposure risks, so they should not be managed as one undifferentiated secret. Each key type requires controls appropriate to its authority, function, and potential impact if compromised.

Key generation should use cryptographically secure mechanisms and approved algorithms with sufficient key strength for the expected operational lifetime. Keys should be generated within controlled environments and should not pass through unnecessary intermediate systems. Predictable randomness, copied development keys, or manually created shared secrets can undermine otherwise strong security mechanisms. Generation procedures should also record ownership and purpose without exposing the private key itself.

Certificate authority keys require particularly strong protection because they represent a root or intermediate source of trust. Compromise of a signing key may allow unauthorized certificates to be created for apparently legitimate ROS 2 participants. Offline storage, restricted administrative access, hardware-backed protection, separation of duties, and carefully controlled signing workflows can reduce this risk. Production and development environments should normally maintain separate trust infrastructures.

Provisioning securely transfers credentials from the trusted issuance environment to the robot, computer, container, or enclave that will use them. This process must prevent interception, substitution, and accidental duplication. Provisioning records should associate each credential with a specific device, software role, security enclave, or participant so that operators can later determine where a key was deployed and which permissions depend on the corresponding identity.

Private keys stored on robot computers require protection against unauthorized extraction. Ordinary file permissions provide a basic layer but may be insufficient when an attacker obtains administrative access. Encrypted storage, trusted platform modules, hardware security modules, secure elements, or platform-specific protected key facilities can strengthen key custody. The appropriate mechanism depends on hardware capability, performance requirements, serviceability, and the consequences of credential compromise.

Key access should follow the principle of least privilege. A process should obtain access only to the key material required for its own identity or communication role. Sharing a single private key across unrelated ROS 2 components increases the compromise domain because one vulnerable process may expose credentials used by many others. Security enclaves and role-specific identities can help align key ownership with meaningful software and trust boundaries.

Rotation limits the period during which a compromised key remains useful and allows cryptographic material to be refreshed before algorithms, certificates, or operational assumptions become obsolete. Rotation should be treated as a normal lifecycle operation rather than an exceptional incident procedure. A fleet that cannot replace credentials without extensive manual intervention may retain vulnerable keys simply because changing them introduces unacceptable operational disruption.

Rotation frequency should reflect risk rather than follow one arbitrary interval for every key. Highly privileged identities, externally exposed gateways, long-lived robots, and credentials stored on physically accessible devices may justify shorter rotation periods. Root signing keys may follow a different lifecycle from participant credentials. Policies should consider key authority, exposure, certificate validity, hardware protection, mission duration, maintenance opportunities, and regulatory requirements.

Credential rotation must preserve availability. Replacing a certificate or private key without coordinating trust configuration can cause participants to reject one another and interrupt DDS discovery or application communication. A controlled transition may require overlapping validity periods, staged distribution of new trust material, verification of new credentials, activation at a defined point, and removal of obsolete material only after the new identity has been confirmed across dependent systems.

Large robot fleets make manual rotation increasingly impractical. Automated credential lifecycle management can identify upcoming expirations, issue replacement credentials, distribute them through authenticated channels, verify installation, activate new material, and report failures. Automation must itself be strongly protected because a compromised provisioning or rotation service could distribute malicious credentials at fleet scale. Administrative actions should therefore be authenticated, authorized, logged, and auditable.

Certificate expiration should be monitored continuously rather than discovered when communication fails. Fleet monitoring can track validity windows and generate warnings sufficiently early for planned renewal. Expiration thresholds should account for robots that may remain offline for extended periods. A robot returning from a long mission should not unexpectedly lose trusted communication because its credentials expired while disconnected from the infrastructure responsible for renewal.

Revocation differs from routine rotation because it removes trust in credentials that should no longer be accepted. Revocation may be necessary after private-key exposure, device theft, suspected compromise, employee or supplier access changes, decommissioning, or erroneous certificate issuance. Response procedures should identify the affected identity, determine its privileges and deployment scope, remove its trust where required, issue replacements when appropriate, and investigate activity performed before revocation.

Shared credentials complicate revocation because the security team may be unable to invalidate one compromised component without affecting many legitimate systems. Unique or narrowly scoped identities therefore improve incident containment. A robot-specific or role-specific credential allows targeted replacement, while a fleet-wide private key can turn one device compromise into a fleet-wide emergency. Credential architecture should consider revocation consequences before deployment begins.

Backup and recovery require careful design because losing keys can make legitimate systems inaccessible, while excessive backups create additional locations from which secrets can be stolen. Not every private key needs to be recoverable; some can be regenerated and associated certificates reissued. When backup is required, copies should be encrypted, access-controlled, inventoried, and protected separately from normal runtime storage. Recovery procedures should be tested before an actual failure occurs.

Secure destruction is the final stage of the key lifecycle. Replaced, revoked, or decommissioned keys should not remain indefinitely in temporary directories, old container images, diagnostic archives, backup folders, or retired storage devices. Destruction procedures should consider the characteristics of the underlying storage technology and should remove obsolete credentials from operational systems after required recovery or evidence-retention obligations have been satisfied.

Key inventory provides the visibility needed to manage this lifecycle. Operators should know which certificates and keys exist, their owners, associated robots or components, issuing authorities, validity periods, privileges, storage locations, and current lifecycle states. Inventory data should never contain exposed private-key values. Instead, identifiers, fingerprints, metadata, and deployment records can support expiration monitoring, incident response, audits, and controlled rotation.

Audit logging should accompany sensitive key-management operations. Certificate issuance, key provisioning, rotation, revocation, trust-store changes, failed updates, and administrative access to credential systems should generate protected records. Correlating these events with ROS 2 authentication failures and fleet behavior can reveal whether a communication disruption is caused by a planned rotation, configuration error, expired credential, or potentially malicious modification.

Rotation procedures should be tested under realistic operating conditions. Tests should include normal renewal, expired credentials, rejected replacements, interrupted distribution, temporarily offline robots, rollback, participant restart, and recovery after partial deployment. The objective is to verify not only cryptographic correctness but also operational continuity. A technically secure rotation mechanism that repeatedly disables robots during maintenance is unlikely to remain effective in production.

Emergency rotation requires a faster path than routine renewal. When a key is suspected of compromise, security teams may need to revoke trust, isolate affected participants, distribute replacement credentials, and restore essential communication under time pressure. Predefined procedures, automated tooling, credential inventories, and tested recovery workflows reduce the temptation to disable authentication or temporarily introduce broad credentials during incident response.

Within the ROS 2 and DDS security structure, cryptographic key management follows certificate configuration, authentication and encryption, access control, node identity, and audit logging, while preceding vulnerability remediation, penetration testing, and compliance mapping. This sequence reflects the need to maintain the cryptographic trust established by earlier controls throughout their operational lifecycle. Volume_24_Robot_Cybersecurity

Effective key management turns cryptographic protection from a deployment-time configuration into a sustainable security capability. Secure generation and storage establish trustworthy credentials, controlled provisioning places them with the correct participants, rotation limits long-term exposure, and revocation contains compromised identities. Combined with inventory, automation, auditing, recovery, and secure destruction, these practices preserve ROS 2 trust relationships throughout the service life of individual robots and entire fleets.

암호학적 키 관리(Cryptographic Key Management)는 인증(Authentication), 무결성 보호(Integrity Protection), 암호화(Encryption)가 궁극적으로 비밀 키 자료(Secret Key Material)의 신뢰성에 의존하기 때문에 안전한 ROS 2 통신의 기본 요구사항이다. 인증서는 참여자의 신원을 식별할 수 있지만 개인 키(Private Key)가 침해되면 공격자가 정상적인 구성요소를 사칭할 수 있다. 따라서 키 관리는 로봇 수명주기 전체에 걸친 생성, 프로비저닝, 저장, 사용, 갱신, 순환, 폐기, 백업, 복구 및 안전한 파기를 포함한다.

ROS 2 배포 환경에는 SROS2 및 DDS 보안(DDS Security)과 관련된 여러 종류의 암호학적 자료(Cryptographic Material)가 존재할 수 있다. 신원 개인 키(Identity Private Key)는 참여자 인증을 지원하고, 인증 기관 키(Certificate Authority Key)는 신뢰를 설정하며, 세션 또는 통신 키(Session or Communication Key)는 데이터 교환을 보호한다. 이러한 자료는 서로 다른 수명과 노출 위험을 가지므로 하나의 동일한 비밀정보로 관리해서는 안 된다. 각 키 유형에는 권한, 기능 및 침해 시 잠재적 영향에 적합한 통제를 적용해야 한다.

키 생성(Key Generation)은 암호학적으로 안전한 메커니즘과 예상되는 운영 수명에 충분한 키 강도를 가진 승인된 알고리즘을 사용해야 한다. 키는 통제된 환경에서 생성하고 불필요한 중간 시스템을 거치지 않도록 해야 한다. 예측 가능한 난수, 복사된 개발용 키 또는 수동으로 생성한 공유 비밀정보(Shared Secret)는 강력한 보안 메커니즘도 약화시킬 수 있다. 생성 절차는 개인 키 자체를 노출하지 않으면서 소유자와 사용 목적을 기록해야 한다.

인증 기관 키(Certificate Authority Key)는 루트 또는 중간 신뢰 원천(Root or Intermediate Source of Trust)을 나타내므로 특히 강력하게 보호해야 한다. 서명 키(Signing Key)가 침해되면 비인가 인증서를 정상적인 ROS 2 참여자의 인증서처럼 생성할 수 있다. 오프라인 저장소(Offline Storage), 제한된 관리자 접근, 하드웨어 기반 보호(Hardware-Backed Protection), 직무 분리(Separation of Duties), 엄격하게 통제된 서명 워크플로(Signing Workflow)를 통해 이러한 위험을 줄일 수 있다. 운영 환경과 개발 환경은 일반적으로 서로 분리된 신뢰 인프라(Trust Infrastructure)를 유지해야 한다.

프로비저닝(Provisioning)은 신뢰할 수 있는 발급 환경에서 실제로 자격증명을 사용할 로봇, 컴퓨터, 컨테이너(Container) 또는 엔클레이브(Enclave)로 안전하게 전달하는 과정이다. 이 과정에서는 가로채기(Interception), 대체(Substitution), 우발적인 복제를 방지해야 한다. 프로비저닝 기록은 각각의 자격증명을 특정 장치, 소프트웨어 역할, 보안 엔클레이브 또는 참여자와 연결하여 운영자가 이후 해당 키가 어디에 배포되었고 어떤 권한이 대응되는 신원에 의존하는지 확인할 수 있도록 해야 한다.

로봇 컴퓨터에 저장되는 개인 키는 비인가 추출(Unauthorized Extraction)로부터 보호해야 한다. 일반적인 파일 권한은 기본적인 보호 계층을 제공하지만 공격자가 관리자 권한을 획득한 경우 충분하지 않을 수 있다. 암호화 저장소(Encrypted Storage), 신뢰 플랫폼 모듈(Trusted Platform Module, TPM), 하드웨어 보안 모듈(Hardware Security Module, HSM), 보안 요소(Secure Element) 또는 플랫폼별 보호 키 기능을 사용하면 키 보관(Key Custody)을 강화할 수 있다. 적절한 메커니즘은 하드웨어 기능, 성능 요구사항, 유지보수성 및 자격증명 침해의 결과에 따라 결정해야 한다.

키 접근(Key Access)은 최소 권한 원칙(Principle of Least Privilege)을 따라야 한다. 프로세스는 자신의 신원 또는 통신 역할에 필요한 키 자료에만 접근할 수 있어야 한다. 하나의 개인 키를 서로 관련 없는 ROS 2 구성요소가 공유하면 취약한 프로세스 하나를 통해 여러 구성요소가 사용하는 자격증명이 노출될 수 있으므로 침해 범위가 증가한다. 보안 엔클레이브(Security Enclave)와 역할별 신원(Role-Specific Identity)은 키 소유권을 의미 있는 소프트웨어 및 신뢰 경계(Trust Boundary)에 맞추는 데 도움을 줄 수 있다.

키 순환(Key Rotation)은 침해된 키가 유효하게 사용될 수 있는 기간을 제한하고 알고리즘, 인증서 또는 운영상의 가정이 더 이상 적절하지 않게 되기 전에 암호학적 자료를 갱신할 수 있도록 한다. 순환은 예외적인 사고 대응 절차가 아니라 정상적인 수명주기 작업(Lifecycle Operation)으로 취급해야 한다. 광범위한 수동 작업 없이 자격증명을 교체할 수 없는 플릿(Fleet)은 키 변경이 과도한 운영 중단을 유발한다는 이유로 취약한 키를 계속 사용할 가능성이 있다.

순환 주기(Rotation Frequency)는 모든 키에 하나의 임의적인 기간을 적용하기보다 위험을 반영해야 한다. 높은 권한을 가진 신원, 외부에 노출된 게이트웨이, 장기간 운용되는 로봇 및 물리적으로 접근 가능한 장치에 저장된 자격증명은 더 짧은 순환 주기가 필요할 수 있다. 루트 서명 키(Root Signing Key)는 참여자 자격증명과 다른 수명주기를 적용할 수 있다. 정책은 키 권한, 노출 정도, 인증서 유효기간, 하드웨어 보호, 임무 기간, 유지보수 기회 및 규제 요구사항을 고려해야 한다.

자격증명 순환(Credential Rotation)은 가용성(Availability)을 유지해야 한다. 신뢰 구성을 조정하지 않고 인증서 또는 개인 키를 교체하면 참여자들이 서로를 거부하여 DDS 디스커버리 또는 애플리케이션 통신이 중단될 수 있다. 통제된 전환 과정에서는 기존 및 신규 자격증명의 유효기간 중첩, 새로운 신뢰 자료의 단계적 배포, 신규 자격증명 검증, 정의된 시점에서의 활성화, 종속 시스템 전체에서 새로운 신원이 확인된 이후의 기존 자료 제거가 필요할 수 있다.

대규모 로봇 플릿에서는 수동 순환(Manual Rotation)이 점점 비현실적이 된다. 자동화된 자격증명 수명주기 관리(Automated Credential Lifecycle Management)는 예정된 만료를 식별하고, 대체 자격증명을 발급하며, 인증된 채널을 통해 배포하고, 설치를 검증하며, 새로운 자료를 활성화하고, 실패를 보고할 수 있다. 그러나 프로비저닝 또는 순환 서비스가 침해되면 악성 자격증명이 플릿 전체에 배포될 수 있으므로 자동화 시스템 자체도 강력하게 보호해야 한다. 따라서 관리 작업은 인증, 인가, 로깅 및 감사가 가능해야 한다.

인증서 만료(Certificate Expiration)는 통신 장애가 발생한 이후 발견하는 것이 아니라 지속적으로 모니터링해야 한다. 플릿 모니터링(Fleet Monitoring)은 유효기간을 추적하고 계획된 갱신을 수행할 수 있도록 충분히 이른 시점에 경고를 생성할 수 있다. 만료 임계값(Expiration Threshold)은 장기간 오프라인 상태로 유지될 수 있는 로봇까지 고려해야 한다. 장기 임무에서 복귀한 로봇이 갱신 인프라와 연결되지 못한 동안 자격증명이 만료되어 신뢰할 수 있는 통신을 갑자기 상실해서는 안 된다.

폐기(Revocation)는 더 이상 허용해서는 안 되는 자격증명에 대한 신뢰를 제거한다는 점에서 일반적인 순환과 다르다. 개인 키 노출, 장치 도난, 침해 의심, 직원 또는 공급업체 접근 권한 변경, 시스템 폐기(Decommissioning), 잘못된 인증서 발급 이후에는 폐기가 필요할 수 있다. 대응 절차는 영향을 받은 신원을 식별하고 해당 신원의 권한과 배포 범위를 확인하며, 필요한 위치에서 신뢰를 제거하고, 적절한 경우 대체 자격증명을 발급하며, 폐기 이전에 수행된 활동을 조사해야 한다.

공유 자격증명(Shared Credential)은 보안 팀이 여러 정상 시스템에 영향을 주지 않고 하나의 침해된 구성요소만 무효화하기 어렵게 만들기 때문에 폐기 과정을 복잡하게 한다. 따라서 고유하거나 좁은 범위로 제한된 신원은 사고 격리(Incident Containment)를 향상시킨다. 로봇별 또는 역할별 자격증명을 사용하면 표적화된 교체가 가능하지만 플릿 전체가 하나의 개인 키를 공유하면 하나의 장치 침해가 플릿 전체의 비상 상황으로 확대될 수 있다. 자격증명 아키텍처는 배포 이전부터 폐기의 영향을 고려해야 한다.

백업 및 복구(Backup and Recovery)는 키를 잃으면 정상적인 시스템에 접근할 수 없게 되는 반면 지나치게 많은 백업은 비밀정보가 탈취될 수 있는 추가 위치를 생성하기 때문에 신중하게 설계해야 한다. 모든 개인 키를 반드시 복구할 필요는 없으며 일부 키는 다시 생성하고 관련 인증서를 재발급할 수 있다. 백업이 필요한 경우 복사본을 암호화하고 접근을 통제하며 목록화하고 일반 런타임 저장소와 분리하여 보호해야 한다. 실제 장애가 발생하기 전에 복구 절차를 테스트해야 한다.

안전한 파기(Secure Destruction)는 키 수명주기의 마지막 단계이다. 교체, 폐기 또는 시스템 종료로 더 이상 사용하지 않는 키가 임시 디렉터리, 이전 컨테이너 이미지, 진단 아카이브, 백업 폴더 또는 폐기된 저장 장치에 무기한 남아 있어서는 안 된다. 파기 절차는 기본 저장 기술의 특성을 고려해야 하며, 필요한 복구 또는 증거 보존(Evidence Retention) 의무를 충족한 이후 운영 시스템에서 오래된 자격증명을 제거해야 한다.

키 인벤토리(Key Inventory)는 이러한 수명주기를 관리하는 데 필요한 가시성을 제공한다. 운영자는 어떤 인증서와 키가 존재하는지, 소유자는 누구인지, 어떤 로봇 또는 구성요소와 연결되어 있는지, 발급 기관, 유효기간, 권한, 저장 위치 및 현재 수명주기 상태가 무엇인지 파악해야 한다. 인벤토리 데이터에는 노출된 개인 키 값을 포함해서는 안 된다. 대신 식별자, 지문(Fingerprint), 메타데이터 및 배포 기록을 사용하여 만료 모니터링, 사고 대응, 감사 및 통제된 순환을 지원할 수 있다.

감사 로깅(Audit Logging)은 민감한 키 관리 작업과 함께 수행되어야 한다. 인증서 발급, 키 프로비저닝, 순환, 폐기, 신뢰 저장소(Trust Store) 변경, 업데이트 실패 및 자격증명 시스템에 대한 관리자 접근은 보호된 기록을 생성해야 한다. 이러한 이벤트를 ROS 2 인증 실패 및 플릿 동작과 연계하면 통신 중단이 계획된 순환, 구성 오류, 만료된 자격증명 또는 잠재적으로 악의적인 변경으로 인해 발생했는지 판단할 수 있다.

순환 절차(Rotation Procedure)는 실제 운영 조건에서 테스트해야 한다. 테스트에는 정상 갱신, 만료된 자격증명, 거부된 대체 자격증명, 중단된 배포, 일시적으로 오프라인 상태인 로봇, 롤백(Rollback), 참여자 재시작 및 부분 배포 이후의 복구가 포함되어야 한다. 목표는 암호학적 정확성뿐만 아니라 운영 연속성(Operational Continuity)까지 검증하는 것이다. 기술적으로 안전하더라도 유지보수 과정에서 반복적으로 로봇을 중단시키는 순환 메커니즘은 운영 환경에서 지속적으로 적용되기 어렵다.

비상 순환(Emergency Rotation)은 일반적인 갱신보다 빠른 대응 경로를 필요로 한다. 키가 침해된 것으로 의심되면 보안 팀은 제한된 시간 안에 신뢰를 폐기하고, 영향을 받은 참여자를 격리하며, 대체 자격증명을 배포하고, 필수 통신을 복구해야 할 수 있다. 사전에 정의된 절차, 자동화 도구, 자격증명 인벤토리 및 검증된 복구 워크플로(Recovery Workflow)는 사고 대응 과정에서 인증을 비활성화하거나 임시로 광범위한 권한의 자격증명을 도입하려는 상황을 방지하는 데 도움을 준다.

ROS 2 및 DDS 보안 구조에서 암호학적 키 관리(Cryptographic Key Management)는 인증서 구성, 인증 및 암호화, 접근 제어, 노드 신원, 감사 로깅 이후에 위치하며 취약점 개선(Vulnerability Remediation), 침투 테스트(Penetration Testing), 규정 준수 매핑(Compliance Mapping)에 앞선다. 이러한 순서는 앞선 보안 통제를 통해 설정된 암호학적 신뢰(Cryptographic Trust)를 전체 운영 수명주기 동안 지속적으로 유지해야 한다는 요구사항을 반영한다.

효과적인 키 관리(Key Management)는 암호학적 보호를 단순한 배포 시점의 구성에서 지속 가능한 보안 기능(Sustainable Security Capability)으로 전환한다. 안전한 생성과 저장은 신뢰할 수 있는 자격증명을 확립하고, 통제된 프로비저닝은 올바른 참여자에게 이를 배치하며, 순환은 장기적인 노출을 제한하고, 폐기는 침해된 신원을 격리한다. 인벤토리, 자동화, 감사, 복구 및 안전한 파기를 결합하면 개별 로봇과 전체 플릿의 서비스 수명(Service Life) 동안 ROS 2 신뢰 관계를 지속적으로 유지할 수 있다.

##  

## 04.08. ROS2 Known CVE Remediation and Patch Mgmt

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

![](images/image9.png){width="7.268055555555556in" height="7.268055555555556in"}

Known vulnerability remediation is essential for ROS 2 security because a protected middleware configuration cannot compensate for exploitable defects in the operating system, ROS packages, DDS implementation, libraries, drivers, or supporting services. Patch management provides the lifecycle process for identifying affected components, evaluating vulnerability relevance, applying corrective updates, validating system behavior, and maintaining evidence that deployed robots remain within an approved security baseline.

A ROS 2 vulnerability-management program should begin with an accurate inventory of software and firmware. Teams need visibility into ROS distributions, middleware vendors and versions, operating-system packages, container images, third-party libraries, device drivers, network services, and embedded components. Without this inventory, a newly disclosed CVE cannot be reliably mapped to affected robots, and vulnerable dependencies may remain hidden inside applications long after patches become available.

Software bills of materials can strengthen this inventory by recording direct and transitive dependencies used to build robot software. ROS 2 applications frequently combine packages from multiple repositories with DDS libraries, cryptographic components, image-processing libraries, AI runtimes, and vendor SDKs. An SBOM allows security teams to search these dependency relationships when a vulnerability is announced instead of relying only on package names visible at the application level.

CVE monitoring should include authoritative vulnerability databases, operating-system security advisories, ROS and middleware vendor notices, package maintainers, and relevant hardware suppliers. The objective is not merely to collect vulnerability identifiers but to determine whether the vulnerable component and affected configuration actually exist in the deployed environment. Automated feeds can improve coverage, but engineering review remains necessary to interpret applicability to a specific robot architecture.

Severity scores provide useful prioritization information but should not determine remediation order by themselves. A moderate vulnerability affecting an externally reachable fleet gateway may create greater operational risk than a high-scoring defect in a disabled local component. Risk evaluation should consider exploitability, network exposure, required privileges, available mitigations, affected robot functions, safety consequences, mission criticality, and whether exploitation is known to occur in realistic environments.

ROS 2 and DDS vulnerabilities require architecture-aware analysis because middleware defects may affect discovery, serialization, authentication, access control, resource handling, or network processing. A vulnerability in a DDS implementation can potentially influence many ROS 2 nodes using that middleware even when the application code itself is unchanged. Security teams should therefore trace shared infrastructure dependencies and avoid evaluating each ROS package as an isolated software component.

Patch prioritization should reflect cyber-physical consequences. Vulnerabilities affecting motion control, safety supervision, remote management, authentication, cryptographic processing, or externally exposed communication paths generally deserve accelerated review. Exploitation that causes a conventional server process to crash is serious, but the same availability failure in a mobile robot may interrupt navigation, disable sensing, halt production, or force the platform into an emergency state.

Immediate patching is not always possible in operational robotics. A vendor fix may be unavailable, a new library may conflict with existing software, or maintenance windows may be limited. Compensating controls can temporarily reduce exposure through network segmentation, firewall rules, service disabling, access-control restrictions, isolation of vulnerable interfaces, or increased monitoring. Such controls should be documented as temporary risk treatments rather than treated as permanent substitutes for remediation.

Patch acquisition must preserve software supply-chain trust. Updates should come from approved repositories or verified suppliers, and package signatures, hashes, provenance, and repository configuration should be validated where supported. Attackers may exploit urgent vulnerability announcements by distributing malicious replacement packages. A remediation process that installs unverified software can therefore create a more severe compromise than the vulnerability it was intended to correct.

Testing is particularly important before patches reach physical robots. Updates can alter middleware behavior, timing, dependencies, discovery, serialization, drivers, resource consumption, or real-time performance. A patch that closes a security vulnerability but destabilizes control communication may introduce unacceptable operational risk. Representative simulation, software-in-the-loop, hardware-in-the-loop, staging, or controlled robot testing should therefore precede broad production deployment.

Security regression testing should accompany functional validation. After an update, teams should confirm that SROS2 identities, DDS authentication, encryption, access-control policies, enclaves, audit logging, and key handling continue to operate as intended. Changes in middleware or dependencies can affect security configuration even when application behavior appears normal. Both authorized communication and deliberate unauthorized attempts should be tested when security-sensitive components are modified.

Fleet deployment should use staged rollout rather than updating every robot simultaneously. A small representative group can receive the patch first, allowing teams to monitor startup behavior, ROS 2 discovery, latency, CPU and memory usage, safety functions, network communication, and application stability. If no unacceptable regression appears, deployment can progressively expand. Staging reduces the probability that one defective update disables an entire operational fleet.

Rollback capability should be prepared before deployment. Robot software may require restoration to a previously validated version if a patch causes instability or incompatibility. Rollback packages, configuration backups, dependency snapshots, and clear decision criteria should be available before installation begins. However, rollback also reintroduces the original vulnerability, so reverting should trigger explicit risk review and compensating controls until a corrected update can be deployed.

Patch management must account for robots that are offline, stored, undergoing repair, or disconnected during a fleet update. A system that misses a critical patch should not silently return to normal service months later with obsolete software. Fleet management should record update status and identify noncompliant devices when they reconnect. Depending on risk, outdated robots may require restricted network access or maintenance before returning to unrestricted operation.

Containers and immutable deployment images can improve reproducibility but do not eliminate patch responsibilities. A vulnerable library embedded in an old container remains vulnerable even if the host operating system is fully updated. Images should be rebuilt from patched dependencies, rescanned, signed, versioned, and redeployed through the normal release process. Obsolete images should be removed from registries and deployment systems when retention requirements permit.

Patch status should be linked to vulnerability records and asset inventory. For each relevant issue, teams should know which robots are affected, whether a fix exists, which mitigation is active, who owns remediation, what validation has been completed, and which deployed version contains the correction. This traceability supports incident response and prevents vulnerabilities from disappearing administratively while remaining technically unresolved in deployed systems.

Exceptions require explicit governance. Some vulnerabilities may remain temporarily unpatched because of certification constraints, unavailable vendor fixes, hardware limitations, or unacceptable operational impact. An exception should document the affected assets, technical rationale, residual risk, compensating controls, responsible owner, review date, and conditions requiring escalation. Open-ended acceptance without reassessment allows temporary exposure to become permanent technical debt.

Audit logs can verify whether remediation activities occurred as planned. Package installation, image replacement, configuration modification, robot reboot, security-policy change, and rollback events should be traceable to authorized maintenance activity. Correlating these records with vulnerability-management data helps distinguish expected changes from unauthorized modification and provides evidence that critical patches were actually deployed rather than merely scheduled.

Post-remediation verification should confirm that the vulnerable component has truly been removed, replaced, disabled, or otherwise mitigated. Version checks alone may be insufficient when multiple copies of a library exist, old containers remain deployable, or dormant packages are still installed. Vulnerability scanning, dependency inspection, configuration validation, and targeted security testing can provide stronger evidence that the original attack path is no longer practically exploitable.

Patch metrics should emphasize risk reduction rather than update volume. Useful measures include time from vulnerability disclosure to triage, time to mitigation, time to validated remediation, percentage of critical assets within the approved baseline, overdue exceptions, and failed deployments. These indicators reveal whether the organization can respond effectively to security defects without encouraging teams to maximize patch counts regardless of operational significance.

Within the chapter structure, known CVE remediation and patch management follows certificate configuration, DDS protection, access control, node identity, audit collection, and cryptographic key management, and precedes ROS 2 penetration testing and compliance mapping. This placement reflects the need to maintain previously established security controls by continuously correcting vulnerabilities in the software stack on which those controls depend.

Effective ROS 2 patch management combines vulnerability intelligence, asset visibility, risk-based prioritization, trusted update acquisition, controlled testing, staged deployment, rollback planning, and verification. The objective is not simply to install the newest packages, but to reduce exploitable exposure while preserving deterministic robot behavior, safety, and availability. A disciplined remediation lifecycle keeps ROS 2 and DDS security effective as vulnerabilities, dependencies, and operational environments evolve.

알려진 취약점 개선(Known Vulnerability Remediation)은 보호된 미들웨어 구성만으로는 운영체제, ROS 패키지, DDS 구현체, 라이브러리, 드라이버 또는 지원 서비스에 존재하는 악용 가능한 결함을 보완할 수 없기 때문에 ROS 2 보안에서 필수적이다. 패치 관리(Patch Management)는 영향을 받는 구성요소를 식별하고, 취약점의 관련성을 평가하며, 수정 업데이트를 적용하고, 시스템 동작을 검증하며, 배포된 로봇이 승인된 보안 기준선(Security Baseline)을 유지하고 있다는 증거를 관리하는 수명주기 프로세스를 제공한다.

ROS 2 취약점 관리 프로그램(Vulnerability-Management Program)은 소프트웨어와 펌웨어에 대한 정확한 인벤토리(Inventory)에서 시작해야 한다. 조직은 ROS 배포판(ROS Distribution), 미들웨어 공급업체와 버전, 운영체제 패키지, 컨테이너 이미지(Container Image), 서드파티 라이브러리(Third-Party Library), 장치 드라이버, 네트워크 서비스 및 임베디드 구성요소를 파악해야 한다. 이러한 인벤토리가 없으면 새롭게 공개된 CVE가 어떤 로봇에 영향을 주는지 정확하게 연결할 수 없으며, 패치가 제공된 이후에도 취약한 종속성이 애플리케이션 내부에 장기간 숨겨져 있을 수 있다.

소프트웨어 자재명세서(Software Bill of Materials, SBOM)는 로봇 소프트웨어 구축에 사용되는 직접 및 전이 종속성(Transitive Dependency)을 기록하여 이러한 인벤토리를 강화할 수 있다. ROS 2 애플리케이션은 여러 저장소의 패키지와 DDS 라이브러리, 암호학적 구성요소, 영상 처리 라이브러리, AI 런타임 및 공급업체 SDK를 결합하는 경우가 많다. SBOM을 사용하면 취약점이 발표되었을 때 애플리케이션 수준에서 보이는 패키지 이름에만 의존하지 않고 이러한 종속 관계를 검색할 수 있다.

CVE 모니터링(CVE Monitoring)은 권위 있는 취약점 데이터베이스, 운영체제 보안 권고(Security Advisory), ROS 및 미들웨어 공급업체 공지, 패키지 유지관리자 및 관련 하드웨어 공급업체 정보를 포함해야 한다. 목적은 단순히 취약점 식별자를 수집하는 것이 아니라 취약한 구성요소와 영향을 받는 구성이 실제 배포 환경에 존재하는지를 판단하는 것이다. 자동화된 피드(Automated Feed)는 탐지 범위를 향상시킬 수 있지만 특정 로봇 아키텍처에 대한 적용 가능성을 판단하기 위해서는 엔지니어링 검토가 필요하다.

심각도 점수(Severity Score)는 유용한 우선순위 정보를 제공하지만 그 자체만으로 개선 순서를 결정해서는 안 된다. 외부에서 접근 가능한 플릿 게이트웨이(Fleet Gateway)에 영향을 미치는 중간 수준의 취약점이 비활성화된 로컬 구성요소의 높은 점수 취약점보다 더 큰 운영 위험을 발생시킬 수 있다. 위험 평가는 악용 가능성(Exploitability), 네트워크 노출, 필요한 권한, 사용 가능한 완화책, 영향을 받는 로봇 기능, 안전 결과, 임무 중요도 및 실제 환경에서의 악용 가능성을 고려해야 한다.

ROS 2 및 DDS 취약점은 미들웨어 결함이 디스커버리(Discovery), 직렬화(Serialization), 인증(Authentication), 접근 제어(Access Control), 자원 처리(Resource Handling) 또는 네트워크 처리에 영향을 줄 수 있기 때문에 아키텍처를 고려한 분석이 필요하다. DDS 구현체의 취약점은 애플리케이션 코드 자체가 변경되지 않더라도 해당 미들웨어를 사용하는 다수의 ROS 2 노드에 영향을 줄 수 있다. 따라서 보안 팀은 공유 인프라 종속성을 추적하고 각 ROS 패키지를 독립적인 소프트웨어 구성요소로만 평가하지 않아야 한다.

패치 우선순위(Patch Prioritization)는 사이버-물리적 결과(Cyber-Physical Consequence)를 반영해야 한다. 모션 제어, 안전 감독, 원격 관리, 인증, 암호학적 처리 또는 외부에 노출된 통신 경로에 영향을 주는 취약점은 일반적으로 신속한 검토가 필요하다. 일반적인 서버 프로세스의 충돌을 유발하는 취약점도 심각하지만 동일한 가용성 장애가 이동형 로봇에서 발생하면 내비게이션 중단, 센싱 비활성화, 생산 중단 또는 플랫폼의 비상 상태 전환을 초래할 수 있다.

운영 중인 로봇 환경에서는 즉각적인 패치 적용이 항상 가능한 것은 아니다. 공급업체의 수정 사항이 아직 제공되지 않았거나 새로운 라이브러리가 기존 소프트웨어와 충돌하거나 유지보수 시간(Maintenance Window)이 제한될 수 있다. 네트워크 분할(Network Segmentation), 방화벽 규칙, 서비스 비활성화, 접근 제어 제한, 취약한 인터페이스 격리 또는 강화된 모니터링과 같은 보완 통제(Compensating Control)를 통해 노출을 일시적으로 줄일 수 있다. 이러한 통제는 영구적인 개선 대체 수단이 아니라 임시 위험 처리(Temporary Risk Treatment)로 문서화해야 한다.

패치 획득(Patch Acquisition)은 소프트웨어 공급망 신뢰(Software Supply-Chain Trust)를 유지해야 한다. 업데이트는 승인된 저장소 또는 검증된 공급업체에서 받아야 하며, 지원되는 경우 패키지 서명, 해시(Hash), 출처(Provenance), 저장소 구성을 검증해야 한다. 공격자는 긴급한 취약점 공지를 악용하여 악성 대체 패키지를 배포할 수 있다. 따라서 검증되지 않은 소프트웨어를 설치하는 개선 절차는 원래 수정하려던 취약점보다 더 심각한 침해를 발생시킬 수 있다.

패치가 실제 물리 로봇에 적용되기 전에 테스트(Testing)를 수행하는 것이 특히 중요하다. 업데이트는 미들웨어 동작, 타이밍, 종속성, 디스커버리, 직렬화, 드라이버, 자원 사용량 또는 실시간 성능(Real-Time Performance)을 변경할 수 있다. 보안 취약점을 해결하면서 제어 통신을 불안정하게 만드는 패치는 허용할 수 없는 운영 위험을 발생시킬 수 있다. 따라서 광범위한 운영 배포 이전에 대표적인 시뮬레이션, 소프트웨어 인 더 루프(Software-in-the-Loop, SIL), 하드웨어 인 더 루프(Hardware-in-the-Loop, HIL), 스테이징(Staging) 또는 통제된 로봇 테스트를 수행해야 한다.

보안 회귀 테스트(Security Regression Testing)는 기능 검증과 함께 수행해야 한다. 업데이트 이후 SROS2 신원, DDS 인증, 암호화, 접근 제어 정책, 엔클레이브(Enclave), 감사 로깅(Audit Logging), 키 처리(Key Handling)가 의도한 대로 계속 동작하는지 확인해야 한다. 미들웨어 또는 종속성 변경은 애플리케이션 동작이 정상적으로 보이는 경우에도 보안 구성에 영향을 줄 수 있다. 보안에 민감한 구성요소가 변경된 경우 허가된 통신과 의도적인 비인가 통신 시도를 모두 테스트해야 한다.

플릿 배포(Fleet Deployment)는 모든 로봇을 동시에 업데이트하는 대신 단계적 롤아웃(Staged Rollout)을 사용해야 한다. 소규모의 대표적인 로봇 그룹에 먼저 패치를 적용하고 시작 동작, ROS 2 디스커버리, 지연시간(Latency), CPU 및 메모리 사용량, 안전 기능, 네트워크 통신 및 애플리케이션 안정성을 모니터링할 수 있다. 허용할 수 없는 회귀(Regression)가 발견되지 않으면 배포 범위를 점진적으로 확대할 수 있다. 단계적 배포는 하나의 결함 있는 업데이트가 전체 운영 플릿을 비활성화할 가능성을 줄인다.

롤백 기능(Rollback Capability)은 배포 전에 준비해야 한다. 패치로 인해 불안정성이나 호환성 문제가 발생하면 로봇 소프트웨어를 이전에 검증된 버전으로 복원해야 할 수 있다. 롤백 패키지, 구성 백업, 종속성 스냅샷(Dependency Snapshot), 명확한 의사결정 기준을 설치 이전에 준비해야 한다. 그러나 롤백은 원래의 취약점을 다시 도입하므로 이전 버전으로 복귀할 경우 수정된 업데이트가 배포될 때까지 명시적인 위험 검토와 보완 통제를 적용해야 한다.

패치 관리는 플릿 업데이트 동안 오프라인 상태이거나 보관 중이거나 수리 중이거나 연결이 끊어진 로봇도 고려해야 한다. 중요 패치를 놓친 시스템이 수개월 후 오래된 소프트웨어를 유지한 상태로 정상 서비스에 자동 복귀해서는 안 된다. 플릿 관리(Fleet Management)는 업데이트 상태를 기록하고 장치가 다시 연결될 때 비준수 장치(Noncompliant Device)를 식별해야 한다. 위험 수준에 따라 오래된 로봇은 정상 운영에 복귀하기 전에 제한된 네트워크 접근 또는 유지보수를 요구할 수 있다.

컨테이너(Container)와 불변 배포 이미지(Immutable Deployment Image)는 재현성을 향상시킬 수 있지만 패치 책임을 제거하지는 않는다. 오래된 컨테이너에 포함된 취약한 라이브러리는 호스트 운영체제가 완전히 업데이트되어 있더라도 여전히 취약하다. 이미지는 패치된 종속성을 기반으로 다시 구축하고, 재스캔하며, 서명하고, 버전을 부여한 후 정상적인 릴리스 프로세스를 통해 다시 배포해야 한다. 보존 요구사항이 허용하는 경우 오래된 이미지는 레지스트리와 배포 시스템에서 제거해야 한다.

패치 상태(Patch Status)는 취약점 기록과 자산 인벤토리에 연결해야 한다. 각 관련 취약점에 대해 어떤 로봇이 영향을 받는지, 수정 사항이 존재하는지, 어떤 완화책이 활성화되어 있는지, 개선 책임자가 누구인지, 어떤 검증이 완료되었는지, 어떤 배포 버전에 수정 사항이 포함되어 있는지를 파악해야 한다. 이러한 추적성(Traceability)은 사고 대응을 지원하고 취약점이 관리상으로는 종료되었지만 실제 배포 시스템에서는 기술적으로 해결되지 않은 상태로 남는 것을 방지한다.

예외(Exception)는 명시적인 거버넌스(Governance)를 필요로 한다. 일부 취약점은 인증 제약, 공급업체 수정 사항 부재, 하드웨어 제한 또는 허용할 수 없는 운영 영향 때문에 일시적으로 패치하지 못할 수 있다. 예외에는 영향을 받는 자산, 기술적 근거, 잔여 위험(Residual Risk), 보완 통제, 책임자, 검토 날짜 및 에스컬레이션 조건을 문서화해야 한다. 재평가 없는 무기한 위험 수용은 일시적인 노출을 영구적인 기술 부채(Technical Debt)로 만들 수 있다.

감사 로그(Audit Log)는 개선 활동이 계획대로 수행되었는지를 검증할 수 있다. 패키지 설치, 이미지 교체, 구성 변경, 로봇 재부팅, 보안 정책 변경 및 롤백 이벤트는 승인된 유지보수 활동과 연결하여 추적할 수 있어야 한다. 이러한 기록을 취약점 관리 데이터와 연계하면 예상된 변경과 비인가 변경을 구분하고 중요 패치가 단순히 예정된 것이 아니라 실제로 배포되었다는 증거를 제공할 수 있다.

개선 이후 검증(Post-Remediation Verification)은 취약한 구성요소가 실제로 제거, 교체, 비활성화 또는 다른 방식으로 완화되었는지 확인해야 한다. 동일한 라이브러리의 여러 복사본이 존재하거나 오래된 컨테이너가 여전히 배포 가능하거나 사용하지 않는 패키지가 설치된 상태라면 버전 확인만으로 충분하지 않을 수 있다. 취약점 스캐닝(Vulnerability Scanning), 종속성 검사, 구성 검증 및 표적 보안 테스트를 통해 원래의 공격 경로가 더 이상 실질적으로 악용 가능하지 않다는 강력한 증거를 확보할 수 있다.

패치 지표(Patch Metric)는 업데이트 수량보다 위험 감소(Risk Reduction)에 초점을 맞추어야 한다. 유용한 지표에는 취약점 공개부터 분류(Triage)까지의 시간, 완화까지의 시간, 검증된 개선까지의 시간, 승인된 기준선을 충족하는 중요 자산의 비율, 기한이 지난 예외 및 실패한 배포 등이 포함된다. 이러한 지표는 운영상 중요성과 관계없이 단순히 패치 수를 최대화하도록 유도하지 않으면서 조직이 보안 결함에 효과적으로 대응할 수 있는지를 보여준다.

전체 구조에서 알려진 CVE 개선 및 패치 관리(Known CVE Remediation and Patch Management)는 인증서 구성, DDS 보호, 접근 제어, 노드 신원, 감사 수집 및 암호학적 키 관리 이후에 위치하며, ROS 2 침투 테스트(Penetration Testing)와 규정 준수 매핑(Compliance Mapping)에 앞선다. 이러한 배치는 앞서 구축된 보안 통제가 의존하는 소프트웨어 스택의 취약점을 지속적으로 수정함으로써 해당 보안 통제의 효과를 유지해야 한다는 구조적 관계를 반영한다.

효과적인 ROS 2 패치 관리(Patch Management)는 취약점 인텔리전스(Vulnerability Intelligence), 자산 가시성(Asset Visibility), 위험 기반 우선순위 결정, 신뢰할 수 있는 업데이트 획득, 통제된 테스트, 단계적 배포, 롤백 계획 및 검증을 결합한다. 목적은 단순히 최신 패키지를 설치하는 것이 아니라 결정론적인 로봇 동작(Deterministic Robot Behavior), 안전 및 가용성을 유지하면서 악용 가능한 노출을 줄이는 것이다. 체계적인 개선 수명주기(Remediation Lifecycle)는 취약점, 종속성 및 운영 환경이 변화하더라도 ROS 2와 DDS 보안이 지속적으로 효과를 유지하도록 한다.

##  

## 04.09. ROS2 Security Penetration Test Methodology [w/Code]

![](images/image10.png){width="7.268055555555556in" height="7.268055555555556in"}

ROS 2 security penetration testing evaluates whether the protections designed around DDS communication, node identity, authorization, cryptographic credentials, and host infrastructure resist realistic adversarial behavior. Unlike ordinary functional testing, penetration testing intentionally attempts to violate security assumptions. Its purpose is to discover exploitable paths, configuration weaknesses, excessive privileges, and unsafe failure behavior before those weaknesses can affect deployed robots.

The methodology should begin by defining the assessment scope and authorization boundaries. Testers need to identify the robots, ROS 2 domains, networks, hosts, containers, middleware implementations, gateways, operator interfaces, and supporting services included in the exercise. Safety restrictions must also be established because aggressive testing against a cyber-physical platform can produce motion, communication loss, resource exhaustion, or unintended transitions into degraded operating states.

Threat modeling provides the basis for selecting meaningful test scenarios. The assessment should consider unauthorized network participants, compromised ROS 2 nodes, malicious maintenance tools, stolen credentials, hostile devices on the local network, compromised containers, and attackers entering through external interfaces. Each adversary model should be connected to assets and trust boundaries so that testing focuses on plausible attack paths rather than arbitrary vulnerability scanning.

Reconnaissance examines what an attacker can learn before attempting exploitation. Testers may evaluate whether ROS 2 or DDS discovery reveals participants, endpoints, topic relationships, service interfaces, namespaces, middleware characteristics, or network topology. Protected environments should minimize information available to unauthorized systems. Discovery behavior should therefore be assessed both without valid credentials and from authenticated participants that possess intentionally restricted permissions.

Participant authentication testing determines whether unauthorized entities can join trusted DDS communication. Test cases should include untrusted certificates, expired credentials, altered identity material, incorrect trust anchors, duplicated node names, and credentials assigned to the wrong enclave or participant. The expected result is rejection without insecure fallback. Successful authentication should also be examined to ensure that identity verification does not unintentionally grant privileges beyond those explicitly authorized.

Impersonation testing evaluates whether an attacker can reproduce the logical identity of a legitimate ROS 2 component. Copying a node name, namespace, topic pattern, or network address should not be sufficient to establish trusted identity. Testers should attempt to imitate planners, sensors, controllers, diagnostic tools, or supervisory components while lacking the legitimate cryptographic credentials, verifying that security decisions remain bound to authenticated identity rather than application-controlled naming.

Authorization testing examines whether authenticated participants can exceed their assigned privileges. A restricted node can attempt to publish to protected command topics, subscribe to confidential sensor streams, invoke administrative services, manipulate lifecycle interfaces, or interact with unauthorized actions. Both explicit names and namespace patterns should be tested because overly broad wildcard permissions can expose resources that were not intended to be accessible to the participant.

Command injection scenarios deserve special attention because ROS 2 often controls physical behavior. Testing should verify that unauthorized participants cannot publish velocity, trajectory, actuator, navigation, manipulation, docking, or other safety-relevant commands. Where testing could cause physical motion, execution should occur in simulation, hardware-in-the-loop environments, controlled test areas, or configurations in which actuators are safely inhibited while the communication path remains representative.

Service and action interfaces should be tested independently from ordinary topic communication. Attackers may attempt to reset components, modify configuration, trigger calibration, change lifecycle states, submit unauthorized goals, or cancel legitimate operations. The assessment should verify both client and server authorization relationships and confirm that hidden or rarely used administrative interfaces do not remain broadly accessible simply because normal robot operation does not invoke them frequently.

Cryptographic protection testing should verify confidentiality and integrity expectations for DDS traffic. Testers can inspect whether protected communication exposes sensitive payloads or discovery information and whether modified traffic is rejected. Attempts to replay previously captured exchanges can help evaluate resistance to reuse of stale authentication or communication material. Testing should focus on verifying security properties rather than attempting to weaken production cryptography through unsafe operational shortcuts.

Credential compromise scenarios evaluate the consequences of obtaining a legitimate participant identity. A stolen certificate and private key may permit authentication, so the remaining authorization boundaries become critical. Testing should determine how much access a compromised identity receives, whether privileges are appropriately scoped, whether abnormal activity generates audit events, and whether the credential can be revoked and replaced without disabling unrelated robots or components.

Host compromise testing examines security below the ROS 2 middleware layer. File permissions, credential storage, container boundaries, process privileges, startup services, configuration files, environment variables, and local administrative interfaces can undermine middleware security if poorly protected. The assessment should determine whether compromise of a lower-trust process provides access to private keys, policy files, privileged sockets, or execution contexts belonging to more critical ROS 2 components.

Network segmentation should be validated through active testing rather than assumed from architecture documentation. Testers should verify whether development systems, diagnostic laptops, fleet services, external networks, and robot control segments can reach only the interfaces they require. Firewall and routing rules should be evaluated for unintended paths. A compromised low-trust network should not automatically provide direct access to safety-critical ROS 2 or DDS communication domains.

Availability testing should evaluate resistance to resource exhaustion while remaining within predefined safety limits. Excessive discovery activity, repeated authentication attempts, connection churn, malformed traffic, or high-rate requests may consume CPU, memory, bandwidth, or middleware resources. The objective is to determine whether the robot maintains essential functions, rejects abusive activity, produces useful alerts, and enters a controlled degraded or safe state when resource pressure exceeds acceptable limits.

Malformed-input testing can expose weaknesses in serialization, deserialization, message handling, middleware parsing, and application validation. Fuzzing may be applied to suitable interfaces in isolated or controlled environments, especially when malformed traffic could crash critical processes. Test planning should account for middleware version, message types, protocol boundaries, and recovery behavior so that discovered failures can be reproduced without unnecessarily endangering physical hardware.

Audit and detection controls should be evaluated during every penetration-testing phase. Failed authentication, denied authorization, suspicious service requests, unexpected participants, credential misuse, and abnormal network behavior should generate appropriate evidence. Testers should determine whether events reach centralized monitoring, contain sufficient attribution information, preserve reliable timestamps, and produce alerts proportional to the operational significance of the attempted activity.

Patch-management effectiveness can also be assessed by comparing the deployed software inventory with known vulnerability status. Testing should verify whether obsolete ROS 2 packages, middleware versions, libraries, container images, operating-system components, or vendor dependencies remain exploitable despite documented remediation. Where a known vulnerability cannot be patched, the assessment should determine whether compensating controls actually prevent or meaningfully restrict the expected attack path.

Multi-robot environments require cross-robot authorization testing. A participant authenticated for one robot should attempt to discover, subscribe to, publish toward, or invoke services belonging to another robot. Fleet-level components should be tested separately because they may legitimately possess broader privileges. The objective is to confirm that robot-specific identities, namespaces, enclaves, and permissions provide isolation while authorized coordination services retain only the cross-robot access they require.

Findings should be evaluated according to exploitability and cyber-physical consequence rather than technical severity alone. A weakness that permits unauthorized actuator commands may demand immediate remediation even when exploitation requires local network access. Reports should document the affected component, prerequisites, attack path, observed result, operational impact, supporting evidence, recommended mitigation, and retest criteria so that engineering teams can reproduce and correct the issue systematically.

Remediation validation is a required final phase rather than an optional follow-up. After certificates, policies, middleware versions, network rules, software, or configurations are changed, the original attack path should be tested again. Regression testing should confirm that the correction does not break legitimate ROS 2 communication or create a new weakness elsewhere. Closed findings should therefore represent verified risk reduction rather than merely completed configuration changes.

Within the chapter structure, ROS 2 security penetration testing follows certificate configuration, DDS protection, access control, node identity, audit logging, cryptographic key management, and known CVE remediation, while preceding compliance mapping. This sequence allows penetration testing to evaluate whether the accumulated ROS 2 and DDS security controls operate together as intended and whether exploitable gaps remain before formal compliance evidence is consolidated.

A mature ROS 2 penetration-testing methodology combines threat-driven scenarios, controlled adversarial testing, cyber-physical safety constraints, evidence collection, remediation, and retesting. The objective is not simply to identify isolated vulnerabilities but to determine whether an attacker can cross trust boundaries and influence robot behavior. Repeated testing across software releases and architecture changes provides practical assurance that ROS 2 security controls remain effective as the robotic system evolves.

ROS 2 보안 침투 테스트(Security Penetration Testing)는 DDS 통신, 노드 신원(Node Identity), 인가(Authorization), 암호학적 자격증명(Cryptographic Credential), 호스트 인프라를 중심으로 설계된 보호 기능이 현실적인 적대적 행위(Adversarial Behavior)에 견딜 수 있는지를 평가한다. 일반적인 기능 테스트와 달리 침투 테스트는 의도적으로 보안 가정(Security Assumption)을 위반하려고 시도한다. 목적은 이러한 약점이 실제 배포된 로봇에 영향을 미치기 전에 악용 가능한 경로, 구성 취약점, 과도한 권한 및 안전하지 않은 실패 동작을 발견하는 것이다.

방법론(Methodology)은 평가 범위(Assessment Scope)와 인가 경계(Authorization Boundary)를 정의하는 것에서 시작해야 한다. 테스터는 평가에 포함되는 로봇, ROS 2 도메인, 네트워크, 호스트, 컨테이너(Container), 미들웨어 구현체, 게이트웨이, 운영자 인터페이스 및 지원 서비스를 식별해야 한다. 사이버-물리 플랫폼에 대한 공격적인 테스트는 움직임, 통신 손실, 자원 고갈 또는 의도하지 않은 성능 저하 운용 상태(Degraded Operating State)로의 전환을 유발할 수 있으므로 안전 제한사항(Safety Restriction)도 설정해야 한다.

위협 모델링(Threat Modeling)은 의미 있는 테스트 시나리오를 선택하기 위한 기반을 제공한다. 평가에서는 비인가 네트워크 참여자, 침해된 ROS 2 노드, 악성 유지보수 도구, 탈취된 자격증명, 로컬 네트워크의 적대적 장치, 침해된 컨테이너 및 외부 인터페이스를 통해 침입하는 공격자를 고려해야 한다. 각 공격자 모델(Adversary Model)은 자산과 신뢰 경계(Trust Boundary)에 연결하여 임의적인 취약점 스캐닝이 아니라 현실적으로 가능한 공격 경로에 테스트를 집중해야 한다.

정찰(Reconnaissance)은 공격자가 실제 악용을 시도하기 전에 어떤 정보를 파악할 수 있는지를 조사한다. 테스터는 ROS 2 또는 DDS 디스커버리(Discovery)를 통해 참여자, 엔드포인트(Endpoint), 토픽 관계, 서비스 인터페이스, 네임스페이스(Namespace), 미들웨어 특성 또는 네트워크 토폴로지가 노출되는지 평가할 수 있다. 보호된 환경은 비인가 시스템에 제공되는 정보를 최소화해야 한다. 따라서 디스커버리 동작은 유효한 자격증명이 없는 경우와 의도적으로 제한된 권한을 가진 인증된 참여자의 경우를 모두 평가해야 한다.

참여자 인증 테스트(Participant Authentication Testing)는 비인가 엔티티(Entity)가 신뢰할 수 있는 DDS 통신에 참여할 수 있는지를 확인한다. 테스트 사례에는 신뢰할 수 없는 인증서, 만료된 자격증명, 변경된 신원 자료, 잘못된 신뢰 앵커(Trust Anchor), 중복된 노드 이름 및 잘못된 엔클레이브(Enclave)나 참여자에 할당된 자격증명이 포함되어야 한다. 예상되는 결과는 비보안 폴백(Insecure Fallback) 없이 연결이 거부되는 것이다. 또한 정상 인증이 명시적으로 인가된 범위를 초과하는 권한을 의도하지 않게 부여하지 않는지도 확인해야 한다.

사칭 테스트(Impersonation Testing)는 공격자가 정상적인 ROS 2 구성요소의 논리적 신원을 복제할 수 있는지를 평가한다. 노드 이름, 네임스페이스, 토픽 패턴 또는 네트워크 주소를 복사하는 것만으로 신뢰할 수 있는 신원을 설정할 수 있어서는 안 된다. 테스터는 정상적인 암호학적 자격증명 없이 플래너(Planner), 센서, 제어기(Controller), 진단 도구 또는 감독 구성요소를 모방하여 보안 결정이 애플리케이션에서 제어되는 이름이 아니라 인증된 신원에 계속 연결되는지 검증해야 한다.

인가 테스트(Authorization Testing)는 인증된 참여자가 할당된 권한을 초과할 수 있는지를 조사한다. 제한된 노드는 보호된 명령 토픽(Command Topic)에 데이터를 발행하거나, 기밀 센서 스트림을 구독하거나, 관리 서비스를 호출하거나, 수명주기 인터페이스(Lifecycle Interface)를 조작하거나, 허가되지 않은 액션(Action)과 상호작용하려고 시도할 수 있다. 지나치게 광범위한 와일드카드 권한(Wildcard Permission)이 의도하지 않은 자원을 노출할 수 있으므로 명시적인 이름과 네임스페이스 패턴을 모두 테스트해야 한다.

명령 주입 시나리오(Command Injection Scenario)는 ROS 2가 물리적 동작을 제어하는 경우가 많으므로 특별한 주의가 필요하다. 테스트를 통해 비인가 참여자가 속도, 궤적, 액추에이터, 내비게이션, 조작, 도킹 또는 기타 안전 관련 명령을 발행할 수 없는지 확인해야 한다. 테스트가 물리적 움직임을 발생시킬 가능성이 있는 경우 시뮬레이션, 하드웨어 인 더 루프(Hardware-in-the-Loop, HIL) 환경, 통제된 시험 구역 또는 통신 경로는 실제와 유사하게 유지하면서 액추에이터를 안전하게 억제한 구성에서 수행해야 한다.

서비스 및 액션 인터페이스(Service and Action Interface)는 일반적인 토픽 통신과 별도로 테스트해야 한다. 공격자는 구성요소 초기화, 구성 변경, 보정(Calibration) 실행, 수명주기 상태 변경, 비인가 목표 제출 또는 정상적인 작업 취소를 시도할 수 있다. 평가에서는 클라이언트와 서버의 인가 관계를 모두 검증하고, 정상적인 로봇 동작에서 자주 사용되지 않는다는 이유만으로 숨겨져 있거나 드물게 사용되는 관리 인터페이스가 광범위하게 접근 가능한 상태로 남아 있지 않은지 확인해야 한다.

암호학적 보호 테스트(Cryptographic Protection Testing)는 DDS 트래픽에 대한 기밀성(Confidentiality)과 무결성(Integrity) 요구사항을 검증해야 한다. 테스터는 보호된 통신이 민감한 페이로드 또는 디스커버리 정보를 노출하는지 확인하고 변경된 트래픽이 거부되는지 평가할 수 있다. 이전에 캡처된 통신을 재전송하는 시도는 오래된 인증 또는 통신 자료의 재사용에 대한 저항성을 평가하는 데 도움이 된다. 테스트는 안전하지 않은 운영상의 우회 방법으로 운영 암호화를 약화시키는 것이 아니라 보안 속성을 검증하는 데 초점을 맞추어야 한다.

자격증명 침해 시나리오(Credential Compromise Scenario)는 정상적인 참여자의 신원을 획득했을 때 발생하는 결과를 평가한다. 탈취된 인증서와 개인 키(Private Key)를 사용하면 인증 자체는 성공할 수 있으므로 나머지 인가 경계가 중요해진다. 테스트에서는 침해된 신원이 어느 정도의 접근 권한을 얻는지, 권한이 적절하게 제한되는지, 비정상적인 활동이 감사 이벤트(Audit Event)를 생성하는지, 관련 없는 로봇이나 구성요소를 중단시키지 않고 해당 자격증명을 폐기하고 교체할 수 있는지를 확인해야 한다.

호스트 침해 테스트(Host Compromise Testing)는 ROS 2 미들웨어 계층 아래의 보안을 조사한다. 파일 권한, 자격증명 저장소, 컨테이너 경계, 프로세스 권한, 시작 서비스, 구성 파일, 환경 변수 및 로컬 관리 인터페이스가 제대로 보호되지 않으면 미들웨어 보안을 약화시킬 수 있다. 평가에서는 낮은 신뢰 수준의 프로세스가 침해되었을 때 더 중요한 ROS 2 구성요소의 개인 키, 정책 파일, 권한이 높은 소켓 또는 실행 컨텍스트에 접근할 수 있는지를 확인해야 한다.

네트워크 분할(Network Segmentation)은 아키텍처 문서만으로 보장된다고 가정하지 말고 능동적인 테스트를 통해 검증해야 한다. 테스터는 개발 시스템, 진단 노트북, 플릿 서비스, 외부 네트워크 및 로봇 제어 세그먼트가 필요한 인터페이스에만 접근할 수 있는지 확인해야 한다. 방화벽 및 라우팅 규칙도 의도하지 않은 경로가 존재하는지 평가해야 한다. 낮은 신뢰 수준의 네트워크가 침해되었다고 해서 안전 필수 ROS 2 또는 DDS 통신 도메인에 직접 접근할 수 있어서는 안 된다.

가용성 테스트(Availability Testing)는 사전에 정의된 안전 한계 내에서 자원 고갈(Resource Exhaustion)에 대한 저항성을 평가해야 한다. 과도한 디스커버리 활동, 반복적인 인증 시도, 연결 변동(Connection Churn), 비정상 트래픽 또는 고속 요청은 CPU, 메모리, 대역폭 또는 미들웨어 자원을 소비할 수 있다. 목적은 자원 압력이 허용 가능한 한계를 초과할 때 로봇이 필수 기능을 유지하고, 악의적인 활동을 거부하며, 유용한 경보를 생성하고, 통제된 성능 저하 상태 또는 안전 상태(Safe State)로 전환하는지를 확인하는 것이다.

비정상 입력 테스트(Malformed-Input Testing)는 직렬화(Serialization), 역직렬화(Deserialization), 메시지 처리, 미들웨어 파싱(Middleware Parsing), 애플리케이션 검증 과정의 취약점을 발견할 수 있다. 퍼징(Fuzzing)은 특히 비정상 트래픽이 중요 프로세스를 중단시킬 수 있는 경우 격리되거나 통제된 환경의 적절한 인터페이스에 적용할 수 있다. 테스트 계획은 미들웨어 버전, 메시지 유형, 프로토콜 경계 및 복구 동작을 고려하여 물리적 하드웨어를 불필요하게 위험에 노출하지 않으면서 발견된 장애를 재현할 수 있도록 해야 한다.

감사 및 탐지 통제(Audit and Detection Control)는 모든 침투 테스트 단계에서 평가해야 한다. 인증 실패, 인가 거부, 의심스러운 서비스 요청, 예상하지 못한 참여자, 자격증명 오용 및 비정상적인 네트워크 동작은 적절한 증거를 생성해야 한다. 테스터는 이벤트가 중앙 집중식 모니터링 시스템에 전달되는지, 충분한 귀속 정보(Attribution Information)를 포함하는지, 신뢰할 수 있는 타임스탬프를 보존하는지, 시도된 활동의 운영상 중요도에 비례하는 경보를 생성하는지 확인해야 한다.

패치 관리 효과(Patch-Management Effectiveness)는 배포된 소프트웨어 인벤토리와 알려진 취약점 상태를 비교하여 평가할 수 있다. 테스트에서는 문서상 개선이 완료되었음에도 오래된 ROS 2 패키지, 미들웨어 버전, 라이브러리, 컨테이너 이미지, 운영체제 구성요소 또는 공급업체 종속성이 여전히 악용 가능한 상태인지 확인해야 한다. 알려진 취약점을 패치할 수 없는 경우 보완 통제(Compensating Control)가 예상되는 공격 경로를 실제로 차단하거나 의미 있게 제한하는지를 평가해야 한다.

다중 로봇 환경(Multi-Robot Environment)은 로봇 간 인가 테스트(Cross-Robot Authorization Testing)를 필요로 한다. 하나의 로봇에 대해 인증된 참여자가 다른 로봇에 속한 자원을 디스커버리하거나 구독하거나 데이터를 발행하거나 서비스를 호출하려고 시도해야 한다. 플릿 수준 구성요소는 정상적으로 더 광범위한 권한을 가질 수 있으므로 별도로 테스트해야 한다. 목적은 로봇별 신원, 네임스페이스, 엔클레이브 및 권한이 격리를 제공하면서 허가된 조정 서비스에는 필요한 최소한의 로봇 간 접근만 허용하는지 확인하는 것이다.

발견 사항(Finding)은 기술적인 심각도만이 아니라 악용 가능성과 사이버-물리적 결과에 따라 평가해야 한다. 비인가 액추에이터 명령을 허용하는 취약점은 악용에 로컬 네트워크 접근이 필요하더라도 즉각적인 개선이 필요할 수 있다. 보고서에는 영향을 받는 구성요소, 사전 조건, 공격 경로, 관찰된 결과, 운영 영향, 지원 증거, 권장 완화책 및 재테스트 기준을 기록하여 엔지니어링 팀이 문제를 체계적으로 재현하고 수정할 수 있도록 해야 한다.

개선 검증(Remediation Validation)은 선택적인 후속 작업이 아니라 필수적인 최종 단계이다. 인증서, 정책, 미들웨어 버전, 네트워크 규칙, 소프트웨어 또는 구성이 변경된 이후에는 원래의 공격 경로를 다시 테스트해야 한다. 회귀 테스트(Regression Testing)를 통해 수정 사항이 정상적인 ROS 2 통신을 방해하거나 다른 위치에 새로운 취약점을 생성하지 않는지도 확인해야 한다. 따라서 종료된 발견 사항은 단순히 구성 변경이 완료되었다는 의미가 아니라 검증된 위험 감소(Verified Risk Reduction)를 의미해야 한다.

전체 구조에서 ROS 2 보안 침투 테스트는 인증서 구성, DDS 보호, 접근 제어, 노드 신원, 감사 로깅, 암호학적 키 관리(Cryptographic Key Management), 알려진 CVE 개선 이후에 위치하며 규정 준수 매핑(Compliance Mapping)에 앞선다. 이러한 순서를 통해 침투 테스트는 누적된 ROS 2 및 DDS 보안 통제가 의도한 대로 함께 동작하는지 평가하고 공식적인 규정 준수 증거를 통합하기 전에 악용 가능한 보안 공백이 남아 있는지를 확인할 수 있다.

성숙한 ROS 2 침투 테스트 방법론(Penetration-Testing Methodology)은 위협 기반 시나리오(Threat-Driven Scenario), 통제된 적대적 테스트, 사이버-물리 안전 제약(Cyber-Physical Safety Constraint), 증거 수집, 개선 및 재테스트를 결합한다. 목적은 단순히 개별적인 취약점을 식별하는 것이 아니라 공격자가 신뢰 경계를 넘어 로봇 동작에 영향을 줄 수 있는지를 판단하는 것이다. 소프트웨어 릴리스와 아키텍처 변경에 따라 반복적인 테스트를 수행하면 로봇 시스템이 발전하더라도 ROS 2 보안 통제가 지속적으로 효과를 유지한다는 실질적인 보증(Practical Assurance)을 제공할 수 있다.

##  

## 04.10. ROS2 Security Compliance IEC 62443 Mapping

![](images/image11.png){width="7.268055555555556in" height="7.268055555555556in"}

Mapping ROS 2 security controls to IEC 62443 provides a structured way to connect middleware protection with industrial cybersecurity requirements. The objective is not to claim that enabling SROS2 or DDS Security automatically creates IEC 62443 compliance. Instead, ROS 2 authentication, authorization, encryption, logging, key management, vulnerability remediation, and testing can provide technical evidence supporting broader system-level security requirements and lifecycle processes.

IEC 62443 treats cybersecurity as a combination of technical controls, secure development practices, system architecture, operational procedures, and lifecycle governance. ROS 2 represents only part of this environment. A compliant robotic system may also include operating systems, industrial networks, safety controllers, sensors, actuators, gateways, cloud interfaces, maintenance tools, and organizational processes. Mapping must therefore identify where ROS 2 contributes to a requirement and where additional controls remain necessary.

A useful mapping begins by defining the system under consideration and its security boundaries. Robot computers, ROS 2 domains, DDS participants, operator stations, fleet servers, gateways, and external services should be associated with appropriate zones and communication paths. IEC 62443 zone-and-conduit concepts can help separate components according to criticality and trust, while ROS 2 identities, namespaces, enclaves, network segmentation, and access policies can reinforce those logical boundaries.

Identification and authentication control can be supported through SROS2 and DDS Security participant authentication. Certificates and private keys establish cryptographically verifiable identities rather than relying only on node names or network addresses. Mutual authentication strengthens trust between communicating participants. Compliance evidence should demonstrate how identities are issued, assigned, validated, renewed, revoked, and protected throughout the operational lifecycle rather than merely showing that certificates exist.

Use control requirements relate closely to ROS 2 authorization and least-privilege policy. Topic publishing, topic subscription, service invocation, service provision, and action communication can be restricted according to participant roles. Policies should prevent an authenticated node from automatically receiving unrestricted middleware access. Evidence should show that command, sensor, lifecycle, administrative, and diagnostic interfaces are granted only to identities whose operational responsibilities require those privileges.

System integrity is supported by multiple ROS 2 and DDS security mechanisms. Cryptographic integrity protection can detect unauthorized modification of protected communication, while authenticated identities reduce the possibility of accepting data from unknown participants. Secure configuration, signed or verified software packages, controlled patching, protected policy files, and host hardening further contribute to integrity. Middleware security should therefore be evaluated as one layer within a larger integrity architecture.

Data confidentiality requirements can be addressed through DDS cryptographic protection where sensitive communication requires encryption. Sensor information, maps, mission data, proprietary algorithms, operational status, or command traffic may require different confidentiality levels. The mapping should document which communication classes are encrypted, why protection is required, and where confidentiality terminates. Protection of data at rest, backups, logs, and external interfaces requires controls beyond ROS 2 middleware encryption.

Restricted data flow aligns with segmentation and controlled ROS 2 communication relationships. DDS domains, network boundaries, firewalls, robot-specific namespaces, enclaves, and authorization rules can reduce unnecessary communication between components. In multi-robot systems, one robot should not automatically access another robot\'s internal resources. Compliance evidence should demonstrate that permitted information flows correspond to documented architectural relationships and that prohibited paths are actively tested.

Timely response to events depends on monitoring and audit capabilities. Authentication failures, authorization denials, unexpected participants, certificate problems, lifecycle changes, configuration modifications, and abnormal network behavior should produce useful security evidence. ROS 2 and DDS events can be correlated with host, container, firewall, gateway, and fleet telemetry. Reliable timestamps and protected centralized collection improve the ability to reconstruct incidents and demonstrate monitoring effectiveness.

Resource availability is especially important for cyber-physical systems because loss of middleware communication can affect physical operation. ROS 2 security assessment should consider excessive discovery activity, repeated authentication attempts, malformed traffic, resource exhaustion, network disruption, and overloaded logging. IEC 62443-oriented evidence should show how essential robot functions are maintained or transitioned into defined degraded or safe states when cyber events threaten communication or computational resources.

Security levels should not be interpreted as simple settings that can be assigned directly to ROS 2. IEC 62443 security objectives depend on the system context, threat environment, architecture, and applicable requirements. Enabling encryption or certificates does not by itself establish a particular security level. A defensible mapping identifies the required security capabilities, demonstrates how ROS 2 contributes to them, and records remaining dependencies on network, platform, operational, and organizational controls.

Secure development lifecycle requirements extend beyond runtime middleware configuration. ROS 2 packages and robot applications should be developed through controlled source management, dependency review, security testing, vulnerability handling, release management, and configuration control. Changes to certificates, permissions, middleware versions, container images, and security policies should be traceable. Development and production trust infrastructures should also remain separated to reduce accidental or unauthorized credential reuse.

Known vulnerability management provides evidence that security is maintained after deployment. ROS 2 distributions, DDS implementations, operating-system packages, libraries, containers, drivers, and vendor components should be inventoried and monitored for relevant CVEs. Risk-based remediation, compensating controls, staged patch deployment, rollback planning, and post-remediation verification demonstrate that known weaknesses are systematically addressed rather than allowed to accumulate throughout the robot lifecycle.

Cryptographic key management supports several compliance objectives because authentication and confidentiality depend on trustworthy credentials. Evidence should describe secure key generation, provisioning, storage, access restrictions, rotation, renewal, revocation, backup where necessary, and destruction. Hardware-backed protection may strengthen high-value identities. Key inventories and audit records should demonstrate which credentials belong to specific robots, components, or trust domains without exposing secret key material.

Penetration testing provides practical validation that documented controls resist adversarial behavior. Testing should attempt unauthorized discovery, participant impersonation, prohibited topic access, privileged service invocation, credential misuse, cross-robot communication, and resource exhaustion within controlled safety boundaries. Findings should be connected to remediation and retesting so that compliance evidence demonstrates verified security behavior rather than relying solely on architecture documents and configuration files.

Configuration management is essential because ROS 2 security behavior depends on coordinated certificates, permissions, governance rules, enclaves, middleware settings, network policies, and software versions. A configuration change can unintentionally weaken a previously validated boundary. Version-controlled artifacts, peer review, automated checks, release baselines, and deployment records help demonstrate that approved security configurations remain consistent between development, testing, and production environments.

Evidence collection should be designed as part of engineering rather than assembled only before an audit. Useful artifacts include architecture descriptions, asset inventories, trust models, access-control policies, certificate records, key lifecycle procedures, vulnerability reports, patch histories, penetration-test results, audit logs, configuration baselines, and remediation records. Each artifact should be traceable to the relevant requirement and to the specific product or system configuration being assessed.

A compliance matrix can connect each applicable IEC 62443 requirement with its ROS 2 implementation, supporting infrastructure, evidence source, responsible owner, validation method, and identified gap. Some requirements may be fully supported by technical controls, while others depend primarily on organizational or lifecycle processes. Explicitly recording partial coverage prevents the misleading assumption that a middleware feature alone satisfies a broader industrial cybersecurity requirement.

Gap analysis should identify requirements for which ROS 2 provides no direct control or only partial support. Physical access protection, personnel procedures, enterprise identity governance, secure manufacturing, recovery planning, supplier management, and some network infrastructure controls exist outside the middleware layer. These gaps do not represent ROS 2 failures; they identify responsibilities that must be addressed by the surrounding robotic platform, deployment environment, and organizational security program.

Compliance should also remain synchronized with system evolution. Adding a new sensor, AI component, remote interface, DDS implementation, fleet gateway, or maintenance workflow can change trust boundaries and invalidate earlier assumptions. The mapping should therefore be reviewed when architecture, software, threats, or operating conditions change. Continuous reassessment keeps compliance evidence aligned with the deployed system rather than with an obsolete design snapshot.

Within the chapter structure, IEC 62443 compliance mapping follows ROS 2 threat analysis, SROS2 certificate configuration, DDS authentication and encryption, access control, node identity, audit logging, key management, CVE remediation, and penetration testing. This final position allows the mapping process to consolidate the technical and lifecycle evidence produced by the preceding ROS 2 and DDS security activities into a coherent assurance framework.

Effective IEC 62443 mapping demonstrates how ROS 2 security participates in defense in depth rather than presenting middleware protection as standalone compliance. Cryptographic identity establishes trusted participants, authorization constrains communication, encryption and integrity protect data, logging supports detection, lifecycle controls maintain trust, and testing verifies enforcement. Combined with platform, network, operational, and organizational controls, these mechanisms support a defensible industrial cybersecurity posture for robotic systems.

ROS 2 보안 통제(Security Control)를 IEC 62443에 매핑(Mapping)하면 미들웨어 보호(Middleware Protection)를 산업 사이버보안 요구사항(Industrial Cybersecurity Requirement)과 체계적으로 연결할 수 있다. 목적은 SROS2 또는 DDS 보안(DDS Security)을 활성화하는 것만으로 IEC 62443 준수(Compliance)가 자동으로 달성된다고 주장하는 것이 아니다. 대신 ROS 2의 인증(Authentication), 인가(Authorization), 암호화(Encryption), 로깅(Logging), 키 관리(Key Management), 취약점 개선(Vulnerability Remediation), 테스트(Testing)는 보다 광범위한 시스템 수준 보안 요구사항과 수명주기 프로세스를 지원하는 기술적 증거를 제공할 수 있다.

IEC 62443은 사이버보안(Cybersecurity)을 기술적 통제(Technical Control), 안전한 개발 관행(Secure Development Practice), 시스템 아키텍처(System Architecture), 운영 절차(Operational Procedure), 수명주기 거버넌스(Lifecycle Governance)의 결합으로 다룬다. ROS 2는 이러한 환경의 일부만을 구성한다. 규정을 준수하는 로봇 시스템에는 운영체제, 산업용 네트워크, 안전 제어기(Safety Controller), 센서, 액추에이터, 게이트웨이, 클라우드 인터페이스, 유지보수 도구 및 조직 프로세스가 포함될 수 있다. 따라서 매핑에서는 ROS 2가 특정 요구사항에 기여하는 부분과 추가적인 통제가 필요한 부분을 식별해야 한다.

효과적인 매핑은 평가 대상 시스템(System Under Consideration)과 보안 경계(Security Boundary)를 정의하는 것에서 시작한다. 로봇 컴퓨터, ROS 2 도메인, DDS 참여자(Participant), 운영자 스테이션, 플릿 서버(Fleet Server), 게이트웨이 및 외부 서비스를 적절한 존(Zone)과 통신 경로에 연결해야 한다. IEC 62443의 존 및 컨듀잇(Zone and Conduit) 개념은 중요도와 신뢰 수준에 따라 구성요소를 분리하는 데 활용할 수 있으며, ROS 2 신원, 네임스페이스(Namespace), 엔클레이브(Enclave), 네트워크 분할(Network Segmentation), 접근 정책(Access Policy)은 이러한 논리적 경계를 강화할 수 있다.

식별 및 인증 통제(Identification and Authentication Control)는 SROS2와 DDS 보안의 참여자 인증(Participant Authentication)을 통해 지원할 수 있다. 인증서(Certificate)와 개인 키(Private Key)는 노드 이름이나 네트워크 주소에만 의존하지 않고 암호학적으로 검증 가능한 신원을 확립한다. 상호 인증(Mutual Authentication)은 통신 참여자 사이의 신뢰를 강화한다. 규정 준수 증거(Compliance Evidence)는 단순히 인증서가 존재한다는 사실이 아니라 신원이 전체 운영 수명주기 동안 어떻게 발급, 할당, 검증, 갱신, 폐기 및 보호되는지를 입증해야 한다.

사용 통제 요구사항(Use Control Requirement)은 ROS 2 인가 및 최소 권한 정책(Least-Privilege Policy)과 밀접하게 관련된다. 토픽 발행(Topic Publishing), 토픽 구독(Topic Subscription), 서비스 호출(Service Invocation), 서비스 제공(Service Provision), 액션 통신(Action Communication)은 참여자의 역할에 따라 제한할 수 있다. 정책은 인증된 노드가 자동으로 무제한적인 미들웨어 접근 권한을 획득하지 못하도록 해야 한다. 증거는 명령, 센서, 수명주기, 관리 및 진단 인터페이스가 운영상 해당 권한을 필요로 하는 신원에만 부여된다는 사실을 보여주어야 한다.

시스템 무결성(System Integrity)은 여러 ROS 2 및 DDS 보안 메커니즘을 통해 지원된다. 암호학적 무결성 보호(Cryptographic Integrity Protection)는 보호된 통신의 비인가 변경을 탐지할 수 있으며, 인증된 신원은 알려지지 않은 참여자의 데이터를 수용할 가능성을 줄인다. 안전한 구성(Secure Configuration), 서명되거나 검증된 소프트웨어 패키지, 통제된 패치 적용, 보호된 정책 파일 및 호스트 강화(Host Hardening) 역시 무결성에 기여한다. 따라서 미들웨어 보안은 보다 광범위한 무결성 아키텍처(Integrity Architecture)의 하나의 계층으로 평가해야 한다.

데이터 기밀성 요구사항(Data Confidentiality Requirement)은 민감한 통신에 암호화가 필요한 경우 DDS 암호학적 보호(Cryptographic Protection)를 통해 대응할 수 있다. 센서 정보, 지도, 임무 데이터, 독점 알고리즘, 운영 상태 또는 명령 트래픽은 서로 다른 기밀성 수준을 요구할 수 있다. 매핑에서는 어떤 통신 유형이 암호화되는지, 보호가 필요한 이유가 무엇인지, 기밀성 보호가 어느 지점에서 종료되는지를 문서화해야 한다. 저장 데이터(Data at Rest), 백업, 로그 및 외부 인터페이스의 보호에는 ROS 2 미들웨어 암호화를 넘어서는 추가 통제가 필요하다.

제한된 데이터 흐름(Restricted Data Flow)은 네트워크 분할 및 통제된 ROS 2 통신 관계와 연계된다. DDS 도메인, 네트워크 경계, 방화벽, 로봇별 네임스페이스, 엔클레이브 및 인가 규칙(Authorization Rule)을 사용하면 구성요소 간 불필요한 통신을 줄일 수 있다. 다중 로봇 시스템(Multi-Robot System)에서는 하나의 로봇이 다른 로봇의 내부 자원에 자동으로 접근해서는 안 된다. 규정 준수 증거는 허용된 정보 흐름이 문서화된 아키텍처 관계와 일치하며 금지된 경로가 능동적으로 테스트된다는 사실을 입증해야 한다.

이벤트에 대한 적시 대응(Timely Response to Events)은 모니터링 및 감사 기능(Audit Capability)에 의존한다. 인증 실패, 인가 거부, 예상하지 못한 참여자, 인증서 문제, 수명주기 변경, 구성 변경 및 비정상적인 네트워크 동작은 유용한 보안 증거를 생성해야 한다. ROS 2 및 DDS 이벤트는 호스트, 컨테이너, 방화벽, 게이트웨이 및 플릿 텔레메트리(Fleet Telemetry)와 연계할 수 있다. 신뢰할 수 있는 타임스탬프(Timestamp)와 보호된 중앙 집중식 수집은 사고를 재구성하고 모니터링 효과를 입증하는 능력을 향상시킨다.

자원 가용성(Resource Availability)은 미들웨어 통신 손실이 물리적 동작에 영향을 줄 수 있으므로 사이버-물리 시스템(Cyber-Physical System)에서 특히 중요하다. ROS 2 보안 평가에서는 과도한 디스커버리 활동, 반복적인 인증 시도, 비정상 트래픽, 자원 고갈(Resource Exhaustion), 네트워크 장애 및 과도한 로깅을 고려해야 한다. IEC 62443 지향 증거는 사이버 이벤트가 통신 또는 연산 자원을 위협할 때 필수적인 로봇 기능이 유지되거나 정의된 성능 저하 상태(Degraded State) 또는 안전 상태(Safe State)로 전환되는 방식을 보여주어야 한다.

보안 수준(Security Level)은 ROS 2에 직접 할당할 수 있는 단순한 설정으로 해석해서는 안 된다. IEC 62443의 보안 목표는 시스템 컨텍스트, 위협 환경, 아키텍처 및 적용되는 요구사항에 따라 달라진다. 암호화 또는 인증서를 활성화하는 것만으로 특정 보안 수준이 자동으로 확립되는 것은 아니다. 방어 가능한 매핑(Defensible Mapping)은 필요한 보안 기능을 식별하고 ROS 2가 해당 기능에 어떻게 기여하는지를 입증하며 네트워크, 플랫폼, 운영 및 조직적 통제에 남아 있는 의존성을 기록해야 한다.

안전한 개발 수명주기 요구사항(Secure Development Lifecycle Requirement)은 런타임 미들웨어 구성을 넘어선다. ROS 2 패키지와 로봇 애플리케이션은 통제된 소스 관리(Source Management), 종속성 검토(Dependency Review), 보안 테스트, 취약점 처리, 릴리스 관리 및 구성 관리를 통해 개발해야 한다. 인증서, 권한, 미들웨어 버전, 컨테이너 이미지 및 보안 정책 변경은 추적할 수 있어야 한다. 개발 환경과 운영 환경의 신뢰 인프라(Trust Infrastructure)도 분리하여 우발적이거나 비인가된 자격증명 재사용을 줄여야 한다.

알려진 취약점 관리(Known Vulnerability Management)는 배포 이후에도 보안이 유지된다는 증거를 제공한다. ROS 2 배포판, DDS 구현체, 운영체제 패키지, 라이브러리, 컨테이너, 드라이버 및 공급업체 구성요소를 인벤토리화하고 관련 CVE를 모니터링해야 한다. 위험 기반 개선(Risk-Based Remediation), 보완 통제(Compensating Control), 단계적 패치 배포(Staged Patch Deployment), 롤백 계획(Rollback Planning), 개선 이후 검증(Post-Remediation Verification)은 알려진 취약점이 로봇 수명주기 동안 누적되도록 방치되지 않고 체계적으로 처리된다는 사실을 입증한다.

암호학적 키 관리(Cryptographic Key Management)는 인증과 기밀성이 신뢰할 수 있는 자격증명에 의존하므로 여러 규정 준수 목표를 지원한다. 증거에는 안전한 키 생성, 프로비저닝(Provisioning), 저장, 접근 제한, 순환(Rotation), 갱신, 폐기(Revocation), 필요한 경우의 백업 및 파기 절차가 포함되어야 한다. 하드웨어 기반 보호(Hardware-Backed Protection)는 높은 가치의 신원을 더욱 강화할 수 있다. 키 인벤토리(Key Inventory)와 감사 기록은 비밀 키 자료를 노출하지 않으면서 어떤 자격증명이 특정 로봇, 구성요소 또는 신뢰 도메인에 속하는지를 입증해야 한다.

침투 테스트(Penetration Testing)는 문서화된 보안 통제가 적대적 행위에 견딜 수 있는지를 실질적으로 검증한다. 테스트에서는 비인가 디스커버리, 참여자 사칭, 금지된 토픽 접근, 권한이 필요한 서비스 호출, 자격증명 오용, 로봇 간 비인가 통신 및 자원 고갈을 통제된 안전 경계 내에서 시도해야 한다. 발견 사항은 개선 및 재테스트와 연결하여 규정 준수 증거가 단순히 아키텍처 문서와 구성 파일에 의존하는 것이 아니라 검증된 보안 동작(Verified Security Behavior)을 입증하도록 해야 한다.

구성 관리(Configuration Management)는 ROS 2 보안 동작이 인증서, 권한, 거버넌스 규칙(Governance Rule), 엔클레이브, 미들웨어 설정, 네트워크 정책 및 소프트웨어 버전의 조정에 의존하기 때문에 필수적이다. 하나의 구성 변경이 이전에 검증된 경계를 의도하지 않게 약화시킬 수 있다. 버전 관리되는 산출물, 동료 검토(Peer Review), 자동화된 검사, 릴리스 기준선(Release Baseline), 배포 기록은 승인된 보안 구성이 개발, 테스트 및 운영 환경 사이에서 일관성을 유지한다는 사실을 입증하는 데 도움을 준다.

증거 수집(Evidence Collection)은 감사 직전에만 수행하는 작업이 아니라 엔지니어링 과정의 일부로 설계해야 한다. 유용한 산출물에는 아키텍처 설명, 자산 인벤토리, 신뢰 모델(Trust Model), 접근 제어 정책, 인증서 기록, 키 수명주기 절차, 취약점 보고서, 패치 이력, 침투 테스트 결과, 감사 로그, 구성 기준선(Configuration Baseline), 개선 기록 등이 포함된다. 각 산출물은 관련 요구사항 및 평가 대상이 되는 특정 제품 또는 시스템 구성과 추적 가능하게 연결되어야 한다.

규정 준수 매트릭스(Compliance Matrix)는 적용 가능한 각각의 IEC 62443 요구사항을 ROS 2 구현, 지원 인프라, 증거 출처(Evidence Source), 책임자, 검증 방법 및 확인된 격차(Gap)와 연결할 수 있다. 일부 요구사항은 기술적 통제로 완전히 지원할 수 있지만 다른 요구사항은 주로 조직적 또는 수명주기 프로세스에 의존할 수 있다. 부분적인 적용 범위를 명시적으로 기록하면 하나의 미들웨어 기능만으로 광범위한 산업 사이버보안 요구사항을 충족한다고 잘못 판단하는 것을 방지할 수 있다.

격차 분석(Gap Analysis)은 ROS 2가 직접적인 통제를 제공하지 않거나 부분적인 지원만 제공하는 요구사항을 식별해야 한다. 물리적 접근 보호(Physical Access Protection), 인력 절차, 기업 신원 거버넌스(Enterprise Identity Governance), 안전한 제조(Secure Manufacturing), 복구 계획, 공급업체 관리 및 일부 네트워크 인프라 통제는 미들웨어 계층 외부에 존재한다. 이러한 격차는 ROS 2의 실패를 의미하는 것이 아니라 주변 로봇 플랫폼, 배포 환경 및 조직의 보안 프로그램에서 해결해야 하는 책임을 식별하는 것이다.

규정 준수는 시스템의 발전과도 지속적으로 동기화되어야 한다. 새로운 센서, AI 구성요소, 원격 인터페이스, DDS 구현체, 플릿 게이트웨이 또는 유지보수 워크플로를 추가하면 신뢰 경계가 변경되고 기존 가정이 더 이상 유효하지 않을 수 있다. 따라서 아키텍처, 소프트웨어, 위협 또는 운영 조건이 변경될 때 매핑을 다시 검토해야 한다. 지속적인 재평가(Continuous Reassessment)는 규정 준수 증거가 오래된 설계 시점의 상태가 아니라 실제 배포된 시스템과 일치하도록 유지한다.

전체 구조에서 IEC 62443 규정 준수 매핑(Compliance Mapping)은 ROS 2 위협 분석(Threat Analysis), SROS2 인증서 구성, DDS 인증 및 암호화, 접근 제어, 노드 신원, 감사 로깅, 키 관리, CVE 개선 및 침투 테스트 이후에 위치한다. 이러한 최종 배치를 통해 매핑 프로세스는 앞선 ROS 2 및 DDS 보안 활동에서 생성된 기술적 증거와 수명주기 증거를 통합하여 일관된 보증 프레임워크(Assurance Framework)로 구성할 수 있다.

효과적인 IEC 62443 매핑은 미들웨어 보호를 독립적인 규정 준수 수단으로 제시하는 대신 ROS 2 보안이 심층 방어(Defense in Depth)에 어떻게 참여하는지를 입증한다. 암호학적 신원(Cryptographic Identity)은 신뢰할 수 있는 참여자를 확립하고, 인가는 통신을 제한하며, 암호화와 무결성 보호는 데이터를 보호하고, 로깅은 탐지를 지원하며, 수명주기 통제는 신뢰를 유지하고, 테스트는 통제의 집행을 검증한다. 이러한 메커니즘을 플랫폼, 네트워크, 운영 및 조직적 통제와 결합하면 로봇 시스템을 위한 방어 가능한 산업 사이버보안 태세(Industrial Cybersecurity Posture)를 구축할 수 있다.
