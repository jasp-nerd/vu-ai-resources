# Lecture 4 Study Guide — The AI Act: Strengths and Weaknesses
**The Law of Artificial Intelligence (VU Amsterdam, 2026)**

This guide covers everything assigned for Lecture 4: the lecture slide deck (*The AI Act: Strengths and Weaknesses* — **Exemptions** and **Regulatory Sandboxes**), the **LeCun & Schrepel podcast** (*AI Dynamics & Regulation*), **Schrepel, *Decoding the AI Act: Implications for Competition Law and Market Dynamics* (2025)**, and the short reading on **Schrepel, *Building a Digital Brain for Research* (2026)**. It is written so you can follow it **cold** — you have not attended the lecture, not done the readings, and you do not have a law background. Every legal term gets unpacked the first time it shows up, and where the law and the code-world collide I translate both directions.

It is written like someone talking you through the material out loud, not like a slide dump, because this exam wants you to *reason*, not just recognise a keyword. It is also engineered around how memory actually works, so read Section 0 before the content. It changes how you use the rest of the document and it is the single biggest lever on your grade.

Lecture 4 is the "critique" lecture. Lectures 2 and 3 taught you *what the AI Act says*. Lecture 4 asks *does it work, and at what cost?* That shift matters for the exam: the questions stop testing "what is the rule" and start testing "what is wrong with the rule, and would this rewrite fix it." Keep that lens on as you read.

---

## 0. How to actually study this so you pass

You were probably taught to study by re-reading and highlighting. Cognitive psychology has tested those methods for decades and they are close to useless on their own. The landmark review is **Dunlosky et al. (2013), *Improving Students' Learning With Effective Learning Techniques***, which graded ten common study methods. Highlighting, re-reading, and summarising scored **low**. The two that scored **high** are below, with three more close behind.

