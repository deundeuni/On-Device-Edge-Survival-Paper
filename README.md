> **Notice of Primary Authority:** The supreme legal and engineering authority of this technical specification resides in the Korean original (`README.ko.md`). `README.md` serves as a secondary English reference. In case of any discrepancy, the Korean original takes precedence.

# On-Device-Edge-Survival-Paper — Rationale for Autonomous Computation Necessity in Edge/On-Device Terminals, Cognitive Read-Time Window of Human-AI Spatiotemporal Asymmetry, Automotive Modular Platform Segment Derivation, and Physical Survival Architecture (v2.11 Baseline)

> This document addresses the structural necessity for universal edge devices—including smartphones, consumer terminals, public safety/administrative infrastructure, autonomous vehicles, unmanned robots, smart factory controllers, high-security zone devices, disaster response infrastructure, and domain-specific custom AI terminals—to perform localized autonomous computation. This mitigates the physical and economic limits of centralized cloud computing, power grid overload and ecosystem perturbation from excessive power generation infrastructure, physical latency limits of any network protocol (Network Protocol & Transport Layer Agnostic), air-gapped network isolation, thermodynamic limits of semiconductor elements, and AI overload hallucination risks.  
> This whitepaper is authored based on a universal survival architecture independent of specific enterprises, public institutions, or network protocols, applying modular platform sharing and segment derivation strategies from automotive engineering to define the scope of prior art invocation. **CC BY 4.0** applies to the documentation, specifications, and design expressions of this whitepaper, while the **Apache-2.0** license applies to published code and implementation source code. The fundamental purpose of this whitepaper is to establish prior art through defensive publication rather than granting patent licenses. (The former DPL v1.0 notation was corrected and deprecated as of 2026-09-27.)  
> **Conception, Organization, and Authoring:** deundeuni

---

## 0. Architecture Proposal & Core Claims Summary

1. **Architectural Background:**  
   This idea paper and architecture specification originated from the author's problem awareness to accommodate: communication latency due to central server dependency; physical light-speed propagation delay limits across any current or future network method (Universal Transport Protocol Layer); natural environment destruction caused by data center power surges and excessive power generation infrastructure construction; physical network disconnection (air-gapping) in high-security zones and public networks; chipset overheating and AI hallucination during urgent calculations; resource reallocation leveraging the spatiotemporal asymmetry between human 1–2 second cognition time and AI operation cycles; thermodynamic invariance of physical semiconductors; segment derivation control through automotive modular platform sharing mechanisms; and diverse custom AI terminal installation demands across personal, public, and corporate sectors. The authority to organize and structure this architecture—integrating the rationale for autonomous on-device computation, TL Bridge-based module isolation, query complexity-linked variable computation delay control, dynamic control of reasoning idle windows based on human-AI spatiotemporal asymmetry, automotive platform-derived segment structuring, network protocol agnosticism, universal applicability across user domains, multi-tier control topology, and 0.1ms/1ms localized preemptive action parameters—belongs to the author as a natural person.

2. **AI Tool Usage Notice:**  
   AI tools were utilized during the drafting and organization process of this whitepaper, and the final content was reviewed by the author. The conceptual intent and final copyright reside with the author.

3. **Summary of Top 10 Core Architectural Claims:**  
   - Claim 1: Rationale for On-Device Autonomous Computation Necessity — Includes localized autonomous inference configurations in terminals to address light-speed transport limits, air-gapped security, excessive power infrastructure construction, and data center power grid loads.  
   - Claim 2: Human-AI Spatiotemporal Asymmetry (Cognitive Read-Time Window) — Includes controls that reallocate human 1–2 second cognitive/reading idle time into GHz NPU dormant states, thermal relaxation, and hallucination verification budgets, recognized as valid execution only under conditions where extended latency directly yields verification accuracy improvements.  
   - Claim 3: Derivation from Automotive Modular Platform Sharing — Includes sharing a common survival baseline (TL Bridge, 3-Point Telemetry) while horizontally deriving into entry-level (Monolithic) vs. industrial (Chiplet), and base (Base) vs. extended (Extended Fusion) segments.  
   - Claim 4: Network Protocol & Transport Layer Agnosticism — Includes structures that prioritize offline terminal-internal decisions independently of transmission media (5G/6G, satellite, quantum, optical, mesh, etc.).  
   - Claim 5: 3-Point Telemetry-Based 0.1ms/1ms Localized Self-Healing — Includes simultaneously monitoring computation, fabric latency, and temperature to execute localized preemptive actions within 0.1ms upon internal fault detection and escalate to higher management layers.  
   - Claim 6: 1ms MIPI Switching and Tri-State (High-Z) Physical Isolation — Includes high-impedance switching of bus signals and display projection layers via hardware clock cycles (ns–tens of ns scale) and 1ms-level switching upon fault detection to mitigate view obstruction and fault propagation.  
   - Claim 7: Simultaneous Preservation of 3 Core Resources & Accuracy-Linked Variable Control — Includes scheduling that expands variable computation latency linked to question complexity to mitigate peak chipset heat, peak battery current, and AI hallucinations, while enforcing early exit upon computation failure if extended latency does not yield verification accuracy gains.  
   - Claim 8: Landauer's Principle-Based Substrate Invariance — Includes applying hardware governance across physical thermodynamic constraints of future computation substrates (silicon, photonics, quantum, bio-devices).  
   - Claim 9: Microsecond (μs) Physical Anti-Tamper — Includes hardware protection that triggers internal eFuse overvoltage and Key Zeroization within microseconds upon sensing physical decapsulation attacks to destroy internal secrets.  
   - Claim 10: Multidisciplinary/Multilingual Non-Invasive Coexistence Overlay (HMI) — Includes non-interfering governance that assists information via external spatial visual layers without arbitrarily modifying target system firmware or control panels.

