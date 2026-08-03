# 03a — NLP pipelines (Lecture 3 Part 1)

**Source slides:** tm-ba-lecture-3-machine-learning-nlp-part1.pdf (68 pp.)
**Companion literature:** Maynard et al. 2016 Ch 2; NLTK ch 6 (learning to classify), ch 8 (sentence structure); Jurafsky ch 4 (Naive Bayes / sentiment classification)
**Quiz questions drawn from this material:** Natural Language Processing (10 Qs — most map to part 1)

---

## Cheat sheet (cover the right column, recall the left)

| Term / question | Answer | Slide |
|-----------------|--------|-------|
| How does tokenisation handle "state-of-the-art"? | Depends on the tokeniser setup — one, three, or four tokens all possible | p. 8, 10 |
| What approaches were used in early NLP? | Rule-based (hand-crafted rules) | p. 31, 35 |
| How many WordNet words for movement? | More than 3,000 (slide title actually says 4,000) | p. 25 |
| How many WordNet words for person? | About 5,000 | p. 24 |
| How many WordNet words for noise? | 2,037 | p. 26 |
| Average meanings per frequent English noun | 7.8 (Princeton WordNet, Ng & Lee 1996) | p. 20 |
| Possible meaning combinations for "He gave a soft ball…"  | 14,041,749,244,723,200 | p. 21 |
| Most ambiguous noun in WordNet 3.0 | head (33 senses) | p. 23 |
| Most ambiguous verb in WordNet 3.0 | break (59) | p. 23 |
| Most ambiguous adjective in WordNet 3.0 | active (11) | p. 23 |
| Two main problems of text mining | Ambiguity and variation | p. 18 |
| Ambiguity = | one form, multiple meanings | p. 19 |
| Variation = | many ways to refer to the same thing | p. 27 |
| Structural ambiguity example | "Fruit flies like a banana" | p. 19 |
| Lexical ambiguity example | "bank" = institution / riverside | p. 19 |
| Example of variation | Different names for one person ("Ms Torretta", "Gina Torretta", "the chairman") | p. 28 |
| Pipeline definition | A complex NLP problem broken into smaller modules; output of one is input of next | p. 6 |
| Two main risks of pipeline architecture | Dependencies across modules; error propagation | p. 6, 15 |
| Levels of NLP processing (bottom-up) | Tokenisation → Lexical → Syntactic → Semantic → Pragmatic | p. 6 |
| Two flavours of NLP techniques | Knowledge-base & rules; machine learning (sup/unsup) | p. 6 |
| Shared early modules across pipelines | Tokenisation & sentence splitting, POS tagging | p. 11, 12 |
| NER pipeline-specific module | Named Entity Recognition & Disambiguation | p. 11 |
| Sentiment pipeline-specific module | Word Sense Disambiguation, Sentiment Analysis | p. 12 |
| Medical NLP pipeline steps | PDF/XHTML→text, section detection, sentence/token, POS/lemma, syntax, NER, entity linking, time, relations, events, hedging | p. 13 |
| Issues with pipelines | Error propagation, ambiguities not exploited downstream, conflicts between modules, hard to maintain (interoperable I/O) | p. 14 |
| Performance vs complexity (Maynard 2016, Fig 1.3) | Accuracy drops from bag-of-words → entities → relations → events | p. 16 |
| Three NLP approaches | Rule-based, machine learning, hybrid | p. 30 |
| Hybrid = | ML + rule-based combined | p. 30 |
| Lexicon ambiguity example | "low prices" (positive) vs "low ceilings" (negative) | p. 31 |
| Rule-based sentiment lexicons | VADER (tweets), NRC (emotions), LIWC (psych features) | p. 31 |
| VADER meaning | Valence Aware Dictionary and sEntiment Reasoner | p. 32 |
| NRC = | crowd-annotated emotion lexicon (anger, joy, fear, …) | p. 33 |
| Law of diminishing returns for rules | More rules → marginal recall gain (50→60→65→68%) | p. 34 |
| Why machine learning? | Hand-crafted models failed empirical tests; ML works better than any rules tried so far | p. 35 |
| Supervised ML inputs | Labelled training corpus + tag set + feature extractor | p. 39 |
| Tag set = | Set of labels described in a code book with examples and decision criteria | p. 39 |
| Fine-grained tag set → | More complex annotation, harder for people | p. 39 |
| Examples of NLP shared tasks | MUC, TREC, CLEF, CoNLL, SensEval, SemEval, PAN | p. 40 |
| Common data formats | Text, CSV, TSV, XML, JSON, HTML | p. 41 |
| Inline annotation | Tags inserted directly inside the text, e.g. ENAMEX XML | p. 44, 45 |
| Stand-off annotation | Separate layer pointing back into raw text via offsets | p. 41, 47 |
| CoNLL format | Each token on its own line, TAB-separated columns, IOB style (Inside/Outside/Beginning) | p. 46 |
| NAF | Newsreader Annotation Format; layered XML stand-off | p. 47, 48 |
| Why stand-off? | Raw text untouched, multiple layers can coexist and point at each other, easy to add layers | p. 47 |
| Annotation procedure steps | Sampling → annotation scheme/code book → train annotators or crowd → annotation tool → store | p. 49 |
| IAA = | Inter-Annotator Agreement; degree to which annotators give same label, corrected for chance | p. 50 |
| Kappa threshold | < 50 Kappa = task too difficult | p. 50 |
| IAA is considered | Upper ceiling of NLP performance | p. 50 |
| BRAT | Web-based annotation environment | p. 50 |
| Gold data | Labels assigned by human annotators | p. 51 |
| Silver data | Machine-proposed labels validated by humans | p. 51 |
| Bronze data | Machine-generated labels, no human validation | p. 51 |
| Why bronze data still useful | Used as training labels OR as extra features (lemmas, POS, deps) | p. 51 |
| Important rule | Train and test data must get the same feature representations, including bronze features | p. 51 |
| Features of text (allowed) | Length, word/sentence length, case/word shape, punctuation, surrounding words, POS, lemma, sentiment, syntax, semantic roles, topic, genre, date | p. 53 |
| NOT features for text | Font, page layout, handwriting, print quality, page count | distractor |
| What cannot be a feature | The gold label itself (would make prediction circular) | p. 52 |
| Two ways to represent text | Sequence (preserves order) or bag (no order) | p. 54 |
| Bag-of-words assumption | Word order ignored; word frequencies act as fingerprint | p. 55 |
| Term-document matrix | Rows = words, columns = documents, cells = counts | p. 56 |
| TF*IDF | Term frequency × Inverse document frequency (Spark-Jones 1972) | p. 57 |
| Why TF*IDF | Words appearing everywhere have low info; words appearing once are idiosyncratic | p. 57 |
| N-gram | Sequence of 1, 2, 3, … words; bigger N → richer info but sparser | p. 58 |
| Character n-gram advantage | More frequent than word n-grams → less data sparseness | p. 58 |
| One-hot encoding | Vector with 1 at the word's position, 0 elsewhere; length = vocabulary size | p. 62 |
| Underfitting | Model too simple, cannot capture variance | p. 63 |
| Overfitting | Model learns idiosyncratic training-data details (e.g. filename) | p. 63, 67 |
| Generative classifier | e.g. Naive Bayes, models P(words \| class) for each class | p. 64 |
| Discriminative classifier | e.g. logistic regression, learns how useful features are for a class | p. 64 |
| Feature engineering goal | Transform raw text into features for ML; pick what works best (ablation) | p. 65, 66 |
| Feature ablation | Test different feature sets to find the best combination | p. 65 |
| Disadvantage of supervised ML | Needs handcrafted annotations: expensive, time-consuming, task/domain-specific, must redo every 5-10 yr | p. 68 |
| Solution direction for ML data hunger | Unsupervised learning / language models | p. 68 |