**1. Retrieval practice (the testing effect).** Pulling an answer *out* of your head, book closed, is what builds durable memory. Reading the answer again does almost nothing by comparison (Roediger & Karpicke's classic experiments). Re-reading feels productive because the page gets easier each pass, but that fluency is an illusion that evaporates in the exam room where the page is gone. So every section here ends with **↻ Recall** prompts. Cover the section, answer aloud or on paper, then check. If you do one thing with this document, do that.

**2. Spaced practice.** The same hours spread across days beat one long cram (Cepeda et al.'s spacing effect). Three 40-minute sessions across three days beat one 2-hour panic the night before. The forgetting *between* sessions is the mechanism: each reload of a fading memory burns it in deeper. Start now, not on June 23.

Three more that matter for *this* lecture specifically:

- **Elaborative interrogation** — keep asking *why is the rule built this way?* Lecture 4 is one long answer to that question. Every exemption exists for a reason (do not repeat GDPR, address Draghi). Every weakness has a cause (vague drafting, uneven burden, no adaptivity). The Part B rewrite questions reward understanding the *reason*, not the wording.
- **Compare-and-contrast.** This lecture is full of paired opposites: innovation vs fundamental rights, recital vs article, SME vs large firm, deterministic vs nondeterministic, open vs closed, sandbox-as-shelter vs sandbox-as-no-free-pass. Memory loves a contrast. Build the pairs.
- **Dual coding.** Pair words with one picture. The spine of this lecture is a single decision you can draw: *Is this AI in scope at all? → if yes, is the actor exempt or relieved? → if not, can they shelter in a sandbox?* Draw that funnel once from memory and you own the structure.

### How to use this document
Read a section once for understanding → cover it and do the **↻ Recall** prompts → at the end, do the **practice MCQs in Section 14 closed-book** → build the **flashcards in Section 15** and run them across several days, interleaved with Lectures 1, 2, 3, 5. The summary parts get you to *understand*; the testing parts get you to *pass*. Most students skip the second and then wonder why recognition fails them in the room.

### What Lecture 4 looks like on the exam (your baseline)

The exam is 100% multiple choice, one correct answer, three plausible near-misses. Part A (Q1–Q27) tests lectures + readings. Part B (Q28–Q30) hands you a clumsy provision and asks for the **best rewrite** — defined on the paper as *clearer than the original while staying proportional to the provision's objective and consistent with the rest of the Act*. Lecture 4 is unusual: its readings (especially the Schrepel *Decoding* paper) are the *engine room* behind questions scattered across the whole exam, and the whole **critical posture** of Lecture 4 is what Part B is testing. Here is the map:

| Mock Q | Topic | Where it comes from | Skill type |
|--------|-------|---------------------|------------|
| **Q13** | Art 10 data quality ("free of errors") — Schrepel's verdict | *Decoding* paper | Reading-comprehension + nuance |
| **Q14** | Art 11 SME simplified documentation — Schrepel's verdict | *Decoding* paper | Reading-comprehension + nuance |
| **Q18** | 10²⁵ FLOP systemic-risk threshold | L3 + *Decoding* paper | Precise-fact recall |
| **Q19** | Which models crossed 10²⁵ (Epoch AI, Apr 2024) | *Decoding* paper | Example recall |
| **Q22** | Schrepel & Potts — openness is a spectrum, not binary | L4 slides (+ L5 reading) | Concept recall |
| **Q25** | Sandbox "without prejudice to other Union law" → GDPR still applies | L4 slides (sandbox limits) | Applied reasoning |
| **Q26** | Market-surveillance authorities feed competition agencies | *Decoding* paper | Reading-comprehension |
| **Q28–30** | Rewrite Art 5 / Art 10 / Art 14 | The *Decoding* vagueness critique made practical | Judgement / drafting |

So your job for Lecture 4: understand the **innovation-vs-rights balancing act** the whole lecture is built around; hold the **exemptions** (which actor, which article, what relief); know the **sandbox machinery and its limits**; and absorb the **Schrepel critique** deeply enough to *rewrite* a bad provision and to recognise his verdicts on Articles 5, 10, 11, 14. Everything below is built around exactly those.

---

## 1. The big picture: the one tension this whole lecture is about

Every slide in Lecture 4 is a variation on a single question: **does the AI Act strike the right balance between protecting fundamental rights and fostering innovation?** That is literally slide 2's third learning objective, and it is the thread you should mentally tag onto everything.

Here is the setup. The AI Act has two faces that pull against each other.

- **Face one — protection.** The Act exists to protect health, safety, and fundamental rights from risky AI. That is the risk pyramid (Lecture 2) and the GPAI rules (Lecture 3). Protection means *obligations*: documentation, risk management, human oversight, transparency, fines.
- **Face two — innovation.** The Act also, repeatedly, promises to *support innovation*. The lecturer's headline stat: **"supporting innovation" appears as an objective 45 times** in the Act (slide 6). Europe is terrified of regulating itself out of the AI race.

Obligations protect rights but raise the cost of building AI. The Act's answer to that tension is a set of **release valves**: places where it *deliberately switches the obligations off or turns them down* to let innovation breathe. Lecture 4 is a tour of those valves and a hard look at whether they leak.

There are two families of valve, and they are the two halves of the lecture:

1. **Exemptions** — categories of AI or actors that get *out* of obligations entirely, or get a *lighter* version. (Slides: Exemptions 1, 2, 3.)
2. **Regulatory sandboxes** — a supervised space where you can *test* AI under relaxed conditions before the full rules bite. (Slides: Sandboxes.)

And running underneath both is the **critique**, supplied mostly by the **Schrepel *Decoding the AI Act* paper** and the **LeCun podcast**: that the Act, even with these valves, still distorts competition, still favours big incumbents, is full of vague language that will breed litigation, and cannot adapt itself when it gets things wrong.

Hold this shape in your head: **two faces (protect / innovate) → two valves (exemptions / sandboxes) → one running critique (it still leaks, it still favours the big, it cannot fix itself).**

> **↻ Recall:** What is the single tension the whole lecture is organised around? Name the two families of "release valve." How many times does the Act mention supporting innovation as an objective, and why did the lecturer put that number on a slide?

---

## 2. Vocabulary: the legal terms you need, unpacked for non-lawyers

Lecture 4 leans on terms from across the course plus a few new ones. Get these straight before the content, because the exam's wrong answers are built by swapping these around.

**Recital (a.k.a. "whereas" clause).** The numbered paragraphs at the *front* of an EU regulation, before the articles, each starting "Whereas...". They explain *why* the law was made and how to read it. The crucial exam point, made explicitly on slide 7: **recitals are not legally binding. They have only "interpretative" value.** A court uses them to resolve ambiguity in the binding articles, but you cannot be fined for breaching a recital. So when the Act says "support innovation" 45 times, much of that is in recitals — aspiration, not enforceable command. (CS analogy: recitals are the **comments** in the codebase; the articles are the **executable code**. Comments tell you the intent; only the code runs.)

**Article.** A numbered operative provision in the *body* of the regulation. **Binding.** This is the enforceable law. "Art 5", "Art 53(2)" etc. When the exam asks what the Act *requires*, it means an article.

**Exemption vs exclusion vs relief.** Loose words for related things; keep the gradient.
- **Exclusion from scope** — the Act *does not apply at all* (e.g. military AI, purely personal use). The strongest valve.
- **Exemption** — the Act applies but a *specific obligation is lifted* for a category (e.g. open-source GPAI is exempt from certain documentation duties).
- **Relief / simplified obligation** — the obligation still applies but in a *lighter* form (e.g. SMEs may file simplified technical documentation). The weakest valve.

The exam does not always police the difference, but understanding it stops you from over-reading an exemption as a total escape.

**SME (small and medium-sized enterprise).** EU-defined (Recommendation **2003/361/EC**): **fewer than 250 employees** AND **either** annual turnover **≤ €50 million** OR balance-sheet total **≤ €43 million**. Memorise the numbers; the slide puts them in a yellow box for a reason.

**SMC (small mid-cap).** A *new, larger* category introduced by the **Digital Omnibus** (see below): **fewer than 750 employees** AND **either** turnover **≤ €150 million** OR balance sheet **≤ €129 million**. Bigger than an SME, smaller than a true large firm. The Omnibus extends several SME reliefs up to SMCs.

**Microenterprise.** The smallest tier (broadly, <10 staff and ≤ €2m turnover/balance sheet under 2003/361/EC). Gets the gentlest treatment — e.g. a *simplified quality-management system* under Recital 146.

**Digital Omnibus on AI.** A 2026 package of amendments to the AI Act (and related laws) aimed at *simplification*. On the slides it is dated **provisional agreement 6 May 2026, pending formal adoption**, and it is the source of several "UPDATED · OMNIBUS" boxes: the SMC extension, the pushed-back sandbox deadline, the new sandbox tiers, the wider real-world-testing scope, and capped/proportionate fines (Art 99(6)/(6a)). **Treat it as examinable lecture content** — the lecturer flagged each change explicitly. (CS analogy: an omnibus is a "patch release" that bundles many small fixes to a law that already shipped.)

**Regulatory sandbox.** A controlled, supervised environment set up by a regulator where a company can **develop, train, and test** an AI system before market entry under the authority's eye, with some procedural relief (notably: good-faith participants are shielded from administrative fines). The term is borrowed from fintech regulation. Article 57 of the AI Act.

**Real-world testing.** Testing an AI system **outside** the sandbox, in actual operating conditions, under an approved plan with guardrails (informed consent, human oversight, time limits). Articles 60 and 60a. Distinct from a sandbox: a sandbox is a *place* a regulator runs; real-world testing is a *permission* to trial in the field.

**Market surveillance authority (MSA).** The national body each Member State must designate to police compliance and enforce the Act once products are on the market (Art 70). Holds strong investigatory powers over high-risk AI (access to documentation, datasets, even source code). Central to the Schrepel competition argument.

**Notifying authority / notified body.** *Notifying authority* — the national body that appoints and oversees *notified bodies* (Art 28). *Notified body* — an independent third party accredited to assess whether a high-risk AI system conforms to the rules (a "conformity assessment"). When you cannot self-assess, a notified body signs off.

**Conformity assessment / presumption of conformity / CE marking.** *Conformity assessment* — the check that a product meets the legal requirements. *Presumption of conformity* — if you followed an official **harmonised standard**, you are legally *assumed* compliant. *CE marking* — the stamp that says a product met EU requirements and may circulate in the single market.

**Technology neutrality.** The drafting ideal of writing rules that do not favour or punish any particular technology. The Commission says it aimed for this. Schrepel's key counter-argument: the Act's neutrality is *not neutral in practice* (Section 10).

**Deterministic vs nondeterministic AI.** *Deterministic* — same input always gives the same output (predictable, low randomness). *Nondeterministic* — the same input can give different outputs (more "creative," higher randomness, e.g. a sampling LLM). Schrepel uses this to argue the Act over-burdens the *safer*, predictable systems by treating them the same as the riskier unpredictable ones. (You know this cold as a CS student; the legal point is that the law ignores the distinction.)

**Computational antitrust / computational law.** *Computational antitrust* — using software (machine learning, NLP, network analysis) to automate and improve competition-law enforcement. *Computational law* — the broader idea of expressing/checking legal rules as runnable code. Both are Schrepel's own research themes, and both connect Lecture 4 back to Lecture 1's "code is law."

**TFEU / Article 101 / Article 102.** The **Treaty on the Functioning of the European Union**, the EU's foundational treaty. **Art 101** bans anti-competitive agreements (e.g. cartels, collusion). **Art 102** bans abuse of a dominant market position. You only need to recognise them when Schrepel says the AI Act's transparency duties might facilitate Art-101-type collusion.

**DMA / DSA / GDPR / PLD / CDSM.** The neighbouring EU digital laws. **DMA** (Digital Markets Act) — rules for "gatekeeper" platforms. **DSA** (Digital Services Act) — content/responsibility rules for online platforms, with *tiered* obligations by size. **GDPR** — data-protection law, the cautionary tale of this lecture. **PLD** (Product Liability Directive) — who pays when a product harms you. **CDSM** (Copyright in the Digital Single Market Directive 2019/790) — its Art 4(3) is the copyright opt-out GPAI providers must respect. You met these in Lecture 3 and will again in Lecture 5; here they are mostly *comparators* showing the AI Act could have been drafted better.

> **↻ Recall:** What is the difference between a recital and an article, and which one can you be fined for breaching? Give the SME thresholds and the new SMC thresholds. What is the difference between a sandbox and real-world testing? What does "technology neutrality" mean, and what is Schrepel's one-line objection to it?

---

## 3. The "45 times" move: innovation as an objective, and why recitals do not bind

The lecture opens its substantive part with a rhetorical setup you should be able to reproduce.

**Step 1 — the claim.** Slide 6: *"Supporting innovation is mentioned 45 times as an objective."* The slide then shows Recitals 1, 2, and 8, with the innovation-supporting phrases highlighted ("to support innovation," "boosting innovation," "measures in support of innovation," "with a particular focus on small and medium enterprises (SMEs), including startups"). The point: the Act *insists* it is pro-innovation.

**Step 2 — the deflation.** Slide 7 adds the killer caption: ***"These recitals are not legally binding. They only have an 'interpretative' value."*** So all that pro-innovation language is, in large part, *mood music*. It guides interpretation but imposes no enforceable duty to be innovation-friendly.

**Step 3 — the bridge.** Slide 8: ***"These statements translate with (among other things) exemptions."*** This is how the recitals' aspiration becomes something with teeth. If the Act genuinely wants to support innovation, the place it does so for real is in the **binding exemptions** — and that is the rest of the lecture.

Why this matters for the exam and for your reasoning: it sets up the **critical frame**. Watch how the lecturer keeps asking, for each exemption: *does this binding relief actually deliver the innovation the recitals promise, or does it leak / favour the wrong people / undermine the protection face?* That is the move Part B is testing — proportionality between a provision's stated objective and what it actually does.

> **↻ Recall:** What is the rhetorical three-step the lecture opens with (claim → deflation → bridge)? Why does it matter, legally, that the innovation language sits mostly in recitals? Where does the Act's pro-innovation promise become binding?

---

## 4. Exemptions (1): small companies — the SME/SMC reliefs and *why* they exist

This is the first family of exemptions and the one with the richest backstory. Two things to learn: **what the reliefs are**, and **why** the EU put them in (the "do not repeat GDPR" / "address Draghi" logic). The *why* is what the exam's reasoning questions and Part B reward.

### 4.1 What the reliefs actually are

The Act gives smaller firms three concrete softeners (slide 9), each tied to a provision:

1. **Simplified quality-management system** for *microenterprises* — Recital 146 says it is appropriate to let the smallest firms meet one of the costliest obligations (a quality-management system) in a *simplified manner*, and tasks the Commission with writing guidelines for how.
2. **Simplified technical documentation** for SMEs/startups — Article 11 lets SMEs (including start-ups) provide the Annex IV technical documentation in a *simplified form*. The Commission still has to design that form.
3. **"Avoid unnecessary burdens"** when assessing compliance — Article 34 tells *notified bodies* to avoid unnecessary burdens and to take account of a provider's size, especially for micro and small enterprises, while still keeping the required rigour.

**The honest caveat, straight off slide 10:** *"In practice? Who knows."* The Commission had not yet produced the promised simplified forms and guidelines. So the relief is real on paper but **uncertain in operation** — a recurring Lecture 4 theme: the Act *gestures* at help and defers the detail.

**Schrepel's sharper verdict (this is your Q14 answer).** In the *Decoding* paper he notes the Article 11 simplified-documentation allowance is **the only SME-specific exemption in the entire "Requirements for high-risk AI systems" section (Section 2)**. Because it is isolated, he judges it **likely insufficient to prevent the market distortion** that the high-risk burden causes (small firms cannot absorb the compliance cost the way large firms can). Memorise that framing: *only SME relief in Section 2 → likely insufficient.*

### 4.2 Why these reliefs exist — reason one: do not repeat GDPR

The lecturer's central justification (slides 12) is that the EU is trying **not to repeat the GDPR's mistake** of crushing small firms with uniform compliance costs. The slide stacks up empirical papers:

- **Profits.** Firms exposed to GDPR saw roughly an **8% drop in profits**, and the drop for small businesses was **almost twice** the average (Chen, Frey & Presidente, Oxford Martin WP 2022-1).
- **App ecosystem.** GDPR led to the **withdrawal of about a third** of available apps, and in the quarters after it took effect the **entry of new apps dropped by half** (Janßen, Kesler, Kummer & Waldfogel).
- **Market concentration.** GDPR **reinforced the concentration** of digital markets — it helped the big get bigger (Johnson, Shriver & Goldberg).
- **Data intensity.** GDPR made data storage about **20% more expensive**; in response EU firms cut data storage by **~26%** and data processing by **~15%** relative to comparable US firms, becoming less "data-intensive" (Demirer, Jiménez Hernández, Li & Peng, NBER 2024).

The mechanism is the one Schrepel spells out in the paper and LeCun repeats in the podcast: **a uniform rule has a regressive cost.** A €1m compliance bill is a rounding error for Google and an existential threat for a five-person start-up. So a rule that applies "to everyone equally" in fact **favours large incumbents** and entrenches concentration. (Compare the **DSA**, slide 13, which learned the lesson and scales obligations *up* with platform size: intermediary < hosting < online platform < very large online platform; and the **DMA**, which only bites designated "gatekeepers." The AI Act, Schrepel argues, fell back into the GDPR trap of treating all comers alike.)

### 4.3 Why these reliefs exist — reason two: address Draghi's concerns

The second justification (slides 16–17) is political. **Mario Draghi's 2024 report, *The Future of European Competitiveness***, framed Europe's productivity gap as an **"existential challenge."** Its diagnosis, highlighted on the slide: Europe does not lack ideas or patents; it fails to **translate innovation into commercialisation**, and scale-ups are **"hindered at every stage by inconsistent and restrictive regulations."** The AI Act's SME reliefs (and the Omnibus that widens them) are the EU answering Draghi: *we hear you, we will lighten the load on the firms that scale.*

So when the exam or a seminar asks *why* the Act has SME exemptions, you have two crisp reasons: **(1) avoid the GDPR regressive-cost / concentration effect; (2) answer Draghi's competitiveness alarm.**

### 4.4 The Omnibus upgrade: SMEs → SMCs

Slide 15 (and the sandbox slides later) flag the **Digital Omnibus** extension, *provisional agreement 6 May 2026, pending formal adoption*:

- Reliefs that were SME-only are **extended to small mid-caps (SMCs)**: fewer than **750 employees** + turnover **≤ €150m** or balance sheet **≤ €129m**.
- Extended reliefs include **simplified technical documentation** and **sandbox priority access**.
- **Capped / proportionate fines** for these firms under **Article 99(6)/(6a)** — the fine cannot be ruinous for a smaller player.

Translation: the EU decided the original SME line was drawn too low and pulled more mid-sized scale-ups under the protective umbrella. This is the Draghi logic in action.

### 4.5 The hard question the lecture leaves you with

Slide 18–19 poses it directly: **"Should small companies benefit from more exemptions (even if their AI systems may be used by millions of people)? Justify."** This is a *proportionality* question and a perfect Part-B-style provocation. The tension: small *firm* size does not mean small *impact*. A two-person start-up can ship an app used by ten million people. If you exempt by *company size*, you may be lightening the rules on a system with enormous reach — exactly where protection matters most. The defensible answers run both ways (foster the challengers vs protect the millions), and the exam wants you to *see* both sides. Bank a one-line argument for each direction.

> **↻ Recall:** Name the three SME/micro reliefs and their articles. What is Schrepel's verdict on the Article 11 relief, and why (your Q14 answer)? Give two empirical GDPR effects the lecturer cites. State the two *reasons* the SME exemptions exist. What did the Omnibus change, and what are the SMC thresholds?

---

## 5. Exemptions (2): the "mixed bag" — R&D, prototyping, military, personal use

The second exemption slide (20–24) is four *scope* exemptions that do not fit a neat theme — hence "mixed bag." For each: know **what** is exempt, **which article**, and **the critique** the lecturer attaches. (A drafting note first: the slides label both the scientific-R&D exemption and the military exemption "Article 2(6)." In the official Act the military/defence/national-security exclusion sits at **Article 2(3)**, and Schrepel's paper cites it as 2(3); scientific R&D is Article 2(6). If a question hinges on the exact sub-number for the military exclusion, **2(3)** is the official answer. Learn the *substance* primarily and keep that flag in mind.)

**1. Scientific research and development — Article 2(6).** AI systems and models developed or used **exclusively** for scientific research and development are **excluded from the Act entirely**. Rationale: do not load compliance onto pure research; let academic and technical innovation happen at the early stage unburdened.

**2. Pre-market development and prototyping — Article 3(63) (and Art 2(8)).** A GPAI model developed **solely** for research, development, and prototyping, *before* it is placed on the market or put into service, is exempt from the related obligations. Rationale: let teams experiment and iterate before commercial deployment. (The GPAI *definition* in Art 3(63) carves out exactly these pre-market R&D models, which is why the slide cites it.)

**3. Military, defence, and national security — Article 2(3)** (slide says 2(6)). AI systems developed or used **exclusively** for military, defence, or national-security purposes fall **outside the scope** of the Act altogether — regardless of who develops them (public or private).

**4. Personal, non-professional use — Article 2(10).** The Act does **not** apply to obligations of *deployers* who are **natural persons** using an AI system in the course of a **purely personal, non-professional** activity. Rationale: the Act regulates the market and professional use, not your private tinkering at home.

### The critiques the lecturer stacks on this slide

The "mixed bag" slides are mostly there to *poke holes*. Learn these as paired problem-statements, because they are exactly the kind of thing Part B and the reflection questions chase:

- **The "exclusively / solely / purely" problem.** Every one of these exemptions is gated by an absolute word — *exclusively* research, *solely* prototyping, *purely* personal. Real projects are rarely pure. **What about public-private partnerships or dual-use projects?** A system built "for research" that quietly has a commercial track exploits the word "research" to **delay regulatory scrutiny** (slide 21). The exemption is only as strong as the boundary of "exclusively," and that boundary is soft.
- **When does development become "placed on the market"?** (Slide 22.) The R&D and prototyping exemptions all end at the moment a system is "placed on the market," but the Act never gives a crisp test for that moment. A company can sit in the exempt "still developing" zone for a long time. Vague trigger = exploitable gap.
- **The military hypocrisy charge.** (Slide 23.) The lecturer's provocation: *"So... it's not okay to have deep fakes of politics, but it's fine to develop AI weapons?!"* The Act bans relatively low-stakes manipulative uses while **completely exempting** military AI — the highest-stakes use imaginable. The EU's stated commitment to **"human-centric AI"** sits awkwardly next to an **opaque, total carve-out for powerful state actors**. (This is reflection-question 2 on slide 45: *should military AI be completely exempt? Why or why not?*)
- **User innovation is now real.** (Slide 24.) We are in an age where **individuals can build and deploy powerful AI from home** (open-source LLMs). The personal-use exemption made more sense when "personal use" meant a spreadsheet macro. Now a natural person at a laptop can fine-tune and release a capable model — "**user innovation**" — which strains the line between "purely personal" and "market actor."

The throughline of slide group 2: **the exemptions are defined by absolute words and fuzzy triggers, which creates loopholes** — research-washing, never-quite-on-the-market, military opacity, hobbyists shipping real models.

> **↻ Recall:** List the four "mixed bag" exemptions with their articles and the absolute word that gates each. What is the official article for the military exclusion? Give two distinct critiques the lecturer attaches to this slide. State the "human-centric AI" objection to the military carve-out in one sentence.

---

## 6. Exemptions (3): open-source — the carve-out, what qualifies, and the spectrum problem

The third exemption is the one with the most conceptual depth and the clearest tie to the readings (and to Lecture 3). Three things to nail: **the exemption and its limits**, **the Act's definition of open source**, and **the spectrum critique** (your Q22).

### 6.1 The exemption and its exceptions-to-the-exception

Recall from Lecture 3 the GPAI obligations: **Article 53** (technical documentation, downstream info, copyright policy, training summary) for providers, and **Article 54** (appoint an EU authorised representative) for third-country providers. The open-source carve-out (slides 25–27) switches *some* of these off:

- A GPAI model **released under a free and open-source licence** is **exempt from the documentation duties** (Art 53(1)(a) and (b), and the Art 54 representative duty) — *unless* the model has **systemic risk**, in which case the relief does **not** apply. (Same structure you learned in L3: open source relieves the two documentation duties; the copyright policy and training-data summary still apply to everyone; systemic-risk models get no relief at all.)
- On top of that, a **scope-level** exemption: the Act does **not apply** to AI systems released under free and open-source licences **unless** they are placed on the market or put into service **as high-risk systems, or as systems falling under Article 5 or Article 50** (slide 26 quotes this; the official location is **Article 2(12)**, the slide labels it 2(15)). 
- **Article 50** is the catch that closes the loophole (slide 27): transparency obligations still apply to AI that **interacts directly with people**, **generates synthetic content**, does **emotion recognition / biometric categorisation**, or creates **deepfakes / public-interest AI-generated text** — open source or not.

So the open-source exemption is real but **fenced on three sides**: no relief for systemic-risk GPAI, no relief if deployed as high-risk, no relief from Article 50 transparency. (CS framing: open source gets you out of the *paperwork*, not out of the *dangerous-use* rules.)

The *reason* for the open-source exemption, threaded through the readings: open source **fosters competitive dynamics** — it spreads transparency, lets anyone fork and improve, and stops a single firm controlling the platform. Schrepel calls it a "positive development." LeCun (Section 9) makes the same case at length. The EU wanted to protect that.

### 6.2 What actually qualifies as "open source"? (Art 53(2) definition)

Slide 28–29 poses the obvious follow-up — *what counts as open source, then?* — and gives the Act's answer (Article 53(2)). A free and open-source licence is one that **allows access, use, modification, and distribution of the model**, and under which the model's **parameters (including the weights), the information on the model architecture, and the information on model usage are made publicly available.**

Read it carefully: the test is essentially **(licence permits the four freedoms) + (weights + architecture + usage info are public).** It is a **purely technical, binary** test — a model either ticks these boxes or it does not.

### 6.3 The spectrum critique — Schrepel & Potts (this is Q22)

Slides 30–31 deliver the punchline and the reading: **openness is a *spectrum*, not a binary.** The Act draws a hard line (open / not open), but real models sit on a continuum.

This is the core of **Schrepel & Potts, *Measuring the Openness of AI Foundation Models* (2025)** (a Lecture 5 reading that the lecturer previews here). They build a scoring framework — **0 to 36 points** across many dimensions of openness (knowledge accessibility, documentation, transparency, contribution policies, credit/revenue sharing, exit rights, dispute resolution, non-compete clauses, interoperability, and more). The killer datapoint, straight onto the mock exam (**Q22**): on their scale, **Llama 3 and GPT-4 differ by only 2 of 36 points**, yet the Act's binary test would treat one as "open" (relief) and the other as "closed" (full obligations).

The consequences Schrepel draws (also in the *Decoding* paper):

- **Misclassification both ways.** Models that are **not genuinely open** can tick the technical boxes and grab the exemption; **genuinely open** models can fall just outside it. The binary rewards box-ticking, not real openness.
- **What the binary ignores.** It captures weights/architecture/usage but **ignores** contribution policy, credit and revenue sharing, exit rights, accessible dispute resolution between contributors — the *governance* dimensions of openness.
- **Internal inconsistency.** The AI Act's open-source definition is **inconsistent with** the definitions in the **revised Product Liability Directive** and the **Cyber Resilience Regulation**. Three EU laws, three different ideas of "open source."

So the open-source exemption is, in Schrepel's verdict, **good in spirit (protects a pro-competitive practice) but badly built (a binary test for a spectrum concept, gameable and internally inconsistent).** That two-part verdict — *right goal, wrong instrument* — is the template for almost every critique in this lecture.

> **↻ Recall:** Which two Article 53 duties does the open-source carve-out switch off, and what are the *three* situations where it does **not** apply? State the Act's Art 53(2) definition of open source in your own words. What is the Schrepel & Potts critique, and what is the Llama-3-vs-GPT-4 datapoint (Q22)? Name the "right goal, wrong instrument" verdict in one line.

---

## 7. Regulatory sandboxes — the machinery (Articles 57, 58, 60/60a)

Now the second family of release valve. A sandbox is the Act's flagship *innovation* tool, so the lecturer spends real time on what it is, who runs it, how it works, and (Section 8) whether it delivers. Several Omnibus updates land here, all examinable.

### 7.1 The objective — Article 57

A sandbox is **a controlled space to develop, train, and test AI before market entry**, built for three things (slide 38): **innovation**, **legal certainty** (you find out what compliance looks like *before* you ship), and **evidence-based regulatory learning** (the regulator learns from watching real systems). 

Key facts:
- **Who must run them:** **every Member State must establish at least one** national sandbox. Regional, local, and joint cross-border sandboxes are also allowed.
- **Priority access:** **free**, with **priority for SMEs, start-ups, and now SMCs** (Omnibus). Comes with reduced conformity-assessment fees plus AI Office templates and guidance.
- **Deadline (Omnibus change):** originally operational by **2 August 2026**, now pushed back **12 months to 2 August 2027**. (Remember the date change — the lecturer struck through the old date on the slide.)

### 7.2 Who can run one — three tiers (Omnibus-expanded, Art 57(3a)–(3b))

Slide 39 — there are now **three tiers** of sandbox, two of them new from the Omnibus:

1. **National** — run by **Member States**, at least one each, operational by 2 Aug 2027; joint/regional/local allowed. (The original tier.)
2. **Union-level — the AI Office (NEW).** An EU-level sandbox for systems under the AI Office's own competence (Art 75(1): GPAI-based systems and systems that are/sit inside a **VLOP/VLOSE**). Priority for SMEs, start-ups, SMCs.
3. **EU institutions — the EDPS (NEW).** A sandbox for **Union institutions, bodies, offices, and agencies**, supervised by the **European Data Protection Supervisor (EDPS)**.

Why this matters: the new **Union-level** sandbox is the Act's first attempt to fix the **harmonisation gap** (see Section 8) — a single EU-level box instead of 27 different national ones.

### 7.3 How it works — Article 58, application to exit report

Slide 40 — the four-step lifecycle. Learn it as a pipeline:

1. **Apply.** Eligibility and selection criteria set by the competent authority. Free, priority access for SMEs and SMCs.
2. **Agree a plan.** A **sandbox plan** is agreed between the provider and the authority. **Data-protection authorities join** where personal data is involved (this is the hook for the GDPR point in Section 8).
3. **Test.** Supervised testing in a controlled space. **Good-faith participants are shielded from administrative fines** — the single most attractive feature.
4. **Exit report.** An exit report feeds the conformity assessment and **smooths market entry**. Cross-border cooperation encouraged.
- **Omnibus update:** the Commission's implementing acts now also cover the **governance** of sandboxes (Art 58).

The shield-from-fines and the exit-report-smooths-entry are the two selling points; the supervised-plan-agreed-with-the-authority is the cost (Schrepel will say this cost deters fast-moving start-ups — Section 10).

### 7.4 Real-world testing — Articles 60 & 60a (testing *outside* the sandbox)

Slide 41 — distinct from the sandbox: this is permission to trial an AI system in **actual operating conditions** in the field, under guardrails.

**The guardrails:**
- An **approved real-world testing plan**, agreed with the authority.
- **Informed consent**, **human oversight**, and **safety guarantees**.
- **Maximum 6 months, extendable once by 6 months** (so 12 months max).
- **Providers stay fully liable**; serious incidents must be reported.
- **Consent can be withdrawn at any time, without consequences** for the participant.

**Wider scope (Omnibus):** *before*, real-world testing covered **Annex III high-risk systems only**. *Now*, it also covers **Annex I, Section A** high-risk systems (Art 60) and adds a new **Article 60a** regime for **Annex I, Section B** products (sectoral product-safety rules), under Member-State frameworks notified to the Commission. **Takeaway (the lecturer's word):** a **longer testing runway for industrial AI**, part of the Omnibus's simplification drive.

> **↻ Recall:** State the three goals of a sandbox (Art 57). Who must run a national sandbox, and by when (post-Omnibus)? Name the three *tiers* of sandbox and which two are new. Walk the four steps of Art 58. What is the single most attractive feature for a participant? Give three guardrails of real-world testing and the maximum duration.

---

## 8. Sandboxes — the limits and whether they actually deliver

Slides 42–43 are the critique, and they are exam gold because they convert into both Part A factual questions (Q25) and Part B reasoning. The lecturer splits the limits into two groups.

### 8.1 "A sandbox is not a free pass" (slide 42) — three structural limits

1. **NO SHIELD from the substantive law.** A sandbox **does not suspend the law.** **GDPR, fundamental-rights, and product-safety obligations still apply in full.** This is the source of **mock exam Q25**: a company testing a healthcare AI in a sandbox **still needs a valid GDPR legal basis to process patient data**, because the sandbox operates *"without prejudice to other Union law."* The sandbox relaxes *AI-Act administrative fines* for good-faith participants; it does **not** hand you a GDPR exemption or a blanket legal basis. Lock this in: **sandbox ≠ GDPR holiday.**
2. **STILL LIABLE.** Providers remain **fully liable** under Union and national law for any **harm caused during testing**. The "no fines" shield is narrow (administrative fines for *good-faith AI-Act* participants); civil and other liability is untouched.
3. **NOT HARMONISED.** Sandboxes are run by **national authorities**, so **capacity, standards, and practice differ across Member States.** A generous, expert sandbox in one country; an under-resourced one next door. (The Omnibus's new **EU-level AI Office sandbox** is the lecturer's "partial fix" for exactly this gap.)

The slide's caption ties it together: *"But no administrative fines for good-faith participants"* is the one real shelter; everything else still bites.

### 8.2 "Does it actually deliver?" (slide 43) — three effectiveness doubts

1. **EXPERTISE GAP.** National authorities may **lack the staff, budget, and technical skill** to supervise complex AI experiments. You cannot oversee a frontier model with a two-person regulator.
2. **MOVING TARGET.** Sandboxes are **project-based and pre-defined**, but many AI systems **keep learning and changing after the test ends.** You validated a snapshot; the deployed system has moved on. (This is a deep point: continuous-learning systems break a test-then-certify model.)
3. **NO FEEDBACK LOOP.** "Evidence-based regulation" is the promise, but there is **no formal channel to turn sandbox findings into legal reform.** The regulator learns things and then... has nowhere to put them. (This connects to Schrepel's "the Act cannot adapt itself" critique in Section 10.4.)

**Tie it to the Omnibus (the lecturer's bridge):** the **16-month delay of the high-risk rules** — caused by **missing standards and missing authorities** — is the **evidence deficit in action.** The EU built a learning machine but is not yet ready to run it, so it pushed the deadlines back. The sandbox's promise and the Act's delay are the same story.

Schrepel adds an SME-specific doubt in the paper (Section 10.1): even with free, simple access, the **real-world testing requirements are burdensome** — you must submit testing plans for the MSA's *approval* and secure **dated, documented consent** from participants. That bureaucracy **conflicts with the permissionless, move-fast model** that many start-ups use to challenge incumbents. So the very firms sandboxes are meant to attract may find them unattractive. (Slide 44's reflection question: *"Are sandboxes attractive to you? Would you apply to one?"*)

> **↻ Recall:** Give the three "not a free pass" limits and explain the GDPR-in-a-sandbox answer (Q25). Give the three "does it deliver?" doubts. What is the lecturer's "partial fix" for the harmonisation gap? How does Schrepel say sandboxes may fail to attract the very start-ups they target?

---

## 9. The LeCun podcast — *AI Dynamics & Regulation* (a mandatory L4 reading)

The full episode is assigned. It is the **pro-innovation, anti-over-regulation voice** of the lecture, and it dovetails exactly with Schrepel's competition critique. Yann LeCun is Meta's chief AI scientist, a Turing Award winner, and the field's loudest **open-source** advocate. Know his arguments as *positions you can recognise*, because the lecture uses him to put a human face on "the Act may chill innovation."

### 9.1 The macro view: open source will dominate, and that is good
- **The future ecosystem will be built on open-source base models.** No single company can build a model that serves every language, culture, and value system on Earth. Open base models let any government, start-up, or community **fine-tune for their own constituency** (his examples: India's 22 official languages; a virtual-doctor LLM for Senegal that must speak Wolof and local languages). So the **long tail of actually-used models will be open** derivatives of a few base models.
- **Why open source wins:** more eyeballs → **more secure and safer** (bugs found and fixed faster); **faster progress** (more contributors); and a strong **common-platform incentive** (you do not want to build your whole stack on a proprietary system whose owner can change the API or pull support). His analogy: the internet's entire software stack (Linux, Apache, the browser engines) and cell-tower software are open source **because they are infrastructure** — and if AI mediates all our interactions, it becomes infrastructure too, and "too dangerous" to leave closed.
- **Open source at Meta is robust, not fragile.** It does not depend on LeCun personally ("Meta does not have an open-source policy because I'm here; I'm here because Meta has an open-source policy"). The **one thing that could flip Meta to closed: legal/liability rules** — a regulation that propagates liability down the whole chain when someone misuses an open model would make releasing in the open irrational. **This is the chilling-effect mechanism the whole lecture worries about**, stated by the person it would affect.

### 9.2 The regulation view: do no harm, do not regulate R&D, the existential-risk "myth"
- **"Do no harm" (like medicine).** LeCun's first ask of the law: **do not impede research and development**, especially open R&D. Product-level safety regulation (transport, healthcare) **already exists** and applies whether or not a product uses AI, so you rarely need *AI-specific* rules for safety.
- **Some AI Act provisions are good.** He explicitly approves the parts that **limit mass surveillance / face recognition in public spaces** and **protect private data** — liberal democracies should not allow governments to spy on people that way.
- **The existential-risk regulation is "misguided."** He argues frontier models are **not intrinsically dangerous** and that regulation built on **fear of existential risk** risks **killing an ecosystem early for no reason**, based on a "myth." He frames the lobbying for such rules as partly **regulatory capture** by companies that think they are ahead, and partly sincere but (in his view) mistaken existential-risk campaigners. Historical analogy: France vs Germany on nuclear power in the 1970s — irrational fear of a technology leads to the wrong choice. And the three-stage pattern of how incumbents greet new tech: **ignore it → argue it cannot scale → call it dangerous.**

### 9.3 Where LeCun and the course materials line up exactly

These overlaps are likely exam-relevant because the lecturer chose this episode to *reinforce* the readings:

- **GDPR as the cautionary tale.** LeCun independently cites the finding that, because of GDPR, **EU firms store ~20% less data** and are less data-intensive than firms outside the EU. That is the **same empirical story** as slide 12 and the Schrepel paper. The cost of uniform rules **falls proportionally harder on small companies**.
- **Article 11 as the regulatory-capture exhibit.** The interviewer raises **Article 11** (release technical documentation showing how your AI complies with EU fundamental rights) as "typically the kind of stuff a big company can afford and a small company will struggle to produce." LeCun agrees: compliance is **no problem for a large, already-regulated firm like Meta** but a real burden for smaller firms — a **chilling effect** that can push small open-source developers out. This is **identical** to Schrepel's Article 11 argument (Section 10.2) and to your **Q14**.
- **The FLOP threshold.** LeCun notes the EU rule that training above ~**10²⁵ FLOP** triggers licensing/disclosure (vs ~10²⁶ in the US) — "not an issue for Meta, possibly an issue for smaller companies." Same threshold as Lecture 3 / **Q18**.

The exam-useful synthesis: **LeCun is the qualitative version of Schrepel's quantitative argument.** Both say the Act, by imposing heavy uniform documentation/compliance duties, **favours large incumbents and chills small and open-source innovation**, and both use **GDPR** and **Article 11** as the showcase. If a question frames "a leading AI scientist argued the Act may entrench big players and chill open source," that is LeCun.

> **↻ Recall:** Give LeCun's three reasons open source wins. What is the *one* thing he says could make Meta go closed, and why does that matter for this lecture? What is his "do no harm" ask of regulators, and which AI Act provisions does he *approve* of? Name the two course readings his argument reinforces, and the two showcase examples (a regulation and an article) all three share.

---

## 10. *Decoding the AI Act* (Schrepel 2025) — the deep critique

This is the heaviest reading of Lecture 4 and the source of several exam questions (Q13, Q14, Q19, Q26, and the raw material for the Part B rewrites). The paper's frame: **the AI Act is a future pillar of competition law**, and a competition lawyer who ignores it is making a mistake. It argues this on two fronts: **implications for competition *law*** (II) and **impact on competitive *dynamics*** (III). Learn it as those two halves, each with sub-points.

### 10.1 Implications for competition law (Part II)

**A. The Act quietly *extends competition agencies' investigative powers* (your Q26).** This is the buried bombshell. The chain:
1. Each Member State must designate a **market surveillance authority** (MSA) to enforce the Act (Art 70).
2. The MSA gets **strong access to high-risk AI systems**: full access to **documentation and the training, validation, and testing datasets** (Art 74(12)), via **API or remote access** if needed; and, on a **justified request**, access to the **source code** (Art 74(13)) — but only where (a) it is essential to assess compliance and (b) testing/auditing on the supplied data and documentation **has been exhausted or proved insufficient**.
3. **Article 74** requires MSAs to send **annual reports** to the Commission and national competition agencies, including **"any information"** they find that **"may be of potential interest"** for enforcing EU competition law.

Why this is radical (the exam-relevant point): it **changes the *when* and the *what*** of competition investigations.
- **The *when*:** competition agencies normally can demand information **only when they suspect a breach** (e.g. Art 18 Reg 1/2003; Art 8 ECN+ Directive). The AI Act lets information flow to them **without any suspicion** — the MSA simply passes on what it finds during routine compliance checks. So the Act creates an **effective monitoring mechanism over all companies, regardless of suspicion.**
- **The *what*:** normally the Court of Justice requires the Commission to **state the subject of its investigation and justify why it needs the specific data** (the *HeidelbergCement* case); a company can refuse access to its algorithm if the Commission cannot justify the need. The AI Act routes around this by giving MSAs systematic access to **source code, training sets, logs** that competition agencies could not otherwise get even *with* a suspicion.

**Q26 answer in one line:** the Act expands competition agencies' powers because **MSAs can access documentation, training data and (on justified request) source code, and must pass on information of potential interest to competition agencies.**

**B. It will *slow down computational antitrust*.** Competition agencies increasingly use AI to detect cartels, run NLP and network analysis, etc. (computational antitrust). But the Act labels AI used by **law-enforcement** authorities as **high-risk** (Annex III), and defines law enforcement to include detecting **criminal** offences (Art 3(45b)). Whether a competition infringement is *criminal* varies by country (some criminalise hardcore cartels or bid-rigging, most do not). So an agency using AI to detect *criminal* competition offences must meet the full high-risk compliance burden, while one detecting *civil* ones does not. The effect: the Act **discourages the use of AI to enforce the most harmful (criminal) practices** — an own goal.

**C. Its transparency duties can *facilitate collusion and abuse of dominance* (the safety-vs-competition trade-off).** The Act forces a lot of information-sharing between market participants:
- **Article 19 + 12** require providers of high-risk AI to keep **logs** (system events, inputs, model training, predictions/decisions, performance metrics, timestamps, external-system interactions, etc.). These logs are **commercially sensitive**: they reveal a customer's strategies, pricing patterns, what software they use, when.
- **Articles 16, 23, 24, 25** push transparency along the value chain (providers must keep documentation; importers and distributors must verify upstream compliance; anyone who rebrands or substantially modifies a system, or repurposes it into high-risk territory, becomes a "provider" with full duties). To meet these, parties need **access to each other's sensitive information**.
- The competition danger: this forced transparency can **expose commercially sensitive data**, let firms **monitor and align** behaviour (logs with timestamps/pricing patterns enable tacit collusion), and create **abuse-of-dominance** openings — a risk Schrepel likens to the **Amazon marketplace-data** case. The twist: because the Act frames this sharing as *safety-related* technical information, firms might argue it is **not "commercially sensitive"** under the Art 101 horizontal-cooperation guidelines, so the **safety justification could shield collusion-like behaviour.** Competition agencies will have to weigh "we increased safety" against "you enabled coordination."

### 10.2 Impact on competitive dynamics (Part III): distortion *within* the single market

Two mechanisms.

**(1) "Technology neutrality" is not neutral in practice.** The Commission tried to write a tech-neutral, **use-case-based** law (obligations attach to *where* AI is deployed, not *how* it works). Schrepel's objection: by **refusing to discriminate based on functioning**, the Act effectively **punishes the safer designs.** A **deterministic** system (predictable, low randomness) is genuinely less risky than a **nondeterministic** one (creative, unpredictable). Regulating them the same means a company that *already mitigated risk through design* still has to carry the full compliance load. **True neutrality would impose different burdens on different designs.** His proposed fix: **combine the use-case approach with a technical approach** — full requirements only on systems that are *both* in a high-risk sector *and* nondeterministic; lighter requirements for high-risk-sector but highly-deterministic systems. (As a CS student you will find this the most intuitive argument in the whole reading.)

**(2) The compliance burden is distributed unevenly — the GDPR trap again.** Identical to Section 4.2: a uniform rule **favours large firms** that can spread compliance cost over a huge user base. **GDPR** is the worked example (cost up ~20%, EU firms storing ~26% less data, computation down ~15% vs US firms). The **DSA learned the lesson** (obligations scale with user count); the **AI Act fell back into the GDPR trap.** 

**The Article 11 case study (your Q14, and LeCun's exhibit).** Article 11 requires **technical documentation** for every high-risk system before market, kept up to date, detailed enough (Annex IV) for regulators to assess compliance — including compliance with **fundamental rights** (freedom of expression, assembly, art and science). That needs **both data-science *and* legal expertise.** Schrepel's vivid comparison: it took roughly **800 Microsoft employees and a decade** to compile the interoperability documentation the D.C. Circuit ordered; a **start-up with a handful of staff** cannot produce Article-11 documentation without starving its actual innovation. The Act's only softener — **SMEs may file a *simplified* form** (still undesigned by the Commission) — is, as noted, **the sole SME exemption in Section 2** and **likely insufficient** to prevent distortion. *(That sentence is your Q14.)* He also flags that sandboxes may not offset the burden (the bureaucracy point from Section 8.2).

### 10.3 Impact on competitive dynamics (Part III): *access* to the single market

Three barriers.

**(1) Vague language → litigation (the engine room of Part B).** Schrepel lists the Act's worst-drafted phrases, and these are exactly the provisions the rewrite questions target:
- **Article 5 manipulation:** bans AI using subliminal/manipulative techniques **"materially distorting"** behaviour and causing **"significant harm."** MSAs will struggle to *prove* "material distortion" and "significant harm"; this could even sweep in **AI-based advertising**. (→ **Q28**, rewrite Art 5.)
- **"Real-time" biometric identification (Art 5):** what counts as "real-time"? A one-second delay surely; a twenty-second delay, debatable. The definition ("limited short delays to avoid circumvention") is itself vague → litigation.
- **Article 10 data quality:** datasets must be **"relevant, sufficiently representative and, to the best extent possible, free of errors and complete."** Schrepel's verdict (**your Q13**): this is a **clear improvement** over the Commission's original "free of errors" (which was **precise but unrealistic** — large datasets with trillions of entries cannot be made fully error-free, and checking them all would be prohibitively costly), **but it remains vague** ("sufficiently," "to the best extent possible") and is **likely to generate litigation.** Memorise that exact shape: *better than the original, still vague, will breed litigation.* (→ **Q29**, rewrite Art 10.)
- **Article 14 human oversight:** persons overseeing the system must **"remain aware"** of the tendency to **over-rely** on outputs (**automation bias**). This leaves firms unsure how to guarantee their staff "remain aware." (→ **Q30**, rewrite Art 14.)

**(2) High fines despite the vagueness.** Vague rules + big penalties = a strong deterrent to entering the market. The fine ladder (**Q9, Q10**):
- **Breach of Article 5 (prohibited practices): up to €35 million or 7% of total worldwide annual turnover, whichever is higher** (Art 99(3)).
- **Breach of other obligations (e.g. high-risk Arts 9–15): up to €15 million or 3%** (Art 99(4)).
- (Misleading authorities: up to €7.5m or 1%.) For **EU institutions/bodies**: €1.5m (Art 5 breach) / €750k (others).
- **Omnibus:** **capped/proportionate fines** for SMEs/SMCs under Art 99(6)/(6a).

**(3) Costly substantive obligations + industry-capture risk.** Several articles are simply expensive to comply with, and the Act repeatedly **prioritises safety/transparency over competition**:
- **Article 9** — a **risk-management system** that is a **continuous, iterative process maintained throughout the entire lifecycle**, with regular reviews (**Q12**). Not a one-off.
- **Article 14** — human oversight; **Article 15** — designed-in **accuracy, robustness, and cybersecurity** across the lifecycle (**Q15**).
- **Article 12/13** — automatic **logging** and enough **transparency** for deployers to interpret outputs (raises reverse-engineering and assessability problems).
- **Industry capture:** two compliance routes — follow a **harmonised standard** (→ presumption of conformity) or **self-assess** (often needing a **notified body**'s sign-off, Art 43). Most firms will follow standards to save cost and gain certainty. So whoever **controls the standard-setting bodies** (CEN, CENELEC, ETSI) and notified bodies effectively shapes the rules — and **SMEs are under-represented** there. The vague Art 17 promise that SMEs be "appropriately represented" is unsatisfying; Schrepel suggests revising Regulation 1025/2012 to make these bodies more transparent.

### 10.4 The GPAI half and the "it cannot fix itself" finale

**GPAI distortions (ties to Lecture 3 and Q17–Q22).** The second pillar (capability-based GPAI rules) shares the first pillar's flaw: **vague definition** (Art 3(63): "significant generality," "large amount of data," "self-supervision at scale," "wide range of distinct tasks," "variety" of downstream systems — every load-bearing word is fuzzy); **costly documentation** (Art 53, Annexes XI/XII) that hits SMEs hardest; an **open-source exemption** built on a **binary** definition (Section 6); and a **systemic-risk gate** at **>10²⁵ FLOP** (Art 51) with the Commission holding wide discretion via delegated acts. The Apr-2024 models above the threshold (**Q19**): **Gemini Ultra, Mistral Large, GPT-4, and Inflection 2** (per Epoch AI). 

**The structural finale — the Act cannot adapt itself (Part III.D).** This is Schrepel's most damning point and the natural close of a "strengths and weaknesses" lecture. The Act *calls itself* "future-proof" and "adaptable," but:
- The **Article 4** power (let the Commission update the *definition of an AI system* as techniques evolve) was **removed** from the final text. The definition is **frozen.**
- The Commission can amend **Annex III** by *removing* high-risk systems (Art 7(3)), *reclassify* systems as not-high-risk (Art 6(3)), and *propose* amendments to Annex III, Article 5, and Article 50 (Art 112) — but the **prohibited list, the GPAI rules, and the lists of obligations are not directly adaptable**, and most amendments need **Parliament and Council approval.**
- So if the evidence later shows a provision is ineffective or anti-innovation, the Commission **cannot simply fix it** — it must write a report and persuade the other institutions. A law built to govern the **fastest-moving technology of our era** has **slow, partial, politically-gated adaptation.** That is the deepest weakness, and it loops straight back to the sandbox critique (Section 8: "no feedback loop" — the Act learns but cannot act on what it learns).

**The conclusion's tone (worth knowing for a "what is Schrepel's overall stance" question):** not nihilistic. The Act **prevents market fragmentation** (a genuine good) but **creates barriers to entry and avoidable distortions**, and its innovation/competition harms are **not clearly offset** by benefits — especially troubling given other scholars doubt it even protects fundamental rights effectively. But "the situation is not beyond repair": the impact depends on what practitioners, scholars, and policymakers **make of it** through engagement, documentation, and combining legal + technical expertise. *Right instinct, flawed build, fixable if we work at it* — the same two-part verdict as every other critique in this lecture.

> **↻ Recall:** Explain how the Act extends competition agencies' powers, including the *when* and the *what* (Q26). Why does it slow computational antitrust? Give Schrepel's verdict on Art 10 (Q13) and Art 11 (Q14) in his exact shape. Why is "technology neutrality" not neutral, and what fix does he propose? List the four vague provisions that map to Part B. State the fine for breaching Art 5 vs other articles (Q9/Q10). What is the single deepest structural weakness, and how does it connect to the sandbox "no feedback loop"?

---

## 11. The fifth reading: *Building a Digital Brain for Research* (Schrepel 2026)

The manual lists this under "**Understand what this does**" — lighter than the others, and not obviously the target of a Part A question. But it is assigned, it is *by the lecturer*, and it closes the conceptual loop of the course, so know what it is and why it is here.

**What it is.** A practical guide to building a **"digital brain"** (a term from Andrej Karpathy): a personal, **queryable knowledge graph** built from a trusted corpus of documents. You feed it PDFs; it converts them to text, maps the connections between sources, and answers natural-language questions **grounded only in your corpus**, with citations. The output is like a **private, queryable Wikipedia** that flags contradictions between sources and surfaces gaps in the literature. The pipeline (Collect → Convert with MarkItDown → Graph with Graphify → Wiki → Query, plus incremental Maintenance) needs no programming and runs on Claude Code.

**Why it is on a *law* course, and the link to make.** This is **"code is law / law as code" (Lecture 1) and computational law (Lecture 4) made concrete.** Schrepel spent the *Decoding* paper arguing the Act gestures at being computational (it points at a FLOP number) but is not itself runnable. The "digital brain" is the flip side: a demonstration of treating a body of legal/scholarly material as **structured, queryable, machine-checkable knowledge.** The one design idea worth carrying into the exam if computational law comes up: the **schema-design step (the CLAUDE.md file)** is what turns a retrieval tool into a **research instrument** — it encodes an **authority hierarchy** (court judgments > administrative decisions > regulations > peer-reviewed work > working papers) and instructs the system to flag **what the sources do *not* say**. The takeaway: structure and explicit hierarchy are what make machine-readable law useful, the same lesson Lecture 1 taught about expressing rules as code.

You do not need the pipeline details for the MCQ. You need: **what it is** (a queryable knowledge graph from a document corpus) and **why it is assigned** (computational-law / "law as code" demonstration, closing the Lecture 1 ↔ Lecture 4 loop).

> **↻ Recall:** In one sentence, what does the "digital brain" do? Why would a *law* lecturer assign it — what course theme does it make concrete?

---

## 12. The Lessig thread (because the course keeps pulling it through)

Lecture 1 gave you **Lessig's four modalities** that regulate behaviour — **Law, social Norms, the Market, and Architecture (code)** — and Schrepel's refinement that the regulated "dot" is **not passive**: it reacts to and reshapes those constraints (the *Not-So-Pathetic Dot Theory*, a complex adaptive system). Lecture 4 is that theory **playing out in real time**, and tagging the material this way is a strong memory hook.

- **Market → Law.** The whole exemptions story is the **Market modality pushing back on Law and bending it.** Mistral and Aleph Alpha lobbying softened the GPAI rules (L3); the **open-source carve-out** and the **SME/SMC reliefs** are Law yielding to economic pressure; the **Omnibus** is the dot (industry + Draghi's competitiveness alarm) reshaping the constraint after the fact.
- **Architecture → Law.** The **10²⁵ FLOP** threshold wires a **technical metric (Architecture)** directly into **legal status** — compute count decides whether systemic-risk Law attaches. Same move as L3.
- **Law freezing Architecture (the Lecture-1 caution).** Schrepel warned regulators not to **"freeze" a technology** by mandating a single fixed standard (the USB-C example). Lecture 4's "**the Act cannot adapt itself**" finale is exactly that danger realised: a frozen definition of "AI system," lists that need Parliament to change, governing the fastest-moving technology around.
- **Norms doing regulatory work.** **Codes of practice** and **harmonised standards** are **Norms** standing in for detailed Law — and the **industry-capture** worry is that whoever controls those Norm-making bodies controls the real rules.

If a question frames any of this as "which Lessig modality," you can answer it: exemptions/lobbying/Omnibus = **Market → Law**; FLOP threshold = **Architecture → Law**; frozen definition = **Law over-constraining Architecture**; standards/codes = **Norms**.

> **↻ Recall:** Tag three Lecture-4 phenomena to a Lessig modality. Which Lecture-1 caution does the "Act cannot adapt itself" finale realise?

---

## 13. The whole lecture as one structure (build this from memory)

Before the practice questions, draw this skeleton once, closed-book. If you can reproduce it, you have the lecture.

**The funnel (the spine):**
1. Is the AI **in scope at all?** → *Scope exemptions:* military (Art 2(3)), scientific R&D (Art 2(6)), pre-market prototyping (Art 3(63)/2(8)), purely personal use (Art 2(10)), open-source-not-deployed-as-high-risk/Art-5/Art-50 (Art 2(12)). **Out of scope → no obligations.**
2. If in scope, is the actor **relieved or exempt?** → *SME/micro reliefs* (simplified QMS – Rec 146; simplified tech docs – Art 11; "avoid unnecessary burdens" – Art 34), extended to **SMCs** by the Omnibus. *Open-source GPAI* exempt from documentation duties (Art 53) — **unless systemic risk, high-risk deployment, or Art 50.**
3. If still bound, can they **shelter while testing?** → *Sandboxes* (Art 57/58: free, priority for SMEs/SMCs, good-faith fine shield, exit report) and *real-world testing* (Art 60/60a: guardrails, ≤6+6 months). **But:** no shield from GDPR/liability, not harmonised, expertise gap, moving target, no feedback loop.

**The running critique (the verdict on every valve):** *right goal, wrong instrument.* Innovation language is mostly **non-binding recitals**; exemptions are gated by **absolute words and fuzzy triggers** (loopholes); uniform burdens **favour incumbents** (the GDPR trap); **vague drafting** breeds litigation while **fines stay high**; the open-source test is **binary for a spectrum concept**; and the Act **cannot adapt itself** when it gets things wrong.

**The two voices:** **Schrepel** (quantitative, competition-law: extended agency powers, distortion, access barriers, non-adaptivity) and **LeCun** (qualitative, open-source: do-no-harm, chilling effect on small/open developers, the existential-risk "myth"), agreeing on the same showcase — **GDPR** and **Article 11**.

---

## 14. Practice MCQs (do these closed-book)

Two batches. Cover the answers. Answer, then read *why each wrong option is wrong* — that is where the learning is. Redo any you miss tomorrow, not now.

**Batch A — exemptions, sandboxes, the lecture's own content**

**1.** Slide 7's key point about the Act's many "support innovation" statements is that:
A) They make innovation a legally enforceable right.
B) They sit mostly in recitals, which are not binding and have only interpretative value.
C) They override the high-risk obligations.
D) They appear only in the annexes.

**2.** The SME definition (Recommendation 2003/361/EC) is:
A) Fewer than 750 employees and turnover ≤ €150m.
B) Fewer than 250 employees and either turnover ≤ €50m or balance sheet ≤ €43m.
C) Fewer than 50 employees and turnover ≤ €10m.
D) Any company not listed on a stock exchange.

**3.** The lecturer's stated *reason* behind the small-company exemptions is, among other things:
A) To copy the GDPR's approach exactly.
B) To do *not* repeat GDPR's regressive cost effect, and to address Draghi's competitiveness concerns.
C) To favour large incumbents deliberately.
D) To comply with the US Executive Order.

