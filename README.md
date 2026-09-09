> **Multilingual Notice:** This document is published in dual languages (Korean/English). (Korean version: [README.ko.md](README.ko.md))  
> **Original Authority Notice:** The supreme authority for legal and engineering judgment of this technical specification belongs to the Korean original (`README.ko.md`), and the English version serves as a secondary reference only.

# FIRST-LIGHT — Technical Specification for Integrated Evacuation & Universal Survival Auxiliary Guidance System Based on Multisensory Infrastructure Anchoring and Wide-Area Seamless Cross-Environment Transition
## Subtitle: Defensive Publication White Paper on Wide-Area Evacuation & Survival Integrating Outdoor Statutory Durable Anchors, Marine Buoys, Mountain Repeaters, Polar Ice Anchors, Orbital Modules, and Heterogeneous Multi-Device Linkage

* **Official Document Classification:** Defensive Publication / Prior Art White Paper
* **Original Intellectual Property (IP) Holder:** soma-moa (Conceiver: deundeuni)
* **Official Repository & Gateway:** github.com/soma-moa | somamoa.ai.kr
* **Applicable Licenses:** Creative Commons Attribution 4.0 (CC BY 4.0) & DPL v1.0 (Defensive Patent License)
* **Master Specification:** `LAST-LIGHT` (Inheriting indoor, underground, and orbital infrastructure anchoring and offline mechanisms)
* **Keywords:** FIRST-LIGHT, LAST-LIGHT, H-INDICATOR, Universal Survival, Seamless Transition, Structure First, Marine Buoy, Port Act, Mountain Repeater, Natural Parks Act, Polar Anchor, ICE-BELT, Co-Survival Bridge, Haptic Compass, Prior Art, chiplet-apu

---

## 0. Conceiver's Declaration and Master Architecture

### 0.1 Field-Driven Motivation & Co-Survival Philosophy Inheritance
Disaster films and educational media often focus primarily on the process of escaping underground or enclosed building structures. However, actual large-scale disasters frequently extend evacuee trajectories into extreme post-escape environments, including open sea drifting, mountain isolation, desert sandstorms, and polar whiteouts. This framework was conceived to fill this critical survival gap, expanding the field-driven Co-Survival philosophy established in `LAST-LIGHT` across global terrain and orbital space.

### 0.2 Master Specification (LAST-LIGHT) Inheritance & Citation
This specification directly cites and inherits the baseline engineering architecture of the master specification **`LAST-LIGHT`**, which governs indoor, underground, and orbital enclosed zones.
* **Inherited Provisions:** Cites `LAST-LIGHT` Sections 0.2–0.5 (Master Concept, Sensor Fusion Standard, Zero-Downtime Principle, Public Standards), Sections 3.B–3.G (ESTIMATION Calibration Algorithm, Emergency Power, Self-Healing Mesh, Co-Survival Bridge Haptic Compass Protocol, WebAR Onboarding, Multisensory Visualization), Section 4 (Dynamic Safety Control / Tri-State Isolation), and Section 5 (Standard Utilization Boundaries).
* **Core Differentiator:** While `LAST-LIGHT` uses indoor fire-rated facilities (hydrant boxes, raceways) under fire safety codes (NFPC) as L0 anchors, `FIRST-LIGHT` completely re-calibrates L0 anchors to outdoor statutory durable facilities (marine buoys, mountain repeaters, desert/polar beacons) and defines **Seamless Cross-Environment Transition (Seamless Transition)** from underground structures to four major outdoor extreme environments as a distinct core invention.

### 0.3 Structure First Principle for Outdoor Facilities
This system adopts fixed outdoor structures with guaranteed physical resistance against water, wind, snow, and pressure—mandated by relevant statutory regulations (Port Act, Natural Parks Act, Emergency Medical Service Act, Maritime Safety Act)—as primary reference points (L0 Anchor), rather than prioritizing sensor counts or network bandwidth. This materializes the 'Structure over Capacity' philosophy of `chiplet-apu` across wide-area space. Outdoor GNSS/GPS signals are subordinated as secondary macro-localization hints; fixed infrastructure anchors perform immediate 0-point position calibration upon signal capture.

### 0.4–0.5 Master Specification (LAST-LIGHT) Provisions Incorporation
Provisions 0.4 (Non-Exclusive Interoperability & Open Public Standards) and 0.5 (Operational Priority Principle) of this specification directly inherit and incorporate the corresponding specifications of the master specification `LAST-LIGHT`.

### 0.6 Universal Application Scope & Wide-Area Route Declaration
The core scope of protection of this system comprehensively applies to the following wide-area evacuation trajectory:
> **"Out of underground -> Out of ocean -> Out of mountain -> Out of desert/polar -> Auxiliary integrated survival route guidance"**

