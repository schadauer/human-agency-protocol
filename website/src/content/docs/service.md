---
title: "HAP Service – Technical Specification"
version: "v0.1"
date: "November 2025"
---

# Human Agency Protocol (HAP) Service – Technical Specification

**Version:** 0.1
**Date:** November 2025
**Status:** Draft for Implementation

---

## 1. Purpose

The **Human Agency Protocol (HAP) Service** provides a centralized and open infrastructure for running and managing HAP-compliant systems.  
It enables any educational or collaborative platform to **integrate agency-aware interaction logic**—without building complex infrastructure from scratch.

---

## 2. Why We Build It

The age of intelligent automation creates a paradox: **intelligence becomes abundant, but human agency becomes scarce**.  
HAP exists to restore that balance by giving platforms the ability to:

- Run **human-first AI interactions** that protect autonomy.  
- Measure **qualitative signals** (feeling understood, alignment, recognition) instead of efficiency-only metrics.  
- Maintain **privacy-by-design**, avoiding data centralization or content sharing.  
- Contribute to a shared, evolving protocol that defines *how AI and humans collaborate responsibly.*

---

## 3. Key Benefits for Platforms

| Benefit | Description |
|----------|--------------|
| **Faster Integration** | Prebuilt Inquiry and Feedback APIs—no need to implement HAP logic locally. |
| **Qualitative Intelligence** | Understand interaction quality (recognition, alignment, agency) without storing private content. |
| **Privacy Compliance** | No transcripts or personal data are collected—only structural, anonymized signals. |
| **Open Protocol, Central Service** | Platforms stay independent but use shared infrastructure that enforces HAP rules. |
| **Future-Proof** | Schema versioning ensures compatibility as the HAP standard evolves. |

---

## 4. System Overview

### Core Components

1. **Inquiry API** – Delivers HAP Blueprints and Signal Guides to local runtimes.  
2. **Feedback API** – Receives anonymized structural feedback from platform interactions.  
3. **Registry Management** – Allows creation, validation, and versioning of blueprints per tenant.  
4. **Governance Engine** – Enforces schema rules and prevents “precision drift” (mixing reflective and convergent modes).

### Supported Modes

| Mode | Focus | Allowed Metrics |
|------|--------|-----------------|
| **Reflective** | Recognition and understanding | `recognition_confirms`, `reflection_cycles`, `alignment_stability` |
| **Convergent** | Decision-making and collaboration | `shared_reference_detected`, `phase_advanced`, `owner_assigned` |

---

## 5. Data Flow Summary

1. **Platform requests Inquiry Blueprint** via `/v1/inquiry/blueprints`  
2. **Local system runs interaction** using the Blueprint logic  
3. **Feedback summary** (signals only, no text/media) is sent to `/v1/feedback/instances`  
4. **Aggregated results** generate anonymized scorecards for tenants

---

## 6. Architecture Diagram

```
Platform Runtime ──► Inquiry API ──► Blueprint Registry
       │                                  │
       └───► Feedback API ◄───────────────┘
                     │
            Aggregation & Governance
```

---

## 7. Development Plan

### Phase 1: Core APIs (Weeks 1–4)
- Implement Inquiry and Feedback endpoints  
- Validate against HAP schemas (reflective/convergent modes)  
- Add tenant authentication and namespace isolation  
- Support JSON snapshot export for offline runtimes

**Outcome:** Platforms can fetch blueprints and submit structural feedback.

---

### Phase 2: Feedback Intelligence (Weeks 5–8)
- Add structural analytics and scorecards  
- Implement k-anonymity and differential privacy thresholds  
- Build admin dashboard for tenants to manage namespaces  
- Enable batch feedback ingestion

**Outcome:** Platforms gain analytics on recognition quality and agency metrics without privacy risk.

---

### Phase 3: Federation and Governance (Weeks 9–12)
- Add review queue for blueprint publication to global registry  
- Support versioning, deprecation, and schema validation  
- Enforce mode-based rules (reflective/convergent guardrails)  
- Generate signed snapshots for external HAP runtimes

**Outcome:** Platforms can publish blueprints globally and trust the central registry as a standards authority.

---

## 8. Technical Stack

| Layer | Technology |
|--------|-------------|
| **API Framework** | FastAPI (Python) |
| **Database** | PostgreSQL (JSONB storage) |
| **Cache** | Redis |
| **Authentication** | OAuth2 / JWT |
| **Deployment** | Docker containers |
| **Data Export** | Signed JSON snapshots |

---

## 9. Security & Privacy Principles