---

## 1. What is NLP and why is it hard

Text mining is harder than search because there is no such thing as simple text. A single sentence
hides multiple levels of analysis. The slide pyramid (p. 6) goes bottom up: tokenisation, lexical
analysis, syntactic analysis, semantic analysis, pragmatic analysis — culminating in the speaker's
intended meaning. The bottom three are structural; the top two cover content.

Each level is a smaller problem. Solve the simple structural ones first, then feed their output into
the harder semantic ones. That stacking is what we call a *pipeline*. The trade-off is that errors
propagate upward: a wrong token boundary corrupts every layer above it.

For each problem there are two technique families:
- knowledge-base and rules (linguistic knowledge)
- machine learning (supervised and unsupervised), data driven

Both can be combined (hybrid).

## 2. Tokenisation

The first problem in any NLP system is "what is a word, what is a sentence?". The lecturer keeps
hammering: this is not trivial, not even for state-of-the-art deep-learning systems (p. 7).

Tricky tokenisation cases (p. 7):
- hyphenated terms: nitty-gritty, data-base, (semi-)irony, state-of-the-art
- numbers and dates: $523,45 — 21st century — 9-11
- encoding issues (Latin, UTF-8/16, diacritics, fancy quotes)
- contractions: don't, men's
- end-of-line hy-p-h-ens (word split across a line)

