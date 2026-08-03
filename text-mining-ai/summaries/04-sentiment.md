# 04 — Sentiment analysis

**Source slides:** tm-ba-lecture-4-sentiment.pdf (47 pp.)
**Companion literature:** Maynard et al. 2016 Ch 7; Jurafsky ch 22 (Lexicons for Sentiment, Affect, and Connotation)
**Quiz questions drawn from this material:** Sentiment (10 Qs)

The slide deck is officially titled "Lecture 4: Subjectivity mining" — the lecturer uses "subjectivity" and "sentiment analysis" almost interchangeably here, with sentiment treated as one specific kind of subjectivity. Worth remembering for exam wording.

---

## Cheat sheet (cover the right column, recall the left)

| Term / question | Answer | Slide |
|-----------------|--------|-------|
| Lecture title | Subjectivity mining | p. 1 |
| Three parts of the deck | I What is subjectivity, II Subjectivity mining, III Tools/resources | p. 2 |
| Opinion structure (4 elements) | Holder, SIP (Source Introducing Predicate), Sentiment, Target | p. 5 |
| Explicit vs implicit sentiment | Explicit = openly evaluative ("ridiculous", "insult"); implicit = inferred from context ("dies", "suffer") | p. 4 |
| Two kinds of opinion holder | Author (writes the text) and Participant (mentioned in text) | p. 4 |
| Agenda setting | Author's subjective choice of what to mention / leave out | p. 4 |
| SIP — speech-act verbs | say, claim, state, express, tell, announce, ensure, guarantee, promise, deny, confirm, reject, accept | p. 6 |
| SIP — cognitive verbs | believe, think, consider, feel, hate, like, love | p. 6 |
| Syntactic subject of a SIP | The agent / source of the belief (person, organisation) | p. 6 |
| Syntactic object of a SIP | The proposition, claim or statement (NP, that-clause, VP) | p. 6 |
| Product-review terminology | Sentiment expressions linked to aspects (picture quality, use, purchase); holder is implicit (author) | p. 7 |
| Hard cases in tweets | Figurative language: metaphor, simile, metonymy, irony, sarcasm | p. 8 |
| Definition of emotion | Subjective response to a situation; inferred from face, voice (tone/pitch/volume), content | p. 9 |
| Ekman 6 basic emotions (Ekman et al. 1976) | Anger, Disgust, Fear, Happiness, Sadness, Surprise | p. 10 |
| Universality claim of Ekman | Same emotions in many different cultures (universal status) read from facial expressions | p. 10 |
| Extended Ekman list (not facially expressed) | Amusement, Contempt, Contentment, Embarrassment, Excitement, Guilt, Pride, Relief, Satisfaction, Sensory pleasure, Shame | p. 10 |
| Plutchik (1980) wheel | Adds intensity dimension + mixtures of basic emotions; says detecting 6 basic emotions is not trivial | p. 11 |
| WordNet-Affect A-labels | EMOTION, MOOD, TRAIT, COGNITIVE STATE, PHYSICAL STATE, HEDONIC SIGNAL, EMOTION-ELICITING SITUATION, EMOTIONAL RESPONSE, BEHAVIOUR, ATTITUDE, SENSATION | p. 12 |
| Subjectivity (terminology) | Umbrella term covering opinion mining, sentiment, stance | p. 13 |
| Sentiment / polarity | Explicit pos / neg / neutral, e.g. good, bad | p. 13 |
| Opinion | Sentiment relation of a holder to a target ("I like him") | p. 13 |
| Stance | Opinion in a debate ("I support the anti-vaccination movement") | p. 13 |
| Aspect | Opinion on an attribute of something ("this iPhone has an incredibly good battery") | p. 13 |
| Argumentation | Explicit arguments for stances ("I like this iPhone because …") | p. 13 |
| Attribution | Source + cue + content (used in news for indirect citations) | p. 13 |
| Levels of analysis | Corpus, document, sentence, phrase | p. 18 |
| Ravi & Ravi 2015 — main tasks | Subjectivity classification, sentiment classification, review usefulness, opinion spam detection, lexicon creation, aspect extraction | p. 21 |
| Ravi & Ravi 2015 — approaches | Machine learning, lexicon-based, hybrid (+ ontology / non-ontology for aspects) | p. 21 |
| Opinion extraction sub-questions | Subjective?, opinion expression?, holder?, target?, polarity? | p. 22 |
| Features for sentiment | Bags of words / n-grams, POS, opinion-word lists, valence shifters / negation / modals, syntactic dependencies | p. 23 |
| Feature selection | Frequency, TF*IDF, term position (title, first/last sentence) | p. 23 |
| Data representations | One-hot BoW, IOB tags, sequence of pos/neg tags, token embeddings, mean-sentence embeddings | p. 24 |
| Ravi & Ravi 2015 — most common ML method | SVM (55 articles) | p. 25 |
| Reported sentiment accuracy range | 72 – 92% in-domain | p. 25 |
| Document-level F-scores (slide example) | Rule+lex 78.3; BoW NB 82.3; BoW+lemma 83.6; BoW+lex+rules 84.7 | p. 26 |
| Cohen κ — hotel reviews | 0.87 (high) | p. 27 |
| Cohen κ — Black Pete tweets | 0.55 – 0.65 (lower, more subjective) | p. 27 |
| Context dependence example | "cold person" (neg) vs "cold soda" (pos) vs "cold shower" (neutral/blue) | p. 30 |
| Double propagation idea | Iteratively learn aspects from sentiment seeds and sentiment words from aspect seeds, using POS patterns | p. 31–33 |
| ABSA benchmark | SemEval 2014 task 4 and 2016 task 5; XML format with target, category, polarity | p. 34 |
| Aspect terms differ per domain | Restaurants → food/service; laptops → battery life/keyboard; hotels → room/staff | p. 35 |
| VADER (full name) | Valence Aware Dictionary and sEntiment Reasoner | p. 36 |
| VADER specialised for | Social media (tweets); lexicon includes emoji ratings | p. 36, 40 |
| NRC emotion lexicon | Words tagged with 8 emotions + pos/neg | p. 37 |
| Other resources mentioned | LIWC, WordNet-Affect, MPQA / OpinionFinder, Bing Liu lexicon, Potts tokenizer, Harvard General Inquirer | p. 38 |
| Transformer pipeline call | `pipeline("sentiment-analysis", model="distilbert-base-uncased-finetuned-sst-2-english")` | p. 45 |

