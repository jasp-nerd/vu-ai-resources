# 07 — Final Exam Prep (built from the 2025 paper)

Companion to the other study summaries. The structure here mirrors the **2025 exam** ([exam_2025_answers.md](../exam_2025_answers.md)) plus topics from the [quiz_answers.md](../quiz_answers.md) that the 2025 paper skipped but the real exam may still touch (mainly topic modeling and a few sentiment-evaluation details).

Each section answers two questions:

1. **What does the exam actually ask?** — the question pattern, not just the term.
2. **What's the distinction you have to nail?** — the contrast with the distractors, because the wrong options on this exam are deliberately close to the right one.

If a concept is already well covered in the older summaries I just point to the file and add the missing nuance.

---

## 1. Linguistics & Pragmatics

The exam tests **terminology** and **the ability to label a sentence**. Memorising the terms is not enough — you have to apply them to a one-line example.

### 1.1 Phrase types (NP, VP, PP, AdjP)

A phrase is named after its **head**:

- **NP (Noun Phrase)** — head is a noun. *"The Text Mining Course"*, *"the place of crime"*.
- **VP (Verb Phrase)** — head is a verb. *"was seen at the place of crime"* (head = *was seen*, contains a PP modifier).
- **PP (Prepositional Phrase)** — head is a preposition. *"at the place of crime"* (preposition *at* + NP *the place of crime*).
- **AdjP (Adjective Phrase)** — head is an adjective. *"very tall"*.

**Exam trap (Q1):** *"was seen at the place of crime"*. The whole phrase is a **VP** because *was seen* is the head. The PP *at the place of crime* lives **inside** the VP. A common wrong choice is "PP that points to the location" — that describes only the embedded PP, not the whole phrase.

**Rule of thumb when labelling:** find the head verb/noun/preposition first, *then* decide what the modifier inside is.

### 1.2 Parsing vs Chunking


|                        | Chunking                                                     | Full parsing                               |
| ---------------------- | ------------------------------------------------------------ | ------------------------------------------ |
| Output                 | Flat list of constituents (NP, VP, PP) up to a shallow depth | Full hierarchical tree or dependency graph |
| Speed                  | Fast, robust                                                 | Slower, more fragile on noisy text         |
| Captures dependencies? | No                                                           | Yes (constituent OR dependency relations)  |
| Captures semantics?    | No                                                           | No (still syntax)                          |


**Exam trap (Q2):** chunking is **not** "NP-only" and does **not** give semantic relations. The right framing is "**faster and more robust than full parsing**."

**Constituency vs dependency parsing (quiz):**

- *Constituency* parser → hierarchical tree of NPs, VPs, PPs etc.
- *Dependency* parser → flat directed relations between words (subject, object, modifier).

Don't confuse the two; the quiz reverses the definitions as a distractor.

### 1.3 Lexical relations

Memorise four words:

- **Polysemy** — one form, multiple **related** meanings. *head of department / head of a beer / head as body part*. The exam (Q3) tests this with "a word can have multiple meanings."
- **Synonymy** — different forms, same meaning. *big / large*.
- **Meronymy** — part-of relation. *wheel* is a meronym of *car*; *"lecture room"* is a meronym of *"university building"* (quiz).
- **Antonymy** — opposite meaning. *hot / cold*.
- **Hyponymy / Hypernymy** — IS-A. *dog* is a hyponym of *animal*.
- **Homonymy / Homophony** — different unrelated meanings happen to share a form/sound. *bank* (river) vs *bank* (financial).

**Polysemy vs homonymy is the classic trick:** polysemy = related senses (head of body, head of department both involve "top/leader"); homonymy = unrelated coincidence.

### 1.4 Ambiguity vs Variation

This is the framing question on the exam (Q4) and it is **abstract**, not example-based.

- **Ambiguity** — *one form, many meanings*. There are **more things than words**, so words have to be reused.
- **Variation** — *one meaning, many forms*. There are **more words for the same thing**, so a concept can be referred to in many ways.

When the exam says *"There are more things than words but also more words for the same thing"* — that's both phenomena together, so the answer is **"Variation and ambiguity."**

Sub-types of ambiguity:

- **Lexical / semantic ambiguity** — one word has multiple meanings (*bank*, *star*).
- **Syntactic / structural ambiguity** — one sentence has multiple parse trees (PP-attachment).
- **Referential ambiguity** — a referring expression can point to multiple entities (which *John*?).
- **Pragmatic ambiguity** — meaning depends on context (irony, metaphor).

### 1.5 PP-attachment (the exam's favourite ambiguity)

The exam tests this **twice** (Q5 and Q6):

> "The burglar threatened the student with the knife."

The PP *with the knife* can attach to:

- The **verb** *threatened* → it's the **instrument** of threatening (the burglar uses the knife).
- The **object** *the student* → describes the student (the student has the knife).
- The **subject** *the burglar* → describes the burglar (he has the knife).

This is **syntactic / structural ambiguity** because the *structure* of the parse tree differs across readings — same words, different attachment.

> "Harvey waved at the girl in her bikini."

