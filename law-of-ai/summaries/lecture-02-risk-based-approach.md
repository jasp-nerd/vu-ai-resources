# Lecture 2 Study Guide — The AI Act: The Risk-Based Approach
**The Law of Artificial Intelligence (VU Amsterdam, 2026)**

This guide covers Lecture 2 and its mandatory readings: Articles 5–15 of the EU AI Act, and Hupont et al., *Documenting High-Risk AI* (IEEE, 2023). It is written so you can follow it cold, without having attended the lecture and without a legal background. Every piece of law jargon is explained the first time it appears.

It is written like someone talking you through the material, not like a bullet-point dump, because the exam asks you to *reason*, not just recognise keywords. But it is also engineered around how memory actually works, so read the next short section before you dive in.

---

## How to use this guide (this part is not filler — it is the single biggest lever on your grade)

The research on studying is unusually clear, and almost everyone ignores it. Two findings matter most for an exam two weeks out.

**1. Retrieval practice beats re-reading.** Decades of work (Roediger and Karpicke's "testing effect" is the classic) show that the act of pulling an answer *out* of your head builds far more durable memory than putting information *in* by reading it again. Re-reading feels productive because the text gets easier to read each time, but that fluency is an illusion. It does not transfer to the exam, where the text is not in front of you. So: every section below ends with a few **Recall checks**. Cover the section, answer them out loud or on paper, then check. If you only do one thing with this document, do that.

**2. Spacing beats cramming.** The same total study hours produce more retention when spread across days than when piled into one session (the "spacing effect," Cepeda et al.). Practically: read this guide once now, do the recall checks. Tomorrow, do *only* the recall checks and the flashcards at the end without re-reading. The day after, do the mock self-test. You will feel like you are forgetting between sessions. That forgetting-then-retrieving is exactly the mechanism that works.

Two supporting techniques worth knowing:

- **Elaborative interrogation** — keep asking "why is the rule like this?" The AI Act is full of design choices with reasons behind them, and the exam (especially the rewrite questions in Part B) rewards understanding the reason, not the wording. Whenever you hit a rule, ask what problem it was solving.
- **Dual coding** — pair words with a picture. The whole Act hangs off one picture: the risk pyramid. Draw it from memory once. If you can sketch the four tiers and name what triggers each, you have the spine of the lecture.

**What the exam actually looks like (your baseline).** The exam is multiple choice, one correct answer per question. Part A tests lectures and readings; for this lecture that means definitions, the four tiers, what each tier triggers, the specific obligations in Articles 9–15, the penalty bands, and the Hupont reading. Part B gives you a clumsy provision and four rewrites and asks which is best. There is a method for those, and it is taught at the very end of this guide. Notice that the questions are not "quote Article 9" — they are "which description of Article 9 is correct," with three plausible-sounding wrong answers. That means you need to be able to *distinguish* the real rule from a near-miss. Recognising the gist is not enough; you need the discriminating detail.

---

## The 60-second overview (read this, then we slow down)

The EU AI Act is a **Regulation** (more on what that word means below) that governs AI by sorting it into four boxes according to how dangerous its *use* is, and attaching heavier rules to more dangerous boxes. From most to least dangerous:

1. **Unacceptable risk → banned outright** (Article 5).
2. **High risk → allowed, but only if you meet a long list of obligations** (Articles 6–15 and more).
3. **Limited risk → allowed, with light transparency duties** (Article 50): mainly "tell people they are dealing with AI."
4. **Minimal / no risk → allowed, no special duties**, just voluntary codes of conduct (Article 95). This is the vast majority of AI.

The clever and contested move is in the word *use*. The Act mostly does not ask "is this technology dangerous?" It asks "what is this system being used *for*?" The same underlying model can be minimal risk in one application and high risk in another. Hold onto that idea — it is the heart of the lecture, and several exam questions probe it.

---

## A vocabulary primer for non-lawyers

You do not need a law degree, but you need maybe a dozen terms. Skim this once and refer back. I am putting it up front so the rest reads smoothly.

**Regulation (capital R).** An EU **Regulation** is a law that applies directly and identically in every member state the moment it takes effect. Nobody has to copy it into Dutch or German law first. Contrast a **Directive**, which sets a goal and leaves each country to write its own implementing statute ("transposition"). The AI Act is a Regulation, which is why there is one EU-wide text and one set of rules, not 27 national variants. When an exam answer hinges on "the AI Act is a Regulation," it usually means *uniform, directly applicable, no national transposition needed*.

**Article vs Recital.** The **Articles** are the numbered binding rules (Article 5, Article 9, and so on). The **Recitals** are the numbered paragraphs at the front of the Act ("Whereas..."). Recitals are *not* directly binding, but courts use them to interpret the Articles — they explain what the drafters meant. The lecture leans on **Recital 12** to unpack the definition of an AI system. So if a question references a recital, treat it as official interpretation, not enforceable rule.

**Annex.** A list attached to the end of the Act, also binding. **Annex I** lists existing EU product-safety laws (toys, machinery, medical devices, and so on). **Annex III** lists the eight areas where standalone AI is high-risk (employment, education, and so on). **Annex IV** lists what technical documentation must contain. You do not memorise annex contents word for word, but you must know what each annex is *for*.

**Provider vs deployer.** The **provider** is whoever develops the AI system (or has it developed) and puts it on the market under their name — think the company that builds and ships the model. The **deployer** is whoever uses it under their own authority in the course of their activity — for example, a hospital running a diagnostic tool, or an HR department running a CV-screener. Most heavy obligations fall on the *provider*. The older drafts and some materials say "user" where the final text says "deployer"; treat them as the same role. (The slide on Article 13 flags exactly this change in wording.)

**Placing on the market / putting into service / making available.** Legal triggers for when obligations bite. "Placing on the market" means the first time the system is made available in the EU. "Putting into service" means supplying it for first use for its intended purpose. The detail to remember: Article 5 prohibits "placing on the market, putting into service, **or** use." Some other prohibitions only catch "placing on the market." That difference matters — see the biometric-categorisation point below, where the lecture notes you can still *sell* a banned-style system to non-EU countries because only the EU-market act is caught.

**Natural person vs legal person.** A **natural person** is a human being. A **legal person** is a company or other organisation. The Act's fundamental-rights protections are about natural persons.

**Fundamental rights.** Rights guaranteed by the EU Charter of Fundamental Rights — privacy, non-discrimination, human dignity, freedom of expression, and so on. The Act repeatedly says its goal is to protect "health, safety **or** fundamental rights." That three-part phrase is the recurring measuring stick for risk, so it is worth memorising as a unit.

**Conformity assessment / CE marking / notified body.** Borrowed from EU product-safety law. **Conformity assessment** is the procedure for checking a product meets the legal requirements before it is sold. If it passes, the maker affixes a **CE marking** (the "CE" logo you see on electronics) to signal compliance. A **notified body** is an independent organisation officially designated to perform that assessment for certain products ("third-party conformity assessment" means an outside body checks it, not just the maker). High-risk AI plugs into this machinery.

**Ex ante vs ex post.** **Ex ante** = before the fact (rules you must satisfy *before* you ship). **Ex post** = after the fact (liability or penalties *after* something goes wrong). The AI Act is mostly ex ante: it front-loads obligations onto the design and release stage.

**Horizontal regulation.** A law that cuts across all sectors rather than targeting one industry. The AI Act is horizontal: the same risk framework applies to AI in healthcare, hiring, banking, policing, and toys. Hupont et al. stress this — it is why documentation standards have to be generic enough to fit any sector.

**Derogation / exemption / "without prejudice to."** A **derogation** or **exemption** is a carve-out from a rule. "**Without prejudice to** [other law]" means "this provision does not override or weaken that other law" — both apply. You will see this with the regulatory sandbox: operating in a sandbox is "without prejudice to" the GDPR, so data-protection law still applies in full.

**Delegated act.** A power the Act gives the European Commission to update technical details (like amending an annex) later, without reopening the whole law. Keep this in mind: the lists are not frozen; the Commission can add or remove items.

**GDPR and "special categories of personal data."** The GDPR is the EU's data-protection law. "**Special categories**" are sensitive data — race, health, sexual orientation, political opinions, and so on — which get extra protection. Article 10 of the AI Act lets providers process such data *exceptionally* to detect and fix bias, under strict safeguards. The point for the exam: the AI Act does not switch off the GDPR; they stack.

That is the toolkit. Now the substance.

> **Recall check (vocabulary):** Without looking — what is the difference between a Regulation and a Directive? Who is the "provider" versus the "deployer"? What three things does the Act repeatedly say it protects? What does "without prejudice to" mean?

---

## Part 1 — What counts as an "AI system" at all? (Article 3(1))

Before you can sort AI into risk boxes, you need to know what is even *in scope*. That is the definition in **Article 3(1)**. The exact wording matters because the exam quotes it back at you with subtle changes.

The definition (final text, as shown on the lecture slide):

> An **AI system** is *a machine-based system that is designed to operate with varying levels of autonomy and that may exhibit adaptiveness after deployment, and that, for explicit or implicit objectives, infers, from the input it receives, how to generate outputs such as predictions, content, recommendations, or decisions that can influence physical or virtual environments.*

Break it into its working parts, because Recital 12 (the interpretive paragraph) singles out exactly these:

- **Machine-based.** It runs on hardware and software. This is doing very little work in the definition — almost everything is machine-based.
- **Varying levels of autonomy.** It has *some* degree of independence from human involvement. Not full autonomy — "varying levels," so even a system with a human closely in the loop can qualify.
- **May exhibit adaptiveness after deployment.** It *may* keep learning or changing once in use. Note the word "may" — adaptiveness is optional, not required. A frozen model that never updates still counts.
- **Infers how to generate outputs.** This is the load-bearing word. Recital 12 calls the **capability to infer** the *key characteristic* that distinguishes AI from ordinary software. "Infer" means the system derives outputs (or derives models/rules) from inputs, rather than executing a fixed set of human-written rules. This is the line the drafters drew to *exclude* traditional software: a plain rules-based program that just runs the instructions a human typed in is meant to fall outside.
- **Explicit or implicit objectives.** It pursues goals, whether the goal was hand-coded (explicit) or emerged from training (implicit). Recital 12 also notes these objectives can differ from the system's intended *purpose* in a given deployment.
- **Outputs: predictions, content, recommendations, or decisions.** A deliberately broad list. "Content" is what pulls generative AI (text, image, audio models) firmly into scope.
- **That can influence physical or virtual environments.** The output has to *do* something in the world — affect a person, a process, a digital environment.

**Why this matters for the exam.** A question (mock Q5) gives you four candidate "features of the definition." Three are plausible traps: that the system must use deep neural networks, must be trained on personal data, or must operate fully autonomously with no human involvement. All three are *false* — the definition is deliberately technology-neutral (no mention of neural networks), says nothing about personal data, and says "varying levels of autonomy," not "fully autonomous." The correct feature is the one about *inferring from input how to generate outputs*. The lesson: the definition is broad and method-agnostic on purpose, and the distinguishing feature is inference, not any particular technique.

**The criticism the lecture invites (and the seminar runs on).** The slides literally ask you: *which two or three words are too vague for a good definition, and does it distinguish AI from traditional software clearly enough?* Good candidate weak spots to have an opinion on:

- "**Varying levels of autonomy**" — how much autonomy is enough? A thermostat has *some*. Where is the floor?
- "**Infers**" — the supposed bright line, but lots of conventional statistical software "infers" outputs from inputs. Does a linear regression infer? The boundary with ordinary software is fuzzy in practice, even though Recital 12 tries to exclude "systems based on the rules defined solely by natural persons to automatically execute operations."
- "**May exhibit adaptiveness**" — since it is optional, it adds nothing to the test; it just describes a possibility.

You do not need the "right" answer here — there isn't one — but the course explicitly trains you to *argue* about drafting quality, and being able to name a vague term and say *why* it is vague is exactly the Part B skill.

> **Recall check (definition):** Recite the five or six components of the Article 3(1) definition. Which single word does Recital 12 call the "key characteristic" that separates AI from ordinary software? Name two words critics call too vague and say why.

---

## Part 2 — The core logic: "use case = risk"

Here is the philosophical spine of the whole Act, and it is worth understanding deeply because it generates several exam questions and most of the critique.

The Act does not regulate AI *technologies*. It regulates AI *uses*. The slide states it bluntly: **use cases = risk.** A facial-recognition model is not "high-risk" in the abstract; it depends on what it is deployed to do. Use it to unlock your own phone, and it is minimal risk. Use it to decide who gets hired, and you are in high-risk territory. Use it to build a mass surveillance database by scraping the internet, and you are in *banned* territory.

This flows from the Act's stated ambition (from the Explanatory Memorandum the lecture quotes): a "**balanced and proportionate horizontal regulatory approach... limited to the minimum necessary requirements to address the risks... without unduly constraining or hindering technological development.**" Read that as: regulate the danger, not the tool, and try not to strangle innovation. The Act calls itself a "proportionate **risk-based approach**" with a "future-proof definition of AI."

Two consequences to file away:

- **It is proportionate by design.** Heavier rules attach only where the stakes (to health, safety, fundamental rights) are higher. That is the justification for the pyramid.
- **It tries to be future-proof.** By regulating uses and writing a technology-neutral definition, the drafters hoped the Act would survive new techniques. Whether it actually does is the debate in later lectures.

**The standard critique to hold ready.** Tying risk to the *use case* sounds elegant but creates real problems, and the lecture's reflection questions push on these:

- Does the law adequately separate "the risk posed by the *system*" from "the risk posed by its *deployment context*"? A genuinely flawed model in a low-stakes use might escape, while a fine model in a high-stakes use gets the full burden.
- How do you keep a risk classification meaningful when a system gets **repurposed**? You classify on intended use, but users repurpose tools constantly.
- General-purpose models (LLMs) have *no single intended purpose*, which breaks the use-case logic entirely. The Act had to bolt on a separate regime for them (Lecture 3). The slides flag this as the "little problem."

> **Recall check (logic):** In one sentence, what does the Act regulate — technologies or uses? Give one example of the same model being minimal risk in one use and high risk in another. Name one weakness of tying risk to the use case.

---

## Part 3 — Tier 1: Prohibited AI (Article 5)

This is the top of the pyramid: uses considered so harmful, or so contrary to EU values, that they are simply **banned**. No compliance route, no documentation that makes them okay. Article 5 is a closed list of practices.

A structural point first, because it is a favourite distractor: most of these prohibitions catch "the **placing on the market, putting into service, or use**" of the system. The verbs matter. Where a prohibition only mentions "placing on the market," the *act of putting it on the EU market* is what is banned, which (as the lecturer notes for biometric categorisation) can leave gaps — for example, selling such a system to a buyer *outside* the EU may not be caught.

Here are the prohibitions. Learn the *idea* of each plus its one tricky feature.

**(a) Subliminal, manipulative, or deceptive techniques.** Bans AI that uses techniques below conscious awareness, or purposefully manipulative or deceptive techniques, that *materially distort* behaviour by appreciably impairing someone's ability to make an informed decision, causing them to take a decision they would not otherwise have taken, in a way that causes or is likely to cause **significant harm**.
- *Tricky features the lecture highlights:* (i) **You do not need intent.** The text catches techniques with "the objective, **or the effect**" of distorting behaviour — so an effect is enough, intent is not required. (ii) There must be **significant harm** — minor nudging is not banned. (iii) "Manipulation" is left undefined, which is the drafting weakness to flag.

**(b) Exploiting vulnerabilities.** Bans AI that exploits vulnerabilities due to **age, disability, or a specific social or economic situation** to materially distort behaviour and cause significant harm.
- *Tricky feature:* the **Unfair Commercial Practices Directive** already bans exploiting vulnerabilities for *commercial* ends; the AI Act extends the idea to *non-commercial* ends too. So this overlaps with existing consumer law (an overlap worth naming in a critique).

**(c) Social scoring.** Bans AI that evaluates or classifies people over time based on social behaviour or personal characteristics, where the resulting **social score** leads to **(i)** detrimental treatment in contexts unrelated to where the data was collected, or **(ii)** detrimental treatment that is unjustified or disproportionate to the behaviour.
- *Tricky features:* it is not "any scoring" — it needs the score-to-mistreatment link, and either the cross-context unfairness or the disproportionality. This is the "China-style social credit" prohibition, but written to also catch private actors. Mock Q7's correct answer is this one: *social scoring leading to detrimental or disproportionate treatment.*

**(d) Predictive policing of individuals.** Bans AI that assesses or predicts the risk of a person committing a crime based **solely** on profiling or personality traits.
- *Tricky feature:* the word **solely**. If the AI merely *supports* a human assessment that is already grounded in objective, verifiable facts linked to criminal activity, it is allowed. So pure profiling-based prediction is out; human-led, fact-based risk assessment with AI support is in.

**(e) Untargeted facial-recognition scraping.** Bans creating or expanding facial-recognition databases by **untargeted scraping** of facial images from the internet or CCTV. (This is the "Clearview AI" prohibition.)

**(f) Emotion recognition at work and school.** Bans AI that infers emotions in the **workplace and education** settings — except for **medical or safety** reasons.
- *Tricky feature:* the ban is location-specific (work and school) and has a medical/safety exception. Emotion recognition elsewhere is not banned by this point.

**(g) Biometric categorisation of sensitive traits.** Bans biometric categorisation that deduces or infers **race, political opinions, trade-union membership, religious or philosophical beliefs, sex life, or sexual orientation**.
- *Tricky features:* it does **not** cover labelling or filtering of *lawfully acquired* biometric datasets, or categorisation in the law-enforcement context. And as noted above, it bans "placing on the market" for this purpose — the lecturer's point that you could still sell such systems to non-EU countries.

**(h) Real-time remote biometric identification (RBI) in public, for law enforcement.** Bans live facial recognition in publicly accessible spaces by police — **unless** strictly necessary for one of three narrow objectives: (i) targeted search for victims of abduction/trafficking/sexual exploitation or missing persons; (ii) preventing a specific, substantial, imminent threat to life or a foreseeable terrorist attack; (iii) locating/identifying a suspect for serious crimes (those in Annex II, punishable by at least four years).
- *Tricky features:* this is the most heavily conditioned prohibition. Even the exceptions require **prior authorisation** by a judicial or independent authority, a **fundamental-rights impact assessment**, registration in an EU database, and tight temporal/geographic/personal limits. The slide also flags an unresolved ambiguity: **what counts as "real-time"?** Ten seconds? Two minutes? The lecturer's point is that "minor delays" should not let a system escape the ban by claiming it is no longer real-time.

**The two newly added prohibitions (lecture update).** The slides mark these as added by the "Digital Omnibus on AI" (a later legislative package; on the slides it is a provisional agreement of 6 May 2026, pending formal adoption). Know them because mock Q8 tests exactly this:

- **Non-consensual intimate imagery ("nudifier" apps)** — AI that generates or manipulates realistic intimate imagery of an identifiable person without consent. (New Art 5(1)(ba).)
- **AI-generated child sexual abuse material (CSAM)** — including wholly or partially synthetic material. (New Art 5(1)(bb).)

So if asked "which prohibition was *newly added*," the answer is the nudifier-apps-and-AI-CSAM pair, not recommender systems or spam filters (those are not prohibited at all).

**Penalty for breaching Article 5.** This is the heaviest band: under **Article 99(3)**, fines up to **€35 million or 7% of total worldwide annual turnover, whichever is higher**. ("Turnover" = total revenue. "Whichever is higher" means for a large company the percentage usually bites harder than the flat figure.) This is mock Q9's answer. Keep the bands straight — see Part 8.

**When the ban applies.** The Act was published in the Official Journal in July 2024 and entered into force on 1 August 2024. The prohibitions are the first obligations to bite. (The lecture slides, updated for the Digital Omnibus, place the start of the Article 5 ban at **2 December 2026**. Be aware that the *original* AI Act timed prohibitions to 2 February 2025; for the exam, follow the lecture's stated date, but do not lose sleep over it — the mock exam tests the *content* of the prohibitions and the *fine band*, not the calendar.)

> **Recall check (Article 5):** List as many of the prohibited practices as you can from memory (aim for six of the eight). For (a), do you need intent? For (d), what does "solely" do? For (h), name one of the three law-enforcement exceptions and one safeguard. Which two prohibitions were newly added? What is the fine band, and which Article sets it?

---

## Part 4 — Tier 2: High-risk AI — getting *into* the box (Article 6)

High-risk is where most of the lecture's detail sits, because these systems are *allowed* but carry a heavy compliance load. First you need to know **how a system becomes high-risk**. There are two routes.

**Route 1 — the product-safety route (Article 6(1), via Annex I).** An AI system is high-risk if **both**: (a) it is a safety component of a product, *or* is itself a product, covered by the EU product-safety laws listed in **Annex I** (toys, machinery, medical devices, lifts, and so on); **and** (b) that product must undergo **third-party conformity assessment** under that legislation. In plain terms: AI baked into things that already need an independent safety check (like a medical device) is high-risk. The lecturer's shorthand: "products already covered by certain Union health and safety harmonisation legislation."

A useful refinement the slides flag from the Digital Omnibus: the definition of "safety component" was tightened. AI used **solely** for user assistance, performance optimisation, efficiency, automation, convenience, or quality control does **not** count as a safety component *unless* its failure would endanger health or safety. That narrows what gets pulled in by Route 1.

**Route 2 — the standalone route (Article 6(2), via Annex III).** AI listed in **Annex III** is high-risk even when it is not part of a regulated product. Annex III is eight fixed areas. Know all eight — they are very examinable:

1. **Biometrics** (insofar as permitted under EU/national law).
2. **Critical infrastructure** (digital infrastructure, road traffic, supply of water, gas, heating, electricity).
3. **Education and vocational training.**
4. **Employment**, worker management, and access to self-employment.
5. **Access to essential private and public services and benefits** (for example credit scoring, social benefits, emergency services).
6. **Law enforcement** (insofar as permitted under EU/national law).
7. **Migration, asylum, and border control** (insofar as permitted).
8. **Administration of justice and democratic processes.**

A memory hook: these are all places where an automated decision can seriously change a person's life chances — your job, your school place, your loan, your liberty, your right to stay in the country. That "life-chances" theme is the through-line.

**The escape hatch — Article 6(3).** This is the most exam-relevant subtlety, and mock Q11 turns on it. Even if a system falls *within* an Annex III area, it is **not** high-risk if it does **not pose a significant risk of harm** to health, safety, or fundamental rights — in particular because it does not materially influence the outcome of a decision. The Act gives four qualifying situations:

- (a) it performs a **narrow procedural task**;
- (b) it improves the result of a **previously completed human activity**;
- (c) it detects decision-making patterns or deviations and is **not meant to replace or influence** the human assessment without proper human review;
- (d) it performs a **preparatory task** to an assessment.

**But** there is a hard override: an Annex III system is **always high-risk if it performs profiling of natural persons**, no matter what.

Two more things on Article 6(3) that distinguish the real rule from near-misses:

- It is a **self-assessment**. The *provider* decides their Annex III system is not high-risk, but must **document** that assessment beforehand and register it, and hand the documentation over on request. The slides flag the obvious worry: letting the regulated party self-certify its way out of the regime is an enforcement soft spot.
- Watch the wrong answers in mock Q11: a system is **not** exempted merely because it was developed outside the EU, because its provider is an SME, or because it is open-source. Those are all distractors. The only thing that exempts is *not posing a significant risk*.

> **Recall check (Article 6):** What are the two routes into high-risk, and which annex does each use? Name at least six of the eight Annex III areas. Under Article 6(3), give two of the four "not significant risk" situations — and name the one thing that *always* makes an Annex III system high-risk regardless. Who performs the 6(3) assessment, and why is that controversial?

---

## Part 5 — High-risk obligations: what providers must actually do (Articles 8–15)

Once a system is high-risk, Section 2 of Chapter III loads obligations onto it. The lecture organises these as "obligations on providers, Articles 9 to 15." Article 8 is the umbrella ("comply with all the requirements in this Section, taking into account intended purpose and the state of the art"). Then each article is one requirement. Learn them as a numbered set — the exam tests whether you can match the article number to the right requirement and spot a wrong description.

I will give each one in the lecturer's framing, then the detail that lets you beat a near-miss answer.

### Article 9 — Risk management system
A **continuous, iterative process run across the entire lifecycle** of the system, with regular review and updating. It identifies and analyses known and foreseeable risks (in intended use *and* reasonably foreseeable misuse), estimates and evaluates them, folds in data from post-market monitoring, and adopts targeted mitigation measures until the **residual risk** is judged acceptable.
- *Beat-the-trap detail:* the killer word is **continuous / lifecycle**. The classic wrong answer (mock Q12) describes it as a *one-off assessment done once before market placement*. That is exactly what it is **not**. It is also not voluntary, and not limited to GPAI providers. Risk management here is ongoing.
- *Note:* providers must give special consideration to adverse impacts on under-18s and other vulnerable groups.

### Article 10 — Data and data governance
Training, validation, and testing datasets must meet **quality criteria** and sit inside proper data-governance practices (documenting design choices, collection, labelling, assumptions, bias examination and mitigation, data gaps). The headline standard in Article 10(3): datasets shall be **relevant, sufficiently representative, and to the best extent possible free of errors and complete** in view of the intended purpose, with appropriate statistical properties for the people the system targets.
- *Beat-the-trap detail:* note the phrase "**to the best extent possible**." An earlier draft reportedly demanded datasets simply "free of errors," which data scientists called impossible — no real dataset is error-free. The softened wording is more realistic but, as Schrepel argues in a later reading, still vague enough to invite litigation over what "sufficiently representative" or "best extent possible" mean. So the correct characterisation is "improved over the unrealistic original, but still vague," not "fully precise" and not "requires zero errors."
- *Bias-data carve-out:* Article 10(5) lets providers process **special categories of personal data** (sensitive data) *exceptionally* to detect and correct bias, under strict GDPR-style safeguards. The AI Act does not override the GDPR; they apply together.

### Article 11 — Technical documentation
Before going to market, the provider draws up **technical documentation** proving compliance, containing at least the elements in **Annex IV**, and keeps it up to date so authorities and notified bodies can assess conformity.
- *Beat-the-trap detail (mock Q14):* the only SME-specific relief in the whole high-risk regime is here — **SMEs and start-ups may provide the documentation in a simplified form**, using a Commission-provided template. Schrepel's characterisation: this is the *sole* SME accommodation among the high-risk requirements and is probably *insufficient* to prevent the rules distorting the market against smaller players. So the right answer is "simplified form for SMEs; only relief; likely not enough" — not "SMEs are fully exempt" and not "SMEs face stricter duties."

### Article 12 — Record-keeping
The system must **automatically log events** over its lifetime, so its operation is **traceable** — to spot situations that create risk, to support post-market monitoring, and (for certain biometric systems) to record each use, the reference database, matches, and who verified results.
- *Beat-the-trap detail:* the lecturer frames the goal as **traceability / transparency, not full explainability**. Logging is about being able to reconstruct what happened, not about making the model's internal reasoning interpretable. Do not conflate Article 12 logging with explainable AI.

### Article 13 — Transparency and provision of information to deployers
The system must be **transparent enough to let deployers interpret its output and use it appropriately**, and must ship with clear **instructions for use** covering the provider's identity, the system's capabilities and limitations, its accuracy/robustness/cybersecurity levels, foreseeable risks, human-oversight measures, expected lifetime, and so on.
- *Beat-the-trap detail:* note the audience. The final text says transparency **to deployers** (the professional users running the system). The slide flags that an earlier draft said "to enable **users**" — the wording shifted from "users" to "deployers." Article 13 is about giving the operating organisation what it needs to use the tool correctly; it is not a general public-facing transparency duty (that is Article 50, the limited-risk tier).

### Article 14 — Human oversight
The system must be **designed so natural persons can effectively oversee it** while in use, through appropriate **human-machine interface tools**. Oversight must let the assigned humans understand the system's capabilities and limits, **stay aware of automation bias** (the tendency to over-trust automated output), correctly interpret output, decide **not to use or to override** the output, and **intervene or stop** the system (a "stop button" or safe-halt).
- *Beat-the-trap detail:* "**automation bias**" is the named risk — humans rubber-stamping the machine. And for certain biometric identification systems (Annex III point 1(a)), there is a **two-person rule**: no action on an identification unless at least two competent people separately verify it (with a carve-out where Union/national law deems that disproportionate for law enforcement, migration, border, asylum). The slide also notes the wording shifted from "enable users to interpret" toward "human-machine interface tools" ensuring systems "can be effectively overseen by a natural person."

### Article 15 — Accuracy, robustness, and cybersecurity
The system must achieve and maintain, across its lifecycle, an **appropriate level of accuracy, robustness, and cybersecurity**, performing consistently. Accuracy levels and metrics go in the instructions for use. Robustness can use redundancy and fail-safes; systems that keep learning must guard against **feedback loops** (biased outputs feeding back into inputs). Cybersecurity must address AI-specific attacks — **data poisoning, model poisoning, adversarial examples, model evasion**, confidentiality attacks, and model flaws.
- *Beat-the-trap detail (mock Q15):* the trio to memorise is **accuracy, robustness, cybersecurity**. The wrong answers swap in things the Act never requires here: open-source licensing/public weights, energy-efficiency certification by a notified body, or profitability. Those are not Article 15. Also note the word "**appropriate**" — the level is proportionate to the system, not an absolute "100% accurate."

A pattern across 9–15 worth internalising: these are mostly **process and documentation** duties (manage risk, govern data, document, log, inform, oversee, test), enforced **ex ante** through conformity assessment. The Act tells you the *goals* but largely leaves the *technical how* to future standards — which is precisely the gap Hupont et al. study (Part 10).

> **Recall check (Articles 9–15):** Match each article number 9 through 15 to its one-line requirement, from memory. Which article's defining word is "continuous/lifecycle"? Which contains the only SME relief in the high-risk regime? Which names "automation bias"? Which lists data poisoning and adversarial examples? For Article 10, what does "to the best extent possible" soften?

---

## Part 6 — Tier 3: Limited risk — the transparency tier (Article 50)

Below high-risk sits **limited risk**, which the Act actually labels "**certain AI systems**." These are not dangerous enough to need the full high-risk machinery, but they share one trait: people might not realise they are dealing with AI. So the obligation is essentially **transparency / disclosure**.

What falls here (Article 50, per the slide):

1. **Chatbots, emotion-recognition systems, and biometric categorisation systems** — tell people they are interacting with, or being processed by, an AI.
2. **AI that generates synthetic audio, image, video, or text content, and deepfakes** — label it as artificially generated or manipulated. With **exceptions for artistic and creative uses**.
3. **Systems producing public-interest information for the public** — disclosure obligations.

The core duty: **users must be informed when they are interacting with an AI system or its outputs, especially where that is not obvious from the context.** A deepfake must be flagged as synthetic; a chatbot must announce it is a bot.

- *Beat-the-trap detail (mock Q16):* limited risk = **transparency obligations**, full stop. The wrong answers attach high-risk machinery (full conformity assessment and CE marking), the systemic-risk regime (that is GPAI, Lecture 3), or a complete ban (that is Article 5). None of those apply here.
- *Reflection the slide raises:* is "just tell people it's AI" an effective combination of **law + social norms**? The disclosure works only if people read and act on the label. This ties back to Lecture 1's idea that law shapes behaviour partly by reinforcing norms, not just by command.

**Penalty.** Breaching the transparency obligations falls under **Article 99(4)**: up to **€15 million or 3% of worldwide turnover**, whichever is higher — the same band as high-risk obligations, not the heavier Article 5 band.

> **Recall check (Article 50):** What is the single defining obligation of the limited-risk tier? Give two example systems that fall here. What is the exception for synthetic content? Which fine band applies?

---

## Part 7 — Tier 4: Minimal / no risk — and codes of conduct (Article 95)

The bottom of the pyramid is **everything else** — the overwhelming majority of AI (spam filters, recommendation engines outside special contexts, AI in video games, inventory forecasting, and so on). The Act imposes **no mandatory obligations** on these systems.

Instead, **Article 95** has the AI Office and member states **encourage and facilitate voluntary codes of conduct**, so that providers of non-high-risk systems can *choose* to apply some or all of the high-risk-style requirements. Note the soft verbs: the Commission "**encourages**" and "**facilitates**." Nothing is compulsory here.

- *The point for the exam:* minimal risk = no binding rules, just voluntary codes. Do not confuse this with limited risk (which has binding *transparency* duties). The four tiers, in order, are **unacceptable, high, limited, minimal** (mock Q6) — get that ordering and the labels exactly right, because the wrong answers offer plausible-sounding alternatives like "systemic / high / medium / low" or "critical / serious / moderate / negligible." Those are made up.

> **Recall check (minimal risk):** What obligations does minimal-risk AI carry? What does Article 95 do, and how binding is it? Recite the four tier names in order.

---

## Part 8 — Penalties: keep the three bands straight (Article 99)

Fines are a reliable exam target because there are three bands and it is easy to mix them up. Memorise them as a descending ladder tied to how serious the breach is:

| Band | What it covers | Maximum fine |
|---|---|---|
| **Article 99(3)** | Breaching the **Article 5 prohibitions** (unacceptable-risk AI) | **€35 million or 7%** of total worldwide annual turnover, whichever is higher |
| **Article 99(4)** | Non-compliance with **other obligations** — including the **high-risk** duties (Articles 9–15) and the **limited-risk transparency** duties (Article 50) | **€15 million or 3%** of turnover, whichever is higher |
| **Article 99(5)** | Supplying **incorrect, incomplete, or misleading information** to authorities/notified bodies | **€7.5 million or 1%** of turnover, whichever is higher |

How this maps to the mock exam: Q9 (Article 5 breach) → €35M/7% under 99(3). Q10 (high-risk breach) → €15M/3% under 99(4). The trap in Q10 is option B, which offers the €35M/7% figure — correct for prohibitions, wrong for high-risk. Anchor it: **prohibitions are the worst sin, so they get the biggest fine (7%); everything else operational is the middle band (3%); lying to the regulator is the smallest band (1%).**

> **Recall check (penalties):** Without the table — which article and which fine band for an Article 5 breach? For a high-risk obligations breach? For misleading the authorities? Which band do limited-risk transparency breaches fall into?

---

## Part 9 — Timeline: staggered entry into application

The Act entered into **force** on 1 August 2024, but its obligations switch on in stages (the "entry into application"). You do not need every date, but understand the *staggering* and its logic: the most dangerous things are banned first, the heaviest compliance loads get the longest runway.

Per the lecture slides (updated for the Digital Omnibus, "pending formal adoption"):

- **Prohibitions (Article 5):** apply from **2 December 2026**.
- **High-risk via Annex III / Article 6(2)** (employment, education, biometrics, law enforcement, and so on): from **2 December 2027**.
- **High-risk via Annex I / Article 6(1)** (products: medical devices, machinery, and so on): from **2 August 2028** — the longest runway, because it has to mesh with existing product-safety cycles.
- **Limited-risk transparency:** providers who placed generative systems on the market before **2 August 2026** have until **2 December 2026** to comply.

(Reality check for your own orientation, not for the exam answer: the original AI Act timed prohibitions to Feb 2025, GPAI rules to Aug 2025, Annex III high-risk to Aug 2026, and Annex I high-risk to Aug 2027. The lecture's dates reflect the later Digital Omnibus changes. **Follow the lecture's dates if a date question appears**, since the manual says you are tested on lecture content. But note that the mock exam does not actually test these dates — it tests the tiers, the obligations, and the fines.)

> **Recall check (timeline):** In what order do the four things switch on (prohibitions, Annex III high-risk, Annex I high-risk, transparency)? Why does product-embedded high-risk AI get the longest runway?

---

## Part 10 — The reading: Hupont et al., *Documenting High-Risk AI* (IEEE, 2023)

This is the mandatory reading paired with the lecture, and it gets at least one direct exam question (mock Q24) plus it reinforces the documentation duties in Articles 11 and 13. Read it as the bridge between *law* (the Act says "document this") and *practice* (what tools exist to actually do the documenting). The authors are European Commission Joint Research Centre researchers.

**The core question of the paper.** The AI Act sets *high-level transparency requirements* but deliberately does **not** mandate specific technical solutions — those will come later as **technical standards**. So Hupont et al. ask: do the **existing, voluntary AI-documentation practices** that industry and academia already invented cover what the Act will require, and could they evolve into the formal standards that operationalise it?

**Two transparency requirements, two audiences.** They focus on a subset of the Act's requirements, split by recipient:
1. **Instructions for use → for users/deployers** (Article 13): concise, accessible information so the operator can use the system properly.
2. **Technical documentation → for authorities and conformity-assessment bodies** (Article 11, Annex IV): comprehensive proof of full compliance.
The same information often appears in both, but at different depth — users get the accessible version, authorities get the detailed metrics-and-methods version.

**The risk tiers, restated.** The paper restates the four levels (unacceptable, high, limited, minimal) and shows graphically that **documentation obligations are heaviest for high-risk systems** and (in their figure) heavier for the authorities-facing technical documentation than for the user-facing instructions. Unacceptable-risk AI gets a red X — it is banned, so documentation is moot.

**The six documentation approaches they assess** (this is mock Q24's answer set — know the names). Three are dataset-focused, two are system/model-focused, one is a classification framework:
- **Datasheets for Datasets** (Gebru et al., 2018) — a questionnaire about a dataset's origin, composition, collection, and uses.
- **The Dataset Nutrition Label** (Holland/Chmielinski et al.) — a visual, food-label-style summary of a dataset.
- **Accountability for Machine Learning Datasets** (Hutchinson et al.) — a software-engineering-style template for dataset accountability.
- **Model Cards** (Mitchell et al., 2019) — short documents reporting a model's intended use and performance, notably **disaggregated** (broken down by subgroup).
- **AI FactSheets** (Arnold et al., IBM) — template-based "supplier's declarations of conformity" for AI services.
- **OECD Framework for the Classification of AI Systems** (2022) — an intergovernmental classification tool.

If a question lists "privacy notices and cookie banners," "CE markings and customs declarations," or "source-code escrow and patent filings," those are distractors. The real set is **Datasheets for Datasets, Dataset Nutrition Label, Model Cards, and AI FactSheets** (plus the Hutchinson template and the OECD framework).

**Their method.** Five Commission AI experts used a **Delphi method** — a structured process where experts independently rate, then disagreements are surfaced and discussed until consensus. They scored each approach's **coverage** (does it address the requirement at all?) and **depth** (how thoroughly?), using a colour scheme (white = low, yellow = medium, green = high, X = not covered). One Delphi round was enough to reach consensus.

**Their findings (the takeaways most likely to be tested or to anchor a Part B / reflection answer):**
- **Dataset documentation is in good shape.** All three dataset approaches give in-depth coverage of the Act's data-related needs; **Datasheets for Datasets is the most complete** overall. Gaps remain on data *correctness*, *representativeness*, and *privacy*, especially the concrete metrics authorities would want.
- **System documentation is also broadly covered but shallower.** **AI FactSheets is the most complete** for AI systems, taking a whole-lifecycle, system-and-service view. **Model Cards** stand out for **disaggregated performance reporting** (results broken out by relevant subgroups), which the experts rated very effective.
- **The big gap:** current approaches do **not** reach the technical depth authorities and conformity-assessment bodies need — they were built mostly to give *users* concise, accessible information, and adopters often link out to papers and code rather than embedding full detail. They are, in their words, a "solid and useful basis" that could, with moderate effort, be extended and **evolve into formal standards** supporting the Act.
- **Why some elements were hard to score:** items like risk mitigation, data representativeness, and privacy safeguards are *subjective* and need careful definition — a hint at how much interpretive work standard-setters still face.

The one-sentence version to carry into the exam: *existing voluntary documentation tools already cover much of what the Act wants for users, are strongest on datasets, but lack the technical depth authorities need — yet they are a credible foundation for future standards.*

> **Recall check (Hupont):** What is the paper's central question? Name the four most-cited documentation approaches. Which is most complete for datasets? Which for systems? What is Model Cards' standout strength? What is the main shortfall the authors identify, and for whom?

---

## Part 11 — The cliffhanger: general-purpose AI breaks the model

End the lecture knowing why the next one exists. The whole risk-based system depends on classifying by **intended use**. But **general-purpose AI (GPAI)** — large language models and similar foundation models — has **no single intended purpose**; the same model writes poems, drafts code, and answers medical questions. You cannot slot "an LLM" into one box of the pyramid. The slides call this the "little problem" and send you to **Lecture 3 (the capabilities approach)**, where the Act bolts on a separate regime that classifies GPAI by *capability and compute* rather than by use case. You do not need GPAI detail for Lecture 2 — just be able to say *why* the use-case logic fails for foundation models.

> **Recall check:** In one sentence, why does the risk-based, use-case approach struggle with LLMs?

---

## Part 12 — How to crush the Part B "rewrite" questions

Part B (mock Q28–30) shows you a clumsy real provision and four rewrites; you pick the best. These all draw on Lecture 2 provisions (manipulation in Article 5, data quality in Article 10, human oversight in Article 14). There is a reliable method, because the exam tells you the winning criteria up front: *a good rewrite is **clearer** than the original while staying **proportional** to the provision's objective and **consistent** with the rest of the regulation.*

Run every option through three filters, and eliminate:

1. **Too vague to do any work.** A rewrite like "Prohibited: AI systems that are manipulative" or "Datasets shall be appropriate" is clearer to *read* but useless to *apply* — it has no operable test. Reject. (This kills Q28 option B and Q29 option B.)
2. **Disproportionate — over- or under-shoots the objective.** "Prohibited: any AI system that influences a user's behaviour" bans everything (all advertising, all UX) — overshoots. "Datasets shall be completely free of all errors" demands the impossible — overshoots and is unrealistic. "Prohibited only where the provider expressly admits an intention to cause harm" guts the rule (the real provision deliberately needs no intent) — undershoots. "A human must individually approve every single output" makes high-risk AI unusable at scale — overshoots the human-oversight goal. Reject all of these. (Kills Q28 C and D, Q29 A and C, Q30 D.)
3. **Inconsistent with the rest of the Act.** A rewrite that contradicts a definition or standard used elsewhere is out. "Datasets may contain whatever data the provider chooses" contradicts the entire data-governance regime. Reject. (Kills Q29 C.)

The survivor is the rewrite that is **precise enough to apply, faithful to the objective, and consistent with the Act's existing concepts**:

- **Q28 (manipulation, Article 5) → A:** keeps the no-intent design ("objective **or** effect"-style breadth via "appreciably impair... and thereby cause, or are likely to cause, significant harm"), names a workable test, and preserves the "significant harm" threshold. It protects autonomy without banning all influence.
- **Q29 (data quality, Article 10) → D:** keeps "relevant and sufficiently representative," ties it to "the persons and contexts of the intended purpose," and replaces the impossible "free of errors" with "**reasonable, documented measures to detect and reduce errors**" — realistic and proportionate to the non-discrimination objective.
- **Q30 (human oversight, Article 14) → A:** gives the overseer "competence, authority and means" to monitor, interpret, and **decide not to use or override** the output — effective control that is workable across many systems, rather than the unworkable "approve every output."

The meta-lesson: in Part B, the most *minimal* and *readable* option is usually a trap (too vague), and the most *aggressive* option is usually a trap (disproportionate). The answer is the carefully-scoped middle one that you could actually hand to an engineer and a regulator and have both know what to do.

> **Recall check (Part B):** State the three winning criteria for a rewrite. For each, name the failure mode it screens out. Why is the shortest, simplest rewrite usually wrong?

---

## One-page cheat sheet (cover everything above; reconstruct this from memory)

**The pyramid (top = most regulated):**

| Tier | Trigger | Key article(s) | Obligation | Max fine |
|---|---|---|---|---|
| **Unacceptable** | Banned uses (manipulation, social scoring, untargeted face-scraping, real-time RBI by police, etc. + new: nudifier apps, AI-CSAM) | Art 5 | Outright ban | €35M / 7% (Art 99(3)) |
| **High** | Annex I product route (Art 6(1)) **or** Annex III standalone areas (Art 6(2)); 6(3) carve-out if no significant risk | Arts 6–15 | Full compliance: risk mgmt, data governance, docs, logs, transparency to deployers, human oversight, accuracy/robustness/security | €15M / 3% (Art 99(4)) |
| **Limited** | "Certain AI systems": chatbots, deepfakes/synthetic content, emotion recognition, biometric categorisation | Art 50 | Transparency: disclose you're AI / label synthetic content | €15M / 3% (Art 99(4)) |
| **Minimal** | Everything else | Art 95 | None (voluntary codes of conduct) | — |

**Definition (Art 3(1)):** machine-based; varying autonomy; may adapt; **infers** from input how to generate outputs (predictions, content, recommendations, decisions); explicit/implicit objectives; influences physical/virtual environments. Key word = **infers** (Recital 12).

**Annex III eight areas:** biometrics; critical infrastructure; education; employment; essential public/private services; law enforcement; migration/asylum/borders; justice/democracy. (Theme: life chances.)

**High-risk obligations (memorise as a set):** 9 = risk management (continuous/lifecycle) · 10 = data & governance (relevant, representative, best-extent error-free) · 11 = technical documentation (Annex IV; SME simplified form) · 12 = record-keeping (automatic logs / traceability) · 13 = transparency to deployers (instructions for use) · 14 = human oversight (automation bias, stop button, 2-person rule for biometric ID) · 15 = accuracy, robustness, cybersecurity (data poisoning, adversarial examples).

**Fines ladder:** prohibitions 7% (99(3)) > other/high-risk/transparency 3% (99(4)) > misleading authorities 1% (99(5)).

**Hupont:** voluntary docs (Datasheets for Datasets, Dataset Nutrition Label, Hutchinson, Model Cards, AI FactSheets, OECD) cover much of the Act's transparency needs; strongest on datasets (Datasheets most complete) and AI FactSheets most complete for systems; Model Cards strong on disaggregated performance; but they lack the technical depth authorities need; could become formal standards.

---

## Flashcards (active recall — Q on the left, cover the answer)

Use these on the *second* day, without re-reading the guide. Struggling to recall is the point.

1. **Q:** Regulation vs Directive? **A:** Regulation applies directly and uniformly across the EU, no national transposition; Directive sets a goal each country implements in its own law. AI Act = Regulation.
2. **Q:** Provider vs deployer? **A:** Provider develops/markets the system under its name; deployer uses it under its own authority. Heavy duties fall on the provider.
3. **Q:** Article vs Recital? **A:** Articles are binding rules; Recitals are non-binding interpretive preamble used to read the Articles. Recital 12 unpacks the AI-system definition.
4. **Q:** The four tiers in order? **A:** Unacceptable, high, limited, minimal.
5. **Q:** Single key word distinguishing AI from ordinary software (Art 3(1) / Recital 12)? **A:** "Infers" (the capability to infer).
6. **Q:** Does Art 5(a) manipulation require intent? **A:** No — "objective **or** effect" of distorting behaviour; intent not required, but "significant harm" is.
7. **Q:** What does "solely" do in the predictive-policing ban (Art 5(d))? **A:** Only bans risk prediction based *solely* on profiling; AI supporting a fact-based human assessment is allowed.
8. **Q:** Two newly added Article 5 prohibitions? **A:** Non-consensual intimate imagery ("nudifier" apps) and AI-generated CSAM.
9. **Q:** Fine for breaching Article 5? **A:** Up to €35M or 7% of worldwide turnover (Art 99(3)).
10. **Q:** Two routes into high-risk? **A:** Annex I product-safety route (Art 6(1)); Annex III standalone areas (Art 6(2)).
11. **Q:** Art 6(3) — when is an Annex III system NOT high-risk? **A:** When it poses no significant risk (narrow procedural task / improves prior human activity / detects patterns without replacing human review / preparatory task) — but **always** high-risk if it profiles people. Self-assessed and documented by the provider.
12. **Q:** Which Annex III system is always high-risk regardless of 6(3)? **A:** One that performs profiling of natural persons.
13. **Q:** Article 9 defining feature? **A:** Continuous, iterative risk-management process across the whole lifecycle — not a one-off.
14. **Q:** Article 10 data standard? **A:** Relevant, sufficiently representative, and "to the best extent possible" free of errors and complete.
15. **Q:** Only SME relief in the high-risk regime, and where? **A:** Simplified technical documentation form, Article 11.
16. **Q:** Article 12 is about? **A:** Automatic logging / traceability (not full explainability).
17. **Q:** Article 13 audience? **A:** Deployers (interpret and use output appropriately) — wording shifted from "users."
18. **Q:** Article 14 named risk + special rule? **A:** Automation bias; plus stop button and a two-person verification rule for certain biometric identification.
19. **Q:** Article 15 trio? **A:** Accuracy, robustness, cybersecurity (covers data/model poisoning, adversarial examples).
20. **Q:** Limited-risk core duty + fine band? **A:** Transparency/disclosure (tell people it's AI; label deepfakes); €15M/3% (Art 99(4)).
21. **Q:** Minimal-risk obligations? **A:** None mandatory; Article 95 voluntary codes of conduct.
22. **Q:** Three fine bands? **A:** 7% prohibitions (99(3)); 3% other incl. high-risk & transparency (99(4)); 1% misleading authorities (99(5)).
23. **Q:** Hupont's four headline documentation approaches? **A:** Datasheets for Datasets, Dataset Nutrition Label, Model Cards, AI FactSheets.
24. **Q:** Hupont's main gap finding? **A:** Existing tools serve users well but lack the technical depth authorities/conformity bodies need; still a basis for future standards.
25. **Q:** Why does the use-case approach struggle with LLMs? **A:** GPAI has no single intended purpose, so it cannot be slotted into one risk tier — hence the separate GPAI regime (Lecture 3).

---

## Mock self-test (Lecture 2 questions, with worked answers)

Do this last, ideally a day or two after first reading, closed-book. These mirror the real mock's style. Answers and reasoning follow each block — cover them.

**1.** Which feature is part of the Article 3(1) definition of an AI system?
A) It must use deep neural networks. B) It must be trained on personal data. C) It infers from its input how to generate outputs such as predictions, content, recommendations, or decisions. D) It must operate fully autonomously.

