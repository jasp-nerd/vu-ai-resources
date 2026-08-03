# Lecture 1 Study Guide — The Relationship Between Law and Code
### The Law of Artificial Intelligence (VU Amsterdam, 2026)

This guide covers everything assigned for Lecture 1: Lessig's *Code is Law* talk (first 10 minutes), Schrepel's *The Not-So-Pathetic Dot Theory* (2022), the *Code, Law, and Business Models in the Age of AI* podcast (Lessig & Schrepel, 2025), and the lecture slides. I wrote it for someone who has not done the readings yet and does not have a law background, so every legal term gets explained the first time it shows up.

The exam is 100% multiple choice. That changes how you should study. Read the next section before the content — it will save you hours.

---

## 0. How to actually study this so you pass

You were probably taught to study by re-reading and highlighting. Cognitive psychology has tested those methods for decades, and they are close to useless. The big review here is Dunlosky and colleagues (2013), *Improving Students' Learning With Effective Learning Techniques*, which rated ten common study methods. Highlighting, re-reading, and summarizing scored **low**. Two methods scored **high**, and one more is close behind:

1. **Retrieval practice (the testing effect).** Pulling an answer out of your own head, with the book closed, is what builds durable memory. Reading the answer does almost nothing by comparison. Every time you *try to remember* and then check, you strengthen the memory more than another read-through would. This is the single most important thing you can do for a multiple-choice exam.

2. **Spaced practice.** Three 40-minute sessions across three days beat one 2-hour session the night before. The forgetting between sessions is the point — each time you reload a fading memory, it comes back stronger. Start now, not on June 23.

3. **Elaboration and self-explanation** (moderate-to-high). After you read something, ask *why is this true?* and *how does this connect to the thing I just learned?* Putting the idea in your own words and linking it to another idea is what makes it stick and what lets you handle "apply the concept to a new scenario" questions like Q3 on the mock.

Two more that matter for this specific exam:

- **Concrete examples.** The mock exam loves application questions ("Instagram down-ranks posts… which modality is this?"). You pass those by having a stock of worked examples in your head, not definitions.
- **Interleaving.** Don't drill one topic to death and move on. Mix Lessig questions with Schrepel questions with computational-law questions. It feels harder and produces better recall.

### How to use this document

Do **not** just re-read it. That is the low-utility trap. Instead:

- Read a section once for understanding.
- Cover it, and answer the **retrieval prompts** I dropped in (marked **↻ Recall**).
- At the end, do the **practice MCQs** in Section 9 closed-book, then check.
- Make the **flashcards** in Section 10 (or load them into Anki) and run them across several days.

The summary parts get you to *understand*. The recall parts get you to *pass*. You need both, and most students skip the second.

### What Lecture 1 looks like on the exam

From the mock exam, Lecture 1 maps directly onto **Q1–Q4**, and it underpins the logic of the rewrite questions in Part B (Q28–Q30). The four Lecture-1 questions test four distinct skills, and that tells you what to prepare:

| Mock Q | What it tests | Skill type |
|--------|---------------|------------|
| Q1 | Naming the four modalities exactly | **Definition recall** — exact words matter |
| Q2 | The core idea of Schrepel's refinement | **Concept recall** |
| Q3 | Classifying a real intervention (Instagram down-ranking) | **Application** |
| Q4 | Schrepel's caution about "freezing" tech | **Nuanced position recall** |

So your job for Lecture 1: memorize the four modalities word-for-word, understand the one big move Schrepel makes, be able to slot any real-world example into the right modality, and remember the practical lessons for regulators. The rest of this guide is built around exactly those.

---

## 1. The big picture: why this lecture exists

The course opens with a culture clash. For a long time, software developers saw lawyers as the people who show up to say "no." The manual tells a story from a GitHub board meeting around 2010: a lawyer starts with "I know you don't want to hear this from a lawyer, but—" and a board member cuts him off with "…then shut up." Developers asked *what is possible*; lawyers asked *what is permitted*; neither tried to understand the other.

Lecture 1 dismantles that opposition. Its claim, taken from Larry Lessig, is that **law is only one of several forces that control behavior**, and that for digital technology it is often not even the strongest one. Once you see that, two things follow. First, a lawyer who only thinks about legal rules is missing most of the picture. Second, technology itself — the code, the architecture — is *already* doing regulatory work, whether or not any lawyer planned it. This is the famous slogan you need to know cold: **"Code is law."**

The lecture has two halves, mirrored in the slide deck:
- **Regulatory forces** — the four modalities (Lessig), and how the regulated thing fights back (Schrepel).
- **Combining law and code** — computational law, and where it breaks down.

The course is taken by AI and CS students alongside law students, so the lecture's deeper question is aimed straight at the technologists in the room: *should policymakers rely on code to regulate?* (That is literally the "if this class was a movie" slide, which pairs the course with *Ex Machina*.)

> **↻ Recall:** Without looking, finish the slogan: "Code is ___." And state in one sentence why the lecture says a lawyer who only thinks about legal rules is missing the picture.

---

## 2. Lessig's Pathetic Dot Theory

