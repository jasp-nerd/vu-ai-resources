# Lecture 5 Study Guide — The AI Act and the Rest of the Legal Stack
**The Law of Artificial Intelligence (VU Amsterdam, 2026)**

This is the condensed version of the Lecture 5 guide. It keeps the exam-relevant context from the lecture slides, the European Parliament study by Graux et al., Schrepel & Potts on openness, the mock exam, and the seminar copyright material, but removes most of the long explanatory prose.

---

## 0. What to Study for the Exam

Lecture 5 is about one big idea:

> **AI systems are rarely governed by the AI Act alone. They sit inside a wider legal stack.**

For the exam, do not just memorise acronyms. You need to recognise **how laws interact**: do they replace each other, duplicate each other, conflict, or complement each other?

### Mock exam hooks

| Mock Q | Topic | Exam answer |
|---|---|---|
| **Q22** | Schrepel & Potts | Openness is a **spectrum**, but the AI Act uses a binary open/closed test. |
| **Q23** | Product Liability Directive | AI Act compliance helps rebut defectiveness; AI Act non-compliance can create a presumption of defectiveness. |
| **Q25** | Sandboxes | AI Act sandboxes do **not** suspend GDPR. A valid GDPR basis is still needed. |
| **Q27** | Graux et al. | Each EU digital law is targeted, but together they create complexity, overlap, and burden. |

### Best study method

Use this guide actively:

1. Read one section.
2. Close it.
3. Explain the section from memory in 60 seconds.
4. Check what you missed.

This is retrieval practice, and it works better than re-reading. For Lecture 5 especially, study by **comparison**: DPIA vs FRIA, DA vs DGA, DSA vs DMA, CRA vs CSA, AI Act vs PLD.

---

## 1. The Legal Stack: The Core Idea

The AI Act is one layer. Other laws may also apply, depending on the system:

| Legal layer | Main concern | Examples |
|---|---|---|
| **Product safety** | Is the product safe when placed on the market? | AI Act, CRA, MDR, IVDR, PLD |
| **Fundamental rights** | Are individual rights protected? | GDPR, ePrivacy |
| **Market-making** | Are platforms/data markets fair and accountable? | DSA, DMA, Data Act, DGA |
| **Intellectual property** | Who controls protected works? | CDSM copyright rules |

The lecture slides count the strongest AI Act interactions as:

- **Product safety:** 24 instruments / 58 mentions.
- **Fundamental rights:** 10 instruments / 58 mentions.
- **Market-making:** 5 instruments / 6 mentions.
- **Intellectual property:** 2 instruments / 4 mentions.

So the AI Act is closest to **product safety** and **fundamental rights**, but real AI systems also trigger platform, data, copyright, cybersecurity, and liability rules.

---

## 2. MediBot: The Worked Example

The lecture uses **MediBot**:

- A French hospital works with Meta.
- MediBot is a WhatsApp-based chatbot for patient triage.
- It uses voice and words from patients.
- It relies on a fine-tuned open-weights language model.
- It suggests a triage category to a nurse.
- The nurse makes the final call.

### What laws apply?

| MediBot layer | Possible law |
|---|---|
| Patient calls via WhatsApp | ePrivacy, DSA, possibly DMA |
| Voice capture/transmission | GDPR, cybersecurity rules |
| Patient health data | GDPR special-category data |
| Speech-to-text | GDPR, AI Act if part of AI system |
| Foundation model | AI Act GPAI rules, CDSM copyright for training data |
| Triage recommendation | AI Act high-risk rules, possibly MDR |
| Hospital as health provider | NIS2, GDPR, AI Act deployer duties |
| Patient harm | PLD, national courts, medical liability |

Key point: **human review by the nurse does not make the legal stack disappear.** It may help with human oversight, but the AI system still influences a sensitive health decision.

---

## 3. How to Classify Legal Interactions

The lecture gives four relationship types. Memorise these.

| Type | Meaning | Example |
|---|---|---|
| **Hierarchical** | One legal route takes precedence or absorbs the other. | AI Act conformity assessment integrated with MDR/IVDR. |
| **Conflicting** | Complying with one law makes another harder. | AI Act Article 10(5) bias correction vs GDPR Article 9 sensitive-data restriction. |
| **Parallel** | Both apply, causing duplicated burden. | AI Act FRIA and GDPR DPIA. |
| **Complementary** | Both point in the same direction. | AI Act and CRA on cybersecurity. |

Also ask two diagnostic questions:

1. **Do the Acts mention each other?** If yes, hierarchy may be partly settled.
2. **Could they have mentioned each other?** If they were drafted in parallel, silence may be a coordination failure.

Graux et al.'s central thesis:

> The EU digital laws are individually reasonable, but their combined application creates overlap, complexity, and institutional fragmentation.

