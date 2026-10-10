**Volume 24. Robot Cybersecurity**


# Chapter 10. Physical AI Security

##  

## 10.01. Physical AI Specific Security Risks for Robots

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Physical AI introduces a security problem that differs fundamentally from conventional information technology because computation is directly connected to sensing, decision-making, and physical action. A compromised robot does not merely expose information or interrupt a digital service; manipulated intelligence can cause motion, force, collision, navigation errors, unsafe manipulation, or interaction with people and infrastructure.

The attack surface of a Physical AI robot spans sensors, perception models, multimodal foundation models, planners, learned policies, motion controllers, middleware, communication links, actuators, and cloud or fleet services. Security must therefore consider how an attacker can influence information as it moves from the physical environment through perception and reasoning toward executable actions, rather than protecting isolated software components alone.

Traditional confidentiality, integrity, and availability remain important, but Physical AI places exceptional emphasis on integrity and behavioral correctness. A robot may continue operating with apparently healthy processors and network connections while acting on corrupted observations, manipulated model outputs, or malicious instructions. Consequently, system availability cannot be interpreted as evidence that the robot remains trustworthy or physically safe.

Sensor manipulation represents one of the most distinctive risks. Cameras, LiDAR, radar, GNSS, microphones, tactile sensors, force sensors, and inertial devices provide the evidence from which autonomous behavior is constructed. Spoofed signals, adversarial visual patterns, environmental interference, replayed measurements, or compromised sensor interfaces can create a false representation of the physical world without requiring direct control of the robot computer.

Perception models extend this vulnerability because learned systems can react unpredictably to inputs intentionally designed to exploit model weaknesses. An adversarial patch placed on an object, wall, vehicle, or piece of equipment may alter classification, detection, segmentation, or pose estimation. In Physical AI, such errors propagate beyond incorrect labels because perception results can immediately influence navigation, manipulation, collision avoidance, and human interaction.

Multimodal and language-enabled robots create another security boundary between human instructions and physical execution. A robot may receive natural-language commands, visual instructions, documents, web content, or information from external agents. Prompt injection or malicious contextual information can attempt to redirect the agent, override operational constraints, disclose protected information, invoke unauthorized tools, or generate actions inconsistent with the operator\'s actual intent.

Learned policies introduce risks that are difficult to capture through conventional software vulnerability analysis. A reinforcement-learning, imitation-learning, or vision-language-action policy may contain behavioral weaknesses that are not represented by explicit program branches. Carefully selected states or observations can move the policy into poorly explored regions where actions become unstable, unsafe, or inconsistent with expected operational constraints.

Physical AI also increases the importance of model confidentiality. Foundation models, specialized perception networks, learned control policies, calibration parameters, embeddings, and adaptation data can represent substantial intellectual property and operational knowledge. Model extraction, unauthorized copying, reverse engineering, or theft from edge storage can expose capabilities that attackers may reproduce or study to identify exploitable behavioral weaknesses.

Training and adaptation pipelines create risks that persist long before deployment. Poisoned demonstrations, mislabeled sensor records, manipulated reinforcement signals, compromised synthetic data, or malicious fine-tuning samples can introduce hidden behavioral tendencies into a model. Because the resulting artifact may pass ordinary software integrity checks, cryptographic verification alone cannot demonstrate that the learned behavior itself is trustworthy.

Online learning and continual adaptation make this challenge more complex. A robot that improves from field experience must distinguish legitimate operational experience from attacker-controlled interactions. If observations, demonstrations, feedback, or reward signals can modify future behavior, the learning mechanism becomes a security-sensitive interface and requires authenticated data provenance, controlled adaptation policies, anomaly detection, and rollback capability.

Model supply chains create additional trust dependencies. Pretrained models, open-source checkpoints, third-party datasets, inference runtimes, acceleration libraries, containers, and model registries may originate from different organizations. A cryptographically valid software environment can still execute an intentionally modified or incorrectly approved AI artifact, making model identity, lineage, provenance, version control, signing, and approval essential security properties.

The boundary between AI reasoning and deterministic control requires particular protection. High-level intelligence may propose goals, trajectories, tool calls, manipulation plans, or mission changes, but unrestricted translation of these proposals into actuator commands creates unacceptable exposure. Security architecture should place independently enforceable constraints between probabilistic AI outputs and safety-critical execution, especially for mobile, aerial, legged, and manipulation systems.

A safety monitor can therefore operate as a security boundary as well as a functional safety mechanism. It can validate speed, force, workspace, collision margin, geofence, actuator state, mission authority, and other invariants independently of the AI policy. When an intelligent component produces an anomalous or unauthorized command, the monitor should reject, constrain, degrade, or terminate the action before unsafe physical consequences develop.

Identity and authorization must also extend beyond users and computers to robots, models, agents, services, sensors, and commands. A valid network connection should not automatically authorize a mission change, model replacement, or actuator-related instruction. Physical AI systems benefit from explicit trust relationships in which every critical command is associated with authenticated origin, permitted capability, operational context, and auditable execution history.

Fleet operation magnifies individual weaknesses because compromised intelligence can propagate across shared infrastructure. Robots may exchange maps, observations, learned representations, task assignments, software packages, or model updates through edge and cloud services. A malicious artifact introduced through one robot can therefore become a fleet-level threat unless synchronization, model distribution, shared learning, and command channels enforce strong isolation and provenance controls.

Physical access creates another security dimension. Robots operate in factories, warehouses, streets, hospitals, construction sites, homes, and remote environments where adversaries may approach sensors, connectors, maintenance interfaces, or storage devices. Debug ports, removable media, exposed Ethernet interfaces, diagnostic services, and maintenance credentials can bypass protections that assume the computing platform remains physically controlled.

Cybersecurity and functional safety consequently become tightly coupled. A security incident may appear first as abnormal acceleration, unexpected manipulation force, route deviation, unstable posture, incorrect obstacle response, or unauthorized mission behavior rather than as a conventional intrusion alert. Monitoring must correlate cyber telemetry with robot state, AI inference behavior, safety events, physical context, and control-system observations.

Risk assessment should therefore evaluate both the probability of compromise and the severity of resulting physical consequences. The same AI vulnerability has different significance when used in a simulation workstation, warehouse AMR, collaborative manipulator, humanoid robot, or cargo UAV. Security priorities should reflect reachable energy, operational authority, proximity to humans, environmental complexity, autonomy level, and the possibility of cascading fleet effects.

A robust Physical AI security architecture ultimately assumes that no single model, sensor, network, or software layer is inherently trustworthy. Defense must combine secure boot, signed models, protected credentials, authenticated communication, sensor consistency checks, adversarial robustness, runtime monitoring, constrained action interfaces, independent safety enforcement, logging, recovery, and controlled model lifecycle management. Volume_24_Robot_Cybersecurity

This approach fits the broader robotics software architecture in which Physical AI intersects perception, learning, foundation models, middleware, edge computing, control, fleet intelligence, and safety rather than existing as an isolated AI subsystem. Security must therefore be designed across the complete perception-to-action chain, preserving trustworthy behavior from physical observation through intelligent reasoning to the final actuator response.

피지컬 AI(Physical AI)는 연산(Computation)이 감지(Sensing), 의사결정(Decision-making), 물리적 행동(Physical Action)과 직접 연결되기 때문에 기존 정보기술(Information Technology)과 근본적으로 다른 보안 문제를 발생시킨다. 침해된 로봇은 단순히 정보를 노출하거나 디지털 서비스를 중단시키는 데 그치지 않는다. 조작된 지능(Manipulated Intelligence)은 움직임, 힘, 충돌, 내비게이션 오류, 위험한 조작 또는 사람과 기반시설에 대한 비정상적인 상호작용으로 이어질 수 있다.

피지컬 AI 로봇(Physical AI Robot)의 공격 표면(Attack Surface)은 센서(Sensor), 인식 모델(Perception Model), 멀티모달 파운데이션 모델(Multimodal Foundation Model), 플래너(Planner), 학습 정책(Learned Policy), 모션 컨트롤러(Motion Controller), 미들웨어(Middleware), 통신 링크(Communication Link), 액추에이터(Actuator), 클라우드 또는 플릿 서비스(Cloud or Fleet Service)에 걸쳐 형성된다. 따라서 보안은 개별 소프트웨어 구성요소만 보호하는 것이 아니라 물리 환경의 정보가 인식과 추론을 거쳐 실행 가능한 행동으로 전달되는 전체 과정에서 공격자가 정보를 어떻게 변조할 수 있는지를 고려해야 한다.

기존의 기밀성(Confidentiality), 무결성(Integrity), 가용성(Availability)은 여전히 중요하지만, 피지컬 AI(Physical AI)에서는 특히 무결성과 행동 정확성(Behavioral Correctness)이 중요하다. 로봇은 프로세서와 네트워크 연결이 정상적으로 동작하는 것처럼 보이면서도 손상된 관측값, 조작된 모델 출력 또는 악의적인 명령을 기반으로 행동할 수 있다. 따라서 시스템 가용성(System Availability)만으로 로봇이 신뢰 가능하거나 물리적으로 안전한 상태라고 판단해서는 안 된다.

센서 조작(Sensor Manipulation)은 피지컬 AI에서 가장 특징적인 위험 중 하나이다. 카메라(Camera), 라이다(LiDAR), 레이더(Radar), 위성항법시스템(GNSS), 마이크(Microphone), 촉각 센서(Tactile Sensor), 힘 센서(Force Sensor), 관성 장치(Inertial Device)는 자율 행동을 구성하는 근거 정보를 제공한다. 스푸핑된 신호(Spoofed Signal), 적대적 시각 패턴(Adversarial Visual Pattern), 환경 간섭(Environmental Interference), 재생된 측정값(Replayed Measurement), 침해된 센서 인터페이스(Compromised Sensor Interface)는 로봇 컴퓨터를 직접 장악하지 않고도 물리 세계에 대한 잘못된 표현을 생성할 수 있다.

인식 모델(Perception Model)은 학습 시스템이 모델의 취약점을 악용하도록 의도적으로 설계된 입력에 예측하기 어려운 방식으로 반응할 수 있기 때문에 이러한 취약성을 더욱 확대한다. 물체, 벽, 차량 또는 장비에 배치된 적대적 패치(Adversarial Patch)는 분류(Classification), 객체 탐지(Detection), 분할(Segmentation), 자세 추정(Pose Estimation)을 변경할 수 있다. 피지컬 AI에서는 이러한 오류가 잘못된 라벨에 그치지 않고 내비게이션, 조작, 충돌 회피 및 인간과의 상호작용에 즉각적인 영향을 미칠 수 있다.

멀티모달 및 언어 기반 로봇(Multimodal and Language-enabled Robot)은 인간의 명령과 물리적 실행 사이에 새로운 보안 경계(Security Boundary)를 형성한다. 로봇은 자연어 명령(Natural-language Command), 시각적 지시(Visual Instruction), 문서, 웹 콘텐츠 또는 외부 에이전트(External Agent)의 정보를 입력받을 수 있다. 프롬프트 인젝션(Prompt Injection)이나 악의적인 컨텍스트 정보(Malicious Contextual Information)는 에이전트의 행동 방향을 변경하고, 운영 제약을 우회하며, 보호된 정보를 노출하거나, 승인되지 않은 도구를 호출하고, 운영자의 실제 의도와 일치하지 않는 행동을 생성하도록 시도할 수 있다.

학습 정책(Learned Policy)은 기존 소프트웨어 취약점 분석만으로 포착하기 어려운 위험을 발생시킨다. 강화학습(Reinforcement Learning), 모방학습(Imitation Learning), 비전-언어-행동 정책(Vision-Language-Action Policy)은 명시적인 프로그램 분기문으로 표현되지 않는 행동적 취약성(Behavioral Weakness)을 포함할 수 있다. 신중하게 선택된 상태나 관측값은 정책을 충분히 탐색되지 않은 영역으로 이동시켜 행동을 불안정하거나 위험하게 만들고 예상되는 운영 제약과 불일치하게 만들 수 있다.

피지컬 AI는 모델 기밀성(Model Confidentiality)의 중요성도 증가시킨다. 파운데이션 모델(Foundation Model), 특화된 인식 네트워크(Specialized Perception Network), 학습된 제어 정책(Learned Control Policy), 보정 파라미터(Calibration Parameter), 임베딩(Embedding), 적응 데이터(Adaptation Data)는 상당한 지식재산(Intellectual Property)과 운영 지식을 포함할 수 있다. 모델 추출(Model Extraction), 무단 복제, 역공학(Reverse Engineering), 엣지 스토리지(Edge Storage)에서의 모델 탈취는 핵심 역량을 외부에 노출하고 공격자가 행동적 취약점을 분석할 수 있게 한다.

훈련 및 적응 파이프라인(Training and Adaptation Pipeline)은 실제 배포 훨씬 이전부터 지속되는 위험을 발생시킨다. 오염된 시연 데이터(Poisoned Demonstration), 잘못 라벨링된 센서 기록, 조작된 강화 신호(Reinforcement Signal), 침해된 합성 데이터(Synthetic Data), 악의적인 파인튜닝 샘플(Fine-tuning Sample)은 모델에 숨겨진 행동 성향을 삽입할 수 있다. 결과 모델이 일반적인 소프트웨어 무결성 검사를 통과할 수도 있기 때문에 암호학적 검증(Cryptographic Verification)만으로 학습된 행동 자체의 신뢰성을 입증할 수는 없다.

온라인 학습(Online Learning)과 지속적 적응(Continual Adaptation)은 이러한 문제를 더욱 복잡하게 만든다. 현장 경험을 통해 성능을 개선하는 로봇은 정상적인 운영 경험과 공격자가 통제하는 상호작용을 구분해야 한다. 관측값, 시연, 피드백 또는 보상 신호가 미래 행동을 변경할 수 있다면 학습 메커니즘 자체가 보안 민감 인터페이스(Security-sensitive Interface)가 되며, 인증된 데이터 출처 추적(Data Provenance), 통제된 적응 정책, 이상 탐지(Anomaly Detection), 롤백(Rollback) 기능이 필요하다.

모델 공급망(Model Supply Chain)은 추가적인 신뢰 의존성(Trust Dependency)을 발생시킨다. 사전학습 모델(Pretrained Model), 오픈소스 체크포인트(Open-source Checkpoint), 서드파티 데이터셋(Third-party Dataset), 추론 런타임(Inference Runtime), 가속 라이브러리(Acceleration Library), 컨테이너(Container), 모델 레지스트리(Model Registry)는 서로 다른 조직에서 제공될 수 있다. 암호학적으로 유효한 소프트웨어 환경이라도 의도적으로 변조되었거나 잘못 승인된 AI 아티팩트(AI Artifact)를 실행할 수 있으므로 모델 신원(Model Identity), 계보(Lineage), 출처(Provenance), 버전 관리, 서명(Signing), 승인 절차가 핵심 보안 속성이 된다.

AI 추론(AI Reasoning)과 결정론적 제어(Deterministic Control) 사이의 경계는 특히 강력하게 보호되어야 한다. 상위 수준의 지능은 목표, 궤적(Trajectory), 도구 호출(Tool Call), 조작 계획 또는 임무 변경을 제안할 수 있지만 이러한 결과가 제한 없이 액추에이터 명령으로 변환되면 심각한 보안 노출이 발생한다. 특히 이동형 로봇, 무인항공기, 다족 로봇 및 조작 시스템에서는 확률적 AI 출력(Probabilistic AI Output)과 안전 필수 실행(Safety-critical Execution) 사이에 독립적으로 강제할 수 있는 제약을 배치해야 한다.

따라서 안전 모니터(Safety Monitor)는 기능 안전(Functional Safety) 메커니즘인 동시에 보안 경계(Security Boundary)로 작동할 수 있다. 안전 모니터는 AI 정책과 독립적으로 속도, 힘, 작업공간, 충돌 여유(Collision Margin), 지오펜스(Geofence), 액추에이터 상태, 임무 권한 및 기타 불변 조건(Invariant)을 검증할 수 있다. 지능형 구성요소가 비정상적이거나 승인되지 않은 명령을 생성하면 위험한 물리적 결과가 발생하기 전에 해당 행동을 거부, 제한, 성능 저하 모드로 전환하거나 종료해야 한다.

신원 및 권한 부여(Identity and Authorization)는 사용자와 컴퓨터뿐만 아니라 로봇, 모델, 에이전트, 서비스, 센서 및 명령까지 확장되어야 한다. 유효한 네트워크 연결이 임무 변경, 모델 교체 또는 액추에이터 관련 명령을 자동으로 승인해서는 안 된다. 피지컬 AI 시스템은 모든 중요 명령을 인증된 출처(Authenticated Origin), 허용된 기능(Permitted Capability), 운영 컨텍스트(Operational Context), 감사 가능한 실행 이력(Auditable Execution History)과 연결하는 명시적 신뢰 관계를 구축해야 한다.

플릿 운영(Fleet Operation)은 공유 인프라를 통해 침해된 지능이 확산될 수 있기 때문에 개별 취약점의 영향을 확대한다. 로봇은 엣지 및 클라우드 서비스를 통해 지도, 관측값, 학습 표현(Learned Representation), 작업 할당, 소프트웨어 패키지 또는 모델 업데이트를 교환할 수 있다. 따라서 동기화, 모델 배포, 공유 학습 및 명령 채널에 강력한 격리(Isolation)와 출처 검증을 적용하지 않으면 하나의 로봇에 유입된 악성 아티팩트가 전체 플릿 수준의 위협으로 확대될 수 있다.

물리적 접근(Physical Access)은 또 다른 보안 차원을 형성한다. 로봇은 공장, 물류창고, 도로, 병원, 건설 현장, 가정 및 원격 환경에서 운영되므로 공격자가 센서, 커넥터, 유지보수 인터페이스 또는 저장장치에 직접 접근할 가능성이 존재한다. 디버그 포트(Debug Port), 이동식 미디어(Removable Media), 노출된 이더넷 인터페이스(Ethernet Interface), 진단 서비스(Diagnostic Service), 유지보수 자격 증명(Maintenance Credential)은 컴퓨팅 플랫폼이 물리적으로 통제된다는 가정에 기반한 보안 체계를 우회할 수 있다.

결과적으로 사이버보안(Cybersecurity)과 기능 안전(Functional Safety)은 매우 밀접하게 결합된다. 보안 사고는 기존의 침입 경보보다 비정상 가속, 예상하지 못한 조작력, 경로 이탈, 불안정한 자세, 잘못된 장애물 대응 또는 승인되지 않은 임무 행동으로 먼저 나타날 수 있다. 따라서 모니터링 시스템은 사이버 텔레메트리(Cyber Telemetry)를 로봇 상태, AI 추론 행동, 안전 이벤트, 물리적 컨텍스트 및 제어 시스템 관측값과 연계하여 분석해야 한다.

따라서 위험 평가(Risk Assessment)는 침해 가능성뿐만 아니라 그 결과로 발생할 수 있는 물리적 피해의 심각성을 함께 평가해야 한다. 동일한 AI 취약점이라도 시뮬레이션 워크스테이션(Simulation Workstation), 물류창고 자율이동로봇(AMR), 협동 매니퓰레이터(Collaborative Manipulator), 휴머노이드 로봇(Humanoid Robot), 화물 무인항공기(Cargo UAV)에 적용될 때 위험 수준은 서로 다르다. 보안 우선순위는 로봇이 발생시킬 수 있는 에너지, 운영 권한, 인간과의 근접성, 환경 복잡성, 자율성 수준 및 플릿으로 연쇄 확산될 가능성을 반영해야 한다.

견고한 피지컬 AI 보안 아키텍처(Physical AI Security Architecture)는 궁극적으로 어떠한 단일 모델, 센서, 네트워크 또는 소프트웨어 계층도 본질적으로 신뢰할 수 있다고 가정하지 않는다. 방어 체계는 보안 부팅(Secure Boot), 서명된 모델(Signed Model), 보호된 자격 증명, 인증 통신, 센서 일관성 검사, 적대적 강건성(Adversarial Robustness), 런타임 모니터링(Runtime Monitoring), 제약된 행동 인터페이스, 독립적 안전 강제(Independent Safety Enforcement), 로깅, 복구 및 통제된 모델 수명주기 관리(Model Lifecycle Management)를 통합해야 한다.

이러한 접근법은 피지컬 AI가 독립된 AI 서브시스템으로 존재하는 것이 아니라 인식(Perception), 학습(Learning), 파운데이션 모델(Foundation Model), 미들웨어(Middleware), 엣지 컴퓨팅(Edge Computing), 제어(Control), 플릿 지능(Fleet Intelligence), 안전(Safety)과 상호 연결되는 광범위한 로보틱스 소프트웨어 아키텍처(Robotics Software Architecture)와 부합한다. 따라서 보안은 물리적 관측에서 지능적 추론을 거쳐 최종 액추에이터 응답에 이르는 전체 인식-행동 체인(Perception-to-Action Chain)에 걸쳐 설계되어야 하며, 모든 단계에서 신뢰할 수 있는 행동을 유지해야 한다.

##  

## 10.02. AI Model Theft and Reverse Engineering Defense [w/Code]

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

AI models used in Physical AI systems are valuable security assets because they contain not only intellectual property but also operational knowledge about perception, decision-making, control, and task execution. A stolen robot model may reveal proprietary capabilities, training characteristics, adaptation strategies, or behavioral assumptions. Model theft must therefore be treated as a security problem that can affect confidentiality, competitive advantage, system integrity, and ultimately the safety of physical operations.

AI model theft can occur at several points across the model lifecycle, including training infrastructure, model registries, development workstations, edge storage, deployment packages, inference servers, and update channels. Attackers may obtain complete model files, intermediate checkpoints, configuration parameters, tokenizer assets, adapters, or associated metadata. In Physical AI, even partial artifacts can be valuable because they may expose architecture decisions, specialized behaviors, or information that facilitates further reverse engineering.

Reverse engineering does not always require direct access to the original model file. An attacker may analyze the robot\'s observable inputs and outputs, measure inference behavior, infer model architecture, identify preprocessing assumptions, and construct a functional approximation. Repeated queries can reveal decision boundaries, confidence characteristics, response patterns, or task-specific behaviors. This makes model extraction a distinct threat from conventional file theft and requires defenses at both the storage and inference interfaces.

Model confidentiality begins with strong protection of model artifacts at rest. Sensitive checkpoints, weights, configuration files, adapters, embeddings, and related assets should be stored using encryption and protected by access controls that distinguish development, validation, deployment, and maintenance roles. Encryption keys should not be embedded directly in application code or model packages. Where practical, keys should be protected by hardware-backed mechanisms so that possession of the storage medium alone does not provide access to the protected model.

Physical AI deployments require particular attention to edge devices because model artifacts may reside close to the robot itself. An attacker with physical access to an edge computer may attempt to remove storage, boot an alternate operating system, inspect application directories, attach debugging equipment, or copy model files during maintenance. Secure boot, measured boot, encrypted storage, hardware-backed key protection, restricted debug interfaces, and controlled maintenance procedures should therefore work together to reduce the likelihood of direct model extraction.

Model protection should also cover the execution environment. A model that is encrypted while stored but becomes completely exposed in an unprotected inference process remains vulnerable. Trusted Execution Environments (TEEs), hardware-backed isolation, process-level access controls, memory protection, and carefully restricted debugging capabilities can reduce unauthorized observation of model contents during inference. The objective is not to assume that every execution environment is perfectly secure, but to reduce the number of locations where valuable model material can be exposed.

Access control must be designed around the sensitivity of individual model assets and operations. A perception model may require different protection from a high-value generalist policy or a foundation model. Developers may need access to training checkpoints while deployment services require only inference access. Maintenance personnel may need to replace a signed model without being able to export its weights. Separating these privileges according to operational necessity reduces the consequences of compromised credentials.

Model packaging and deployment should establish a verifiable chain of trust. Each approved model artifact should have a defined identity, version, provenance, integrity measurement, and authorization status. Cryptographic signatures can allow a robot to verify that a model originates from an approved source and has not been modified after release. Signature verification should occur before model loading, and unauthorized, expired, or revoked artifacts should be rejected rather than treated as acceptable alternatives.

Confidentiality and integrity must be considered together because an attacker who obtains a model may attempt to modify it before redeployment. A stolen checkpoint could be altered to introduce a hidden behavior, weaken a safety constraint, change a perception response, or create a targeted trigger. Consequently, model protection should combine encryption for confidentiality with cryptographic hashing, digital signatures, secure loading, version control, and runtime verification for integrity.

Reverse engineering through inference APIs presents a different challenge. If a robot or cloud service provides unrestricted access to model outputs, attackers may repeatedly query the system to reconstruct aspects of the underlying model. Query rate limiting, authentication, authorization, anomaly detection, usage monitoring, and controlled output exposure can reduce this risk. The system should avoid exposing unnecessary internal information such as raw logits, detailed confidence distributions, intermediate representations, debugging traces, or hidden state.

The level of output exposure should be proportional to operational requirements. A production robot may only need a bounded decision or action recommendation rather than the complete internal representation generated by an AI model. Reducing unnecessary observability makes extraction more difficult while also limiting information that could help an attacker discover weaknesses. However, security controls must preserve legitimate diagnostic and safety requirements, particularly when engineers need sufficient information to investigate failures.

Watermarking and fingerprinting can provide additional protection for high-value models. A model owner may embed identifiable behavioral characteristics or cryptographic markers that help establish provenance when unauthorized copies are discovered. These techniques should not be considered a replacement for access control or encryption because sophisticated attackers may attempt to remove or obscure them. Their principal value is supporting ownership verification, leakage investigation, and accountability.

Model fingerprinting can also support fleet-level monitoring. If multiple robots use related models, deployment systems can maintain expected model identities and measurements for each approved version. Unexpected differences between robots can then trigger investigation. This is particularly important when models are distributed through OTA mechanisms, shared storage, cloud services, or fleet management infrastructure because a single unauthorized modification could otherwise propagate across many physical systems.

The model supply chain introduces another important attack surface. Physical AI systems may depend on pretrained models, open-source checkpoints, third-party libraries, datasets, adapters, containers, inference engines, and acceleration frameworks. Each dependency can introduce uncertainty regarding provenance and integrity. Organizations should therefore maintain an inventory of model components, record their sources and versions, verify signatures where available, and establish approval procedures before models enter production environments.

Model lineage should remain traceable throughout adaptation and deployment. When a foundation model is fine-tuned for a particular robot, the resulting artifact should retain information about its parent model, training data, adaptation process, configuration, validation results, and approval state. This lineage allows security teams to determine which deployed systems may be affected when a vulnerability or unauthorized modification is discovered in an upstream model.

Protection against theft must also account for adapters and lightweight fine-tuning artifacts. A small adapter may appear less valuable than a complete foundation model, but it can encode domain-specific behavior and may reveal how a general model was adapted for a particular application. In some systems, combining a publicly available base model with a stolen private adapter may recreate a highly valuable proprietary capability. Adapter files therefore require security controls comparable to those applied to complete model packages.

Model extraction can also occur indirectly through training and evaluation services. Shared development environments, notebooks, experiment tracking platforms, artifact repositories, and automated pipelines may retain checkpoints or intermediate outputs long after an experiment is completed. Security controls should include appropriate retention policies, repository permissions, credential protection, audit logging, and secure deletion procedures so that obsolete artifacts do not become persistent extraction targets.

Monitoring should identify behavior consistent with unauthorized model acquisition. Unusual numbers of inference requests, repeated systematic queries, access outside normal operating periods, unexpected model export attempts, abnormal administrative activity, or repeated requests designed to probe decision boundaries can indicate extraction activity. Detection should correlate application logs, identity events, model registry activity, endpoint telemetry, and network observations rather than relying on a single signal.

Incident response for suspected model theft should distinguish between exposure, extraction, modification, and confirmed distribution. If a model artifact may have been accessed, the organization should identify the affected version, determine where it was stored and who could access it, examine relevant logs, revoke compromised credentials, and evaluate whether the model must be replaced. If integrity is uncertain, the affected artifact should not continue to be trusted merely because it remains operational.

