<div align="center">

# 🔗 ChainGuard
### Cross-Tier Supply Chain Fraud Intelligence

**Pre-Disbursement Fraud Detection for Multi-Tier Supply Chain Finance**

Detecting fraud hidden across supplier networks before financing approval.

![Status](https://img.shields.io/badge/Status-Hackathon%20Build-brightgreen)
![Domain](https://img.shields.io/badge/Domain-Supply%20Chain%20Finance-blue)
![Detection](https://img.shields.io/badge/Detection-Pre--Disbursement-red)
![Stack](https://img.shields.io/badge/Stack-Python%20%7C%20Graph%20Analytics%20%7C%20Streamlit-orange)
![License](https://img.shields.io/badge/License-Hackathon-lightgrey)

---

> **"Each invoice looked valid. Together, they formed a $47M fraud."**
> ChainGuard reveals risks invisible to isolated invoice checks.

</div>

---

## 🚨 The Problem

Supply Chain Finance (SCF) allows lenders to release funds based on supplier invoices across multiple tiers:

**Tier-1 → Tier-2 → Tier-3 suppliers**

A real-world fraud case demonstrated:

- 340 fabricated invoices worth **~$47M**
- Each invoice passed traditional validation
- Multiple lenders financed the same economic activity
- Goods never existed
- Circular trading masked exposure
- Fraud became visible only after defaults occurred

Traditional systems validate **documents**.
Fraud emerges from **relationships**.

---

## 💡 What is ChainGuard?

ChainGuard is a **pre-disbursement fraud intelligence layer** designed for lenders.

It answers a single decision-critical question:

> **Should this invoice be trusted before funds are released?**

The system correlates invoices, suppliers, transactions, and behavioral signals across the entire supply chain network and produces an **explainable risk score**.

---

## 🧭 Design Principles

ChainGuard is built on three core assumptions:

1. Fraud manifests at the **network level**, not document level.
2. Economic infeasibility appears **before financial default**.
3. Data silos between lenders create systemic blind spots.

Therefore, detection must analyze **relationships, timing, and feasibility simultaneously**.

---

## 🌍 How Fraud Happens in Real Life

```
1️⃣  Supplier generates invoice
2️⃣  Lender finances invoice after validation
3️⃣  Same trade reappears across supply chain tiers
4️⃣  Multiple lenders unknowingly finance duplicates
5️⃣  Circular trade loops hide fraud exposure
6️⃣  Losses appear only after payment failure
```

Fraud becomes visible only when the **entire network** is analyzed together.

---

## 🧨 Fraud Threat Model

ChainGuard assumes adversaries may:

- Create syntactically valid invoices
- Coordinate across shell suppliers
- Exploit lender data isolation
- Inflate invoice velocity gradually
- Recycle invoices via circular trade loops

Detection therefore targets **behavioral inconsistencies**, not formatting anomalies.

---

## 🔍 Fraud Typologies Detected

| Fraud Type | Description |
|---|---|
| 🧾 **Phantom Invoices** | Fabricated trade activity |
| 🔁 **Double Financing** | Same invoice funded multiple times |
| 📈 **Over-Invoicing** | Value exceeds economic capacity |
| 🔄 **Carousel Trades** | Circular A → B → C → A transactions |
| 💧 **Dilution Fraud** | Manipulated post-collection reporting |
| 🌊 **Cross-Tier Cascading** | Exposure multiplied across tiers |

---

## ⚙️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    DATA INGESTION LAYER                      │
│   Invoices │ Purchase Orders │ GRN │ ERP Feeds │ Payments   │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│              MULTI-LAYER FRAUD DETECTION ENGINE              │
│                                                             │
│   Layer 1: Invoice Fingerprinting & Deduplication           │
│   Layer 2: Feasibility Scoring (Revenue vs Volume)          │
│   Layer 3: Velocity & Sequencing Analysis                   │
│   Layer 4: Graph Analysis — Cycles & Cascades               │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                  RISK INTELLIGENCE LAYER                     │
│        Weighted Signal Aggregation → Risk Score (0–100)     │
└─────────────────────────┬───────────────────────────────────┘
                          │
            ┌─────────────┼─────────────┐
            ▼             ▼             ▼
         🟢 Low        🟡 Medium      🔴 High
       Auto Approve   Manual Review    Block
```

---

## 🌐 Why Graph-Based Detection?

Supply chains naturally form networks:

- **Nodes** → Companies
- **Edges** → Transactions
- **Cycles** → Potential fraud loops

Graph traversal enables detection of circular trading, abnormal relationship density, and disconnected economic flows.

Tabular validation cannot capture these structures.

---

## 🧠 Detection Pipeline

| Step | Module | Purpose |
|------|--------|---------|
| 1 | Invoice Input | Financing request received |
| 2 | Fingerprinting | SHA-256 invoice identity check |
| 3 | Graph Analysis | Multi-tier relationship mapping |
| 4 | Feasibility Checks | Economic realism validation |
| 5 | Behavioral Analysis | Velocity & sequencing anomalies |
| 6 | Risk Scoring | Explainable fraud probability |
| 7 | Alert Engine | Pre-disbursement decision |

---

## 📊 Example Risk Report

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  CHAINGUARD RISK REPORT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  Invoice ID   : INV-2024-00847
  Supplier     : XYZ Trading Co.
  Amount       : ₹4,80,00,000

  Risk Score   : 82 / 100  🔴 HIGH

  Flags:
  ✗ Duplicate invoice across lenders
  ✗ Invoice volume exceeds revenue by 40×
  ✗ Circular trade detected

  Recommendation: BLOCK DISBURSEMENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🏗️ Technology Stack

| Layer | Technology |
|---|---|
| Backend | Python, FastAPI |
| Graph Engine | NetworkX / Neo4j |
| Analysis | Statistical + Rule-Based Models |
| Frontend | Streamlit / React |
| Data | Synthetic SCF datasets |
| Fingerprinting | SHA-256 hashing |

---

## 📏 Evaluation Strategy

Prototype performance evaluated using:

- Fraud detection recall across simulated cascades
- False positive rate per supplier tier
- Detection latency before disbursement
- Network anomaly precision

Goal: maximize early detection while minimizing operational friction.

---

## ⚠️ Current Limitations

- Synthetic datasets used for prototype testing
- Cross-lender data simulated
- Risk weights manually calibrated
- Real-time streaming under development

---

## 📈 Expected Impact

- 🛑 Prevent fraud before funds leave lenders
- 🔁 Reduce duplicate financing exposure
- 🕸️ Detect hidden network-level fraud
- 📊 Provide explainable risk decisions
- 📡 Scale across multi-tier ecosystems

---

## 🔭 Future Scope

- [ ] Real-time ERP integrations via REST APIs
- [ ] Kafka-based streaming ingestion
- [ ] Adaptive ML risk calibration
- [ ] Multi-bank intelligence sharing
- [ ] Regulatory audit modules

---


## 🏆 What We Are Working Towards

Supply chain fraud is not a niche problem — it costs lenders and economies billions every year. Most of it goes undetected until after the money is gone.

We are working towards a world where **no lender finances a fraudulent invoice** simply because they lacked visibility into the network around it.

ChainGuard is our step in that direction — a system that treats fraud as a **network problem**, not a document problem, and catches it **before damage is done**.

This is a hackathon prototype today. The problem it solves is real, urgent, and largely unsolved at scale.

---

<div align="center">

**ChainGuard — Fraud hides in connections, not documents.**

</div>