---

## 0.1 Prior Research Review & Premises

This document is conceived based on the author's problem awareness regarding 'how edge and on-device terminals can be conceptualized in this manner.' The author does not claim to have been the first to invent these concepts. Following conception, existing papers, patents, and standards aligned with these directions were identified and cited as supporting evidence, with credit for individual techniques and concepts belonging to their respective original authors. Conflicting or closely related studies identified within the investigated scope are also documented. The contribution of this document lies in combining and structuring these elements within the edge/on-device context. (See §2.2 for scope and limitations.)

* **Item 1: On-Device Autonomous Computation Rationale & Offline Edge Independent Inference (Relates to Claim 1)**
  - Supporting Evidence — Mahadev Satyanarayanan, "The Emergence of Edge Computing", IEEE Computer, Vol. 50 [Issue, Pages, DOI Need Verification]; Weisong Shi et al., "Edge Computing: Vision and Challenges", IEEE Internet of Things Journal, Vol. 3, No. 5, pp. 637–646, 2016 (DOI: 10.1109/JIOT.2016.2579198). Research supporting local computation necessity to supplement central cloud propagation latency and network instability.
  - Conflicting / Neighboring Studies — Guégain et al., "The Battery Price of edge AI: A study of the Environmental Impact of LLM Inference on Mobile Devices" (arXiv:2609.11940). Reports based on abstract that on-device inference may be less energy-efficient than server-side batch inference.
  - Direct Evidence — Not identified within the investigated scope (requires additional investigation).

* **Item 2: Human-AI Spatiotemporal Asymmetry & Cognitive Idle Window Reallocation (Relates to Claim 2)**
  - Supporting Evidence — Robert B. Miller, "Response time in man-computer conversational transactions", Proc. AFIPS Fall Joint Computer Conference, 1968, pp. 267–277 (DOI: 10.1145/1476589.1476628); Jakob Nielsen, "Usability Engineering" [Publisher, Year Need Verification]. Research providing background on cognitive idle time and response time expectations in human-computer interaction.
  - Direct Evidence — Not identified within the investigated scope (requires additional investigation).

* **Item 3: Automotive Modular Platform & Segment Derivation Mechanism (Relates to Claim 3)**
  - Supporting Evidence — Timothy W. Simpson, "Product platform design and customization: Status and promise", AIEDAM [Volume, Pages Need Verification]; Marc H. Meyer & Alvin P. Lehnerd, "The Power of Product Platforms", Free Press, 1997 [Based on Simpson citation, bibliographic details Need Verification]. Research supporting modular platform premises deriving variable segments from common architectural baselines.
  - Direct Evidence — Not identified within the investigated scope (requires additional investigation).

* **Item 4: Protocol-Agnostic Offline Edge Independent Inference (Relates to Claim 4)**
  - Supporting Evidence — Mahadev Satyanarayanan, "The Emergence of Edge Computing", IEEE Computer, Vol. 50 [Issue, Pages, DOI Need Verification]; Weisong Shi et al., "Edge Computing: Vision and Challenges", IEEE Internet of Things Journal, Vol. 3, No. 5, pp. 637–646, 2016 (DOI: 10.1109/JIOT.2016.2579198). Research supporting terminal-internal determination premises to overcome network disconnection and latency.
  - Direct Evidence — Not identified within the investigated scope (requires additional investigation).

* **Item 5: 3-Point Telemetry Monitoring & Localized Self-Healing/Escalation (Relates to Claim 5)**
  - Supporting Evidence — 
    1) Autonomous Self-Healing & Autonomic Computing Architectures: Jeffrey O. Kephart & David M. Chess, "The Vision of Autonomic Computing", IEEE Computer, Vol. 36, No. 1, 2003, pp. 41–50 [Details/DOI Need Verification]; Steve R. White et al., "An Architectural Approach to Autonomic Computing", ICAC'04, 2004 [Details/DOI Need Verification].
    2) Vehicle Functional Safety Fault Tolerant Time Interval (FTTI) Concept: ISO 26262-1 functional safety standard defining the time span between fault occurrence and potential hazard manifestation without safety mechanisms.
    3) On-Chip Network Fault Mitigation & Self-Healing: Pengju Ren et al., "FASHION: Fault-Aware Self-Healing Intelligent On-chip Network", arXiv:1702.02313, 2017; Ritesh Parikh, "Routing and Topology Reconfiguration for Networks-on-Chip's Runtime Health", Univ. of Michigan Ph.D. Dissertation; Shashikiran Venkatesha & Ranjani Parthasarathi, "A Survey of fault mitigation techniques for multi-core architectures", arXiv:2112.14952, 2021.
    4) Multi-Core Thermal Real-Time Monitoring: K. Vaddina et al., "Self-Timed Thermal Sensing and Monitoring of Multicore Systems", DDECS 2009, pp. 246–251 (DOI: 10.1109/DDECS.2009.5012139).
  - Direct Evidence — A control structure combining simultaneous 3-point monitoring of computation/fabric latency/temperature with localized preemptive action and escalation to central monitoring was not identified within the investigated scope. (※ The 0.1ms parameter represents a hardware design target for local control responsiveness.)

