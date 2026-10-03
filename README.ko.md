> **원본 권위 고지:** 본 기술 명세의 최상위 법적·공학적 권위는 한글 원본(`README.ko.md`)에 있습니다. `README.md`는 보조 영문 참고본입니다. 불일치 시 한글 원본이 우선합니다.

# On-Device-Edge-Survival-Paper — 엣지·온디바이스 단말의 자율 연산 필연성 논거, 인간-AI 시공간 비대칭성 인지 창, 자동차 모듈러 플랫폼 세그먼트 파생 및 물리적 생존 아키텍처 (v2.11 Baseline)

> 본 문서는 스마트폰, 개인 컨슈머 단말, 공공기관 행정·안전 인프라, 자율주행 이동체, 무인 로봇, 스마트팩토리 제어기, 특정보안구역 단말, 재난 인프라, 도메인 특화 커스텀 AI 단말 등 개인·공공·기업을 아우르는 범용 엣지 구동체가 중앙집중형 클라우드 연산의 물리적·경제적 한계, 기존 원자력·화력·수력 및 차세대 발전 인프라 과잉 건설에 따른 전력망 부하와 자연환경 섭란, 유무선·위성·양자·메쉬 등 임의의 네트워크 방식(Network Protocol & Transport Layer Agnostic)이 가지는 물리적 전송 지연 한계, 에어갭(Air-Gapped) 망분리 환경, 물리적 반도체 소자의 열역학적 한계 및 AI 과부하 환각 리스크를 완화하고 자체적인 실시간 연산을 수행할 수밖에 없는 구조적 당위성을 다룹니다.  
> 본 백서는 특정 기업, 공공기관, 개인 브랜드 등 특정 운용 주체나 특정 통신 프로토콜/네트워크 방식에 종속되지 않는 범용 생존 아키텍처를 기반으로 작성되었으며, 완성차 그룹의 공통 모듈러 플랫폼 공유 및 세그먼트 파생 전략 구조를 적용하여 선행기술 원용 범위를 정의합니다. 본 백서의 문서·명세·설계도 표현물에는 **CC BY 4.0**을 적용하며, 공개되는 코드 및 구현물 소스코드에는 **Apache-2.0** 라이선스를 적용합니다. 본 백서는 특허 라이선스 부여가 아닌 방어적 공표(Defensive Publication)를 통한 선행기술(Prior Art) 확립을 근본 목적으로 합니다. (구 DPL v1.0 표기는 2026-09-27자로 정정 및 폐기됨)  
> **구상·정리·작성:** deundeuni

---

## 0. 아키텍처 제안 및 핵심 주장 요약 (Architecture Proposal & Core Claims Summary)

1. **설계 배경 및 구성 특징 (Architectural Background):**  
   본 아이디어 논문 및 아키텍처 규격은 중앙 서버 의존성에 따른 통신 지연, 특정 통신 규격(5G/6G 등)에 국한되지 않고 유무선·위성·광·양자·메쉬 등 현존하거나 향후 개발될 모든 네트워크 방식(Universal Transport Protocol Layer)의 물리적 광속 propagation 지연 한계, 데이터센터 전력 폭주 및 대용량 발전 인프라 과잉 건설로 야기되는 자연환경 훼손, 특정보안구역 및 공공망의 물리적 네트워크 해제(망분리), 급박한 연산 시 칩셋 과열 및 AI 환각(Hallucination) 발생, 인간의 1~2초 인지 시간과 AI 연산 주기 사이의 시공간 비대칭성을 활용한 자원 재할당, 물리적 반도체 실체의 열역학적 불변성, 자동차 모듈러 플랫폼 공유 메커니즘을 통한 세그먼트 파생 통제, 개인·공공기관·기업 전반의 다각적 커스텀 AI 단말 탑재 요구를 수용하기 위해 작성자의 문제 의식에서 출발하였다. 온디바이스 연산 필연성 논거 제시, TL Bridge 기반 모듈 격리, 질문 복잡도 연동 가변 연산 지연 제어, 인간-AI 시공간 비대칭성 기반 사유 유휴 창 동적 제어, 완성차 플랫폼 원용 세그먼트 구조화, 네트워크 방식 무관성, 개인·공공·기업 범용 주체 확장성, 다층 제어 토폴로지 및 0.1ms/1ms 국소 선조치 파라미터를 통합·정립한 아키텍처의 구성 및 정리 권한은 작성자 자연인에게 귀속된다.

2. **소프트웨어 유틸리티 및 AI 도구 활용에 관한 명시 (AI Tool Usage Notice):**  
   본 백서의 작성·정리 과정에서 AI 도구를 활용하였으며, 최종 내용은 작성자가 검토하였습니다. 구상 의도 및 최종 저작권은 작성자에게 있습니다.

3. **핵심 아키텍처 주장 및 선행기술 포크 포인트 10선 (Summary of Top 10 Core Architectural Claims):**  
   - 개시 항목 1: 온디바이스 자율 연산 필연성 논거 — 광속 수송 한계, 망분리(Air-Gap) 보안, 대용량 발전 인프라 과잉 건설 및 데이터센터 전력망 부하 완화를 위한 단말 국소 자율 추론 구성을 포함함.  
   - 개시 항목 2: 인간-AI 시공간 비대칭성 (Cognitive Read-Time Window) — 인간의 1~2초 인지·독해 유휴 시간을 GHz NPU의 연산 억제(Dormant), 열 완화(Thermal Relaxation) 및 환각 검증 예산으로 재할당하되, 지연 확대가 실제 검증 정확도 향상으로 이어지는 조건하에서만 유효 구동으로 인정하는 제어를 포함함.  
   - 개시 항목 3: 완성차 모듈러 플랫폼 원용 세그먼트 파생 — 공통 생존 뼈대(TL Bridge, 3-포인트 텔레메트리)를 공유하되 보급형(Monolithic)/산업용(Chiplet), 기본형(Base)/확장형(Extended Fusion)으로 수평 파생하는 구성을 포함함.  
   - 개시 항목 4: 네트워크 프로토콜 및 수송 레이어 무관성 (Protocol-Agnostic) — 5G/6G/위성/양자/광/메쉬 등 전송 매체 종류에 종속되지 않고 오프라인 단말 내부 결정을 최우선 집행하는 구조를 포함함.  
   - 개시 항목 5: 3-포인트 텔레메트리 기반 0.1ms/1ms 국소 자가치유 — 연산·패브릭 지연·온도를 동시 감시하여 단말 내부 결함 포착 시 0.1ms 이내 국소 선조치 및 상위 에스컬레이션을 수행하는 구성을 포함함.  
   - 개시 항목 6: 1ms MIPI 스위칭 및 트라이스테이트(High-Z) 물리 격리 — 결함 포착 시 하드웨어 클럭 사이클(수 ns~수십 ns 스케일) 및 1ms급 스위칭으로 버스 신호와 디스플레이 투사 레이어를 고임피던스 전환하여 시야 가림 및 전이 장애를 완화하는 구성을 포함함.  
   - 개시 항목 7: 3대 자원 동시 보전 및 검증 정확도 연동 가변 제어 — 질문 복잡도에 연동된 가변 연산 지연 확장을 통해 칩셋 피크 발열, 배터리 피크 전류 및 AI 환각을 완화하되, 지연 증가가 검증 정확도 향상을 수반하지 않을 경우 연산 실패로 규정하고 조기 절단(Early Exit)을 집행하는 스케줄링을 포함함.  
   - 개시 항목 8: 란다우어 법칙 기반 물리적 실체 불변성 — 실리콘, 광 포토닉스, 양자, 바이오 소자 등 미래 연산 매체의 물리적 열역학 제약에 하드웨어 거버넌스를 포괄 적용하는 구성을 포함함.  
   - 개시 항목 9: 수 마이크로초(μs) 물리 안티탬퍼 — 디캡슐레이션 물리 공격 감지 시 수 μs 이내에 internal eFuse 과전압 인가 및 Key Zeroization으로 내부 기밀을 파괴하는 하드웨어 보호를 포함함.  
   - 개시 항목 10: 다학제·다국어 비침습 공존 HMI (Coexistence Overlay) — 대상 시스템 펌웨어 및 제어반을 임의 개조하지 않고 외부 시각 레이어로 정보를 보조하는 비간섭 거버넌스를 포함함.