This is the spine of the whole lecture. If you learn one thing perfectly, learn this.

### 2.1 First, what "regulation" means here

In everyday speech, "regulation" means government rules. Lessig uses the word much more broadly. He looks at the world from the point of view of **the thing being regulated** — a person, a company, a piece of technology — and asks: *what constrains its behavior?* A constraint is anything that makes some action harder, costlier, or impossible, or that enables an action that was not possible before. Government rules are one kind of constraint. They are not the only kind.

He draws the regulated thing as a single dot in the middle of a diagram and calls it the **"pathetic dot"** — "pathetic" in the old sense of *passive, acted-upon, to be pitied*, a creature that just sits there while forces push on it. (You = the pathetic dot, in his framing.) Remember that word; the exam uses it, and Schrepel's whole paper is a play on it.

### 2.2 The four modalities

Four forces push on the dot. **Memorize these four names exactly** — Q1 gives you four plausible-looking lists and only one is right.

**The four modalities of regulation: Law, Social Norms, the Market, and Architecture (code).**

Here is each one, with Lessig's own examples from the talk, plus how it is enforced and *when* it bites.

**1. Law.** Rules laid down by the state, backed by the threat of punishment after the fact. Lessig's example: a road sign says *Do Not Merge*. The law tells you in advance what not to do, and if you break it the state sanctions you. This is an **ex ante rule, enforced by the state.** (*Ex ante* is Latin for "from before" — the rule is set out beforehand. Its opposite, *ex post*, "from after," means a consequence applied after you act. Law typically announces the rule ex ante and punishes ex post.)

**2. Social Norms.** Informal expectations enforced by a community, through approval and disapproval rather than courts. Lessig's example: there is no law against him wearing a dress to give a lecture, but there is a strong norm against it among his audience, and the cost is social — losing the respect of people whose respect he wants. The enforcer is **the community**, not the state.

**3. The Market.** Prices and money. Offering someone \$300 to do something is a different constraint than offering \$3,000. The market shapes behavior through what things cost and what they pay, and it works through the legal scaffolding of **property and contract**. Note the timing: the market acts on you **simultaneously**, in the moment, through price, rather than announcing a rule in advance.

**4. Architecture (code).** The physical or technical reality of the space you are in — what the built environment simply makes possible or impossible. Lessig's example is the speed of light: a favorite MIT t-shirt reads "186,282 miles per second — it's not just a good idea, it's the law." You cannot break it; the constraint is built into reality and enforced, he jokes, "by God." In the **digital** world, architecture means **code**: the software that decides what a user can and cannot do. A website that has no "delete account" button has made deletion architecturally impossible, no statute required. Architecture also acts **simultaneously** — it constrains you as you act, with no need to catch you afterward.

A clean way to hold the four in memory is by **who or what enforces them, and when**:

| Modality | Enforced by | Timing | Lessig's example |
|----------|-------------|--------|------------------|
| **Law** | The state (courts, fines, prison) | Announced before, punished after | "Do not merge" sign |
| **Norms** | The community (approval/shame) | Before / ongoing | Don't wear a dress to give a talk |
| **Market** | Price, via property & contract | Simultaneous | \$300 vs \$3,000 to do a task |
| **Architecture / Code** | Reality / the system itself | Simultaneous | Speed of light; what software lets you click |

The "regulation" of the dot is the **sum of all four** acting together. Change one and you change the overall pressure on the dot. Some constraints reinforce each other; some pull against each other.

> **↻ Recall:** Name the four modalities in any order. For each, say who enforces it. Then classify these three on your own: (a) a paywall that blocks an article until you pay; (b) people side-eyeing you for vaping indoors; (c) a 30 km/h speed limit with cameras. *(Answers: market; norms; law.)*

### 2.3 The trap in Q3 — telling code apart from law

The mock exam's Q3 is the one students miss. "Instagram automatically down-ranks posts its classifier flags as likely false, so fewer users see them." Which modality?

It is **Architecture (code)** — not law. The instinct is to say "that's Instagram enforcing a rule, so it's law-like." But there is no state, no statute, no court. Instagram changed *what the software does* — the ranking algorithm now buries certain posts. The constraint is baked into the system's behavior. That is architecture/code regulating the dot. Lessig's point exactly: **code regulates, and it often does the work we assume only law can do.**

Rule of thumb for these questions:
- A government rule with a sanction → **Law**.
- A price or a payment → **Market**.
- People judging people → **Norms**.
- The *system itself* making something easy, hard, or impossible → **Architecture / Code**.

---

## 3. Lessig's second idea: law regulating the regulators

If law were just one of four forces, it would look small, and Lessig (a law professor) does not want law to look small. So he adds a second move: **law does not only push on the dot directly — it can push on the other three modalities, which then push on the dot.** Law regulates the regulators.

His example is **smoking**. The state can attack smoking through every modality:
- **Directly via law:** ban smoking (at least for some people, in some places).
- **Through norms:** run campaigns that make smoking uncool, so smokers lose social standing.
- **Through the market:** raise cigarette taxes so the price rises. (He notes the irony that governments also *subsidize* tobacco — set that aside.)
- **Through architecture:** mandate less nicotine per cigarette, so the product itself is less addictive and the pull to keep smoking weakens.