- No raw text, transcripts, or media are ever stored.  
- All data is **structural**, aggregated, and anonymized.  
- Each tenant owns their namespace and can export or delete it anytime.  
- All schema validations are enforced server-side—no arbitrary JSON accepted.  
- Governance ensures reflective systems cannot drift into precision optimization.

---

## 10. Future Extensions

- Public global registry of verified blueprints  
- SDKs for JavaScript, Python, and Go runtimes  
- Integration templates for educational and collaboration tools  
- Optional on-premise deployment for sensitive institutions

---

## 11. Registry Management and Continuous Improvement

The **Registry** stores, validates, and evolves all blueprints and signal guides while preserving integrity and privacy.

### Blueprint Lifecycle

| State | Description |
|--------|--------------|
| **Draft** | Created by a tenant within their namespace. |
| **Candidate** | Under review; schema and mode checks applied. |
| **Stable** | Approved and used in production. |
| **Deprecated** | Retired; replaced by a newer version. |

Each blueprint is **mode-locked** (reflective or convergent). Platform owners can manage drafts, publish stable versions, and export signed JSON snapshots for their runtimes.

### Iterating and Improving Blueprints

Platforms enhance their blueprints through a **structured experimentation cycle**:

1. Detect friction or low recognition stability.  
2. Clone the current blueprint and adjust a single constraint (tone, word count, etc.).  
3. Run A/B testing between the versions.  
4. Collect structural feedback (`recognition_confirms`, `alignment_stability`, etc.).  
5. Compare results; promote winning variant to stable.  

**Reflective improvement:** deeper understanding, fewer corrections.  
**Convergent improvement:** clearer shared purpose, fewer reopenings.

### Governance Rules

- No free-text fields or raw content storage.  
- One controlled change per version for clean evaluation.  
- Scorecards only aggregate cohorts above anonymity thresholds.  
- Full tenant control—export or delete data at any time.

---

## 12. Summary

The HAP Service is **infrastructure for human autonomy in intelligent systems**.  
It lets any platform participate in the Human Agency Protocol ecosystem—responsibly, safely, and without rebuilding the foundation.

> “HAP turns qualitative understanding into a scalable standard—without reducing it to numbers.”

---

---

## 13. Signal Guides

**Signal Guides** are independent reference definitions that describe the meaning, structure, and validation rules of each measurable signal in the Human Agency Protocol.

They are versioned separately from Blueprints to preserve consistency across platforms and ensure interpretability across contexts.

### Structure Overview

```
/registry/
  ├── blueprints/
  │    └── reflect-meaning-restate-01@0.2.2.json
  ├── signal_guides/
  │    ├── recognition_confirms@1.0.0.json
  │    ├── alignment_stability@1.1.0.json
  │    └── phase_advanced@1.0.1.json
```

### In a Blueprint

Each blueprint references the signals it emits or expects:

```json
{
  "id": "reflect-meaning-restate-01",
  "version": "0.2.2",
  "mode": "reflective",
  "expected_signals": [
    {"id": "recognition_confirms", "version": "1.0.0"},
    {"id": "alignment_stability", "version": "1.1.0"}
  ],
  "prohibited_signals": ["phase_advanced"],
  "constraints": {
    "tone": "neutral",
    "word_count": "60-90"
  }
}
```

### Signal Guide Example

```json
{
  "id": "recognition_confirms",
  "version": "1.0.0",
  "agency_mode": "reflective",
  "definition": "Indicates that the system’s recognition of a human’s state was confirmed by the user.",
  "data_schema": {
    "type": "object",
    "properties": {
      "valence": {"type": "number", "minimum": -1, "maximum": 1},
      "confidence": {"type": "number", "minimum": 0, "maximum": 1}
    },
    "required": ["confidence"]
  },
  "emission_rules": {
    "only_after": "recognition_turn",
    "max_frequency": "1_per_session"
  }
}
```

### Registry Validation Rules

- All `expected_signals` in a blueprint must reference valid Signal Guides.  
- Mode consistency is enforced: reflective blueprints cannot use convergent signals.  
- Signal versions must match or be backward-compatible.  
- Tenants may propose new signals through a review process before federation.

### Why Separation Matters

| Benefit | Description |
|----------|--------------|
| **Stability** | Blueprints evolve rapidly; signals remain stable for long-term analysis. |
| **Cross-Domain Reuse** | Shared signal definitions enable interoperability between different HAP systems. |
| **Governance Clarity** | Signal semantics can be reviewed independently from private blueprint logic. |
| **Evolution** | New signals can be added experimentally without breaking old versions. |

> The blueprint defines *the choreography*, the signal guide defines *the language each step speaks.*

---