---

## 0.1 선행 연구 점검 및 개별 전제 근거 (Prior Research Review & Premises)

본 문서는 작성자가 '엣지·온디바이스 단말에서 이런 방식으로 생각해볼 수 있다'는 문제의식과 사고 방향을 바탕으로 구상한 것입니다. 작성자는 이 구상을 최초로 고안했다고 주장하지 않습니다. 구상 이후, 그 사고 방향과 맞닿는 기존 논문·특허·표준을 찾아 근거 자료로 인용했으며, 개별 기법과 개념의 공은 해당 원저자에게 있습니다. 구상과 상충하거나 가까운 연구도 확인된 범위에서 함께 기재했습니다. 본 문서의 기여는 이 요소들을 엣지·온디바이스 맥락에서 조합·구성한 데 있습니다. (조사 범위와 한계는 §2.2 참조)

* **항목 1: 온디바이스 자율 연산 필연성 논거 및 오프라인 엣지 독립 추론 (개시 항목 1 관련)**
  - 지지 근거 — Mahadev Satyanarayanan, "The Emergence of Edge Computing", IEEE Computer, Vol. 50 [호·쪽수·DOI 확인 필요]; Weisong Shi et al., "Edge Computing: Vision and Challenges", IEEE Internet of Things Journal, Vol. 3, No. 5, pp. 637–646, 2016 (DOI: 10.1109/JIOT.2016.2579198). 중앙 클라우드 전파 지연 및 네트워크 불안정성을 보완하기 위한 국소 연산 당위성 전제를 뒷받침하는 연구이다.
  - 상충·근접 연구 — Guégain et al., "The Battery Price of edge AI: A study of the Environmental Impact of LLM Inference on Mobile Devices" (arXiv:2609.11940). 초록 기준 온디바이스 추론이 서버 배치 추론보다 에너지 효율이 낮을 수 있다고 보고.
  - 직접 근거 — 조사한 범위에서 확인하지 못함 (추가 조사 필요).

* **항목 2: 인간-AI 시공간 비대칭성 및 인지 유휴 창 재할당 (개시 항목 2 관련)**
  - 지지 근거 — Robert B. Miller, "Response time in man-computer conversational transactions", Proc. AFIPS Fall Joint Computer Conference, 1968, pp. 267–277 (DOI: 10.1145/1476589.1476628); Jakob Nielsen, "Usability Engineering" [출판사·연도 서지 확인 필요]. 인간-시스템 상호작용에서의 인지 유휴 시간 및 반응 시간 기대치 배경을 제시하는 연구이다.
  - 직접 근거 — 조사한 범위에서 확인하지 못함 (추가 조사 필요).

* **항목 3: 완성차 모듈러 플랫폼 및 세그먼트 파생 메커니즘 (개시 항목 3 관련)**
  - 지지 근거 — Timothy W. Simpson, "Product platform design and customization: Status and promise", AIEDAM [권·쪽수 확인 필요]; Marc H. Meyer & Alvin P. Lehnerd, "The Power of Product Platforms", Free Press, 1997 [Simpson 논문 인용 기준, 서지 확인 필요]. 공통 아키텍처 뼈대로부터 가변 세그먼트를 파생시키는 모듈러 플랫폼 전제를 뒷받침하는 연구이다.
  - 직접 근거 — 조사한 범위에서 확인하지 못함 (추가 조사 필요).

* **항목 4: 네트워크 프로토콜 무관 오프라인 엣지 독립 추론 (개시 항목 4 관련)**
  - 지지 근거 — Mahadev Satyanarayanan, "The Emergence of Edge Computing", IEEE Computer, Vol. 50 [호·쪽수·DOI 확인 필요]; Weisong Shi et al., "Edge Computing: Vision and Challenges", IEEE Internet of Things Journal, Vol. 3, No. 5, pp. 637–646, 2016 (DOI: 10.1109/JIOT.2016.2579198). 네트워크 단절 및 전송 지연을 극복하기 위한 단말 자체 판단 전제를 뒷받침하는 연구이다.
  - 직접 근거 — 조사한 범위에서 확인하지 못함 (추가 조사 필요).

* **항목 5: 3-포인트 텔레메트리 감시 및 국소 자가치유·에스컬레이션 (개시 항목 5 관련)**
  - 지지 근거 — 
    1) 자율 자가치유 및 자가관리 아키텍처: Jeffrey O. Kephart & David M. Chess, "The Vision of Autonomic Computing", IEEE Computer, Vol. 36, No. 1, 2003, pp. 41–50 [서지/DOI 추가 확인 필요]; Steve R. White et al., "An Architectural Approach to Autonomic Computing", ICAC'04, 2004 [서지/DOI 추가 확인 필요].
    2) 차량 기능 안전 고장 허용 시간 간격(FTTI) 개념: 차량 기능 안전 규격(ISO 26262-1)에서 고장 발생 시점부터 안전 메커니즘이 작동하지 않을 때 위험 사건이 발생할 수 있는 시점까지의 시간 간격.
    3) 온칩 네트워크 결함 완화 및 자가치유: Pengju Ren et al., "FASHION: Fault-Aware Self-Healing Intelligent On-chip Network", arXiv:1702.02313, 2017; Ritesh Parikh, "Routing and Topology Reconfiguration for Networks-on-Chip's Runtime Health", Univ. of Michigan 박사논문; Shashikiran Venkatesha & Ranjani Parthasarathi, "A Survey of fault mitigation techniques for multi-core architectures", arXiv:2112.14952, 2021.
    4) 멀티코어 온열 실시간 감시: K. Vaddina et al., "Self-Timed Thermal Sensing and Monitoring of Multicore Systems", DDECS 2009, pp. 246–251 (DOI: 10.1109/DDECS.2009.5012139).
  - 직접 근거 — 컴퓨트 연산·패브릭 지연·온도의 3-포인트 동시 감시, 국소 선조치 실행 후 상위 관제로의 에스컬레이션을 결합한 통제 구조에 대해 조사한 범위에서 확인하지 못함. (※ 본 항목의 0.1ms 수치는 국소 제어 반응성 확보를 위한 백서의 하드웨어 설계 목표값임)