For *Harvey* to wear the bikini, the PP *in her bikini* must attach to the **subject** (Harvey). If it attaches to the object (the girl) she wears it; if it attaches to the verb (waved) the waving happens "in her bikini" (semantically odd).

**Trick:** to read the question right, ask *"which constituent does the PP modify to produce that interpretation?"* — that's exactly what the answer choices give you.

### 1.6 Pragmatics

**Pragmatics** = how meaning is shaped by **context**, going beyond the literal meaning encoded in the words.

Key phenomena:

- **Metaphor** — transfer property from one concept to an unrelated concept. *"Time is money."*
- **Metonymy** — refer to something by something **related**. *"The White House said..."* (the government, not the building).
- **Indirect speech acts** — form ≠ function. *"Can you pass the salt?"* is a request, not a yes/no question.
- **Irony / sarcasm** — meaning is the opposite of the form.

The exam (Q7) wants you to recognise: *pragmatic use creates **new meanings in context**, which is hard for computers.* The wrong choices reframe pragmatics as "bad language" or "emotion" — neither is right.

**Semantics vs pragmatics:**

- *Semantics* = literal, context-free meaning.
- *Pragmatics* = meaning shaped by context.

### 1.7 Parts of Speech

**Open class (content words)** — carry meaning; new ones constantly added:

- Nouns (N)
- Verbs (V)
- Adjectives (A)
- Adverbs (R)

**Closed class (function words)** — finite, grammatical glue:

- Pronouns, prepositions, conjunctions, determiners, auxiliaries.

**Exam Q8** asks which option is *exclusively* content words. *"Nouns and Verbs"* is the only fully-content pair among the choices. *"Adverbs and Prepositions"* mixes content (R) and function (P); *"Nouns and Pronouns"* mixes N and function.

### 1.8 Penn Treebank POS tags

The exam expects you to recognise these tags:


| Tag     | Meaning                           | Example                           |
| ------- | --------------------------------- | --------------------------------- |
| **NN**  | common singular noun              | *weed*, *dog*                     |
| **NNP** | proper noun (a name)              | *Woody*, *Harrelson*, *Amsterdam* |
| **VB**  | verb, base form                   | *eat*                             |
| **VBZ** | verb, 3rd-person singular present | *is*, *eats*                      |
| **VBG** | verb, gerund / present participle | *smoking*                         |
| **VBD** | verb, past tense                  | *ate*                             |
| **VBN** | verb, past participle             | *eaten*                           |
| **JJ**  | adjective                         | *fast*                            |
| **RB**  | adverb                            | *not*, *anymore*, *quickly*       |
| **DT**  | determiner                        | *the*, *a*                        |
| **IN**  | preposition                       | *at*, *in*                        |


**Q9 trap:** *"not"* and *"anymore"* are **adverbs (RB)**, not adjectives (JJ/A). *"weed"* is a common noun (NN), not a proper noun (NNP). *"Woody Harrelson"* is two proper nouns (NNP NNP), not common.

### 1.9 Morphology (quiz only)

- **Inflection** — change grammatical features without changing the lemma. *walk → walked* (tense), *dog → dogs* (number). The word's POS stays the same.
- **Derivation** — create a new word, often a new POS. *happy (adj) → happiness (noun)*.
- **Compounding** — fuse two words into one. *blackboard*, *firetruck*.
- **Affixation** — adding a prefix or suffix (a *morphological* process, covers both inflection and derivation).

The quiz tests this: "adding a prefix to alter meaning" = morphology; "tense or number changes" = inflection.

---

## 2. NLP Pipeline & Pre-processing

### 2.1 Pipeline order

The lecture's standard order is:

1. **Tokenization** — break text into tokens.
2. **Sentence splitting** — group tokens into sentences (or split first if you treat it that way, but the slides put tokenization first).
3. **POS tagging** — label each token's part of speech.
4. **Parsing & Chunking** — build phrase structure.
5. **NER, coreference, semantic roles, etc.** — downstream tasks.

**Exam Q10 nuance:** the textbook order sometimes puts sentence splitting first (sentences are the "bigger" unit). The lecture slides put tokenization first because that's how spaCy and modern libraries actually work. **Answer per slides: tokenization first.**

### 2.2 Things that complicate sentence splitting

The slide lists, and the exam (Q11) asks you to recognise, **all of these**:

- **Titles & abbreviations** with periods — *Dr., Mrs., Mt., U.S.*
- **Numbers** with decimals — *7.5*
- **Domain names / abbreviations** — *Bol.com*, *etc.*
- **Tables, formulae, HTML markup, tabs, newlines** — non-prose structure.

The right answer is *"all of the above"* whenever the question lists titles, formulae, tables.

### 2.3 Tokenization edge cases (quiz)

Hyphenated compounds (*state-of-the-art*) can become 1, 3, or 4 tokens depending on the tokeniser's rules. There is **no single right answer** — "it depends on the tokeniser" is the exam answer.

### 2.4 WordNet scale (Q12)

You don't need to know the exact numbers, just the **order of magnitude**:

