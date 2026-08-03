# Lecture 3 Study Guide — The AI Act: The Capabilities Approach
**The Law of Artificial Intelligence (VU Amsterdam, 2026)**

This guide covers everything assigned for Lecture 3: **Articles 51–55** of the EU AI Act (the General-Purpose AI chapter), and **Moreira, Freitas & Novais, *The AI Act Meets General Purpose AI: The Good, The Bad and The Uncertain* (2023)**, plus the full lecture slide deck (*The Capabilities Approach*). It is written so you can follow it **cold** — you have not attended the lecture, not done the readings, and you do not have a law background. Every legal term gets unpacked the first time it appears, and where the law and the code-world meet, I translate in both directions.

It is written like someone talking you through the material out loud, not like a slide dump, because the exam wants you to *reason*, not just recognise a keyword. But it is also engineered around how memory actually works. So read the next short section before the content — it will change how you use the rest of the document and it is the single biggest lever on your grade.

---

## 0. How to actually study this so you pass

You were probably taught to study by re-reading and highlighting. Cognitive psychology has tested those methods for decades, and they are close to useless on their own. The big review is **Dunlosky et al. (2013), *Improving Students' Learning With Effective Learning Techniques***, which graded ten common methods. Highlighting, re-reading, and summarizing scored **low**. The methods that scored **high** are the two below; a few more are close behind.