**4.** Under the Digital Omnibus, the SMC ("small mid-cap") threshold is:
A) Fewer than 250 employees + turnover ≤ €50m.
B) Fewer than 500 employees + turnover ≤ €100m.
C) Fewer than 750 employees + turnover ≤ €150m or balance sheet ≤ €129m.
D) Fewer than 1,000 employees + any turnover.

**5.** Which is a *scope* exemption (the Act does not apply at all), not merely a relief?
A) SMEs filing simplified technical documentation.
B) AI used exclusively for military, defence, or national-security purposes.
C) High-risk providers running a sandbox test.
D) GPAI providers publishing a training-data summary.

**6.** The open-source carve-out for GPAI documentation duties does **not** apply when:
A) The provider is based in the EU.
B) The model has systemic risk, or is deployed as high-risk, or falls under Article 5 or 50.
C) The model has fewer than 10 billion parameters.
D) The provider is an SME.

**7.** The Act's Article 53(2) definition of "open source" is criticised (Schrepel & Potts) because:
A) It is too generous to closed models.
B) Openness is a spectrum, but the Act uses a binary open/closed test (e.g. Llama 3 and GPT-4 differ by only 2 of 36 points).
C) No model is open in any respect.
D) It gives open models stricter duties than closed ones.

**8.** A company tests a healthcare AI inside an Article 57 sandbox. Because the sandbox is "without prejudice to other Union law," the company:
A) Is exempt from GDPR for the test.
B) May treat the sandbox as a blanket legal basis for any processing.
C) Must still identify a valid GDPR legal basis to process patient data.
D) No longer needs to comply with the AI Act inside the sandbox.