- Words referring to a **person** in WordNet: ~5,000 → answer is "**more than 2,000**".
- Words referring to **movements** in WordNet: > 3,000.

Conceptual point: natural language has *enormous* lexical variation for everyday concepts — that's the *variation* problem from §1.4 made concrete.

### 2.5 Annotation types (quiz)

- **Inline annotation** — labels embedded in the text itself (XML tags, BIO tags interleaved).
- **Stand-off annotation** — labels stored in a separate file/layer with offsets pointing into the source text. Preferred for multi-layer annotation (you can have several stand-off layers over one document).

**Gold / Silver / Bronze data:**

- **Gold** — fully manually annotated by humans. Most reliable, most expensive.
- **Silver** — semi-automatic with some human verification.
- **Bronze** — fully automatic, minimal or no human involvement. Cheap, noisy.

### 2.6 Features in NLP

A "feature" is any property of a token, sentence, or document that goes into a model. Valid features include: sentence length, punctuation, POS tags, lemmas, word shape, n-grams. **Not features:** the labels themselves ("gold labels"), or physical/visual properties of the document (font, page colour, handwriting).

---

## 3. Representations (BoW, n-grams, embeddings)

This block is the **most heavily tested** section after NERC. Six questions on the 2025 exam (Q13–Q19).

### 3.1 Bag-of-Words (BoW)

A document is represented as a vector of **word frequencies (or 1/0)** over the vocabulary. Word **order is discarded**.

- *"The chicken produced an egg"* and *"the egg produced a chicken"* → identical BoW vectors.
- Two documents are **BoW-similar** to the extent that the **same words appear** (regardless of order or position).

**Exam Q13/Q14 distractors:**

- "BoW is more similar if order is similar" → **wrong**, order is gone.
- "BoW is more similar if n-grams match" → that's an **n-gram representation**, not BoW.
- "BoW is more similar if most-frequent words match" → frequent words (*the*, *of*) match everywhere, so this isn't informative; the actual definition is vocabulary overlap regardless of order.

### 3.2 N-grams

An n-gram is a contiguous sequence of *n* tokens or characters.

- **Word bi-grams** of *"the chicken produced an egg"*: *(the, chicken), (chicken, produced), (produced, an), (an, egg)*.
- **Character bi-grams** of *"the"*: *(t, h), (h, e), (e, _)*.

**Why character n-grams help (Q15):** there are far fewer distinct characters than words, so **character n-grams are more frequent** than word n-grams. This makes them useful when data is sparse (rare words, typos, morphologically rich languages).

> *Character bi-grams are more frequent than word bi-grams* — that is the exam's exact answer.

The other claims are wrong because:

- Character n-grams capture **form**, not meaning.
- Word tri-grams are **rarer** than character tri-grams (not more frequent).

### 3.3 One-hot encoding

Each word is represented as a vector of length |V| (vocabulary size) with a 1 in the position of that word and 0s elsewhere.

- **Pros:** simple, exact.
- **Cons:** huge (V can be 100k+), **sparse**, all words are equidistant — *cat* and *dog* are as far apart as *cat* and *aardvark*. No notion of similarity.

### 3.4 Word embeddings (static)

Dense vectors (~100–500 dimensions). Learned by **predicting context words** (word2vec skip-gram, CBOW) or by factorising co-occurrence statistics (GloVe).

The **distributional hypothesis** (Firth, Harris): *"You shall know a word by the company it keeps."* Words that appear in similar contexts get similar vectors.

What embeddings capture:

- **Semantic similarity** — *cat ≈ dog* vectorially.
- **Syntactic regularities** — *walk : walked :: run : ran* (linear offsets).
- **Morphological regularities** — singular/plural, adjective/comparative.
- **Analogies** — *king − man + woman ≈ queen*.

**Exam Q17 answer:** embeddings capture *"various relations, including syntactic, morphological and semantic"* — **not** only one type.

**Q16 — advantage over one-hot:**

- **Condensed** (dense, low-dimensional).
- **Robust** — semantically similar words match even if the test word wasn't seen.

Note the question asks about *"robust **and** more condensed"* (both true). The distractor "**precise** and condensed" reverses this — embeddings are not more *precise* than one-hot (one-hot is exactly precise per type); they're more *robust*.

### 3.5 Static vs contextual embeddings


|                   | Static (word2vec, GloVe, fastText)                            | Contextual (BERT, ELMo, GPT, …)                                 |
| ----------------- | ------------------------------------------------------------- | --------------------------------------------------------------- |
| Vector per token  | one per **type** (the word *star* always has the same vector) | one per **occurrence** (different vector depending on sentence) |
| Captures polysemy | No                                                            | Yes                                                             |
| Trained how       | Skip-gram / CBOW / matrix factorisation                       | Masked LM / next-token prediction with attention                |


**Exam Q18:** *"star"* in *"the star is many lightyears away"* (astronomy) vs *"the star went into rehab today"* (celebrity) needs **different vectors**. Only a **contextual / transformer-based** embedding (BERT et al.) gives that. One-hot is one vector per type, TF-IDF is one weight per type, **averaged** embeddings still produce one type vector — none of these distinguish senses.