**1. Retrieval practice (the testing effect).** Pulling an answer *out* of your head, book closed, is what builds durable memory. Reading the answer again does almost nothing by comparison (Roediger & Karpicke's classic work). Re-reading feels productive because the text gets easier each pass — but that fluency is an illusion that evaporates in the exam room, where the text is gone. So every section below ends with **↻ Recall** prompts. Cover the section, answer out loud or on paper, then check. If you do only one thing with this document, do that.

**2. Spaced practice.** The same hours spread across days beat one long cram (Cepeda et al.'s "spacing effect"). Three 40-minute sessions across three days beat one 2-hour panic the night before. The forgetting *between* sessions is the mechanism — each reload of a fading memory burns it in deeper. Start now, not on June 23.

Three more that matter specifically for *this* lecture and *this* exam:

- **Elaborative interrogation** — keep asking *why is the rule built this way?* The whole GPAI chapter is a series of design choices made under industry pressure, and the exam (especially the Part B rewrite questions) rewards understanding the reason, not the wording.
- **Concrete examples.** The exam loves "which models crossed the threshold?" and "classify this situation." You beat those with a stock of worked examples (GPT-4, Mistral Large, the open-source carve-out), not abstract definitions.
- **Dual coding.** Pair words with one picture. This whole lecture hangs off **one branching diagram**: *Is it a GPAI model? → Does it have systemic risk? → which obligations attach?* Draw that tree from memory once and you own the spine of the lecture.

### How to use this document
Read a section once for understanding → cover it and do the **↻ Recall** prompts → at the end, do the **practice MCQs in Section 15 closed-book** → build the **flashcards in Section 16** and run them across several days, interleaved with Lectures 1, 2, 4, 5. The summary parts get you to *understand*; the testing parts get you to *pass*. Most students skip the second and wonder why recognition in the room fails them.

### What Lecture 3 looks like on the exam (your baseline)

The exam is 100% multiple choice, one correct answer, three plausible near-misses. Part A tests lectures + readings; Part B gives you a clumsy provision and asks for the best rewrite. From the mock exam, **Lecture 3 maps directly onto Q17–Q21**, and the open-source theme spills into Q22. Here is the map, and crucially, *what skill each question is testing* — that tells you what to drill:

| Mock Q | Topic | What it tests | Skill type |
|--------|-------|---------------|------------|
| **Q17** | Definition of a GPAI model (Art 3(63)) | Recognise the real definition among look-alikes | **Definition recall** — exact elements matter |
| **Q18** | 10²⁵ FLOP → systemic-risk presumption (Art 51) | The one number in this lecture | **Precise-fact recall** |
| **Q19** | Which models crossed the threshold (Epoch AI, Apr 2024) | A named list | **Example recall** |
| **Q20** | Art 53(1) obligations (copyright policy + training summary) | Match obligation to article | **Obligation recall** |
| **Q21** | Open-source exemption limit (Art 53(2)) | The exception-to-the-exception | **Nuanced rule recall** |
| (Q22) | Schrepel & Potts on openness (binary open/closed test) | *Lecture 5 reading*, but the open-source theme connects here | Cross-over |

So your job for Lecture 3: nail the **definition elements**, memorise the **one number (10²⁵ FLOP)** and what it actually triggers, hold a **named list of threshold-crossing models**, learn the **four Article 53 duties** and the **open-source carve-out and its limit**, and understand the **two-category structure** (with/without systemic risk) that organises the entire chapter. Everything below is built around exactly those, plus the conceptual material from Moreira and the Lessig call-backs the lecturer threads through.

---

## 1. The big picture: why this lecture even exists

To understand Lecture 3 you have to remember where Lecture 2 left you. The AI Act's **risk-based approach** sorts AI by its **use**: the same technology is minimal-risk in one application and high-risk in another, and the obligations attach to the *use case*, not the tool. That works beautifully — right up until you hit a model that has **no single use**.

That is exactly what a **general-purpose AI model** (a large foundation model like GPT-4, Gemini, Claude, Llama, Mistral) is. You train it once on an enormous pile of data, and it can then write code, translate, summarise, draft contracts, generate images, give medical-sounding answers, and a thousand things its creators never specifically planned. Ask "what is its intended purpose, so I can put it in a risk box?" and the honest answer is "all of them and none of them." The use-based machine **jams**. (This is the cliffhanger Lecture 2 ended on, and the slide deck for Lecture 3 opens by naming it.)

So the Act needed a **second, parallel regime** bolted on next to the risk pyramid — one that regulates these models **by what they *can do* rather than by what they are *used for*.** That is the **capabilities approach** (hence the lecture title). Instead of asking *"what is this used for?"* it asks *"how capable / how powerful is this model?"* — and it measures power with two proxies: **generality** (can it do a wide range of distinct tasks competently?) and, for the most dangerous tier, **compute** (how many floating-point operations went into training it?).

Two framings the lecturer wants you to carry the whole way through:

1. **There is a definition half and a rules half.** The deck is literally split into two doors: **Definition** (what counts as a GPAI model, and when does it become "systemic-risk") and **Rules** (what its provider must then do). Keep those two halves separate in your head; the exam tests both.

2. **Lessig is back.** Slide-deck objective #3 says you must *"identify where (and how) Lessig's four constraints are being leveraged in the AI Act."* So the lecturer deliberately annotates each provision with the **Pathetic-Dot modalities** from Lecture 1 — **Law, Architecture (code), Market, Norms**. The headline example: the **10²⁵ FLOP threshold** is a piece of **Architecture** (a raw technical metric) being wired straight into **Law** (it flips your legal status). I give a dedicated synthesis of all the call-backs in Section 13 — it is a genuine exam target, not decoration.

> **↻ Recall:** In one sentence, *why* does the Lecture-2 use-based approach break down for foundation models? What two proxies does the capabilities approach use to measure a model's "power"? Which Lessig modality is the 10²⁵ FLOP threshold an example of?

---

## 2. A vocabulary primer for non-lawyers

You met some of these in Lecture 2; the ones below are the toolkit you specifically need for the GPAI chapter. Skim once, refer back. I am front-loading them so the substance reads smoothly.

**Regulation vs Directive.** An EU **Regulation** (capital R) applies directly and identically in all 27 member states the moment it takes effect — no national copying needed. A **Directive** sets a goal and leaves each country to write its own implementing law ("transposition"). The **AI Act is a Regulation**. The **CDSM Directive** (which the copyright obligation points to — more later) is a **Directive**. That difference is itself a trap-able fact.

**Article / Recital / Annex.** **Articles** are the numbered binding rules (Article 51, 53…). **Recitals** are the "Whereas…" paragraphs at the front — not directly binding, but courts use them to interpret the Articles. **Annexes** are binding lists at the back. For this lecture the key annexes are **Annex XI** (technical documentation a GPAI provider must keep), **Annex XII** (information to pass to downstream providers), and **Annex XIII** (the criteria for designating systemic risk — number of parameters, dataset size, compute, modalities, benchmarks, market reach, end-users).

**Provider / downstream provider / deployer.** The **provider** is whoever develops the model and puts it on the market under their name (OpenAI, Google, Mistral). A **downstream provider** is someone who takes that model and builds an AI *system* on top of it (a startup wrapping GPT-4 into a hiring tool). A **deployer** is whoever *uses* a system in their own activity (the HR department running that tool). Most GPAI obligations sit on the **upstream provider** of the model — and *whether that is fair* is the central debate in the Moreira reading.

**GPAI model vs GPAI system.** This distinction is doing real work in the Act. A **model** is the trained artefact — the weights, the thing that does the inference (GPT-4 the model). A **system** is a model wrapped in an interface, plumbing, and a use (ChatGPT the product). **Articles 51–55 regulate the *model*.** Article 3(63), the definition you must know, defines the **model**. When a question says "general-purpose AI *model*," it means the underlying trained object, not the consumer app.

**Self-supervision at scale.** A training method, named right in the definition. The model learns from raw unlabelled data (e.g. predict the next word) rather than from human-labelled examples — which is what lets you train on "a large amount of data." You do not need the maths; you need to recognise the phrase as part of the GPAI definition's description of *how* these models are typically built.

**FLOP (floating-point operation).** One arithmetic operation on a decimal number. **Training compute** is counted in total FLOP across the whole training run. It is the Act's chosen proxy for "how powerful / how much was invested in this model." The magic number is **10²⁵ FLOP** (that is a 1 followed by 25 zeros). Above it, a model is *presumed* to carry systemic risk. (CS note: this is a measure of *training* cost, not inference cost or parameter count — though parameter count is a *separate* Annex XIII criterion.)

**Systemic risk.** A term of art in the Act. It means a risk *specific to the high-impact capabilities of the most powerful models*, with potential **large-scale, Union-wide** effects on health, safety, fundamental rights, or society as a whole — think mass disinformation, large-scale cyber-offence, loss of control, dangerous CBRN (chemical/biological/radiological/nuclear) uplift. It is **not** the same as "high-risk" from Lecture 2. *High-risk* is about a dangerous **use**; *systemic risk* is about a dangerously **capable model**. Keep them in separate drawers — mixing them up is a designed trap.

**Ex officio.** Latin, "by virtue of one's office." When the Commission acts **ex officio**, it acts on its own initiative — nobody had to ask it. (You will see it in Article 52: the Commission can designate a model as systemic-risk ex officio, i.e. even if the company never notified it.)

**Delegated act / implementing act.** Powers the Act hands the **European Commission** to fill in or update technical detail later *without* reopening the whole law. A **delegated act** can amend non-essential elements (e.g. update the Annex XIII criteria, move the FLOP threshold). Practical upshot: the numbers and lists in this chapter are **not frozen** — the Commission can move them as the technology moves.

**Third country.** EU-speak for any country outside the EU. A "third-country provider" is a non-EU company (OpenAI in the US, say). Article 54 is about them.

**Authorised representative.** A person or entity *inside* the EU that a non-EU provider formally appoints (by **written mandate** — a signed legal authorisation) to be the EU-facing point of contact and compliance-holder. Think "legal proxy on EU soil."

**Code of practice / harmonised standard / presumption of conformity.** Because the detailed technical rules for GPAI did not exist yet, the Act lets providers show compliance by following a **code of practice** (Article 56 — an agreed industry/Commission playbook) *until* official **harmonised standards** are published. Following a published harmonised standard gives you a **presumption of conformity** — you are legally assumed compliant unless proven otherwise. If you follow neither, you must demonstrate "alternative adequate means." (Lessig note: codes of practice and standards are **Norms** doing regulatory work alongside Law.)

**Trade secret / IP (intellectual property).** Confidential commercially-valuable information (a model's training recipe, data sources). The Act repeatedly promises to protect trade secrets even while demanding documentation — a constant tension, because transparency duties and secrecy pull against each other.

**CDSM Directive & the Article 4(3) opt-out (text-and-data-mining).** The **Copyright in the Digital Single Market Directive (EU) 2019/790**. Its **Article 4** created a **text-and-data-mining (TDM) exception**: you may mine lawfully-accessible content (including copyrighted works) to train models — **unless** the rights-holder has **expressly reserved** that right (the "**opt-out**," Article 4(3)), typically in a machine-readable form (e.g. robots.txt-style signals). The AI Act's copyright obligation (Art 53(1)(c)) tells GPAI providers they must have a policy to *respect* those opt-outs. (This is the whole subject of Seminar 2.)

**VLOP / VLOSE / DSA.** From the **Digital Services Act (Regulation 2022/2065)**. A **VLOP** is a *Very Large Online Platform*; a **VLOSE** is a *Very Large Online Search Engine* (each ~45M+ EU users). They appear in the *enforcement* slide because, under the proposed Digital Omnibus, the AI Office takes exclusive enforcement over GPAI-based systems that are (or sit inside) a VLOP/VLOSE.

**"Whichever is higher."** EU fines are written as "€X million **or** Y% of total worldwide annual turnover, **whichever is higher**." For a giant firm the percentage bites; for a small one the flat figure bites. For GPAI providers the band is **€15 million or 3%** (Article 101).

> **↻ Recall (vocabulary):** What is the difference between a GPAI *model* and a GPAI *system*, and which one do Arts 51–55 regulate? What does **systemic risk** mean and how is it different from **high-risk**? What is the Article 4(3) CDSM **opt-out**? What is an **authorised representative** and who needs one?

---

## 3. The legislative backstory — how GPAI got into the Act at all

This section *is* the historical core of the Moreira reading, and the slides retell it visually (the screenshots of the 2021 Commission text, the 2023 Parliament text, and the photo of the Mistral / Aleph Alpha founders). It is examinable as "content of the lectures," and it is also the *why* behind every odd compromise in the chapter.

**April 2021 — the original Commission draft said *nothing* about GPAI.** The slide literally captions the 2021 proposal: **"NOTHING ON GENERAL PURPOSE AI."** The first draft was a pure use-based, risk-pyramid law. Foundation models were not even a named category. (They were not *excluded* either: Moreira notes that if a GPAI system was put to a high-risk *use*, it would have had to meet high-risk requirements anyway. But there was no dedicated regime.)

Then the technology lapped the legislation. **GPT-3, and then GPT-4 (March 2023)**, made it obvious that the most consequential AI was exactly the kind the draft ignored. The drafting then ping-ponged between the rotating **Council Presidencies** (Moreira's main timeline — note these are *proposals during negotiation*, not final law):

- **Slovenian Presidency (Nov 2021):** proposed to **exclude** the automatic application of the Act to GPAI; the Act would bite only if the model had an intended purpose within scope or was integrated into an in-scope system. (Rationale: providers cannot meet "high-risk" requirements when the model has no "intended purpose.")
- **French Presidency (May 2022):** swung the other way — **expand** scope to regulate GPAI explicitly, adapting high-risk requirements to GPAI *unless* the provider excluded all high-risk uses in the documentation.
- **Czech Presidency (Dec 2022 "General Approach"):** softened again — replaced *direct* application of high-risk requirements with the possibility of *future implementing acts*. **This December 2022 General Approach is the exact text Moreira analyses.** (Critical for reading the paper: it uses **old draft article numbers** — articles 4a–4c, 4b, 4c, 55a — which do **not** match the final Articles 51–55. More on that in Section 12.)

- **European Parliament (14 June 2023):** the slide captions the Parliament's adopted text **"introduces new provisions on general purpose AI."** Parliament added dedicated obligations for "foundation models," and the final trilogue produced the **standalone GPAI chapter** you now read as Articles 51–55 (plus 56 on codes of practice).

**The lobbying — "Market → Law" in the flesh.** Slide 9 shows **Arthur Mensch and Cédric O (Mistral AI)** and **Jonas Andrulis (Aleph Alpha)** — the founders of Europe's flagship GPAI companies — who lobbied hard during the final negotiations to *soften* the GPAI rules (especially for open-source and for not over-burdening foundation-model providers). This is not gossip; it is the lecture's live demonstration of **Lessig's Market modality reshaping the Law**: economic actors pushing back on the constraint, and the constraint bending. Several of the chapter's escape hatches (the opt-out in Art 52, the open-source exemption in Art 53) read the way they do partly because of this pressure.

The throughline: **the Act did not plan for GPAI; GPAI forced its way in late, under heavy industry pressure, which is why the chapter is full of thresholds, presumptions, opt-outs, and carve-outs rather than clean rules.**

> **↻ Recall:** What did the original April-2021 Commission draft say about GPAI? Which **draft** does Moreira analyse, and why does its article numbering not match Articles 51–55? Name the two European GPAI companies whose founders lobbied on the final rules, and say which Lessig modality that illustrates.

---

## 4. The definition — what counts as a GPAI model (Article 3(63))

This is **Q17 on the mock**, and it is a pure definition-recall question, so the exact elements matter. The slide walks the definition phrase by phrase and tags three things on it: an **example**, two pieces of **precision**, and an **exception**. Learn it in those chunks.

The definition (Article 3(63), final text, as shown on the slide):

> A **'general-purpose AI model'** means an AI model, **including where such an AI model is trained with a large amount of data using self-supervision at scale**, that **displays significant generality and is capable of competently performing a wide range of distinct tasks** regardless of the way the model is placed on the market, and that **can be integrated into a variety of downstream systems or applications**, **except AI models that are used for research, development or prototyping activities before they are placed on the market.**

Break it into the slide's chunks:

- **"general-purpose AI model" means an AI model** — the thing being defined; the slide marks this as the **example** anchor (the prototypical case is a large language model / foundation model).
- **"including where… trained with a large amount of data using self-supervision at scale"** — a *typical* manner of building one. Note the word **"including where"**: this is illustrative, not a strict requirement. The huge-data-self-supervision route is the usual one, but the definition does not *limit* GPAI to that recipe.
- **"displays significant generality and is capable of competently performing a wide range of distinct tasks"** — the slide marks this as **precision** #1, and it is the real heart of the test. Two ideas welded together: **generality** (breadth) **+ competence** (it can actually *do* the tasks, not just gesture at them) across **a wide range of distinct tasks**. This is the "capabilities" in "capabilities approach."
- **"regardless of the way the model is placed on the market"** — closes a loophole: how you ship it (API, download, embedded) does not change whether it is a GPAI model.
- **"can be integrated into a variety of downstream systems or applications"** — **precision** #2: the model is a base/component others build on. (Echoes the "foundation model" idea — a pre-product others fine-tune and wrap.)
- **"except AI models used for research, development or prototyping activities before they are placed on the market"** — the slide marks this as the **exception**. Models still in the lab, pre-market, are carved out. The duties bite once you actually **place it on the market**, not while you are still experimenting.

**Why this is examinable and where the traps are.** Mock Q17 gives four candidate definitions; three are wrong in instructive ways:
- *"Any AI system classified as high-risk under Annex III"* — wrong: that confuses the **GPAI** regime with the **high-risk** regime (Lecture 2). Different drawer.
- *"Any AI system deployed by a very large online platform"* — wrong: a VLOP fact is about *enforcement*, not the definition.
- *"A model trained exclusively on personal data"* — wrong: the definition says nothing about personal data (just like the Art 3(1) "AI system" definition in Lecture 2 was technology-neutral).
- **Correct:** the option about *significant generality + competently performing a wide range of distinct tasks + integration into many downstream systems, excluding R&D/prototyping before market.* That is the definition's spine.

**The single biggest confusion to kill now:** the GPAI **definition** (Art 3(63)) has **no compute number in it**. There is no "10²⁵ FLOP" in the definition. The FLOP threshold belongs to a *different* question — *systemic risk* (Article 51) — covered next. The slide's yellow "Back to Lessig" box on the definition slides is slightly loose when it says a model is "presumed general-purpose if trained using more than 10²⁵ FLOPs"; for exam precision, hold this line: **generality makes you a GPAI model; 10²⁵ FLOP makes a GPAI model *presumed systemic-risk*.** Two separate gates.

> **↻ Recall:** State the three load-bearing ideas in the GPAI definition (generality + competence + integration). What is the one **exception**? Does the definition mention compute or FLOP? (No — say where that number actually lives.)

---

## 5. The structural spine: two categories of GPAI

Before any rules, internalise the **branching tree** that organises the entire chapter. The red sticky-note on the slide spells it out: **there are two categories of GPAI model.**

```
Is it a GPAI model? (Art 3(63): significant generality + wide range of distinct tasks)
        │  yes
        ▼
Does it have SYSTEMIC RISK? (Art 51)
        ├── NO  → "plain" GPAI → obligations of Article 53 (+ Article 54 if third-country)
        │                         …with an OPEN-SOURCE carve-out (Art 53(2))
        └── YES → systemic-risk GPAI → Article 53 + 54 obligations
                                       PLUS the heavier Article 55 obligations
                                       …and the open-source carve-out NO LONGER helps
```

Everything in Sections 6–11 is just filling in that tree. If you can redraw it from memory and say what attaches at each branch, you have the lecture's architecture. The two "doors" from the title — **Definition** (am I a GPAI model? do I have systemic risk?) and **Rules** (Art 53 / 54 / 55) — are exactly the two halves of this tree.

> **↻ Recall:** Draw the tree from memory. What pushes a plain GPAI model up into the systemic-risk category? Which article carries the *extra* obligations for systemic-risk models, and does it *replace* or *add to* Article 53?

---

## 6. Article 51 — Classification: when is a GPAI model "systemic-risk"?

This is the gate between the two categories, and it contains **the one number you must know (Q18)**.

**Two ways in (Art 51(1)).** A GPAI model is classified as **systemic-risk** if **either**:
- **(a)** it has **high-impact capabilities**, evaluated using appropriate **technical tools, methodologies, indicators and benchmarks**; **or**
- **(b)** by a **decision of the Commission** — acting **ex officio** or **following a qualified alert from the scientific panel** — that it has capabilities or impact equivalent to (a), judged against the **Annex XIII** criteria.

(The **scientific panel** is an independent expert body that can raise a "qualified alert" flagging a model the Commission should look at. This is **Norms/expertise** feeding into **Law**.)

**The presumption — the examinable number (Art 51(2)).** A GPAI model is **presumed to have high-impact capabilities** (and therefore to be systemic-risk under 51(1)(a)) when the **cumulative compute used for its training, measured in FLOP, is greater than 10²⁵.** That is **Q18**: the trigger is **training compute > 10²⁵ FLOP**. The wrong options on the mock are designed to tempt you — "more than one billion users," "turnover over €35 million," "trained longer than six months." None of those is the trigger. **It is the compute.**

Two precision points that beat near-miss answers:
- It is a **presumption**, i.e. **rebuttable** — you can argue your way out of it (that is Article 52's opt-out, next section). It is not an automatic life sentence.
- It is **cumulative training compute**, not parameter count, not inference cost. (Parameter count is a *separate* Annex XIII factor.)

**Annex XIII — the criteria behind the Commission route (51(1)(b)).** When the Commission designates a model as systemic-risk *without* relying on the FLOP presumption, it weighs the Annex XIII factors (the slide lists them): **number of parameters; quality/size of the dataset (e.g. tokens); amount of compute; input/output modalities (text-to-text, text-to-image, multimodality); benchmarks and evaluations of capability (including autonomy, adaptability); whether it has high impact on the internal market — presumed once it is available to at least 10,000 registered business users; and number of registered end-users.** You do not need them word-perfect; you need to recognise that the Commission has a *multi-factor* discretionary route, with the FLOP presumption as the fast lane.

**Moving target (Art 51(3)).** The Commission may adopt **delegated acts** to amend the thresholds and supplement the benchmarks "in light of evolving technological developments, such as algorithmic improvements or increased hardware efficiency." Translation: **10²⁵ is not carved in stone** — it is meant to track the state of the art.

### 6.1 The Lessig call-back: Architecture wired into Law
This is the lecture's signature point and a likely exam idea. **Article 51 fuses Architecture + Law.** A purely **technical** metric — total training FLOP, a fact about the *code/architecture* — is plugged directly into the **legal** machine to flip your status and load you with obligations. In Lessig's terms, the regulator is using **a measurement of the architecture as the trigger for the law.** That is elegant (objective, hard to fake) but also fragile (next section).

### 6.2 The international angle and the "freezing / favouring small models" critique
The slides put the EU number next to the **US Executive Order (30 Oct 2023)**, which used a **different threshold: 10²⁶ FLOP** (and a lower **10²³** for models trained mostly on **biological sequence data**, because of bioweapon-uplift fears). Then the next slide **crosses the whole EO out** — signalling it is **no longer in force** (the 2023 Biden order was rescinded in 2025). Two lessons the lecturer is drawing:
1. **Thresholds are political and divergent** — the EU picked 10²⁵, the US picked 10²⁶, and the US then abandoned its number entirely. There is no settled international definition.
2. **A fixed number ages badly.** The **Epoch AI** charts make this vivid: in **April 2024** only a handful of models were above 10²⁵ (the slide highlights **Gemini Ultra, GPT-4, Mistral Large, and Inflection 2** — that named set is **Q19**). By **June 2025**, Epoch counted **over 33 models from 11 developers** above the line. By **June 2026**, the table shows a crowd well past it (Grok 4, GPT-4.5, Grok 3, GPT-5, Llama 4 Behemoth, Gemini 1.0 Ultra, Claude 3.7 Sonnet, and many more), and projections run steeply upward to 2030.

This is **exactly Schrepel's Lecture-1 warning** about law "favouring certain characteristics" of a technology: a fixed compute line nudges developers and, as compute gets cheaper, sweeps in more and more models until "systemic risk" stops being exceptional. A line meant to catch a rare few becomes a line that catches almost everyone — and then has to be moved by delegated act (51(3)) to stay meaningful. Hold this critique ready; it is prime "reflect on the weaknesses" material and connects three lectures at once.

> **↻ Recall:** Above what training-compute figure is a GPAI model *presumed* systemic-risk, and which article sets it? Name the four models the Apr-2024 Epoch slide flagged above the line (Q19). What threshold did the US EO use, and what happened to that EO? In Lessig terms, Article 51 fuses which two modalities?

---

## 7. Article 52 — Procedure: "how to get out of it"

If Article 51 is how you get *labelled* systemic-risk, **Article 52 is the procedure around the label** — and, pointedly, **how a company can try to escape it.** The slide organises it into four boxes; learn them by their tags.

**52(1) — DESIGNATION (the duty to notify, and the back-stop).** A provider whose model meets the 51(1)(a) condition (i.e. crosses the threshold / has high-impact capabilities) must **notify the Commission without delay, and in any event within two weeks** of meeting it — or of it becoming known that the model *will* meet it. If a provider *fails* to notify, the Commission can still **designate** the model as systemic-risk itself — **ex officio, or following a qualified alert** from the scientific panel. (The slide flags the awkward "(no sanction?)" — failing to self-report is caught by designation, but the deterrent there is soft.)

**52(2) — OPT-OUT (the rebuttal).** Here is the escape hatch. When notifying, the provider may present **"sufficiently substantiated arguments"** that, **exceptionally**, despite crossing the threshold, the model **does not present systemic risks "due to its specific characteristics."** In plain terms: *"yes, we're over 10²⁵ FLOP, but here's why our model is not actually systemically dangerous."* This is the rebuttable-presumption escape valve.

**52(3) — rejection.** If the Commission decides those arguments are **not sufficiently substantiated**, it rejects them and the model **is** treated as systemic-risk.

**52(4)–(5) — UPDATE / REASSESS.** The Commission can also designate ex officio under Annex XIII (52(4)) and can **amend Annex XIII by delegated act** (delegating power from Parliament/Council to the Commission to update the criteria). A provider already designated can ask the Commission to **reassess** (52(5)) — but the request must contain **"objective, detailed and new reasons that have arisen since the designation,"** and can be made **at the earliest six months after** the designation decision (and again six months after any decision to maintain it). So: escape is possible, but slow and evidence-heavy.

**52(6) — PUBLICATION.** The Commission **must publish and keep up to date a list** of GPAI models with systemic risk (while protecting IP / trade secrets). Public naming-and-listing is itself a regulatory tool.

### 7.1 The Lessig call-back: Market → Law
The slide's yellow box on Article 52 reads **"Market to Law: Opt-out (52.2) allows economic argumentation to avoid the 'systemic risk' label."** The point: the opt-out is a built-in channel for **market actors to argue their way out of a legal status** — exactly the dot pushing back on the constraint. It is the Mistral/Aleph-Alpha lobbying pressure, *crystallised into a procedure.* That is a clean, examinable instance of Lessig's framework operating inside the statute.

> **↻ Recall:** Within how long must a provider notify the Commission once it crosses the threshold? If it doesn't, what can the Commission do, and on what two bases? What exactly can a provider argue under the 52(2) **opt-out**? How soon, and on what kind of reasons, can a designated provider ask for **reassessment**? Which Lessig modality does the opt-out illustrate?

---

## 8. Article 53 — Obligations for *all* GPAI providers (the "without systemic risk" baseline)

Now the **Rules** door. Article 53 is the **baseline every GPAI provider** owes — systemic-risk or not (systemic-risk models owe these *plus* Article 55). The slide lists **four duties**; this is **Q20** territory, so learn the set.

**The four Article 53(1) obligations:**

1. **(a) Technical documentation of the model.** Draw up and keep up to date the model's technical documentation — including its **training and testing process and evaluation results** — containing at minimum the **Annex XI** elements, to provide on request to the **AI Office** and **national competent authorities**. (This is the *regulator-facing* file.)

2. **(b) Information for downstream providers.** Draw up, keep current, and make available information and documentation **to providers of AI systems who intend to integrate the model** — enough to let them **understand the model's capabilities and limitations** and meet their own obligations, containing at minimum the **Annex XII** elements. (This is the *downstream-facing* file. It is the legal basis for the value-chain cooperation that Moreira spends pages on.)

3. **(c) Copyright policy.** Put in place a **policy to comply with EU copyright law**, in particular to **identify and respect the rights reservations** (opt-outs) expressed under **Article 4(3) of the CDSM Directive (EU) 2019/790** — using state-of-the-art technologies to detect machine-readable opt-outs. (This is the obligation Seminar 2 is built around.)

4. **(d) Public training-content summary.** Draw up and **make publicly available a sufficiently detailed summary** of the content used to train the model, following a **template provided by the AI Office.**

A memory hook: **two files and two publics** — a *secret-ish* file for **regulators** (a), a file for **downstream builders** (b), then two **public** transparency duties: a **copyright** promise (c) and a **training-data summary** (d).

**Q20 precision.** The mock's correct answer pairs **the copyright policy (respecting Art 4(3) CDSM opt-outs)** with **publishing a detailed training-content summary.** The wrong options drag in machinery from *other* regimes — *CE marking and third-party conformity assessment* (that's the high-risk product route, Lecture 2), *consent from every data subject* (a GDPR-flavoured distractor), *a Fundamental Rights Impact Assessment under Art 27* (a high-risk deployer duty). GPAI providers do **not** CE-mark their models. Knowing which machinery does **not** apply is half the battle.

### 8.1 The open-source carve-out — and its limit (Q21)

This is the subtle, high-value rule, and it is **Q21**. Article **53(2)** says obligations **(a) and (b)** — the two documentation duties — **do not apply** to GPAI models released under a **free and open-source licence** that genuinely opens the model up: the licence must allow **access, use, modification and distribution**, *and* the **parameters (including weights), model-architecture information, and usage information must be publicly available.**

**But** — and this is the exam point — there is an **exception to the exception**: *"This exception shall not apply to general-purpose AI models with systemic risks."* So:

- **Plain open-source GPAI** → skips duties (a) and (b). **But still owes (c) copyright policy and (d) training summary — those apply *no matter what.***
- **Open-source GPAI *with systemic risk*** → the carve-out **vanishes**; it owes **everything**, including the heavy Article 55 duties.

Mock **Q21**'s correct answer is precisely *"the open-source exemption does not apply to GPAI models with systemic risk."* The wrong options ("removes all obligations including for systemic-risk models," "only for EU-developed models," "only below 10²⁵ FLOP regardless of risk") all misstate either the scope or the limit.

A cleaner way to hold the whole Article 53 picture (the slide draws this with three arrows):
- **(c) and (d)** → apply **no matter what** (even open-source, even systemic-risk).
- **(a) and (b)** → apply **UNLESS** the model is genuinely open-source…
- …**UNLESS** that open-source model has **systemic risk**, in which case (a), (b) — and Article 55 — all come back.

### 8.2 The Lessig call-back and the copyright debate
The slide tags Article 53 **"Law + Market + Architecture: open-source models are exempt unless they pose systemic risk."** The open-source carve-out is the **Law** accommodating an **economic/architectural** structure (open development norms and the market for open models), then pulling the accommodation back the moment **Architecture** (a very capable model) makes it too dangerous. And the live policy question the slide poses — and Seminar 2 debates — is squarely about the copyright duty: **"Should companies be allowed to train GPAI using all available data, including copyrighted material like newspapers?"** That tension between (c)'s opt-out-respect duty and the practical reality of web-scale scraping is exactly where law, market, and code collide.

> **↻ Recall:** List the four Article 53(1) duties (two files, two public duties). Which **two** does the open-source carve-out switch off? Which two apply **no matter what**? What is the exception-to-the-exception that brings everything back (Q21)? Name two pieces of machinery that do **not** apply to GPAI providers.

---

## 9. Article 54 — Authorised representatives for third-country providers

Short article, clean exam fact. Because most frontier GPAI providers are **non-EU** (US, etc.), the Act needs a way to reach them. **Article 54:** *before* placing a GPAI model on the **Union market**, a provider established in a **third country** must, **by written mandate, appoint an authorised representative established in the Union.**

The representative's **mandated tasks** (the slide lists them):
- **Verify** that the **Annex XI technical documentation** has been drawn up and that all the **Article 53** obligations (and Article 55 where relevant) have been met by the provider.
- **Keep a copy** of that technical documentation at the disposal of the AI Office and national authorities **for 10 years** after the model is placed on the market, plus the provider's contact details.
- **Provide** the AI Office, on reasoned request, with the information needed to demonstrate compliance.
- **Cooperate** with the AI Office and competent authorities on any action relating to the model.

The representative must **terminate the mandate** and tell the AI Office if it believes the provider is breaching its obligations — a built-in tripwire. And the **same open-source carve-out applies (54(6)): not required for genuinely open-source models — unless they carry systemic risk.**

**Lessig call-back:** the slide tags this **"Law + Market: formal legal delegation with implications for market access (non-EU providers); goal — accountability without stifling global trade."** The representative is the legal hook that lets the EU hold a foreign provider accountable as the price of EU-market access, while trying not to wall off the global market.

> **↻ Recall:** Who must appoint an authorised representative, and *when*? Name two of the representative's mandated tasks (hint: one involves a 10-year retention). Does the open-source carve-out apply here too, and what is its limit?

---

## 10. Article 55 — The heavy obligations for systemic-risk GPAI

This is the top of the tree: the **extra** duties that load onto a model **once it is classified systemic-risk**, **in addition to** Articles 53 (and 54 if it is a third-country provider). The slide lists **four**, arranged as a pipeline.

**The four Article 55(1) obligations:**

1. **(a) Model evaluation, including adversarial testing.** Perform model evaluation using **standardised protocols and state-of-the-art tools**, *including* conducting and **documenting adversarial testing** — i.e. deliberately **red-teaming** the model to find and then mitigate systemic risks. (CS translation: structured attempts to make the model do dangerous things, on the record.)
2. **(b) Assess and mitigate systemic risks at Union level.** Identify, assess, and **reduce** the systemic risks — including their *sources* — that could arise from developing, marketing, or using the model.
3. **(c) Report serious incidents.** Keep track of, document, and **report — without undue delay — serious incidents and possible corrective measures** to the **AI Office** (and, as appropriate, national authorities). (An ongoing, post-market duty — echoing the lifecycle logic of high-risk Article 9 from Lecture 2.)
4. **(d) Cybersecurity.** Ensure an **adequate level of cybersecurity** for **both the model and its physical infrastructure** — to stop theft, leaking of weights, or tampering.

A memory hook: **Evaluate → Mitigate → Report → Protect.** (Test it adversarially, reduce the risks, tell the AI Office when things go wrong, and lock it down.)

**Two routes to *show* compliance (Art 55(2)).** Because detailed standards did not exist when the Act passed, providers can demonstrate compliance by either: (1) **adhering to a code of practice (Article 56)** until a **harmonised standard** is published (and a published harmonised standard then grants a **presumption of conformity**); or (2) **self-assessment** — demonstrating "alternative adequate means" for the Commission to assess. The slide compresses this to **"Two options: rely on the code of conduct (Art 56), or self-assessment."**

**Lessig call-back:** the slide tags Article 55 **"Law + Architecture + Norms"** — a **legal** duty to do **technical** things (adversarial testing, cybersecurity), measured against **normative** expectations encoded in codes of practice and standards. All four modalities show up across the chapter; here three of them sit in a single article.

> **↻ Recall:** Article 55 applies *in addition to* which other article(s)? List the four duties (Evaluate / Mitigate / Report / Protect) and say what "adversarial testing" means in plain terms. What are the **two routes** a provider can use to show compliance while standards don't yet exist?

---

## 11. Enforcement, timing, and penalties

The slides close the "Rules" door with three operational facts. These are clean, examinable, and easy to mix up, so pin them down.

### 11.1 Enforcement — who polices GPAI (Art 75(1), via the Digital Omnibus)
The deck flags this as **updated to reflect the *Digital Omnibus on AI*, a provisional agreement of 6 May 2026, pending formal adoption** — so treat it as *as-presented-in-lecture* and recent, not yet final. The headline: a **new Article 75(1)** makes the **AI Office** (the EU-level body inside the Commission) **exclusively competent** to enforce against:
- **(a)** AI **systems built on GPAI models** where the **model and the system come from the same provider** (or providers within the same undertaking); and
- **(b)** AI systems that **are, or are embedded in, a VLOP or VLOSE** under the DSA.

It comes with **full market-surveillance powers (Arts 75a–75e):** information requests, **on-site inspections**, binding commitments, **fines (Art 99)**, and **periodic penalty payments up to 5% of average daily turnover.** The lesson (the slide's yellow box): enforcement of the **most integrated, most powerful GPAI players is centralised at the EU level (the AI Office), not left to national authorities.** In Lessig terms, **Law scaling up to the EU level** to match a technology that does not respect borders.

### 11.2 WHEN — the timeline (slide 38)
- **GPAI rules apply from 2 August 2025** for models placed on the EU market **on or after** that date.
- **Legacy models** already on the market **before 2 August 2025** get a grace period **until 2 August 2027** to comply.
- **AI Office enforcement powers apply from 2 August 2026.**

Memory hook: **2025 new models → 2026 enforcement → 2027 old models must be compliant.**

### 11.3 IF NOT — the penalty (slide 39)
For GPAI providers: a fine of **up to €15 million or 3% of worldwide annual turnover, whichever is higher**, for **intentional or negligent** infringement of the relevant provisions — set by **Article 101.**

**Do not confuse this with the Lecture-2 fines (Article 99).** Article 99 governs *AI systems*: **€35M/7%** for breaching the Article 5 prohibitions, **€15M/3%** for breaching high-risk and transparency obligations, **€7.5M/1%** for giving authorities misleading information. **Article 101** is the *GPAI-model-specific* fine, and its band is **€15M/3%.** If a question is about a **GPAI model provider**, the number is **Article 101 → €15M or 3%.**

> **↻ Recall:** Under the proposed Art 75(1), which two categories of system does the **AI Office** exclusively enforce? Give the three key dates (new models / enforcement / legacy). What is the **GPAI fine** and which article sets it — and how does it differ from the Article 99 bands?

---

## 12. The Moreira reading in depth — *The Good, The Bad and The Uncertain*

Moreira, Freitas & Novais (2023) is the lecture's mandatory paper. **Read it for its concepts, not its article numbers.** Crucial caveat first, then the ideas.

### 12.1 The big caveat: old draft, old numbers
Moreira analyses the **Czech "General Approach" of December 2022**, an *interim negotiating draft* — **not** the final law. So the paper talks about **articles 4a, 4b, 4c, 28b, 55a, 23a**, a "title on General Purpose AI Systems," and "implementing acts." **None of these numbers map to the final Articles 51–55.** When the paper says "article 4b obligations" or "the 55a(3) SME exemption," mentally translate to *"the draft's GPAI obligations"* and *"a draft SME carve-out."* The exam will test the paper's **arguments**; don't get tripped trying to align its numbering with the statute you read for Section 6–11.

A second framing note: the draft Moreira critiques tried to fit GPAI into the **risk-based** machine (presume a high-risk *use* unless the provider excludes it). The **final** Act instead built the **separate capabilities-based chapter** you now know. So in places Moreira is criticising a design the legislator later *replaced* — which is useful, because the paper essentially predicts the move toward a dedicated regime.

### 12.2 THE GOOD
- The draft had the **merit of regulating an expanding, high-leverage field** — models applied across many domains, at scale, in a fast-moving context. Bringing GPAI inside the tent at all is progress over the 2021 silence.
- It recognised the **value-chain reality**: a base model feeds countless downstream applications, so leaving everything to downstream users would be unworkable (and would simply hand the market to big tech).

### 12.3 THE BAD / THE UNCERTAIN — the arguments to actually know

**(a) The definition is unclear and "overly inclusive."** Moreira argues "generality" is a slippery concept. Is the definition **cumulative** (must a model satisfy *all* of: many purposes + many contexts + integration into other systems)? Unclear. They cite **Gutierrez et al.**'s four lenses for defining generality — **ability, domain, task, output** — and favour a **task-based + taxonomy** approach. Key nuance: **versatility is not AGI** — these models still "cannot generalise to completely different data types outside their training data," so this is evolution, not a singularity. And they warn the definition risks sweeping in narrow systems (e.g. a speech-recognition model) that merely *can* be reused — proposing that re-usability be a **necessary but not sufficient** condition.

**(b) The central question: a "general-risk" category, or just a species of high-risk?** This is the line from the abstract — *"It is essential to ascertain whether we are dealing with a general-risk category or a specific category of high-risk."* Tying GPAI to an **intended purpose** fails, because a GPAI model *has no single intended purpose*. So the draft's "presume high-risk use unless excluded" logic either (i) catches **everything** (any GPAI could be put to a high-risk use → over-regulation) or (ii) lets foundation models slip a **loophole** (regulate the use, ignore the base model). Moreira leans toward **Helberger & Diakopoulos**'s idea of a **dedicated "general-risk" category** — which is, in effect, what the final Act's separate GPAI chapter became.

**(c) Risk should track *foreseeable* purposes, not just *intended* ones.** Because real-world users determine actual uses, a provider can't honestly claim a narrow intended purpose. The fix is to assess **reasonably foreseeable** uses and misuses — but you can only foresee *some* risks, not all.

**(d) "Black swan" risks (Kolt).** A concept worth a flashcard: **highly consequential risks that are very hard to predict in advance but easy to explain in hindsight.** Moreira uses it to argue that exhaustively pre-listing every GPAI risk is impossible, so regulation must be **lifecycle-long and adaptive** rather than a one-off checklist. (Notice the resonance with Schrepel's "adaptive, not future-proof" from Lecture 1.)

**(e) The value chain and the allocation of responsibility — the paper's beating heart.** Who should carry the duties: the **upstream developer/provider** or the **downstream deployer/user**?
- The draft tended to push burdens **downstream**, onto entities (SMEs) with **fewer resources and less control**, while **exempting the well-resourced creators** — which **Kolt** flags as backwards.
- **Engler & Renda**'s principle: assign responsibility to the **"cheapest cost avoider"** — whichever actor is **best placed to identify and mitigate a risk** at the point it is most easily addressed. (Memorise that phrase.)
- **Hacker et al.** propose **four roles with differentiated duties**: **developers (providers), deployers, users (professional/non-professional), and recipients.** Universal duties (non-discrimination, data governance) sit with developers from the start; use-specific duties (risk management for a concrete use) sit with deployers.
- **Cooperation** is essential: upstream providers must pass **necessary information** to downstream providers (the final Act does this via **Art 53(1)(b) / Annex XII**), and that cooperation should be **continuous**, not a one-off at launch — while **protecting trade secrets / IP** (e.g. via NDAs), or providers won't share.

**(f) Release strategy and open source.** Moreira surveys the spectrum — closed vs open, **structured access**, **review boards**, **know-your-customer** API controls. The trade-off the final Act wrestles with: **open source aids innovation and third-party auditing**, **but makes risk control very hard and widens malicious-use and cyber-attack surface.** That is precisely why the final **Art 53(2) open-source carve-out exists *but evaporates for systemic-risk models*.** (This is the natural bridge to **Schrepel & Potts** in Lecture 5, who argue openness is a *spectrum* the Act wrongly treats as a *binary* — mock Q22.)

**(g) Exemptions, including for SMEs.** The draft let providers escape obligations by **excluding high-risk uses** in the documentation (old art 4c) — which Moreira says is hard to rely on **in good faith**, since a GPAI's myriad uses make high-risk use almost inevitable. And the draft **exempted SMEs** (old art 55a(3)); Moreira questions this: *if the whole point is to govern high-impact technology, why exempt SMEs that build GPAI?* — suggesting **government support** or a **simplified regime** instead of a blanket carve-out.

### 12.4 Moreira's conclusions (the examinable thesis)
Regulate the **entire lifecycle**; achieve a **balanced, clear allocation of responsibilities** (don't dump the burden on the weakest actors); require at least a **fundamental-rights assessment** considering vulnerable groups and misuse; keep rules **proportionate and tailored** to the sector and the stage of development; and build a **collaborative** environment among companies, regulators, and stakeholders. The closing optimism: **the AI Act may slow AI down, but it will not stop innovation** — the real question is *what kind of AI we want.*

> **↻ Recall (Moreira):** Why don't the paper's article numbers match Arts 51–55? State the central "general-risk vs high-risk" question in one sentence. What is the **"cheapest cost avoider"** principle and who proposed it? Define a **"black swan"** risk. Name **two** reasons Moreira gives for being cautious about the open-source treatment.

---

## 13. Lessig's four constraints, mapped across the GPAI chapter

Slide-deck objective #3 demands you can **spot where each of Lessig's four modalities is being leveraged.** The lecturer annotates this throughout; here it is consolidated into one table you should be able to reproduce in spirit. (Recall the four from Lecture 1: **Law**, **Architecture/code**, **Market**, **Norms**.)

| Provision | What it does | Lessig modalities at work |
|-----------|--------------|---------------------------|
| **Art 51** — 10²⁵ FLOP presumption | A raw **technical metric** flips your **legal status** | **Architecture + Law** — measuring the code to trigger the law |
| **Art 52(2)** — opt-out | Lets a firm **argue economically** out of the "systemic-risk" label | **Market → Law** — the dot reshaping the constraint |
| **Art 53** — baseline duties + open-source carve-out | Exempts genuinely open models, **unless** too capable | **Law + Market + Architecture** — accommodating open-development economics until capability makes it unsafe |
| **Art 53(1)(c)** — copyright policy | Legal duty to respect machine-readable **opt-outs** | **Law + Architecture** (respecting a *coded* rights signal) + **Norms** (industry copyright practice) |
| **Art 54** — authorised representative | EU-market **access** conditioned on a legal hook | **Law + Market** — accountability as the price of trade |
| **Art 55** — systemic-risk duties | Legal duty to do **technical** safety work, judged against **standards** | **Law + Architecture + Norms** |
| **Art 55(2)/56** — codes of practice & standards | Compliance shown via agreed **norms** until law/standards mature | **Norms** doing regulatory work alongside **Law** |
| **Art 75(1)** — AI Office enforcement | Centralises power at **EU level** for the biggest players | **Law scaling up** to match a borderless **architecture** |

The meta-point — and a great essay-style thing to be able to say — is that the GPAI chapter is a **deliberate *mix* of modalities** (Lessig's "what mix works best?"), with **technical metrics (architecture) repeatedly used to trigger legal consequences**, and with **market actors visibly bending the rules** (the opt-out, the open-source carve-out) — i.e. **Schrepel's adaptive, fighting-back dot**, written into a statute.

> **↻ Recall:** Give the modality pairing for Art 51, for the Art 52 opt-out, and for Art 55. Why is the FLOP threshold the lecturer's favourite example of "Architecture + Law"?

---

## 14. "Something is missing…" — the computational-law callback

The deck ends the substantive part with a horror-movie slide: **"Something is missing… Computational law (law using code)."** This loops straight back to Lecture 1. The capabilities approach **uses a technical metric** (FLOP) as a legal trigger — which is *clever*, but it is **not** "computational law" in the full Lecture-1 sense of **expressing and enforcing legal rules *as code* a machine can run.** The GPAI chapter is still **classical text-law** that merely *points at* a number. The lecturer's implied critique: for a regime aimed at the most code-heavy technology on earth, the Act makes surprisingly little use of code-as-regulation — the very tool (and its limits: not everything is written down, decision-trees force fuzzy questions into 0/1, explainability, correlation ≠ causation) that Lecture 1 laid out. Hold this as the bridge between Lecture 1's theory and Lecture 4's "strengths and weaknesses."

> **↻ Recall:** In what sense does the GPAI chapter use "code" — and in what sense does it *not* count as full computational law from Lecture 1?

---

## 15. Practice MCQs (closed-book, then check)

Do these a day or two after your first read, book closed. The first batch mirrors the real mock's Lecture-3 questions; the second batch covers the rest of the chapter the mock could draw on. Answers + reasoning follow each block — cover them until you've committed.

### Batch A — mirrors the mock (Q17–Q21 style)

**1.** Which best captures the Article 3(63) definition of a GPAI model?
A) Any AI system classified as high-risk under Annex III.
B) A model with significant generality that can competently perform a wide range of distinct tasks and be integrated into many downstream systems (excluding R&D/prototyping before market).
C) Any AI system deployed by a very large online platform.
D) A model trained exclusively on personal data.

**2.** A GPAI model is *presumed* to have high-impact capabilities (and thus systemic risk under Art 51) when:
A) It has more than one billion users.
B) Cumulative training compute exceeds 10²⁵ FLOP.
C) Its provider's turnover exceeds €35 million.
D) It has been trained for more than six months.