**9.** Which is a genuine *limit* of regulatory sandboxes the lecture stresses?
A) They suspend all liability for participants.
B) They are perfectly harmonised across the EU.
C) Providers remain fully liable for harm, and sandboxes are run by national authorities with differing capacity (not harmonised).
D) They automatically turn findings into new legislation.

**10.** Real-world testing under Articles 60/60a is capped at:
A) 3 months, non-extendable.
B) 6 months, extendable once by 6 months.
C) 24 months, extendable twice.
D) No time limit.

> **Answers A:** 1-**B** · 2-**B** · 3-**B** · 4-**C** · 5-**B** (A and D are obligations/reliefs *within* scope; C is a shelter, not an exclusion) · 6-**B** · 7-**B** · 8-**C** (this is Q25 — sandbox ≠ GDPR holiday) · 9-**C** (A/B/D are the *opposite* of the slide 42–43 limits) · 10-**B**.

**Batch B — the Schrepel paper and the readings (the engine-room questions)**

**11.** How does the AI Act indirectly *expand* competition agencies' powers (Q26)?
A) It lets them block mergers in AI markets.
B) Market-surveillance authorities can access documentation, training data and (on justified request) source code, and must pass on information of potential interest to competition agencies.
C) It transfers all GPAI enforcement to national competition authorities.
D) It lets them demand information in all cases without any suspicion of a competition infringement.