### 3.6 What goes into sequence labelling

For **sequence labelling** (POS, IOB) you need one vector **per token** *and* preserve token **order**. Specifically:

- A **sequence of one-hot encodings** — one vector per token, in order. ✓
- Averaged embeddings → loses order. ✗
- A single one-hot of the whole sentence → loses everything. ✗
- A bag-of-word-embeddings → loses order. ✗

The exam (Q19) asks this verbatim.

### 3.7 TF-IDF (mentioned in entity linking)

**Term Frequency × Inverse Document Frequency.**

- TF = how often the term appears in the document.
- IDF = penalises terms that appear in many documents (log N / df).

Used to score document-document similarity (and as a baseline keyword extractor in topic modeling).

---

## 4. Named Entity Recognition & Classification (NERC)

The biggest topic on the exam. Nine questions (Q20–Q28).

### 4.1 Three tasks

- **NER (Recognition)** — identify the **span** that refers to a named entity.
- **NEC (Classification)** — assign a **type** (PERSON, LOCATION, ORG, …).
- **NEL / NED (Linking / Disambiguation)** — connect the mention to a specific entry in a **knowledge base** (Wikipedia, DBpedia).

Recognition and classification are usually trained jointly as one sequence-labelling problem (IOB tags include the type).

### 4.2 BIO / IOB annotation

Each token receives one of:

- **B-{type}** — beginning of an entity of that type.
- **I-{type}** — inside (continuation) of an entity.
- **O** — outside any entity.

**Why BIO over class-only labels?** It encodes **entity boundaries**, so two adjacent entities of the same type can be distinguished. *"London Berlin"* → *B-LOC B-LOC* (two entities) vs *B-LOC I-LOC* (one entity spanning both — wrong).

### 4.3 IO vs IOB (Q20)

There are two variants:

- **IOB / BIO** — uses **B-, I-, O**. Full version.
- **IO** — uses only **I-, O** (no B). Cheaper but cannot distinguish two adjacent same-type entities.

The exam example uses *"President/I-PER Obama/I-PER ... Germany/I-LOC"* — note **no B- tags**. That's the **IO** variant. It still classifies (I-PER, I-LOC) so it's "entity detection **and classification**" — not just "detecting all words."

### 4.4 Referring vs named entity expressions

- **Referring expression** — any expression that picks out an entity. Includes proper nouns, common noun phrases, pronouns, even verbs/adjectives for events and properties.
- **Named entity expression** — a stricter subset: definite NPs and proper nouns.