**3.** As of the April-2024 Epoch AI data shown in the lecture, which set of models had crossed the systemic-risk compute threshold?
A) Gemini Ultra, Mistral Large, GPT-4, and Inflection 2.
B) Only GPT-4.
C) No model had crossed it yet.
D) Llama 2 and BLOOM.

**4.** Article 53(1) requires GPAI providers (without systemic risk) to, among other things:
A) Affix a CE marking and undergo third-party conformity assessment.
B) Put in place an EU-copyright policy (respecting Art 4(3) CDSM opt-outs) and publish a sufficiently detailed summary of training content.
C) Obtain consent from every person whose data appears in the training corpus.
D) Conduct a Fundamental Rights Impact Assessment under Article 27.

**5.** A GPAI model gets reduced obligations under a free and open-source licence. The key limit on that exemption is:
A) It does not apply to GPAI models with systemic risk.
B) It removes all obligations, including for systemic-risk models.
C) It applies only to models developed inside the EU.
D) It applies only to models trained on fewer than 10²⁵ FLOP, regardless of risk.

> **Answers A:** 1-**B** (A/C/D confuse the GPAI definition with the high-risk regime, enforcement facts, or add a personal-data requirement that isn't there). 2-**B** (the trigger is *compute*; the others are pure distractors). 3-**A** (the four named on the slide). 4-**B** (CE marking, blanket consent, and the Art 27 FRIA all belong to *other* regimes — GPAI providers don't CE-mark). 5-**A** (the exception-to-the-exception: systemic-risk models can't use the open-source carve-out).

### Batch B — the rest of the chapter

**6.** Which is the correct relationship between Articles 53 and 55?
A) Article 55 replaces Article 53 for systemic-risk models.
B) Article 55 applies *in addition to* Articles 53 (and 54 if relevant) for systemic-risk models.
C) Article 55 applies only to open-source models.
D) Article 55 applies to all GPAI models regardless of risk.