Credential and key compromise can turn a well-designed model protection mechanism into an ineffective control. Model encryption keys, signing keys, registry credentials, deployment certificates, and administrative tokens should therefore have separate protection and lifecycle management. Key rotation, revocation, hardware-backed storage, least-privilege access, and auditable administrative operations reduce the possibility that one compromised credential provides unrestricted access to the complete model lifecycle.

Security architecture should also assume that some defensive layers may eventually be bypassed. A stolen model should not automatically provide unrestricted authority over the robot. Model execution must remain separated from safety-critical control boundaries, and independently enforced constraints should limit what a compromised or modified AI component can command. This separation reduces the physical consequences of model compromise even when confidentiality or integrity protections fail.

For Physical AI, the strongest defense against AI model theft and reverse engineering is therefore layered protection across the complete lifecycle. Model confidentiality should be supported by encrypted storage and protected execution, while integrity should be supported by signatures, secure loading, provenance, version control, and registry governance. Inference interfaces should minimize unnecessary information exposure, and operational monitoring should detect systematic extraction attempts.

Ultimately, AI model security should be treated as part of the broader cybersecurity architecture of the robot rather than as an isolated intellectual-property control. The model must remain identifiable, confidential, integrity-protected, traceable, and safely constrained from development through deployment, adaptation, update, and retirement. This lifecycle approach is consistent with the Physical AI Security structure, where model theft and reverse engineering defense is positioned alongside adversarial attacks, prompt injection, AI decision manipulation, safety monitoring, training-data protection, and model registry security.

피지컬 AI 시스템(Physical AI System)에서 사용되는 AI 모델은 지식재산(Intellectual Property)뿐만 아니라 인식(Perception), 의사결정(Decision-making), 제어(Control), 작업 실행(Task Execution)에 관한 운영 지식을 포함하고 있기 때문에 중요한 보안 자산(Security Asset)이다. 탈취된 로봇 모델은 독점적인 기능, 학습 특성, 적응 전략 또는 행동상의 가정을 노출할 수 있다. 따라서 모델 탈취(Model Theft)는 기밀성(Confidentiality), 경쟁 우위(Competitive Advantage), 시스템 무결성(System Integrity), 그리고 궁극적으로 물리적 운영의 안전성(Safety)에 영향을 미칠 수 있는 보안 문제로 취급해야 한다.

AI 모델 탈취(AI Model Theft)는 모델 수명주기(Model Lifecycle)의 여러 지점에서 발생할 수 있다. 여기에는 학습 인프라(Training Infrastructure), 모델 레지스트리(Model Registry), 개발 워크스테이션(Development Workstation), 엣지 스토리지(Edge Storage), 배포 패키지(Deployment Package), 추론 서버(Inference Server), 업데이트 채널(Update Channel) 등이 포함된다. 공격자는 완전한 모델 파일, 중간 체크포인트(Checkpoint), 구성 파라미터(Configuration Parameter), 토크나이저 자산(Tokenizer Asset), 어댑터(Adapter) 또는 관련 메타데이터를 획득할 수 있다. 피지컬 AI에서는 부분적인 아티팩트(Artifact)만으로도 아키텍처 설계, 특화된 행동 또는 추가적인 역공학에 도움이 되는 정보를 노출할 수 있기 때문에 가치가 있을 수 있다.

역공학(Reverse Engineering)은 원본 모델 파일에 직접 접근하지 않고도 수행될 수 있다. 공격자는 로봇의 입력과 출력을 분석하고, 추론 행동을 측정하며, 모델 아키텍처를 추론하고, 전처리 가정을 식별하여 기능적으로 유사한 모델을 구축할 수 있다. 반복적인 질의를 통해 의사결정 경계(Decision Boundary), 신뢰도 특성(Confidence Characteristic), 응답 패턴(Response Pattern) 또는 작업별 행동(Task-specific Behavior)을 추출할 수 있다. 따라서 모델 추출(Model Extraction)은 기존의 파일 탈취와 구별되는 별도의 위협이며, 스토리지와 추론 인터페이스 모두에서 방어가 필요하다.

모델 기밀성(Model Confidentiality)은 무엇보다 저장된 모델 아티팩트(Artifact)를 강력하게 보호하는 것에서 시작된다. 민감한 체크포인트, 가중치(Weights), 구성 파일, 어댑터, 임베딩(Embedding) 및 관련 자산은 암호화(Encryption)하여 저장해야 하며, 개발(Development), 검증(Validation), 배포(Deployment), 유지보수(Maintenance) 역할을 구분하는 접근 제어(Access Control)를 적용해야 한다. 암호화 키(Encryption Key)는 애플리케이션 코드나 모델 패키지 안에 직접 포함해서는 안 된다. 가능한 경우 키는 하드웨어 기반 메커니즘(Hardware-backed Mechanism)으로 보호하여 저장 매체를 확보하는 것만으로 보호된 모델에 접근할 수 없도록 해야 한다.

피지컬 AI 배포(Physical AI Deployment)에서는 모델 아티팩트가 로봇 자체에 가까운 곳에 저장될 수 있기 때문에 엣지 장치(Edge Device)에 특별한 주의가 필요하다. 공격자가 엣지 컴퓨터에 물리적으로 접근하면 저장장치를 제거하거나, 다른 운영체제로 부팅하거나, 애플리케이션 디렉터리를 검사하거나, 디버깅 장비를 연결하거나, 유지보수 과정에서 모델 파일을 복사하려 할 수 있다. 따라서 보안 부팅(Secure Boot), 측정 부팅(Measured Boot), 암호화된 스토리지(Encrypted Storage), 하드웨어 기반 키 보호(Hardware-backed Key Protection), 제한된 디버그 인터페이스(Debug Interface), 통제된 유지보수 절차를 함께 적용하여 직접적인 모델 추출 가능성을 줄여야 한다.

모델 보호는 실행 환경(Execution Environment)에도 적용되어야 한다. 저장 상태에서는 암호화된 모델이라도 보호되지 않은 추론 프로세스(Inference Process)에서 완전히 노출된다면 여전히 취약하다. 신뢰 실행 환경(Trusted Execution Environment, TEE), 하드웨어 기반 격리(Hardware-backed Isolation), 프로세스 수준 접근 제어(Process-level Access Control), 메모리 보호(Memory Protection), 제한된 디버깅 기능은 추론 중 모델 내용에 대한 무단 관찰을 줄일 수 있다. 목적은 모든 실행 환경이 완벽하게 안전하다고 가정하는 것이 아니라 중요한 모델 정보가 노출될 수 있는 위치의 수를 줄이는 것이다.

접근 제어는 개별 모델 자산과 작업의 민감도를 기준으로 설계해야 한다. 인식 모델(Perception Model)은 고가치 범용 정책(Generalist Policy)이나 파운데이션 모델(Foundation Model)과 다른 수준의 보호가 필요할 수 있다. 개발자는 학습 체크포인트에 접근해야 할 수 있지만, 배포 서비스(Deployment Service)는 추론 기능만 필요할 수 있다. 유지보수 담당자는 서명된 모델(Signed Model)을 교체해야 할 수 있지만 모델 가중치를 외부로 추출할 수 있어서는 안 된다. 이러한 권한을 운영상 필요한 범위에 따라 분리하면 자격 증명(Credential)이 침해되었을 때의 영향을 줄일 수 있다.

모델 패키징(Model Packaging)과 배포는 검증 가능한 신뢰 체인(Chain of Trust)을 구축해야 한다. 승인된 각 모델 아티팩트에는 명확한 신원(Identity), 버전(Version), 출처(Provenance), 무결성 측정값(Integrity Measurement), 승인 상태(Authorization Status)가 정의되어야 한다. 암호학적 서명(Cryptographic Signature)을 사용하면 로봇이 모델이 승인된 출처에서 생성되었으며 배포 이후 변경되지 않았음을 검증할 수 있다. 서명 검증은 모델 로딩(Model Loading) 전에 수행되어야 하며, 승인되지 않았거나 만료되었거나 폐기된 아티팩트는 허용 가능한 대체물로 취급하지 말고 거부해야 한다.

기밀성과 무결성은 함께 고려해야 한다. 공격자가 모델을 확보한 뒤 재배포 전에 이를 수정하려 할 수 있기 때문이다. 탈취된 체크포인트는 숨겨진 행동을 삽입하거나, 안전 제약(Safety Constraint)을 약화시키거나, 인식 응답을 변경하거나, 특정 조건에서만 작동하는 트리거를 생성하도록 변조될 수 있다. 따라서 모델 보호는 기밀성을 위한 암호화와 함께 무결성을 위한 암호학적 해시(Cryptographic Hash), 디지털 서명(Digital Signature), 안전한 로딩(Secure Loading), 버전 관리(Version Control), 런타임 검증(Runtime Verification)을 결합해야 한다.

추론 API(Inference API)를 통한 역공학은 다른 형태의 문제를 제기한다. 로봇이나 클라우드 서비스가 모델 출력에 제한 없이 접근하도록 허용하면 공격자는 반복적인 질의를 통해 내부 모델의 특성을 재구성할 수 있다. 질의 속도 제한(Query Rate Limiting), 인증(Authentication), 권한 부여(Authorization), 이상 탐지(Anomaly Detection), 사용량 모니터링(Usage Monitoring), 출력 정보 제한을 적용하면 이러한 위험을 줄일 수 있다. 시스템은 원시 로짓(Raw Logit), 상세 신뢰도 분포(Detailed Confidence Distribution), 중간 표현(Intermediate Representation), 디버깅 추적(Debugging Trace), 은닉 상태(Hidden State)와 같이 불필요한 내부 정보를 외부에 노출하지 않아야 한다.

출력 정보의 노출 수준은 운영상의 요구사항에 비례해야 한다. 실제 운영 로봇은 AI 모델이 생성하는 완전한 내부 표현보다는 제한된 의사결정이나 행동 권고만 필요할 수 있다. 불필요한 관찰 가능성(Observability)을 줄이면 모델 추출을 어렵게 만들면서 공격자가 취약점을 발견하는 데 활용할 수 있는 정보도 제한할 수 있다. 다만 보안 제어(Security Control)는 특히 엔지니어가 장애를 조사해야 하는 경우 정당한 진단 및 안전 요구사항을 충분히 지원해야 한다.

워터마킹(Watermarking)과 핑거프린팅(Fingerprinting)은 고가치 모델에 추가적인 보호 기능을 제공할 수 있다. 모델 소유자는 식별 가능한 행동 특성이나 암호학적 마커(Cryptographic Marker)를 모델에 삽입하여 무단 복제본이 발견되었을 때 출처(Provenance)를 확인할 수 있다. 그러나 이러한 기술은 접근 제어나 암호화를 대체하는 수단으로 간주해서는 안 된다. 정교한 공격자는 이를 제거하거나 숨기려 할 수 있기 때문이다. 주요 가치는 소유권 검증(Ownership Verification), 정보 유출 조사(Leakage Investigation), 책임 추적(Accountability)을 지원하는 데 있다.

모델 핑거프린팅은 플릿 수준 모니터링(Fleet-level Monitoring)에도 활용할 수 있다. 여러 로봇이 관련된 모델을 사용하는 경우 배포 시스템은 승인된 각 모델 버전의 예상 신원과 측정값을 관리할 수 있다. 이후 로봇 간 예상하지 못한 차이가 발견되면 조사를 시작할 수 있다. 이는 OTA 메커니즘, 공유 스토리지, 클라우드 서비스 또는 플릿 관리 인프라를 통해 모델이 배포되는 환경에서 특히 중요하다. 그렇지 않으면 하나의 무단 변경이 다수의 물리적 시스템으로 확산될 수 있다.

모델 공급망(Model Supply Chain)은 또 다른 공격 표면(Attack Surface)을 형성한다. 피지컬 AI 시스템은 사전학습 모델(Pretrained Model), 오픈소스 체크포인트(Open-source Checkpoint), 서드파티 라이브러리(Third-party Library), 데이터셋(Dataset), 어댑터, 컨테이너(Container), 추론 엔진(Inference Engine), 가속 프레임워크(Acceleration Framework)에 의존할 수 있다. 각 의존성은 출처와 무결성에 대한 불확실성을 발생시킬 수 있다. 따라서 조직은 모델 구성요소의 목록을 유지하고 출처와 버전을 기록하며 가능한 경우 서명을 검증하고 모델이 운영 환경에 들어가기 전에 승인 절차를 마련해야 한다.

모델 계보(Model Lineage)는 적응(Adaptation)과 배포 전 과정에서 추적 가능해야 한다. 파운데이션 모델을 특정 로봇에 맞게 파인튜닝(Fine-tuning)한 경우 결과 아티팩트는 부모 모델(Parent Model), 학습 데이터(Training Data), 적응 과정, 구성, 검증 결과, 승인 상태에 관한 정보를 유지해야 한다. 이러한 계보를 통해 보안팀은 상위 모델에서 취약점이나 무단 변경이 발견되었을 때 어떤 배포 시스템이 영향을 받을 수 있는지 파악할 수 있다.

탈취 방어는 어댑터(Adapter)와 경량 파인튜닝 아티팩트(Lightweight Fine-tuning Artifact)도 고려해야 한다. 작은 어댑터는 완전한 파운데이션 모델보다 가치가 낮아 보일 수 있지만, 도메인 특화 행동(Domain-specific Behavior)을 포함하고 특정 애플리케이션에 범용 모델이 어떻게 적응되었는지를 노출할 수 있다. 일부 시스템에서는 공개된 기반 모델과 탈취된 비공개 어댑터를 결합하면 매우 가치 있는 독점 기능을 재현할 수 있다. 따라서 어댑터 파일도 완전한 모델 패키지에 적용하는 것과 유사한 수준의 보안 제어가 필요하다.

모델 추출은 학습 및 평가 서비스(Training and Evaluation Service)를 통해서도 간접적으로 발생할 수 있다. 공유 개발 환경, 노트북(Notebook), 실험 추적 플랫폼(Experiment Tracking Platform), 아티팩트 저장소(Artifact Repository), 자동화 파이프라인은 실험이 종료된 후에도 체크포인트나 중간 결과를 보관할 수 있다. 따라서 보안 제어에는 적절한 보존 정책(Retention Policy), 저장소 권한, 자격 증명 보호, 감사 로깅(Audit Logging), 안전한 삭제 절차가 포함되어야 하며, 오래된 아티팩트가 지속적인 탈취 대상이 되지 않도록 해야 한다.

모니터링 시스템은 무단 모델 획득과 일치하는 행동을 식별해야 한다. 비정상적으로 많은 추론 요청, 반복적이고 체계적인 질의, 정상적인 운영 시간 외의 접근, 예상하지 못한 모델 내보내기 시도, 비정상적인 관리자 활동, 의사결정 경계를 탐색하도록 설계된 반복 질의는 모델 추출 활동을 나타낼 수 있다. 탐지는 단일 신호에 의존하기보다 애플리케이션 로그(Application Log), 신원 이벤트(Identity Event), 모델 레지스트리 활동, 엔드포인트 텔레메트리(Endpoint Telemetry), 네트워크 관측 정보를 상호 연계해야 한다.

모델 탈취가 의심되는 경우의 사고 대응(Incident Response)은 노출(Exposure), 추출(Extraction), 변조(Modification), 확인된 배포(Confirmed Distribution)를 구분해야 한다. 모델 아티팩트에 접근했을 가능성이 있다면 조직은 영향을 받은 버전을 식별하고 해당 모델이 어디에 저장되어 있었으며 누가 접근할 수 있었는지 확인하고 관련 로그를 분석하며 침해된 자격 증명을 폐기하고 모델을 교체해야 하는지 평가해야 한다. 무결성이 확실하지 않다면 모델이 계속 정상적으로 작동한다는 이유만으로 해당 아티팩트를 신뢰해서는 안 된다.

자격 증명과 키가 침해되면 잘 설계된 모델 보호 메커니즘도 효과를 잃을 수 있다. 따라서 모델 암호화 키, 서명 키(Signing Key), 레지스트리 자격 증명, 배포 인증서(Deployment Certificate), 관리자 토큰은 서로 분리하여 보호하고 수명주기를 관리해야 한다. 키 교체(Key Rotation), 폐기(Revocation), 하드웨어 기반 저장(Hardware-backed Storage), 최소 권한 접근(Least-privilege Access), 감사 가능한 관리 작업은 하나의 침해된 자격 증명이 전체 모델 수명주기에 제한 없이 접근하는 것을 방지한다.

보안 아키텍처는 일부 방어 계층이 결국 우회될 가능성도 고려해야 한다. 탈취된 모델이 로봇에 대한 무제한 권한을 자동으로 제공해서는 안 된다. 모델 실행은 안전 필수 제어 경계(Safety-critical Control Boundary)와 분리되어야 하며 독립적으로 강제되는 제약 조건이 침해되거나 변조된 AI 구성요소가 실행할 수 있는 명령의 범위를 제한해야 한다. 이러한 분리는 기밀성 또는 무결성 보호가 실패하더라도 모델 침해로 인한 물리적 결과를 줄일 수 있다.

피지컬 AI에서 AI 모델 탈취와 역공학에 대한 가장 강력한 방어는 전체 수명주기에 걸친 다층 보호(Layered Protection)이다. 모델 기밀성은 암호화된 저장과 보호된 실행 환경으로 지원하고, 무결성은 서명, 안전한 로딩, 출처 추적(Provenance), 버전 관리, 레지스트리 거버넌스(Registry Governance)로 강화해야 한다. 추론 인터페이스는 불필요한 정보 노출을 최소화해야 하며 운영 모니터링은 체계적인 모델 추출 시도를 탐지해야 한다.

궁극적으로 AI 모델 보안(AI Model Security)은 독립적인 지식재산 보호 수단이 아니라 로봇의 전체 사이버보안 아키텍처(Cybersecurity Architecture)의 일부로 취급해야 한다. 모델은 개발(Development)에서 배포(Deployment), 적응(Adaptation), 업데이트(Update), 폐기(Retirement)에 이르는 전체 수명주기 동안 식별 가능하고, 기밀성이 유지되며, 무결성이 보호되고, 추적 가능하며, 안전하게 제약되어야 한다. 이러한 수명주기 접근법(Lifecycle Approach)은 모델 탈취 및 역공학 방어가 적대적 공격(Adversarial Attack), 프롬프트 인젝션(Prompt Injection), AI 의사결정 조작(AI Decision Manipulation), 안전 모니터링(Safety Monitoring), 학습 데이터 보호(Training Data Protection), 모델 레지스트리 보안(Model Registry Security)과 함께 배치된 피지컬 AI 보안 구조와 일치한다.

##  

## 10.03. Adversarial Patch Attack on Robot Vision [w/Code]

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Adversarial patch attacks represent a distinctive threat to robot vision because they manipulate the visual evidence used by an autonomous system to understand its environment. An adversarial patch is a deliberately designed visual pattern that causes a vision model to misclassify, ignore, or incorrectly localize an object. Unlike ordinary sensor noise, the attack is constructed to exploit weaknesses in learned perception and can remain effective even when the robot operates in a complex physical environment.

The security impact becomes significant when visual perception directly influences physical behavior. A robot may use camera observations for object detection, localization, obstacle recognition, navigation, grasp selection, human detection, or scene understanding. If an adversarial patch causes an object to disappear from perception or changes its semantic identity, downstream planning and control components may receive an incorrect representation of the environment and generate inappropriate physical actions.

A major characteristic of adversarial patches is that they can be placed directly into the robot\'s physical environment. An attacker does not necessarily need network access, administrative credentials, or direct access to the robot computer. A malicious visual pattern attached to a sign, package, vehicle, floor surface, safety marker, or other visible object may influence perception when the robot\'s camera observes it. This creates a cyber-physical attack path from the physical environment into the AI inference pipeline.

The attack can target different stages of the perception pipeline. A patch may interfere with object detection, classification, segmentation, pose estimation, tracking, or visual localization. In a multimodal Physical AI system, the manipulated visual information may then be combined with language or other sensor inputs and influence a higher-level reasoning process. The resulting failure can therefore propagate across multiple AI components rather than remaining isolated within the camera perception module.

Physical conditions also affect adversarial patch behavior. Changes in viewing distance, camera angle, illumination, shadows, motion blur, occlusion, and object deformation can alter attack effectiveness. A security evaluation should therefore avoid testing only ideal laboratory images. Physical AI security requires testing under representative operational conditions to determine whether an attack remains effective when the robot moves, the camera viewpoint changes, or the environment becomes dynamically populated.

The relationship between perception confidence and physical behavior is particularly important. A model may produce an apparently valid prediction even when the visual evidence has been maliciously manipulated. If downstream systems interpret the prediction as trustworthy without considering uncertainty or contextual consistency, an attacker can exploit the gap between statistical confidence and actual environmental correctness. Confidence values alone should therefore not be treated as sufficient evidence that perception remains trustworthy.

Sensor fusion can provide an important defensive mechanism against visual attacks. Camera observations may be compared with LiDAR, radar, depth, inertial, tactile, or other independent measurements. When different sensing modalities produce inconsistent representations of the same physical situation, the system can reduce confidence, request additional observations, enter a degraded mode, or prevent the affected perception result from directly controlling a safety-critical action.

Temporal consistency provides another useful defense. A legitimate physical object normally produces observations that evolve according to the robot\'s motion and the dynamics of the environment. A sudden semantic change, disappearance, or implausible object transition can therefore indicate perception manipulation. Tracking systems can compare current observations with previous states and identify inconsistencies that would be difficult to explain through normal physical motion.

Spatial and semantic context should also be incorporated into detection. A robot can evaluate whether an object interpretation is consistent with its location, surrounding geometry, expected size, motion, and relationships with other objects. For example, if a perception model reports an object category that is inconsistent with depth measurements or scene geometry, the system should avoid blindly accepting the classification. Contextual validation reduces dependence on a single learned prediction.

Adversarial training can improve robustness by exposing models to representative manipulated inputs during development. Training data may include transformed, occluded, distorted, or physically captured adversarial patterns so that the model learns more stable representations. However, adversarial training should not be regarded as a universal solution because attackers may discover patterns outside the training distribution. Robustness must therefore be combined with runtime monitoring and independent safety mechanisms.

Certified robustness provides a stronger form of assurance for selected perception tasks. Instead of relying only on empirical testing, formal or mathematically bounded methods can establish that a model\'s prediction remains stable within a defined perturbation range. Such guarantees are valuable for safety-critical applications, but their practical applicability depends on the model architecture, input representation, computational requirements, and threat model being considered.

Input preprocessing can provide an additional defensive layer, although it must be evaluated carefully. Image transformations, normalization, resizing, feature processing, and consistency checks may reduce the effectiveness of particular attack patterns. However, preprocessing can also degrade legitimate visual information or fail against adaptive adversaries. It should therefore be treated as one component of a layered defense rather than as a standalone protection mechanism.

Runtime anomaly detection is especially important for deployed robots. The system can monitor changes in perception confidence, object persistence, spatial relationships, sensor agreement, and model outputs to identify behavior inconsistent with normal operation. When anomalous evidence is detected, the robot can trigger additional sensing, reduce operational speed, restrict certain actions, or transition to a safe behavior. The appropriate response should reflect the physical consequences associated with the affected perception function.

Security monitoring should also preserve evidence of suspicious perception events. Relevant information may include timestamps, sensor identifiers, model versions, perception outputs, confidence values, sensor-fusion results, environmental context, and safety responses. These records can help determine whether an apparent perception failure resulted from ordinary environmental conditions, model limitations, sensor malfunction, or deliberate manipulation.

The defense strategy should account for the possibility that an attacker repeatedly tests the robot against different physical patterns. Repeated encounters with unusual visual structures, systematic changes in perception output, or recurring inconsistencies between camera and independent sensors may indicate an adversarial campaign rather than isolated environmental noise. Fleet-level monitoring can help identify patterns that are difficult to recognize from a single robot.

Model updates must also be controlled because improvements to perception robustness can introduce new behaviors. Each updated model should be evaluated against established adversarial test suites, representative physical scenarios, sensor-fusion conditions, and safety constraints before deployment. Signed model packages and controlled deployment processes help ensure that a security improvement is not replaced by an unauthorized or unvalidated perception model.

The consequences of adversarial visual manipulation should ultimately be evaluated at the physical action layer. A perception error that merely changes a noncritical label may have limited impact, while the same error in a collision-avoidance, grasping, navigation, or human-detection function may create a serious hazard. Security assessment should therefore trace the complete path from manipulated visual input through perception, reasoning, planning, and control to the resulting physical behavior.

A robust architecture should avoid allowing a single camera prediction to directly determine safety-critical action. Independent safety monitors can enforce constraints on velocity, workspace, collision distance, actuator behavior, geofencing, and other operational invariants. If visual perception becomes unreliable, these controls can limit the physical consequences even when the underlying AI model fails to recognize the adversarial manipulation.

Adversarial patch defense should therefore be understood as a layered cyber-physical security problem rather than simply an image-classification problem. Protection should combine robust perception models, adversarial evaluation, sensor fusion, temporal and spatial consistency checks, runtime anomaly detection, controlled model updates, audit logging, and independent safety enforcement. The objective is not to guarantee that every malicious visual input will be recognized, but to prevent a manipulated perception result from becoming an uncontrolled physical consequence.

Within the Physical AI Security structure, adversarial patch attacks form a distinct security topic alongside AI model theft, prompt injection, AI decision manipulation, certified robustness, safety monitoring, training-data protection, and model registry security. Volume_24_Robot_Cybersecurity This positioning emphasizes that robot vision security must be considered as part of the complete Physical AI security lifecycle, connecting perception integrity with AI reasoning, physical action, monitoring, and recovery.

적대적 패치 공격(Adversarial Patch Attack)은 자율 시스템이 주변 환경을 이해하기 위해 사용하는 시각적 증거(Visual Evidence)를 조작하기 때문에 로봇 비전(Robot Vision)에 독특한 위협을 제기한다. 적대적 패치(Adversarial Patch)는 비전 모델(Vision Model)이 객체를 잘못 분류하거나, 무시하거나, 잘못된 위치에 배치하도록 의도적으로 설계된 시각적 패턴(Visual Pattern)이다. 일반적인 센서 잡음(Sensor Noise)과 달리 이러한 공격은 학습된 인식(Perception)의 약점을 악용하도록 구성되며, 로봇이 복잡한 물리적 환경에서 작동하는 상황에서도 효과를 유지할 수 있다.

보안 영향은 시각적 인식(Visual Perception)이 물리적 행동(Physical Behavior)에 직접 영향을 미칠 때 더욱 중요해진다. 로봇은 카메라 관측(Camera Observation)을 객체 탐지(Object Detection), 위치 추정(Localization), 장애물 인식(Obstacle Recognition), 내비게이션(Navigation), 파지 선택(Grasp Selection), 사람 탐지(Human Detection), 장면 이해(Scene Understanding)에 사용할 수 있다. 적대적 패치가 객체를 인식에서 사라지게 하거나 의미적 정체성(Semantic Identity)을 변경하면, 이후의 계획 및 제어 구성요소(Planning and Control Components)는 환경에 대한 잘못된 표현을 입력받아 부적절한 물리적 행동을 생성할 수 있다.

적대적 패치의 주요 특징은 로봇의 물리적 환경에 직접 배치될 수 있다는 점이다. 공격자는 반드시 네트워크 접근 권한, 관리자 자격 증명(Administrative Credential), 또는 로봇 컴퓨터에 대한 직접적인 접근 권한을 가질 필요가 없다. 표지판(Sign), 포장물(Package), 차량(Vehicle), 바닥 표면(Floor Surface), 안전 표시(Safety Marker) 또는 기타 가시적인 물체에 부착된 악의적인 시각 패턴(Malicious Visual Pattern)이 로봇의 카메라에 포착될 때 인식에 영향을 줄 수 있다. 이는 물리적 환경에서 AI 추론 파이프라인(AI Inference Pipeline)으로 이어지는 사이버-물리적 공격 경로(Cyber-Physical Attack Path)를 형성한다.