This restores law to a central role, because law can reach the dot indirectly through any of the other forces. And it drives everything to a single design question, which the lecture wants you to carry forward:

> **What is the mix of modalities that works best?**

A regulator always has a choice: write a direct rule, shift a norm, change a price, or re-engineer the architecture. Good regulation is choosing the right mix. Hold onto this question — it is the bridge to the whole AI Act, which is itself one big bet on a particular mix.

### 3.1 Two stories that show code and law trading places

Lessig gives two early-internet examples. You do not need every detail, but they illustrate the headline idea — **the market changes the architecture, and then the law exploits the new architecture** — and they are exactly the kind of thing a lecture-content MCQ can hang on.

**Cookies (1994).** The early web was "stateless": a site forgot who you were the instant you left a page. Great for privacy, terrible for commerce — a shop could not remember that you had a cart. Netscape introduced **cookies**, a bit of code that lets a site recognize a returning visitor. Commerce needed it, so the market drove a change in architecture. The side effect: your actions on the web became traceable. **Privacy fell not because a law changed, but because the code changed**, and the code changed because the market demanded it.

**Geolocation and Yahoo France (around 1999–2000).** The internet was built borderless: the core protocols (TCP/IP) did not know who or where you were. A man named Cyril Houri noticed 1-800-Flowers advertising to him in Paris, where a US 1-800 number is useless, and realized you *could* map an IP address to a physical location. He built IP-geolocation tech (then 95–98% accurate). Yahoo France was being sued because its auction site let people sell Nazi memorabilia, illegal in France. Yahoo's defense: "it's the web, we can't know where a user is." The new geolocation tech destroyed that defense — you *could* tell where a user was — so the French court (Judge Gomez) could order Yahoo to block French users from the illegal content. **The market built the architecture to sell ads; then the law took advantage of that same architecture to enforce a border online.**

The shared lesson: **law and code are not rivals on separate tracks. They reshape each other.** A change in code can do a law's job; a change in code can also hand the law a new tool.

> **↻ Recall:** In the cookies story, which modality changed first, and which modality exploited the change? State the smoking example's four interventions, one per modality.

---

## 4. The podcast layer: East Coast vs West Coast code, and "business models eat law"

The Lessig–Schrepel podcast (2025) updates the framework for the AI era. A few ideas from it are fair game for "content of the lectures" questions, and they deepen everything above.

**East Coast Code vs West Coast Code.** Lessig's nickname for the two kinds of "code" that govern us. **East Coast Code** = the legal rules written in Washington DC (statutes, regulations). **West Coast Code** = the software written in Silicon Valley. His blunt 2025 assessment: **West Coast code still wins.** The dominant regulator of online behavior is the engagement-driven software of social media, not anything Congress passes. He notes that in the US even child-online-safety laws stall, while West Coast code keeps shaping behavior at scale.

**"Business models eat law."** This is Lessig's phrase, and it is worth knowing. He means that a company's economic incentives (its business model) routinely overpower the state's attempts to regulate it, because business is the more effective, better-resourced player. In the US he ties this to campaign-finance corruption: after the Facebook whistleblower testimony, Congress briefly wanted to act, then lobbying money split it and nothing happened. Contrast Europe, which *has* passed sweeping rules — GDPR, the DSA, the DMA, the AI Act — even where Lessig doubts their strategy. (Glossary for these is in Section 11; for now, just clock that the EU regulates where the US cannot.)

**Lessig's critique of consent-based privacy law.** He thinks GDPR's cookie-consent model was a strategic mistake. Forcing everyone to click "I agree" to policies nobody reads turned consent into an empty ritual — Europeans burn an estimated 575 million hours a year clicking cookie banners while real privacy does not improve. His preferred design: mark some practices as presumptively fine, some as presumptively forbidden, and only ask the user to choose in the narrow grey zone between. This is a concrete instance of the "what mix of modalities works best?" question, and a good example of regulation that triggers a reaction without solving the problem.

**Which modality has scaled the most?** Schrepel proposes, and Lessig accepts, that **architecture/code has benefited most from digitalization.** Software shows *increasing returns* (it scales almost for free, copy and deploy globally), where physical building architecture shows *decreasing returns* (more wood and concrete cost more). Code used to be local; now it is global. That is why the architecture modality has grown so powerful relative to the others — and why "code is law" matters more in 2025 than in 1999.