**7.** Under Article 52, if a provider crosses the threshold but fails to notify the Commission, the Commission may:
A) Do nothing until the next reporting cycle.
B) Immediately impose the maximum €35M/7% fine without process.
C) Designate the model as systemic-risk *ex officio* or following a qualified alert from the scientific panel.
D) Revoke the model's CE marking.

**8.** The Article 52(2) "opt-out" allows a provider to:
A) Exit the EU market without penalty.
B) Argue, with substantiated reasons, that *exceptionally* its model does not present systemic risks due to its specific characteristics.
C) Delay all obligations for two years automatically.
D) Convert to an open-source licence to avoid all duties.

**9.** Which list correctly states the four Article 55 obligations for systemic-risk GPAI?
A) CE marking; FRIA; registration; insurance.
B) Model evaluation incl. adversarial testing; assess & mitigate systemic risks; report serious incidents; ensure cybersecurity.
C) Consent collection; data minimisation; DPO appointment; breach notification.
D) Pay a levy; publish source code; appoint a notified body; obtain a licence.

**10.** Under Article 54, a third-country GPAI provider must, before placing the model on the Union market:
A) Open an EU subsidiary.
B) Appoint, by written mandate, an authorised representative established in the Union.
C) Transfer its weights to the AI Office.
D) Obtain unanimous approval from all 27 member states.