공격은 인식 파이프라인(Perception Pipeline)의 여러 단계에서 발생할 수 있다. 패치는 객체 탐지(Object Detection), 분류(Classification), 분할(Segmentation), 자세 추정(Pose Estimation), 추적(Tracking), 시각적 위치 추정(Visual Localization)을 방해할 수 있다. 멀티모달 피지컬 AI 시스템(Multimodal Physical AI System)에서는 조작된 시각 정보가 언어 또는 다른 센서 입력과 결합되어 상위 수준의 추론 과정에 영향을 줄 수 있다. 따라서 발생한 장애는 카메라 인식 모듈에 국한되지 않고 여러 AI 구성요소로 확산될 수 있다.

물리적 조건도 적대적 패치의 동작에 영향을 미친다. 관측 거리(Viewing Distance), 카메라 각도(Camera Angle), 조명(Illumination), 그림자(Shadow), 모션 블러(Motion Blur), 가림(Occlusion), 객체 변형(Object Deformation)의 변화는 공격의 효과를 변경할 수 있다. 따라서 보안 평가는 이상적인 실험실 이미지에 대한 테스트만으로 구성되어서는 안 된다. 피지컬 AI 보안(Physical AI Security)은 로봇이 이동하고, 카메라 시점이 변화하며, 환경에 동적으로 움직이는 객체가 존재하는 실제 운영 조건에서 공격이 지속적으로 효과적인지를 평가해야 한다.

인식 신뢰도(Perception Confidence)와 물리적 행동 사이의 관계는 특히 중요하다. 악의적으로 조작된 시각적 증거가 존재하더라도 모델은 겉보기에는 유효한 예측을 생성할 수 있다. 후속 시스템이 불확실성(Uncertainty)이나 상황적 일관성(Contextual Consistency)을 고려하지 않고 해당 예측을 신뢰할 수 있는 것으로 해석한다면, 공격자는 통계적 신뢰도와 실제 환경의 정확성 사이에 존재하는 차이를 악용할 수 있다. 따라서 신뢰도 값만으로 인식이 신뢰할 수 있는 상태라고 판단해서는 안 된다.

센서 융합(Sensor Fusion)은 시각적 공격에 대한 중요한 방어 메커니즘을 제공할 수 있다. 카메라 관측값은 라이다(LiDAR), 레이더(Radar), 깊이(Depth), 관성(Inertial), 촉각(Tactile) 또는 기타 독립적인 측정값과 비교할 수 있다. 서로 다른 센서 모달리티가 동일한 물리적 상황에 대해 서로 일치하지 않는 표현을 생성하면 시스템은 신뢰도를 낮추거나, 추가 관측을 요청하거나, 성능 저하 모드(Degraded Mode)에 진입하거나, 영향을 받은 인식 결과가 안전 필수 행동(Safety-critical Action)을 직접 제어하지 못하도록 할 수 있다.

시간적 일관성(Temporal Consistency)은 또 다른 유용한 방어 수단이다. 정상적인 물리적 객체는 일반적으로 로봇의 움직임과 환경의 동역학에 따라 관측값이 변화한다. 따라서 갑작스러운 의미적 변화(Semantic Change), 객체의 소실, 또는 물리적으로 설명하기 어려운 객체 상태 변화는 인식 조작을 나타낼 수 있다. 추적 시스템(Tracking System)은 현재 관측값을 이전 상태와 비교하여 정상적인 물리적 움직임으로 설명하기 어려운 불일치를 식별할 수 있다.

공간적 및 의미적 컨텍스트(Spatial and Semantic Context)도 탐지에 통합해야 한다. 로봇은 객체의 해석이 객체의 위치, 주변 형상, 예상 크기, 움직임 및 다른 객체와의 관계와 일치하는지를 평가할 수 있다. 예를 들어 인식 모델이 깊이 측정값이나 장면 형상(Scene Geometry)과 일치하지 않는 객체 범주를 보고한다면 시스템은 해당 분류를 무조건 받아들여서는 안 된다. 컨텍스트 검증(Contextual Validation)은 단일 학습 예측(Learned Prediction)에 대한 의존도를 줄인다.

적대적 학습(Adversarial Training)은 개발 과정에서 조작된 입력을 모델에 노출함으로써 견고성을 향상시킬 수 있다. 학습 데이터에는 변형된 패턴, 가려진 패턴, 왜곡된 패턴 또는 실제 환경에서 촬영된 적대적 패턴을 포함시켜 모델이 더욱 안정적인 표현을 학습하도록 할 수 있다. 그러나 공격자가 학습 분포(Training Distribution) 밖의 패턴을 발견할 수 있기 때문에 적대적 학습을 보편적인 해결책으로 간주해서는 안 된다. 견고성은 런타임 모니터링(Runtime Monitoring) 및 독립적인 안전 메커니즘과 결합되어야 한다.

인증된 견고성(Certified Robustness)은 특정 인식 작업에 대해 보다 강력한 형태의 보증을 제공할 수 있다. 단순한 경험적 테스트(Empirical Testing)에만 의존하는 대신 형식적 또는 수학적으로 제한된 방법을 사용하여 정의된 섭동 범위(Perturbation Range) 내에서 모델의 예측이 안정적으로 유지되는지를 입증할 수 있다. 이러한 보증은 안전 필수 애플리케이션에서 가치가 있지만, 실제 적용 가능성은 모델 아키텍처, 입력 표현(Input Representation), 계산 요구사항 및 고려되는 위협 모델(Threat Model)에 따라 달라진다.

입력 전처리(Input Preprocessing)는 추가적인 방어 계층을 제공할 수 있지만 신중하게 평가해야 한다. 이미지 변환(Image Transformation), 정규화(Normalization), 크기 조정(Resizing), 특징 처리(Feature Processing), 일관성 검사는 특정 공격 패턴의 효과를 줄일 수 있다. 그러나 전처리는 정상적인 시각 정보를 저하시킬 수도 있고 적응형 공격자(Adaptive Adversary)에게는 효과가 없을 수도 있다. 따라서 전처리는 독립적인 보호 수단이 아니라 다층 방어(Layered Defense)의 하나의 구성요소로 취급해야 한다.

런타임 이상 탐지(Runtime Anomaly Detection)는 배포된 로봇에서 특히 중요하다. 시스템은 인식 신뢰도, 객체 지속성(Object Persistence), 공간적 관계, 센서 간 일치성, 모델 출력의 변화를 모니터링하여 정상적인 운영과 일치하지 않는 행동을 식별할 수 있다. 비정상적인 증거가 탐지되면 로봇은 추가 센싱을 수행하거나, 운영 속도를 낮추거나, 특정 행동을 제한하거나, 안전 행동(Safe Behavior)으로 전환할 수 있다. 적절한 대응 수준은 영향을 받은 인식 기능과 관련된 물리적 결과를 고려하여 결정해야 한다.

보안 모니터링(Security Monitoring)은 의심스러운 인식 이벤트에 대한 증거도 보존해야 한다. 관련 정보에는 타임스탬프(Timestamp), 센서 식별자(Sensor Identifier), 모델 버전(Model Version), 인식 출력(Perception Output), 신뢰도 값, 센서 융합 결과, 환경 컨텍스트 및 안전 대응(Safety Response)이 포함될 수 있다. 이러한 기록은 인식 장애가 일반적인 환경 조건, 모델의 한계, 센서 고장 또는 의도적인 조작으로 인해 발생했는지를 판단하는 데 도움이 된다.

방어 전략은 공격자가 다양한 물리적 패턴을 사용하여 로봇을 반복적으로 시험할 가능성도 고려해야 한다. 비정상적인 시각 구조와의 반복적인 접촉, 인식 출력의 체계적인 변화, 또는 카메라와 독립적인 센서 사이에서 반복적으로 발생하는 불일치는 단순한 환경 잡음이 아니라 적대적 공격 캠페인(Adversarial Campaign)을 나타낼 수 있다. 플릿 수준 모니터링(Fleet-level Monitoring)은 단일 로봇에서는 인식하기 어려운 패턴을 식별하는 데 도움이 될 수 있다.

모델 업데이트(Model Update)도 통제해야 한다. 인식 견고성을 개선하는 변경이 새로운 행동을 발생시킬 수 있기 때문이다. 각각의 업데이트된 모델은 배포 전에 기존의 적대적 테스트 스위트(Adversarial Test Suite), 대표적인 물리적 시나리오, 센서 융합 조건 및 안전 제약(Safety Constraint)에 대해 평가해야 한다. 서명된 모델 패키지(Signed Model Package)와 통제된 배포 프로세스(Controlled Deployment Process)는 보안 개선 모델이 승인되지 않았거나 검증되지 않은 인식 모델로 대체되는 것을 방지하는 데 도움이 된다.

적대적 시각 조작의 결과는 궁극적으로 물리적 행동 계층(Physical Action Layer)에서 평가해야 한다. 중요하지 않은 라벨 하나를 변경하는 인식 오류는 영향이 제한적일 수 있지만, 동일한 오류가 충돌 회피(Collision Avoidance), 파지(Grasping), 내비게이션(Navigation), 사람 탐지(Human Detection) 기능에서 발생하면 심각한 위험을 초래할 수 있다. 따라서 보안 평가는 조작된 시각 입력에서 인식, 추론, 계획 및 제어를 거쳐 최종 물리적 행동에 이르는 전체 경로를 추적해야 한다.

견고한 아키텍처는 단일 카메라 예측이 안전 필수 행동을 직접 결정하도록 허용해서는 안 된다. 독립적인 안전 모니터(Independent Safety Monitor)는 속도, 작업공간(Workspace), 충돌 거리(Collision Distance), 액추에이터 행동(Actuator Behavior), 지오펜싱(Geofencing) 및 기타 운영 불변조건(Operational Invariant)을 강제할 수 있다. 시각적 인식의 신뢰성이 떨어지더라도 이러한 제어는 기본 AI 모델이 적대적 조작을 인식하지 못하는 경우에도 물리적 영향을 제한할 수 있다.

따라서 적대적 패치 방어(Adversarial Patch Defense)는 단순한 이미지 분류(Image Classification) 문제가 아니라 다층적인 사이버-물리 보안(Cyber-Physical Security) 문제로 이해해야 한다. 보호 체계는 견고한 인식 모델, 적대적 평가, 센서 융합, 시간적 및 공간적 일관성 검사, 런타임 이상 탐지, 통제된 모델 업데이트, 감사 로깅(Audit Logging), 독립적인 안전 강제를 결합해야 한다. 목표는 모든 악의적인 시각 입력을 반드시 탐지할 수 있다고 보장하는 것이 아니라, 조작된 인식 결과가 통제되지 않은 물리적 결과로 이어지는 것을 방지하는 것이다.

피지컬 AI 보안(Physical AI Security) 구조에서 적대적 패치 공격은 AI 모델 탈취(AI Model Theft), 프롬프트 인젝션(Prompt Injection), AI 의사결정 조작(AI Decision Manipulation), 인증된 견고성(Certified Robustness), 안전 모니터링(Safety Monitoring), 학습 데이터 보호(Training Data Protection), 모델 레지스트리 보안(Model Registry Security)과 함께 독립적인 보안 주제로 구성된다. 이러한 구성은 로봇 비전 보안(Robot Vision Security)이 전체 피지컬 AI 보안 수명주기(Physical AI Security Lifecycle)의 일부로 고려되어야 하며, 인식 무결성(Perception Integrity)을 AI 추론, 물리적 행동, 모니터링 및 복구와 연결해야 한다는 점을 강조한다.

##  

## 10.04. Prompt Injection Attack on LLM Robot Agent [w/Code]

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Prompt injection attacks create a distinctive security risk when a Large Language Model (LLM) is used as a robot agent that can interpret instructions and invoke tools or control physical functions. Unlike conventional software input attacks, malicious instructions may be embedded in natural-language commands, documents, web content, images, sensor-derived descriptions, or other contextual information. If the agent treats untrusted content as authoritative instructions, an attacker may influence decisions without directly compromising the underlying robot software.

The risk becomes more significant when an LLM robot agent has access to tools, sensors, navigation functions, manipulation capabilities, fleet services, or external information sources. A compromised conversational context can potentially influence which tools are selected, what parameters are supplied, or how an operational objective is interpreted. Because these decisions can eventually reach physical actuators, prompt injection must be considered a cyber-physical security threat rather than merely an information-processing problem.

Prompt injection may occur through both direct and indirect channels. A direct attack can be placed in a command provided by a user, while an indirect attack may be embedded in a webpage, document, object label, visual scene, message, or other data that the robot retrieves during task execution. The agent may encounter the malicious instruction while performing a legitimate task and incorrectly treat it as part of the trusted instruction context.

The central security problem is the absence of a reliable distinction between instructions and data. An LLM can process both using the same language representation, while the security architecture must assign different trust levels to each source. A robot agent should therefore not assume that every sentence appearing in its context represents an authorized command. User intent, system policy, retrieved information, sensor interpretation, and third-party content should remain logically distinguishable.

System instructions and operational policies should have a clearly defined authority hierarchy. Higher-trust policies should establish boundaries that lower-trust content cannot override. User requests may define legitimate objectives, while external documents or retrieved web content should normally be treated as untrusted information. The agent should not allow an instruction discovered inside untrusted content to silently redefine safety rules, authorization requirements, mission constraints, or access privileges.

Tool access is one of the most important control points. An LLM should not receive unrestricted authority simply because it can generate a valid tool call. Tools that affect navigation, manipulation, configuration, communication, model management, or physical motion should require explicit authorization and enforce their own input constraints. The tool interface should validate parameters independently rather than assuming that the language model has correctly interpreted the intended operation.

Privilege separation can reduce the consequences of successful prompt injection. A robot agent may require broad reasoning capabilities while only a restricted subset of actions should be available under particular operating conditions. Read-only information retrieval, mission planning, actuator control, firmware management, and administrative functions should therefore be separated according to their risk. A compromised reasoning context should not automatically provide access to higher-privilege operations.

Natural-language instructions should also be converted into structured representations before reaching safety-critical functions. Instead of allowing free-form generated text to directly control a robot, an intermediate policy layer can translate an approved intent into constrained commands. This layer can verify permitted actions, operational parameters, workspace boundaries, speed limits, and other requirements before execution.

External information sources require explicit trust boundaries. A robot may retrieve documents, maps, web pages, task descriptions, object metadata, or messages while performing an assigned task. Such information can contain content designed to influence the agent. Retrieval systems should therefore preserve source identity and trust classification so that the agent can distinguish authoritative operational information from untrusted content encountered during execution.

Multimodal agents create additional prompt injection pathways because malicious instructions may be presented through images, signs, text displayed on screens, audio, or objects in the physical environment. A vision-language model may interpret text visible in the environment as meaningful instructions even when that text was never authorized by the operator. Consequently, perception-derived language should not automatically receive the same authority as authenticated mission commands.

Context management is another important defensive mechanism. Long-context agents may accumulate instructions from multiple sources over extended tasks, making it difficult to determine which information remains authoritative. The system should maintain explicit provenance for important instructions and prevent untrusted content from silently becoming persistent policy. Context expiration, source tagging, and controlled memory mechanisms can reduce the chance that a malicious instruction remains active after the original interaction has ended.

Agent memory requires particular protection because persistent memory can turn a temporary injection into a long-term behavioral influence. If an attacker succeeds in causing the agent to store malicious instructions, future missions may be affected even when the original attack source is no longer present. Memory writes should therefore be subject to authorization, validation, provenance tracking, and appropriate review rather than being treated as ordinary conversational content.

Prompt injection defenses should not rely exclusively on asking the LLM to ignore malicious instructions. Language models can be probabilistic and context-sensitive, and an attacker may construct instructions that exploit unexpected interactions between legitimate and malicious content. Security-critical controls should therefore exist outside the model itself, using deterministic policy enforcement, authorization checks, tool restrictions, and independent validation.

Action confirmation can provide an additional safeguard for high-consequence operations. When a requested action involves physical risk, sensitive information, external communication, or privileged configuration, the system may require confirmation from an authorized controller or a higher-level policy engine. Confirmation should be based on the structured action and its consequences rather than simply asking the same language model whether the command appears safe.

The robot should also evaluate whether a proposed action is consistent with the current mission and physical context. A prompt injection may instruct the agent to perform an operation that is linguistically valid but operationally unrelated to the assigned task. Mission consistency checks can identify unexpected tool requests, abnormal destinations, unusual object interactions, or changes in operational objectives before they reach the physical control layer.

Independent safety monitors remain essential even when prompt-injection defenses are present. A safety boundary can enforce constraints on velocity, force, workspace, collision distance, geofencing, actuator states, and other physical invariants regardless of what the LLM recommends. This creates a final barrier between potentially compromised reasoning and physical execution.

Logging and provenance are necessary for detecting and investigating prompt injection. The system should preserve relevant information about instruction sources, tool requests, authorization decisions, policy evaluations, rejected actions, and physical responses. Such records can help distinguish legitimate agent behavior from manipulation and provide evidence for improving future defenses.

Testing should include both direct and indirect prompt injection scenarios. Evaluation should examine malicious user commands, compromised documents, untrusted web content, manipulated visual information, persistent memory attacks, conflicting instructions, and attempts to escalate tool privileges. Testing should continue through the complete perception-to-action chain rather than evaluating only whether the LLM produced an undesirable textual response.

A particularly important test condition is the combination of prompt injection with other attacks. A malicious visual pattern may introduce text that influences a vision-language model, while a compromised external service may provide instructions intended to manipulate the same agent. Security evaluation should therefore consider how multiple untrusted inputs interact and whether the agent can maintain trust boundaries when several sources provide conflicting information.

Fleet environments increase the potential impact because one compromised agent policy or shared context mechanism may affect multiple robots. Shared prompts, task templates, agent memories, tool configurations, model updates, or cloud-based orchestration services should therefore be protected and version controlled. An injection discovered in one robot should be investigated for possible propagation through common infrastructure.

Prompt injection defenses must also evolve with model and application updates. Changes to the underlying LLM, system prompts, tool definitions, retrieval mechanisms, memory architecture, or multimodal interfaces can introduce new attack paths. Each update should therefore undergo security regression testing that verifies instruction hierarchy, authorization boundaries, tool restrictions, memory protection, and independent physical safety controls.

The most effective defense is a layered architecture in which the LLM is treated as an intelligent reasoning component rather than an inherently trusted authority. Trusted instructions should be separated from untrusted data, tools should enforce independent authorization, high-risk actions should pass through deterministic policy controls, and physical execution should remain constrained by safety mechanisms. This approach limits the ability of a successful prompt injection to become an uncontrolled physical action.

Within the Physical AI Security structure, prompt injection against an LLM robot agent is positioned alongside AI model theft, adversarial attacks on robot vision, AI decision manipulation, certified robustness, AI safety monitoring, training-data protection, and model registry security. Volume_24_Robot_Cybersecurity This structure emphasizes that LLM security must be connected to the broader robot security lifecycle, particularly where language-based reasoning interacts with perception, tools, authorization, planning, and physical actuation.

대규모 언어 모델(Large Language Model, LLM)이 명령을 해석하고 도구를 호출하거나 물리적 기능을 제어할 수 있는 로봇 에이전트(Robot Agent)로 사용될 경우, 프롬프트 인젝션 공격(Prompt Injection Attack)은 독특한 보안 위험을 발생시킨다. 기존의 소프트웨어 입력 공격과 달리 악의적인 명령은 자연어 명령(Natural-language Command), 문서(Document), 웹 콘텐츠(Web Content), 이미지(Image), 센서에서 생성된 설명(Sensor-derived Description) 또는 기타 컨텍스트 정보(Contextual Information)에 포함될 수 있다. 에이전트가 신뢰할 수 없는 콘텐츠를 권한 있는 명령으로 잘못 처리하면 공격자는 기본 로봇 소프트웨어를 직접 침해하지 않고도 의사결정에 영향을 미칠 수 있다.

LLM 로봇 에이전트가 도구(Tool), 센서(Sensor), 내비게이션 기능(Navigation Function), 조작 기능(Manipulation Capability), 플릿 서비스(Fleet Service) 또는 외부 정보 소스(External Information Source)에 접근할 수 있을 때 이러한 위험은 더욱 커진다. 침해된 대화 컨텍스트(Conversational Context)는 어떤 도구를 선택할지, 어떤 매개변수를 전달할지, 또는 운영 목표를 어떻게 해석할지에 영향을 줄 수 있다. 이러한 의사결정이 궁극적으로 물리적 액추에이터(Physical Actuator)에 전달될 수 있기 때문에 프롬프트 인젝션은 단순한 정보 처리 문제가 아니라 사이버-물리적 보안 위협(Cyber-Physical Security Threat)으로 간주해야 한다.

프롬프트 인젝션은 직접적인 채널과 간접적인 채널 모두를 통해 발생할 수 있다. 직접 공격(Direct Attack)은 사용자가 제공하는 명령에 포함될 수 있으며, 간접 공격(Indirect Attack)은 로봇이 작업 수행 중 검색하는 웹페이지, 문서, 객체 라벨, 시각적 장면, 메시지 또는 기타 데이터에 포함될 수 있다. 에이전트는 정당한 작업을 수행하는 과정에서 악의적인 명령을 접할 수 있으며, 이를 신뢰된 명령 컨텍스트(Trusted Instruction Context)의 일부로 잘못 처리할 수 있다.

핵심적인 보안 문제는 명령(Instruction)과 데이터(Data)를 신뢰성 있게 구분하지 못하는 데 있다. LLM은 두 가지를 동일한 언어 표현(Language Representation)으로 처리할 수 있지만, 보안 아키텍처(Security Architecture)는 각 정보 출처에 서로 다른 신뢰 수준(Trust Level)을 부여해야 한다. 따라서 로봇 에이전트는 컨텍스트에 나타나는 모든 문장이 승인된 명령을 의미한다고 가정해서는 안 된다. 사용자 의도(User Intent), 시스템 정책(System Policy), 검색된 정보(Retrieved Information), 센서 해석(Sensor Interpretation), 제3자 콘텐츠(Third-party Content)는 논리적으로 구분되어야 한다.

시스템 명령(System Instruction)과 운영 정책(Operational Policy)은 명확하게 정의된 권한 계층(Authority Hierarchy)을 가져야 한다. 높은 신뢰 수준의 정책은 낮은 신뢰 수준의 콘텐츠가 이를 무시하거나 변경하지 못하도록 경계를 설정해야 한다. 사용자의 요청은 정당한 목표를 정의할 수 있지만 외부 문서나 검색된 웹 콘텐츠는 일반적으로 신뢰할 수 없는 정보(Untrusted Information)로 처리해야 한다. 에이전트는 신뢰할 수 없는 콘텐츠에서 발견한 명령이 안전 규칙(Safety Rule), 권한 요구사항(Authorization Requirement), 임무 제약(Mission Constraint) 또는 접근 권한(Access Privilege)을 조용히 재정의하도록 허용해서는 안 된다.

도구 접근(Tool Access)은 가장 중요한 통제 지점(Control Point) 중 하나이다. LLM이 유효한 도구 호출(Tool Call)을 생성할 수 있다는 이유만으로 제한 없는 권한을 제공해서는 안 된다. 내비게이션, 조작, 구성 변경, 통신, 모델 관리 또는 물리적 움직임에 영향을 미치는 도구는 명시적인 권한 부여(Authorization)를 요구하고 자체적인 입력 제약(Input Constraint)을 적용해야 한다. 도구 인터페이스(Tool Interface)는 언어 모델이 작업을 올바르게 해석했다고 가정하지 말고 매개변수를 독립적으로 검증해야 한다.

권한 분리(Privilege Separation)는 프롬프트 인젝션이 성공했을 때의 영향을 줄일 수 있다. 로봇 에이전트는 광범위한 추론 능력(Reasoning Capability)을 필요로 할 수 있지만, 특정 운영 조건에서는 제한된 일부 행동만 사용할 수 있어야 한다. 읽기 전용 정보 검색(Read-only Information Retrieval), 임무 계획(Mission Planning), 액추에이터 제어(Actuator Control), 펌웨어 관리(Firmware Management), 관리자 기능(Administrative Function)은 위험 수준에 따라 분리해야 한다. 침해된 추론 컨텍스트가 자동으로 더 높은 권한의 작업에 접근할 수 있어서는 안 된다.

자연어 명령(Natural-language Instruction)은 안전 필수 기능(Safety-critical Function)에 전달되기 전에 구조화된 표현(Structured Representation)으로 변환하는 것이 바람직하다. 생성된 자유 형식 텍스트(Free-form Text)가 로봇을 직접 제어하도록 허용하는 대신, 중간 정책 계층(Intermediate Policy Layer)이 승인된 의도를 제한된 명령으로 변환할 수 있다. 이 계층은 실행 전에 허용된 행동, 운영 매개변수, 작업공간 경계(Workspace Boundary), 속도 제한(Speed Limit) 및 기타 요구사항을 검증할 수 있다.

외부 정보 소스(External Information Source)는 명시적인 신뢰 경계(Trust Boundary)를 필요로 한다. 로봇은 할당된 작업을 수행하면서 문서, 지도(Map), 웹페이지, 작업 설명, 객체 메타데이터(Object Metadata) 또는 메시지를 검색할 수 있다. 이러한 정보에는 에이전트의 행동에 영향을 주도록 설계된 콘텐츠가 포함될 수 있다. 따라서 검색 시스템(Retrieval System)은 출처의 신원(Source Identity)과 신뢰 등급(Trust Classification)을 유지하여 에이전트가 권한 있는 운영 정보와 작업 중 발견한 신뢰할 수 없는 콘텐츠를 구분할 수 있도록 해야 한다.

멀티모달 에이전트(Multimodal Agent)는 이미지, 표지판(Sign), 화면에 표시된 텍스트, 오디오 또는 물리적 환경의 객체를 통해 추가적인 프롬프트 인젝션 경로를 생성한다. 비전-언어 모델(Vision-Language Model)은 환경에서 보이는 텍스트를 운영자가 승인하지 않은 경우에도 의미 있는 명령으로 해석할 수 있다. 따라서 인식에서 생성된 언어(Perception-derived Language)는 인증된 임무 명령(Authenticated Mission Command)과 동일한 권한을 자동으로 부여받아서는 안 된다.

컨텍스트 관리(Context Management)는 또 다른 중요한 방어 메커니즘이다. 장시간의 작업을 수행하는 에이전트는 여러 출처의 명령을 장기간 축적할 수 있기 때문에 어떤 정보가 여전히 권한 있는 정보인지 판단하기 어려워질 수 있다. 시스템은 중요한 명령에 대해 명시적인 출처 추적(Provenance)을 유지하고 신뢰할 수 없는 콘텐츠가 지속적인 정책(Persistent Policy)으로 조용히 변환되는 것을 방지해야 한다. 컨텍스트 만료(Context Expiration), 출처 태깅(Source Tagging), 통제된 메모리 메커니즘(Controlled Memory Mechanism)은 악의적인 명령이 원래의 상호작용이 종료된 후에도 계속 활성화되는 위험을 줄일 수 있다.

에이전트 메모리(Agent Memory)는 일시적인 인젝션 공격을 장기적인 행동 영향으로 전환할 수 있기 때문에 특별한 보호가 필요하다. 공격자가 에이전트가 악의적인 명령을 저장하도록 유도하면 원래의 공격 출처가 더 이상 존재하지 않더라도 향후 임무에 영향을 줄 수 있다. 따라서 메모리 기록(Memory Write)은 일반적인 대화 콘텐츠로 취급해서는 안 되며 권한 부여, 검증, 출처 추적 및 적절한 검토의 대상이 되어야 한다.

프롬프트 인젝션 방어는 단순히 LLM에게 악의적인 명령을 무시하도록 지시하는 방식에만 의존해서는 안 된다. 언어 모델은 확률적이고 컨텍스트에 민감하게 반응할 수 있으며, 공격자는 정상적인 콘텐츠와 악의적인 콘텐츠 사이의 예상하지 못한 상호작용을 이용하는 명령을 구성할 수 있다. 따라서 보안 필수 제어(Security-critical Control)는 모델 외부에 존재해야 하며 결정론적 정책 강제(Deterministic Policy Enforcement), 권한 검사(Authorization Check), 도구 제한(Tool Restriction), 독립적인 검증(Independent Validation)을 사용해야 한다.