Tricky sentence splitting (p. 7): Dr., Mrs., Bol.com, 7.5, etc. etc, white spaces, tables, formulae,
titles, TABs, new lines, HTML markup.

**Worked example, "Jelly Bean and Ice Cream Sandwich" (p. 10):**
- without punctuation → 9 tokens
- with punctuation, treating double quotes as one token → 14 tokens
- with punctuation, treating each quote separately → 18 tokens

So the number of tokens depends on the tokeniser configuration. This is the quiz Q1 trap: the
"correct" multiple-choice answer for "how does a tokeniser split state-of-the-art?" is **it depends
on the setup**, not a fixed number.

## 3. Variation vs ambiguity

These are the two big problems for text mining (p. 17).

### Ambiguity — one form, multiple meanings (p. 18-23)
- **Structural ambiguity**: "Fruit flies like a banana" — fruit flies (insects) enjoy a banana, OR
  fruit travels through the air like a banana does. Same goes for the classic news headlines:
  "Foot Heads Arms Body", "Hospitals Sued by 7 Foot Doctors", "British Left Waffles on Falkland
  Islands", "Stolen Painting Found by Tree" (p. 19).
- **Lexical ambiguity (polysemy)**: words with multiple meanings. "bank" = financial institution
  or riverside.

Pervasiveness: the 121 most frequent English nouns each have on average **7.8** meanings, and
those 121 words make up about **20%** of word occurrences in real text (Princeton WordNet, Ng & Lee
1996; p. 20).

A 10-word sentence "He gave a soft ball across the line from the center of the field, making a
major point and giving a minor lead" yields **14,041,749,244,723,200** possible meaning
combinations when you multiply the sense counts (p. 21). This is the "puzzle for a computer"
slide.

WordNet 3.0 distribution (p. 22): nouns peak at 1 meaning (101,863), but a long tail goes up to
59. Most polysemous nouns: head (33), line (30), point (26), base/case/cut (20). Most polysemous
verbs: break (59), make (49), give (44), take (42). Most polysemous adjectives: active (11),
soft/light/inactive (8).

### Variation — many forms, one meaning (p. 27-29)
- Different words and phrases can refer to the same entity. "Ms G Torretta", "Gina Torretta",
  "Ms. Gina Torretta", "the chairman", "Ms Torretta" (p. 28). Coreference spreads information
  across multiple sentences.
- WordNet has roughly:
  - **5,000 words for person** (p. 24) — withholder, scandalmonger, cyberpunk, word-painter, etc.
  - **4,000 words for movements** (p. 25) — swash, zigzag, jazz_around — relevant for quiz Q3
    which says "more than 3,000". 4,000 satisfies "more than 3,000" so the answer is correct.
  - **2,037 words for noise** (p. 26) — clatter, katzenjammer, swoosh, squeal, ding-dong.