**Open source and the AI Act (a preview of later lectures).** The podcast flags a problem you will meet again: the AI Act treats "open source" as a **binary** (you either qualify for the open-source exemption or you don't), when openness is really a **spectrum** (weights, training code, and training data can each be open or closed). Lessig also floats regulating AI at the **hardware layer** — building "circuit breakers" into chips so a runaway model can be slowed or shut down, which would let open-source innovation continue while keeping a safety backstop. You do not need this for Lecture 1's questions, but it shows the framework feeding directly into AI policy.

> **↻ Recall:** Define East Coast Code and West Coast Code. Explain "business models eat law" in one sentence. Why does Schrepel argue architecture scaled the most? *(Hint: increasing vs decreasing returns.)*

---

## 5. Schrepel's Not-So-Pathetic Dot Theory (2022)

This is the most-tested reading for Lecture 1 after the four modalities, and Q2 targets it directly. The whole paper is one move on top of Lessig.

### 5.1 The one big idea

Lessig's dot is **passive** — it just absorbs the four constraints. Schrepel's complaint: **the dot is not passive. It reacts, and by reacting it reshapes the four constraints that act on it.** Lessig drew arrows pointing *inward* at the dot. Schrepel makes the arrows **two-way**: the constraints push the dot, and the dot pushes back on the constraints. So the dot is **"not so pathetic."**

He grounds this in **complexity science** — the study of how systems react to and reshape the environment they sit in. The result is not a fixed, static picture but a **complex adaptive system**: an "infinite and dynamic game" rather than a "finite and static" one. The dot adapts, the constraints shift in response, the dot adapts again, and so on.

**If you remember nothing else about Schrepel:** the central refinement is that *the dot reacts to and reshapes the four constraints, forming a complex adaptive system.* That sentence is, almost verbatim, the correct answer to Q2.

### 5.2 The same examples, now with the dot fighting back

**Smoking, reworked.** Lessig used smoking to show the four constraints pressing on smokers. Schrepel asks: what do smokers *do back*?
- They buy cigarettes in a cheaper state → **market** pressure to keep prices low.
- They lobby lawmakers → change the **law**.
- They shift what is socially acceptable → change **norms** (in some ancient cultures it was fine for children to smoke).
- They favor one cigarette type over another → create an incentive that changes the product → **architecture**.

The dot is proactive. Its reactions become new constraints, which it then reacts to again.

**Blockchain / crypto (the cyberspace test).** Schrepel shows the theory holds online:
- User behavior moves crypto **prices** (market).
- When New York introduced a tough Bitcoin license, companies "walked with their feet" to New Jersey — **forum shopping** forced the **law** to change. (*Forum shopping* = choosing the jurisdiction with the friendliest rules. *Jurisdiction* = the territory whose laws apply to you.)
- Ethereum switched from Proof-of-Work to Proof-of-Stake, reopening the question of what is acceptable in the ecosystem (**norms**).
- Projects strip out chokepoints and single points of control so there is no one for regulators to hold liable (**architecture** reacting to **law**). (*Liability* = legal responsibility you can be made to answer for.)

In every case the dot is not absorbing regulation — it is bending the constraints around itself and forcing policymakers to innovate.

### 5.3 Why it matters — the tools Schrepel adds

Schrepel imports two concepts from complexity science that the exam can ask about.

**Robustness vs fragility.** A **robust** system absorbs shocks and stays the same; its problems are long-lasting (his example: the dark web — it has survived everything thrown at it). A **fragile** system changes the moment you touch one constraint (his example: metaverses). The lesson for a regulator: if you face a *problematic robust* system, you will need to hit *several* constraints hard to move it; if a system is fragile, a small nudge may be enough.

**Feedback loops.** Borrowed from biology.
- A **positive feedback loop** amplifies a change and pushes the system to a new state that does not revert. (His example: childbirth — pressure triggers oxytocin triggers more contractions triggers more oxytocin, until the baby is born.)
- A **negative feedback loop** counteracts a change and returns the system to its original state. (His example: body temperature — you get cold, you shiver to warm up, you get hot, you sweat to cool down, back to baseline.)
- Transposed to law: **regulation that sets off a strong positive feedback loop can genuinely shift a robust system; regulation that only triggers negative loops will be absorbed and fizzle.** Schrepel suggests lawyers sort past regulations into these two buckets and learn from them.

**The practical payoff: dynamic regulation, not "future-proof" regulation.** Because the dot keeps adapting, you cannot write one perfect rule and walk away. Schrepel argues against the fantasy of **"future-proof" regulation** (enacted once, valid forever) and for **adaptive regulation** (collect data on whether the rule still works, and adjust in real time). He also warns against **legal solutionism** — the habit of reaching for a legal rule as the answer to everything. When the dot ignores your legal fix, the move is to combine modalities, designing **law + architecture** together rather than law alone.

A closing note of humility from the paper: the dot adapts in **unpredictable** ways, so do not deprive a technology of what it needs to "adapt, survive and flourish." Dots form networks and compete; competition between them should stay fair. This is the seed of every "be careful regulating a living technology" lesson in the next section.

> **↻ Recall:** State Schrepel's central refinement in one sentence (this is Q2). Give one example of the dot changing a constraint. Define a positive vs a negative feedback loop, and say which one a regulator needs to shift a robust system.

---

## 6. The five learnings for regulators (slides)

The lecture turns Schrepel's theory into practical advice. The slides list two framing points and then five learnings. These are prime "content of the lectures" material, and **Q4 is taken straight from learning #3.**

Two framing points first:
- **#1 The constraints can be combined.** You rarely use one modality alone; you mix them (this is Lessig's "what mix works best?" made operational).
- **#2 The dot is adaptive.** Straight from Schrepel — plan for a target that reacts.

The five learnings:

1. **The law is not self-sufficient — combine it.** Against an increasingly robust digital ecosystem, law on its own is not enough. Pair it with norms, market, and code.

2. **The law should not necessarily trump the other constraints — because it needs them.** Don't assume law should always win; it depends on the other three to actually work.

3. **The law regulates a living subject (technology) fighting for survival, so it can *influence* architecture but must be careful about *annihilating* it.** This is the most tested learning. Three specific cautions:
   - **Careful when "freezing" the tech** (stopping its evolution): the slide's example is **USB-C**, where the EU mandated one fixed charging standard. Lock in a standard and you stop the technology from evolving.
   - **Careful when favoring certain characteristics** (steering evolution): the example is rules that **favor small models** via the **10²⁵ FLOP** threshold. (FLOP = floating-point operations, a measure of how much compute trained the model. The AI Act treats models above 10²⁵ FLOP as systemically risky, which nudges developers toward staying small.)
   - **Careful when imposing central coordination:** the slide's jab is the "obsession for *governing*…" — the urge to centralize control over a technology.

   **Q4's correct answer is exactly this:** the law should be careful when freezing a technology and halting its evolution, e.g. mandating a single fixed standard such as USB-C. The wrong options on the mock (law should *never* touch architecture; law should pick a single winner early; law should be written once and never changed) are all the opposite of the lesson.

4. **The law is often more static than the other constraints — so make it dynamic.** Norms, markets, and code move fast; law moves slowly. Build in mechanisms to update it. (This is "adaptive over future-proof" again.)

5. **The law should be concerned with the dot's reaction — because the dot can react in unintended ways — so run transparent retrospective studies and evaluate publicly.** Watch what your rule actually did after the fact, in the open.

### Future-proof vs adaptive regulation (the speed-limit slide)

The deck makes the future-proof/adaptive contrast concrete:
- **Future-proof regulation:** a flat rule — "you may drive up to 80 km/h on this road." Fixed, simple, brittle.
- **Adaptive regulation:** specify the *objective* ("minimize accidents on this highway"), the *metrics* for success (accidents per day; average journey time), the *range* of acceptable interventions (speed limits between 70 and 100 km/h), and an *ordering* that lets the rule discriminate between vehicles, weather, and so on. The limit then flexes with conditions instead of sitting frozen.

This is the design philosophy the whole course leans toward, and it is the bridge into computational law.

> **↻ Recall:** List the five learnings from memory. Which learning does Q4 come from, and what is its USB-C point? Give the future-proof vs adaptive contrast using the speed-limit example.

---

## 7. Computational law — combining law and code

The second half of the lecture answers the course's headline question: if code can regulate, **should we write law *as* code?** That field is **computational law** — expressing legal rules in a form a computer can execute, check, or analyze.

### 7.1 Why bother (the rationale, three points)

From the "Rationale" slides:

1. **Computational law is integrative.** It forces lawyers and coders to sit at the same table and understand each other — which is the whole premise of this course.
2. **It handles complex rules.** Natural language processing (**NLP** — software that reads and analyzes human-language text) can help policymakers digest huge bodies of case law and adapt their rules.
3. **It enables effective interventions.** Code can execute automatically the instant its conditions are met, so you may not even need to *detect* a violation first — the rule self-enforces (depending on how strictly it is wired up).

### 7.2 The four tools, and exactly where each one breaks

This is the part students underestimate. For each computational-law tool, the slides pair a use-case with a **"main limit."** The limits are the most exam-friendly bit, because they are crisp and quotable. Learn the **tool → limit** pairs.

**1. Decision trees (for compliance).** A branching "if-yes-then" questionnaire that walks a user to an answer. The slide's example is an **EU AI Act Compliance Checker** that asks step-by-step whether your system counts as an "AI system," whether it is high-risk, and so on.
- **Main limit: the world is not always 0s and 1s.** Many legal questions are not clean yes/no — they are matters of degree and judgment. A binary tree forces a fuzzy question into a hard branch. The provocation on the slide: *should we change the law* to make it more tree-shaped?

**2. Digital brains (knowledge graphs).** A network map of legal decisions where each case is a node and relationships are edges, which you can query (Schrepel's competition-law graph linking French and UK cases). It can surface, for instance, that a legal structure exists in one jurisdiction with **no analog** in another.
- **Main limit: explainability.** The graph can show you *that* two things connect, but struggle to explain *why* in terms a court or a regulator would accept. (*Explainability* = being able to give human-understandable reasons for a system's output. It recurs all through AI law.)

**3. NLP (e.g., CLAUDETTE).** Train a model to read legal text and flag issues — the slide cites **CLAUDETTE**, a tool built to analyze whether terms of service comply with the GDPR, with the further ambition of having it *justify* its choices.
- **Main limit: not everything is put in writing.** NLP only sees the text. Much of what matters in law — context, intent, unwritten practice, the reason behind a clause — never makes it onto the page, so a text-only system misses it.

**4. Scraping.** Automatically harvesting data from the web to study behavior at scale — the slide cites *Dark Patterns at Scale: Findings from a Crawl of 11K Shopping Websites* (Mathur et al.), which scraped thousands of sites to map manipulative design.
- **Main limit: legality, and correlation is not causation.** Scraping itself can be legally fraught, and even when it surfaces a pattern, a correlation in scraped data does not prove one thing *caused* another. You can see that sites with feature X tend to have outcome Y without showing X causes Y.

A compact table to drill:

| Tool | What it does | Main limit |
|------|--------------|------------|
| **Decision trees** | Branching compliance questionnaire (AI Act checker) | The world isn't always 0s and 1s |
| **Digital brains / knowledge graphs** | Queryable network of legal decisions | Explainability |
| **NLP (CLAUDETTE)** | Reads legal text, flags (non-)compliance | Not everything is put in writing |
| **Scraping** | Harvests web data at scale (dark patterns) | Legality + correlation ≠ causation |

The lecture groups these under two headers — **#1 Understanding** (decision trees, digital brains, NLP help us *understand* law and compliance) and **#2 Enforcement** (scraping and automated execution help *enforce*). And it ends on the open question it keeps circling: these techniques exist, but *are any of them actually in the AI Act?* — which is the cliff-hanger into Lecture 2.

> **↻ Recall:** Match each tool to its main limit without looking: decision trees, digital brains, NLP, scraping. Then explain in one line why "correlation is not causation" limits scraping.

---

## 8. The bridge to the AI Act (so you see where this goes)

Lecture 1 plants one concrete AI Act detail you will need on June 24, and it appears on the compliance-checker slide and in **Q5** of the mock: the **definition of an "AI system."**

Under **Article 3(1)** of the AI Act, an AI system is, in essence, a machine-based system that operates with some autonomy, may adapt after deployment, and — the key phrase — **infers, from the input it receives, how to generate outputs such as predictions, content, recommendations, or decisions** that can influence physical or virtual environments. The exam-critical element is that **inference-to-output** clause (Q5's correct answer). It does **not** require deep neural networks specifically, does **not** require training on personal data, and does **not** require full autonomy with zero human involvement — those are the decoy options.

You don't need the rest of the Act for Lecture 1. Just lock in that this whole "code is law / what mix of modalities / should law be code" framing is what the AI Act is *doing*: it is the EU choosing a mix of modalities to regulate a fast-moving, adaptive technological dot — and the rest of the course judges how well it pulled that off.

---

## 9. Practice exam — Lecture 1 (do this closed-book first)

This is the highest-value part of the guide. **Cover the answers. Commit to a letter for each. Then check and read the explanation, especially when you were wrong** — getting one wrong and finding out why teaches more than getting it right.

The first four are the actual Lecture-1 questions from the mock (options reordered here so the answer key isn't a pattern, and lengths evened out so the longest option isn't a tell). The rest I wrote in the same style to stretch you.

**Q1.** Lessig's Pathetic Dot Theory holds that the regulated dot's behavior is shaped by four modalities. Which set lists them correctly?
- A) Law, enforcement agencies, deterrence, and criminal sanctions
- B) Law, social norms, the market, and architecture (code)
- C) Law, ethics, public policy, and digital technology
- D) Legislation, case law, private contracts, and technical standards