---

## 1. What sentiment analysis is

Sentiment analysis (called "subjectivity mining" in the deck) is the automatic extraction of opinions, emotions and sentiment from text (p. 16). It lets us track attitudes and feelings across blogs, comments, reviews and tweets, and decide whether a product, brand or person is positively or negatively perceived on the web — what the slides call reputation management.

The course frames it broadly: any time a writer expresses something subjective (an evaluation, a feeling, a belief, an emotional response), we can try to mine it. The slide on p. 15 makes the slogan explicit: "We do not live in an information society — we live in a communication society," and subjectivity mining is what lets us study that communication at scale.

Tasks that sit under this umbrella (Ravi & Ravi 2015, p. 21):

- **Subjectivity classification** — is this sentence objective or subjective? (step 1)
- **Sentiment classification** — what is the polarity (positive/negative)? With sub-tasks: polarity determination, vagueness in opinionated text, multi- / cross-lingual SC, cross-domain SC. (step 2)
- **Review usefulness measurement** and **opinion spam detection** — is this opinion trustworthy? (step 3)
- **Lexicon creation** and **aspect extraction** — at what level of detail are people commenting? (step 4)

Quiz Q4 ("Emma believes the new restaurant is fantastic") is a definitional question about the opinion holder; the answer is **Emma**.

## 2. Opinion structure

The deck's central diagram on p. 5 says: **an opinion is a complex relationship involving a holder and the judgment (sentiment) that the holder has regarding a particular target**. The four roles to know are:

- **Holder** — who has the opinion (person or organisation). Can be the *author* of the text or a *participant* mentioned inside it.
- **SIP — Source Introducing Predicate** — the verb / phrase that connects the holder to the judgment (urged, said, claims, believes, hates).
- **Sentiment** — the actual evaluative content (aggressively diversify, stop, mental hostage).
- **Target** — what the opinion is about (activities, rely on coffee, businessmen).

On the slide's Colombia / coffee news example: the holder is "official" / "Yohai", the SIP is "urged" / "said", the sentiment is "aggressively diversify" / "stop" / "mental hostage", the target is "activities" / "rely on coffee" / "businessmen". The reporter is outside the picture and provides only objective framing.