Quiz Q5's specific British "colour" vs American "color" example is **not** in the slides, but the
concept of variation is. The slide's examples are different forms of person reference and
event-expression variation, but the spelling example fits the same definition.

### NLG vs NLU (p. 28-29)
- Natural Language Generation = finding the right expression for data/images/signals (machine
  translation, summarisation, chatbots, robo-journalism). Risk: generic answers like "person" or
  "tell me more" to stay on the safe side.
- Natural Language Understanding = mapping text → words → resources (rules/lexicon or classifier)
  → interpretation. Either way, somebody has to build the lexicon/rules or annotate training data.

## 4. NLP pipelines

A pipeline breaks the big problem (extract information from text) into smaller modules whose
outputs feed each other (p. 6). The architecture has dependencies across modules and is prone to
error propagation.

**Examples in the slides:**
- *NER pipeline* (p. 11): Document → Tokenisation & sentence splitting → POS tagging → Named
  Entity Recognition & Disambiguation.
- *Sentiment Analysis pipeline* (p. 12): Document → Tokenisation & sentence splitting → POS
  tagging → Word Sense Disambiguation → Sentiment Analysis.
- *Medical NLP pipeline* (p. 13): X/HTML or PDF → text, section detection, sentence/token, POS
  /lemma, syntax, NER (gene, protein, drug, disease), then hedging, time, relation, event, entity
  linking. Output: structured data.

The pattern: **the first modules are shared across tasks (tokenisation, sentence splitting, POS).
The later, task-specific modules differ.** Quiz Q4 is literally this sentence: "NLP pipelines are
likely to share basic processing steps (such as tokenization) while including specific modules
for higher-level interpretations."

The wrong distractors in Q4 are worth memorising:
- "Pipelines always process text directly without preprocessing" — wrong, you always need
  preprocessing (p. 7).
- "Pipelines have entirely distinct modules with no shared components" — wrong, see above.
- "Pipelines are rigid sequences that cannot be modified" — wrong, modularity is the point.

### Issues (p. 14, 15)
- **Error propagation** — bar chart on p. 15 shows isolated accuracy ~85% for POS and syntax but
  drops to ~55% for POS and ~35% for syntax once errors propagate through the pipeline.
- **Ambiguities not exploited downstream** — POS tagger outputs 80% noun / 20% verb but the next
  module only takes the top label.
- **Conflicts** — two modules state incompatible info.
- **Hard to maintain** — input/output formats must be interoperable.

### Performance vs complexity (p. 16, Maynard 2016 Fig 1.3)
A 2D plot: y-axis specificity (domain general → domain specific), x-axis task complexity
(bag-of-words → entities → relations → events). The "usable accuracy" curve drops steeply:
bag-of-words tasks reach 90%+ accuracy, event extraction drops to ~30%.

## 5. Annotation

### Data formats (p. 41)
Plain text, CSV, TSV, XML, JSON, HTML. DOC/PDF/Excel get converted to one of these. Two
annotation styles matter:

### Inline annotations (p. 44, 45)
Tags inserted **directly inside** the text. Example (p. 45): the ENAMEX XML scheme wraps
"Taffner" in `<ENAMEX TYPE="PERSON">…</ENAMEX>`, "Capital City" in `<ENAMEX TYPE="WORK_OF_ART">`,
etc. Penn Treebank trees `(S (NP-SBJ (NNP Bartok)) (VP (VBZ describes) …))` are also inline.

### CoNLL format (p. 46)
TSV style: each token on its own line, columns for the annotations. Uses **IOB tagging**:
- **B-** = beginning of an entity
- **I-** = inside an entity
- **O** = outside any entity

Example from the slides:
```
1   The       O
2   American  B-Organization
5   Museum    I-Organization
...
12  New       B-Location
13  York      I-Location
```