**Q2.** In Schrepel's *Not-So-Pathetic Dot Theory* (2022), what is the central refinement of Lessig's model?
- A) The dot reshapes the constraints it faces, forming a complex adaptive system
- B) Architecture is always the single strongest constraint and overrides the other three
- C) The four constraints act independently and never influence one another at all
- D) Law should be removed as a constraint, since code now does its regulatory work

**Q3.** Instagram automatically down-ranks posts its classifier flags as likely false, so fewer users see them. In Lessig's framework this is regulation through:
- A) Law
- B) Social norms
- C) Architecture (code)
- D) The market

**Q4.** Which best reflects Schrepel's caution about how the law affects technology (architecture)?
- A) The law should be careful when freezing a technology, e.g. fixing one standard like USB-C
- B) The law should be written down once and then left wholly unchanged, to stay "future-proof"
- C) The law should never touch architecture at all, and should act only through norms and markets
- D) The law should always pick one single winning technology as early as it possibly can

**Q5.** In Lessig's smoking example, raising the tax on cigarettes is an attempt to regulate smokers through which modality?
- A) Norms
- B) Law
- C) Architecture
- D) The market

**Q6.** In Lessig's account of the early web, why did online privacy decline when Netscape introduced cookies?
- A) Social norms around personal privacy collapsed online before anything else did
- B) Courts ordered commercial websites to begin systematically tracking their users
- C) The code changed to make web behavior traceable, driven by market demand
- D) An existing privacy-protection statute was quietly repealed by the legislature