* **Item 6: MIPI Switching & Tri-State (High-Z) Physical Isolation (Relates to Claim 6)**
  - Supporting Evidence — MIPI Alliance Specification for Display Serial Interface (DSI) / D-PHY [Version/Text Need Verification]. Specification materials for display and fabric physical interface signals.
  - Conflicting / Neighboring Studies — Refer to the Prior Patent References subsection.
  - Direct Evidence — High-Z physical tri-stating and 1-frame transparency upon fault detection were not identified within the investigated scope (requires additional investigation).

* **Item 7: Query Complexity-Linked Variable Computation & Early Exit Scheduling (Relates to Claim 7)**
  - Supporting Evidence — Alex Graves, "Adaptive Computation Time for Recurrent Neural Networks" (2016, arXiv:1603.08983 / DOI: 10.48550/arXiv.1603.08983); Surat Teerapittayanon et al., "BranchyNet: Fast inference via early exiting from deep neural networks" (2016 23rd ICPR, pp. 2464–2469, DOI: 10.1109/ICPR.2016.7900006); Kaya et al., "Shallow-Deep Networks: Understanding and Mitigating Network Overthinking" (2019, ICML, PMLR 97, pp. 3301–3310, arXiv:1810.07052); Snell et al., "Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters" (2024, arXiv:2408.03314); Chen et al., "Do NOT Think That Much for 2+3=? On the Overthinking of o1-Like LLMs" (2024, arXiv:2412.21187); Dhuliawala et al., "Chain-of-Verification" (arXiv:2309.11495, ACL Findings 2024 pp. 3563–3578, DOI: 10.18653/v1/2024.findings-acl.212); "MELTing point: Mobile Evaluation of Language Transformers" (2024, arXiv:2403.12844).
  - Conflicting / Neighboring Studies — EnerInfer: Energy-Aware On-Device LLM Inference (arXiv:2606.23001, framework managing energy, throughput, and thermal comfort); Kaya et al. 2019, Chen et al. 2024 (prior research on stopping/reducing computations without gain).
  - Direct Evidence — Not identified within the investigated scope (combining accuracy-linked termination with thermal, battery, and hallucination verification budgets).

* **Item 8: Landauer's Principle-Based Substrate Invariance & Thermal Control (Relates to Claim 8)**
  - Supporting Evidence — Rolf Landauer, "Irreversibility and Heat Generation in the Computing Process", IBM Journal of Research and Development, Vol. 5, No. 3, pp. 183–191, 1961 (DOI: 10.1147/rd.53.0183, secondary citation [Need Verification]); Brooks & Martonosi, HPCA 2001, pp. 171–182 [DOI Need Verification]; Kevin Skadron et al., "Temperature-aware microarchitecture", ACM SIGARCH Computer Architecture News 31(2), 2003, pp. 2–13 (DOI: 10.1145/871656.859620). Research supporting thermodynamic limits of bit erasure and microarchitecture-scale Dynamic Thermal Management (DTM).
  - Direct Evidence — While Landauer and DTM studies support thermodynamic/thermal management premises, applying hardware governance across arbitrary future computing substrates was not identified within the investigated scope.

* **Item 9: Physical Anti-Tamper & Decapsulation Destruction Mechanism (Relates to Claim 9)**
  - Supporting Evidence — Ross Anderson & Markus Kuhn, "Tamper Resistance — a Cautionary Note", 2nd USENIX Workshop on Electronic Commerce, 1996 [Author Notation Need Verification]; Sergei Skorobogatov, "Semi-invasive attacks: A new approach to hardware security analysis", UCAM-CL-TR-630 [Year Need Verification]; NIST FIPS 140-3, "Security Requirements for Cryptographic Modules" [Text Need Verification]. Research and standards supporting physical hardware invasive attack and anti-tamper controls.
  - Conflicting / Neighboring Studies — Refer to the Prior Patent References subsection.
  - Direct Evidence — Executing internal eFuse overvoltage Key Zeroization within microseconds upon decapsulation sensing was not identified within the investigated scope (requires additional investigation).

* **Item 10: Non-Invasive Visual Overlay Coexistence HMI (Relates to Claim 10)**
  - Supporting Evidence — Dhruv Jain et al., "Exploring Augmented Reality Approaches to Real-Time Captioning: A Preliminary Autoethnographic Study" [Conference, Authors, Details Need Verification]; Samaradivakara et al., arXiv:2501.02233. Research supporting augmented reality visual assistance and spatial overlay interfaces.
  - Conflicting / Neighboring Studies — Refer to the Prior Patent References subsection.
  - Direct Evidence — Non-interfering governance via external visual layers without modifying target system firmware was not identified within the investigated scope (requires additional investigation).