Quiz Q2 ("These guys are terrible") asks for the **target**. The opinion is *about* "These guys", so that is the target. "Terrible" is the sentiment expression, the speaker/writer is the (implicit author-)holder. Don't be tricked into picking the sentiment word.

Two extra concepts on p. 4:

- **Explicit sentiment** — openly evaluative wording: *boundless energy* (pos), *completely ridiculous, insult, horrible, cancer* (neg).
- **Implicit sentiment** — inferred from world knowledge (*dies, suffer, pains, death* read as negative for most readers, though culture-dependent).
- **Agenda setting** — what the author chooses to mention or leave out is itself a subjective act.

## 3. Source Introducing Predicates (SIPs)

p. 6 gives a closed-ish list:

- **Speech-act verbs** (someone is performing a communication act): *say, claim, state, express, tell, announce, ensure, guarantee, promise, deny, confirm, reject, accept*.
- **Cognitive verbs** (someone has a mental state): *believe, think, consider, feel, hate, like, love*.

The **syntactic subject** of a SIP is the agent / source of the belief; the **syntactic object** is the proposition, claim or statement (NP, that-clause, VP — e.g. *I like taking the train to the university*).

This is the deck's grammar-side way of finding holders automatically: look for SIPs and grab their subjects and complements.

## 4. Sources of sentiment text

The deck illustrates three genres with concrete corpus snippets:

- **News articles** (p. 5), formal style; the reporter is outside the opinion and gives objective information, while holders inside the text express subjective claims via SIPs.
- **Product reviews** (p. 7); short, often noisy, with implicit holder (the author) and explicit aspects (picture quality, use, purchase).
- **Tweets** (p. 8); short, informal, full of irony, sarcasm and emoji — "Everything in the kids section of IKEA is so cute. Shame I'm nearly 19 in 2 months :(" mixes a positive evaluation with a negative twist.

The "Data Never Sleeps" infographic on p. 14 is decorative and not exam material — the point it makes (that enormous amounts of subjective content are produced every minute) is the only takeaway.

## 5. Aspect-Based Sentiment Analysis (ABSA)

p. 7 / 13 / 33–35. An **aspect** (also called a facet, feature or property) is a specific attribute of a product or service that an opinion is about. Example phrases: "this iPhone has an *incredible good* **battery**"; the camera review on p. 7 breaks the document into aspect–sentiment pairs *(picture quality – excellent), (use – very easy), (purchase – extremely satisfied)*.