* **항목 6: MIPI 스위칭 및 트라이스테이트(High-Z) 물리 격리 (개시 항목 6 관련)**
  - 지지 근거 — MIPI Alliance Specification for Display Serial Interface (DSI) / D-PHY [버전·원문 확인 필요]. 디스플레이 및 패브릭 물리 인터페이스 신호 규격 전제를 뒷받침하는 자료이다.
  - 상충·근접 연구 — 선행 특허 문헌 소목록 참조.
  - 직접 근거 — 결함 포착 시 하드웨어 트라이스테이트(High-Z) 물리 전환 및 1프레임 내 투명화 구성에 대해 조사한 범위에서 확인하지 못함 (추가 조사 필요).

* **항목 7: 질문 복잡도 연동 가변 연산 및 조기 종료 스케줄링 (개시 항목 7 관련)**
  - 지지 근거 — Alex Graves, "Adaptive Computation Time for Recurrent Neural Networks" (2016, arXiv:1603.08983 / DOI: 10.48550/arXiv.1603.08983); Surat Teerapittayanon et al., "BranchyNet: Fast inference via early exiting from deep neural networks" (2016 23rd ICPR, pp. 2464–2469, DOI: 10.1109/ICPR.2016.7900006); Kaya et al., "Shallow-Deep Networks: Understanding and Mitigating Network Overthinking" (2019, ICML, PMLR 97, pp. 3301–3310, arXiv:1810.07052); Snell et al., "Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters" (2024, arXiv:2408.03314); Chen et al., "Do NOT Think That Much for 2+3=? On the Overthinking of o1-Like LLMs" (2024, arXiv:2412.21187); Dhuliawala et al., "Chain-of-Verification" (arXiv:2309.11495, ACL Findings 2024 pp. 3563–3578, DOI: 10.18653/v1/2024.findings-acl.212); "MELTing point: Mobile Evaluation of Language Transformers" (2024, arXiv:2403.12844).
  - 상충·근접 연구 — EnerInfer: Energy-Aware On-Device LLM Inference (arXiv:2606.23001, 초록 기준 에너지·처리량·발열을 함께 관리하는 온디바이스 LLM 추론 프레임워크); Kaya et al. 2019, Chen et al. 2024 (이득이 없는 추가 연산의 중단·절감 관련 선행 연구).
  - 직접 근거 — 조사한 범위에서 확인하지 못함 (정확도 연동 중단 조건과 열·배터리·환각 검증 예산을 결합한 구성).

* **항목 8: 란다우어 법칙 기반 물리적 실체 불변성 및 열 제어 (개시 항목 8 관련)**
  - 지지 근거 — Rolf Landauer, "Irreversibility and Heat Generation in the Computing Process", IBM Journal of Research and Development, Vol. 5, No. 3, pp. 183–191, 1961 (DOI: 10.1147/rd.53.0183, 2차 인용 기준 [확인 필요]); Brooks & Martonosi, HPCA 2001, pp. 171–182 [DOI 확인 필요]; Kevin Skadron et al., "Temperature-aware microarchitecture", ACM SIGARCH Computer Architecture News 31(2), 2003, pp. 2–13 (DOI: 10.1145/871656.859620). 비트 삭제의 열역학적 한계 및 마이크로아키텍처 스케일 동적 열 관리(DTM) 전제를 뒷받침하는 연구이다.
  - 직접 근거 — 란다우어·DTM 연구는 열역학·열관리 전제를 뒷받침하나, 미래 연산 매체 전반에 하드웨어 거버넌스를 적용하는 구성은 조사한 범위에서 확인하지 못함.

* **항목 9: 물리 안티탬퍼 및 디캡 감지 파괴 메커니즘 (개시 항목 9 관련)**
  - 지지 근거 — Ross Anderson & Markus Kuhn, "Tamper Resistance — a Cautionary Note", 2nd USENIX Workshop on Electronic Commerce, 1996 [저자 표기 확인 필요]; Sergei Skorobogatov, "Semi-invasive attacks: A new approach to hardware security analysis", UCAM-CL-TR-630 [연도 확인 필요]; NIST FIPS 140-3, "Security Requirements for Cryptographic Modules" [원문 확인 필요]. 물리적 하드웨어 침습 공격 및 안티탬퍼 제어 전제를 뒷받침하는 연구 및 규격이다.
  - 상충·근접 연구 — 선행 특허 문헌 소목록 참조.
  - 직접 근거 — 디캡슐레이션 감지 시 수 μs 이내 internal eFuse 과전압 키 파기(Zeroization) 구현에 대해 조사한 범위에서 확인하지 못함 (추가 조사 필요).

* **항목 10: 비침습 시각 오버레이 공존 HMI (개시 항목 10 관련)**
  - 지지 근거 — Dhruv Jain et al., "Exploring Augmented Reality Approaches to Real-Time Captioning: A Preliminary Autoethnographic Study" [학회·저자·서지 확인 필요]; Samaradivakara et al., arXiv:2501.02233. 증강현실 기반 시각 정보 보조 및 공간 오버레이 인터페이스 전제를 뒷받침하는 연구이다.
  - 상충·근접 연구 — 선행 특허 문헌 소목록 참조.
  - 직접 근거 — 대상 시스템 제어기 펌웨어를 임의 개조하지 않는 외부 시각 레이어 비간섭 거버넌스 구현에 대해 조사한 범위에서 확인하지 못함 (추가 조사 필요).

### 선행 특허 문헌 소목록 (Prior Patent References)
* US 10,846,899 — "Methods and systems for augmented reality safe visualization during performance of tasks" [변리사 검토 대상]
* US 10,535,202 — "Virtual reality and augmented reality for industrial automation" [변리사 검토 대상]  
*(본 소목록은 관련 선행 특허의 서지만을 열거한 것이며, 청구범위나 법적 의미 해석은 포함하지 않음)*

개별 기법의 공은 인용된 원 저자들에게 있으며, 본 문서는 이를 엣지 단말 맥락에서 조합·구성한 것이다.

## 0.2 문서 작성 및 공개 목적 (Purpose of Publication)
본 문서는 엣지·온디바이스 연산과 관련된 아이디어와 근거 자료를 누구나 자유롭게 참고·활용·비판할 수 있도록 공익적 목적에서 공개합니다. 이를 위해 문서·명세·설계도는 CC BY 4.0, 코드·구현물은 Apache-2.0으로 공개합니다.

---

## 1. 중앙집중형 클라우드 AI 연산의 물리적·환경적·제도적 한계