**Q7.** Lessig distinguishes "East Coast Code" from "West Coast Code." These refer to:
- A) Common law judicial systems versus codified civil law systems
- B) Legal rules from Washington DC versus software from Silicon Valley
- C) US federal statutes versus the separate laws of individual states
- D) Permissively open-source software versus proprietary closed-source software

**Q8.** Schrepel borrows "feedback loops" from complexity science. A *positive* feedback loop is one where:
- A) A small change is counteracted, returning the whole system to its original state
- B) A change is amplified, pushing the system into a new state that doesn't revert
- C) The regulation involved always improves overall social welfare for everyone
- D) The dot gradually stops reacting to any of the four constraints around it

**Q9.** The lecture contrasts "future-proof" regulation with "adaptive" regulation. The adaptive approach is best illustrated by:
- A) An objective plus metrics and a flexible limit range, say 70–100 km/h by conditions
- B) Banning all private driving on the entire road in order to remove every possible risk
- C) Leaving the road's posted speed limit entirely unwritten and formally unstated
- D) A single fixed rule such as "you may drive at up to 80 km/h on this road"

**Q10.** In the computational-law segment, which tool is paired with the limit "not everything is put in writing"?
- A) Knowledge graphs ("digital brains")
- B) Web scraping
- C) Decision trees
- D) NLP (e.g. CLAUDETTE)