ABSA is more granular than document-level sentiment: a single review can be positive about *food* and negative about *service*. The ABSA SemEval format (p. 34) makes this explicit with XML where each `<Opinion>` has a `target`, a `category` (e.g. RESTAURANT#GENERAL, FOOD#QUALITY) and a `polarity` (positive/negative).

The training task usually has two stages: (1) token classification to mark which tokens are aspect terms (BIO / IOB tags), then (2) classification of the polarity attached to each aspect.

The aspect ranking table on p. 35 makes the domain dependency very concrete: top aspects for restaurants are *food / service / staff / bar*; for laptops they are *battery life / keyboard / screen / feature*; for hotels they are *hotel / room / staff / service*. A model trained only on laptops will not know what to do with "the duvet was thin".

Quiz Q5: aspect = "a specific feature or attribute of the product or service being evaluated".

## 6. Figurative language and other hard cases

p. 8. Figurative language is a cover term for:

- **Metaphor** — "the rooms were a refrigerator"
- **Simile** — "it's like going to the dentist"
- **Metonymy** — substituting one entity for a related one ("the White House said")
- **Irony** — saying the opposite of what is meant in a way the audience is expected to catch
- **Sarcasm** — irony with a critical / mocking edge

All of these are difficult for sentiment classifiers because the literal polarity of the words and the intended polarity diverge. A bag-of-words classifier sees "so cute" and predicts positive; a human reads "Shame I'm nearly 19" and flips the whole thing.

Quiz Q6 asks which option is figurative language — metaphor, simile and metonymy are all listed individually, so the right answer is **All of the above**. Sarcasm and irony belong to the same family.

## 7. Emotion vs sentiment

The deck draws a careful line:

- **Sentiment / polarity** is binary or ternary (positive / negative / neutral). It is what most classifiers output.
- **Emotion** is categorical and richer.

p. 9 says emotions are subjective responses to situations, indirectly inferred from face, voice (tone, pitch, volume) and actual content. In text we only get the last channel.

**Ekman et al. (1976)** — the standard reference for "basic emotions" (p. 10). Six basic emotions read from facial expressions claimed to be universal across cultures: **Anger, Disgust, Fear, Happiness, Sadness, Surprise**. The slide shows the six classic Ekman photos. The deck also lists an extended set that is not necessarily facially expressed (amusement, contempt, contentment, embarrassment, excitement, guilt, pride, relief, satisfaction, sensory pleasure, shame) — these are the kinds of mental states you might still need to detect in text.

Quiz Q7 lists the six exactly: Happiness, sadness, anger, fear, surprise, disgust. The distractor "Love, jealousy, pride, excitement, boredom, shame" is wrong — note that *pride*, *excitement*, *shame* appear in the extended list but not in the core six, and *love* / *jealousy* / *boredom* are nowhere in Ekman's core set.

**Plutchik (1980) wheel of emotions** (p. 11) is a dimensional / categorical hybrid that adds two things on top of basic emotions:

- intensity of basic emotions (so anger ranges over annoyance — anger — rage)
- mixtures of emotions (love = joy + trust, contempt = anger + disgust, awe = fear + surprise)

Plutchik's eight base emotions are joy, trust, fear, surprise, sadness, disgust, anger, anticipation. The slide explicitly notes that even detecting the 6 basic Ekman emotions is "not trivial", let alone the mixtures.

**WordNet-Affect** (p. 12) is a labelled extension of WordNet where synsets get A-labels: EMOTION, MOOD, TRAIT, COGNITIVE STATE, PHYSICAL STATE, HEDONIC SIGNAL, EMOTION-ELICITING SITUATION, EMOTIONAL RESPONSE, BEHAVIOUR, ATTITUDE, SENSATION. This is the resource side of the same idea.

## 8. Features for sentiment classification

p. 23. The features the deck names — all fair game in the exam — are:

- **(Bags of) words or n-grams.** Often the baseline.
- **Part-of-speech tags.** Especially adjectives and adjective-adverb combinations (because evaluative content lives in them).
- **Lists of opinion words.** From a sentiment lexicon (good, bad, terrible, fantastic).
- **Valence intensifiers and shifters; modal verbs; negation.** *Very*, *extremely*, *not*, *should*.
- **Syntactic dependencies (for opinions).** Subject and object of SIPs — to extract holder–target structure.

Feature selection is done by frequency, TF*IDF, and term position (terms in the title or the first/last sentence carry more sentiment weight). Representations covered (p. 24):

- one-hot BoW (keeps exact wording)
- averaged word-embeddings (more semantic / generalising — higher recall, lower precision)
- contextual embeddings via transformer encoders like BERT — best of both worlds; semantic representation plus compositional relations through attention; better recall and precision

Quiz Q8 lists three of these (POS tags, modal verbs, words/n-grams) — the right answer is **All of the above**.

## 9. Negation and valence shifting

p. 23 and p. 26. Negation is the classic case of a valence shifter — a word that flips the polarity of the words it scopes over.

Typical negation words: **not, never, no, neither** (Quiz Q3). Inline negator tagging: rewrite "the rooms are not clean" as "the rooms are not clean+**negator_tag**" so a bag-of-words classifier sees the negated token as a separate feature. The deck shows that adding lexicon + negation rules takes hotel-review F1 from 82.3 (plain BoW Naive Bayes) → 83.6 (BoW + lemma) → 84.7 (BoW + lexicon + negation rules), and combining everything pushes accuracy up to ~92%.

The slide also distinguishes negation from related things:

- **Intensifiers** (*very, completely, absolutely, certainly*) — strengthen polarity, don't flip it.
- **Diminishers / downtoners** (*hardly, scarcely, barely, slightly*) — weaken polarity.
- **Positive sentiment words** (*good, excellent, fantastic, delightful*) — carry polarity themselves.

The Quiz Q3 distractors are exactly these three classes — the only set with true negators is *not / never / no / neither*.

## 10. Approaches: lexicon vs ML vs hybrid

p. 21 (Ravi & Ravi 2015 overview), p. 25 (their numbers), p. 31–33 (double propagation).

Three families:

- **Lexicon-based** — count positive vs negative words from a sentiment dictionary, apply rules for negation and shifters. Works without labelled data; struggles with context-dependent polarity ("cold" on p. 30).
- **Machine learning** — supervised classifiers trained on labelled documents. Bag-of-words + Naive Bayes / SVM / NN; modern systems use BERT-style transformer encoders.
- **Hybrid** — combine the two, e.g. use a lexicon as one feature inside an ML model.

Ravi & Ravi 2015 surveyed published sentiment work and counted which intelligent technique was applied (Table 6 on p. 25):

| Technique | #articles |
|-----------|-----------|
| **SVM** | **55** |
| Dictionary-based approaches | 41 |
| Naive Bayes | 28 |
| Neural networks | 11 |
| Logistic regression | 9 |
| Decision trees | 9 |
| Linear regression / Maximum entropy / Ontology / LDA | 8 each |
| Random forest / SVR / CRF / Boosting / SVM-SMO / Rule miner | 4–5 each |

SVM is the most common method. Reported in-domain accuracy ranges from ~72% to ~92%. Quiz Q9 asks exactly this — the answer is **Support Vector Machines (SVM)**.

**Double propagation** (p. 31–33) is the deck's example of an unsupervised / weakly-supervised hybrid for ABSA. Start with a tiny sentiment seed (good, bad) and a small set of POS patterns (D+A+N, D+Adv+A+N, with+A+N, has+A+N). Then:

1. Step 1: find aspects (nouns) using sentiment words via patterns — *good plot, bad actor* → aspects {plot, actor}.
2. Step 2: use those aspects to find new sentiment words — *bright, fantastic, great, romantic, ugly, boring, sober plot* → sentiments {bright, boring, …}.
3. Step 3: feed the new sentiments back to find more aspects. Iterate.

Finally, classify the discovered opinion words as positive or negative using word embeddings and patterns.

## 11. Lexicons

p. 36 onwards.

- **VADER (Valence Aware Dictionary and sEntiment Reasoner)** — the headline lexicon-based tool. Each token has a mean sentiment rating (–4 to +4) from 10 raters, a standard deviation, and the raw ratings. Crucially, VADER also covers emoji and slang, which is why it is **specifically attuned to social media** (tweets, Twitter-style posts). Quiz Q10 — VADER is for **social media**, not news, not scientific reports, not all of the above.
- **NRC emotion lexicon** (Saif Mohammad) — words tagged with eight emotions (anger, anticipation, disgust, fear, joy, sadness, surprise, trust) plus pos/neg. Used for emotion detection rather than just polarity.
- **LIWC (Linguistic Inquiry and Word Count)** — psychological / cognitive categories, much broader than sentiment alone.
- **WordNet-Affect** — A-labelled synsets of WordNet (see §7).
- **MPQA / OpinionFinder** — annotated for subjective sentences, sources, and pos/neg sentiment phrases.
- **Bing Liu's opinion lexicon** — two long lists of positive / negative words.
- **Christopher Potts' sentiment tokenizer** and the **Harvard General Inquirer** — older resources, also fair game by name.
- **SentiWordNet** (referenced in Jurafsky ch 22) — adds pos/neg/objective scores to WordNet synsets.

For modern systems the deck shows the transformer-pipeline route (p. 45–46): `pipeline("sentiment-analysis", model="distilbert-base-uncased-finetuned-sst-2-english")` returns `{"label": "POSITIVE", "score": 0.999…}`. Hugging Face hosts many language-specific sentiment models (Dutch BERT, Japanese BERT, Italian BERT, etc., p. 44).

## 12. Annotation and inter-annotator agreement

p. 27–29. Hotel reviews annotated at three classes (pos / neg / neutral) reached Cohen's κ = 0.87 — high agreement, chance-corrected. The Black Pete tweet debate, with four classes and three annotators, only managed κ = 0.55 – 0.65 — sentiment in political/controversial domains is genuinely contested. News annotations on opinion expressions: κ = 0.70. The slide on p. 28 makes the methodological point: even user star ratings (1–5) and trained annotator scores (–5 / 0 / +5) on the same hotel review can disagree (4 stars vs –2 from an annotator), because personal perspective matters.

Take-away: sentiment labels are never fully objective; expect Cohen κ values to drop as the task becomes more nuanced or politically charged.

## 13. Context dependence

p. 30. The polarity of a word depends on what it modifies:

- "A cold person" — negative
- "A cold soda" — positive
- "A cold shower" — neutral-to-negative depending on domain
- "Low prices" — positive in shopping; "low ceilings" — negative in housing
- "Fast food" — neutral/negative; "fast cars" — positive for petrolheads

This is why double propagation and domain-specific lexicons exist — and why a movie-trained classifier transfers poorly to electronics reviews.

## 14. Evaluation in sentiment (macro-averaging, Quiz Q1)

This is the one calculation question in the Sentiment quiz. Macro-averaging across two classes is asked, and the formula itself is not on these slides — it lives in the ML-for-NLP deck and Jurafsky ch 4. Worked example, exactly as in Quiz Q1:

100 reviews. **Gold:** 40 positive, 60 negative. **System predictions:** 50 positive, 50 negative. Correctly identifies 10 positives and 20 negatives.

Build the confusion matrix:

|              | predicted pos | predicted neg | gold total |
|--------------|---------------|---------------|------------|
| gold pos     | 10 (TP)       | 30 (FN)       | 40         |
| gold neg     | 40 (FP for pos = FN for neg's view) | 20 (TP for neg) | 60 |
| predicted total | 50          | 50            | 100        |

For the **positive class**:
- TP = 10, FP = 50 − 10 = 40, FN = 40 − 10 = 30
- Precision_pos = TP / (TP + FP) = 10 / 50 = 0.20
- Recall_pos    = TP / (TP + FN) = 10 / 40 = 0.25

For the **negative class**:
- TP = 20, FP = 50 − 20 = 30, FN = 60 − 20 = 40
- Precision_neg = TP / (TP + FP) = 20 / 50 = 0.40
- Recall_neg    = TP / (TP + FN) = 20 / 60 ≈ 0.333

**Macro precision** = (0.20 + 0.40) / 2 = **0.30**
**Macro recall** = (0.25 + 0.333) / 2 ≈ 0.292 ≈ **0.3**

So macro precision ≈ macro recall ≈ 0.3 — matches Quiz Q1's correct option *"The recall & precision are both 0.3"*.

A useful sanity check: micro-averaged accuracy is (10 + 20) / 100 = 0.30 as well, because total predicted = total gold = 100. The 0.5 distractor in the quiz comes from confusing precision with the proportion of *predictions* in one class (50/100). The 0.15 distractor likely comes from dividing TP only by total reviews (10/100 + 20/100 = 0.3, then halved).

Why this is a Sentiment-lecture question even though the formula is foundational: evaluation of a 2-class sentiment classifier is the canonical use of macro-averaging in this course.

---

## Likely exam traps

- **Target ≠ Holder.** The holder is the person *having* the opinion; the target is what the opinion is *about*. In a tweet, the holder is usually the author (implicit); the target is the topic.
- **Aspect ≠ target.** "Phone is great" — target is phone. "The battery life is great on the phone" — target is the phone, aspect is battery life. ABSA tracks aspects within a target.
- **VADER is for social media**, not "all of the above". The right Q10 option is "Social media" only.
- **Ekman's basic six** are exactly Anger, Disgust, Fear, Happiness, Sadness, Surprise. Love, jealousy, pride, excitement, boredom, shame are *not* among the basic six (pride / excitement / shame are in the extended list).
- **Negation ≠ intensifier ≠ diminisher.** "Not / never / no / neither" flip polarity. "Always / completely / absolutely / certainly" strengthen it. "Hardly / scarcely / barely / slightly" weaken it. Quiz Q3's distractors are all from those other categories.
- **SIP is the verb, not the holder.** "Emma believes that …" — Emma is the holder, *believes* is the SIP.
- **Sentiment is polarity, emotion is categorical.** Don't confuse Plutchik mixtures with positive/negative.
- **Cohen κ corrects for chance**, so an 80% raw-agreement task can still have a mediocre κ if the labels are imbalanced.
- **Macro vs micro averaging.** Macro = average per-class metrics (gives each class equal weight, even small classes). Micro = pool TPs/FPs/FNs across classes first.
- **SVM was most common in 2015** (Ravi & Ravi). The deck explicitly flags "2015!" because today transformer models would top the chart — but the exam answer is SVM.
- **ML on the deck includes lemma / lexicon / rules.** Plain BoW Naive Bayes scored 82.3; the boost to 92% F1 comes from combining features, not from a fancier model.

---

## Self-quiz (cover the answers)

1. In the sentence *"The official has urged the business community to aggressively diversify,"* what is the SIP?
   - a) aggressively diversify
   - b) the official
   - c) urged
   - d) the business community
   *Answer: c. SIPs are the verbs (speech-act or cognitive) that introduce the opinion; "urged" is a speech-act verb.*