행동 확인(Action Confirmation)은 높은 결과 위험을 가진 작업에 추가적인 보호 수단을 제공할 수 있다. 물리적 위험, 민감한 정보, 외부 통신 또는 권한 있는 구성 변경과 관련된 요청은 승인된 제어 주체(Authorized Controller)나 상위 정책 엔진(Higher-level Policy Engine)의 확인을 요구할 수 있다. 확인 과정은 동일한 언어 모델에게 명령이 안전해 보이는지를 묻는 방식이 아니라 구조화된 행동과 그 결과를 기반으로 수행해야 한다.

로봇은 제안된 행동이 현재 임무 및 물리적 컨텍스트와 일치하는지도 평가해야 한다. 프롬프트 인젝션은 언어적으로는 유효하지만 할당된 작업과 운영상 관련이 없는 행동을 에이전트에게 지시할 수 있다. 임무 일관성 검사(Mission Consistency Check)는 예상하지 못한 도구 요청, 비정상적인 목적지, 특이한 객체 상호작용 또는 운영 목표의 변경을 식별하여 물리적 제어 계층(Physical Control Layer)에 전달되기 전에 차단할 수 있다.

프롬프트 인젝션 방어가 존재하더라도 독립적인 안전 모니터(Independent Safety Monitor)는 여전히 필수적이다. 안전 경계(Safety Boundary)는 LLM이 무엇을 권고하는지와 관계없이 속도, 힘, 작업공간, 충돌 거리, 지오펜싱(Geofencing), 액추에이터 상태 및 기타 물리적 불변조건(Physical Invariant)을 강제할 수 있다. 이를 통해 잠재적으로 침해된 추론과 실제 물리적 실행 사이에 최종적인 방어 장벽을 구축할 수 있다.

로깅(Logging)과 출처 추적(Provenance)은 프롬프트 인젝션을 탐지하고 조사하는 데 필요하다. 시스템은 명령의 출처, 도구 요청, 권한 결정, 정책 평가, 거부된 행동 및 물리적 응답에 관한 관련 정보를 보존해야 한다. 이러한 기록은 정상적인 에이전트 행동과 조작된 행동을 구분하는 데 도움이 되며 향후 방어 체계를 개선하기 위한 증거를 제공한다.

테스트에는 직접적인 프롬프트 인젝션과 간접적인 프롬프트 인젝션 시나리오가 모두 포함되어야 한다. 평가는 악의적인 사용자 명령, 침해된 문서, 신뢰할 수 없는 웹 콘텐츠, 조작된 시각 정보, 지속적인 메모리 공격(Persistent Memory Attack), 충돌하는 명령, 도구 권한 상승 시도를 포함해야 한다. 테스트는 LLM이 바람직하지 않은 텍스트 응답을 생성했는지만 평가하는 데 그치지 않고 전체 인식-행동 체인(Perception-to-Action Chain)을 대상으로 수행해야 한다.

특히 중요한 테스트 조건은 프롬프트 인젝션과 다른 공격을 결합하는 것이다. 악의적인 시각 패턴은 비전-언어 모델에 영향을 주는 텍스트를 삽입할 수 있으며, 침해된 외부 서비스는 동일한 에이전트를 조작하도록 설계된 명령을 제공할 수 있다. 따라서 보안 평가는 여러 개의 신뢰할 수 없는 입력이 상호작용할 때 에이전트가 신뢰 경계를 유지할 수 있는지를 고려해야 한다.

플릿 환경(Fleet Environment)은 하나의 침해된 에이전트 정책이나 공유 컨텍스트 메커니즘이 여러 로봇에 영향을 줄 수 있기 때문에 잠재적인 영향을 확대한다. 공유 프롬프트(Shared Prompt), 작업 템플릿(Task Template), 에이전트 메모리, 도구 구성(Tool Configuration), 모델 업데이트 또는 클라우드 기반 오케스트레이션 서비스(Cloud-based Orchestration Service)는 보호하고 버전 관리해야 한다. 하나의 로봇에서 발견된 인젝션 공격은 공통 인프라를 통한 확산 가능성을 확인하기 위해 조사해야 한다.

프롬프트 인젝션 방어는 모델과 애플리케이션 업데이트에 따라 지속적으로 발전해야 한다. 기본 LLM, 시스템 프롬프트, 도구 정의, 검색 메커니즘(Retrieval Mechanism), 메모리 아키텍처(Memory Architecture), 멀티모달 인터페이스(Multimodal Interface)의 변경은 새로운 공격 경로를 생성할 수 있다. 따라서 각각의 업데이트는 명령 계층, 권한 경계, 도구 제한, 메모리 보호, 독립적인 물리적 안전 제어가 정상적으로 유지되는지를 확인하는 보안 회귀 테스트(Security Regression Test)를 거쳐야 한다.

가장 효과적인 방어는 LLM을 본질적으로 신뢰할 수 있는 권한자가 아니라 지능형 추론 구성요소(Intelligent Reasoning Component)로 취급하는 다층 아키텍처(Layered Architecture)이다. 신뢰된 명령은 신뢰할 수 없는 데이터와 분리해야 하며, 도구는 독립적인 권한 부여를 적용해야 하고, 고위험 행동은 결정론적 정책 제어를 통과해야 하며, 물리적 실행은 안전 메커니즘에 의해 지속적으로 제한되어야 한다. 이러한 접근 방식은 프롬프트 인젝션이 성공하더라도 그것이 통제되지 않은 물리적 행동으로 전환되는 것을 제한한다.

피지컬 AI 보안(Physical AI Security) 구조에서 LLM 로봇 에이전트에 대한 프롬프트 인젝션 공격은 AI 모델 탈취(AI Model Theft), 로봇 비전에 대한 적대적 공격(Adversarial Attack on Robot Vision), AI 의사결정 조작(AI Decision Manipulation), 인증된 견고성(Certified Robustness), AI 안전 모니터링(AI Safety Monitoring), 학습 데이터 보호(Training Data Protection), 모델 레지스트리 보안(Model Registry Security)과 함께 구성된다. 이러한 구조는 LLM 보안(LLM Security)이 로봇의 광범위한 보안 수명주기(Security Lifecycle)와 연결되어야 하며, 특히 언어 기반 추론(Language-based Reasoning)이 인식(Perception), 도구(Tool), 권한 부여(Authorization), 계획(Planning), 물리적 작동(Physical Actuation)과 상호작용하는 영역에서 통합적으로 관리되어야 함을 강조한다.

##  

## 10.05. AI Decision Manipulation and Physical Consequences

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

AI decision manipulation represents a critical security risk in Physical AI because an attacker may influence not only what a robot perceives but also how it interprets information, selects actions, and prioritizes objectives. A manipulated AI decision can remain syntactically valid and appear operationally normal while producing behavior that differs from the intended mission. The security problem therefore extends beyond model correctness to the trustworthiness of decisions that ultimately affect the physical world.

Physical AI systems transform observations into decisions through multiple interconnected stages, including perception, state estimation, reasoning, planning, policy selection, and control. Manipulation at any stage can propagate toward physical execution. An attacker may alter sensor information, contextual inputs, model outputs, task instructions, reward signals, or intermediate representations. Even when individual components continue functioning normally, their combined interpretation may lead the robot toward an unsafe or unauthorized action.

Decision manipulation is particularly dangerous because AI systems often operate under uncertainty. A robot may need to select an action when sensor observations are incomplete, ambiguous, or changing rapidly. An attacker can exploit this uncertainty by introducing information that makes an unsafe action appear reasonable. The resulting decision may not resemble a conventional software failure because the system can produce a coherent plan that is inappropriate only when evaluated against the actual physical situation.

One important attack path involves manipulation of the robot\'s perception-to-decision interface. If an attacker changes the perceived identity, position, motion, or importance of an object, the planner may generate a different trajectory or task sequence. A robot that incorrectly interprets an obstacle, person, vehicle, package, or workspace boundary may consequently change its movement or manipulation behavior. Security controls must therefore protect the integrity of information passed between perception and decision-making components.

Context manipulation creates another risk. Modern Physical AI systems may combine visual observations, language instructions, maps, task descriptions, historical memory, and environmental information when selecting an action. If one contextual source is compromised, the AI system may assign inappropriate importance to that information. A malicious instruction may appear consistent with the surrounding context and therefore influence the final decision without directly modifying the underlying model parameters.

Goal and priority manipulation can have especially significant consequences. Autonomous systems frequently operate under multiple objectives, such as completing a task, avoiding obstacles, preserving battery energy, maintaining communication, protecting payloads, and respecting safety constraints. An attacker who influences the relative priority of these objectives may cause the robot to choose behavior that appears efficient from one perspective while violating a more important operational requirement.

Reward manipulation is particularly relevant to learning-enabled robots. Reinforcement learning and adaptive systems may use rewards, feedback, demonstrations, or evaluation signals to determine preferred behavior. If an attacker can influence these signals, the system may gradually favor actions that benefit the attacker rather than actions aligned with the original mission. The danger increases when learning occurs during deployment because manipulated feedback may affect future behavior rather than producing only a single incorrect decision.

Decision manipulation can also target learned policies directly through carefully constructed states. A policy may behave safely across normal operating conditions but produce unexpected actions in rarely encountered regions of its state space. An attacker may deliberately create or induce such conditions through environmental changes, sensor manipulation, unusual object arrangements, or carefully selected commands. The resulting behavior may emerge from the policy itself rather than from an obvious software error.

In language-enabled robot agents, decision manipulation may occur through conflicting or misleading instructions. An agent may receive a legitimate mission objective while simultaneously encountering untrusted content that suggests a different action. If the system does not maintain a clear authority hierarchy, the agent may resolve the conflict incorrectly. This problem becomes more serious when language reasoning is directly connected to tools, navigation, manipulation, or other physical capabilities.

Decision integrity therefore requires explicit separation between information, recommendation, authorization, and execution. An AI model may recommend an action, but the recommendation should not automatically constitute permission to execute it. A policy enforcement layer can evaluate whether the proposed action is authorized for the current robot, mission, environment, and operating state. This separation reduces the possibility that manipulated reasoning will directly become physical behavior.

Safety constraints should remain independent of the AI decision process wherever practical. Velocity limits, force limits, workspace boundaries, collision distances, geofences, actuator restrictions, and emergency-stop conditions should be enforced by mechanisms that do not depend solely on the model being protected. If an AI system proposes an unsafe action, the independent safety layer should be able to reject, constrain, or replace that action before physical execution.

Decision validation should also consider the consistency of an action with the robot\'s current state. A proposed command may be linguistically valid but physically impossible, operationally inappropriate, or inconsistent with available resources. The robot can evaluate whether the action is compatible with current localization, sensor observations, actuator status, battery state, workspace conditions, and mission constraints. Such validation can identify manipulation that would otherwise appear reasonable at the language or policy level.

Multi-sensor consistency provides another method for detecting manipulated decisions. If the AI proposes an action based on an environmental interpretation that conflicts with independent sensor observations, the system should reduce confidence or require additional verification. This approach is particularly valuable when one perception channel may have been compromised. Independent evidence can prevent a single manipulated observation from becoming the sole basis for a high-consequence physical action.

Temporal consistency is similarly important. Physical environments normally evolve according to observable dynamics, and a robot\'s decisions should generally reflect plausible changes over time. A sudden change in perceived object identity, mission priority, route preference, or safety status without a corresponding physical or operational cause can indicate manipulation. Monitoring decision histories can therefore reveal attacks that are difficult to detect from individual commands.

The consequences of manipulated decisions should be classified according to physical severity. A minor change in task ordering may have limited impact, while an incorrect navigation decision may cause a collision, an inappropriate manipulation may damage equipment, and a compromised flight decision may create an aviation safety hazard. Security architecture should therefore assign stronger verification requirements to decisions with greater physical authority or greater potential for harm.

Human oversight can provide an additional control for high-consequence decisions. When an AI system proposes an action involving significant physical risk, irreversible changes, sensitive infrastructure, or external mission authority, an authorized human or higher-level supervisory system may be required to approve the action. Human confirmation should be selective and risk-based rather than applied indiscriminately, so that normal autonomous operation remains practical.

Runtime monitoring should observe not only system health but also behavioral patterns. Unexpected route changes, abnormal actuator commands, repeated boundary approaches, unusual task priorities, unexplained mission modifications, or significant deviations from established operating patterns can indicate decision manipulation. Behavioral monitoring is particularly important because a compromised AI component may continue to report normal software and network health while generating unsafe decisions.

Audit logging should preserve enough information to reconstruct why an important decision was made. Relevant records may include input sources, model identity, model version, contextual information, selected policy, confidence or uncertainty indicators, authorization results, safety checks, tool calls, and final physical commands. Maintaining decision provenance supports incident investigation and allows security teams to distinguish model limitations from deliberate manipulation.

Model and policy updates require controlled validation because changes to one component can alter decision behavior elsewhere in the system. A new perception model may change planner inputs, a new language model may alter tool selection, and a policy update may change how the robot responds to previously rare situations. Security regression testing should therefore evaluate not only component functionality but also end-to-end decision behavior under adversarial and safety-critical conditions.

Fleet environments amplify decision manipulation because a compromised policy, configuration, or shared service can affect many robots. Common mission templates, centralized planning services, shared models, fleet policies, and cloud-based decision services should have strong authentication, integrity protection, version control, and deployment governance. When abnormal decisions are detected on one robot, the organization should determine whether the same condition exists across other members of the fleet.

Recovery mechanisms should be designed for situations in which decision integrity cannot be established. The robot may need to transition to a safe state, suspend autonomous operation, return to a predefined location, reduce capabilities, or await authorized instructions. Recovery behavior should not depend on the same compromised decision mechanism that caused the problem. Independent fallback logic provides a more reliable path to containment.

Security testing should examine complete attack chains rather than isolated model failures. Tests can begin with manipulated sensor observations, contextual instructions, model outputs, reward signals, or external data and then trace their influence through reasoning, planning, authorization, and physical control. The objective is to determine whether an attacker can convert a small information manipulation into a meaningful change in physical behavior.

The strongest defense is therefore a layered decision-security architecture in which AI intelligence is powerful but not independently authoritative. Trusted inputs, contextual data, model outputs, policy decisions, authorization, safety enforcement, and actuator execution should have distinct trust boundaries. Independent validation and safety controls should prevent a compromised reasoning process from exercising unrestricted physical authority.

Within the Physical AI Security structure, AI decision manipulation and physical consequences form a dedicated security area alongside AI model theft, adversarial attacks on robot vision, LLM prompt injection, certified robustness, AI safety monitoring, training-data protection, and model registry security. This organization reflects the fundamental requirement that Physical AI security must protect not only data and models but also the integrity of the decisions that transform machine intelligence into real-world physical action.

AI 의사결정 조작(AI Decision Manipulation)은 공격자가 로봇이 무엇을 인식하는지뿐만 아니라 정보를 어떻게 해석하고, 행동을 선택하며, 목표의 우선순위를 어떻게 결정하는지까지 영향을 미칠 수 있기 때문에 피지컬 AI(Physical AI)에서 중요한 보안 위험을 나타낸다. 조작된 AI 의사결정은 문법적으로 유효하고 운영상 정상적으로 보일 수 있지만, 의도된 임무와는 다른 행동을 생성할 수 있다. 따라서 보안 문제는 단순한 모델의 정확성을 넘어 최종적으로 물리적 세계에 영향을 미치는 의사결정 자체의 신뢰성(Trustworthiness)을 포함한다.

피지컬 AI 시스템은 인식(Perception), 상태 추정(State Estimation), 추론(Reasoning), 계획(Planning), 정책 선택(Policy Selection), 제어(Control) 등 서로 연결된 여러 단계를 통해 관측값을 의사결정으로 변환한다. 어느 한 단계에서 발생한 조작도 물리적 실행으로 전파될 수 있다. 공격자는 센서 정보, 컨텍스트 입력(Contextual Input), 모델 출력, 작업 지시, 보상 신호(Reward Signal) 또는 중간 표현(Intermediate Representation)을 변경할 수 있다. 개별 구성요소가 정상적으로 작동하더라도 전체적인 해석이 결합되면서 로봇을 위험하거나 승인되지 않은 행동으로 유도할 수 있다.

의사결정 조작은 AI 시스템이 불확실성(Uncertainty) 속에서 작동하는 경우 특히 위험하다. 로봇은 센서 관측값이 불완전하거나 모호하거나 빠르게 변화하는 상황에서 행동을 선택해야 할 수 있다. 공격자는 이러한 불확실성을 악용하여 안전하지 않은 행동이 합리적인 선택처럼 보이도록 정보를 주입할 수 있다. 결과적으로 발생하는 의사결정은 일반적인 소프트웨어 오류와는 다른 형태를 보일 수 있다. 시스템은 실제 물리적 상황을 기준으로 평가했을 때만 부적절한 일관성 있는 계획을 생성할 수 있기 때문이다.

중요한 공격 경로 중 하나는 로봇의 인식-의사결정 인터페이스(Perception-to-Decision Interface)를 조작하는 것이다. 공격자가 객체의 인식된 정체성, 위치, 움직임 또는 중요도를 변경하면 플래너(Planner)는 다른 궤적이나 작업 순서를 생성할 수 있다. 장애물, 사람, 차량, 화물 또는 작업공간 경계를 잘못 해석한 로봇은 그 결과 이동 또는 조작 행동을 변경할 수 있다. 따라서 보안 제어는 인식 구성요소와 의사결정 구성요소 사이에서 전달되는 정보의 무결성을 보호해야 한다.

컨텍스트 조작(Context Manipulation)도 또 다른 위험을 발생시킨다. 현대의 피지컬 AI 시스템은 행동을 선택할 때 시각적 관측값, 언어 명령, 지도(Map), 작업 설명, 과거 메모리 및 환경 정보를 결합할 수 있다. 하나의 컨텍스트 출처가 침해되면 AI 시스템이 해당 정보에 부적절한 중요도를 부여할 수 있다. 악의적인 명령이 주변 컨텍스트와 일치하는 것처럼 보이면 기본 모델 파라미터를 직접 수정하지 않고도 최종 의사결정에 영향을 줄 수 있다.

목표와 우선순위 조작(Goal and Priority Manipulation)은 특히 중요한 결과를 발생시킬 수 있다. 자율 시스템은 작업 완료, 장애물 회피, 배터리 에너지 보존, 통신 유지, 화물 보호, 안전 제약 준수와 같이 여러 목표를 동시에 고려하여 작동한다. 공격자가 이러한 목표의 상대적 우선순위에 영향을 주면 로봇은 한 가지 관점에서는 효율적으로 보이지만 더 중요한 운영 요구사항을 위반하는 행동을 선택할 수 있다.

보상 조작(Reward Manipulation)은 학습 기반 로봇에서 특히 중요한 문제이다. 강화학습(Reinforcement Learning) 및 적응형 시스템(Adaptive System)은 선호되는 행동을 결정하기 위해 보상, 피드백, 시연 또는 평가 신호를 사용할 수 있다. 공격자가 이러한 신호를 조작할 수 있다면 시스템은 원래 임무와 일치하는 행동보다 공격자에게 유리한 행동을 점진적으로 선호할 수 있다. 배포 이후에도 학습이 지속되는 경우 조작된 피드백이 단일한 잘못된 의사결정에 그치지 않고 미래 행동 자체에 영향을 줄 수 있기 때문에 위험은 더욱 커진다.

의사결정 조작은 정교하게 구성된 상태(State)를 통해 학습된 정책(Learned Policy)을 직접 공격할 수도 있다. 정책은 정상적인 운영 조건에서는 안전하게 행동하더라도 상태 공간(State Space)에서 거의 경험하지 못한 영역에서는 예상하지 못한 행동을 생성할 수 있다. 공격자는 환경 변화, 센서 조작, 비정상적인 객체 배치 또는 정교하게 선택된 명령을 통해 이러한 조건을 의도적으로 생성하거나 유도할 수 있다. 이러한 행동은 명백한 소프트웨어 오류가 아니라 정책 자체에서 발생할 수 있다.

언어 기반 로봇 에이전트(Language-enabled Robot Agent)에서는 서로 충돌하거나 오해를 유발하는 명령을 통해 의사결정 조작이 발생할 수 있다. 에이전트는 정당한 임무 목표를 받는 동시에 다른 행동을 제안하는 신뢰할 수 없는 콘텐츠를 접할 수 있다. 시스템이 명확한 권한 계층(Authority Hierarchy)을 유지하지 못하면 에이전트는 이러한 충돌을 잘못 해결할 수 있다. 언어 추론(Language Reasoning)이 도구, 내비게이션, 조작 또는 기타 물리적 기능과 직접 연결될 경우 이러한 문제는 더욱 심각해진다.

따라서 의사결정 무결성(Decision Integrity)은 정보, 권고(Recommendation), 권한 부여(Authorization), 실행(Execution)을 명확하게 분리해야 한다. AI 모델이 행동을 권고할 수 있지만 그 권고가 자동으로 실행 권한을 의미해서는 안 된다. 정책 강제 계층(Policy Enforcement Layer)은 제안된 행동이 현재 로봇, 임무, 환경 및 운영 상태에 대해 승인되었는지를 평가할 수 있다. 이러한 분리는 조작된 추론이 직접적인 물리적 행동으로 전환될 가능성을 줄인다.

가능한 경우 안전 제약(Safety Constraint)은 AI 의사결정 과정과 독립적으로 유지해야 한다. 속도 제한, 힘 제한, 작업공간 경계, 충돌 거리, 지오펜스(Geofence), 액추에이터 제한 및 비상 정지(Emergency Stop) 조건은 보호 대상 모델에만 의존하지 않는 메커니즘으로 강제되어야 한다. AI 시스템이 안전하지 않은 행동을 제안하면 독립적인 안전 계층이 물리적 실행 전에 해당 행동을 거부하거나 제한하거나 대체할 수 있어야 한다.

의사결정 검증(Decision Validation)은 해당 행동이 로봇의 현재 상태와 일치하는지도 고려해야 한다. 제안된 명령은 언어적으로는 유효하지만 물리적으로 불가능하거나 운영상 부적절하거나 사용 가능한 자원과 일치하지 않을 수 있다. 로봇은 해당 행동이 현재 위치 추정(Localization), 센서 관측값, 액추에이터 상태, 배터리 상태, 작업공간 조건 및 임무 제약과 호환되는지를 평가할 수 있다. 이러한 검증은 언어 또는 정책 수준에서는 합리적으로 보이는 조작을 식별할 수 있다.

다중 센서 일관성(Multi-sensor Consistency)은 조작된 의사결정을 탐지하는 또 다른 방법을 제공한다. AI가 제안한 행동이 독립적인 센서 관측값과 충돌하는 환경 해석을 기반으로 한다면 시스템은 신뢰도를 낮추거나 추가 검증을 요구해야 한다. 이러한 접근법은 하나의 인식 채널이 침해되었을 가능성이 있을 때 특히 유용하다. 독립적인 증거는 하나의 조작된 관측값이 고위험 물리적 행동의 유일한 근거가 되는 것을 방지할 수 있다.

시간적 일관성(Temporal Consistency) 역시 중요하다. 물리적 환경은 일반적으로 관찰 가능한 동역학에 따라 변화하며 로봇의 의사결정도 시간에 따른 합리적인 변화를 반영해야 한다. 물리적 또는 운영상의 원인이 없음에도 인식된 객체의 정체성, 임무 우선순위, 경로 선호도 또는 안전 상태가 갑자기 변경된다면 조작의 신호일 수 있다. 따라서 의사결정 이력을 모니터링하면 개별 명령만으로는 탐지하기 어려운 공격을 식별할 수 있다.

조작된 의사결정의 결과는 물리적 심각도(Physical Severity)에 따라 분류해야 한다. 작업 순서가 약간 변경되는 것은 영향이 제한적일 수 있지만, 잘못된 내비게이션 결정은 충돌을 일으킬 수 있고, 부적절한 조작은 장비를 손상시킬 수 있으며, 침해된 비행 의사결정은 항공 안전 위험을 발생시킬 수 있다. 따라서 보안 아키텍처는 물리적 권한이 크거나 잠재적인 피해가 큰 의사결정에 더 강력한 검증 요구사항을 적용해야 한다.

인간의 감독(Human Oversight)은 높은 결과 위험을 가진 의사결정에 추가적인 통제 수단을 제공할 수 있다. AI 시스템이 상당한 물리적 위험, 되돌릴 수 없는 변경(Irreversible Change), 민감한 기반시설 또는 외부 임무 권한과 관련된 행동을 제안하는 경우 승인된 인간 또는 상위 감독 시스템(Higher-level Supervisory System)의 승인이 필요할 수 있다. 인간 확인(Human Confirmation)은 모든 행동에 무차별적으로 적용하기보다 위험 기반(Risk-based)으로 선택해야 하며, 이를 통해 정상적인 자율 운용의 실용성을 유지할 수 있다.

런타임 모니터링(Runtime Monitoring)은 시스템 상태뿐만 아니라 행동 패턴도 관찰해야 한다. 예상하지 못한 경로 변경, 비정상적인 액추에이터 명령, 반복적인 경계 접근, 특이한 작업 우선순위, 설명되지 않는 임무 변경 또는 기존 운영 패턴에서 크게 벗어나는 행동은 의사결정 조작을 나타낼 수 있다. 침해된 AI 구성요소가 정상적인 소프트웨어 및 네트워크 상태를 계속 보고하면서도 안전하지 않은 의사결정을 생성할 수 있기 때문에 행동 모니터링(Behavioral Monitoring)은 특히 중요하다.

감사 로깅(Audit Logging)은 중요한 의사결정이 왜 내려졌는지를 재구성할 수 있을 정도의 정보를 보존해야 한다. 관련 기록에는 입력 출처(Input Source), 모델 신원(Model Identity), 모델 버전, 컨텍스트 정보, 선택된 정책, 신뢰도 또는 불확실성 지표, 권한 부여 결과, 안전 검사, 도구 호출(Tool Call), 최종 물리적 명령이 포함될 수 있다. 의사결정 출처 추적(Decision Provenance)을 유지하면 사고를 조사하고 모델의 한계와 의도적인 조작을 구분하는 데 도움이 된다.

모델과 정책 업데이트(Model and Policy Update)는 하나의 구성요소 변경이 시스템의 다른 부분의 의사결정 행동을 변경할 수 있기 때문에 통제된 검증이 필요하다. 새로운 인식 모델은 플래너 입력을 변경할 수 있고, 새로운 언어 모델은 도구 선택을 변경할 수 있으며, 정책 업데이트는 로봇이 과거에는 드물었던 상황에 반응하는 방식을 변경할 수 있다. 따라서 보안 회귀 테스트(Security Regression Testing)는 구성요소의 기능뿐만 아니라 적대적 조건과 안전 필수 조건에서의 종단 간 의사결정 행동을 평가해야 한다.

플릿 환경(Fleet Environment)은 침해된 정책, 구성 또는 공유 서비스가 여러 로봇에 영향을 줄 수 있기 때문에 의사결정 조작의 영향을 확대한다. 공통 임무 템플릿, 중앙 집중식 계획 서비스, 공유 모델, 플릿 정책 및 클라우드 기반 의사결정 서비스는 강력한 인증(Authentication), 무결성 보호(Integrity Protection), 버전 관리(Version Control), 배포 거버넌스(Deployment Governance)를 갖추어야 한다. 하나의 로봇에서 비정상적인 의사결정이 탐지되면 조직은 동일한 조건이 다른 플릿 구성원에게도 존재하는지 확인해야 한다.

의사결정 무결성을 확립할 수 없는 상황을 고려하여 복구 메커니즘(Recovery Mechanism)을 설계해야 한다. 로봇은 안전 상태(Safe State)로 전환하거나 자율 운용을 중지하거나, 사전에 정의된 위치로 복귀하거나, 기능을 축소하거나, 승인된 명령을 기다려야 할 수 있다. 복구 행동은 문제를 발생시킨 동일한 침해된 의사결정 메커니즘에 의존해서는 안 된다. 독립적인 폴백 로직(Independent Fallback Logic)은 보다 신뢰할 수 있는 격리 및 복구 경로를 제공한다.