**11.** The GPAI-specific fine for intentional or negligent infringement (Article 101) is:
A) €35 million or 7% of worldwide annual turnover.
B) €15 million or 3% of worldwide annual turnover, whichever is higher.
C) €750,000 in all cases.
D) No fine; only corrective orders.

**12.** In the lecture's Lessig framing, the 10²⁵ FLOP threshold is the clearest example of:
A) Norms regulating the market.
B) The market regulating law.
C) Architecture (a technical metric) being wired into Law (to trigger legal status).
D) Social norms enforced by the community.

**13.** Moreira's "cheapest cost avoider" idea (citing Engler & Renda) means responsibility should fall on:
A) Whoever has the deepest pockets.
B) Whichever actor is best placed to identify and mitigate the risk at the point it is most easily addressed.
C) The downstream user in every case.
D) The national regulator.

**14.** Why do the article numbers in Moreira (e.g. "article 4b," "55a") not match Articles 51–55?
A) The paper contains typos.
B) Moreira analyses the December-2022 *draft* (General Approach), which used different numbering than the final Act.
C) The final Act renumbered everything alphabetically.
D) Moreira analyses the US Executive Order, not the AI Act.

**15.** Under the proposed Article 75(1) (Digital Omnibus), the AI Office becomes *exclusively* competent to enforce against:
A) Every AI system sold in the EU.
B) Only systems developed by SMEs.
C) AI systems built on GPAI models where model and system share the same provider/undertaking, and systems that are/are embedded in a VLOP or VLOSE.
D) Only systems used by national governments.