**2.** The four risk tiers, correctly ordered, are:
A) Systemic, high, medium, low. B) Unacceptable, high, limited, minimal. C) Critical, serious, moderate, negligible. D) Prohibited, regulated, voluntary, exempt.

**3.** Which is prohibited outright under Article 5?
A) AI assisting medical diagnosis. B) A retail chatbot. C) CV-screening AI. D) Social scoring leading to detrimental or disproportionate treatment.

**4.** Which was *newly added* to the Article 5 list?
A) Social-media recommender systems. B) AI for marketing copy. C) Email spam filtering. D) Nudifier apps and AI-generated CSAM.

**5.** A breach of Article 5 can attract fines up to:
A) €750,000 always. B) €10M or 2%. C) €15M or 3%. D) €35M or 7%, whichever is higher.

**6.** Non-compliance with high-risk obligations (Arts 9–15) attracts fines under Art 99(4) up to:
A) No fine. B) €35M or 7%. C) €15M or 3%, whichever is higher. D) €1.5M always.

**7.** Even within an Annex III area, a system is NOT high-risk under Art 6(3) if:
A) It was developed outside the EU. B) Its provider is an SME. C) It poses no significant risk of harm (e.g. a narrow procedural task). D) It is open-source.

**8.** Article 9's risk-management system is best described as:
A) A one-off pre-market assessment. B) A voluntary code. C) An obligation only for GPAI providers. D) A continuous, iterative process across the system's whole lifecycle.