(Side note: slide p. 46 says "I = insight" but means "Inside". Just a typo in the deck.)

### Stand-off / layered annotations (p. 41, 47, 48)
- The raw text is **not modified**.
- Annotations live in a separate file (or layer) and **point** at character offsets in the text.
- Layers can point to each other.
- Easy to add new layers without touching existing ones.
- Alternatives do not complicate the representation.

Example: **Newsreader Annotation Format (NAF)** — XML with a `<text>` layer of `<wf>` word forms
(id, sent, para, offset, length), a `<terms>` layer with lemma/POS/morphofeat plus
`<externalReferences>` to WordNet synsets, and an `<entities>` layer pointing back to terms and
linking out to DBpedia (p. 47-48).

Quiz Q6 maps directly: "Inline annotations are inserted directly within the text, while
stand-off annotations are stored in a separate file or a different layer."

### Annotation procedure (p. 49)
1. **Sampling** — collect texts (tweets, news, blogs, books).
2. Define an **annotation scheme** or **code book**: tag set, unit of annotation (token / phrase
   / sentence / paragraph / document), criteria for when a tag applies.
3. Train **human annotators** or set up a **crowd task**.
4. Provide an **annotation tool** (e.g. BRAT, p. 50).
5. **Store** annotations with text (XML, TSV, …).

### Quality (p. 50)
- More than one annotator per item; for crowdsourcing, 10-20 workers.
- **Inter-Annotator Agreement (IAA)** measures how often annotators picked the same label,
  corrected for chance.
- If IAA is too low (<50 Kappa) the task is considered too difficult.
- IAA is treated as the **upper ceiling** of what an NLP system can achieve (a few exceptions like
  Native Language Identification).

## 6. Gold / silver / bronze data (p. 51)

- **Gold data**: labels assigned by human annotators.
- **Silver data**: labels proposed by a machine and then validated by humans.
- **Bronze data**: labels generated by a machine and **not validated**.

Bronze data still has a role: it can be used as training labels OR as **extra features** (lemmas,
POS tags, dependency parses) alongside gold IOB annotations.

Critical rule: train and test data must get the same feature representations, including the
bronze ones.

Quiz Q7 matches the definitions exactly. Distractors to avoid:
- "Gold = user feedback, silver = ML, bronze = surveys" — wrong, has nothing to do with the
  source.
- "Gold = raw, silver = processed, bronze = aggregated" — wrong.
- "Gold = training, silver = validation, bronze = testing" — wrong. Gold is about who annotated,
  not what split.

## 7. Features in NLP

A feature is any property of the text the classifier can use, **except the gold label itself**
(that would make the prediction circular, p. 52).

Allowed feature types (p. 53):
- Text-level: text length, average sentence length, word length
- Surface: case / word shape, punctuation
- Context: surrounding words
- Lexical word properties: POS, meaning (sense), sentiment scores
- Sentence properties: syntactic parse, semantic roles
- Document properties: topic, genre, publication date

Crucial: **any feature must be mapped to some vector representation** (numeric).

Quiz Q8 picks the only option made of textual features (sentence length, punctuation marks, POS
tags). Distractors mention things that simply do not exist for plain text — font style, page
layout, handwriting, text colour, print quality. Those are document-image features, not text
features. "Gold labels" is also wrong because using the label as a feature is circular.

### Representing the text (p. 54-58)
Two strategies:
- **Sequence representation**: keep word order, get a grammatical-semantic structure.
- **Bag-of-words (BoW)**: drop order, keep word frequencies as a fingerprint.

**Bag-of-words concretely (p. 55, 59):**
- Corpus: doc1 = "Vaccines are safe", doc2 = "Vaccines cause autism".
- Vocabulary = [vaccines, are, cause, safe, autism] (size 5).
- doc1 vector = [1,1,0,1,0]; doc2 vector = [1,0,1,0,1].

**Term-document matrix (p. 56, Jurafsky Fig 15.2):**
A small Shakespeare-plays example: four words (battle, soldier, fool, clown) × four plays. Each
play becomes a column vector of length 4. You can plot two dimensions (fool × battle) and the
comedies cluster together.