2. Which of the following is **not** one of Ekman's six basic emotions?
   - a) Surprise
   - b) **Pride**
   - c) Sadness
   - d) Disgust
   *Answer: b. Pride is in the extended list, not in the basic six.*

3. A sentiment classifier outputs 50 "pos" and 50 "neg" predictions on 100 documents (40 actually pos, 60 actually neg), getting 10 positives and 20 negatives correct. What is macro recall?
   - a) 0.50
   - b) 0.40
   - c) 0.30
   - d) 0.15
   *Answer: c. (10/40 + 20/60) / 2 ≈ 0.292 ≈ 0.3.*

4. Which technique was found by Ravi & Ravi (2015) to be the most used for sentiment classification?
   - a) Logistic regression
   - b) **SVM**
   - c) LDA
   - d) BERT
   *Answer: b. 55 articles in their survey used SVM.*

5. Which set of words consists of valence intensifiers (and **not** of negation words)?
   - a) hardly, scarcely, barely, slightly
   - b) not, never, no, neither
   - c) good, excellent, fantastic, delightful
   - d) **always, completely, absolutely, certainly**
   *Answer: d. Intensifiers strengthen polarity. (b) flips polarity, (a) weakens it, (c) are sentiment words.*

6. ABSA aims to:
   - a) **Find sentiment about specific attributes of a product**
   - b) Find the overall sentiment of a document
   - c) Detect figurative language in text
   - d) Identify the syntactic structure of opinion sentences
   *Answer: a.*