### Prior Patent References
* US 10,846,899 — "Methods and systems for augmented reality safe visualization during performance of tasks" [Subject to Patent Attorney Review]
* US 10,535,202 — "Virtual reality and augmented reality for industrial automation" [Subject to Patent Attorney Review]  
*(This list enumerates bibliographic references only and does not contain claim interpretations or legal assessments)*

Credit for individual techniques belongs to cited original authors; this document combines and structures them in an edge terminal context.

## 0.2 Purpose of Publication
This document is published for public benefit so that anyone can freely cite, utilize, and critique the ideas and supporting evidence related to edge/on-device computing. To this end, documentation/specifications/design materials are released under CC BY 4.0, and code/implementations under Apache-2.0.

---

## 1. Physical, Environmental, and Institutional Limitations of Centralized Cloud AI Computation

* **Mitigating Power CapEx Cliffs, Excessive Power Generation Infrastructure, and Ecosystem Perturbation** — Unlimited cloud expansion risks triggering hyper-scale data center construction costs, cooling water depletion, and excessive construction of nuclear, thermal, hydro, and next-generation power generation infrastructure (including SMRs) to meet massive energy demands. This incurs physical ecosystem burdens such as land degradation, aquatic ecosystem changes from thermal effluent, and potential environmental contamination; hence, on-device computing aims to distribute power consumption. There are also studies suggesting that on-device inference may be less energy-efficient than server-side batch inference (Guégain et al., arXiv:2609.11940, based on abstract).
* **Transmission Latency and Physical Transport Limits of Arbitrary Network Protocols (Wireless, Satellite, Space, Optical, Quantum, Mesh)** — Cellular communications (5G/6G/7G), low-Earth orbit (LEO)/geostationary (GEO) satellite networks, optical backhauls, quantum transmission, Wi-Fi/Bluetooth, and P2P mesh networks are merely illustrative examples. Regardless of the transmission layer utilized (Universal Transport Protocol Layer), physical speed-of-light propagation limits and router signal conversion delays make sub-millisecond real-time physical control responsiveness difficult to guarantee. Independent inference systems on terminal chipsets are required regardless of network advancements.
* **Air-Gapped Network Isolation Constraints in High-Security Zones and Public Infrastructure** — Semiconductor fabs, defense facilities, public sector administrative networks, research laboratories, and financial core networks isolate or strictly restrict external network connectivity to prevent espionage and data leaks. Because cloud-dependent AI becomes non-functional in air-gapped environments, terminal-internal independent computation systems are essential.
* **Mitigating AI Hallucination and Chipset Overheating under Time Constraints** — Attempting ultra-low latency processing of complex queries within constrained cloud/terminal resources increases NPU overheating risks, precision degradation, and premature context truncation, elevating hallucination risks.
* **Fragmentation of Domain/Custom AI Models and Central Server Incompatibility** — Personalized private models, public administrative models, and enterprise domain AI (sLLM/VLM) struggle to rely on generic clouds due to security, human rights, and real-time constraints, requiring on-device edge adaptability.

---

## 2. Rationales for Necessary Autonomous Computation in Edge and On-Device Terminals

Dedicated edge terminals (including smartphones) must execute localized computation at the chipset (NPU/APU) level due to physical realities, environmental conservation, automotive platform structure derivation, transmission constraints, and institutional security requirements:

* **Human-AI Spatiotemporal Asymmetry and Empirical Verification Mechanism for Reasoning Window** — The 1–2 second cognitive/reading duration brief to humans represents a vast temporal horizon for GHz-clocked AI NPUs, permitting hundreds of millions to billions of operations. Reallocating this micro-time gap into NPU dormant states, thermal relaxation, and multi-stage verification steps is treated as a valid design only when extended reasoning time yields empirical accuracy gains; if extended latency fails to improve accuracy, it is classified as computation failure and triggers early exit, simultaneously pursuing hallucination reduction and resource efficiency.
* **Derivation from Automotive Modular Platform Sharing Structures** — Just as automotive modular platforms (E-GMP, MQB) derive entry-level to high-performance segments from a shared structural baseline, this whitepaper fixes core safety baselines (TL Bridge, 3-Point Telemetry, 0.1ms E-Stop) as common platform specifications and extends horizontally across sub-segments (Monolithic vs. Chiplet, Base vs. Extended Fusion). This adapts widely used platform strategies from industry.
* **Protocol-Agnostic Offline Independence** — Operates independently of 5G/6G cellular, satellite, quantum, or mesh networks, remaining unaffected by physical propagation delays or communication shadows, completing sub-millisecond determinations internally.
* **Universal Domain Expansion and Custom AI System Integration** — Serves custom AI models built by personal (consumer), public (administrative, fire, police, medical), and corporate (industrial, manufacturing, finance) entities within hardware-enforced autonomous sandboxes.
* **Complexity-Linked Variable Computation Latency & Core Resource Preservation** — Preemptively detects query complexity to dynamically adjust latency budgets, mitigating peak chipset thermal spikes, battery peak currents, and AI hallucinations by securing reasoning windows. Hard deadline timeout ceilings take precedence in safety-critical control layers (such as autonomous vehicle emergency maneuvers).
* **Environmental Preservation and Power Grid Load Relief (Green Edge Computing)** — Distributing micro-computations across billions of personal, public, and corporate terminal NPUs may reduce power consumption of centralized data centers and pressure for power plant expansion, though effects have not been verified through empirical measurement.
* **Sub-Millisecond Real-Time Physical Control Requirements** — Autonomous vehicle evasion, emergency evacuation guidance, industrial motor load control, and robotic arm positioning demand latencies tied directly to system survival, making localized chipset determinations unavoidable.
* **Energy Efficiency via Distributed Data Processing and Confidentiality/Privacy Retention** — Processing and refining raw data locally rather than transmitting massive unrefined streams has the potential to mitigate communication power consumption, though effects have not been verified through empirical measurement.
* **Offline Autonomy in Air-Gapped Environments** — Maintains failsafe function and safety controls in air-gapped security zones, public safety networks, or harsh environments where external network connectivity is physically severed.
* **Base vs. Extended Fusion Dual-Tier Sensor Integration** — Defines lightweight implementations using standard built-in sensors as Base configurations to mitigate thermal wear, facial heat limits, and battery drain, while encompassing Extended Fusion combinations incorporating external detachable sensors (non-contact EMF, thermal imaging, smart rings).