**9.** Article 15 requires high-risk systems to maintain an appropriate level of:
A) Open-source licensing. B) Accuracy, robustness, and cybersecurity. C) Energy efficiency certified by a notified body. D) Profitability.

**10.** Limited-risk systems under Article 50 are mainly subject to:
A) Transparency obligations (disclose AI use; label synthetic content). B) Full conformity assessment and CE marking. C) The systemic-risk regime. D) A complete ban.

**11.** Hupont et al. examine which documentation approaches?
A) Privacy notices and cookie banners. B) CE markings and customs declarations. C) Source-code escrow and patent filings. D) Datasheets for Datasets, the Dataset Nutrition Label, Model Cards, and AI FactSheets.

**12.** (Rewrite) Best rewrite of the Article 14 human-oversight duty?
A) Enable deployers to assign oversight to persons with the competence, authority and means to monitor, correctly interpret output, and decide not to use or override it. B) Persons should stay aware of risks. C) Human oversight is recommended where feasible. D) A human must individually approve every single output.

> **Answers:** 1-**C** (definition is technology-neutral; "infers" is the feature; A/B/D are things the Act deliberately does *not* require). 2-**B** (memorise the labels and order). 3-**D** (the others are permitted, possibly as high-risk, but not banned). 4-**D** (recommenders/marketing/spam aren't even prohibited). 5-**D** (Art 99(3), top band). 6-**C** (Art 99(4); B is the prohibition band, a trap). 7-**C** (only "no significant risk" exempts; nationality, size, licence are distractors; and profiling always makes it high-risk). 8-**D** (the word is *continuous/lifecycle*; A is the classic wrong answer). 9-**B** (accuracy, robustness, cybersecurity). 10-**A** (transparency only; the others belong to other tiers). 11-**D** (the real four; the rest are distractors). 12-**A** (precise, proportionate, workable; B too vague, C too weak, D disproportionate).

If you can score these closed-book and *explain why the wrong answers are wrong*, you have Lecture 2 cold. Spend your remaining time on the articles you fumbled, then come back a day later and test again rather than re-reading. The forgetting between sessions is doing the work.