**Q11.** The "main limit" the lecture attaches to compliance **decision trees** is that:
- A) They inherently violate the GDPR's core requirements
- B) They are simply far too slow to compute at any scale
- C) Legal questions are not always just 0s and 1s
- D) They can never actually be shown to the end user

**Q12.** Schrepel argues that, among the four modalities, **architecture** has benefited most from digitalization because:
- A) Courts deliberately granted code a special and protected legal status
- B) Governments around the world simply stopped trying to regulate it
- C) Norms and markets both effectively disappeared the very moment everything moved online
- D) Code has increasing returns and scales globally, unlike physical architecture

---

### Answers and explanations

**Q1 — B.** The four modalities are **Law, social norms, the market, architecture (code)**. The other lists are plausible legal-sounding decoys (case law, sanctions, ethics) but none is Lessig's set. Memorize the exact four.

**Q2 — A.** Schrepel's one move: the dot is **active**, reacting to and reshaping the constraints, which makes the picture a **complex adaptive system**. "Remove law" overstates him (he never says delete law), "architecture always strongest" is not his claim, and "constraints never influence each other" is the opposite of both Lessig and Schrepel.

**Q3 — C.** No state, no statute, no court — Instagram changed *what the software does*. That is **architecture/code**. This is the classic "don't mistake code for law" trap.

**Q4 — A.** Straight from learning #3: be careful **freezing** a technology, e.g. the EU mandating **USB-C**. The other three are each the inverse of the lesson (never touch architecture / pick a winner early / write once and freeze).

**Q5 — D.** A cigarette tax works through **price**, which is the **market** modality. Easy to misread as "law" because a government imposes the tax, but the *mechanism that reaches the smoker* is the price. Watch this distinction.

**Q6 — C.** Privacy fell because the **code** changed (cookies made behavior traceable), and the code changed because the **market** wanted commerce. No statute, no court order — that is the whole point of the story.

**Q7 — B.** **East Coast Code** = DC legal rules; **West Coast Code** = Silicon Valley software. Lessig's 2025 line: West Coast still wins.

**Q8 — B.** Positive loop = **amplify and shift to a new state** (childbirth). Negative loop = counteract and return to baseline (body temperature). The "counteracted, returns to its original state" option describes the *negative* loop.

**Q9 — A.** Adaptive regulation sets objective + metrics + a flexible range of interventions. The fixed "up to 80 km/h" option is the *future-proof* (frozen) version.

**Q10 — D.** **NLP / CLAUDETTE** is limited because it only reads text, and "not everything is put in writing." (Decision trees → 0s and 1s; digital brains → explainability; scraping → legality + correlation ≠ causation.)

**Q11 — C.** Decision trees force fuzzy legal questions into hard branches; the world isn't always 0s and 1s.

**Q12 — D.** Increasing returns (software scales for free, globally) versus decreasing returns (more concrete costs more). This is the Schrepel point Lessig accepts in the podcast.

> If you missed more than two, the fix is not to re-read — it is to redo these tomorrow, closed-book, then again two days later. That spacing is what moves them into long-term memory.

## 10. Flashcards (front → back)

Make these physical or load them into Anki, and run them across several days. Front side first; say the answer out loud before flipping.