**12.** Schrepel's verdict on Article 10's "relevant, sufficiently representative … to the best extent possible, free of errors and complete" (Q13) is that it:
A) Is fully precise and leaves no room for interpretation.
B) Should be deleted because data quality is irrelevant.
C) Improves on the unrealistic original "free of errors," but remains vague and likely to generate litigation.
D) Requires datasets to be entirely error-free.

**13.** On Article 11's SME accommodation (Q14), Schrepel argues:
A) SMEs face stricter duties than large firms.
B) SMEs may file simplified documentation; it is the only SME-specific relief in the high-risk requirements and is likely insufficient to prevent market distortion.
C) SMEs are fully exempt from all high-risk obligations.
D) The Act draws no SME distinction anywhere.

**14.** Why does Schrepel say the Act's "technology neutrality" is not neutral in practice?
A) It bans specific technologies by name.
B) By treating deterministic (safer) and nondeterministic (riskier) systems the same, it over-burdens firms that already mitigated risk by design; true neutrality would impose different burdens on different designs.
C) It favours nondeterministic systems explicitly.
D) It applies only to open-source models.

**15.** As of April 2024 (Epoch AI), which models had crossed the 10²⁵ FLOP systemic-risk threshold (Q19)?
A) Only GPT-4.
B) Gemini Ultra, Mistral Large, GPT-4, and Inflection 2.
C) Llama 2 and BLOOM.
D) No model had crossed it.