보안 테스트(Security Testing)는 개별적인 모델 장애가 아니라 전체 공격 체인(Attack Chain)을 평가해야 한다. 테스트는 조작된 센서 관측값, 컨텍스트 명령, 모델 출력, 보상 신호 또는 외부 데이터에서 시작하여 추론, 계획, 권한 부여 및 물리적 제어를 거치는 영향을 추적할 수 있다. 목적은 공격자가 작은 정보 조작을 의미 있는 물리적 행동 변화로 전환할 수 있는지를 확인하는 것이다.

따라서 가장 강력한 방어는 AI 지능은 강력하지만 독립적인 권한자는 아닌 것으로 설계하는 다층 의사결정 보안 아키텍처(Layered Decision Security Architecture)이다. 신뢰된 입력, 컨텍스트 데이터, 모델 출력, 정책 결정, 권한 부여, 안전 강제(Safety Enforcement), 액추에이터 실행은 서로 구분된 신뢰 경계(Trust Boundary)를 가져야 한다. 독립적인 검증과 안전 제어는 침해된 추론 프로세스가 제한 없이 물리적 권한을 행사하는 것을 방지해야 한다.

피지컬 AI 보안(Physical AI Security) 구조에서 AI 의사결정 조작과 물리적 결과(AI Decision Manipulation and Physical Consequences)는 AI 모델 탈취(AI Model Theft), 로봇 비전에 대한 적대적 공격(Adversarial Attack on Robot Vision), LLM 프롬프트 인젝션(LLM Prompt Injection), 인증된 견고성(Certified Robustness), AI 안전 모니터링(AI Safety Monitoring), 학습 데이터 보호(Training Data Protection), 모델 레지스트리 보안(Model Registry Security)과 함께 독립적인 보안 영역을 구성한다. 이러한 구성은 피지컬 AI 보안이 데이터와 모델만을 보호하는 것이 아니라 기계 지능을 실제 세계의 물리적 행동으로 변환하는 의사결정의 무결성까지 보호해야 한다는 근본적인 요구사항을 반영한다.

##  

## 10.06. Certified Robustness for Safety Critical AI [w/Code]

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

Certified robustness provides a stronger security and safety assurance for safety-critical Artificial Intelligence (AI) systems by attempting to establish that a model\'s behavior remains within defined limits when its inputs are subjected to specified perturbations. Conventional robustness testing demonstrates performance through selected examples, whereas certification seeks a formal or mathematically defensible guarantee under a clearly defined threat model. For Physical AI, this distinction is important because perception errors can propagate directly into navigation, manipulation, locomotion, or flight behavior.

A safety-critical AI system operates under conditions where an incorrect prediction may have consequences beyond degraded software performance. A perception model used for collision avoidance, human detection, obstacle recognition, or autonomous navigation may influence decisions that control substantial physical energy. Certified robustness therefore needs to connect model-level guarantees with the operational conditions in which the robot is expected to function. The certification boundary should identify which inputs, perturbations, outputs, and operating states are actually covered by the guarantee.

Robustness certification generally requires a precisely defined perturbation model. The permitted perturbation may represent bounded changes to pixels, sensor measurements, feature representations, or other inputs. The guarantee is meaningful only within the specified mathematical or operational boundary. If an attack falls outside that boundary, the certificate does not automatically establish safety. Consequently, security engineers must ensure that the selected perturbation model corresponds realistically to the threats that a robot can encounter in its physical environment.

Certified robustness is particularly relevant to adversarial attacks against robot perception. A vision model may be required to maintain a stable prediction when an input image experiences bounded changes. Formal robustness techniques can attempt to demonstrate that the model\'s output cannot change within a defined perturbation region. This can provide stronger assurance than testing a finite collection of adversarial examples, because the objective is to reason about an entire class of possible inputs rather than only those explicitly generated during testing.

However, certification does not mean that an AI model is universally secure. A certificate is always associated with assumptions about the model, input domain, perturbation magnitude, output property, and verification method. Changes to preprocessing, sensor configuration, model architecture, deployment environment, or threat assumptions may invalidate the original conclusion. Certified robustness should therefore be treated as evidence supporting a defined security claim rather than as a general declaration that the AI system cannot be attacked.

The choice of robustness property should reflect the physical role of the model. For classification, the property may require that the predicted class remain unchanged within a defined perturbation region. For object detection or segmentation, the required property may involve preservation of object identity, localization, or relevant scene structure. For a safety-critical robot, the ultimate concern may instead be whether perception uncertainty can cause an unsafe planning or control decision. The verification target should therefore be connected to the physical consequence of model failure.

Certification becomes more difficult as models and inputs become more complex. Modern Physical AI systems may process high-resolution images, LiDAR point clouds, multimodal observations, temporal sequences, language instructions, or combinations of these inputs. Verifying the behavior of large neural networks across such domains can require substantial computational resources and specialized verification techniques. The resulting cost and scalability limitations must be considered when defining which components receive formal robustness guarantees.

Neural network verification may use mathematical abstractions, constraint solving, interval-based methods, linear relaxations, or other formal reasoning techniques to establish bounds on model behavior. These methods attempt to determine whether possible inputs within a specified region can produce an unacceptable output. The practical value of the result depends on how tightly the verification method represents the actual network behavior. Excessively conservative bounds may produce inconclusive results even when the model is practically robust.

A certified result should therefore distinguish between verified, violated, and unresolved cases. A verified region provides evidence that the specified property holds within the examined assumptions. A violation demonstrates that an unsafe or undesired behavior can occur within the defined region. An unresolved result means that the verification procedure could not establish either conclusion and should not be interpreted as evidence of robustness. This distinction is essential for safety-critical assurance and prevents inconclusive analysis from being mistaken for certification.

Physical validation remains necessary because mathematical input perturbations do not automatically represent every real-world condition. Lighting changes, shadows, camera motion, sensor calibration errors, occlusion, vibration, environmental reflections, and viewpoint changes may produce complex effects that are difficult to capture using a simple perturbation model. Certified robustness should therefore be combined with physical testing, simulation, sensor-fusion validation, and operational scenario testing.

Sensor fusion can strengthen robustness when independent sensing modalities provide complementary evidence. A camera model may be formally robust against a defined image perturbation while the overall robot remains vulnerable to a different sensor attack. Conversely, combining camera, LiDAR, radar, inertial, or depth information may allow the system to detect inconsistencies that a single model cannot resolve. Certification should therefore clarify whether the guarantee applies to an individual AI component or to the complete perception and decision pipeline.

Temporal robustness is also important for robots operating continuously in dynamic environments. A model may produce stable predictions for individual frames while generating inconsistent behavior across a sequence of observations. Safety-critical verification may therefore need to consider temporal properties, state transitions, tracking consistency, or bounded changes between successive observations. This is particularly relevant to autonomous navigation, locomotion, manipulation, and flight systems where a sequence of decisions determines physical behavior.

The relationship between certified robustness and safety constraints should be explicitly established. Even a formally verified perception model cannot guarantee that the entire robot remains safe if planning, control, actuation, or environmental assumptions fail. Independent safety mechanisms should therefore continue to enforce limits on velocity, force, workspace, collision distance, geofencing, actuator states, and other physical invariants. Certification strengthens one layer of assurance but should not eliminate defense in depth.

Certified robustness can also support model selection and deployment decisions. When several candidate models achieve comparable task performance, a model with stronger verified guarantees under relevant threat conditions may provide greater assurance for a safety-critical application. Model evaluation can therefore include both conventional accuracy metrics and security-oriented robustness properties. This creates a more complete basis for selecting models intended to control physical systems.

Model updates require renewed verification. Even a small change to model weights, architecture, preprocessing, input resolution, training procedure, or optimization configuration can alter robustness properties. A previously certified model should not automatically retain its certification after modification. Continuous integration and deployment processes should therefore maintain versioned verification evidence and require appropriate re-evaluation before a modified model is released to safety-critical robots.

The certification evidence should remain traceable to the exact model artifact and verification configuration. Model identity, version, cryptographic measurement, verification method, perturbation assumptions, certified property, tool version, verification result, and approval status should be recorded. This information allows an organization to determine precisely what was certified and prevents a different or modified model from being incorrectly treated as equivalent to the verified artifact.

Runtime monitoring remains valuable even when formal certification is available. The deployed robot may encounter conditions outside the certified input region, sensor failures, distribution shifts, environmental changes, or combined attacks that were not represented by the original threat model. Runtime monitors can detect unusual confidence, sensor disagreement, distribution anomalies, or unsafe decision patterns and initiate additional verification, degraded operation, or safe-state behavior.

The threat model should also be periodically reviewed. Attack techniques evolve, sensor configurations change, new model architectures are introduced, and robots may operate in environments that were not anticipated during the original certification effort. A robustness certificate based on outdated assumptions can create a false sense of security. Security governance should therefore define conditions that trigger re-analysis, such as major model changes, newly discovered attacks, new sensors, new operational domains, or significant changes in physical authority.

For high-consequence systems, certified robustness should be integrated with the broader safety and cybersecurity assurance process. Threat modeling identifies relevant attack conditions, robustness verification establishes bounded properties, penetration testing searches for practical weaknesses, physical testing examines real-world behavior, and safety mechanisms constrain consequences. These activities provide complementary evidence because no single verification method can capture every failure mode of a complex Physical AI system.

The ultimate objective is not to prove that a robot\'s AI model is mathematically perfect. It is to establish defensible boundaries within which the model\'s behavior can be trusted and to ensure that failures outside those boundaries cannot automatically become uncontrolled physical actions. Certified robustness therefore functions as one layer within a larger architecture that combines secure models, trustworthy data, runtime monitoring, independent safety controls, controlled deployment, and recovery mechanisms.

Within the Physical AI Security structure, Certified Robustness for Safety-critical AI is positioned after AI decision manipulation and before AI safety monitoring, training-data security, model registry security, and the broader Physical AI security framework. Volume_24_Robot_Cybersecurity This placement reflects its role as a bridge between AI robustness and physical safety: the objective is not merely to demonstrate that a model performs well, but to establish evidence that its behavior remains acceptably bounded under defined adversarial conditions before AI decisions are allowed to influence safety-critical physical actions.

인증된 견고성(Certified Robustness)은 입력이 특정한 섭동(Perturbation)을 받더라도 모델의 행동이 정의된 범위 안에서 유지된다는 것을 확립함으로써 안전 필수 인공지능(Artificial Intelligence, AI) 시스템에 보다 강력한 보안 및 안전 보증을 제공한다. 기존의 견고성 테스트(Robustness Testing)는 선택된 사례를 통해 성능을 입증하는 반면, 인증(Certification)은 명확하게 정의된 위협 모델(Threat Model) 아래에서 형식적(Formal) 또는 수학적으로 방어 가능한 보증을 확보하려고 한다. 피지컬 AI(Physical AI)에서는 인식 오류가 내비게이션(Navigation), 조작(Manipulation), 보행(Locomotion) 또는 비행(Flight) 행동으로 직접 전파될 수 있기 때문에 이러한 차이가 중요하다.

안전 필수 AI 시스템(Safety-critical AI System)은 잘못된 예측이 단순한 소프트웨어 성능 저하를 넘어서는 결과를 초래할 수 있는 조건에서 작동한다. 충돌 회피(Collision Avoidance), 사람 탐지(Human Detection), 장애물 인식(Obstacle Recognition) 또는 자율 내비게이션(Autonomous Navigation)에 사용되는 인식 모델은 상당한 물리적 에너지를 제어하는 의사결정에 영향을 미칠 수 있다. 따라서 인증된 견고성은 모델 수준의 보증과 로봇이 실제로 작동해야 하는 운영 조건을 연결해야 한다. 인증 범위(Certification Boundary)는 어떤 입력, 섭동, 출력 및 운영 상태가 실제 보증의 대상인지 명확하게 정의해야 한다.

견고성 인증(Robustness Certification)은 일반적으로 정밀하게 정의된 섭동 모델(Perturbation Model)을 요구한다. 허용되는 섭동은 픽셀, 센서 측정값, 특징 표현(Feature Representation) 또는 기타 입력에 대한 제한된 변화를 나타낼 수 있다. 보증은 지정된 수학적 또는 운영적 경계 안에서만 의미를 갖는다. 공격이 해당 경계를 벗어나면 인증서(Certificate)가 자동으로 안전성을 보장하는 것은 아니다. 따라서 보안 엔지니어는 선택한 섭동 모델이 로봇의 물리적 환경에서 실제로 발생할 수 있는 위협을 현실적으로 반영하는지 확인해야 한다.

인증된 견고성은 로봇 인식에 대한 적대적 공격(Adversarial Attack)과 특히 관련성이 높다. 비전 모델(Vision Model)은 입력 이미지에 제한된 변화가 발생하더라도 안정적인 예측을 유지해야 할 수 있다. 형식적 견고성 기법(Formal Robustness Technique)은 정의된 섭동 영역(Perturbation Region) 안에서 모델의 출력이 변경될 수 없음을 입증하려고 한다. 이는 유한한 수의 적대적 사례만을 테스트하는 것보다 강력한 보증을 제공할 수 있다. 명시적으로 생성된 사례뿐만 아니라 가능한 입력의 전체 범위를 추론하는 것이 목표이기 때문이다.

그러나 인증(Certification)이 AI 모델이 보편적으로 안전하다는 의미는 아니다. 인증서는 항상 모델, 입력 영역, 섭동 크기, 출력 속성(Output Property), 검증 방법(Verification Method)에 관한 가정과 연결되어 있다. 전처리(Preprocessing), 센서 구성, 모델 아키텍처, 배포 환경 또는 위협 가정이 변경되면 기존 결론은 더 이상 유효하지 않을 수 있다. 따라서 인증된 견고성은 AI 시스템이 공격될 수 없다는 일반적인 선언이 아니라 정의된 보안 주장(Security Claim)을 뒷받침하는 증거로 취급해야 한다.

견고성 속성(Robustness Property)의 선택은 해당 모델의 물리적 역할을 반영해야 한다. 분류(Classification)의 경우 정의된 섭동 영역 안에서 예측 클래스가 변경되지 않아야 한다는 조건이 필요할 수 있다. 객체 탐지(Object Detection) 또는 분할(Segmentation)의 경우 객체의 정체성, 위치 또는 관련 장면 구조가 유지되는 것이 요구될 수 있다. 안전 필수 로봇에서는 최종적인 관심 대상이 인식 불확실성(Perception Uncertainty)이 안전하지 않은 계획 또는 제어 결정을 발생시킬 수 있는지 여부일 수도 있다. 따라서 검증 대상은 모델 실패가 발생했을 때의 물리적 결과와 연결되어야 한다.

모델과 입력이 복잡해질수록 인증은 더욱 어려워진다. 현대의 피지컬 AI 시스템은 고해상도 이미지, 라이다 포인트 클라우드(LiDAR Point Cloud), 멀티모달 관측값(Multimodal Observation), 시간적 시퀀스(Temporal Sequence), 언어 명령 또는 이러한 입력의 조합을 처리할 수 있다. 이러한 대규모 신경망(Neural Network)의 행동을 다양한 입력 영역에서 검증하려면 상당한 계산 자원과 전문화된 검증 기법이 필요할 수 있다. 따라서 어떤 구성요소에 형식적 견고성 보증을 적용할 것인지 결정할 때 비용과 확장성의 한계를 고려해야 한다.

신경망 검증(Neural Network Verification)은 수학적 추상화(Mathematical Abstraction), 제약 조건 해결(Constraint Solving), 구간 기반 방법(Interval-based Method), 선형 완화(Linear Relaxation) 또는 기타 형식적 추론 기법을 사용할 수 있다. 이러한 방법은 지정된 영역 안의 가능한 입력이 허용되지 않는 출력을 생성할 수 있는지를 판단하려고 한다. 결과의 실질적인 가치는 검증 방법이 실제 네트워크 행동을 얼마나 정확하게 표현하는지에 달려 있다. 지나치게 보수적인 경계는 모델이 실제로 견고하더라도 결론을 내리지 못하게 만들 수 있다.

따라서 인증 결과는 검증됨(Verified), 위반됨(Violated), 해결되지 않음(Unresolved)을 구분해야 한다. 검증된 영역은 정의된 가정 아래에서 지정된 속성이 유지된다는 증거를 제공한다. 위반은 정의된 영역 안에서 안전하지 않거나 바람직하지 않은 행동이 발생할 수 있음을 보여준다. 해결되지 않은 결과는 검증 절차가 어느 쪽의 결론도 확립하지 못했다는 의미이며, 견고성의 증거로 해석해서는 안 된다. 이러한 구분은 안전 필수 보증(Safety-critical Assurance)에 중요하며, 결론을 내리지 못한 분석 결과가 인증으로 잘못 해석되는 것을 방지한다.

수학적 검증만으로는 모든 실제 환경 조건을 자동으로 표현할 수 없기 때문에 물리적 검증(Physical Validation)도 여전히 필요하다. 조명 변화, 그림자, 카메라 움직임, 센서 보정 오류, 가림, 진동, 환경 반사 및 시점 변화는 단순한 섭동 모델로 표현하기 어려운 복잡한 영향을 발생시킬 수 있다. 따라서 인증된 견고성은 물리적 테스트, 시뮬레이션, 센서 융합 검증(Sensor Fusion Validation), 운영 시나리오 테스트와 결합해야 한다.

센서 융합은 서로 독립적인 센서 모달리티가 상호 보완적인 증거를 제공할 때 견고성을 강화할 수 있다. 카메라 모델이 정의된 이미지 섭동에 대해서 형식적으로 견고하더라도 전체 로봇은 다른 형태의 센서 공격에 여전히 취약할 수 있다. 반대로 카메라, 라이다, 레이더, 관성 또는 깊이 정보를 결합하면 단일 모델로는 해결하기 어려운 불일치를 탐지할 수 있다. 따라서 인증은 보증이 개별 AI 구성요소에 적용되는지 또는 전체 인식 및 의사결정 파이프라인에 적용되는지를 명확히 해야 한다.

연속적으로 작동하는 동적 환경의 로봇에서는 시간적 견고성(Temporal Robustness)도 중요하다. 모델이 개별 프레임에 대해 안정적인 예측을 생성하더라도 여러 관측값의 시퀀스에서는 일관되지 않은 행동을 생성할 수 있다. 따라서 안전 필수 검증은 시간적 속성(Temporal Property), 상태 전이(State Transition), 추적 일관성(Tracking Consistency) 또는 연속 관측값 사이의 제한된 변화 등을 고려해야 할 수 있다. 이는 연속적인 의사결정이 물리적 행동을 결정하는 자율 내비게이션, 보행, 조작 및 비행 시스템에서 특히 중요하다.

인증된 견고성과 안전 제약 사이의 관계는 명확하게 설정해야 한다. 형식적으로 검증된 인식 모델이라도 계획, 제어, 작동 또는 환경 가정이 실패하면 전체 로봇의 안전성을 보장할 수 없다. 따라서 독립적인 안전 메커니즘은 속도, 힘, 작업공간, 충돌 거리, 지오펜싱(Geofencing), 액추에이터 상태 및 기타 물리적 불변조건(Physical Invariant)을 계속 강제해야 한다. 인증은 보증의 한 계층을 강화하지만 심층 방어(Defense in Depth)를 제거해서는 안 된다.

인증된 견고성은 모델 선택과 배포 의사결정(Model Selection and Deployment Decision)에도 활용할 수 있다. 여러 후보 모델이 유사한 작업 성능을 달성한다면 관련 위협 조건에서 더 강력한 검증 보증을 제공하는 모델이 안전 필수 애플리케이션에서 더 높은 보증 수준을 제공할 수 있다. 따라서 모델 평가는 일반적인 정확도 지표뿐만 아니라 보안 지향 견고성 속성(Security-oriented Robustness Property)도 포함할 수 있다. 이를 통해 물리적 시스템을 제어하는 데 사용되는 모델을 선택하기 위한 보다 종합적인 근거를 마련할 수 있다.

모델 업데이트(Model Update)는 새로운 검증을 필요로 한다. 모델 가중치, 아키텍처, 전처리, 입력 해상도, 학습 절차 또는 최적화 구성의 작은 변경도 견고성 속성을 변경할 수 있다. 기존에 인증된 모델이 수정된 이후에도 자동으로 동일한 인증 상태를 유지한다고 간주해서는 안 된다. 따라서 지속적 통합 및 배포 프로세스(Continuous Integration and Deployment Process)는 버전이 관리되는 검증 증거를 유지하고 수정된 모델이 안전 필수 로봇에 배포되기 전에 적절한 재평가를 요구해야 한다.

인증 증거(Certification Evidence)는 정확한 모델 아티팩트(Model Artifact)와 검증 구성(Verification Configuration)에 추적 가능해야 한다. 모델 신원, 버전, 암호학적 측정값(Cryptographic Measurement), 검증 방법, 섭동 가정, 인증된 속성, 도구 버전, 검증 결과 및 승인 상태를 기록해야 한다. 이러한 정보는 조직이 정확히 무엇이 인증되었는지를 확인할 수 있게 하며, 다른 모델이나 수정된 모델이 검증된 아티팩트와 동일한 것으로 잘못 취급되는 것을 방지한다.

형식적 인증이 존재하더라도 런타임 모니터링(Runtime Monitoring)은 여전히 중요하다. 배포된 로봇은 인증된 입력 영역을 벗어난 조건, 센서 고장, 분포 변화(Distribution Shift), 환경 변화 또는 원래의 위협 모델에 포함되지 않았던 복합 공격을 경험할 수 있다. 런타임 모니터는 비정상적인 신뢰도, 센서 불일치, 분포 이상 또는 안전하지 않은 의사결정 패턴을 탐지하고 추가 검증, 성능 저하 운용(Degraded Operation) 또는 안전 상태(Safe State) 행동을 시작할 수 있다.

위협 모델(Threat Model)도 주기적으로 검토해야 한다. 공격 기법은 발전하고, 센서 구성이 변경되며, 새로운 모델 아키텍처가 도입되고, 로봇은 최초 인증 과정에서 예상하지 못했던 환경에서 작동할 수 있다. 오래된 가정에 기반한 견고성 인증서는 잘못된 보안 신뢰감을 만들 수 있다. 따라서 보안 거버넌스(Security Governance)는 주요 모델 변경, 새롭게 발견된 공격, 새로운 센서, 새로운 운영 영역 또는 물리적 권한의 중대한 변화와 같이 재분석을 요구하는 조건을 정의해야 한다.

결과의 영향이 큰 시스템에서는 인증된 견고성을 보다 광범위한 안전 및 사이버보안 보증 프로세스(Safety and Cybersecurity Assurance Process)에 통합해야 한다. 위협 모델링(Threat Modeling)은 관련 공격 조건을 식별하고, 견고성 검증(Robustness Verification)은 제한된 속성을 확립하며, 침투 테스트(Penetration Testing)는 실제 취약점을 탐색하고, 물리적 테스트는 실제 환경에서의 행동을 검증하며, 안전 메커니즘은 결과를 제한한다. 이러한 활동은 상호 보완적인 증거를 제공한다. 복잡한 피지컬 AI 시스템의 모든 실패 모드를 하나의 검증 방법만으로 포착할 수 없기 때문이다.

궁극적인 목표는 로봇의 AI 모델이 수학적으로 완벽하다는 것을 증명하는 것이 아니다. 목표는 모델의 행동을 신뢰할 수 있는 범위를 방어 가능하게 설정하고, 해당 범위를 벗어난 실패가 자동으로 통제되지 않은 물리적 행동으로 전환되지 않도록 하는 것이다. 따라서 인증된 견고성은 보안 모델, 신뢰할 수 있는 데이터, 런타임 모니터링, 독립적인 안전 제어, 통제된 배포 및 복구 메커니즘을 결합하는 보다 광범위한 아키텍처 안에서 하나의 보증 계층으로 기능한다.

피지컬 AI 보안(Physical AI Security) 구조에서 안전 필수 AI를 위한 인증된 견고성(Certified Robustness for Safety-critical AI)은 AI 의사결정 조작 이후, 그리고 AI 안전 모니터링, 학습 데이터 보안, 모델 레지스트리 보안 및 전체 피지컬 AI 보안 프레임워크 이전에 배치된다. 이러한 배치는 인증된 견고성이 AI 견고성과 물리적 안전 사이를 연결하는 역할을 한다는 점을 반영한다. 목적은 단순히 모델의 성능이 우수하다는 것을 입증하는 것이 아니라, AI 의사결정이 안전 필수 물리적 행동에 영향을 미치기 전에 정의된 적대적 조건에서 모델의 행동이 허용 가능한 범위 안에 유지된다는 증거를 확립하는 것이다.

##  

## 10.07. AI Safety Monitor as Security Boundary [w/Code]

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

An AI safety monitor can serve as a security boundary between probabilistic Physical AI intelligence and the deterministic mechanisms responsible for physical execution. The monitor does not need to understand every internal operation of an AI model. Its primary role is to independently evaluate whether proposed actions remain within predefined safety, authorization, and operational constraints before those actions can affect actuators or other safety-critical functions.

The need for an independent safety boundary arises because AI models can produce incorrect, manipulated, or unexpected decisions while continuing to operate normally from a software perspective. A model may generate a syntactically valid trajectory, navigation command, grasp action, or task instruction that is inappropriate for the actual physical situation. A safety monitor provides a separate control point capable of detecting or constraining such behavior without relying entirely on the correctness of the AI component being monitored.

The safety monitor should evaluate the relationship between AI outputs and the robot\'s current physical state. Relevant information may include velocity, acceleration, force, position, orientation, workspace occupancy, obstacle distance, actuator status, battery condition, localization confidence, and other operational variables. The monitor can compare proposed actions against these conditions and determine whether execution is permitted, must be constrained, or should be rejected.

Security boundaries become particularly important when an AI component has been exposed to adversarial inputs, compromised data, prompt injection, model manipulation, or unexpected environmental conditions. An attacker may successfully influence an AI decision without gaining direct access to the low-level controller. If the resulting command must still pass through an independently enforced safety boundary, the attacker faces an additional barrier before the manipulated decision can produce physical consequences.

A safety monitor should enforce deterministic constraints wherever practical. Examples include maximum velocity, acceleration limits, actuator force limits, joint ranges, workspace boundaries, collision distances, geofencing restrictions, payload constraints, and emergency-stop conditions. These constraints should be implemented independently from the AI reasoning process so that an AI model cannot simply redefine the conditions under which its own actions are considered safe.

The monitor should also distinguish between different levels of physical authority. A language model may generate a task description, a planner may generate a trajectory, and a controller may generate actuator commands. These outputs should not automatically receive equivalent trust. The closer an output is to direct physical actuation, the stronger the validation and authorization requirements should become. This creates a hierarchical security boundary from high-level reasoning to low-level execution.

Action validation should consider both static and dynamic constraints. A command may be safe under one condition but unsafe after the robot changes position, encounters an obstacle, loses localization confidence, or experiences an actuator fault. The safety monitor therefore needs access to current state information and should continuously evaluate whether an already approved action remains valid as the environment changes.

Temporal behavior is another important consideration. Some unsafe actions cannot be identified from a single command because the danger emerges from a sequence of individually acceptable actions. Repeated acceleration, gradual movement toward a restricted area, increasingly aggressive manipulation, or a sequence of commands that progressively violates operational intent may indicate a developing hazard. The monitor should therefore evaluate trajectories and behavioral trends rather than only isolated commands.

Sensor consistency can strengthen the security boundary. The monitor can compare AI decisions against independent sensor information such as LiDAR, radar, depth, inertial measurements, force sensing, or other trusted signals. If the AI proposes an action based on an environmental interpretation that conflicts with independent evidence, the monitor can lower the permitted authority of that action or require additional verification.

The monitor should be designed to recognize uncertainty and degraded operating conditions. AI systems may encounter unfamiliar environments, distribution shifts, sensor failures, missing observations, or conflicting inputs. Rather than forcing the robot to continue operating under uncertain conditions, the safety boundary can impose conservative limits, reduce speed, restrict manipulation, request additional sensing, or transition to a predefined safe state.