That is the answer logic for mock Q27.

---

## 4. AI Act + GDPR

This is the most important overlap.

### Basic relationship

The AI Act is **without prejudice** to GDPR. That means:

> The AI Act does not override GDPR. Both apply.

If personal data is processed, GDPR still requires:

- a legal basis under Article 6;
- extra protection for special-category data under Article 9;
- transparency;
- security;
- data-subject rights;
- possibly a DPIA.

### DPIA vs FRIA

| Feature | GDPR DPIA | AI Act FRIA |
|---|---|---|
| Full name | Data Protection Impact Assessment | Fundamental Rights Impact Assessment |
| Legal basis | GDPR Article 35 | AI Act Article 27 |
| Actor | Controller | Deployer |
| Trigger | Processing likely to create high risk to rights/freedoms | Certain deployers of high-risk AI, especially public bodies/services |
| Focus | Data-protection risks | Broader fundamental-rights risks |
| Authority | Data Protection Authority | AI/market surveillance authorities |

Problem: both may be needed for the same AI deployment. They overlap but are not identical.

### Bias correction conflict

This is the cleanest conflict:

- **AI Act Article 10(5):** high-risk AI providers may process special-category data when strictly necessary to detect and correct bias.
- **GDPR Article 9:** processing special-category data is prohibited unless a strict derogation applies.

Special-category data includes health, race/ethnic origin, political opinions, religion, biometric data for identification, sex life, and sexual orientation.

Why this matters:

- To detect bias, you may need sensitive attributes.
- But GDPR restricts using those attributes.
- AI Act Recital 70 points to "substantial public interest" under GDPR Article 9(2)(g).
- But a recital is not a sufficient legal basis by itself; Union or national law must specify conditions.

### Sandboxes

AI Act sandboxes allow controlled testing. But:

> Sandboxes suspend or soften some AI Act burdens; they do **not** suspend GDPR or copyright law.

So a healthcare AI tested in a sandbox still needs a GDPR legal basis for patient data. This is mock Q25.

---

## 5. AI Act + Data Act / Data Governance Act

### Data Act (DA)

Core idea:

> The Data Act gives access and portability rights over certain data, especially from connected products and related services.

It aims to reduce data lock-in and make data circulate more fairly.

AI Act overlap:

- AI systems need data.
- Data Act may give users access to product/service data.
- AI Act requires risk management, data governance, documentation, logging, robustness, and sometimes conformity assessment.

High-yield distinction:

> **Data Act access is not AI Act quality.**

Getting access to data does not mean the data is representative, complete, accurate, or suitable under AI Act Article 10.

### Data Governance Act (DGA)

Core idea:

> The DGA creates trusted infrastructure for voluntary data sharing.

It covers:

- reuse of protected public-sector data;
- data intermediation services;
- data altruism;
- European data spaces;
- the European Data Innovation Board.

AI Act overlap:

- The DGA may help create trusted data-sharing channels for AI.
- It can support AI Act data-governance goals.
- But it does not replace AI Act obligations.

Short version:

- **DA:** access and portability rights.
- **DGA:** trusted sharing infrastructure.

---

## 6. AI Act + DSA / DMA

### Digital Services Act (DSA)

The DSA regulates online intermediaries and platforms, especially **VLOPs** and **VLOSEs**:

- VLOP = Very Large Online Platform.
- VLOSE = Very Large Online Search Engine.

DSA concerns:

- illegal content;
- content moderation;
- recommender-system transparency;
- advertising transparency;
- systemic platform risks;
- researcher access to platform data;
- intermediary liability.

AI Act overlap:

1. AI can generate/manipulate content that platforms host.
2. Platforms can use AI for moderation, recommendations, search, or summaries.

Key distinction:

> **AI Act:** generation/model/system risk.  
> **DSA:** hosting, distribution, moderation, and platform systemic risk.

Example: an AI-generated deepfake on a large platform may trigger AI Act transparency duties and DSA platform duties.

The AI Act does not abolish DSA hosting-liability protections. It complements them.

### Digital Markets Act (DMA)

The DMA targets **gatekeepers** controlling core platform services.

It is about:

- contestable markets;
- anti-self-preferencing;
- interoperability;
- data portability;
- limits on tying/bundling;
- limits on combining data across services without consent.

AI systems are not currently directly designated as core platform services, but AI can be part of:

- search engines;
- virtual assistants;
- cloud services;
- operating systems;
- browsers;
- recommender systems.

Key distinction:

> **DMA:** market power and gatekeepers.  
> **AI Act:** AI risk and model/system obligations.

So DMA can matter if a gatekeeper uses AI to lock users in, self-preference, or control access to AI infrastructure.

---