---

## 1. Version History & Genealogy

* **LAST-LIGHT Linkage & Genealogy:** Established indoor/underground/orbital 0-point calibration, Co-Survival Bridges, hydrant fire-rated anchors, and Graceful Fallback mechanisms.
* **FIRST-LIGHT Integrated Specification:** Reduced indoor redundancy via inheritance. Completely replaced L0 anchors with outdoor marine, mountain, desert, and polar statutory facilities; defined Seamless Transition from underground to wide-area outdoor environments as a standalone core invention.

---

## 2. 3-Tier Applied Architecture & Complete L0 Replacement

* **[L2] Wide-Area Auxiliary Guidance & Multi-Device UI Layer —** Co-Survival Bridges (across all physical form factors), AR HUD 3D guide lines, smart rings, life jacket embedded modules for evacuees/survivors; high-contrast NVG/thermal views and backend telemetry for rescue teams.
* **[L1] Perception, Calibration, Estimation & Handover Fabric —** Multispectral perception, microphone array sound source tracking, BLE Auracast/UWB, maritime LTE-M/satellite auxiliary signal fusion, Graceful Fallback controller, ring-buffer blackbox logging.
* **[L0] Wide-Area Outdoor Statutory Infrastructure Layer (Core Differentiator)**
  * **Marine/Ocean Zone —** Marine smart buoys, lighthouses/navigational aids (Maritime Aids to Navigation Act), breakwater fixed structures (Harbor Act), MAX-LIFE ICE-BELT seawater armor anchors.
  * **Mountain/Wilderness Zone —** Mountain shelters, trail national location number plates / smart repeaters (Natural Parks Act / Emergency Medical Service Act), elevated reflective panels.
  * **Desert/Polar Zone —** Polar station modules, glacier anchors, desert water towers / fixed bedrock beacons, solar/thermal emergency beacons.
  * **Space/Orbital Zone —** Space station living module external signs, airlock fire/pressure-rated chambers.
  * **Common Receptacles —** Heat-, pressure-, and impact-resistant distributed local blackbox memory embedded inside buoys, shelter chambers, and seawater casings.

### 2.5 Common Reliability Evaluation Layer Integration (H-INDICATOR Integration)
System health, hardware voltage error, RF path loss, DTN disconnect duration, and node synchronization density calculations within this wide-area framework directly reference the formula structure of the independent master specification **`H-INDICATOR`**.

$$H = \alpha \left(1 - \frac{V_{err}}{V_{max}}\right) + \beta \left(\frac{L_p}{2.6}\right) + \gamma \left(\frac{T_r}{T_o}\right) + \delta (1 - S_{node})$$

* **Formula Variable Definitions —** $V_{err}$: Power error voltage, $V_{max}$: Maximum allowable error voltage, $L_p$: RF path loss, $T_r$: DTN communication disruption duration, $T_o$: Valid reception period, $S_{node}$: Surrounding mesh node synchronization density ($0 \le S_{node} \le 1$). (For detailed mathematical derivations and parameter control logic, refer to the master specification `H-INDICATOR`.)
* **Operational Control —** When calculation yields $H > 0.85$, it acts as the decision index to execute Tri-State Isolation within 100ms while proactively transferring control to adjacent anchors.

---

## 3. Core Wide-Area System Blocks & Outdoor L0 Anchors

### A. Environment-Specific L0 Anchors & Legal Survival Grounds
* **Marine Smart Buoy & Navigational Aid Anchors —** Fixed structures under maritime aids to navigation standards and port regulations, maintaining fixed physical coordinates amidst waves and submersion. Projects BLE Auracast and acoustic signals across water surfaces to deliver 0-point coordinates to life jacket / bridge receivers worn by adrift survivors.
* **Mountain Shelter & Smart Repeater Anchors —** Managed under natural park regulations, mountain shelters and location-numbered repeaters supply terrain 0-point coordinates to AR glasses and smart rings in mountain fog and signal shadow zones.
* **Desert/Polar Fixed Beacons & ICE-BELT Anchors —** Glacier bedrock anchors and desert fixed beacons that maintain signal continuity via `MAX-LIFE ICE-BELT` cold/heat protective casing during whiteouts and sandstorms.

### B–G. Inherited Mechanisms & Specifications (Citation of LAST-LIGHT)
* ESTIMATION error calibration, emergency power linkage, self-healing mesh, Co-Survival Bridge standard haptic compass protocol (Left / Right / Forward / Hazard / Reached), WebAR passive QR/NFC quick release, and Visual SLAM 0-point calibration logic directly inherit specifications from `LAST-LIGHT`.