**TF*IDF (Spark-Jones 1972, p. 57):**
- Words in every document (the, is, of) have low information value.
- Words appearing once anywhere are idiosyncratic.
- TF * IDF = (frequency of term t in doc d) × (inverse of how many documents contain t).
- Sweet spot: terms typical of a topic/domain but not too common.

**N-grams (p. 58):**
- Unigram = single word ("the"), bigram = two-word sequence ("the_room"), trigram = three-word
  sequence ("the_room_was").
- Higher N → richer info but more sparsity and more features.
- **Character n-grams** like [th, he, e\_, \_r, ro] are more frequent than word n-grams →
  helpful when data is sparse, robust to typos and morphology.

**Bag-of-bigrams (p. 60):** same idea but the vocabulary is over bigrams.

**TF*IDF bag-of-words (p. 61):** A real tweet's BoW vector is mostly zeros, with non-zero entries
at the words that occurred, weighted by TF*IDF.

**One-hot encoding (p. 63):** each vocabulary word gets a vector with 1 in its own position and
0 elsewhere. Text = sum of one-hot vectors (presence, counts, or weights). Vectors become **huge
and sparse**, even when restricted to informative words.

## 8. Feature engineering (p. 66)

Definition (quiz Q9): **transform raw text into features usable by an ML model.**

Approach:
- Choose properties of the text to become features (or feature functions) in a vector.
- Run experiments to pick the features that work best.
- **Feature ablation**: try different feature sets, compare scores. Example table (p. 66):
  Unigrams 0.78 — Bi-grams 0.56 — Lemmas 0.72 — UniPoS 0.69 — Uni NoStopw 0.81 — Uni Freq10 0.76
  — Uni Freq100 0.72 — Uni deps 0.64.
- Other choices: multiword expressions (collocations, idioms), compound splitting, frequency
  cutoffs, stop word removal.

Distractors in quiz Q9 are wrong because feature engineering is not about cleaning data, not
about increasing model complexity, not about reducing data size.

## 9. Rule-based vs ML vs deep learning (p. 30, 31, 35)

Rule-based: "tell the machine exactly what to do under specific circumstances". Becomes too
complex to maintain, but still used by some companies (p. 30). Examples of lexicon-rule systems:
VADER, NRC, LIWC.

Two technical problems with rules:
- **Ambiguity** — same word in different contexts (low prices vs low ceilings, p. 31).
- **Negation and intensifiers** — "staff is not friendly but the place is clean" needs scope
  rules; "very friendly" needs intensifier handling.

**Law of diminishing returns (p. 34):** writing more rules gives less and less recall gain. N=1 →
50% recall, N=2 → 60%, N=3 → 65%, N=4 → 68%. Exponential effort for marginal improvement.