## 7. AI Act + Cybersecurity Laws

### Cybersecurity Act (CSA)

CSA is mainly about:

- ENISA;
- EU cybersecurity certification schemes;
- voluntary certification unless another law makes it mandatory.

AI Act link:

- AI Act Article 42(2) can recognise CSA certification for AI Act cybersecurity compliance.
- But CSA certification only helps with cybersecurity, not the whole AI Act.

### Cyber Resilience Act (CRA)

CRA is about mandatory cybersecurity for **products with digital elements**: software/hardware connected to a device or network.

It requires:

- cybersecurity-by-design;
- vulnerability handling;
- security updates;
- incident reporting;
- conformity assessment;
- CE marking.

AI Act link:

> CRA compliance may help satisfy AI Act Article 15 cybersecurity requirements, but it does not replace all AI Act duties.

This is mostly complementary.

### NIS2

NIS2 applies to **essential and important entities**, including sectors like:

- health;
- banking;
- energy;
- transport;
- drinking water;
- digital infrastructure;
- public administration;
- research.

It requires cybersecurity risk management and incident reporting.

AI Act overlap:

A hospital using MediBot may face:

- AI Act serious-incident reporting;
- NIS2 cybersecurity incident reporting;
- GDPR data-breach reporting.

Problem: different authorities, timelines, and reporting duties.

---

## 8. AI Act + Medical-Device Law

MediBot may trigger medical-device law if it has a medical purpose, such as diagnosis, triage, monitoring, or treatment support.

Relevant laws:

- **MDR:** Medical Devices Regulation.
- **IVDR:** In Vitro Diagnostic Medical Devices Regulation.

AI Act relationship:

- Some AI Act conformity-assessment duties can be integrated into MDR/IVDR processes.
- This is a **hierarchical** interaction.

Key point:

> The AI Act often plugs into existing EU product-safety machinery instead of creating a totally separate process.

---

## 9. AI Act + Copyright / CDSM

The key copyright law is the **CDSM Directive**.

### CDSM Article 4

Article 4 creates a text-and-data-mining exception:

> TDM of lawfully accessible works is allowed unless the rights-holder has reserved rights.

### CDSM Article 4(3)

Rights-holders can opt out. For online content, this reservation should be machine-readable.

### AI Act Article 53(1)(c)

GPAI providers must:

> put in place a policy to comply with EU copyright law, including respecting CDSM Article 4(3) opt-outs.

Also relevant:

- AI Act Article 53(1)(d): GPAI providers must publish a sufficiently detailed summary of training content.

High-yield distinction:

> **CDSM** creates the copyright/TDM rule.  
> **AI Act** requires GPAI providers to have a copyright compliance policy and training-content summary.

### Seminar angle: automated opt-out checking

A good ingestion-time compliance pipeline:

1. Identify source and URL/dataset origin.
2. Check lawful access.
3. Check machine-readable opt-out signals.
4. Log the result.
5. Exclude or restrict opted-out content.
6. Route ambiguous cases to human/legal review.
7. Timestamp and version decisions.
8. Keep audit evidence.

Limits of automation:

- A machine can detect metadata or opt-out signals.
- It cannot always determine copyright ownership, licence validity, or whether a legal exception applies.

---

## 10. Product Liability Directive (PLD)

This is mock Q23.

### Core idea

The AI Act is mostly **ex ante**: it imposes duties before/during market placement and deployment.

The PLD is **ex post**: it matters after harm occurs.

### AI Act + PLD relationship

Lecture slide rule:

- **AI Act compliance** helps show the product was not defective.
- **AI Act non-compliance** can trigger a presumption of defectiveness.
- The compliance record becomes key evidence.

Correct mock Q23 answer:

> AI Act compliance helps rebut a defectiveness claim, while breaching mandatory safety requirements can trigger a presumption of defectiveness.

Wrong answers:

- Compliance does **not** give total immunity.
- PLD can apply to software/AI; software is not simply excluded.
- The claimant does not always need to prove traditional fault.

Responsibility mismatch:

| AI Act | PLD |
|---|---|
| Provider has design-time duties. | Manufacturer/supplier may be liable for defective product. |
| Deployer has use/deployment duties. | Liability focuses on product defect and harm. |

In MediBot, possible responsible actors include Meta/model provider, the hospital/deployer, WhatsApp/platform provider, speech-to-text provider, and any medical-device manufacturer.

---

## 11. Schrepel & Potts: Openness Is a Spectrum

This is mock Q22.

### Problem with the AI Act

AI Act Article 53(2) gives reduced obligations for certain free and open-source GPAI models, unless they have systemic risk.

Schrepel & Potts argue:

> The AI Act treats openness as binary, but foundation-model openness is a spectrum.