* **전력 CapEx 절벽과 발전 인프라 과잉 증설 및 자연환경 섭란 완화** — 무한한 클라우드 확장은 초거대 데이터센터 건설 비용, 냉각 용수 고갈뿐만 아니라, 막대한 전력 수요를 충당하기 위한 원자력·화력·수력 및 차세대 발전 인프라(SMR 포함)의 과잉 건설을 유발할 가능성이 존재합니다. 이는 토지 훼손, 냉각 온수 배출로 인한 수생태계 변화, 잠재적 환경 오염 등 물리적 생태계 부하를 야기하므로 온디바이스 연산을 통한 전력 분산을 지향합니다. 다만 온디바이스 추론이 서버 배치 추론보다 에너지 효율이 낮을 수 있다는 연구도 있다 (Guégain et al., arXiv:2609.11940, 초록 기준).
* **임의의 네트워크 방식(유무선·위성·우주망·광·양자·메쉬)의 전송 지연 및 물리적 수송 한계** — 셀룰러 이동통신(5G/6G/7G 등), 저궤도(LEO)·정지궤도(GEO) 위성 통신, 광 백홀, 양자 전송망, Wi-Fi/Bluetooth, P2P 메쉬 네트워크 등 특정 통신 방식은 일 예시에 불과하며 어떠한 네트워크 전송 방식(Universal Transport Protocol Layer)을 활용하더라도, 광속 전파 상수의 물리적 제약과 라우터 신호 변환 지연으로 인해 밀리초(ms) 이하 급의 실시간 물리 제어 반응성을 보장하기는 어렵습니다. 네트워크 고도화 방식과 상관없이 단말 국소 칩셋의 독립 추론 체계 구축이 요구됩니다.
* **특정보안구역, 공공기관 핵심망 및 에어갭(Air-Gapped) 네트워크 해제 제약** — 반도체 팹, 방산 인프라, 국가 공공기관 행정망, 연구소, 금융 핵심망 등에서는 기밀 및 개인정보 유출 방지와 물리적 보안을 위해 외부 네트워크 연결이 해제되거나 엄격히 제한됩니다. 외부 클라우드 접속이 불가능한 환경에서는 외부 서버 의존형 AI가 무력화되므로, 단말 내부의 독립적 연산 체계 구축이 필수적입니다.
* **시간 압박에 따른 AI 환각 및 칩셋 과열 리스크 완화** — 제한된 클라우드/단말 자원 내에서 복잡한 질문을 초저지연으로 일괄 처리하려 할 경우, NPU 과열에 따른 정밀도 저하와 문맥 조기 절단이 발생하여 잘못된 정보나 환각(Hallucination)을 생성할 위험이 증대됩니다.
* **운용 주체별 커스텀 AI 모델의 파편화 및 중앙 서버 호환성 한계** — 개인 맞춤형 비공개 모델, 공공기관 행정 특화 모델, 기업 전용 도메인 AI(sLLM/VLM)는 보안성, 인권 보호 및 실시간성 문제로 범용 클라우드에 의존하기 어려우며, 각 단말 현장에서 맞춤형 추론을 수행하는 온디바이스 엣지 수용성이 요구됩니다.

---

## 2. 엣지 및 온디바이스 단말의 자체 연산 필연성 논거

스마트폰을 포함한 다양한 전용 단말기가 칩셋(NPU/APU) 레벨에서 자체 연산을 수행해야만 하는 이유는 다음과 같은 물리적 실재, 환경 보전, 완성차 플랫폼 구조 원용, 임의 네트워크 방식의 전송 제약 및 제도적 보안 요구에 근거합니다.

* **인간-AI 시공간 비대칭성 및 사유 유휴 창의 검증 정확도 실증 메커니즘** — 인간 사용자에게 찰나인 1~2초의 인지·독해 시간은 GHz 클럭으로 구동되는 AI NPU에게 수억~수십억 회의 연산이 가능한 상대적으로 거대한 시간 지평입니다. 이 미시적 시차를 연산 억제(Dormant), 열 식히기(Thermal Relaxation) 및 다단계 검증 구간으로 재할당하되, 확장된 사유 시간(Reasoning Window)은 시간 투입 대비 실질적인 검증 정확도 향상이 실증될 때에만 유효한 설계로 간주하며, 지연 증가가 검증 정확도 개선을 수반하지 않는 경우 연산 실패 및 조기 절단(Early Exit) 조건으로 정의하여 환각 완화와 자원 효율을 동시에 지향합니다.
* **자동차 모듈러 플랫폼 공유 및 세그먼트 파생 구조 원용** — 완성차 그룹의 모듈러 플랫폼(E-GMP, MQB 등)이 공통 뼈대 위에 보급형부터 고성능 세그먼트를 파생시키듯, 본 백서의 핵심 안전 뼈대(TL Bridge, 3-포인트 텔레메트리, 0.1ms E-Stop)를 최하위 공통 플랫폼 규격으로 고정하고 하위 세그먼트(Monolithic vs Chiplet, Base vs Extended Fusion)로 수평 확장함으로써 선행기술 방어 범위를 정의합니다. 이는 산업계에서 널리 쓰이는 플랫폼 전략을 원용한 것입니다.
* **네트워크 방식 무관 오프라인 독립성 (Protocol-Agnostic Independence)** — 5G/6G 등 특정 이동통신에 국한되지 않고 위성, 양자, 차세대 유무선 통신망, 메쉬 네트워크 등 어떠한 전송 레이어의 물리적 전파 속도 한계 및 통신 음영 상황에도 영향받지 않으며, 단말 내부에서 밀리초 이하급의 판단과 추론을 완결합니다.
* **개인·공공·기업 범용 주체 확장 및 커스텀 AI 시스템 연동** — 개인(컨슈머), 공공기관(행정·소방·경찰·의무), 기업(산업·제조·금융)이 독자 구축한 맞춤형 AI 모델을 단말 하드웨어 자율 샌드박스 내에 온전히 채용·격리 구동하여, 운용 주체별 특수 수요에 유연하게 대응합니다.
* **복잡도 연동 가변 연산 지연 및 3대 자원(칩셋·배터리·AI) 보전** — 질문 및 해결 과제의 복잡도와 난이도를 선제 감지하여 연산 지연시간(Latency Window)을 동적으로 늘리거나 스케줄링함으로써, 칩셋의 피크 발열을 완화하고, 배터리 피크 전류 유발을 억제하며, AI의 정밀 사유 시간(Reasoning Window)을 확보해 환각 완화를 지향합니다. 단, 무인택시 비상 회피 등 안전 임계 제어 레이어의 경우 Hard Deadline 타임아웃 상한선을 최우선 집행합니다.
* **자연환경 보전 및 전력망 부하 완화 (Green Edge Computing)** — 미시적 연산 및 추론을 전 세계 수십억 대의 개인·공공·기업 단말 NPU로 분산 처리하여 중앙 데이터센터의 전력 소모와 발전 시설 증설 압력을 줄일 가능성이 있으나, 효과는 실측으로 검증되지 않았다.
* **실시간 물리 제어의 초저지연(Sub-millisecond) 요구성** — 무인택시의 회피 기동, 공공 재난 대피 유도, 산업용 모터 부하 제어, 로봇 암의 위치 교정 등은 지연 시간이 시스템 생존과 직결되므로 국소 칩셋에서의 자체 결정이 불가피합니다.
* **데이터 분산 처리를 통한 에너지 효율화 및 기밀·개인정보 유지** — 정제되지 않은 대용량 원시 데이터를 외부로 전송하는 대신, 단말 내부에서 1차 가공·추론함으로써 통신 전력 소모를 완화할 가능성이 있으며 실측으로 검증되지 않았다.
* **에어갭 및 네트워크 해제 환경에서의 오프라인 자율성** — 외부 통신망과의 연결이 물리적으로 해제된 보안구역, 공공 안전 망 또는 가혹 환경에서도 단말 독자적으로 최소 기능(Failsafe) 및 안전 제어를 유지할 수 있는 독립적 격리성을 지향합니다.
* **Base vs Extended Fusion 센서 결합 이원화** — 엣지 단말의 열 마모, 안면 발열 한계, 배터리 지속시간 단축 리스크를 완화하기 위해 표준 내장 센서 기반 경량 구현을 기본형(Base)으로 정의하되, 비접촉 EMF·열화상·스마트 링 등 외부 착탈식 센서가 추가 결합되는 확장 조합(Extended Fusion)의 기술적 원용 범위를 함께 포괄합니다.