Why machine learning (p. 35):
- Hand-crafted models (grammars) failed empirical tests.
- Variation and dynamics of language is far bigger than realised.
- Rule systems are too complex, difficult to maintain, and psychologically unrealistic (children
  don't learn rules).
- **"Machine learning appears to work better than any set of the rules we invented so far."**

This is the slide that backs quiz Q2 ("early NLP used rules"). The historical arc — symbolic
(rules) → statistical (classical ML) → neural (deep learning) — is implied but not stated as a
timeline in the deck. Hybrid systems combine ML and rules.

## 10. Supervised ML pros/cons

### How supervised ML works (NLTK book, p. 36)
Training: text → feature extractor → feature vector + label → ML algorithm → classifier model.
Prediction: text → feature extractor → feature vector → classifier model → predicted label.

The label can be anything ("sad", "pro/against"). The prediction is meaningful for people but
"not for a machine" — that differs from how children learn language (p. 37).

### Supervised ML system components (p. 39)
- **Training corpus** — representative texts annotated with interpretation labels (POS, word
  meanings, entity phrases, syntactic dependencies, events, sentiments).
- **Tag set** — set of labels described in a code book with examples and decision criteria. More
  fine-grained → more complex for annotators.
- **Feature selection** — represent text as a set of features so a computer can compare training
  texts T₁..ₜ associated with labels L₁..ₗ to a test text T_test.
- **Classifier** — matches features of T_test to features of training texts to predict L_test.

### Generative vs discriminative (p. 64)
- **Generative** (Naive Bayes): builds a model for each class predicting which words are most
  likely given the class.
- **Discriminative** (logistic regression): learns how useful specific features are for
  predicting a class.

### Underfitting and overfitting (p. 63, 67)
- **Underfitting**: model too simple to explain variance; cannot find enough class-discriminative
  properties.
- **Appropriate fitting**: smooth boundary that generalises.
- **Overfitting**: forcing the model through every training point; learns idiosyncratic specifics
  (e.g. learning the filename as a feature).
- Other problem: **data sparseness** — variation and dynamics underestimated by the training
  data.

### Disadvantages of supervised ML (p. 68)
- **Requires handcrafted annotations** (supervision)
- time-consuming and expensive
- has to be redone for **each task / domain**
- has to be redone every 5-10 years due to language change and world change
- Solution direction: unsupervised learning / language models.

Quiz Q10 picks the annotation-cost answer. The wrong distractors:
- "Unable to generalize to unseen data" — wrong, supervised ML can generalise within the training
  distribution; that's its main strength.
- "Requires unannotated data" — wrong, that's unsupervised.
- "Doesn't work with text" — wrong, text classification is one of its biggest success stories.

---

## Likely exam traps

- "Pipelines are rigid sequences" — wrong. They're modular and share early steps across tasks.
- "Tokenisers always split hyphenated terms into N tokens" — wrong. It depends on the tokeniser.
- Stand-off annotation does **not** mean "no processing required". It means annotations live in a
  separate layer and point at offsets in the raw text.
- Gold data is **not** "data used for training" in general. It is human-annotated data. Training
  data can be silver, bronze, or even unannotated.
- Features ≠ document-image properties. Font, page layout, handwriting, text colour, print
  quality are not features of text — they are properties of the document image.
- The gold label cannot be a feature (circular prediction).
- Feature engineering is not "cleaning data" or "reducing data size". It is transforming raw text
  into a feature vector for ML.
- Variation and ambiguity are opposites: variation is many surface forms for one meaning;
  ambiguity is one surface form for many meanings. Both are problems for text mining.
- WordNet movement count: the slide says 4,000; the quiz says "more than 3,000". 4,000 > 3,000 so
  the quiz answer is consistent. Don't pick "between 300 and 3,000".
- IAA < 50 Kappa = task too difficult. IAA is the ceiling of NLP performance.
- The disadvantage of supervised ML is the cost of **annotation**, not failure to generalise.

---

## Self-quiz (cover the answers)

**Q1.** A tokeniser is asked to process "twenty-first-century". How many tokens does it produce?
- a) two, splitting on the first hyphen only
- b) **It depends on the tokeniser's setup**
- c) one, treating the hyphenated form as a single unit
- d) four, splitting on every hyphen and the suffix

**Q2.** Which of the following is an example of *variation* rather than ambiguity?
- a) "bank" meaning a financial institution or a riverside
- b) "I saw her duck" — duck as verb or noun
- c) **"Ms G Torretta", "Gina Torretta" and "the chairman" referring to the same person**
- d) "Fruit flies like a banana" parsed two ways

**Q3.** What is the difference between inline and stand-off annotations?
- a) Inline is for images, while stand-off is used for plain text
- b) Stand-off is embedded inside the text, inline is in a separate file
- c) **Inline is inserted directly into the text; stand-off lives in a separate layer pointing
  at offsets**
- d) Inline requires no preprocessing of the source text before tagging

**Q4.** Which is NOT a typical feature used in text classification?
- a) Sentence length, measured in tokens
- b) Punctuation marks in the sentence
- c) Part-of-speech tags from a tagger
- d) **Font style and page layout**