**16.** Non-compliance with the Article 5 prohibitions can attract fines up to (Q9):
A) €750,000 in all cases.
B) €10 million or 2% of worldwide turnover.
C) €15 million or 3% of worldwide turnover.
D) €35 million or 7% of total worldwide annual turnover, whichever is higher.

**17.** Schrepel's *deepest structural* criticism of the Act is that:
A) Its fines are too low.
B) It cannot adapt its own substance: the Art 4 power to update the AI definition was removed, and most amendments need Parliament/Council, so a fast-moving technology is governed by a law that cannot easily fix itself.
C) It contains no definition of GPAI.
D) It applies only inside the EU.

**18.** In the LeCun podcast, the *one* development he says could push Meta from open to closed source is:
A) A competitor releasing a better model.
B) Running out of GPUs.
C) Legal/liability rules that propagate liability down the chain, making open release irrational.
D) A change in CEO.

**19.** LeCun and the Schrepel paper agree on a showcase example of regressive compliance cost, namely:
A) The DSA's tiered platform rules.
B) GDPR (EU firms storing ~20% less data; cost falling harder on small firms) and Article 11's documentation burden.
C) The Digital Markets Act's gatekeeper list.
D) The CE-marking regime.

**20.** The "digital brain" reading is assigned on this *law* course mainly because it:
A) Teaches you to build commercial software for profit.
B) Demonstrates computational law / "law as code" — turning a document corpus into structured, queryable, citation-grounded knowledge.
C) Replaces the AI Act.
D) Is required reading for the GDPR.