---

### 2.1 선행 연구 검토 및 차별성 (Related Work & Differentiation)

본 백서의 개시 항목 2(인간-AI 시공간 비대칭성) 및 개시 항목 7(가변 연산 지연 및 조기 절단)은 가변 추론, 조기 종료(Early Exit), 열/에너지 인지 스케줄링 분야의 기존 선행 연구를 인지하고 다음과 같은 차별적 제어 메커니즘을 정의합니다. (조사 범위와 한계는 §2.2 참조)

* **적응형 연산 단계 할당 연구와의 비교** — Alex Graves의 *Adaptive Computation Time for Recurrent Neural Networks* (2016, arXiv:1603.08983 — https://arxiv.org/abs/1603.08983 / DOI: https://doi.org/10.48550/arXiv.1603.08983) 연구는 입력 과제의 난이도에 따라 신경망의 연산 단계(Computational steps) 수를 적응적으로 동적 할당하는 메커니즘을 다루었습니다.
* **조기 종료 기반 추론 지연 단축 연구와의 비교** — Surat Teerapittayanon 등의 *BranchyNet: Fast inference via early exiting from deep neural networks* (2016 23rd ICPR, pp. 2464–2469, DOI: 10.1109/ICPR.2016.7900006 — https://doi.org/10.1109/ICPR.2016.7900006) 연구는 심층 신경망 중간 레이어에 조기 종료 가지(Branch)를 추가하여 추론 지연(Latency)과 에너지 사용을 단축하는 방식을 제시하였습니다.
* **열 및 에너지 인지 제어 연구와의 비교** — Kevin Skadron 등의 *Temperature-aware microarchitecture* (ACM SIGARCH Computer Architecture News 31(2), 2003, pp. 2–13, DOI: 10.1145/871656.859620) 및 EnerInfer(arXiv:2606.23001, 초록 기준: 에너지 효율, 처리량, 열 쾌적성을 함께 관리하는 온디바이스 LLM 추론 프레임워크) 등 선행 연구가 존재합니다.
* **본 백서의 추론 제어 특징** — 본 백서는 연산 지연 단축이나 개별 열/에너지 스케줄링만을 목적으로 삼는 데 그치지 않고, (a) 인간 사용자에게 주어지는 1~2초의 인지·독해 유휴 창(Cognitive Read-Time Window)이라는 인간-컴퓨터 시공간 비대칭 구간을 NPU 연산 억제(Dormant), 열 완화 및 환각 검증 예산으로 의도적으로 재할당하며, (b) 열·에너지 통합 관리는 EnerInfer 등 선행 연구가 있으며, 본 백서는 여기에 인지 유휴 창과 환각 검증 예산을 동일 스케줄링 루프의 변수로 포함하는 구성을 기술한다. 이득이 없는 추가 연산의 중단·절감은 Kaya et al. 2019, Chen et al. 2024 등에서 이미 다루어졌으며, 본 백서는 이를 인지 유휴 창·열·배터리 예산과 결합한 구성을 기술한다. (c) 지연 할당 확장이 실질적인 검증 정확도 향상으로 이어지지 않을 경우 연산 실패로 정의하여 조기 절단(Early Exit)을 집행하는 통제 구조를 선행 연구와의 조합의 특징으로 기술한다.

---

### 2.2 선행기술 조사의 범위와 한계 (Scope and Limitations of Prior Art Review)

* **개인 작성자의 조사:** 본 문서의 선행 연구·특허 인용은 개인 작성자가 AI 도구의 도움을 받아 2026-10-03 기준으로 공개 웹 검색을 통해 수행한 것이며, 전문 선행기술 조사 기관이나 변리사의 조사가 아닙니다. 개인이 전 세계 논문·특허·표준·제품 문서를 빠짐없이 확인하는 것은 현실적으로 불가능하며, 본 조사는 전수 조사를 목표로 하지도 않았습니다. AI 도구의 검색·요약에도 오류가 있을 수 있습니다.
* **자료 접근의 한계:** 로그인·유료 장벽이 있는 자료(일부 학회·저널 원문, 표준 문서 등)는 원문 전체를 확인하지 못했고, 초록·서지 레코드·2차 요약에 의존한 항목이 있습니다. 각 인용은 확인한 범위 안에서만 서술했습니다.
* **조사 범위:** 영문 웹 검색과 공개 초록·인용 레코드 중심입니다. 특허 데이터베이스(KIPRIS, Google Patents, Espacenet 등), 국문 및 기타 언어 문헌, 비공개·제품 문서는 체계적으로 조사하지 않았습니다. 언급된 특허 문헌은 서지만 기재했으며 청구범위나 법적 의미는 해석하지 않았습니다.
* **누락 가능성:** 동일하거나 유사한 구성을 다룬 선행 연구·특허·제품이 존재할 수 있습니다. "조사한 범위에서 확인하지 못함"은 해당 구성이 본 백서 작성자가 조사한 범위(공개 웹/영문 레코드 중심) 내에서 발견되지 못했음을 뜻하며, 해당 구성의 절대적 신규성이나 선행기술 부재를 보장하는 것은 아닙니다.
* **오류 가능성:** 서지정보와 요약에 오류가 있을 수 있으며, 확인된 오류는 개정 이력에 반영합니다. 인용된 자료의 저작권은 각 원저작자·권리자에게 있습니다.
* **법적 판단 아님:** 본 조사와 서술은 신규성·진보성·침해 여부에 대한 법적 판단이 아니며 법률 자문이 아닙니다. 법적·특허적 효과의 범위는 전문 변리사의 검토를 권장합니다. (§7 참조)
* **미발견 자료의 취급:** 이후 동일하거나 유사한 내용의 선행 연구·특허·제품이 발견되는 경우, 해당 원저자의 공을 명시하고 내용을 정정하여 부록 A(제개정 이력)에 반영합니다.

---

## 3. 범용 조립형 생존 아키텍처 기반의 엣지 제어 매커니즘

`ARCHITECTURE_STRATEGY.md` 규격에 입각하여 엣지 및 온디바이스 단말은 단일 통합형(Monolithic)의 한계를 극복하고 조립 분리형(Chiplet / Modular Integration) 구조를 채택함으로써 연산 자가치유를 달성합니다.

* **단일 통합형 제약 완화 및 TL Bridge 연동** — 단일 칩셋에 모든 온디바이스 AI 연산이 집중될 경우 발생할 수 있는 열 마모 및 결함 전이를 조립 분리형 구조로 예방하며, TL Bridge 인터페이스를 통해 AQL 명령 번역 및 큐 임계치 도달 시 역방향 백프레셔 신호를 송출하여 메모리 폭주를 선제 완화합니다.
* **사유 유휴 창(Cognitive Read-Time Window) 기반 2단계 동적 자원 제어 및 조기 절단** — 최초 이벤트 발생 시 1ms급 스케일로 NPU 추론을 가동하되, 인간 사용자가 1~2초 동안 정보를 스캔·해독하는 사유 유휴 시간 동안 NPU 연산을 스로틀링(Dormant)하거나 정속 추론으로 전환하여 발열 완화를 도모합니다. 단, 검증 반복 횟수가 증가함에도 검증 정확도가 상향되지 않을 경우 지연을 무한히 연장하지 않고 선제적으로 추론을 중단하는 조기 절단(Early Exit) 메커니즘을 적용합니다.
* **범용 주체 커스텀 AI 동적 샌드박스 및 자원 파티셔닝** — 개인, 공공기관, 기업이 탑재한 다양한 이종 커스텀 AI 에이전트가 단말 내 NPU/APU 슬라이스 자원을 동적으로 분할 점유하도록 파티셔닝 구조를 제공하여, 상호 간섭(Interference) 완화 및 독립 추론을 지향합니다.
* **복잡도 기반 동적 쿨다운 및 검증 정확도 연동 스케줄링** — 고난도 질문 감지 시 칩셋 NPU의 클럭 피크를 자제하고 전력 예산 내에서 의도적 타임라인(Latency Budget)을 확장 할당하되, 지연 할당 대비 검증 정확도 향상을 실시간 스캐닝하여 효율성이 입증된 지연 확장 구간 내에서만 발열 억제 및 안정적 검증 추론을 집행합니다. 단말 DRAM 대역폭 점유 정속화를 위해 양자화 및 분산 캐싱을 병행 적용할 수 있습니다.
* **다층 제어 토폴로지 및 3-포인트 텔레메트리** — 개별 노드 자율 통제, 팀 내부 자체 통제, 중간 관리자 제어, 수평 P2P 피어 통제, 중앙 관리 관제(CCS)가 연계되며, 컴퓨트 연산·패브릭 지연·온도 3-포인트 텔레메트리를 감시하여 단말 내 부분 장애 발생 시 0.1ms 이내에 국소 선조치를 실행하고 상위 관리자로 상신 및 에스컬레이션합니다.
* **다학제·다국어 공존 브릿지(Polyglot Coexistence Bridge) 비침습 오버레이** — 대상 시스템의 PLC/NC 펌웨어, 공공 제어반 회로, 전문 지식 음성 해설 및 원작 미디어를 임의 개조·훼손하지 않고 외부 시각 공간 레이어로만 정보를 보조하는 공존(Coexistence) 및 비간섭(Non-Interference) 거버넌스를 구현합니다.

---

## 4. 물리적 제약 조건 극복, 무중단 자가치유, 안티탬퍼 및 물리적 실체 불변성

* **물리적 실체 불변성 (Universal Physical Substrate Invariance)** — 란다우어의 법칙($k T \ln 2$)에 따라 정보 처리 및 비트(bit) 삭제 시 발생하는 열역학적 에너지 방출, 전력 밀도 제약 및 광속 전파 지연은 물리 우주의 불변 법칙입니다. (원논문 Landauer 1961에서는 $k T$ 스케일의 최소 발열로 서술되었으며, $k T \ln 2$는 후속 문헌에서 공식화된 표기임) 실리콘 반도체, 광 포토닉스, 양자 컴퓨팅, 생체/분자 소자 등 미래 어떠한 매체가 활용되더라도 본 백서의 물리적 하드웨어 제어 및 국소 생존 거버넌스가 포괄 적용됩니다.
* **전력 밀도, 발열 제어 및 자원 점유 억제(T-Reg)** — 텔레메트리를 동적으로 감지하여 클럭을 제어하며, 자가 치유 모듈의 버스 점유율이 임계치(5%~30%)를 초과할 경우 하드웨어적으로 동작을 강제 억제(Rate Limit)하여 부하 전이를 완화합니다.
* **백혈구 비동기 무작위 스캔(Stealth Scan)** — 버스 트래픽을 비동기로 무작위 추출하여 무한 루프나 인가되지 않은 이상 패킷 포착 즉시 격리 버퍼로 억류합니다.
* **트라이스테이트(High-Z) 물리 격리 및 1ms MIPI 스위칭** — 연산 오류나 과부하 발생 시 하드웨어 클럭 사이클(수 ns~수십 ns 스케일) 및 1ms급 스위칭으로 물리 버스 및 투사 레이어를 고임피던스(High-Z) 전환하여 디스플레이 1프레임(16.6ms) 이내에 투명화함으로써 관찰 시야 가림 리스크를 완화합니다.
* **독립 Safety IP 및 안티탬퍼 물리 무력화** — 물리적 디캡슐레이션 및 칩 분석 공격 감지 시 하드웨어 제어 시퀀스 내(수 μs 수준)에 internal eFuse 과전압 인가 및 Key Zeroization을 실행하여 엣지 기밀, 공공 데이터 및 커스텀 AI 모델 웨이트의 영구 물리 파괴를 지향합니다.
* **L0 생체모방 구조적 유격/응력 흡수** — L0(물리 하드웨어 계층 — `Chiplet-APU-Multi-System-Survival-Architecture` 백서 참조)의 반도체 인터포저, TSV 및 물리 커넥터 접점에 생체모방 구조(따개비 접착 단백질 메커니즘 등)를 원용하여 열팽창 응력 및 유격 오차를 물리적으로 흡수합니다.

---

## 5. 산업·공공·개인 분야별 적용 및 수평 전개 레퍼런스

* **개인 및 컨슈머 모바일 단말 (Personal Sector)** — 개인 소유 스마트폰, 태블릿, 컨슈머 AR 글래스(BYOD), 스마트 링 등 웨어러블 단말에서 OS 커널 레벨의 NPU 샌드박스와 연동하여 개인 맞춤형 AI 모델 구동을 통제하고, 인간-AI 시공간 비대칭성 및 질의 난이도에 따른 동적 연산 지연 제어로 칩셋·배터리·AI 신뢰성을 보전하며 데이터센터 전력 소비 전이를 억제·완화할 가능성이 있으며 효과는 실측으로 검증되지 않았다.
* **공공기관, 지자체 및 국가 인프라 (Public Sector)** — 지자체 행정 단말, 소방·경찰 대피 인프라, 공공 의료 기기, 교통 관제 시스템 등 외부 통신망이 제한되거나 위성·공공 메쉬망과 연결된 환경에서 공공 특화 AI를 안전하게 구동하며, 공공 안전 유도를 보조합니다.
* **특정보안구역 및 스마트팩토리 전용 단말기 (Enterprise Sector)** — 외부 네트워크 연결이 물리적으로 해제된 반도체 팹, 방산 라인 내 제어기와 직결되어 기업 도메인 특화 커스텀 AI의 기밀 유출 위험을 완화하며, 에어갭 환경에서도 에러 발생부터 선조치 완료까지의 생애주기를 PII 파기 후 CBOR 익명 로그로 자가 기록하여 기업 인프라(NAS/S3/MES)로 자동 이관·문서화합니다.
* **무인택시, 자율주행 및 커스텀 로보틱스 이동체 (Mobility & Robotics Sector)** — 라이다 및 카메라 데이터의 초저지연 처리, 휴머니오드 로봇(옵티머스급 포함) 기구 제어 및 물리 기구 클러치 제어를 결합하여 외부 서버 접속 불가 시에도 독립적 안전 정지 및 회피를 수행하며, 운용 주체별 커스텀 AI 제어 루프를 격리 연동합니다.
* **재난 피난 유도 인프라 (`LAST-LIGHT`) 및 비침습 공간 HMI (`POLYLINK-HUD`)** — 전원 및 통신망 단절 시 잔여 에너지를 활용해 앵커 노드 간 메시 연산을 구동하며, 개인 AR 글래스 HUD를 통한 비침습 공간 자막 및 공공 가이드 오버레이를 제공합니다.

---

## 6. 구현 수단 및 통신 매체 무관성 상위개념 포괄 정의 (Layer, Topology & Network-Agnostic Scope)

본 규격은 엣지 및 온디바이스 단말의 연산 물리 매체, 전송 통신망, 소프트웨어 계층에 국한되지 않으며, 범용적 구조 목적을 동일하게 달성하는 모든 기술적 수단을 선행기술 범주로 포괄합니다.

* **임의 네트워크 전송 방식 무관성 (Universal Network Protocol & Transport Layer Agnostic)** — 5G, 6G, 7G 등 무선 이동통신 규격은 일 예시에 불과하며, LEO/GEO 저궤도 위성 통신, 우주 백홀, 양자 네트워크, 광 파이버 패브릭, Wi-Fi, Bluetooth, P2P 메쉬망 등 현존하거나 향후 개발될 모든 유무선 네트워크 전송 방식을 포괄합니다. 어떠한 네트워크 전송 방식을 활용하더라도 네트워크 전송 한계를 보완하기 위한 온디바이스 연산 및 생존 자가치유 구성을 적용하면 본 규격의 선행기술 범주로 포괄 정의됩니다.
* **실행 계층 및 물리 매체 무관성** — 마이크로코드, 펌웨어, OS 커널, 하이퍼바이저, AI 가속 에이전트 계층을 포함하며, 광학/포토닉스(Co-Packaged Optics, 광 인터커넥트), 양자(Quantum Sensing, 양자 얽힘), 분자/바이오 소자 및 테라헤르츠 매체를 통한 칩셋 간 통신 및 상태 검증 수단을 포함합니다.

---

## 7. 실리보호 및 법적 적용 범위 이원화 (Practical Protection & License Separation)

* **원안 우선 원칙:** 본 명세서의 법적·기술적 해석은 한국어 원본(`README.ko.md`)을 최우선 기준으로 적용하며, 영문본 및 기타 언어 번역본은 참고용으로만 기능한다.
* **문서 및 소스코드 라이선스 구분 적용:** 본 백서 문서, 명세서, 시각 자료 및 설계도 표현물에는 **CC BY 4.0**이 적용되며, 공개된 소프트웨어 소스코드 및 하드웨어 구현물에는 **Apache-2.0** 라이선스를 적용한다. CC BY 4.0 저작권 라이선스는 특허 실시권을 부여하지 않으며, 본 백서의 기술적 방어 효과는 특허 라이선스 계약이 아닌 방어적 공표(Defensive Publication)에 따른 선행기술화(Prior Art) 및 타임스탬프 공개에 기반한다. (구 DPL v1.0 표기는 2026-09-27자로 폐기 및 정정됨) 본 문서의 CC BY 4.0 및 Apache-2.0은 작성자가 직접 작성·정리한 표현물에만 적용되며, 인용·참조한 논문, 표준, 도표, 상표 등 제3자 자료의 저작권은 각 원저작자·권리자에게 있습니다.
* **범위 포괄성:** 본 문서에 기술된 조립 방식, TL Bridge 연동, 다층 제어 토폴로지, 자동차 모듈러 플랫폼 공유 원용 세그먼트 파생 구조, 질문 복잡도 연동 가변 연산 지연 제어, 인간-AI 시공간 비대칭성 기반 1~2초 인지 유휴 창 자원 재할당 및 조기 절단 조건, 물리적 실체 불변성(란다우어 법칙 연계), 칩셋·배터리·AI 동시 보전 메커니즘, 임의 네트워크 전송 방식 무관성, 개인·공공·기업 범용 주체 확장성, 사유 유휴 창 동적 제어, 전력망 부하 완화 및 자연환경 보전 연계, 1ms MIPI 스위칭 및 트라이스테이트 격리, 수 μs 안티탬퍼 파괴, 비침습 에러 블랙박스 라우팅, Base/Extended Fusion 이원화를 포함한 모든 상위 개념은 선행기술 공표 및 원용 범위로 포괄 적용된다.
* **비의도적 생략 및 예시적 미한정 고지 (Non-Intentional Omission & Non-Exhaustive Disclaimer):** 본 명세서에 인용되거나 열거된 기술 표준, 공지 원리, 법령 및 관련 저장소 목록은 이해를 돕기 위한 예시적 서술이며 전면적·고착적 한정을 의미하지 않는다. 작성자의 주관적 한계나 인지적 착오로 인해 특정 세부 규격, 관련 산업 표준, 후속 개정안 또는 균등 선행기술의 명시가 누락되거나 누적 생략되었을 수 있으나, 이는 의도적인 은폐나 배척이 아니다. 다만, 본 고지는 작성자의 서술적 누락이 비의도적임을 명시하는 고지일 뿐, 제3자의 독자적 선행기술을 본 백서의 권리 범위나 선행기술 범위로 부당하게 흡수·끌어오는 법적 효력을 갖지는 않는다.
* **방어적 공표:** 본 백서는 방어적 선행기술(Prior Art) 공표를 1차 목적으로 한다. 본 백서의 법적·특허적 방어 효과의 구체적 범위는 전문 변리사의 검토와 확인을 권장한다. (선행기술 조사의 범위와 한계는 §2.2 참조)
* **사업화 내용 분리:** 본 백서 원안에는 Pure Open Source 및 선행기술 개시 내용만을 포함하며, 독자적인 수익 모델 및 사업화 세부 실행안은 별도 기술 문서로 분리 관리한다.

---

## 8. 출처 및 기록 (Sources & Records)

* **소마모아 생태계 저장소 및 학술 식별자 (Ecosystem Repositories & DOIs — Title-Kebab-Case Baseline)**
  * 최상위 범용 생존 아키텍처 마스터 허브 (`Smart-System-Multi-Survival-Architecture`) — GitHub: `deundeuni / smart-system-multi-survival-architecture`
  * 상위 범용 생존 아키텍처 & APU 연산 제어기 (`Chiplet-APU-Multi-System-Survival-Architecture`) — GitHub: `deundeuni / Chiplet-APU-Multi-System-Survival-Architecture` | CERN Zenodo DOI: `10.5281/zenodo.22374987` (https://doi.org/10.5281/zenodo.22374987)
  * 생체모방 열역학 회복탄력성 아키텍처 (`Biomimetic-Thermodynamic-Resilience-Architecture`) — GitHub: `deundeuni / Biomimetic-Thermodynamic-Resilience-Architecture`
  * 해조류 고정형 공생 해양 구조물 (`Seaweed-Anchored-Mutualistic-Marine-Structure`) — GitHub: `deundeuni / Seaweed-Anchored-Mutualistic-Marine-Structure`
  * 본 백서 전용 독립 저장소 (`On-Device-Edge-Survival-Paper`) — GitHub: `deundeuni / On-Device-Edge-Survival-Paper` | 메인 백서 파일: `README.md` (영문 보조) / `README.ko.md` (한글 원본)
  * 프레스·절곡기·절단기 근접 안전 백서 저장소 (`Press-Brake-Shear-Edge-Safety-Paper`) — GitHub: `deundeuni / Press-Brake-Shear-Edge-Safety-Paper` | 메인 백서 파일: `README.md` (영문 보조) / `README.ko.md` (한글 원본)
  * 상위 아키텍처 전략 명세 (`ARCHITECTURE_STRATEGY.md`) — GitHub: `soma-moa / chiplet-apu-multi-system-survival-architecture` 저장소 내 수록 | 한글 원본 `ARCHITECTURE_STRATEGY.ko.md` v3.4 (2026-09-27) 병기
  * 다국어 비침습 AR HUD 공간 HMI 게이트웨이 (`POLYLINK-HUD`) — GitHub: `deundeuni / POLYLINK-HUD` | CERN Zenodo DOI: `10.5281/zenodo.22726318` (https://doi.org/10.5281/zenodo.22726318)
  * 재난 피난 유도 & 보조 인프라 (`LAST-LIGHT`) — GitHub: `deundeuni / LAST-LIGHT` | CERN Zenodo DOI: `10.5281/zenodo.22373189` (https://doi.org/10.5281/zenodo.22373189)
  * 선행 광학 인지 & 공간 탐색 인프라 (`FIRST-LIGHT`) — GitHub: `deundeuni / FIRST-LIGHT` | CERN Zenodo DOI: `10.5281/zenodo.22683225` (https://doi.org/10.5281/zenodo.22683225)
  * 단말 착용형 미시 열응력 완화 모듈 (`MAX-LIFE-ICE-BELT`) — GitHub: `deundeuni / MAX-LIFE-ICE-BELT` | CERN Zenodo DOI: `10.5281/zenodo.22373686` (https://doi.org/10.5281/zenodo.22373686)
  * CWP 진입 유도 정렬 (`CWP-Entry`) — GitHub: `deundeuni / CWP-Entry` | CERN Zenodo DOI: `10.5281/zenodo.22683234` (https://doi.org/10.5281/zenodo.22683234)
  * CWP 배터리 교환 도킹 (`CWP-Battery-Swap`) — GitHub: `deundeuni / CWP-Battery-Swap` | CERN Zenodo DOI: `10.5281/zenodo.22373538` (https://doi.org/10.5281/zenodo.22373538)
  * CWP 전자기 클램핑 (`CWP-Clamping-Battery-Swap-System`) — GitHub: `deundeuni / CWP-Clamping-Battery-Swap-System` | CERN Zenodo DOI: `10.5281/zenodo.22373722` (https://doi.org/10.5281/zenodo.22373722)
  * CWP 롤링 셀프얼라인 (`CWP-Rolling-Self-Align-Battery-Swap-System`) — GitHub: `deundeuni / CWP-Rolling-Self-Align-Battery-Swap-System` | CERN Zenodo DOI: `10.5281/zenodo.22373704` (https://doi.org/10.5281/zenodo.22373704)
  * 최상위 거점 관문 및 메인 저장소 (`soma-moa`) — GitHub: `deundeuni / soma-moa` | CERN Zenodo DOI: `10.5281/zenodo.22435773` (https://doi.org/10.5281/zenodo.22435773) | 관문 도메인: `somamoa.ai.kr`
* **법적 근거 및 적용 라이선스 규정 (Legal Statutes & Licenses)**
  * 문서·명세·설계도 표현물 라이선스: Creative Commons Attribution 4.0 International (CC BY 4.0)
  * 소스코드 및 구현물 라이선스: Apache License 2.0 (Apache-2.0)
  * 특허 방어 메커니즘: 방어적 공표(Defensive Publication)에 의한 Prior Art 확립 (구 DPL v1.0 표기는 2026-09-27자로 폐기 및 정정됨)
  * 기술적 기반 참조 표준: UCIe, CXL, TL-UL 등 모듈러 Interconnect 오픈 표준을 참조한 생존형 확장 규격

---

## 부록 A. 제개정 이력 (Revision History)

* **v2.9 (2026-09-13):** 엣지·온디바이스 자율 연산 필연성, 인간-AI 시공간 비대칭성 인지 창 및 자동차 모듈러 플랫폼 세그먼트 파생 아키텍처 규격 통합 정립 (`v2.9 Baseline`)
* **v2.10 (2026-10-03):** 라이선스 표기 정정(DPL v1.0 폐기, CC BY 4.0 및 Apache-2.0 구분 적용), 선행 연구 점검 및 개별 전제 근거 섹션(§0.1) 신설, 문서 작성 및 공개 목적 섹션(§0.2) 신설, 선행기술 조사의 범위와 한계 섹션(§2.2) 신설 및 상호참조 반영
* **v2.11 (2026-10-03):** 독창성·주장 어조 완화(§0, §7), 선사용권 관련 서술 제거(§7, §8), §0 항목 2 서술 단순화(AI 활용 및 작성자 최종 검토 명시), FASHION/Parikh/ISO 26262/Shi/Miller/Satyanarayanan/Nielsen 서지 및 인용 교정, 개시 항목 8(란다우어) §0.1 항목 복원 및 원논문 $k T$ 해설 추가, BranchyNet 에너지 표현 정정, §0.1 "상충·근접 연구" 줄 정리 및 항목 7·8 논문 제목 병기 및 근거 보강, §2.1 (b)/(c) 문장 분리 및 EnerInfer/Guégain/Kaya/Chen 서술 정밀화, §1/§2 전력·환경 및 검증 관련 표현 정리, §2 플랫폼 용어 완화, §0.2 헤더 표기 수정, §2.2 미발견 자료 취급 및 제3자 저작권 고지 추가 (`v2.11 Baseline`)