---

### 2.1 Related Work & Differentiation

Claims 2 (Human-AI Spatiotemporal Asymmetry) and 7 (Complexity-Linked Variable Computation & Early Exit) acknowledge existing literature in variable inference, early exit, and thermal/energy-aware scheduling, defining the following control mechanisms (see §2.2 for scope and limitations):

* **Comparison with Adaptive Computation Step Allocation Research** — Alex Graves, *Adaptive Computation Time for Recurrent Neural Networks* (2016, arXiv:1603.08983 / DOI: 10.48550/arXiv.1603.08983) addressed dynamically allocating neural network computational steps based on input task difficulty.
* **Comparison with Early Exit-Based Latency Reduction Research** — Surat Teerapittayanon et al., *BranchyNet: Fast inference via early exiting from deep neural networks* (2016 23rd ICPR, pp. 2464–2469, DOI: 10.1109/ICPR.2016.7900006) proposed adding early exit branches to deep neural network intermediate layers to reduce inference latency and energy usage.
* **Comparison with Thermal and Energy-Aware Control Research** — Prior research includes Kevin Skadron et al., *Temperature-aware microarchitecture* (ACM SIGARCH Computer Architecture News 31(2), 2003, pp. 2–13, DOI: 10.1145/871656.859620) and EnerInfer (arXiv:2606.23001, managing energy, throughput, and thermal comfort).
* **Characteristics of the Whitepaper's Inference Control** — This whitepaper goes beyond merely aiming for latency reduction or isolated thermal/energy scheduling: (a) it intentionally reallocates the 1–2 second Cognitive Read-Time Window (human-computer spatiotemporal asymmetry) into NPU dormant state, thermal relaxation, and hallucination verification budget; (b) while thermal/energy integrated management has prior research such as EnerInfer, this whitepaper describes a configuration that incorporates the cognitive read-time window and hallucination verification budget as variables within the same scheduling loop. The termination or reduction of additional computations without gain has been addressed in prior work such as Kaya et al. 2019 and Chen et al. 2024, and this whitepaper describes combining this with cognitive read-time window, thermal, and battery budgets. (c) If extended latency allocation fails to yield improvements in verification accuracy, it defines the execution as a computation failure and enforces an early exit, described as a characteristic of the combination with prior research.

---

### 2.2 Scope and Limitations of Prior Art Review

* **Individual Author Investigation:** Prior research and patent citations were collected by an individual author utilizing AI tools as of 2026-10-03 via public web searches; this does not constitute a search by professional search firms or patent attorneys. Exhaustive global searches are practically impossible for an individual and were not intended. AI searches and summaries may contain errors.
* **Access Limitations:** Paywalled or subscription-restricted literature (certain journal texts, standards documents) could not be reviewed in full, relying on abstracts or secondary records. Citations reflect only verified scopes.
* **Search Scope:** Focused primarily on English web searches, public abstracts, and citation records. Patent databases (KIPRIS, Google Patents, Espacenet), non-English literature, and proprietary documents were not systematically searched. Listed patent references contain bibliographic data only without claim interpretation.
* **Omission Possibility:** Identical or similar prior research, patents, or products may exist. "Not identified within the investigated scope" denotes absence within the author's public English web search scope and does not guarantee absolute novelty or total absence of prior art.
* **Error Potential:** Bibliographic details may contain errors; verified discrepancies are corrected in Appendix A. Copyrights of cited materials belong to respective rights holders.
* **Not Legal Judgment:** Descriptions do not constitute legal determinations of novelty, inventive step, or non-infringement, nor legal advice. Professional patent attorney consultation is recommended (§7).
* **Handling of Undiscovered Materials:** Should identical or similar prior research/patents be discovered later, original author credits will be acknowledged and documented in Appendix A.