**Exam Q21:** named entity expressions can refer to **people, organisations, places, and events**. They are not limited to people, and not all referring expressions are named entities (pronouns aren't).

### 4.5 Extent and nesting (Q22)

The boundary of an entity is hard to fix because:

- Other tokens beyond the proper name may be included: *"the CEO of the US-based company Facebook"* — is the entity *Facebook*, *the company Facebook*, or the whole NP?
- Entities may **nest**: *"[ the [CEO] of the [US]-based company [Facebook] ]"* contains three nested entities.

That nesting + token-inclusion is what makes **extent** a problem.

### 4.6 Feature families

NERC features come in three families (Nadeau & Sekine 2007):


| Family                | Examples                                                                                               |
| --------------------- | ------------------------------------------------------------------------------------------------------ |
| **Word-level**        | case (Xxx, XX), punctuation, digits, character n-grams, morphology, POS, word shape                    |
| **Lookup**            | gazetteers (first-name list, country list), Wikipedia titles, organisation cue words                   |
| **Document & corpus** | other occurrences of the same word in the document, position in sentence/paragraph, document frequency |


**Context features** are a sub-type of word-level features: *the words/POS tags before and after the target token*.

**Exam Q23 trap:** *"appearance in named entity gazetteers"* is a **lookup feature**, **not a context feature**. Context = surrounding tokens; lookup = external lists. The other three options (preceding words, following words, surrounding POS tags) are all context features.

### 4.7 Word shape

A compact code of the orthography:


| Word         | Long shape | Short shape |
| ------------ | ---------- | ----------- |
| *Joe*        | Xxx        | Xx          |
| *spaCy*      | xxxXx      | xXx         |
| *VW2024*     | XXdddd     | Xd          |
| *12-10-2007* | dd-dd-dddd | d-d-d       |


X = uppercase letter, x = lowercase letter, d = digit. Useful because most names share shape patterns even across languages.

### 4.8 Factors that impact NERC performance (Q24)

The slide lists five factors. Memorise them:

1. **Annotation of spans / nesting** (inter-annotator agreement is low).
2. **Genre of text** (news vs Twitter vs medical).
3. **Type of entity** (PERSON is easier than fine-grained types).
4. **Amount of training data**.
5. **Difference between training data and test data** — domain dependency, drift over time.

**"Number of entities"** is **not** on the list. That's the answer to "which does **NOT** impact performance."

A second distractor that *does* impact performance: *text font size* — quiz Q10 lists this as the obvious wrong-answer (text font size doesn't change the linguistic content the NER model sees).

### 4.9 Temporal mismatch (Q25)

You train on news from 1990, test on news from 2020. What drifts?

- **Word shapes / case / orthography** — stable. *Xxx* still looks like a name.
- **Surrounding syntactic context** — stable. *"X said that..."*, *"according to Y..."* hasn't changed.
- **Entity names themselves** — **drift heavily**. New people, companies, places, products appear; old ones fade.

So the mismatch is: **entity names differ, but word features and surrounding words stay similar.**

This matters because a model that learned to predict "PERSON" partly by memorising 1990 names will fail on 2020 names — even though every other feature looks the same.

### 4.10 Metonymy (Q26)

**Metonymy** — using one expression to refer to a **related** concept of a different type. The same surface form can mean:

- *"The US said..."* — country name standing for the **government** (ORG).
- *"The US won gold"* — country name standing for the **team** (sometimes PER).
- *"the US"* literally — the **location** (LOC).

**Why is this a problem for NEC but not NER?**

- **Recognition** still finds the span *"US"*.
- **Classification** has to pick the right type **based on context** — and the surface form is identical across types.

Other examples: *Holland*, *Mexico*, *Ford*, *Washington*, *Downing Street*.

### 4.11 BiLSTM-CRF (Q27)

Sequence labelling model with three layers:

1. **Embedding layer** — concatenates a **word embedding** with a **character-level embedding** (the char-LSTM recovers word-shape information word embeddings lose).
2. **BiLSTM layer** — two LSTMs read the embedding sequence in opposite directions: a forward (left-to-right) LSTM and a backward (right-to-left) LSTM. The outputs at each position are concatenated, giving a representation aware of both left and right context.
3. **CRF layer** — instead of independent token predictions, the CRF models the **dependencies between adjacent tags** (e.g., *I-PER cannot follow B-LOC*). Decoded with Viterbi.

**Exam-line summary:** *"BiLSTM combines word- and character-embedding weights left-to-right and right-to-left."*

### 4.12 Why BERT doesn't need a CRF (Q28)

A pre-trained transformer (BERT) produces **contextual embeddings**: each token's vector already depends on all surrounding tokens, via **attention heads** and **position embeddings**. So sequence dependencies are baked into the token representations themselves — the CRF layer that BiLSTM relied on for tag-to-tag dependencies is no longer the only way to model that.

The other choices are wrong because:

- BERT does **not** learn from unlabeled data the IOB tag sequences (it learns masked-LM and next-sentence, not IOB).
- BERT is not "end-to-end without sequence dependencies" — it represents sequence info, just not via CRF.
- BERT does **not** use gazetteers / word shape / external KBs.

---

## 5. Entity Linking & Coreference

Six questions on the 2025 exam (Q29–Q33 entity linking, Q36–Q37 coreference, plus the calculation Q34 and Q35).

### 5.1 NIL entities and the closed-world assumption

**NIL entity** — a mention in text that has **no corresponding entry** in the reference knowledge base. The lecture example: *Edgar Gonzalez* (a local San Benito shooting victim) has no Wikipedia entry, so an entity linker should output NIL rather than guess a different Edgar Gonzalez.

**Closed-world assumption (CWA)** — *every* target entity is in the database. NIL entities are the **failure** of CWA: their existence is exactly what proves the CWA is unrealistic for general text.

### 5.2 Recall / precision trade-off in EL (Q31)

When you generate **more candidates** per mention before disambiguating:

- **Recall ↑** — higher chance the gold entity is in your candidate set.
- **Precision ↓** — more wrong candidates compete with the right one, so more wrong selections leak through.

This is the standard IR recall/precision trade-off.

### 5.3 Word-based vs graph-based entity linking (Q32, Q33)

The lecture table lays out two approach families. Know both:


|                | **Word-based**                                                                                    | **Graph-based**                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Idea           | Find candidate whose **textual description** is most similar to the mention's surrounding context | Find a set of candidates that are **mutually coherent** via connections in the KB |
| Scoring        | Text similarity (e.g., cosine) weighted by TF-IDF                                                 | Graph centrality / coherence over candidate sub-graph                             |
| Decision unit  | **Local** (per mention, independently)                                                            | **Global / collective** (all mentions in a document jointly)                      |
| Example system | **DBpedia Spotlight**                                                                             | **AIDA**, **AGDISTIS**                                                            |


**Q33 wording trap:** *"Find the candidate with the most similar description to the mention in text"* — that is verbatim the word-based row. The distractor "local" describes the *decision unit* of word-based, not the *approach family*; "global" is the decision unit of graph-based, not an approach family.

**Q32 wording trap:** *"compute global coherence over all entity mentions in a document, according to connections across all target entities in a knowledge base"* — that's the graph-based row almost word-for-word.

### 5.4 Counting TP / FP / FN in EL (Q34)

For a **single mention** with a single gold answer:

- If the system links to the **right entity** → 1 TP, 0 FP, 0 FN.
- If the system links to a **wrong entity** → 0 TP, **1 FP** (the wrong link is a false positive) **and 1 FN** (the correct entity wasn't predicted, so it's a false negative).
- If the system links to **NIL when there is a gold entity** → 0 TP, 0 FP, **1 FN**.
- If the system links to **an entity when the gold is NIL** → 0 TP, **1 FP**, 0 FN.

The exam example: gold = *US_Army*, prediction = *United_States*. The prediction is wrong → **1 FP, 1 FN**.

### 5.5 Commonness score (Q35)

**Commonness(entity | phrase)** = probability that a given **surface phrase** refers to a given **entity**, estimated from Wikipedia link statistics.

$$ \text{Commonness}(e \mid p) = \frac{\text{links}(p \to e)}{\text{links}(p \to \text{any entity})} $$

The crucial bit: **only count links that use the phrase you're asking about.** A different surface form ("GER" instead of "Germany") is a different *p* and doesn't enter the denominator.

Worked example from the exam:

- Surface phrase = *"Germany"*.
- Links *"Germany"* → country Germany: 90.
- Links *"Germany"* → German soccer team: 45.
- Links *"GER"* → country Germany: 10 (**ignored**, different phrase).

Denominator = 90 + 45 = 135. Numerator (country | "Germany") = 90.

$$ \text{Commonness}(\text{country} \mid \text{"Germany"}) = \frac{90}{135} = \frac{2}{3} $$

### 5.6 Coreference

**Coreference** = two or more expressions that **refer to the same entity** in the world. The two expressions form a *coreference chain*.

Examples:

- *"Lincoln returned to Springfield and resumed his successful law practice."* → *Lincoln* and *his* are coreferent (same person). Relation = **coreference**, **not** possession (the syntactic relation is possessive, but the *referential* relation between the two surface forms is coreference).
- *"Hozier released the EP Take Me to Church ... with the title track becoming his breakthrough single after it went viral."* → two chains:
  - Chain 1: *Hozier* ↔ *his*.
  - Chain 2: *the title track* ↔ *his breakthrough single* ↔ *it* (all three refer to the song *"Take Me to Church"*).

**Trick on the multi-chain question (Q36):** find every expression that refers to the title track and group them all in one chain. The answer must contain **all three** items, not just two.

---

## 6. Sentiment & Evaluation

Three questions on the 2025 exam (Q38–Q40), plus the quiz adds depth.

### 6.1 Agenda setting (Q38)

In any opinion text, the **author chooses** what aspects to bring up at all. That selection is itself subjective — a hotel reviewer who mentions the breakfast and not the location is implicitly judging which aspects matter. **Agenda setting is the subjective choice of topics/aspects to mention**, separate from the polarity of the actual claims.

### 6.2 Levels of sentiment analysis

- **Corpus level** — overall sentiment across many texts.
- **Document level** — one sentiment per document (e.g., a movie review = positive).
- **Sentence level** — sentiment per sentence.
- **Phrase / aspect level** — sentiment paired with a specific target.

**General sentiment analysis** assigns a sentiment to a *document or sentence*.

**Aspect-Based Sentiment Analysis (ABSA)** pairs sentiment with a *specific aspect* of a target:

- *"The battery is great but the camera is terrible."*
- General SA: mixed / neutral.
- ABSA: (battery, +), (camera, –).

**Exam Q39 phrasing:** *"In general SA a sentiment is ascribed to a document or sentence; in ABSA to an opinion target."* The distractors swap this — read the direction carefully.

### 6.3 Opinion holder, target, polarity (quiz)

For each opinion, identify:

- **Opinion holder** — who has the opinion. *"Emma believes the restaurant is fantastic"* → Emma.
- **Opinion target** — what the opinion is about. *"These guys are terrible"* → *these guys*.
- **Polarity** — positive / negative / neutral.
- **Aspect** — which feature/attribute is being evaluated (in ABSA).

### 6.4 Sentiment lexicons and negation

- **Negation words** that flip polarity: *not, never, no, neither* (also *nobody, nothing, nowhere*).
- **Diminishers / hedges**: *hardly, scarcely, barely, slightly* — weaken polarity, don't flip it.
- **Intensifiers**: *absolutely, completely, very* — strengthen polarity.

**VADER** (Valence Aware Dictionary and sEntiment Reasoner) — a rule-based sentiment analyser tuned for **social media** (handles emojis, slang, exclamation marks, capitalisation).

**Ekman's six basic emotions:** happiness, sadness, anger, fear, surprise, disgust.

**Most-used classifier for sentiment (Ravi & Ravi 2015 survey):** **SVM**.

### 6.5 Figurative language

Umbrella term for non-literal language. Includes:

- **Metaphor**
- **Metonymy**
- **Simile** (*"as quiet as a mouse"*)
- **Irony / sarcasm**
- **Hyperbole**

The quiz tests this with an "all of the above" answer for metaphors + metonyms + similes.

### 6.6 F1 per class (Q40 — the calculation)

For a multi-class classifier with K classes, compute precision / recall / F1 **per class**, treating that class as positive and everything else as negative.

For each class *c*:

- TP_c = predicted *c* AND truly *c*.
- FP_c = predicted *c* but actually some other class.
- FN_c = truly *c* but predicted some other class.
- Precision_c = TP_c / (TP_c + FP_c) = TP_c / predicted-as-c.
- Recall_c = TP_c / (TP_c + FN_c) = TP_c / truly-c.
- F1_c = 2 · P · R / (P + R).

**Worked example (Q40):**

100 reviews, gold = 37 positive / 14 negative / 49 neutral.
Predictions = 41 positive (21 correct) / 28 negative (6 correct) / 31 neutral (22 correct).


| Class    | TP  | Predicted | Gold | P             | R             | F1        |
| -------- | --- | --------- | ---- | ------------- | ------------- | --------- |
| Positive | 21  | 41        | 37   | 21/41 ≈ 0.512 | 21/37 ≈ 0.568 | **0.538** |
| Negative | 6   | 28        | 14   | 6/28 ≈ 0.214  | 6/14 ≈ 0.429  | **0.286** |
| Neutral  | 22  | 31        | 49   | 22/31 ≈ 0.710 | 22/49 ≈ 0.449 | **0.550** |


Neutral wins. Tip on the exam: don't compute exact F1 for every class — compute precision and recall in your head, eyeball which class has the highest *harmonic mean*. Here neutral has very high precision (0.71) but the lowest recall of the three (0.45); positive has middling both (~0.54). The harmonic mean penalises imbalance, so the closer-to-balanced of the two is neutral... *just barely*. The exam paper picks neutral.

### 6.7 Macro averaging (quiz Q1)

**Macro-averaged precision / recall** = average of per-class precision / recall, treating each class equally (no weighting by support).

Worked example (quiz): 40 positive, 60 negative; classifier predicts 50 positive / 50 negative; correct = 10 positive + 20 negative.

- Positive: P = 10/50 = 0.2, R = 10/40 = 0.25.
- Negative: P = 20/50 = 0.4, R = 20/60 = 0.333.
- Macro P = (0.2 + 0.4) / 2 = 0.3.
- Macro R = (0.25 + 0.333) / 2 = 0.292 ≈ 0.3.

Both macro P and macro R ≈ 0.3. (Round to the nearest answer option.)

**Micro averaging** would pool TP/FP/FN across classes first; it tends to match accuracy on balanced data.

---

## 7. Topic Modeling & Text Categorisation

**Not on the 2025 exam**, but the quiz devotes 10 questions to it, so it might appear. Cover the high-level distinctions.

### 7.1 Text categorisation vs topic modeling


|                          | Text categorisation (supervised)    | Topic modeling (unsupervised)                                             |
| ------------------------ | ----------------------------------- | ------------------------------------------------------------------------- |
| Topics known in advance? | **Yes** (labelled training data)    | **No** (discovered from data)                                             |
| Approach                 | Train a classifier on labelled docs | Cluster docs or words (LDA, NMF, BERTopic)                                |
| Output                   | Each doc gets a known class         | Each doc gets a distribution over discovered "topics" (clusters of words) |
| New topics?              | Cannot detect unseen topics         | Naturally produces new clusters                                           |
| Maintenance              | Manual label updates                | Re-run model                                                              |


### 7.2 Why universal topics are hard

Topics are **subjective categories**, and both the world and our worldview keep changing. There is no fixed taxonomy that satisfies everyone.

### 7.3 Granularity

How fine-grained you label depends on the **application** — there's no fixed correct number of topics. For news you might use 5 categories; for academic abstracts you might want 100.

### 7.4 Topic modeling with LDA

**Latent Dirichlet Allocation** — generative model. Each document is a mixture of topics; each topic is a distribution over words.

Limitations:

- **Random initialisation + Gibbs sampling** → **unstable** results (different runs yield different topics).
- Bag-of-words assumption → ignores order.
- You have to pick K (number of topics) up front.

### 7.5 Labelling topic-model clusters

The standard automatic approach: extract the **most distinctive** words per cluster using **TF-IDF** (or chi-square, log-likelihood). Domain experts may then refine.

### 7.6 Catastrophic forgetting

When you **fine-tune** a pre-trained model on a new task, it can **forget** what it learned during pre-training (because the same weights are updated for the new task's loss). Mitigated by techniques like adapter modules, low learning rates, or regularisation on the original weights.

### 7.7 Factors when choosing a topic model (Churchill & Singh 2021)

The paper lists: **dataset size**, **noise level**, **document length**, **number of topics**, **interpretability**. It does **not** list "complexity of the algorithm" as a primary factor — that's the quiz's wrong answer.

---

## 8. Self-quiz — close the file and answer

Quick drill from cold. Answers below the questions.

1. *"The PP can attach to the subject, the object, or the verb."* What kind of ambiguity is this?
2. What's the difference between polysemy and homonymy?
3. *"Tokenization comes first, then sentence splitting."* True or false per the slides?
4. Give the BoW vector property that the n-gram property doesn't share.
5. Why does *"star"* need a contextual embedding to be disambiguated, while *"cat"* and *"dog"* could be handled by static embeddings?
6. List the three NERC feature families.
7. *"President I-PER Obama I-PER ..."* — which annotation scheme?
8. Why isn't gazetteer lookup a *context* feature?
9. Train on 1990 / test on 2020. What changes most: word shapes, syntactic context, or entity names?
10. Define metonymy in one sentence. Why does it hurt classification but not recognition?
11. What does the CRF layer of a BiLSTM-CRF do that the BiLSTM alone wouldn't?
12. Why doesn't BERT need a CRF on top?
13. What is the **closed-world assumption** and what observation breaks it?
14. *"Find the candidate with the most similar description to the mention"* — word-based or graph-based?
15. Commonness("Germany" → country) given 90 country links from "Germany", 45 team links from "Germany", and 10 country links from "GER"?
16. AIDA links *"U.S."* → *United_States*; gold = *US_Army*. How many TP/FP/FN?
17. Coreference in *"Hozier ... with the title track becoming his breakthrough single after it went viral."* — list both chains.
18. What is agenda setting and why is it subjective?
19. Macro-averaged precision when class A has P=0.4 and class B has P=0.6?
20. Why is LDA unstable across runs?

Answers

1. Syntactic / structural ambiguity (PP-attachment).
2. Polysemy = one form, **related** senses (*head of body / department*). Homonymy = one form, **unrelated** senses (*bank* river / financial).
3. **True** per the slides — tokenization → sentence splitting.
4. BoW discards order; n-grams preserve local order within each n-gram.
5. *"Star"* is polysemous (astronomical body vs celebrity); static embeddings give one vector per type and can't separate senses. *Cat / dog* are semantically close enough that a single vector per type captures them well.
6. Word-level, lookup (gazetteers), document & corpus features.
7. **IO** (only I-, no B-).
8. Gazetteer lookup matches the *target* token against an external list. Context features look at *surrounding* tokens (preceding/following words and POS).
9. **Entity names**. Word shapes and surrounding syntactic context stay stable.
10. Same surface form refers to **related entities of different types** (*"the US"* = country / government / team). Recognition still finds the span; classification has to pick the right type from context.
11. The CRF models **tag-tag transition probabilities** (e.g., *I-PER cannot follow B-LOC*) so the decoded sequence is globally consistent — independent token classification wouldn't enforce that.
12. Contextual embeddings + attention + position embeddings already encode sequence dependencies, so the per-token representation carries the info the CRF was needed for.
13. CWA = every target entity is in the database. **NIL entities** (mentions with no KB entry) break it.
14. **Word-based**.
15. 90 / (90 + 45) = **2/3**. The "GER" links use a different surface phrase and don't enter the denominator.
16. 0 TP, **1 FP** (wrong prediction), **1 FN** (missed correct entity).
17. Chain 1: *Hozier* ↔ *his*. Chain 2: *the title track* ↔ *his breakthrough single* ↔ *it*.
18. The author **chooses which aspects to mention** at all. That selection is subjective and shapes the reader's perception before any polarity is even applied.
19. (0.4 + 0.6) / 2 = **0.5**.
20. **Random initialisation + Gibbs sampling**: different runs explore different parts of the parameter space and converge to different topic distributions.



---

## 9. Quick-fire mistakes to avoid on exam day

- **PP attachment questions:** read the answer options carefully — *modifies subject / object / verb* is what changes the interpretation.
- **"All of the above"** is correct on this exam **only when the listed items are genuinely all valid**. Don't pick it as a default — the exam also uses *"none of the above"* and single-correct options where the distractors are plausible.
- **POS tag questions:** *not* is RB, *anymore* is RB, *weed* (the noun) is NN, *Woody* / *Harrelson* are NNP. Don't auto-pick the option that "looks longest" — pick by the actual tags.
- **NERC features:** word-level / **lookup** / context / document — gazetteer is *lookup*, surrounding words are *context*. These are sometimes asked as "which is *not* a context feature" — read for the negation.
- **Embeddings:** robust + condensed (not "precise + condensed"). Robust = generalises to unseen words via semantic similarity.
- **Static vs contextual:** if the question contrasts two sentences with the same word and asks which representation distinguishes them, the answer is always **contextual / transformer**.
- **IO vs IOB:** if you see I-tags without any B-tag, it's the **IO** variant.
- **Closed-world assumption:** CWA = everything is in the KB; **NIL entities are the failure of CWA**, not the assumption itself.
- **Commonness score:** denominator only counts links that use the **same surface phrase**. A synonym is a different phrase.
- **TP/FP/FN in EL:** a wrong link is **both** an FP (you predicted wrong) **and** an FN (you missed the right one), never just one.
- **F1 per class:** the harmonic mean penalises imbalance. A class with very high P but mediocre R can still lose to a more balanced one — compute, don't eyeball when scores are close.
- **Macro vs micro averaging:** macro averages **per-class** rates; micro pools all TP/FP/FN first. On balanced data they're close; on imbalanced data they diverge.

Good luck.