A critical design principle is that the safety monitor should not depend entirely on the same AI component that it is intended to constrain. If the AI model determines both the proposed action and whether that action is safe, a successful manipulation could compromise both decisions simultaneously. Independent logic, separately protected configuration, isolated execution, and trusted state information reduce this common-mode failure risk.

The safety monitor can also enforce authorization boundaries. A command may be physically safe but still unauthorized for the current mission or operator. For example, changing a restricted destination, entering a protected area, modifying robot configuration, or initiating a high-impact operation may require additional authorization even when the immediate motion appears physically safe. Security therefore includes both physical safety constraints and operational authority.

Policy enforcement should remain explicit and auditable. Each high-consequence action should have a clear basis for acceptance or rejection, including the relevant constraint, authorization state, robot operating mode, and contextual conditions. This makes it possible to investigate why an action was blocked or permitted and provides evidence for security analysis, safety validation, and incident response.

The safety boundary should support multiple response levels rather than only allowing or denying an action. Depending on the severity of the detected condition, the monitor may permit the action, modify its parameters, reduce operational speed, restrict available tools, request human confirmation, transition to degraded operation, or initiate an emergency stop. A graduated response allows the robot to remain useful while preventing unsafe behavior.

Physical AI systems should also protect the safety monitor itself. Its configuration, thresholds, authorization rules, trusted sensor inputs, and software should be protected against unauthorized modification. If an attacker can simply disable the monitor, increase safety limits, or change geofence boundaries, the security architecture loses its independent enforcement capability. Secure boot, signed software, protected configuration, access control, logging, and controlled updates should therefore apply to the safety boundary.

The monitor should maintain an auditable record of significant decisions. Logs can include the proposed AI action, relevant robot state, constraint evaluations, sensor consistency results, authorization decisions, intervention type, and final actuator outcome. These records are valuable for detecting repeated manipulation attempts, reconstructing incidents, validating safety behavior, and improving future security controls.

Testing should deliberately attempt to bypass the safety boundary. Security and safety evaluations can introduce adversarial perception inputs, manipulated language instructions, compromised model outputs, abnormal trajectories, sensor disagreement, unauthorized commands, and degraded hardware conditions. The objective is to determine whether the monitor continues enforcing its constraints when the upstream AI system behaves incorrectly or maliciously.

The safety monitor should also be evaluated under realistic timing conditions. A theoretically correct safety rule is insufficient if monitoring or intervention occurs too slowly to prevent physical consequences. The architecture must therefore consider sensing latency, decision latency, communication delay, controller cycle time, actuator response time, and worst-case execution behavior. Safety enforcement must operate within a time budget appropriate to the robot\'s physical dynamics.

For fleet systems, the safety boundary should remain effective even when higher-level cloud or orchestration services are compromised. Fleet commands, shared policies, mission updates, and model changes may influence many robots simultaneously. Each robot should retain local safety enforcement so that a compromised centralized service cannot directly authorize actions that violate physical or operational constraints.

Recovery behavior should also be independent and predictable. When the safety monitor detects a condition that cannot be safely resolved, the robot should transition according to predefined fallback behavior rather than relying on the potentially compromised AI system to decide what happens next. Depending on the platform, this may involve controlled stopping, maintaining a safe posture, returning to a safe location, restricting actuators, or awaiting authorized intervention.

The safety monitor therefore acts as a bridge between cybersecurity and functional safety. Cybersecurity controls attempt to prevent unauthorized manipulation, while the safety boundary limits the physical consequences if manipulation or unexpected AI behavior nevertheless occurs. This defense-in-depth relationship is particularly important for autonomous systems because no single model, security mechanism, or verification technique can guarantee correct behavior under every possible condition.

The strongest architecture treats the AI system as a source of intelligent recommendations rather than an unrestricted authority over physical action. AI outputs should pass through independent validation, authorization, deterministic safety constraints, and runtime monitoring before reaching safety-critical actuators. This separation ensures that improved AI capability does not automatically imply unrestricted physical authority.

Within the Physical AI Security structure, the AI Safety Monitor as Security Boundary follows certified robustness and precedes AI training-data security and model registry security. Volume_24_Robot_Cybersecurity Its position reflects an important architectural principle: even when model behavior has been evaluated for robustness, the final protection against unsafe or malicious physical behavior should remain outside the AI model itself. The safety monitor provides this independent enforcement layer between intelligent decision-making and real-world physical execution.

AI 안전 모니터(AI Safety Monitor)는 확률적 피지컬 AI 지능(Probabilistic Physical AI Intelligence)과 물리적 실행(Physical Execution)을 담당하는 결정론적 메커니즘(Deterministic Mechanism) 사이에서 보안 경계(Security Boundary) 역할을 수행할 수 있다. 안전 모니터는 AI 모델의 모든 내부 동작을 이해할 필요가 없다. 주요 역할은 액추에이터(Actuator) 또는 기타 안전 필수 기능(Safety-critical Function)에 영향을 미치기 전에 제안된 행동이 사전에 정의된 안전, 권한 부여(Authorization), 운영 제약(Operational Constraint)의 범위 안에 있는지를 독립적으로 평가하는 것이다.

독립적인 안전 경계(Independent Safety Boundary)가 필요한 이유는 AI 모델이 정상적인 소프트웨어 관점에서 계속 작동하면서도 잘못되거나 조작되었거나 예상하지 못한 의사결정을 생성할 수 있기 때문이다. 모델은 문법적으로 유효한 궤적, 내비게이션 명령, 파지 행동(Grasp Action) 또는 작업 지시를 생성할 수 있지만 실제 물리적 상황에는 부적절할 수 있다. 안전 모니터는 이러한 AI 구성요소의 정확성에 전적으로 의존하지 않고 이러한 행동을 탐지하거나 제한할 수 있는 별도의 통제 지점을 제공한다.

안전 모니터는 AI 출력과 로봇의 현재 물리적 상태 사이의 관계를 평가해야 한다. 관련 정보에는 속도, 가속도, 힘, 위치, 자세, 작업공간 점유(Workspace Occupancy), 장애물 거리, 액추에이터 상태, 배터리 상태, 위치 추정 신뢰도(Localization Confidence) 및 기타 운영 변수가 포함될 수 있다. 모니터는 제안된 행동을 이러한 조건과 비교하여 실행을 허용할지, 제한할지 또는 거부할지를 결정할 수 있다.

공격자가 적대적 입력(Adversarial Input), 침해된 데이터, 프롬프트 인젝션(Prompt Injection), 모델 조작(Model Manipulation) 또는 예상하지 못한 환경 조건을 통해 AI 구성요소에 영향을 미친 경우 보안 경계는 특히 중요해진다. 공격자는 저수준 제어기(Low-level Controller)에 직접 접근하지 않고도 AI 의사결정에 영향을 줄 수 있다. 결과적으로 생성된 명령이 독립적으로 강제되는 안전 경계를 통과해야 한다면, 공격자는 조작된 의사결정이 물리적 결과로 이어지기 전에 추가적인 방어 장벽을 넘어야 한다.

안전 모니터는 가능한 경우 결정론적 제약(Deterministic Constraint)을 강제해야 한다. 예로는 최대 속도, 가속도 제한, 액추에이터 힘 제한, 관절 범위(Joint Range), 작업공간 경계, 충돌 거리, 지오펜싱(Geofencing) 제한, 페이로드 제약(Payload Constraint), 비상 정지(Emergency Stop) 조건 등이 있다. 이러한 제약은 AI 추론 과정과 독립적으로 구현되어야 하며, AI 모델이 스스로 자신의 행동을 안전하다고 판단할 수 있는 조건을 변경하지 못하도록 해야 한다.

모니터는 서로 다른 수준의 물리적 권한(Physical Authority)도 구분해야 한다. 언어 모델은 작업 설명을 생성할 수 있고, 플래너(Planner)는 궤적을 생성할 수 있으며, 제어기는 액추에이터 명령을 생성할 수 있다. 이러한 출력에 동일한 수준의 신뢰를 자동으로 부여해서는 안 된다. 출력이 직접적인 물리적 작동에 가까워질수록 더 강력한 검증 및 권한 부여 요구사항을 적용해야 한다. 이를 통해 상위 수준의 추론에서 하위 수준의 실행으로 이어지는 계층적 보안 경계(Hierarchical Security Boundary)를 구축할 수 있다.

행동 검증(Action Validation)은 정적 제약(Static Constraint)과 동적 제약(Dynamic Constraint)을 모두 고려해야 한다. 특정 조건에서는 안전한 명령이 로봇의 위치가 변경되거나, 장애물을 만나거나, 위치 추정 신뢰도를 잃거나, 액추에이터 고장이 발생한 이후에는 안전하지 않을 수 있다. 따라서 안전 모니터는 현재 상태 정보에 접근해야 하며 환경이 변화함에 따라 이미 승인된 행동이 계속 유효한지를 지속적으로 평가해야 한다.

시간적 행동(Temporal Behavior)도 중요한 고려사항이다. 일부 안전하지 않은 행동은 단일 명령만으로 식별할 수 없으며 개별적으로는 허용 가능한 행동들의 연속을 통해 위험이 발생할 수 있다. 반복적인 가속, 제한 구역으로의 점진적인 이동, 점점 공격적인 조작 또는 운영 의도를 단계적으로 위반하는 명령의 연속은 발생 중인 위험을 나타낼 수 있다. 따라서 모니터는 개별 명령뿐만 아니라 궤적과 행동 추세(Behavioral Trend)도 평가해야 한다.

센서 일관성(Sensor Consistency)은 보안 경계를 강화할 수 있다. 모니터는 AI 의사결정을 라이다(LiDAR), 레이더(Radar), 깊이(Depth), 관성 측정(Inertial Measurement), 힘 감지(Force Sensing) 또는 기타 신뢰할 수 있는 신호와 비교할 수 있다. AI가 제안한 행동이 독립적인 센서 정보와 충돌하는 환경 해석을 기반으로 한다면 모니터는 해당 행동에 허용되는 권한 수준을 낮추거나 추가 검증을 요구할 수 있다.

모니터는 불확실성(Uncertainty)과 성능 저하 운영 조건(Degraded Operating Condition)을 인식하도록 설계해야 한다. AI 시스템은 익숙하지 않은 환경, 분포 변화(Distribution Shift), 센서 고장, 관측값 누락 또는 충돌하는 입력을 경험할 수 있다. 로봇이 불확실한 조건에서도 계속 작동하도록 강제하기보다는 안전 경계가 보수적인 제한을 적용하고, 속도를 낮추며, 조작 기능을 제한하고, 추가 센싱을 요청하거나, 사전에 정의된 안전 상태(Safe State)로 전환할 수 있어야 한다.

핵심 설계 원칙은 안전 모니터가 자신이 제한하려는 동일한 AI 구성요소에 전적으로 의존해서는 안 된다는 것이다. AI 모델이 행동과 해당 행동의 안전성 여부를 모두 결정한다면 성공적인 조작 공격이 두 의사결정을 동시에 침해할 수 있다. 독립적인 로직, 별도로 보호되는 구성, 격리된 실행(Isolated Execution), 신뢰할 수 있는 상태 정보(Trusted State Information)는 이러한 공통 원인 장애(Common-mode Failure) 위험을 줄일 수 있다.

안전 모니터는 권한 경계(Authorization Boundary)도 강제할 수 있어야 한다. 어떤 명령은 물리적으로 안전하더라도 현재 임무나 운영자에게 승인되지 않았을 수 있다. 예를 들어 제한된 목적지를 변경하거나, 보호 구역에 진입하거나, 로봇 구성을 수정하거나, 높은 영향의 작업을 시작하는 것은 즉각적인 움직임이 물리적으로 안전해 보이더라도 추가적인 권한 부여가 필요할 수 있다. 따라서 보안은 물리적 안전 제약뿐만 아니라 운영 권한(Operational Authority)도 포함한다.

정책 강제(Policy Enforcement)는 명시적이고 감사 가능(Auditable)해야 한다. 결과 영향이 큰 각 행동은 관련 제약, 권한 상태, 로봇 운영 모드, 컨텍스트 조건을 포함하여 해당 행동을 허용하거나 거부한 명확한 근거를 가져야 한다. 이를 통해 왜 행동이 차단되거나 허용되었는지를 조사할 수 있으며, 보안 분석, 안전 검증, 사고 대응(Incident Response)을 위한 증거를 제공할 수 있다.

안전 경계는 단순히 행동을 허용하거나 거부하는 것 이상의 여러 대응 수준(Response Level)을 지원해야 한다. 탐지된 조건의 심각도에 따라 모니터는 행동을 허용하거나, 매개변수를 수정하거나, 운영 속도를 낮추거나, 사용 가능한 도구를 제한하거나, 인간의 확인(Human Confirmation)을 요청하거나, 성능 저하 운용(Degraded Operation)으로 전환하거나, 비상 정지를 시작할 수 있다. 이러한 단계적 대응(Graduated Response)은 로봇의 유용성을 유지하면서 안전하지 않은 행동을 방지할 수 있다.

피지컬 AI 시스템은 안전 모니터 자체도 보호해야 한다. 안전 모니터의 구성, 임계값, 권한 부여 규칙, 신뢰할 수 있는 센서 입력, 소프트웨어는 무단 변경으로부터 보호되어야 한다. 공격자가 모니터를 단순히 비활성화하거나 안전 한계를 높이거나 지오펜스 경계를 변경할 수 있다면 독립적인 강제 기능을 상실하게 된다. 따라서 보안 부팅(Secure Boot), 서명된 소프트웨어(Signed Software), 보호된 구성(Protected Configuration), 접근 제어(Access Control), 로깅(Logging), 통제된 업데이트(Controlled Update)를 안전 경계에도 적용해야 한다.

모니터는 중요한 의사결정에 대한 감사 가능한 기록(Auditable Record)을 유지해야 한다. 로그에는 AI가 제안한 행동, 관련 로봇 상태, 제약 평가 결과, 센서 일관성 결과, 권한 부여 결정, 개입 유형(Intervention Type), 최종 액추에이터 결과가 포함될 수 있다. 이러한 기록은 반복적인 조작 시도를 탐지하고, 사고를 재구성하며, 안전 행동을 검증하고, 향후 보안 제어를 개선하는 데 유용하다.

테스트는 의도적으로 안전 경계를 우회하려는 시도를 포함해야 한다. 보안 및 안전 평가는 적대적 인식 입력, 조작된 언어 명령, 침해된 모델 출력, 비정상적인 궤적, 센서 불일치, 승인되지 않은 명령, 성능이 저하된 하드웨어 조건을 주입할 수 있다. 목적은 상위 수준의 AI 시스템이 잘못되거나 악의적으로 행동하더라도 모니터가 지속적으로 제약을 강제할 수 있는지를 확인하는 것이다.

안전 모니터는 현실적인 시간 조건에서도 평가해야 한다. 이론적으로 올바른 안전 규칙도 물리적 결과를 방지할 만큼 빠르게 모니터링하거나 개입하지 못한다면 충분하지 않다. 따라서 아키텍처는 센싱 지연(Sensing Latency), 의사결정 지연(Decision Latency), 통신 지연, 제어기 주기 시간(Controller Cycle Time), 액추에이터 응답 시간(Actuator Response Time), 최악 조건 실행 동작(Worst-case Execution Behavior)을 고려해야 한다. 안전 강제는 로봇의 물리적 동역학에 적합한 시간 예산(Time Budget) 안에서 작동해야 한다.

플릿 시스템(Fleet System)에서는 상위 클라우드 또는 오케스트레이션 서비스(Orchestration Service)가 침해되더라도 안전 경계가 계속 효과적으로 작동해야 한다. 플릿 명령, 공유 정책, 임무 업데이트 및 모델 변경은 동시에 여러 로봇에 영향을 줄 수 있다. 따라서 각 로봇은 중앙 집중식 서비스가 물리적 또는 운영적 제약을 위반하는 행동을 직접 승인할 수 없도록 로컬 안전 강제(Local Safety Enforcement) 기능을 유지해야 한다.

복구 행동(Recovery Behavior) 역시 독립적이고 예측 가능하도록 설계해야 한다. 안전 모니터가 안전하게 해결할 수 없는 조건을 탐지하면 로봇은 이후에 무엇을 할지를 잠재적으로 침해된 AI 시스템에 의존하지 않고 사전에 정의된 폴백 행동(Fallback Behavior)에 따라 전환해야 한다. 플랫폼에 따라 이는 통제된 정지(Controlled Stop), 안전한 자세(Safe Posture) 유지, 안전 위치로의 복귀, 액추에이터 제한 또는 승인된 개입을 기다리는 행동을 포함할 수 있다.

따라서 안전 모니터는 사이버보안(Cybersecurity)과 기능 안전(Functional Safety)을 연결하는 역할을 수행한다. 사이버보안 제어는 승인되지 않은 조작을 방지하려고 하는 반면, 안전 경계는 조작이나 예상하지 못한 AI 행동이 발생하더라도 그 물리적 결과를 제한한다. 이러한 심층 방어 관계(Defense-in-depth Relationship)는 모든 가능한 조건에서 정확한 행동을 보장할 수 있는 단일 모델, 보안 메커니즘 또는 검증 기법이 존재하지 않기 때문에 자율 시스템에서 특히 중요하다.

가장 강력한 아키텍처는 AI 시스템을 물리적 행동에 대한 제한 없는 권한자가 아니라 지능적인 권고(Intelligent Recommendation)를 제공하는 구성요소로 취급한다. AI 출력은 안전 필수 액추에이터에 도달하기 전에 독립적인 검증, 권한 부여, 결정론적 안전 제약 및 런타임 모니터링을 통과해야 한다. 이러한 분리를 통해 AI의 능력이 향상되더라도 자동으로 제한 없는 물리적 권한이 부여되는 것을 방지할 수 있다.

피지컬 AI 보안(Physical AI Security) 구조에서 보안 경계로서의 AI 안전 모니터(AI Safety Monitor as Security Boundary)는 인증된 견고성(Certified Robustness) 이후, 그리고 AI 학습 데이터 보안(AI Training Data Security)과 모델 레지스트리 보안(Model Registry Security) 이전에 배치된다. 이러한 배치는 모델의 행동이 견고성 측면에서 평가되었더라도 안전하지 않거나 악의적인 물리적 행동에 대한 최종 보호 기능은 AI 모델 외부에 유지되어야 한다는 중요한 아키텍처 원칙을 반영한다. 안전 모니터는 지능적인 의사결정과 실제 물리적 실행 사이에서 독립적인 강제 계층(Independent Enforcement Layer)을 제공한다.

##  

## 10.08. AI Training Data Security Poisoning Defense [w/Code]

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

Training data security is a foundational requirement for Physical AI because the behavior of a deployed robot can be strongly influenced by the data used to train, fine-tune, validate, and adapt its models. If an attacker can manipulate training data, the resulting model may learn incorrect associations, unsafe behaviors, hidden triggers, or biased responses. Unlike a conventional software defect, data poisoning can become embedded into learned behavior and remain difficult to identify after the original malicious data has been removed.

Training data poisoning occurs when an attacker intentionally introduces manipulated, misleading, mislabeled, corrupted, or otherwise malicious information into a dataset. The objective may be to reduce overall model accuracy, cause targeted misclassification, implant a specific trigger condition, alter a policy preference, or influence behavior in a particular operational environment. For Physical AI, the consequences can extend beyond information integrity because poisoned learning may eventually affect navigation, manipulation, locomotion, perception, or other physical actions.

The training-data attack surface extends across the complete data lifecycle. Data may originate from robot sensors, human demonstrations, public datasets, simulation environments, partner organizations, cloud storage, annotation services, or continuously collected operational experience. Each source introduces different trust assumptions. Security therefore requires organizations to maintain clear provenance for datasets and to understand how individual data sources enter training, validation, and deployment pipelines.

Data provenance is particularly important for identifying unauthorized changes. Each dataset should have traceable information describing its source, collection process, acquisition time, applicable environment, transformation history, annotation process, and version. Cryptographic hashes or other integrity measurements can help determine whether stored data has changed unexpectedly. Maintaining provenance also allows security teams to identify which trained models may have been affected when a compromised dataset is discovered.

Dataset access should follow least-privilege principles. Personnel and automated processes should receive only the permissions required to collect, annotate, transform, validate, or consume particular datasets. Write access to authoritative training repositories should be more restricted than read access, and production training datasets should not be treated as ordinary shared storage. Strong authentication, access logging, approval workflows, and controlled service credentials reduce opportunities for unauthorized modification.

Annotation integrity is another important security consideration. A poisoned dataset does not necessarily require modification of the original sensor data if an attacker can alter its labels. Incorrect object classes, bounding boxes, segmentation masks, action labels, task outcomes, or preference annotations can cause a model to learn systematically incorrect relationships. Annotation systems should therefore maintain reviewer identity, annotation history, quality checks, version information, and appropriate separation between annotation and approval activities.

Physical AI datasets require attention to the relationship between data and real-world behavior. A dataset may appear statistically reasonable while containing examples that teach unsafe associations. For example, demonstrations may consistently associate an environmental condition with an inappropriate action, or a small set of manipulated examples may encourage a policy to respond incorrectly to a particular object or situation. Security evaluation should therefore consider behavioral consequences rather than relying solely on conventional dataset quality metrics.

Poisoning may be indiscriminate or targeted. An indiscriminate attack attempts to degrade general model performance, while a targeted attack seeks a specific behavioral change under selected conditions. A targeted poisoning attack may remain difficult to detect because the overall dataset statistics and validation accuracy can remain relatively normal. Detection mechanisms should therefore examine both aggregate quality and unusual correlations between inputs, labels, environments, actions, and outcomes.

Backdoor poisoning represents a particularly serious threat to autonomous systems. An attacker may attempt to create a hidden relationship between a specific trigger and an undesired model response. The trigger could involve a visual pattern, object characteristic, environmental condition, textual instruction, or combination of features. During ordinary validation the model may appear normal, while the malicious behavior emerges only when the trigger is present. Physical AI security therefore requires testing for anomalous conditional behaviors rather than only measuring average performance.

Data validation should occur before information enters trusted training pipelines. Automated checks can identify malformed records, duplicate samples, unexpected distributions, inconsistent labels, suspicious metadata, abnormal sensor values, or unusual relationships between observations and actions. These checks should be combined with statistical analysis and targeted security review because sophisticated poisoning may be designed specifically to remain within ordinary quality boundaries.

Dataset diversity and independent validation can reduce the influence of poisoned subsets. When training information comes from multiple independent sources, a compromised source is less likely to dominate the learned representation. Separate validation datasets should also be protected from the training pipeline so that an attacker cannot modify both training and evaluation data to conceal the effect of poisoning. Independence is particularly important when the same organization controls the complete data lifecycle.

Continuous learning creates additional risk because new operational data may automatically influence future models. A robot fleet that continuously collects demonstrations, corrections, sensor observations, or task outcomes may unintentionally provide an attacker with a mechanism for influencing future training. Online learning should therefore use controlled ingestion, data quarantine, quality assessment, provenance tracking, and explicit approval gates before newly collected information becomes part of a trusted training corpus.

Security controls should extend to data transformation and preprocessing. Cropping, filtering, normalization, augmentation, synchronization, sensor fusion, and labeling transformations can alter the meaning or integrity of training examples. Each transformation stage should be version controlled and reproducible so that unexpected changes can be investigated. Training pipelines should preserve enough lineage information to determine how an original observation became the final training example consumed by the model.

Detection should also examine trained-model behavior for evidence of poisoning. Unexpected sensitivity to particular patterns, abnormal behavior on rare inputs, unusual correlations, performance discrepancies between data sources, or differences between independently trained models can indicate data integrity problems. Model-level analysis cannot prove that a dataset is clean, but it can provide an additional detection layer when combined with dataset provenance and pipeline monitoring.

If poisoning is suspected, incident response should identify the affected datasets, models, training runs, and deployed robots. The organization should preserve relevant artifacts and logs before modifying them, determine the earliest trusted dataset version, and evaluate whether downstream models inherited the compromised information. If model integrity cannot be established, affected models should be withdrawn or isolated rather than remaining in operational use simply because their normal performance appears acceptable.

Recovery requires the ability to reproduce trusted training states. Versioned datasets, reproducible preprocessing, controlled training configurations, model lineage, and signed model artifacts allow an organization to rebuild models from verified inputs. Without this capability, removing a poisoned dataset may not be sufficient because the organization may not know which historical models or intermediate artifacts were influenced by it.

Training-data security should ultimately be integrated with model security, safety monitoring, and deployment governance. Data integrity alone cannot guarantee safe behavior, while model verification alone may not reveal the origin of a learned vulnerability. A layered approach combines trusted provenance, access control, annotation validation, poisoning detection, independent evaluation, model verification, runtime monitoring, and controlled deployment to reduce the probability that manipulated training information becomes a physical safety problem.

Within the Physical AI Security structure, AI Training Data Security and Poisoning Defense is positioned after the AI Safety Monitor as Security Boundary and before AI Model Registry Security and Signing. Volume_24_Robot_Cybersecurity This placement reflects the importance of protecting the data foundation from which Physical AI capabilities are learned. The objective is not merely to preserve dataset accuracy, but to maintain trustworthy lineage from real-world observations and training examples through model development, validation, deployment, and ultimately physical robot behavior.

학습 데이터 보안(Training Data Security)은 피지컬 AI(Physical AI)에서 기본적인 보안 요구사항이다. 배포된 로봇의 행동은 모델을 학습, 파인튜닝(Fine-tuning), 검증 및 적응(Adaptation)하는 데 사용된 데이터의 영향을 강하게 받을 수 있기 때문이다. 공격자가 학습 데이터를 조작할 수 있다면 결과 모델은 잘못된 연관관계, 안전하지 않은 행동, 숨겨진 트리거(Hidden Trigger) 또는 편향된 응답을 학습할 수 있다. 일반적인 소프트웨어 결함과 달리 데이터 포이즈닝(Data Poisoning)은 학습된 행동 속에 내재될 수 있으며, 원래의 악성 데이터가 제거된 이후에도 식별하기 어려울 수 있다.

학습 데이터 포이즈닝은 공격자가 조작되었거나, 오해를 유발하거나, 잘못 라벨링되었거나, 손상되었거나, 기타 악의적인 정보를 데이터셋에 의도적으로 삽입할 때 발생한다. 공격 목적은 전체 모델 정확도를 저하시키거나, 특정 오분류를 발생시키거나, 특정 트리거 조건을 삽입하거나, 정책 선호도(Policy Preference)를 변경하거나, 특정 운영 환경에서의 행동에 영향을 주는 것일 수 있다. 피지컬 AI에서는 이러한 결과가 정보 무결성을 넘어 내비게이션(Navigation), 조작(Manipulation), 보행(Locomotion), 인식(Perception) 또는 기타 물리적 행동에 영향을 미칠 수 있다.

학습 데이터의 공격 표면(Attack Surface)은 전체 데이터 수명주기(Data Lifecycle)에 걸쳐 존재한다. 데이터는 로봇 센서, 인간 시연(Human Demonstration), 공개 데이터셋, 시뮬레이션 환경, 파트너 조직, 클라우드 스토리지, 데이터 주석 서비스 또는 지속적으로 수집되는 운영 경험(Operational Experience)에서 유입될 수 있다. 각각의 출처는 서로 다른 신뢰 가정(Trust Assumption)을 갖는다. 따라서 보안을 확보하려면 조직은 데이터셋의 명확한 출처 추적(Provenance)을 유지하고 각각의 데이터 소스가 학습, 검증 및 배포 파이프라인에 어떻게 유입되는지를 이해해야 한다.

데이터 출처 추적(Data Provenance)은 무단 변경을 식별하는 데 특히 중요하다. 각 데이터셋에는 출처, 수집 과정, 획득 시간, 적용 환경, 변환 이력, 주석 처리 과정 및 버전을 설명하는 추적 가능한 정보가 있어야 한다. 암호학적 해시(Cryptographic Hash) 또는 기타 무결성 측정값(Integrity Measurement)은 저장된 데이터가 예상하지 못하게 변경되었는지를 확인하는 데 도움이 될 수 있다. 출처 정보를 유지하면 침해된 데이터셋이 발견되었을 때 어떤 학습 모델이 영향을 받을 수 있는지를 보안팀이 식별할 수 있다.