---

## 3. Edge Control Mechanism Based on Universal Modular Survival Architecture

Based on the `ARCHITECTURE_STRATEGY.md` specification, edge and on-device terminals overcome monolithic limitations by adopting chiplet/modular integration structures to achieve self-healing computation:

* **Monolithic Constraint Relief & TL Bridge Coupling** — Prevents thermal wear and fault propagation associated with centralized single-chipset designs via modular chiplet isolation. Transmits reverse backpressure signals through TL Bridge interfaces during AQL command translation when queues reach thresholds, preventing memory overload.
* **Cognitive Read-Time Window-Based 2-Stage Dynamic Resource Control & Early Exit** — Activates 1ms-scale NPU inference upon initial events, then throttles (Dormants) or shifts NPUs to steady-state inference during human 1–2 second cognitive read times. Enforces early exit when verification iterations fail to yield accuracy gains, preventing infinite latency extension.
* **Universal Custom AI Dynamic Sandbox & Resource Partitioning** — Provides dynamic partitioning for heterogeneous custom AI agents (personal, public, corporate) to occupy NPU/APU slice resources independently, mitigating mutual interference.
* **Complexity-Linked Dynamic Cooldown & Accuracy-Linked Scheduling** — Restrains peak NPU clocks during complex queries, allocating extended latency budgets while dynamically monitoring accuracy yields to execute thermal suppression and verified inference. Combines quantization and distributed caching to maintain steady DRAM bandwidth usage.
* **Multi-Tier Control Topology & 3-Point Telemetry** — Interlinks individual node autonomy, team-internal control, intermediate management, peer-to-peer control, and central control stations (CCS). Monitors 3-point telemetry (computation, fabric latency, temperature) to execute localized preemptive actions within 0.1ms upon partial failure, escalating to upper managers.
* **Multidisciplinary/Multilingual Coexistence Bridge Non-Invasive Overlay** — Implements non-invasive, non-interfering governance assisting information via external spatial visual layers without modifying target PLC/NC firmware, public control circuits, or original media.

---

## 4. Overcoming Physical Constraints, Seamless Self-Healing, Anti-Tamper, and Invariance of Physical Substrate

* **Universal Physical Substrate Invariance** — In accordance with Landauer's principle ($k T \ln 2$), thermodynamic energy dissipation during bit erasure, power density limits, and speed-of-light propagation delays are invariant physical laws. (The original Landauer 1961 paper described minimum heat generation on the scale of $k T$, while $k T \ln 2$ is a formalized notation in subsequent literature.) This whitepaper's hardware control and local survival governance apply comprehensively across silicon, photonics, quantum, or bio-molecular substrates.
* **Power Density, Thermal Control, and Resource Occupation Suppression (T-Reg)** — Dynamically senses telemetry to regulate clocks, enforcing hardware rate limits when self-healing module bus occupancy exceeds thresholds (5%–30%) to prevent load transfer.
* **Leukocyte Asynchronous Stealth Scan** — Asynchronously and randomly samples bus traffic, detaining infinite loops or unauthorized anomaly packets into isolated buffers immediately upon detection.
* **Tri-State (High-Z) Physical Isolation & 1ms MIPI Switching** — Switches physical buses and projection layers to high-impedance (High-Z) via hardware clock cycles (ns–tens of ns scale) and 1ms-level switching upon computation errors or overload, achieving transparency within 1 display frame (16.6ms) to eliminate view obstruction.
* **Independent Safety IP & Anti-Tamper Physical Neutralization** — Executes internal eFuse overvoltage and Key Zeroization within hardware control sequences (μs scale) upon sensing physical decapsulation or chip analysis, permanently destroying edge secrets, public data, and custom AI weights.
* **L0 Biomimetic Structural Clearance/Stress Absorption** — Absorbs thermal expansion stress and clearance errors at semiconductor interposers, TSVs, and physical connectors in L0 (Physical Hardware Layer — see `Chiplet-APU-Multi-System-Survival-Architecture`) using biomimetic structures (barnacle adhesive protein mechanisms).

---

## 5. Domain-Specific Applications and Horizontal Expansion References

* **Personal & Consumer Mobile Terminals (Personal Sector)** — Governs custom AI execution via OS kernel-level NPU sandboxes on personal smartphones, tablets, consumer AR glasses (BYOD), and smart rings. Preserves chipset, battery, and AI reliability via human-AI spatiotemporal asymmetry and query-linked latency control, seeking to mitigate data center power transfer risks (unverified by empirical measurement).
* **Public Institutions, Local Governments, and National Infrastructure (Public Sector)** — Safely runs public-specialized AI on administrative terminals, fire/police evacuation infrastructure, public medical devices, and traffic control systems under isolated or satellite/mesh networks, assisting public safety guidance.
* **High-Security Zones & Smart Factory Dedicated Terminals (Enterprise Sector)** — Directly connects to controllers in air-gapped semiconductor fabs and defense lines, mitigating enterprise domain AI leaks. Self-records error-to-preemption lifecycles as CBOR anonymous logs post-PII destruction, automatically transferring and documenting logs to corporate infrastructure (NAS/S3/MES).
* **Robotaxi, Autonomous Driving, and Custom Robotics Mobility (Mobility & Robotics Sector)** — Processes LiDAR/camera data at ultra-low latency, combining humanoid robot mechanical and clutch controls to execute independent safe stops and evasions during external server disconnections while isolating custom AI control loops.
* **Disaster Evacuation Guidance Infrastructure (`LAST-LIGHT`) & Non-Invasive Spatial HMI (`POLYLINK-HUD`)** — Operates mesh computations across anchor nodes using residual energy during power/communication blackouts, providing non-invasive spatial captions and public guidance overlays via personal AR glasses HUDs.