Exam fact:

- Llama 3: **12/36**
- GPT-4: **10/36**
- Difference: only **2 points**
- Even the most open model tested scores only **20/36**

So "Llama is open, GPT-4 is closed" is too crude.

### Why openness matters

Open models support **innovation commons**:

- shared code;
- shared weights/data/documentation;
- forking;
- scrutiny;
- lower dependency on closed providers;
- dynamic competition.

But a model can be "open weights" and still legally/economically restrictive.

### Their 18-variable method

They score model licences across three clusters:

| Cluster | Meaning |
|---|---|
| **Knowledge problem** | Does the licence help pool knowledge? |
| **Implicit contracting problem** | Does it protect contributors/users against opportunism? |
| **Collective-action governance problem** | Does it govern the commons sustainably? |

Examples of variables:

- knowledge accessibility;
- documentation/support;
- transparency;
- contribution policies;
- exit rights;
- derivative works;
- access and use rights;
- participatory governance;
- non-competes;
- interoperability.

### Policy implications

Schrepel & Potts argue policymakers should:

- check whether existing laws make openness harder;
- avoid crude binary open/closed exemptions;
- support genuinely open models through funding, procurement, open data repositories, and interoperability;
- focus competition enforcement more on closed models and licence restrictions, not just company size.

Important nuance:

> Open models are not risk-free. They are just generally less able to create lock-in and foreclosure through control over the model.

---

## 12. Final Exam Cheat Sheet

Memorise these distinctions.

1. **Without prejudice = both laws still apply.**
   AI Act sandbox does not suspend GDPR.

2. **DPIA vs FRIA.**
   DPIA is GDPR/data protection; FRIA is AI Act/fundamental rights.

3. **AI Act Article 10(5) vs GDPR Article 9.**
   Bias correction may need sensitive data; GDPR restricts sensitive data.

4. **Data Act access is not AI Act quality.**
   Access to data does not mean representative or error-reduced datasets.

5. **DSA vs AI Act.**
   DSA = platform hosting/moderation/systemic platform risk. AI Act = AI system/model duties.

6. **DMA vs AI Act.**
   DMA = gatekeeper market power. AI Act = AI risk/capability.

7. **CRA vs CSA.**
   CRA = mandatory cybersecurity for digital products. CSA = certification framework.

8. **NIS2 adds reporting duties.**
   Essential/important entities may have AI Act, NIS2, and GDPR reporting obligations.

9. **CDSM vs AI Act.**
   CDSM defines copyright/TDM opt-outs. AI Act requires GPAI copyright policy.

10. **AI Act compliance is not immunity.**
    It helps in PLD analysis but does not eliminate liability.

11. **Non-compliance can matter in PLD.**
    It can trigger a presumption of defectiveness.

12. **Openness is a spectrum.**
    Llama 3 and GPT-4 differ by only 2/36 in Schrepel & Potts.

---

## 13. Practice Questions

### Q1

A healthcare AI system is tested in an AI Act sandbox using patient data. What is still required?

A) Nothing; the sandbox suspends all EU law.  
B) A valid GDPR basis, and likely an Article 9 derogation for health data.  
C) Only permission from the AI Office.  
D) Only a copyright policy.

**Answer:** B

### Q2

Which best describes the GDPR DPIA and AI Act FRIA?

A) They are identical.  
B) FRIA replaces DPIA.  
C) They may apply in parallel with different triggers and authorities.  
D) DPIA applies only to AI providers.

**Answer:** C

### Q3

What is the Schrepel & Potts critique of the AI Act's open-source approach?

A) Open source is always dangerous.  
B) Openness is a spectrum, but the AI Act uses a binary test.  
C) Closed models are always illegal.  
D) No AI model has any open features.

**Answer:** B

### Q4

Under Lecture 5's PLD logic, AI Act non-compliance with mandatory safety duties can:

A) create a presumption of defectiveness;  
B) create total immunity;  
C) suspend national courts;  
D) prove criminal intent.

**Answer:** A

### Q5

Which statement is best?

A) The Data Act guarantees AI Act dataset quality.  
B) The Data Act gives access/portability rights; AI Act Article 10 still governs dataset quality for high-risk AI.  
C) The AI Act repeals the Data Act.  
D) The Data Act only applies to personal data.

**Answer:** B

### Q6

Which interaction type best describes AI Act Article 10(5) and GDPR Article 9?

A) Hierarchical.  
B) Conflicting.  
C) Irrelevant.  
D) Identical.

**Answer:** B

---

## 14. One-Sentence Summary

**Lecture 5 teaches that AI compliance is legal-stack debugging: identify every applicable regime, classify the interaction as hierarchical/conflicting/parallel/complementary, and then work out the practical consequence for the actor.**