데이터셋 접근(Data Access)은 최소 권한 원칙(Least-privilege Principle)을 따라야 한다. 담당자와 자동화된 프로세스에는 특정 데이터셋을 수집, 주석 처리, 변환, 검증 또는 사용하는 데 필요한 권한만 제공해야 한다. 신뢰된 학습 저장소(Trusted Training Repository)에 대한 쓰기 권한은 읽기 권한보다 엄격하게 제한해야 하며, 운영 학습 데이터셋을 일반적인 공유 스토리지처럼 취급해서는 안 된다. 강력한 인증(Authentication), 접근 로깅(Access Logging), 승인 워크플로(Approval Workflow), 통제된 서비스 자격 증명(Service Credential)은 무단 변경의 기회를 줄인다.

주석 무결성(Annotation Integrity)도 중요한 보안 고려사항이다. 공격자는 원본 센서 데이터를 수정하지 않고도 라벨을 변경하여 데이터셋을 오염시킬 수 있다. 잘못된 객체 클래스, 바운딩 박스(Bounding Box), 분할 마스크(Segmentation Mask), 행동 라벨(Action Label), 작업 결과 또는 선호도 주석(Preference Annotation)은 모델이 체계적으로 잘못된 관계를 학습하도록 만들 수 있다. 따라서 주석 시스템은 검토자 신원(Reviewer Identity), 주석 이력, 품질 검사, 버전 정보 및 주석과 승인 활동 사이의 적절한 분리를 유지해야 한다.

피지컬 AI 데이터셋은 데이터와 실제 세계의 행동 사이의 관계에도 주의를 기울여야 한다. 데이터셋이 통계적으로 합리적으로 보이더라도 안전하지 않은 연관관계를 학습시키는 사례를 포함할 수 있다. 예를 들어 시연 데이터가 특정 환경 조건과 부적절한 행동을 지속적으로 연결하거나, 소수의 조작된 사례가 특정 객체 또는 상황에 대해 정책이 잘못 반응하도록 유도할 수 있다. 따라서 보안 평가는 일반적인 데이터셋 품질 지표에만 의존하지 않고 행동상의 결과도 고려해야 한다.

포이즈닝은 무차별적 공격(Indiscriminate Attack) 또는 표적 공격(Targeted Attack)의 형태로 발생할 수 있다. 무차별적 공격은 일반적인 모델 성능을 저하시키려는 반면, 표적 공격은 특정 조건에서 특정 행동 변화를 유도하려고 한다. 표적 포이즈닝 공격은 전체적인 데이터셋 통계와 검증 정확도가 정상적으로 유지될 수 있기 때문에 탐지하기 어려울 수 있다. 따라서 탐지 메커니즘은 전체적인 품질뿐만 아니라 입력, 라벨, 환경, 행동 및 결과 사이의 비정상적인 연관관계도 분석해야 한다.

백도어 포이즈닝(Backdoor Poisoning)은 자율 시스템에 특히 심각한 위협이다. 공격자는 특정 트리거와 원하지 않는 모델 응답 사이에 숨겨진 관계를 생성하려 할 수 있다. 트리거는 시각적 패턴, 객체 특성, 환경 조건, 텍스트 명령 또는 여러 특징의 조합일 수 있다. 일반적인 검증 과정에서는 모델이 정상적으로 보이지만 트리거가 존재할 때만 악의적인 행동이 나타날 수 있다. 따라서 피지컬 AI 보안에서는 평균 성능뿐만 아니라 비정상적인 조건부 행동(Conditional Behavior)에 대한 테스트도 필요하다.

데이터 검증(Data Validation)은 정보가 신뢰된 학습 파이프라인에 들어가기 전에 수행해야 한다. 자동화된 검사는 형식이 잘못된 레코드, 중복 샘플, 예상하지 못한 분포, 일관성이 없는 라벨, 의심스러운 메타데이터, 비정상적인 센서 값 또는 관측값과 행동 사이의 특이한 관계를 식별할 수 있다. 이러한 검사는 통계적 분석과 표적화된 보안 검토를 함께 적용해야 한다. 정교한 포이즈닝은 일반적인 품질 기준 안에 남도록 의도적으로 설계될 수 있기 때문이다.

데이터셋의 다양성과 독립적인 검증(Independent Validation)은 오염된 데이터 부분집합의 영향을 줄일 수 있다. 학습 정보가 여러 독립적인 출처에서 제공되면 하나의 침해된 출처가 학습된 표현을 지배할 가능성이 낮아진다. 또한 독립적인 검증 데이터셋은 학습 파이프라인과 분리하여 보호해야 한다. 이를 통해 공격자가 학습 데이터와 평가 데이터를 모두 변경하여 포이즈닝의 영향을 숨기는 것을 방지할 수 있다. 이러한 독립성은 동일한 조직이 전체 데이터 수명주기를 관리하는 경우 특히 중요하다.

지속적 학습(Continuous Learning)은 새로운 운영 데이터가 미래의 모델에 자동으로 영향을 미칠 수 있기 때문에 추가적인 위험을 발생시킨다. 시연, 수정, 센서 관측값 또는 작업 결과를 지속적으로 수집하는 로봇 플릿은 공격자에게 향후 학습에 영향을 미칠 수 있는 경로를 제공할 수 있다. 따라서 온라인 학습(Online Learning)은 통제된 데이터 유입, 데이터 격리(Data Quarantine), 품질 평가, 출처 추적 및 새롭게 수집된 정보가 신뢰된 학습 데이터에 포함되기 전에 명시적인 승인 절차를 사용해야 한다.

보안 제어는 데이터 변환 및 전처리(Data Transformation and Preprocessing)에도 적용되어야 한다. 크롭(Cropping), 필터링(Filtering), 정규화(Normalization), 증강(Augmentation), 동기화(Synchronization), 센서 융합(Sensor Fusion), 라벨링 변환은 학습 사례의 의미 또는 무결성을 변경할 수 있다. 각 변환 단계는 버전 관리하고 재현 가능하게 만들어 예상하지 못한 변경을 조사할 수 있도록 해야 한다. 학습 파이프라인은 원본 관측값이 최종적으로 모델에 입력되는 학습 사례로 어떻게 변환되었는지를 확인할 수 있을 정도의 계보(Lineage) 정보를 보존해야 한다.

탐지는 학습된 모델의 행동에서도 포이즈닝의 증거를 찾아야 한다. 특정 패턴에 대한 예상하지 못한 민감도, 희귀한 입력에 대한 비정상적인 행동, 특이한 연관관계, 데이터 소스 간 성능 차이 또는 독립적으로 학습된 모델 사이의 차이는 데이터 무결성 문제를 나타낼 수 있다. 모델 수준 분석(Model-level Analysis)만으로 데이터셋이 깨끗하다는 것을 증명할 수는 없지만, 데이터셋 출처 추적과 파이프라인 모니터링을 결합하면 추가적인 탐지 계층을 제공할 수 있다.

포이즈닝이 의심되는 경우 사고 대응(Incident Response)은 영향을 받은 데이터셋, 모델, 학습 실행(Training Run), 배포된 로봇을 식별해야 한다. 조직은 데이터를 변경하기 전에 관련 아티팩트(Artifact)와 로그를 보존하고, 가장 이른 신뢰 가능한 데이터셋 버전을 확인하며, 이후 모델이 침해된 정보를 상속했는지를 평가해야 한다. 모델 무결성을 확립할 수 없다면 정상적인 성능이 유지된다는 이유만으로 영향을 받은 모델을 계속 운영해서는 안 되며, 해당 모델을 철회하거나 격리해야 한다.

복구(Recovery)를 위해서는 신뢰할 수 있는 학습 상태(Trusted Training State)를 재현할 수 있는 능력이 필요하다. 버전이 관리되는 데이터셋, 재현 가능한 전처리, 통제된 학습 구성, 모델 계보(Model Lineage), 서명된 모델 아티팩트(Signed Model Artifact)는 조직이 검증된 입력으로부터 모델을 다시 구축할 수 있도록 한다. 이러한 능력이 없다면 오염된 데이터셋을 제거하는 것만으로는 충분하지 않을 수 있다. 조직은 어떤 과거 모델이나 중간 아티팩트가 영향을 받았는지를 알 수 없기 때문이다.

학습 데이터 보안은 궁극적으로 모델 보안(Model Security), 안전 모니터링(Safety Monitoring), 배포 거버넌스(Deployment Governance)와 통합되어야 한다. 데이터 무결성만으로 안전한 행동을 보장할 수 없으며, 모델 검증만으로 학습된 취약점의 원인을 발견할 수 있는 것도 아니다. 다층 접근법(Layered Approach)은 신뢰할 수 있는 출처 추적, 접근 제어, 주석 검증, 포이즈닝 탐지, 독립적인 평가, 모델 검증, 런타임 모니터링(Runtime Monitoring), 통제된 배포를 결합하여 조작된 학습 정보가 물리적 안전 문제로 전환될 가능성을 줄인다.

피지컬 AI 보안(Physical AI Security) 구조에서 AI 학습 데이터 보안 및 포이즈닝 방어(AI Training Data Security and Poisoning Defense)는 보안 경계로서의 AI 안전 모니터(AI Safety Monitor as Security Boundary) 이후, 그리고 AI 모델 레지스트리 보안 및 서명(AI Model Registry Security and Signing) 이전에 배치된다. 이러한 배치는 피지컬 AI 역량이 학습되는 데이터 기반(Data Foundation)을 보호하는 것이 중요하다는 점을 반영한다. 목표는 단순히 데이터셋의 정확성을 유지하는 것이 아니라 실제 세계의 관측값과 학습 사례에서 시작하여 모델 개발, 검증, 배포, 그리고 궁극적으로 로봇의 물리적 행동에 이르는 신뢰할 수 있는 계보(Trustworthy Lineage)를 유지하는 것이다.

##  

## 10.09. AI Model Registry Security and Signing [w/Code]

![](images/image9.png){width="7.268055555555556in" height="7.268055555555556in"}

An AI model registry is a central security control for Physical AI because it manages the model artifacts that can ultimately influence robot perception, reasoning, planning, and physical action. The registry should provide a trusted location where approved models are identified, versioned, stored, and associated with their deployment status. Without strong registry security, an attacker may replace an approved model, introduce an unauthorized version, or distribute a modified artifact across multiple robots.

Model identity must remain unambiguous throughout the deployment lifecycle. Each model should have a unique identifier, version, provenance information, integrity measurement, applicable platform, and defined approval status. These attributes allow a robot or deployment service to distinguish an authorized model from an artifact with a similar name. Model identity should remain associated with the exact artifact rather than relying only on filenames, directory locations, or human-readable version labels.

Cryptographic signing provides an important mechanism for establishing model authenticity and integrity. An approved model artifact can be digitally signed by an authorized signing authority, allowing the receiving robot or deployment system to verify that the artifact originated from a trusted source and has not been modified after signing. Signature verification should occur before the model is loaded or activated, particularly when the model can influence safety-critical perception, planning, or control functions.

The signing process itself must be strongly protected because compromise of a signing key can undermine the entire model trust chain. Signing keys should be stored using appropriate protected mechanisms, with access restricted to authorized processes and personnel. Key usage should be auditable, and key rotation, expiration, revocation, and recovery procedures should be defined. A model should never be considered trustworthy merely because it carries a signature if the signing authority or key lifecycle cannot itself be trusted.

Model registry access should follow least-privilege principles. Developers may require permission to upload candidate models, validation systems may need to read and evaluate artifacts, and deployment services may need access only to models that have passed approval. Administrative capabilities such as changing model status, deleting artifacts, modifying metadata, or controlling release channels should be more restricted. Separating these privileges reduces the possibility that a compromised account can directly promote an unverified model into production.

The registry should distinguish clearly between development, testing, validation, staging, and production model states. A model uploaded for experimentation should not automatically become eligible for deployment. Promotion between states should require defined validation and authorization conditions. This separation creates an explicit security boundary between experimental artifacts and models that are permitted to influence physical robots.

Model provenance should be preserved as part of registry metadata. The registry should maintain information about the originating model, training or fine-tuning process, dataset lineage, configuration, validation results, security assessments, and approval history where applicable. Provenance allows security and engineering teams to determine how a deployed model was created and which systems may be affected when a vulnerability or integrity problem is discovered.

Integrity measurements should identify the exact artifact that was approved. Cryptographic hashes can provide a compact representation of model contents and allow deployment systems to detect unexpected changes. If the measured artifact differs from the approved value, the deployment process should treat the model as untrusted until the discrepancy has been investigated. This prevents an attacker from modifying a model while retaining the appearance of an approved filename or version.

Model signing should also be integrated with secure deployment. A robot should verify the signature, model identity, integrity measurement, compatibility requirements, and authorization state before activating a new model. The deployment mechanism should reject unsigned, incorrectly signed, expired, revoked, or otherwise unauthorized artifacts. Verification should be performed locally where appropriate so that temporary loss or compromise of a central service cannot force a robot to accept an untrusted model.

Compatibility validation is important because a correctly signed model may still be inappropriate for a particular robot. A model may require a specific hardware accelerator, sensor configuration, software environment, firmware version, or input representation. Registry metadata should therefore identify applicable deployment conditions. The deployment system should verify these conditions before activation so that an authentic model is not treated as safe merely because its cryptographic signature is valid.

Model version management should prevent unauthorized rollback to an older artifact. An attacker may attempt to replace a current model with an older version containing a known vulnerability or previously exploitable behavior. Version policies should therefore define acceptable model generations and prevent unauthorized downgrade operations. When rollback is legitimately required for recovery, the selected version should still pass signature, integrity, authorization, and compatibility checks.

Revocation is necessary when a model is discovered to be compromised, vulnerable, obsolete, or otherwise unsuitable for deployment. The registry should maintain a mechanism for marking affected artifacts as revoked and communicating that status to deployment systems. Robots should reject revoked models even when the artifact has a technically valid signature. This distinction is important because cryptographic validity establishes authenticity and integrity at signing time, while revocation establishes whether the artifact remains authorized for operational use.

Model registries should maintain detailed audit records. Important events include artifact creation, upload, modification of metadata, signing, validation, approval, promotion, deployment, rollback, revocation, and administrative access. Logs should identify the responsible account or service, time of operation, affected model, and relevant authorization context. These records support incident investigation and can reveal attempts to manipulate the model supply chain.

The registry should also protect its metadata because security decisions may depend on information stored alongside the model. An attacker who cannot modify the model file directly may attempt to change its version, approval status, deployment target, compatibility information, or security classification. Metadata therefore requires integrity protection and access control comparable to the model artifacts themselves.

Automated deployment pipelines should not bypass registry security controls. Continuous integration and deployment systems may move models rapidly between training, validation, and production environments, creating opportunities for an attacker to exploit automation. Every automated promotion should remain subject to authentication, authorization, signature verification, validation evidence, and policy checks. Automation should increase deployment efficiency without removing the security gates that establish trust.

For Physical AI fleets, registry security must extend beyond a central repository to the complete model distribution path. Models may travel through cloud services, edge servers, network connections, robot gateways, removable media, or local storage before reaching the final execution environment. Each stage should preserve artifact identity and integrity. A secure registry is therefore only one part of a broader model supply-chain security architecture.

Offline and intermittently connected robots require particular consideration. A robot may need to verify and activate an approved model without continuous access to the central registry. Local trust anchors, cached authorization information, signed metadata, and controlled revocation information can support secure operation under limited connectivity. The design should nevertheless prevent stale authorization information from allowing indefinitely outdated or revoked models to remain active.

The registry should support recovery after a security incident. If a signing key is compromised or a model repository is suspected of unauthorized modification, the organization should be able to identify affected artifacts, invalidate compromised trust relationships, issue new signing credentials, and deploy verified replacement models. Recovery procedures should be tested in advance because model trust cannot be restored reliably if the organization lacks a known-good registry state and a controlled re-signing process.

Model registry security should also be connected to training-data security and model validation. A registry should not simply store models; it should preserve evidence showing that a model passed the required development, security, robustness, and safety evaluation stages. A model that has been correctly signed but has never completed required validation should not automatically qualify for production deployment. Trust therefore depends on both cryptographic integrity and governance evidence.

Security monitoring should identify unusual registry behavior. Unexpected uploads, repeated failed signature checks, unauthorized promotion attempts, unusual administrative access, abnormal deployment patterns, or simultaneous model changes across multiple robots may indicate an attack against the model supply chain. Registry events should be correlated with deployment, identity, network, and robot telemetry to determine whether suspicious activity has progressed into physical systems.

The security boundary should ultimately continue into the robot itself. Even a trusted registry cannot guarantee that the deployed model remains protected if local storage, execution environments, or update mechanisms are compromised. Robots should therefore verify model artifacts at activation and, where appropriate, maintain runtime identity or integrity measurements that allow the deployed state to be compared against the approved registry state.

A strong AI model registry establishes a chain of trust from model creation through validation, signing, approval, distribution, activation, monitoring, revocation, and retirement. Each stage should preserve model identity and integrity while enforcing appropriate authorization. This lifecycle approach reduces the possibility that an attacker can introduce a modified model into a Physical AI system or cause an approved model to be replaced without detection.

Within the Physical AI Security structure, AI Model Registry Security and Signing follows AI Training Data Security and Poisoning Defense and precedes the Physical AI Security Framework Design. Volume_24_Robot_Cybersecurity Its position reflects the registry\'s role as a final trust-management layer between model development and operational deployment. The objective is not merely to store model files securely, but to ensure that only authenticated, integrity-verified, authorized, validated, and appropriately versioned AI models are permitted to influence physical robot behavior.

AI 모델 레지스트리(AI Model Registry)는 피지컬 AI(Physical AI)에서 중요한 보안 통제 수단(Security Control)이다. 레지스트리는 궁극적으로 로봇의 인식(Perception), 추론(Reasoning), 계획(Planning), 물리적 행동(Physical Action)에 영향을 미칠 수 있는 모델 아티팩트(Model Artifact)를 관리하기 때문이다. 레지스트리는 승인된 모델을 식별하고, 버전을 관리하며, 저장하고, 배포 상태와 연결할 수 있는 신뢰된 위치(Trusted Location)를 제공해야 한다. 강력한 레지스트리 보안이 없다면 공격자는 승인된 모델을 교체하거나, 승인되지 않은 버전을 삽입하거나, 수정된 아티팩트를 여러 로봇에 배포할 수 있다.

모델 신원(Model Identity)은 배포 수명주기(Deployment Lifecycle) 전체에서 명확하게 유지되어야 한다. 각 모델에는 고유 식별자(Unique Identifier), 버전, 출처 정보(Provenance Information), 무결성 측정값(Integrity Measurement), 적용 가능한 플랫폼, 정의된 승인 상태(Approval Status)가 있어야 한다. 이러한 속성을 통해 로봇이나 배포 서비스는 이름이 유사한 다른 아티팩트와 승인된 모델을 구분할 수 있다. 모델 신원은 파일 이름, 디렉터리 위치 또는 사람이 읽을 수 있는 버전 라벨에만 의존하지 않고 정확한 아티팩트 자체와 연결되어야 한다.

암호학적 서명(Cryptographic Signing)은 모델의 진위성(Authenticity)과 무결성(Integrity)을 확립하는 중요한 수단이다. 승인된 모델 아티팩트에는 권한 있는 서명 기관(Authorized Signing Authority)이 디지털 서명(Digital Signature)을 적용할 수 있으며, 이를 통해 수신하는 로봇이나 배포 시스템은 해당 아티팩트가 신뢰된 출처에서 생성되었고 서명 이후 변경되지 않았음을 검증할 수 있다. 특히 안전 필수 인식(Safety-critical Perception), 계획 또는 제어에 영향을 미칠 수 있는 모델은 로딩되거나 활성화되기 전에 서명을 검증해야 한다.

서명 과정 자체도 강력하게 보호해야 한다. 서명 키(Signing Key)가 침해되면 전체 모델 신뢰 체인(Model Trust Chain)이 무력화될 수 있기 때문이다. 서명 키는 적절하게 보호되는 메커니즘을 사용하여 저장하고, 권한이 있는 프로세스와 담당자만 접근할 수 있도록 제한해야 한다. 키 사용은 감사 가능해야 하며, 키 교체(Key Rotation), 만료(Expiration), 폐기(Revocation), 복구(Recovery) 절차를 정의해야 한다. 서명 기관이나 키 수명주기(Key Lifecycle) 자체를 신뢰할 수 없다면 모델이 서명을 가지고 있다는 이유만으로 신뢰해서는 안 된다.

모델 레지스트리 접근(Model Registry Access)은 최소 권한 원칙(Least-privilege Principle)을 따라야 한다. 개발자는 후보 모델을 업로드할 권한이 필요할 수 있고, 검증 시스템은 아티팩트를 읽고 평가할 권한이 필요하며, 배포 서비스는 승인된 모델에만 접근하면 될 수 있다. 모델 상태 변경, 아티팩트 삭제, 메타데이터 수정 또는 릴리스 채널 제어와 같은 관리자 기능은 더욱 엄격하게 제한해야 한다. 이러한 권한을 분리하면 침해된 계정 하나가 검증되지 않은 모델을 직접 운영 환경으로 승격시키는 것을 방지할 수 있다.

레지스트리는 개발(Development), 테스트(Testing), 검증(Validation), 스테이징(Staging), 운영(Production) 모델 상태를 명확하게 구분해야 한다. 실험을 위해 업로드된 모델이 자동으로 배포 가능한 모델이 되어서는 안 된다. 상태 간 승격(Promotion)은 정의된 검증 및 권한 부여 조건을 충족해야 한다. 이러한 분리는 실험용 아티팩트와 실제 물리적 로봇에 영향을 미칠 수 있는 모델 사이에 명확한 보안 경계(Security Boundary)를 만든다.

모델 출처(Model Provenance)는 레지스트리 메타데이터의 일부로 보존해야 한다. 레지스트리는 가능한 경우 원본 모델, 학습 또는 파인튜닝 과정, 데이터셋 계보(Dataset Lineage), 구성(Configuration), 검증 결과, 보안 평가(Security Assessment), 승인 이력에 관한 정보를 유지해야 한다. 출처 정보는 보안 및 엔지니어링 팀이 배포된 모델이 어떻게 생성되었는지를 확인할 수 있도록 하며, 취약점이나 무결성 문제가 발견되었을 때 어떤 시스템이 영향을 받을 수 있는지를 판단할 수 있도록 한다.

무결성 측정값은 승인된 정확한 아티팩트를 식별해야 한다. 암호학적 해시(Cryptographic Hash)는 모델 콘텐츠를 간결하게 표현하며 배포 시스템이 예상하지 못한 변경을 탐지할 수 있도록 한다. 측정된 아티팩트가 승인된 값과 다르면 배포 시스템은 해당 모델을 조사하기 전까지 신뢰할 수 없는 것으로 처리해야 한다. 이를 통해 공격자가 승인된 파일 이름이나 버전이라는 외형을 유지하면서 모델을 수정하는 것을 방지할 수 있다.

모델 서명(Model Signing)은 안전한 배포(Secure Deployment)와도 통합되어야 한다. 로봇은 새로운 모델을 활성화하기 전에 서명, 모델 신원, 무결성 측정값, 호환성 요구사항(Compatibility Requirement), 승인 상태를 검증해야 한다. 배포 메커니즘은 서명이 없거나, 잘못된 서명이 적용되었거나, 만료되었거나, 폐기되었거나, 기타 방식으로 승인되지 않은 아티팩트를 거부해야 한다. 적절한 경우 검증은 로컬에서 수행하여 중앙 서비스의 일시적인 장애나 침해가 로봇으로 하여금 신뢰할 수 없는 모델을 수용하도록 강제하지 못하게 해야 한다.

호환성 검증(Compatibility Validation)도 중요하다. 올바르게 서명된 모델이라도 특정 로봇에는 적합하지 않을 수 있기 때문이다. 모델은 특정 하드웨어 가속기(Hardware Accelerator), 센서 구성, 소프트웨어 환경, 펌웨어 버전 또는 입력 표현(Input Representation)을 요구할 수 있다. 따라서 레지스트리 메타데이터는 적용 가능한 배포 조건을 식별해야 한다. 배포 시스템은 활성화 전에 이러한 조건을 검증해야 하며, 암호학적 서명이 유효하다는 이유만으로 인증된 모델을 안전한 모델로 간주해서는 안 된다.

모델 버전 관리(Model Version Management)는 승인되지 않은 이전 버전으로의 롤백(Rollback)을 방지해야 한다. 공격자는 현재 모델을 알려진 취약점이나 과거에 악용 가능한 행동을 포함한 이전 모델로 교체하려 할 수 있다. 따라서 버전 정책은 허용되는 모델 세대를 정의하고 승인되지 않은 다운그레이드(Downgrade) 작업을 방지해야 한다. 복구를 위해 롤백이 정당하게 필요한 경우에도 선택된 버전은 서명, 무결성, 권한 부여 및 호환성 검사를 통과해야 한다.

모델이 침해되었거나, 취약하거나, 오래되었거나, 기타 운영에 부적합한 것으로 확인되면 폐기(Revocation)가 필요하다. 레지스트리는 영향을 받은 아티팩트를 폐기 상태로 표시하고 그 상태를 배포 시스템에 전달할 수 있는 메커니즘을 유지해야 한다. 아티팩트가 기술적으로 유효한 서명을 가지고 있더라도 로봇은 폐기된 모델을 거부해야 한다. 이는 암호학적 유효성이 서명 시점의 진위성과 무결성을 확인하는 반면, 폐기는 해당 아티팩트가 현재도 운영에 사용할 수 있도록 승인되었는지를 결정하기 때문에 중요하다.

모델 레지스트리는 상세한 감사 기록(Audit Record)을 유지해야 한다. 중요한 이벤트에는 아티팩트 생성, 업로드, 메타데이터 변경, 서명, 검증, 승인, 승격, 배포, 롤백, 폐기 및 관리자 접근이 포함된다. 로그에는 작업을 수행한 계정 또는 서비스, 작업 시간, 영향을 받은 모델 및 관련 권한 부여 컨텍스트가 기록되어야 한다. 이러한 기록은 사고 조사를 지원하며 모델 공급망(Model Supply Chain)을 조작하려는 시도를 발견하는 데 도움이 될 수 있다.

레지스트리는 모델과 함께 저장되는 메타데이터도 보호해야 한다. 모델 파일 자체를 직접 수정할 수 없는 공격자가 모델의 버전, 승인 상태, 배포 대상, 호환성 정보 또는 보안 분류(Security Classification)를 변경하려 할 수 있기 때문이다. 따라서 메타데이터에는 모델 아티팩트와 유사한 수준의 무결성 보호와 접근 제어를 적용해야 한다.

자동화된 배포 파이프라인(Automated Deployment Pipeline)은 레지스트리 보안 제어를 우회해서는 안 된다. 지속적 통합 및 배포 시스템(Continuous Integration and Deployment System)은 학습, 검증, 운영 환경 사이에서 모델을 빠르게 이동시킬 수 있으며, 이러한 자동화 과정은 공격자가 악용할 수 있는 기회를 제공할 수 있다. 모든 자동화된 승격 작업은 인증, 권한 부여, 서명 검증, 검증 증거 및 정책 검사를 계속 거쳐야 한다. 자동화는 배포 효율성을 높여야 하지만 신뢰를 확립하는 보안 게이트(Security Gate)를 제거해서는 안 된다.

피지컬 AI 플릿(Physical AI Fleet)의 경우 레지스트리 보안은 중앙 저장소를 넘어 전체 모델 배포 경로(Model Distribution Path)로 확장되어야 한다. 모델은 최종 실행 환경에 도달하기 전에 클라우드 서비스, 엣지 서버, 네트워크 연결, 로봇 게이트웨이, 이동식 미디어 또는 로컬 스토리지를 거칠 수 있다. 각 단계에서는 아티팩트의 신원과 무결성을 유지해야 한다. 따라서 안전한 레지스트리는 더 광범위한 모델 공급망 보안(Model Supply Chain Security) 아키텍처의 한 구성요소일 뿐이다.