> **Answers B:** 11-**B** (D is wrong because the *justified-request/HeidelbergCement* limits still apply to direct competition requests; the Act's trick is the indirect MSA channel) · 12-**C** · 13-**B** · 14-**B** · 15-**B** · 16-**D** (the 7%/€35m band is the *prohibition* band; do not confuse with the 3%/€15m other-articles band) · 17-**B** · 18-**C** · 19-**B** · 20-**B**.

If you can score both batches closed-book **and explain why each wrong answer is wrong**, you have Lecture 4 cold. For Part B (Q28–30), see the rewrite drill in Section 16.

---

## 15. Flashcards (front → back)

Make these physical or load them into Anki; run them across several days, interleaved with the other lectures. Say the answer aloud before flipping.

- **The one tension Lecture 4 is about?** → Protecting fundamental rights vs fostering innovation.
- **Two families of "release valve"?** → Exemptions and regulatory sandboxes.
- **Are recitals binding?** → No — interpretative value only (the articles bind).
- **"Support innovation" appears how many times as an objective?** → 45.
- **SME thresholds (2003/361/EC)?** → <250 staff AND (turnover ≤ €50m OR balance sheet ≤ €43m).
- **SMC thresholds (Omnibus)?** → <750 staff AND (turnover ≤ €150m OR balance sheet ≤ €129m).
- **Three SME/micro reliefs + articles?** → Simplified QMS (Rec 146, micro) · simplified technical docs (Art 11) · "avoid unnecessary burdens" (Art 34).
- **Schrepel on the Art 11 SME relief (Q14)?** → Only SME relief in Section 2 → likely insufficient to prevent market distortion.
- **Two *reasons* for the SME exemptions?** → Do not repeat GDPR's regressive cost/concentration effect; address Draghi's competitiveness alarm.
- **GDPR effect figures?** → ~8% profit drop (≈2× for small firms); ~⅓ of apps withdrawn, new-app entry halved; reinforced concentration; ~20% costlier data storage → EU firms store ~26% less, compute ~15% less than US.
- **Four "mixed bag" exemptions + articles?** → Scientific R&D (Art 2(6)) · pre-market prototyping (Art 3(63)/2(8)) · military/defence/national security (Art 2(3)) · purely personal non-professional use (Art 2(10)).
- **The word that gates each "mixed bag" exemption?** → *exclusively / solely / purely* — and that absolutism is the loophole.
- **The military exemption critique?** → Bans low-stakes manipulation but totally exempts the highest-stakes use; clashes with "human-centric AI."
- **Open-source carve-out — what it switches off?** → The Art 53 documentation duties (and Art 54 representative).
- **Three situations where open-source relief does NOT apply?** → Systemic-risk GPAI · deployed as high-risk · falls under Art 5 or Art 50.
- **Art 53(2) open-source definition?** → Licence allowing access/use/modification/distribution + public weights, architecture, usage info.
- **Schrepel & Potts critique (Q22)?** → Openness is a spectrum; the Act's binary test misclassifies (Llama 3 vs GPT-4 = 2/36 points apart); ignores governance dimensions; inconsistent with PLD and Cyber Resilience Regulation.
- **Sandbox goals (Art 57)?** → Innovation, legal certainty, evidence-based regulatory learning.
- **Sandbox: who runs them, by when (Omnibus)?** → Every Member State ≥1, operational by 2 Aug 2027 (pushed back 12 months).
- **Three sandbox tiers?** → National (Member States) · Union-level (AI Office, NEW) · EU institutions (EDPS, NEW).
- **Art 58 four steps?** → Apply → Agree a plan → Test (good-faith fine shield) → Exit report (smooths market entry).
- **Most attractive sandbox feature?** → No administrative fines for good-faith participants.
- **Real-world testing cap (Art 60/60a)?** → 6 months, extendable once by 6 (12 max); guardrails: approved plan, informed consent, human oversight, full liability, withdrawable consent.
- **Sandbox "not a free pass" — three limits?** → No shield (GDPR/rights/product-safety still apply) · still liable for harm · not harmonised across Member States.
- **Sandbox in a sandbox — GDPR (Q25)?** → Still need a valid GDPR legal basis; sandbox ≠ GDPR exemption.
- **Sandbox "does it deliver" — three doubts?** → Expertise gap · moving target (systems keep learning) · no feedback loop into legal reform.
- **LeCun's three reasons open source wins?** → More secure (more eyeballs) · faster progress · common-platform/infrastructure incentive.
- **The one thing that could flip Meta to closed?** → Liability rules propagating down the chain → chilling effect.
- **LeCun's "do no harm" ask?** → Don't regulate (open) R&D; product-safety rules already exist; he approves the Act's anti-mass-surveillance and data-protection parts.
- **How the Act extends competition agencies' powers (Q26)?** → MSAs access docs/training data/(justified) source code and must pass on info of potential interest to competition agencies — bypassing the usual "suspicion" and "justify the request" limits.
- **Why it slows computational antitrust?** → AI used by law enforcement to detect *criminal* offences is high-risk; whether competition infringements are criminal varies by country → discourages AI use against the most harmful practices.
- **The safety-vs-competition trade-off?** → Forced transparency (logs Art 19/12; Arts 16/23/24/25) can expose sensitive data and enable collusion/abuse, possibly shielded as "safety" info.
- **"Tech neutrality is not neutral" — the point + fix?** → Treating deterministic and nondeterministic systems alike over-burdens safer designs; fix = combine use-case with a technical (determinism) approach.
- **Art 10 verdict (Q13)?** → Better than the unrealistic "free of errors," still vague ("sufficiently," "to the best extent possible"), litigation-prone.
- **Four vague provisions feeding Part B?** → Art 5 ("materially distorting"/"significant harm" + "real-time") · Art 10 (data quality) · Art 14 ("remain aware") .
- **Fine for Art 5 breach vs other articles (Q9/Q10)?** → €35m/7% (Art 5) vs €15m/3% (others); EU bodies €1.5m / €750k; Omnibus caps for SMEs/SMCs.
- **Models above 10²⁵ FLOP, Apr 2024 (Q19)?** → Gemini Ultra, Mistral Large, GPT-4, Inflection 2.
- **The deepest structural weakness (Part III.D)?** → The Act cannot adapt its own substance (Art 4 removed; most changes need Parliament/Council) → frozen law for a fast technology.
- **"Digital brain" reading — what + why?** → A queryable knowledge graph from a document corpus; assigned as a computational-law / "law as code" demonstration.
- **Lessig tags for Lecture 4?** → Exemptions/lobbying/Omnibus = Market → Law; 10²⁵ FLOP = Architecture → Law; frozen definition = Law over-constraining Architecture; codes/standards = Norms.
- **The one-line verdict shared by every critique?** → Right goal, wrong instrument (fixable).

---

## 16. Part B drill — rewriting a bad provision (Q28–Q30)

Part B is not about memorising; it is about *judgement*. The paper defines the best rewrite as **clearer than the original while staying (a) proportional to the provision's objective and (b) consistent with the rest of the Act.** So a winning answer does three things at once and avoids three traps.

**The three things a good rewrite does:**
1. **Keeps the objective.** Art 5 manipulation → protect *autonomy*. Art 10 → *data quality / non-discrimination*. Art 14 → *effective human control*. Do not rewrite the goal away.
2. **Sharpens the vague term** Schrepel flagged, into something an authority could actually apply ("appreciably impair a person's ability to make an informed decision" instead of "materially distorting"; "reasonable, documented measures to detect and reduce errors" instead of "to the best extent possible free of errors").
3. **Stays proportional.** No absolute, impossible demand (not "completely free of all errors," not "a human must approve every single output").

**The three traps (the wrong options are always one of these):**
- **Too vague / empty** ("Prohibited: AI systems that are manipulative"; "Datasets shall be appropriate"). Clear-sounding, says nothing.
- **Too narrow / guts the objective** ("only where the provider admits intent to cause harm"; "may contain whatever data the provider chooses"). Kills the protection.
- **Too absolute / disproportionate** ("completely free of all errors"; "a human must individually approve every single output"). Unworkable, the exact flaw Schrepel diagnosed in the *original* Art 10.

**Worked logic on the three live ones (from the mock):**
- **Q28 (Art 5):** the winner sharpens "materially distorting" into "appreciably impair a person's ability to make an informed decision" and keeps the harm element ("cause or be likely to cause significant harm"). It preserves autonomy, sharpens the vague term, stays proportional. The losers are empty ("are manipulative"), gutted ("only if the provider admits intent"), or overbroad ("any system that influences behaviour" — that would ban all advertising).
- **Q29 (Art 10):** the winner keeps "relevant and sufficiently representative" but replaces the impossible completeness/"free of errors" language with **"reasonable, documented measures to detect and reduce errors."** That is the proportional, realistic version Schrepel was asking for. The losers are absolute ("completely free of all errors"), empty ("appropriate"), or objective-destroying ("whatever data the provider chooses").
- **Q30 (Art 14):** the winner gives the overseer real, operational powers — **competence, authority, and means to monitor, correctly interpret the output, and decide not to use it or to override it.** That delivers *effective human control*. The losers are vague ("stay aware of its risks"), toothless ("recommended where feasible"), or disproportionate ("approve every single output").

**Your drill:** for each of Articles 5, 10, 14, write your *own* one-sentence rewrite from memory, then check it against the three-things / three-traps test. If your sentence is clearer, keeps the goal, and is not absolute, you will recognise the right option instantly in the room.

---

## 17. One-page cheat sheet, glossary, and study plan

### The whole lecture in one box
- **The tension:** protect fundamental rights **vs** foster innovation. The Act mentions innovation 45×, mostly in **non-binding recitals**; the real innovation tools are the binding **exemptions** and **sandboxes**.
- **Exemptions (1) — small firms:** simplified QMS (Rec 146) · simplified tech docs (Art 11) · "avoid unnecessary burdens" (Art 34); Omnibus extends to **SMCs** (<750 staff). *Why:* don't repeat GDPR's regressive cost; answer **Draghi**. *Schrepel:* Art 11 relief is the only one in Section 2 → insufficient.
- **Exemptions (2) — mixed bag:** scientific R&D (Art 2(6)) · pre-market prototyping (Art 3(63)) · military (Art 2(3)) · purely personal use (Art 2(10)). *Flaw:* gated by *exclusively/solely/purely* + fuzzy "placed on the market" trigger → loopholes; military carve-out vs "human-centric AI."
- **Exemptions (3) — open source:** relieves Art 53 documentation duties **unless** systemic-risk / high-risk / Art 5 or 50. *Definition (Art 53(2)):* public weights + architecture + usage. *Schrepel & Potts:* openness is a **spectrum**, the Act's **binary** test misclassifies (Llama 3 vs GPT-4 = 2/36).
- **Sandboxes (Art 57/58):** controlled pre-market testing; free, priority for SMEs/SMCs; **good-faith fine shield**; exit report smooths entry; ≥1 per Member State by **2 Aug 2027**; three tiers (National / AI Office / EDPS). **Real-world testing (Art 60/60a):** field testing, ≤6+6 months, guardrails.
- **Sandbox limits:** no shield (GDPR/rights/safety still apply — **Q25**) · still liable · not harmonised · expertise gap · moving target · no feedback loop.
- **Schrepel critique:** extends competition-agency powers (**Q26**); slows computational antitrust; transparency enables collusion; "tech neutrality" isn't neutral (determinism); GDPR-trap uneven burden (Art 11 — **Q14**); vague drafting (Art 5/10/14 — **Q13**, Part B) + high fines (**Q9/Q10**); industry capture via standards; **cannot adapt itself** (deepest flaw).
- **LeCun:** open source wins (secure/fast/infrastructure); liability rules could chill it; "do no harm," existential-risk regulation is a "myth"; same GDPR + Art 11 showcase as Schrepel.
- **Digital brain:** queryable knowledge graph from a corpus = **computational law / "law as code"** demo.
- **Lessig:** Market→Law (exemptions/lobbying/Omnibus) · Architecture→Law (10²⁵ FLOP) · Law freezing Architecture (frozen definition) · Norms (standards/codes).
- **The verdict everywhere:** *right goal, wrong instrument, fixable.*

### Glossary (plain-language, for the non-lawyers)
- **Recital / article:** non-binding "whereas" preamble (interpretation only) / binding operative rule (enforceable).
- **Exclusion / exemption / relief:** Act doesn't apply at all / a specific duty lifted / a duty made lighter.
- **SME / SMC / microenterprise:** <250 staff (€50m/€43m) / <750 staff (€150m/€129m, Omnibus) / smallest tier.
- **Digital Omnibus:** 2026 simplification patch to the Act (SMC extension, sandbox delay, new sandbox tiers, wider real-world testing, capped SME/SMC fines).
- **Sandbox / real-world testing:** regulator-run pre-market test space (Art 57/58) / field-testing permission with guardrails (Art 60/60a).
- **Market surveillance authority / notified body:** national enforcer with access powers / accredited third party that certifies conformity.
- **Conformity assessment / presumption of conformity / CE marking:** the compliance check / "assumed compliant if you followed a harmonised standard" / the EU market-access stamp.
- **Technology neutrality:** writing rules that don't favour a technology; Schrepel says the Act's version isn't neutral because it ignores determinism.
- **Deterministic / nondeterministic AI:** same input → same output (safer) / same input → varying output (riskier).
- **Computational antitrust / computational law:** software-assisted competition enforcement / law expressed as runnable, checkable code.
- **TFEU / Art 101 / Art 102:** the EU treaty / ban on anti-competitive agreements (collusion) / ban on abuse of dominance.
- **GDPR / DSA / DMA / PLD / CDSM:** data-protection law (the cautionary tale) / platform-responsibility law (tiered by size) / gatekeeper-platform law / product-liability rules / copyright TDM-opt-out directive.
- **FLOP / 10²⁵ threshold:** floating-point operation; training compute > 10²⁵ FLOP presumes systemic risk (Art 51).
- **Systemic risk vs high-risk:** dangerous *model* (capability) vs dangerous *use* (use case) — don't mix them.

### Study plan (spaced, not crammed)
- **Today:** read Sections 1–8 once; do every **↻ Recall** aloud; sketch the **Section 13 funnel** from memory.
- **Tomorrow:** read Sections 9–12 (LeCun, Schrepel, digital brain, Lessig); do **Batch A** MCQs closed-book; build the flashcards.
- **+2 days:** do **Batch B** MCQs and the **Section 16 Part B drill** closed-book; redo anything missed in Batch A; one full flashcard pass.
- **+4 days, then twice-weekly to June 24:** one fast flashcard pass, **interleaved** with Lectures 1, 2, 3, 5 — mix Lecture-4 exemption cards with risk-pyramid cards (L2), GPAI cards (L3), Lessig cards (L1), and legal-stack cards (L5). It feels harder; that difficulty is the point.

That rhythm — **recall, space, interleave** — is what the research says actually moves a multiple-choice grade. The summary got you to understand it. The testing is what makes you remember it in the room on **June 24**.