- **The four modalities?** → Law, social norms, the market, architecture (code).
- **Who enforces each?** → Law: the state. Norms: the community. Market: price (property & contract). Architecture: the system/reality itself.
- **"Code is law" means?** → Software architecture regulates behavior the way law does; code can do law's job.
- **Why is the dot "pathetic" (Lessig)?** → It is passive; it only absorbs the four constraints.
- **Schrepel's central refinement?** → The dot is active: it reacts to and reshapes the constraints → a complex adaptive system.
- **Lessig's second idea?** → Law can regulate the *other modalities* (the regulators), not just the dot directly.
- **The single design question Lessig drives at?** → What mix of modalities works best?
- **Smoking, four interventions?** → Ban (law), make it uncool (norms), tax it (market), cut nicotine (architecture).
- **Cookies story lesson?** → Market drove a code change; code change killed privacy; then law could exploit traceability.
- **Yahoo France lesson?** → Geolocation (built for ads) gave the law a tool to enforce borders online.
- **East vs West Coast Code?** → DC legal rules vs Silicon Valley software; West Coast still dominates online behavior.
- **"Business models eat law"?** → A company's economic incentives routinely overpower state regulation.
- **Robust vs fragile system?** → Robust absorbs shocks and stays the same; fragile changes the moment you touch a constraint.
- **Positive vs negative feedback loop?** → Positive amplifies into a new state (childbirth); negative returns to baseline (body temperature).
- **Future-proof vs adaptive regulation?** → Fixed rule forever vs objective + metrics + flexible range that updates with data.
- **Learning #3 (most tested)?** → Law can influence architecture but be careful annihilating it — freezing (USB-C), favoring characteristics (10²⁵ FLOP), central coordination.
- **Computational law, the three rationales?** → Integrative (lawyers + coders); handles complex rules (NLP); enables effective/automatic interventions.
- **Tool → limit: decision trees?** → Not always 0s and 1s.
- **Tool → limit: digital brains?** → Explainability.
- **Tool → limit: NLP (CLAUDETTE)?** → Not everything is put in writing.
- **Tool → limit: scraping?** → Legality + correlation is not causation.
- **AI system, the key part of Art. 3(1)?** → It *infers, from input, how to generate outputs* (predictions, content, recommendations, decisions).

---

## 11. One-page cheat sheet and glossary

### The whole lecture in one box

- **Lessig:** four constraints push on the passive "pathetic dot" → **Law, Norms, Market, Architecture (code)**. Law can also regulate the other three. Best regulation = the right **mix**. **Code is law.**
- **Schrepel:** the dot is **not** passive — it reshapes the constraints → **complex adaptive system**. So regulate **adaptively**, watch feedback loops, don't annihilate a living technology.
- **Combining law + code (computational law):** four tools, four limits. Powerful, but legal judgment doesn't reduce to 0s and 1s, isn't always written down, isn't always explainable, and correlation isn't causation.
- **Forward:** the AI Act is the EU's chosen *mix of modalities* for an adaptive technological dot. Define an "AI system" by its **inference-to-output**.

### Glossary (plain-language, for the non-lawyers)

- **Regulation (Lessig's sense):** any force that constrains or enables behavior, not just government rules.
- **Modality of regulation:** one of the four forces (law, norms, market, architecture).
- **Pathetic dot:** the regulated subject, drawn as passive in Lessig's diagram.
- **Architecture / code:** the built or technical environment; online, the software that makes actions possible or impossible.
- **Ex ante / ex post:** "from before" / "from after." A rule announced in advance vs a consequence applied afterward.
- **Norms:** informal social expectations enforced by approval and disapproval.
- **East Coast Code / West Coast Code:** legal rules (Washington DC) vs software (Silicon Valley).
- **Business models eat law:** economic incentives outrun and defeat state regulation.
- **Complex adaptive system:** a system whose parts react to and reshape the whole, evolving over time rather than sitting still.
- **Robustness / fragility:** a system's tendency to absorb shocks (robust) or change at the first push (fragile).
- **Feedback loop (positive/negative):** a change that amplifies into a new state (positive) or self-corrects back to the old one (negative).
- **Future-proof vs adaptive regulation:** a fixed rule meant to last forever vs a rule that updates from data and conditions.
- **Legal solutionism:** the reflex of treating a new legal rule as the answer to every problem.
- **Computational law:** expressing legal rules as code a computer can run, check, or analyze.
- **NLP (natural language processing):** software that reads and analyzes human-language text.
- **Knowledge graph:** a queryable network of nodes (e.g. cases) and the relationships between them.
- **Explainability:** the ability to give human-understandable reasons for a system's output.
- **Forum shopping:** picking the jurisdiction with the most favorable rules.
- **Jurisdiction:** the territory whose laws apply to a person or activity.
- **Liability:** legal responsibility you can be made to answer for.
- **FLOP:** floating-point operations; a measure of training compute. The AI Act's systemic-risk line is 10²⁵ FLOP.
- **GDPR / DSA / DMA / AI Act:** EU laws on, respectively, data protection / online-platform duties / gatekeeper-platform competition / AI systems. (Detail comes in later lectures; for now, just know the EU regulates here where the US largely hasn't.)

### Study plan for the next stretch (spaced, not crammed)

- **Today:** read Sections 1–6 once; do the **↻ Recall** prompts out loud.
- **Tomorrow:** read Sections 7–8; do the Section 9 MCQs closed-book; build the flashcards.
- **+2 days:** redo every MCQ you missed; run the full flashcard deck.
- **+4 days and weekly until the exam:** one fast flashcard pass, interleaved with the other lectures' material.

That rhythm — recall, space, mix — is what the research says actually moves a multiple-choice grade. The summary got you to understand it. The testing is what makes you remember it on June 24.