### H. Environment-Resistant Distributed Local Blackbox
Heat-, pressure-, and impact-resistant flash memory embedded within buoy chambers, mountain shelter fireproof boxes, and polar modules logs recent N hours of trajectory data in ring buffers. During central communication blackouts, recovered blackbox chips objectively reconstruct evacuation paths and feed data back into AI training pipelines.

---

## 4. Dynamic Safety Control & Legal Boundaries

* **Dynamic Control & Tri-State Isolation —** Incorporates the Rate Limiter, T-Reg Suppressor, and 0.1s Tri-State Physical/Logical Isolation controls from `LAST-LIGHT` to suppress physical and electrical interference with statutory safety equipment in outdoor environments.
* **Statutory Non-Substitutability —** Operates strictly as an auxiliary survival reference system and does not replace statutory safety facilities mandated by maritime, park, or fire regulations.

---

## 6. Core Novel Invention: Seamless Cross-Environment Transition (Seamless Transition)

The standalone novel aspect of this system lies in the autonomous handover of 0-point calibration control without positioning interruption as evacuees exit indoor/underground structures into extreme outdoor environments.

* **Underground -> Marine Transition —** The moment an evacuee exits underground parking or sea-tunnel L0 anchors, BLE Auracast/RF signals from coastal smart buoys and breakwater L0 anchors assume positioning control, continuously delivering haptic compass guidance to life-jacket-embedded bridges.
* **Underground -> Wilderness Transition (Mountain / Desert / Polar) —** Upon exiting underground zones into mountain fog or polar whiteouts where GNSS signals are impaired, mountain repeaters and polar beacons rapidly reset cumulative IMU drift errors to 0 within 100ms (Rapid Drift Reset).
* **Ground -> Orbital Transition —** Ground infrastructure anchor structures maintain identical 0-point calibration algorithms using space station living module pressure chambers and spacesuit-embedded haptic pads.

---

## 7. Practical Protection & Legal Framework

* **Original Language Authority Rule —** Legal and technical interpretation of this specification is governed strictly by the Korean original (`README.ko.md`). English and other translations serve solely as secondary references.
* **Comprehensive Prior Art Coverage —** All concepts disclosed herein—including Seamless Transition across wide-area environments, outdoor L0 anchoring, multi-form-factor Co-Survival Bridges, and multi-device Graceful Fallback—apply broadly as defensive prior art to mitigate private patent monopolization by third parties.
* **DPL License & Prior Use Rights —** Applies CC BY 4.0 and DPL v1.0 licenses, preserving legal prior use rights under Article 103 of the Korean Patent Act and 35 U.S.C. §273.
* **Defensive Publication Timestamp —** Defensive Publication Date: 2026-09-09 / GitHub Commit: [commit hash] / CC BY 4.0 + DPL v1.0 (CERN Zenodo DOI pending)

---

## 8. Sources & Ecosystem

* **Master Universal Survival Architecture & APU Controller —** `chiplet-apu-multi-system-survival-architecture` (GitHub: `deundeuni/chiplet-apu-multi-system-survival-architecture`)
* **Indoor / Underground Evacuation Auxiliary Infrastructure Master —** `LAST-LIGHT` (GitHub: `soma-moa/LAST-LIGHT`)
* **Health & Positional Uncertainty Evaluation Layer —** `H-INDICATOR` (GitHub: `soma-moa/FIRST-LIGHT/H-INDICATOR`)
* **Linked Survival Strategy & Sacrificial Armor —** `ARCHITECTURE_STRATEGY`, `MAX-LIFE-ICE-BELT`
* **Linked CWP Repositories —** `CWP-Battery-Swap`, `CWP-Clamping-Battery-Swap-System`, `CWP-Rolling-Self-Align-Battery-Swap-System`
* **Canonical Gateway & Main Repository —** `soma-moa` (GitHub: `deundeuni/soma-moa` | Domain: `somamoa.ai.kr`)
* **Document Completeness Notice —** Version numbers cited across this specification and linked repositories are variable elements subject to ongoing revision. The overarching prior art validity of the disclosed technical concepts applies broadly to master domain mechanisms independent of specific version numbers.

---

## Appendix A: Inventorship & AI Assistance Disclosure
* **System Architect & Sole Inventor —** deundeuni (soma-moa) — Sole intellectual entity responsible for total conceptualization, field motivation establishment, circuit combination design, and final technical decisions.
* **AI Assistance Disclosure —** All core technical architectures, haptic logic, mathematical formulas, and legal defense frameworks within this white paper belong strictly to the sole human inventor (deundeuni). AI tools (AI models) functioned under explicit human direction solely as auxiliary text refinement, translation, and structural formatting tools (Auxiliary Text Editing Tools), without participating in technical conception or inventive steps.