> **Answers B:** 6-**B** (55 *adds to* 53; the killer word is "in addition"). 7-**C** (designation is the back-stop; note "no sanction?" — not an automatic max fine). 8-**B** (the rebuttal of the presumption). 9-**B** (Evaluate/Mitigate/Report/Protect; the others import GDPR or product-safety machinery). 10-**B** (the written-mandate representative; the others are invented). 11-**B** (Art 101 = €15M/3%; A is the Art 99 *prohibition* band, a deliberate trap). 12-**C** (Architecture + Law). 13-**B** (best-placed risk-mitigator). 14-**B** (old draft, old numbers). 15-**C** (same-undertaking GPAI systems + VLOP/VLOSE).

If you can score these closed-book **and explain why each wrong answer is wrong**, you have Lecture 3 cold. For any you fumble, don't re-read — redo them tomorrow, then again two days later. The forgetting between attempts is what moves them into long-term memory.

---

## 16. Flashcards (front → back)

Make these physical or load them into Anki; run them across several days, interleaved with the other lectures. Say the answer aloud before flipping.

- **Why does the use-based approach break for GPAI?** → A foundation model has no single intended purpose, so it can't be slotted into one risk box.
- **What does the "capabilities approach" measure instead of use?** → Capability/power — via **generality** (+ competence across distinct tasks) and, for the top tier, **compute (FLOP)**.
- **GPAI model definition, the three load-bearing ideas (Art 3(63))?** → Significant **generality** + **competently** performs a **wide range of distinct tasks** + **integrable** into many downstream systems.
- **The one exception in the GPAI definition?** → Models used only for **R&D / prototyping before being placed on the market**.
- **Does the GPAI definition contain a compute number?** → **No.** Generality defines a GPAI model; FLOP defines *systemic risk*.
- **The systemic-risk presumption number (Art 51(2))?** → Cumulative training compute **> 10²⁵ FLOP**.
- **Is that presumption rebuttable, and how?** → Yes — via the **Art 52(2) opt-out**.
- **Annex XIII factors (gist)?** → Parameters, dataset size, compute, modalities, benchmarks, market reach (≥10,000 business users), end-users.
- **US EO threshold, and its fate?** → **10²⁶ FLOP** (10²³ for biological-sequence data); the 2023 EO was later **rescinded**.
- **Models above 10²⁵ on the Apr-2024 Epoch slide (Q19)?** → **Gemini Ultra, GPT-4, Mistral Large, Inflection 2.**
- **Art 52 four tags?** → **Designation** (52.1, notify within 2 weeks / Commission can designate ex officio), **Opt-out** (52.2), **Update/Reassess** (52.5), **Publication** (52.6, public list).
- **Lessig tag for the Art 52 opt-out?** → **Market → Law** (economic argument to dodge the label).
- **Four Article 53(1) duties?** → (a) technical documentation (Annex XI, for regulators); (b) info for downstream providers (Annex XII); (c) **copyright policy** (respect Art 4(3) CDSM opt-outs); (d) **public training-content summary** (AI Office template).
- **Open-source carve-out — what it switches off?** → Only **(a) and (b)**, the two documentation duties.
- **Which Art 53 duties apply *no matter what*?** → **(c) copyright** and **(d) training summary** — even for open-source.
- **Exception-to-the-exception (Q21)?** → The open-source carve-out **does not apply to systemic-risk GPAI**.
- **Who needs an authorised representative (Art 54)?** → **Third-country** (non-EU) providers, by **written mandate**, **before** placing the model on the EU market; keep docs **10 years**.
- **Four Article 55 duties (systemic-risk)?** → **Evaluate** (incl. adversarial testing) → **Mitigate** systemic risks → **Report** serious incidents to the AI Office → **Protect** (cybersecurity of model + infrastructure).
- **Art 55 — relationship to 53/54?** → **In addition to** them, not instead of.
- **Two ways to show Art 55 compliance?** → (1) **Code of practice (Art 56)** until a harmonised standard exists; (2) **self-assessment** / alternative adequate means.
- **GPAI fine (Art 101)?** → **€15M or 3%** of worldwide turnover, whichever is higher (intentional/negligent).
- **Don't confuse with Art 99 bands?** → 99: €35M/7% (prohibitions), €15M/3% (high-risk), €7.5M/1% (misleading authorities). 101 = GPAI = €15M/3%.
- **Three GPAI dates?** → New models **2 Aug 2025**; AI Office enforcement **2 Aug 2026**; legacy models compliant by **2 Aug 2027**.
- **AI Office exclusive enforcement (Art 75(1))?** → Same-undertaking GPAI-based systems **+** VLOP/VLOSE systems.
- **Moreira's central question?** → Is GPAI a **general-risk category** or just a **species of high-risk**?
- **"Cheapest cost avoider" (Engler & Renda)?** → Put duties on whoever is **best placed to spot and mitigate** the risk most cheaply.
- **"Black swan" risk (Kolt)?** → Highly consequential, **hard to predict in advance, easy to explain in hindsight**.
- **Why don't Moreira's article numbers match?** → It analyses the **Dec-2022 draft** (different numbering).
- **The lecturer's "something is missing"?** → **Computational law** — the Act points at a number but isn't law-as-runnable-code.