**Q5.** What does TF*IDF do?
- a) Lowercases all tokens before counting
- b) **Weights words by frequency in the document and rarity across the corpus**
- c) Removes stop words from the vocabulary
- d) Adds part-of-speech tags as extra features

**Q6.** Bronze data is:
- a) Data labelled by humans following a code book
- b) **Data labelled by a machine without any human validation**
- c) Raw, unprocessed text held back as test material
- d) Data labelled by a machine and validated by humans

**Q7.** Which problem describes error propagation in NLP pipelines?
- a) **Mistakes from early modules (e.g. tokenisation) corrupt downstream output**
- b) Two modules give conflicting outputs on the same span
- c) Each module needs its own training data and tag set
- d) The same word has multiple meanings in different contexts

**Q8.** Why is machine learning preferred over hand-crafted rules in modern NLP?
- a) Rules are too cheap to license at scale
- b) **Variation in language is larger than expected and rules don't scale; ML works better
  than any rules so far**
- c) Children learn languages by memorising rules from textbooks
- d) Rules cannot be combined with lexicons or gazetteers

**Q9.** Which statement about supervised ML in NLP is FALSE?
- a) Annotations are time-consuming and expensive to produce
- b) It needs handcrafted annotations to train on
- c) **It does not work with text data**
- d) Annotations are task and domain-specific

**Q10.** What is the primary goal of feature engineering?
- a) Cleaning typos and encoding errors in the raw data
- b) Increasing the model's capacity and parameter count
- c) Shrinking the dataset down to a manageable size
- d) **Transforming raw text into vector features usable by ML**

**Q11.** Which of the following is TRUE about WordNet?
- a) Each word has on average 7.8 senses, equally for all parts of speech
- b) **It contains more than 3,000 words for movement (the slide shows around 4,000)**
- c) It contains about 300 words for movement only
- d) It contains only nouns, no verbs or adjectives

**Q12.** In CoNLL IOB format, what does B-Location mean?
- a) **Beginning of a Location entity**
- b) Bottom of a location label column
- c) Boundary of a location span
- d) Background of a location reference

**Q13.** Which modules are most likely shared across an NER pipeline and a sentiment-analysis
pipeline?
- a) Word sense disambiguation and sentiment scoring
- b) Hedging detection and event extraction
- c) Entity linking and dependency parsing
- d) **Tokenisation, sentence splitting and POS tagging**

**Q14.** What does Inter-Annotator Agreement (IAA) measure, and what does a low IAA imply?
- a) Cost of annotation; low IAA means the work was cheap
- b) Speed of annotation; low IAA means slow annotators
- c) Total number of annotations produced; low IAA means few items annotated
- d) **Agreement between annotators (chance-corrected); low IAA (<50 Kappa) means the task
  is too hard**

**Q15.** Which of the following best characterises overfitting?
- a) **The model learns idiosyncratic specifics of the training data (e.g. file names) that
  don't generalise**
- b) The model is too simple to explain the variance in the data
- c) The model has far too little training data to learn from
- d) The model uses too few features to discriminate classes

---

## What's in the quiz but NOT in these slides

- Quiz Q5's specific British vs American "color/colour" example is not in the slides. The
  *concept* of variation (many words for one referent) is covered on pp. 22-28 with examples
  about person reference (5,000 person words in WordNet, "Gina Torretta" / "Ms Torretta" / "the
  chairman").
- Quiz Q2's framing of "early NLP used rules" is consistent with the deck but not stated as a
  historical timeline. The slides on pp. 30, 31, 35 say rule-based systems exist, are still used
  by some companies, hit a law of diminishing returns, and were eventually outperformed by ML.
- WordNet movement count discrepancy: slide title (p. 25) says "4,000 words for movements", quiz
  Q3 says "more than 3,000". Both are consistent (4,000 > 3,000), so the quiz answer "more than
  3,000" is correct — just be aware the exact slide number is 4,000.