7. In *"Everything in the kids section of IKEA is so cute. Shame I'm nearly 19 in 2 months,"* the main difficulty for a bag-of-words classifier is:
   - a) Negation
   - b) Multilingual mixing
   - c) **Irony / sarcasm**
   - d) Domain mismatch
   *Answer: c. The literal pos words ("so cute") are inverted by the ironic twist.*

8. VADER is specifically tuned for:
   - a) **Tweets / social media**
   - b) Movie reviews
   - c) Scientific abstracts
   - d) All written domains equally
   *Answer: a.*

9. Which of these is **not** an example of figurative language?
   - a) **Past tense**
   - b) Simile
   - c) Metaphor
   - d) Metonymy
   *Answer: a. Past tense is grammatical, not figurative.*

10. The opinion holder in *"Emma believes that the new restaurant is fantastic"* is:
    - a) Fantastic
    - b) The new restaurant
    - c) The reader of the sentence
    - d) **Emma**
    *Answer: d. Emma is the source of the belief; "believes" is the SIP, "fantastic" is the sentiment, "the new restaurant" is the target.*

11. Which feature type was **not** listed in the lecture as useful for sentiment classification?
    - a) Bigrams
    - b) Adjective-adverb combinations
    - c) **Phoneme inventories**
    - d) Modal verbs
    *Answer: c. Sentiment is text-level; phoneme inventories belong to phonology.*

12. Plutchik's wheel of emotions adds two ideas on top of Ekman's basic emotions. They are:
    - a) Universality and facial expression
    - b) Polarity and valence
    - c) Tone and pitch
    - d) **Intensity and emotion mixtures**
    *Answer: d.*

---

## What's in the quiz but NOT in the slides

- **Q1 (macro-averaging calculation).** Macro-averaging precision and recall is not on the sentiment deck; it is foundational evaluation material covered in the ML-for-NLP / part-2 lecture and in Jurafsky ch 4. You need the per-class precision/recall formulas and the rule that macro = unweighted mean across classes.
- **Q3 (explicit list of negation words).** The slides mention negation as a feature and show "not" being inline-tagged, but they don't list "not / never / no / neither" as a closed set. The right option here is identifiable by elimination — the other three distractors are intensifiers, diminishers, or positive sentiment words.
- **Q10 (VADER acronym expansion).** VADER appears on p. 36 with the full name "Valence Aware Dictionary and sEntiment Reasoner" — that *is* on the slides. The "social media" framing is also on the same slide, so this one is fully covered.