---

## 6. Comprehensive Definitions of Layer, Topology, and Universal Transport Protocol Agnosticism

This specification is not limited to specific computational physical media, transmission networks, or software layers, encompassing all technical means achieving equivalent structural goals within prior art scope:

* **Universal Network Protocol & Transport Layer Agnosticism** — Cellular standards (5G, 6G, 7G) serve merely as examples; encompasses LEO/GEO satellite networks, space backhauls, quantum networks, optical fiber fabrics, Wi-Fi, Bluetooth, and P2P mesh networks. Applying on-device computation and survival self-healing to compensate for network limits falls under this specification's prior art scope.
* **Execution Layer & Physical Media Agnosticism** — Encompasses microcode, firmware, OS kernel, hypervisor, and AI accelerator agent layers, alongside co-packaged optics (CPO), quantum sensing/entanglement, molecular/bio-devices, and terahertz inter-chip communication/verification media.

---

## 7. Practical Protection & License Separation

* **Principle of Original Supremacy:** Legal and technical interpretation of this specification prioritizes the Korean original (`README.ko.md`); English and other translations serve secondary reference functions.
* **Separate Application of Document and Source Code Licenses:** **CC BY 4.0** applies to documentation, specifications, visual materials, and design expressions; **Apache-2.0** applies to published source code and hardware implementations. CC BY 4.0 does not grant patent licenses; defensive effects rely on prior art establishment and timestamped publication via defensive publication. (The former DPL v1.0 notation was deprecated and corrected as of 2026-09-27.) CC BY 4.0 and Apache-2.0 apply strictly to author-created expressions; copyrights of cited third-party papers, standards, and trademarks belong to respective rights holders.
* **Comprehensiveness of Scope:** Modular assembly, TL Bridge coupling, multi-tier control topologies, automotive platform segment derivation, query complexity-linked variable computation latency, human-AI spatiotemporal asymmetry 1–2 second cognitive read-time window reallocation, early exit conditions, substrate invariance (Landauer's principle), 3-core resource preservation, protocol agnosticism, universal domain expansion, green edge power grid relief linkages, 1ms MIPI switching, microsecond anti-tamper destruction, non-invasive black-box error routing, and Base/Extended Fusion dual-tier sensor integration are included within the scope of this prior art publication and invocation.
* **Non-Intentional Omission & Non-Exhaustive Disclaimer:** Technical standards, public principles, statutes, and repository lists cited are illustrative and non-exhaustive. Unintentional omissions of specific standards or equivalent prior art due to author limitations do not constitute intentional exclusion. This disclaimer affirms non-intentional omission and does not improperly absorb third-party prior art into this whitepaper's scope.
* **Defensive Publication:** This whitepaper primarily aims at defensive prior art publication. Professional patent attorney review and verification are recommended regarding the specific scope of legal and patent defense effects. (See §2.2 for scope and limitations of prior art review)
* **Separation of Commercialization Details:** The whitepaper original contains pure open-source and prior art disclosures only; proprietary revenue models and commercial execution plans are managed in separate technical documents.

---

## 8. Sources & Records

* **Soma-Moa Ecosystem Repositories & DOIs (Title-Kebab-Case Baseline)**
  * Master Universal Survival Architecture Hub (`Smart-System-Multi-Survival-Architecture`) — GitHub: `deundeuni / smart-system-multi-survival-architecture`
  * Upper Universal Survival Architecture & APU Controller (`Chiplet-APU-Multi-System-Survival-Architecture`) — GitHub: `deundeuni / Chiplet-APU-Multi-System-Survival-Architecture` | CERN Zenodo DOI: `10.5281/zenodo.22374987` (https://doi.org/10.5281/zenodo.22374987)
  * Biomimetic Thermodynamic Resilience Architecture (`Biomimetic-Thermodynamic-Resilience-Architecture`) — GitHub: `deundeuni / Biomimetic-Thermodynamic-Resilience-Architecture`
  * Seaweed-Anchored Mutualistic Marine Structure (`Seaweed-Anchored-Mutualistic-Marine-Structure`) — GitHub: `deundeuni / Seaweed-Anchored-Mutualistic-Marine-Structure`
  * Whitepaper Independent Repository (`On-Device-Edge-Survival-Paper`) — GitHub: `deundeuni / On-Device-Edge-Survival-Paper` | Main Whitepaper Files: `README.md` (Secondary English) / `README.ko.md` (Korean Original)
  * Press/Brake/Shear Edge Safety Paper Repository (`Press-Brake-Shear-Edge-Safety-Paper`) — GitHub: `deundeuni / Press-Brake-Shear-Edge-Safety-Paper` | Main Whitepaper Files: `README.md` (Secondary English) / `README.ko.md` (Korean Original)
  * Master Architecture Strategy Specification (`ARCHITECTURE_STRATEGY.md`) — Included in GitHub: `soma-moa / chiplet-apu-multi-system-survival-architecture` repository | Accompanied by Korean original `ARCHITECTURE_STRATEGY.ko.md` v3.4 (2026-09-27)
  * Multilingual Non-Invasive AR HUD Spatial HMI Gateway (`POLYLINK-HUD`) — GitHub: `deundeuni / POLYLINK-HUD` | CERN Zenodo DOI: `10.5281/zenodo.22726318` (https://doi.org/10.5281/zenodo.22726318)
  * Disaster Evacuation Guidance Infrastructure (`LAST-LIGHT`) — GitHub: `deundeuni / LAST-LIGHT` | CERN Zenodo DOI: `10.5281/zenodo.22373189` (https://doi.org/10.5281/zenodo.22373189)
  * Optical Perception & Spatial Exploration Infrastructure (`FIRST-LIGHT`) — GitHub: `deundeuni / FIRST-LIGHT` | CERN Zenodo DOI: `10.5281/zenodo.22683225` (https://doi.org/10.5281/zenodo.22683225)
  * Wearable Micro Thermal Stress Mitigation Module (`MAX-LIFE-ICE-BELT`) — GitHub: `deundeuni / MAX-LIFE-ICE-BELT` | CERN Zenodo DOI: `10.5281/zenodo.22373686` (https://doi.org/10.5281/zenodo.22373686)
  * CWP Entry Guidance Alignment (`CWP-Entry`) — GitHub: `deundeuni / CWP-Entry` | CERN Zenodo DOI: `10.5281/zenodo.22683234` (https://doi.org/10.5281/zenodo.22683234)
  * CWP Battery Swap Docking (`CWP-Battery-Swap`) — GitHub: `deundeuni / CWP-Battery-Swap` | CERN Zenodo DOI: `10.5281/zenodo.22373538` (https://doi.org/10.5281/zenodo.22373538)
  * CWP Electromagnetic Clamping (`CWP-Clamping-Battery-Swap-System`) — GitHub: `deundeuni / CWP-Clamping-Battery-Swap-System` | CERN Zenodo DOI: `10.5281/zenodo.22373722` (https://doi.org/10.5281/zenodo.22373722)
  * CWP Rolling Self-Align (`CWP-Rolling-Self-Align-Battery-Swap-System`) — GitHub: `deundeuni / CWP-Rolling-Self-Align-Battery-Swap-System` | CERN Zenodo DOI: `10.5281/zenodo.22373704` (https://doi.org/10.5281/zenodo.22373704)
  * Top-Level Gateway & Main Repository (`soma-moa`) — GitHub: `deundeuni / soma-moa` | CERN Zenodo DOI: `10.5281/zenodo.22435773` (https://doi.org/10.5281/zenodo.22435773) | Gateway Domain: `somamoa.ai.kr`
* **Legal Foundations & Applicable Licenses**
  * Documentation, Specifications, and Design Expressions License: Creative Commons Attribution 4.0 International (CC BY 4.0)
  * Source Code and Implementation License: Apache License 2.0 (Apache-2.0)
  * Patent Defense Mechanism: Prior Art establishment via Defensive Publication (former DPL v1.0 notation deprecated and corrected as of 2026-09-27)
  * Technical Baseline Standards: Survival extension specifications referencing open modular interconnect standards such as UCIe, CXL, and TL-UL

---

## Appendix A. Revision History

* **v2.9 (2026-09-13):** Unified baseline established integrating on-device/edge autonomous computation rationale, human-AI spatiotemporal asymmetry cognitive window, and automotive modular platform segment derivation (`v2.9 Baseline`).
* **v2.10 (2026-10-03):** Corrected license notations (DPL v1.0 deprecated, separate CC BY 4.0 and Apache-2.0 application), added Prior Research Review & Premises section (§0.1), added Purpose of Publication section (§0.2), added Scope and Limitations of Prior Art Review section (§2.2), and reflected cross-references.
* **v2.11 (2026-10-03):** Tone down of originality/claim tone (§0, §7), removal of prior commercial use rights descriptions (§7, §8), simplification of §0 item 2 text (AI usage and author final review specified), bibliographic corrections for FASHION/Parikh/ISO 26262/Shi/Miller/Satyanarayanan/Nielsen, restoration of item 8 (Landauer) in §0.1 with original paper $k T$ explanation, correction of BranchyNet energy expression, alignment of §0.1 "Conflicting/Neighboring Studies" and addition of titles/evidence for items 7 & 8, separation of sentences in §2.1 (b)/(c) and refining EnerInfer/Guégain/Kaya/Chen descriptions, expression cleanup for power/environment and verification in §1/§2, softening of platform strategy terminology in §2, §0.2 header formatting fix, §2.2 handling of undiscovered materials and third-party copyright disclaimers added (`v2.11 Baseline`).