오프라인 또는 간헐적으로 연결되는 로봇(Intermittently Connected Robot)은 특별한 고려가 필요하다. 로봇은 중앙 레지스트리에 지속적으로 연결되지 않은 상태에서도 승인된 모델을 검증하고 활성화해야 할 수 있다. 로컬 신뢰 앵커(Local Trust Anchor), 캐시된 권한 부여 정보(Cached Authorization Information), 서명된 메타데이터, 통제된 폐기 정보는 제한된 연결 환경에서도 안전한 운영을 지원할 수 있다. 그러나 설계상 오래된 권한 정보가 무기한으로 유지되어 오래되었거나 폐기된 모델이 계속 활성화되는 것을 방지해야 한다.

레지스트리는 보안 사고 이후의 복구(Recovery)를 지원해야 한다. 서명 키가 침해되었거나 모델 저장소가 무단으로 변경되었다고 의심되는 경우 조직은 영향을 받은 아티팩트를 식별하고, 침해된 신뢰 관계를 무효화하며, 새로운 서명 자격 증명을 발급하고, 검증된 대체 모델을 배포할 수 있어야 한다. 모델 신뢰를 안정적으로 복구하려면 알려진 정상 상태의 레지스트리와 통제된 재서명(Re-signing) 절차가 필요하기 때문에 복구 절차는 사전에 테스트해야 한다.

모델 레지스트리 보안은 학습 데이터 보안(Training Data Security) 및 모델 검증(Model Validation)과도 연결되어야 한다. 레지스트리는 단순히 모델을 저장하는 곳이 아니라 모델이 필요한 개발, 보안, 견고성(Robustness), 안전 평가를 통과했다는 증거를 보존해야 한다. 올바르게 서명되었지만 필수 검증을 완료하지 않은 모델이 자동으로 운영 배포 자격을 가져서는 안 된다. 따라서 신뢰는 암호학적 무결성뿐만 아니라 거버넌스 증거(Governance Evidence)에 의해서도 결정된다.

보안 모니터링(Security Monitoring)은 비정상적인 레지스트리 행동을 식별해야 한다. 예상하지 못한 업로드, 반복적인 서명 검증 실패, 승인되지 않은 승격 시도, 비정상적인 관리자 접근, 특이한 배포 패턴 또는 여러 로봇에서 동시에 발생하는 모델 변경은 모델 공급망에 대한 공격을 나타낼 수 있다. 레지스트리 이벤트는 배포, 신원, 네트워크 및 로봇 텔레메트리(Robot Telemetry)와 상관 분석하여 의심스러운 활동이 실제 물리적 시스템으로 확산되었는지를 판단해야 한다.

보안 경계(Security Boundary)는 궁극적으로 로봇 자체까지 이어져야 한다. 신뢰할 수 있는 레지스트리라고 해서 로컬 스토리지, 실행 환경 또는 업데이트 메커니즘이 침해되었을 때 배포된 모델이 계속 보호된다는 것을 보장할 수는 없다. 따라서 로봇은 모델을 활성화할 때 아티팩트를 검증해야 하며, 필요한 경우 런타임 신원(Runtime Identity) 또는 무결성 측정값을 유지하여 실제 배포 상태를 승인된 레지스트리 상태와 비교할 수 있어야 한다.

강력한 AI 모델 레지스트리는 모델 생성부터 검증, 서명, 승인, 배포, 활성화, 모니터링, 폐기 및 사용 종료(Retirement)에 이르는 신뢰 체인(Chain of Trust)을 구축한다. 각 단계에서는 적절한 권한 부여를 적용하면서 모델의 신원과 무결성을 유지해야 한다. 이러한 수명주기 접근법(Lifecycle Approach)은 공격자가 수정된 모델을 피지컬 AI 시스템에 삽입하거나 승인된 모델을 탐지되지 않은 상태로 교체하는 가능성을 줄인다.

피지컬 AI 보안(Physical AI Security) 구조에서 AI 모델 레지스트리 보안 및 서명(AI Model Registry Security and Signing)은 AI 학습 데이터 보안 및 포이즈닝 방어(AI Training Data Security and Poisoning Defense) 이후에 위치하며 피지컬 AI 보안 프레임워크 설계(Physical AI Security Framework Design)에 앞서 배치된다. 이러한 위치는 모델 개발과 운영 배포 사이에서 레지스트리가 최종적인 신뢰 관리 계층(Trust Management Layer)으로 기능한다는 점을 반영한다. 목적은 단순히 모델 파일을 안전하게 저장하는 것이 아니라 인증되고, 무결성이 검증되며, 권한이 부여되고, 검증되었으며, 적절한 버전으로 관리되는 AI 모델만이 실제 로봇의 물리적 행동에 영향을 미칠 수 있도록 보장하는 것이다.

##  

## 10.10. Physical AI Security Framework Design

![](images/image10.png){width="7.268055555555556in" height="7.268055555555556in"}

A Physical AI security framework must integrate cybersecurity, AI security, functional safety, and physical operational controls into a single lifecycle architecture. The purpose is not simply to protect networks or AI models independently, but to prevent compromise of digital intelligence from becoming an uncontrolled physical consequence. The framework should therefore establish security boundaries from data acquisition and model development through inference, decision-making, actuation, fleet operation, incident response, and system retirement.

The framework begins with a clear understanding of the unique security risks created when AI is connected to physical robots. Physical AI systems combine perception, learned models, planning, control, sensors, actuators, communication networks, and operational environments. A weakness in one layer can propagate into another layer and ultimately influence physical behavior. Security architecture must therefore consider both conventional cyber threats and attacks that manipulate perception, reasoning, decision-making, or learned behavior.

Trust boundaries should be explicitly defined across the complete Physical AI pipeline. Sensor data, training datasets, AI models, external information, user instructions, AI-generated decisions, policy controls, and actuator commands should not automatically receive the same level of trust. Each boundary should identify the source, required authentication, integrity protection, authorization requirements, validation method, and conditions under which information can cross into a higher-trust domain.

AI models should be treated as controlled security assets rather than ordinary software packages. Model development must maintain provenance from training data through training configuration, evaluation, validation, signing, registry storage, deployment, and runtime use. Model artifacts should have identifiable versions and integrity measurements, while production deployment should require explicit approval. This creates a chain of trust that can be independently verified before a model is allowed to influence physical behavior.

Training-data security forms an important foundation of the framework. Data poisoning, manipulated annotations, hidden backdoors, compromised demonstrations, and unauthorized dataset modifications can introduce vulnerabilities that become embedded in learned behavior. Training datasets should therefore have controlled access, provenance, integrity verification, validation, version management, and independent evaluation. When a compromised dataset is discovered, its relationship to trained models and deployed robots should be traceable.

The framework should also protect AI models against extraction, reverse engineering, adversarial manipulation, and unauthorized modification. Model confidentiality may be important when proprietary intelligence is deployed on edge robots, while model integrity is essential when the model controls safety-relevant behavior. Secure storage, access control, cryptographic protection, signed artifacts, controlled deployment, and runtime verification should be combined rather than relying on a single protection mechanism.

Adversarial attacks against robot perception require a dedicated security boundary because perception is often the first stage through which the physical environment enters the AI decision process. Adversarial patches, manipulated objects, sensor interference, environmental deception, and multimodal inconsistencies can cause a robot to construct an incorrect representation of its surroundings. The framework should therefore combine robust perception, sensor consistency checks, anomaly detection, independent sensing, and downstream safety constraints.

Language-enabled robot agents introduce another security boundary between natural-language information and physical action. Prompt injection may originate from users, documents, web content, visual text, external services, or environmental objects. The framework should distinguish trusted instructions from untrusted information and should prevent retrieved or perceived content from silently acquiring operational authority. High-risk tool calls should require independent authorization and deterministic policy validation before execution.

AI decision manipulation represents a further architectural concern because an attacker may influence not only perception but also priorities, planning, policy selection, or action recommendations. A model output should therefore be treated as a recommendation rather than unrestricted authority. The framework should separate reasoning, policy enforcement, authorization, and physical execution so that a compromised decision process cannot directly control high-consequence actuators.

Certified robustness can provide additional assurance for safety-critical AI components. Where appropriate, the framework should define formal or mathematically defensible properties under a specified threat model and perturbation boundary. Certification should remain tied to the exact model, input assumptions, verification method, and operational scope. It should complement rather than replace physical testing, adversarial evaluation, runtime monitoring, and independent safety controls.

An AI safety monitor should provide an independent enforcement boundary between AI decisions and physical execution. The monitor can evaluate velocity, force, position, workspace, collision distance, geofencing, actuator state, and other operational constraints without relying entirely on the AI model being monitored. When a proposed action violates a defined constraint, the monitor should be capable of rejecting, restricting, modifying, or safely terminating that action.

The safety boundary should also consider temporal and contextual behavior. A sequence of individually acceptable actions may become unsafe when considered together, particularly during navigation, manipulation, locomotion, or flight. Runtime monitoring should therefore evaluate trajectories, behavioral trends, sensor consistency, uncertainty, and deviations from the authorized mission. Where confidence cannot be established, the system should be able to transition into degraded or safe operation.

Model and data security should be integrated with a protected AI model registry. The registry should maintain approved artifacts, versions, provenance, integrity measurements, validation evidence, deployment status, and revocation information. Digital signatures should establish authenticity and integrity, while authorization controls should determine whether a particular model is permitted to run on a specific robot or platform. The registry should prevent unauthorized promotion, rollback, replacement, or distribution of model artifacts.

The framework should establish a secure deployment lifecycle for AI models and related configurations. Development, testing, validation, staging, and production environments should have distinct trust levels and access controls. Automated deployment pipelines should preserve security gates rather than bypassing them for operational convenience. Before activation, a robot should verify model identity, signature, integrity, compatibility, authorization, and applicable security status.

Runtime security must remain effective after deployment. A model that was secure during validation may encounter distribution shifts, sensor failures, environmental changes, novel attacks, or conditions outside its certification boundary. Runtime controls should therefore monitor model behavior, sensor consistency, operational state, and security events. Detection of significant anomalies should trigger appropriate responses such as additional verification, capability reduction, human confirmation, isolation, or transition to a predefined safe state.

The framework should integrate cybersecurity and functional safety rather than treating them as separate disciplines. Cybersecurity controls attempt to prevent unauthorized access and manipulation, while safety controls limit the consequences when prevention fails. Independent emergency mechanisms, actuator restrictions, physical boundaries, and deterministic safety functions should remain effective even when higher-level AI, network, or orchestration components are compromised.

Fleet-level architecture requires additional controls because a single compromised service, model, policy, or configuration can affect many robots. Fleet management should use strong identity, authenticated commands, signed configuration and model artifacts, secure communication, deployment governance, centralized monitoring, and local safety enforcement. Each robot should retain sufficient local security authority to reject unsafe or unauthorized commands even if the central fleet infrastructure is unavailable or compromised.

The framework should also establish comprehensive security monitoring and auditability. Important events should include model creation, dataset changes, validation results, signing operations, deployment decisions, policy changes, AI interventions, safety violations, authentication events, and fleet commands. Logs should preserve sufficient provenance to reconstruct significant security decisions and determine whether an incident originated from data, models, interfaces, infrastructure, human actions, or external manipulation.

Incident response must be designed specifically for AI-enabled physical systems. When compromise is suspected, the organization should be able to isolate affected robots, quarantine models or datasets, preserve forensic evidence, revoke credentials or model artifacts, deploy verified replacements, and restore fleet operations through a controlled process. Recovery mechanisms should not depend exclusively on the potentially compromised AI decision layer and should provide predictable fallback behavior.

Security assurance should continue throughout the system lifecycle. Threat models, model architectures, datasets, deployment environments, and operational assumptions change over time, requiring periodic reassessment. Security regression testing, adversarial evaluation, penetration testing, model verification, safety validation, and incident exercises should be repeated when significant changes occur. Evidence should remain traceable to the exact system, model, configuration, and operational version that was evaluated.

The framework should ultimately establish defense in depth across the entire Physical AI system. No individual control should be expected to prevent every attack or guarantee safe behavior under every condition. Data provenance, secure model development, adversarial robustness, prompt-injection defense, decision validation, safety monitoring, model signing, runtime controls, fleet security, and incident recovery should operate as mutually reinforcing layers.

The final security principle is that intelligence should not automatically imply unrestricted physical authority. AI models can provide perception, reasoning, prediction, planning, and recommendations, but physical execution should remain subject to independent authorization and safety constraints. This separation allows Physical AI systems to benefit from increasingly capable intelligence while maintaining controlled boundaries between digital reasoning and real-world physical consequences.

Within the Physical AI Security structure, Physical AI Security Framework Design follows AI Model Registry Security and Signing as the concluding element of Chapter 10. Volume_24_Robot_Cybersecurity Its role is to integrate the preceding protections into a coherent architecture covering AI-specific threats, model and data security, adversarial resilience, decision integrity, safety monitoring, trusted deployment, and operational governance. The framework should provide continuous protection from data acquisition and model creation through deployment, physical execution, fleet operation, incident recovery, and eventual system retirement.

피지컬 AI 보안 프레임워크(Physical AI Security Framework)는 사이버보안(Cybersecurity), AI 보안(AI Security), 기능 안전(Functional Safety), 물리적 운영 제어(Physical Operational Control)를 하나의 수명주기 아키텍처(Lifecycle Architecture)로 통합해야 한다. 목적은 단순히 네트워크나 AI 모델을 개별적으로 보호하는 것이 아니라 디지털 지능의 침해가 통제되지 않은 물리적 결과로 이어지는 것을 방지하는 것이다. 따라서 프레임워크는 데이터 수집과 모델 개발부터 추론(Inference), 의사결정, 작동(Actuation), 플릿 운영(Fleet Operation), 사고 대응(Incident Response), 시스템 폐기에 이르기까지 보안 경계를 설정해야 한다.

프레임워크는 AI가 물리적 로봇과 연결될 때 발생하는 고유한 보안 위험을 명확하게 이해하는 것에서 시작한다. 피지컬 AI 시스템은 인식(Perception), 학습 모델(Learned Model), 계획(Planning), 제어(Control), 센서(Sensor), 액추에이터(Actuator), 통신 네트워크(Communication Network), 운영 환경을 결합한다. 하나의 계층에서 발생한 취약점은 다른 계층으로 전파되어 궁극적으로 물리적 행동에 영향을 미칠 수 있다. 따라서 보안 아키텍처는 기존의 사이버 위협뿐만 아니라 인식, 추론, 의사결정 또는 학습된 행동을 조작하는 공격까지 고려해야 한다.

신뢰 경계(Trust Boundary)는 전체 피지컬 AI 파이프라인에 걸쳐 명시적으로 정의해야 한다. 센서 데이터, 학습 데이터셋, AI 모델, 외부 정보, 사용자 명령, AI가 생성한 의사결정, 정책 제어(Policy Control), 액추에이터 명령에 동일한 수준의 신뢰를 자동으로 부여해서는 안 된다. 각 경계는 출처, 필요한 인증(Authentication), 무결성 보호(Integrity Protection), 권한 부여 요구사항(Authorization Requirement), 검증 방법(Validation Method), 정보가 더 높은 신뢰 영역으로 이동할 수 있는 조건을 정의해야 한다.

AI 모델은 일반적인 소프트웨어 패키지가 아니라 통제된 보안 자산(Security Asset)으로 취급해야 한다. 모델 개발은 학습 데이터에서부터 학습 구성, 평가, 검증, 서명, 레지스트리 저장, 배포, 런타임 사용에 이르는 출처(Provenance)를 유지해야 한다. 모델 아티팩트(Model Artifact)는 식별 가능한 버전과 무결성 측정값(Integrity Measurement)을 가져야 하며, 운영 환경 배포에는 명시적인 승인이 필요해야 한다. 이를 통해 모델이 물리적 행동에 영향을 미치기 전에 독립적으로 검증할 수 있는 신뢰 체인(Chain of Trust)을 구축할 수 있다.

학습 데이터 보안(Training Data Security)은 프레임워크의 중요한 기반을 형성한다. 데이터 포이즈닝(Data Poisoning), 조작된 주석, 숨겨진 백도어(Hidden Backdoor), 침해된 시연 데이터, 승인되지 않은 데이터셋 변경은 학습된 행동에 내재되는 취약점을 만들 수 있다. 따라서 학습 데이터셋은 통제된 접근, 출처 추적, 무결성 검증, 검증, 버전 관리, 독립적인 평가를 갖추어야 한다. 침해된 데이터셋이 발견되면 해당 데이터셋과 학습된 모델 및 배포된 로봇 사이의 관계를 추적할 수 있어야 한다.

프레임워크는 AI 모델을 탈취(Model Theft), 역공학(Reverse Engineering), 적대적 조작(Adversarial Manipulation), 승인되지 않은 변경으로부터 보호해야 한다. 독점적인 지능이 엣지 로봇에 배포되는 경우 모델의 기밀성(Confidentiality)이 중요할 수 있으며, 모델이 안전 관련 행동을 제어하는 경우 모델 무결성(Model Integrity)은 필수적이다. 보안 저장소, 접근 제어, 암호학적 보호, 서명된 아티팩트, 통제된 배포, 런타임 검증을 단일 보호 메커니즘에 의존하지 않고 결합해야 한다.

로봇 인식에 대한 적대적 공격(Adversarial Attack)은 인식이 물리적 환경이 AI 의사결정 과정으로 유입되는 첫 번째 단계인 경우가 많기 때문에 전용 보안 경계가 필요하다. 적대적 패치(Adversarial Patch), 조작된 객체, 센서 간섭, 환경적 기만(Environmental Deception), 멀티모달 불일치(Multimodal Inconsistency)는 로봇이 주변 환경에 대해 잘못된 표현을 구성하도록 만들 수 있다. 따라서 프레임워크는 견고한 인식(Robust Perception), 센서 일관성 검사(Sensor Consistency Check), 이상 탐지(Anomaly Detection), 독립적인 센싱, 하위 단계의 안전 제약을 결합해야 한다.

언어 기반 로봇 에이전트(Language-enabled Robot Agent)는 자연어 정보와 물리적 행동 사이에 또 다른 보안 경계를 만든다. 프롬프트 인젝션(Prompt Injection)은 사용자, 문서, 웹 콘텐츠, 시각적 텍스트, 외부 서비스 또는 환경에 존재하는 객체에서 발생할 수 있다. 프레임워크는 신뢰된 명령과 신뢰할 수 없는 정보를 구분해야 하며, 검색되거나 인식된 콘텐츠가 운영 권한을 조용히 획득하는 것을 방지해야 한다. 고위험 도구 호출(High-risk Tool Call)은 실행 전에 독립적인 권한 부여와 결정론적 정책 검증(Deterministic Policy Validation)을 거쳐야 한다.

AI 의사결정 조작(AI Decision Manipulation)은 공격자가 인식뿐만 아니라 우선순위, 계획, 정책 선택 또는 행동 권고에도 영향을 미칠 수 있기 때문에 또 다른 아키텍처적 고려사항이다. 따라서 모델 출력은 제한 없는 권한이 아니라 권고(Recommendation)로 취급해야 한다. 프레임워크는 추론(Reasoning), 정책 강제(Policy Enforcement), 권한 부여, 물리적 실행을 분리하여 침해된 의사결정 프로세스가 고위험 액추에이터를 직접 제어하지 못하도록 해야 한다.

인증된 견고성(Certified Robustness)은 안전 필수 AI 구성요소에 추가적인 보증을 제공할 수 있다. 적절한 경우 프레임워크는 지정된 위협 모델과 섭동 경계(Perturbation Boundary) 아래에서 형식적 또는 수학적으로 방어 가능한 속성을 정의해야 한다. 인증은 정확한 모델, 입력 가정, 검증 방법 및 운영 범위와 연결되어 있어야 한다. 또한 인증은 물리적 테스트, 적대적 평가, 런타임 모니터링(Runtime Monitoring), 독립적인 안전 제어를 대체하지 않고 보완해야 한다.

AI 안전 모니터(AI Safety Monitor)는 AI 의사결정과 물리적 실행 사이에 독립적인 강제 경계(Independent Enforcement Boundary)를 제공해야 한다. 모니터는 모니터링 대상 AI 모델에 전적으로 의존하지 않고 속도, 힘, 위치, 작업공간, 충돌 거리, 지오펜싱(Geofencing), 액추에이터 상태 및 기타 운영 제약을 평가할 수 있다. 제안된 행동이 정의된 제약을 위반하면 모니터는 해당 행동을 거부하거나, 제한하거나, 수정하거나, 안전하게 종료할 수 있어야 한다.

안전 경계는 시간적 및 컨텍스트적 행동도 고려해야 한다. 개별적으로는 허용 가능한 행동의 연속이 전체적으로는 안전하지 않은 상황을 만들 수 있으며, 이는 특히 내비게이션, 조작, 보행 또는 비행에서 중요하다. 런타임 모니터링은 따라서 궤적, 행동 추세, 센서 일관성, 불확실성 및 승인된 임무에서 벗어난 정도를 평가해야 한다. 신뢰도를 확립할 수 없는 경우 시스템은 성능 저하 운용(Degraded Operation) 또는 안전 운용(Safe Operation)으로 전환할 수 있어야 한다.

모델 및 데이터 보안은 보호된 AI 모델 레지스트리(AI Model Registry)와 통합되어야 한다. 레지스트리는 승인된 아티팩트, 버전, 출처, 무결성 측정값, 검증 증거, 배포 상태 및 폐기 정보(Revocation Information)를 유지해야 한다. 디지털 서명(Digital Signature)은 진위성과 무결성을 확립해야 하며, 권한 제어는 특정 모델이 특정 로봇 또는 플랫폼에서 실행될 수 있는지를 결정해야 한다. 레지스트리는 모델 아티팩트의 승인되지 않은 승격, 롤백, 교체 또는 배포를 방지해야 한다.

프레임워크는 AI 모델과 관련 구성에 대한 안전한 배포 수명주기(Secure Deployment Lifecycle)를 수립해야 한다. 개발, 테스트, 검증, 스테이징, 운영 환경은 서로 다른 신뢰 수준과 접근 제어를 가져야 한다. 자동화된 배포 파이프라인은 운영상의 편의를 위해 보안 게이트(Security Gate)를 우회해서는 안 된다. 활성화 전에 로봇은 모델 신원, 서명, 무결성, 호환성, 권한 부여 및 적용 가능한 보안 상태를 검증해야 한다.

런타임 보안(Runtime Security)은 배포 이후에도 계속 효과적으로 작동해야 한다. 검증 과정에서 안전했던 모델이라도 분포 변화, 센서 고장, 환경 변화, 새로운 공격 또는 원래의 인증 범위를 벗어난 조건을 경험할 수 있다. 따라서 런타임 제어는 모델 행동, 센서 일관성, 운영 상태 및 보안 이벤트를 모니터링해야 한다. 중요한 이상이 탐지되면 추가 검증, 기능 축소, 인간 확인(Human Confirmation), 격리(Isolation) 또는 사전에 정의된 안전 상태로의 전환과 같은 적절한 대응을 시작해야 한다.

프레임워크는 사이버보안과 기능 안전을 별개의 분야로 취급하지 않고 통합해야 한다. 사이버보안 제어는 승인되지 않은 접근과 조작을 방지하는 반면, 안전 제어는 예방이 실패했을 때 발생할 수 있는 결과를 제한한다. 독립적인 비상 메커니즘, 액추에이터 제한, 물리적 경계 및 결정론적 안전 기능은 상위 수준의 AI, 네트워크 또는 오케스트레이션 구성요소가 침해된 경우에도 계속 작동해야 한다.

플릿 수준 아키텍처(Fleet-level Architecture)는 하나의 침해된 서비스, 모델, 정책 또는 구성이 여러 로봇에 영향을 줄 수 있기 때문에 추가적인 제어가 필요하다. 플릿 관리는 강력한 신원, 인증된 명령, 서명된 구성 및 모델 아티팩트, 보안 통신, 배포 거버넌스(Deployment Governance), 중앙 집중식 모니터링, 로컬 안전 강제를 사용해야 한다. 각 로봇은 중앙 플릿 인프라를 사용할 수 없거나 해당 인프라가 침해된 경우에도 안전하지 않거나 승인되지 않은 명령을 거부할 수 있는 충분한 로컬 보안 권한을 유지해야 한다.

프레임워크는 종합적인 보안 모니터링과 감사 가능성(Auditability)도 확립해야 한다. 중요한 이벤트에는 모델 생성, 데이터셋 변경, 검증 결과, 서명 작업, 배포 결정, 정책 변경, AI 개입, 안전 위반, 인증 이벤트, 플릿 명령 등이 포함되어야 한다. 로그는 중요한 보안 의사결정을 재구성하고 사고가 데이터, 모델, 인터페이스, 인프라, 인간의 행동 또는 외부 조작에서 시작되었는지를 판단할 수 있도록 충분한 출처 추적 정보를 보존해야 한다.

사고 대응(Incident Response)은 AI 기반 물리적 시스템을 위해 특별히 설계해야 한다. 침해가 의심되면 조직은 영향을 받은 로봇을 격리하고, 모델이나 데이터셋을 격리하며, 포렌식 증거(Forensic Evidence)를 보존하고, 자격 증명 또는 모델 아티팩트를 폐기하며, 검증된 대체 모델을 배포하고, 통제된 절차를 통해 플릿 운영을 복구할 수 있어야 한다. 복구 메커니즘은 잠재적으로 침해된 AI 의사결정 계층에 전적으로 의존해서는 안 되며 예측 가능한 폴백 행동(Fallback Behavior)을 제공해야 한다.

보안 보증(Security Assurance)은 시스템 수명주기 전체에서 지속되어야 한다. 위협 모델, 모델 아키텍처, 데이터셋, 배포 환경 및 운영 가정은 시간이 지나면서 변경되므로 주기적인 재평가가 필요하다. 중대한 변경이 발생하면 보안 회귀 테스트(Security Regression Testing), 적대적 평가, 침투 테스트(Penetration Testing), 모델 검증, 안전 검증 및 사고 대응 훈련을 반복해야 한다. 증거는 평가된 정확한 시스템, 모델, 구성 및 운영 버전과 추적 가능하게 연결되어 있어야 한다.

프레임워크는 궁극적으로 전체 피지컬 AI 시스템에 걸쳐 심층 방어(Defense in Depth)를 구축해야 한다. 어떠한 단일 제어도 모든 공격을 방지하거나 모든 조건에서 안전한 행동을 보장할 수 있다고 가정해서는 안 된다. 데이터 출처 추적, 안전한 모델 개발, 적대적 견고성, 프롬프트 인젝션 방어, 의사결정 검증, 안전 모니터링, 모델 서명, 런타임 제어, 플릿 보안 및 사고 복구는 서로를 강화하는 계층으로 작동해야 한다.

최종적인 보안 원칙은 지능이 자동으로 제한 없는 물리적 권한을 의미해서는 안 된다는 것이다. AI 모델은 인식, 추론, 예측, 계획 및 권고를 제공할 수 있지만 물리적 실행은 독립적인 권한 부여와 안전 제약의 적용을 받아야 한다. 이러한 분리를 통해 피지컬 AI 시스템은 더욱 강력해지는 지능의 이점을 활용하면서도 디지털 추론과 실제 세계의 물리적 결과 사이에 통제된 경계를 유지할 수 있다.

피지컬 AI 보안(Physical AI Security) 구조에서 피지컬 AI 보안 프레임워크 설계(Physical AI Security Framework Design)는 AI 모델 레지스트리 보안 및 서명(AI Model Registry Security and Signing)에 이어 Chapter 10의 마지막 구성요소로 배치된다. 그 역할은 앞에서 다룬 보호 기능을 하나의 일관된 아키텍처로 통합하여 AI 특화 위협, 모델 및 데이터 보안, 적대적 복원력(Adversarial Resilience), 의사결정 무결성, 안전 모니터링, 신뢰된 배포, 운영 거버넌스를 포괄하는 것이다. 프레임워크는 데이터 수집과 모델 생성부터 배포, 물리적 실행, 플릿 운영, 사고 복구, 최종적인 시스템 폐기에 이르기까지 지속적인 보호를 제공해야 한다.