---

## 17. One-page cheat sheet, glossary, and study plan

### The whole lecture in one box
- **Problem:** the use-based risk approach (Lecture 2) can't classify a model with **no single use** → the Act adds a **capabilities approach** for **GPAI models**.
- **Definition (Art 3(63)):** significant **generality** + competently performs a **wide range of distinct tasks** + **integrable** downstream; **except R&D/prototyping pre-market.** *(No compute number here.)*
- **Two categories:** plain GPAI vs **systemic-risk** GPAI. **Gate (Art 51):** presumed systemic-risk if training compute **> 10²⁵ FLOP** (rebuttable).
- **Procedure (Art 52):** notify within 2 weeks → can **opt out** with substantiated arguments → Commission can **designate** ex officio → public **list**.
- **Baseline duties — all GPAI (Art 53):** (a) tech docs (Annex XI) · (b) downstream info (Annex XII) · (c) **copyright policy** (Art 4(3) CDSM) · (d) **public training summary.** **Open-source** switches off (a)&(b) — **unless systemic-risk.**
- **Third-country (Art 54):** appoint an **authorised representative** in the EU (10-yr docs); same open-source limit.
- **Systemic-risk duties (Art 55, on top):** **Evaluate** (adversarial testing) · **Mitigate** · **Report** incidents · **Protect** (cybersecurity). Show compliance via **codes of practice (Art 56)** or **self-assessment.**
- **Enforce/When/Fine:** AI Office exclusive over same-undertaking GPAI systems + VLOP/VLOSE (Art 75(1)); dates **2025/2026/2027**; fine **€15M or 3%** (Art 101).
- **Lessig thread:** technical metrics (**Architecture**) trigger **Law**; market actors **bend** the rules (opt-out, open-source) — the **adaptive dot** in statute form.
- **Moreira:** definition too inclusive; **general-risk vs high-risk** question; fix the **value-chain** allocation (**cheapest cost avoider**); beware **black swans**; open source cuts both ways.

### Glossary (plain-language, for the non-lawyers)
- **GPAI model / system:** the trained artefact (weights) vs the product built around it. Arts 51–55 regulate the **model**.
- **Systemic risk:** risk from the **high-impact capabilities** of the most powerful models, with **Union-wide** potential effects. Not the same as **high-risk** (a dangerous *use*).
- **High-impact capabilities:** the capability level that makes a model systemic-risk; **presumed** above 10²⁵ FLOP.
- **FLOP:** floating-point operation; total training **compute** is the proxy for model power.
- **Self-supervision at scale:** training on huge unlabelled data (e.g. next-token prediction).
- **Presumption (rebuttable):** a legal default you can argue your way out of (here, via the Art 52 opt-out).
- **Ex officio:** the Commission acting on its own initiative.
- **Scientific panel:** independent experts who can raise a "qualified alert."
- **Delegated act:** Commission power to update technical details (thresholds, annex criteria) without reopening the law.
- **Provider / downstream provider / deployer:** model-maker / system-builder-on-top / end-user-organisation.
- **Authorised representative:** the EU-based legal proxy a non-EU provider must appoint.
- **Third country:** any non-EU country.
- **Annex XI / XII / XIII:** regulator-facing tech docs / downstream-facing info / systemic-risk designation criteria.
- **Code of practice (Art 56) / harmonised standard / presumption of conformity:** interim norm-based compliance route / official standard / legal assumption you comply if you follow the standard.
- **CDSM Directive / Art 4(3) opt-out / TDM:** EU copyright directive / rights-holders' reservation against text-and-data-mining / the mining of works to train models.
- **VLOP / VLOSE / DSA:** very large online platform / search engine / the Digital Services Act that defines them.
- **AI Office:** the EU-level body (in the Commission) that supervises GPAI and, under the Digital Omnibus, gains exclusive enforcement over the biggest players.
- **Article 99 vs Article 101 fines:** AI-*system* fines (35M/7%, 15M/3%, 7.5M/1%) vs the **GPAI-model** fine (**15M/3%**).
- **Black swan (Kolt):** consequential risk, unpredictable beforehand, obvious in hindsight.
- **Cheapest cost avoider (Engler & Renda):** assign duties to whoever can mitigate the risk most cheaply.

### Study plan (spaced, not crammed)
- **Today:** read Sections 1–11 once; do every **↻ Recall** out loud; sketch the **Section 5 tree** from memory.
- **Tomorrow:** read Section 12 (Moreira) + Section 13 (Lessig map); do **Batch A** MCQs closed-book; build the flashcards.
- **+2 days:** do **Batch B** MCQs closed-book; redo anything missed in Batch A; one full flashcard pass.
- **+4 days and then weekly to June 24:** one fast flashcard pass, **interleaved** with Lectures 1, 2, 4, 5 — mix GPAI cards with risk-pyramid cards with Lessig cards. It feels harder; that difficulty is the point.

That rhythm — **recall, space, interleave** — is what the research says actually moves a multiple-choice grade. The summary got you to understand it. The testing is what makes you remember it in the room on **June 24**.
