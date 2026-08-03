# 05 — Named Entity Recognition & Classification (NERC)

**Source slides:** tm-ba-lecture-5a-nerc.pdf (48 pp.)
**Companion literature:** Maynard et al. 2016 Ch 3; Jurafsky ch 17 (Sequence Labeling for POS and Named Entities); NLTK ch 7 §1, 2, 5, 6; Yadav & Bethard 2019 (NER deep-learning survey)
**Quiz questions drawn from this material:** Named Entities (10 Qs)

---

## Cheat sheet (cover the right column, recall the left)

| Term / question | Answer | Slide |
|-----------------|--------|-------|
| What is an entity? | An instance of a person, organisation, place, object, or incident that exists in some world | p. 3 |
| What is reference? | A communicative act to identify an entity (point at someone, picture identifying someone) | p. 4 |
| What is a referring expression? | Proper noun, common noun phrase or pronoun; for events/properties also verbs, verb phrases, adjectives | p. 5, 6 |
| What is a named entity expression? | Definite noun phrases and proper nouns (a stricter subset of referring expressions) | p. 6 |
| What is NERC? | The task of finding and classifying named entity expressions in text | p. 7 |
| NER vs NEC vs NEL | Recognition = find the span; Classification = assign a type; Linking/Disambiguation = identify which real-world entity in a KB | p. 13, 41 |
| Standard entity types in slides | People, Locations, Organisations, Time, Events | p. 11, 12 |
| BIO / IOB format | Each token gets B-{type} (Begin), I-{type} (Inside), or O (Outside); encodes phrase boundaries plus type | p. 13, 19, 20, 21 |
| Why BIO over class-only? | Better expresses the boundaries of an entity or chunk — adjacent same-type entities can be told apart | quiz Q1, p. 21 |
| Why is NERC hard? | Variation, ambiguity, extent (nesting), types, time, metonymy | p. 14 |
| Variation example | IBM / The Big Blue; New York / NY / The Big Apple | p. 14 |
| Ambiguity example | "may may still rule in may" (name / month / modal); "Apple" the org vs apple the fruit | p. 14, quiz Q7 |
| Metonymy | Same name used for different types — US, Holland, Mexico, Ford → can mean people, organisation, or location | p. 14, quiz Q2 |
| Extent / nesting | "[the [CEO] of the [US]-Based company [Facebook]]" — whole phrase vs three entities; low inter-annotator agreement on borders | p. 14, 33 |
| Word shape for "spaCy" | xxxXx (long shape); xXx (short shape) | p. 16, quiz Q8 |
| Word shape for "Joe" | Xxx (long); Xx (short) | p. 16 |
| Word shape for "12-10-2007" | dd-dd-dddd | p. 16 |
| Three feature families for NERC | Word-level, Lookup (gazetteers/lexicons), Document & corpus | p. 15, quiz Q6 |
| Word-level feature types (Nadeau & Sekine table) | Case, punctuation, digit, character, morphology, part-of-speech, function | p. 16 |
| Gazetteer | A lookup list (e.g., first names, country names, organisation cue words) | p. 17 |
| Document feature examples | Multiple occurrences in context, anaphora, position in sentence/paragraph, meta info, corpus frequency | p. 18 |
| Why document/corpus features help | Coherence: a news article about the US in a period mentions the same people / orgs repeatedly | p. 15 |
| CoNLL-style row contains | Word, POS, Chunk, Short shape, Label (B-/I-/O) | p. 20 |
| What does a CRF do? | Models sequence dependencies between tokens (left-to-right, right-to-left) to predict an IOB sequence | p. 21 |
| Why CRF over independent token classification? | The label of token t depends on the labels of neighbouring tokens — sequence-level decoding | p. 21 |
| Bi-LSTM-CRF idea | BiLSTM reads embeddings left-to-right (l) and right-to-left (r), combines them (c), CRF layer outputs IOB labels | p. 25, 27 |
| Why add character embeddings? | Word embeddings lose structural info (word shape, prefixes/suffixes) — char-LSTM recovers it | p. 27, 28 |
| Pre-trained transformer for NERC | Fine-tune BERT-style model with token-classification head, output is BIO labels; uses word-piece tokenisation | p. 30, 35 |
| Why transformers disambiguate "Apple"? | Contextual embeddings: "Apple delayed the iPhone" vs "Apple with cinnamon" produce different vectors | p. 30 |
| Performance ballpark | Bi-LSTM-CRF reaches ~90 on CoNLL-2003 English; modern transformer-based NER 91+ | p. 29, 36 |
| Cross-domain drop | Up to ~20 F1 points lost when training and test domains differ (CoNLL → DrugNER) | p. 37 |
| Factors impacting NERC performance | Annotation of spans/nesting, genre, entity types, amount of training data, train/test difference | p. 33, quiz Q10 |
| What does NOT impact NERC | Text font size (distractor) | quiz Q10 |
| Entity Linking (NEL) | Establishing the identity of the entity in a reference DB (Wikipedia, DBpedia, YAGO) | p. 13, 41, 42 |
| NIL entity | An entity that has no entry in the knowledge base (e.g., unpopular Edgar Gonzalez) | p. 44, 45 |
| Word-based vs graph-based linking | Word-based: TF/IDF text similarity, local decision per mention (DBpedia Spotlight). Graph-based: candidates coherent via KB connections, global decision (AIDA/AGDISTIS) | p. 47 |
| Coreference resolution | Finding which words/phrases (pronouns, NPs, etc.) refer to the same entity | p. 41, 48 |

---

## 1. What is an entity / named entity

An entity is an instance of something in some world — a person, an organisation, a place, an object, or an incident (p. 3). Entities exist independently of language. Reference is the separate communicative act of pointing to an entity, whether by pointing physically, by showing a picture, or by using words (p. 4).

Text mining cares about the linguistic side: referring expressions. A referring expression in language can be a proper noun, a common noun phrase, or a pronoun. Crucially, for events and properties it can also be a verb, a verb phrase, or an adjective (p. 5). Quiz Q4 keys on this broad definition — the answer is not "only proper nouns" but the wider set including common NPs, pronouns, and (for events/properties) verbs and adjectives.

A named entity expression is a narrower category: definite noun phrases and proper nouns (p. 6). The Abraham Lincoln Wikipedia text (pp. 7–12) is used to walk through what gets marked as a named entity: people (Abraham Lincoln, Lincoln, Stephen A. Douglas), locations (United States, Kentucky, Illinois, Springfield), organisations (Republican Party, Whig Party, U.S. Senate, House of Representatives), times (February 12, 1834, 1846), and events (Civil War, Mexican–American War). The slides note (p. 11) that there is no agreement on which entity types should be in the task — different annotation schemes pick different subsets.

A subtle point (p. 12): "Traveling to work" exists as an event but has no name, so it would not be a named event. "Civil War" is a famous named event, so it counts.

## 2. NER vs NEC vs NEL

Three separate tasks live under the NERC umbrella (p. 13, 41):

- **NER (Recognition)**: detect the phrase that is the name of an entity — the span.
- **NEC (Classification)**: assign an entity type to the phrase (PER / LOC / ORG / ...).
- **NEL (Linking) / NED (Disambiguation)**: establish the identity of the entity in a given reference database (Wikipedia, DBpedia, YAGO).

Coreference resolution is a related task: any phrase (pronoun, NP, abbreviation, acronym) that refers to an entity instance (p. 41).

Quiz Q5 swaps the definitions and is easy to misread. The correct mapping is NER = identifying phrases that refer to named entities, NEC = assigning the type.

Older NERC pipelines (p. 13) chained linguistic preprocessing, gazetteer lookup, grammar rules, and coreference resolution. Modern pipelines reduce to preprocessing → a pre-trained transformer fine-tuned for token classification with BIO/IOB labels.

## 3. Entity types

The slides illustrate the typical set (pp. 8–12): People, Locations, Organisations, Time, Events. Many systems also distinguish Money, Percent, Date, MISC. There is no universal type set — CoNLL uses four core types (PER, LOC, ORG, MISC), OntoNotes uses 18, and fine-grained typing schemes like FIGER use 112 types from Freebase (p. 14).

The slides flag (p. 14) that types can extend to professions and social roles (doctor, patient, teacher, student, criminal, victim), price, and age. The NERD ontology at nerd.eurecom.fr is referenced as a class hierarchy.

A practical wrinkle: results vary a lot per type (p. 33). Persons and locations are usually easier than organisations or events.

## 4. What makes NERC hard

The "hard task" slide (p. 14) lists six headaches.

**Variation.** Popular entities collect aliases — IBM also goes by The Big Blue, New York by NY or The Big Apple. The more popular, the more names.

**Ambiguity.** A surface form may refer to different things. Three flavours:
- Same word lowercased / cased: "may may still rule in may" — the modal verb, a person name (in social media), and the month.
- Same name, different categories: Austin Reed (fashion shop), Parkinson's disease (illness named after a person), Pythagoras' Theorem (mathematical concept).
- Names of works overlapping with everyday referents: Miami Vice (TV series), Brazil (movie).

Quiz Q7 asks for an ambiguity example. The answer is "Apple" the organisation vs "apple" the fruit — same surface form, different entity type. The other options describe variation (multiple names for one entity) or metonymy, not ambiguity.

**Extent / nesting.** "[the [CEO] of the [US]-Based company [Facebook]]" — is the whole phrase one entity or three nested ones? Annotators often disagree on borders, which lowers inter-annotator agreement.

**Types.** No universal type inventory, and fine-grained typing makes the task harder (p. 14).

**Time.** Dates can be absolute (8-3-2022), partial (Tuesday, 8am), or relative (yesterday, this week, next month). Relative expressions need a reference point to resolve.

**Metonymy.** The same name is used for different *types* — "US said…" treats the country name as standing for the government; "Holland", "Ford", "Mexico" similarly slide between location, organisation, and person (p. 14). This is the key distinction quiz Q2 tests. Metonymy is *not* irrelevant for typing — it directly forces the classifier to pick between PER / ORG / LOC based on context.

## 5. BIO / IOB tagging

Sequence labelling for NERC needs to mark not just the type of each token but where the entity phrase begins and ends. The BIO (also called IOB) scheme does both (pp. 13, 19, 20):

- **B-{type}**: token is the Beginning of an entity of that type.
- **I-{type}**: token is Inside (continues) the entity.
- **O**: token is Outside any entity.

The CoNLL example on p. 20:

```
American   NNP  B-NP   Xx    B-ORG
Airlines   NNPS I-NP   Xx    I-ORG
,          ,    O      ,     O
a          DT   B-NP   x     O
unit       NN   I-NP   x     O
...
AMR        NNP  B-NP   X     B-ORG
Corp.      NNP  I-NP   Xx.   I-ORG
```

"American Airlines" is one ORG span (B-ORG, I-ORG); "AMR Corp." starts a new ORG with B-ORG even though I-ORG would also be of type ORG — the B marks the *boundary*. Without B, two adjacent same-type entities would merge.

This is exactly the rationale quiz Q1 keys: the IOB format better expresses the boundaries of an entity or chunk. The other options (easier to read, easier for machines, all of the above) are wrong because the underlying motivation is boundary disambiguation, not surface readability.

A variant scheme is BIOES / BILOU, which adds E (End) and S (Singleton), but the slides stick to BIO.

## 6. Feature engineering for NERC

Slide 15 names three feature families. Quiz Q6 keys exactly on this — the answer is "all of the above", because all three are used.

**Word-level features (p. 16, from Nadeau & Sekine 2007 Table 1).** Capture structural and semantic properties of the token itself:
- Case: starts capital, all caps, mixed case (ProSys, eBay).
- Punctuation: internal period (St., I.B.M.), apostrophe (O'Connor), hyphen, ampersand.
- Digit pattern: cardinal, ordinal, Roman numeral, word-with-digit (W3C, 3M).
- Character: possessive mark, first-person pronoun, Greek letters.
- Morphology: prefix, suffix, singular, stem, common ending.
- Part-of-speech: proper name, verb, noun, foreign word.
- Function: alpha/non-alpha, n-gram, lowercase/uppercase version, pattern, summarised pattern, token length, phrase length.

**Lookup features (gazetteers / lexicons, p. 17, Nadeau & Sekine Table 2).** Match the token against curated lists:
- General lists: dictionary, stop words, capitalised nouns (January, Monday), common abbreviations.
- List of entities: organisation, airline, first name, last name, celebrity, continent, country, state, city.
- List of entity cues: typical organisation words, person titles (Dr., Mr.), name prefixes, post-nominal letters (Jr., PhD), location typical words, cardinal points.

**Document & corpus features (p. 18, Nadeau & Sekine Table 3).** Look beyond the token's immediate context:
- Multiple occurrences: other entities in the document, mixed upper/lower case versions, anaphora, coreference.
- Local syntax: enumeration, apposition, position in sentence/paragraph/document.
- Meta information: URI, email header, XML section, position in bulleted lists/tables/figures.
- Corpus frequency: word and phrase frequency, co-occurrences, multiword unit permanency.

The "data sample" slide (p. 19) shows the actual columns of an annotated NER corpus: id, lemma, next-lemma, next-next-lemma, next-next-pos, next-next-shape, next-next-word, next-pos, next-shape, next-word, pos, prev-iob, prev-lemma, prev-pos, prev-prev-iob, prev-prev-lemma, prev-prev-pos, prev-prev-shape, prev-prev-word, prev-shape, prev-word, sentence_idx, shape, word, tag. So the feature window goes two tokens to the left and two to the right, including their IOB tags, lemmas, POS, and shapes.

## 7. Word shape feature

Word shape (p. 16, the side box) is a compact representation of the orthographic pattern of a token:
- Replace every uppercase letter with X, every lowercase letter with x, every digit with d, keep punctuation.
- Long shape keeps consecutive identical characters; short shape collapses runs.

Examples from the slide:
- "Joe" → long Xxx, short Xx.
- "Amsterdam" → long Xxxxxxxxx, short Xx.
- "spaCy" → long xxxXx, short xXx.
- "12-10-2007" → long dd-dd-dddd, short d-d-d.

Quiz Q8 confirms: the representation "xxxXx" for "spaCy" is a word shape feature. It is *not* a character n-gram (which would be substrings like "spa", "paC"), not a digit pattern (no digits in "spaCy"), and not just a case feature (case alone would not preserve the position of the capital).

Word shape is useful because it generalises across unseen words — any 5-letter token with a single internal capital looks like "xxxXx" and can be tagged similarly.

## 8. Token-level features (per slide p. 16, 20)

The slide on p. 20 (Jurafsky & Martin) and p. 19 (data sample) together imply typical features used per token for sequence classification:
- POS of the current word and of neighbours (previous, next, next-next, previous-previous).
- Lemma of the current word and of neighbours.
- Word shape of current and neighbours.
- The IOB tag of the previous token (a sequence feature — what the classifier already decided one step back).
- Chunk tag (B-NP, I-NP, etc.) for shallow syntactic chunking.

Quiz Q9 asks which feature is *not* typically used. The given answer is "length of the current word." However, the Nadeau & Sekine table on p. 16 explicitly lists "token length, phrase length" under Function features, so the slides actually treat length as a valid word-level feature. This is a quiz-vs-slide contradiction worth flagging. On the exam, go with the quiz's preferred answer (length-of-current-word as "not typical") because that is the answer key the course is using.

The other three options in Q9 — POS of the previous word, lemma of the next word, IOB tag of the previous word — are all canonical sequence-labelling features and are clearly used.

## 9. Models for NERC

The slides walk through three eras of NERC models.

**Era 1: Feature-engineered CRF (p. 21).** A Conditional Random Field models the joint distribution over the whole label sequence, conditioned on the input features. It learns transition weights between adjacent labels (e.g., B-PER is likely to be followed by I-PER or O, but not by I-ORG) and emission weights from features to labels. The figure on p. 21 shows tokens "The CEO of Apple Inc. resigned." mapped to "O B-PER O B-ORG I-ORG O O" via a CRF that connects labels with probability factors p.

**Era 2: Bi-LSTM + CRF (pp. 22–28).** Each word is represented by its embedding. A left-to-right LSTM (l layer) reads the sequence; a right-to-left LSTM (r layer) reads it in reverse; the two are combined (c layer) to give each token a contextual representation. A CRF layer on top decodes the best IOB sequence. The bullet on p. 25 notes that pure word embeddings lose structural info like word shape, so the architecture (p. 27) feeds each word through a character-level LSTM whose output is concatenated to the GloVe embedding before the BiLSTM. Yadav & Bethard 2018 (p. 28) compare word-level, character-level, word+character, and word+character+affix architectures — affix embeddings learn from all n-gram prefixes/suffixes in training corpus.

**Era 3: Pre-trained transformers fine-tuned for NERC (pp. 30, 35, 36).** A transformer like BERT (768 dimensions, 12 layers/attention heads) is pre-trained unsupervised on massive data using a masked language modelling objective. It is then fine-tuned with a small annotated corpus (CoNLL-2003) for token classification using BIO labels. Because the embeddings are contextual, "to run the show" and "to run a marathon" produce different vectors for "run"; "Apple delayed the iPhone 13" and "Apple with cinnamon go well together" produce different vectors for "Apple" — enabling disambiguation that earlier models could not handle.

Hugging Face (p. 34) hosts many fine-tuned NER models. The pipeline call `pipeline("ner")` defaults to `dbmdz/bert-large-cased-finetuned-conll03-english`. Output uses word-piece tokenisation (`Il`, `##ia`, `##s`), so post-processing is needed to merge sub-word pieces back into entity spans. Cross-lingual models like `xlm-roberta-large-finetuned-conll03-english` work across languages without retraining (p. 35).

## 10. Evaluation

The standard metric is span-level precision, recall, and F1 (p. 36 table from Yadav & Bethard). A prediction is correct only if both the span (every token) and the type match the gold annotation. Partial matches and type-only matches don't count in the strict metric.

Performance on CoNLL-2003 English (p. 29) reaches ~91 F1 with feature-inferring NN word+character models. Pre-trained transformers push this further.

The "factors impacting performance" slide (p. 33, quiz Q10) lists five factors:
- **Annotation of spans and of nesting** — schemes that allow nested entities vs flat schemes change the task.
- **Genre of text** — news vs tweets/social media. Twitter has more variation, less standard capitalisation, more noise.
- **Entity types** — results differ per type; PER is usually easiest, ORG harder, events / amounts trickier.
- **Amount of training data** — more is better.
- **Difference between training and test data** — domain dependency, training data goes stale.

Quiz Q10's wrong answer is text font size — it is a pure distractor. PDF or HTML formatting does not affect tokenised text.

The domain-shift slide (p. 37) shows that moving from CoNLL-2003 news to DrugNER medical text can lose up to ~20 F1 points.

## 11. Balanced evaluation sets

Quiz Q3 asks why balanced evaluation data sets matter for NLP research. The keyed answer is that without a realistic sample of the linguistic phenomenon, the data set doesn't allow measuring a system's performance on that phenomenon adequately.

This concept is *not* explicitly stated in the 48 slides — it is general evaluation methodology that almost certainly comes from Maynard et al. ch 3 or the lab notebook. If your training and test data are skewed toward common entity types or one genre, F1 numbers look great but the system fails on real distributions. The slide on p. 33 hints at this when it lists "difference between training data and test data" as a performance factor.

## 12. Entity Linking (pp. 41–47)

NEL takes a recognised, typed mention and links it to a unique identifier in a knowledge base (Wikipedia URL, DBpedia URI, YAGO entry). The Obama–Michelle example on p. 42 shows that multiple entries match the surface form "Obama" (Obama Fukui the place, Barack Obama, Mount Obama, …); the system ranks candidates based on context.

Two challenges (pp. 43, 44):
- **Name ambiguity** — one mention, many candidates. Wikipedia and DBpedia maintain disambiguation pages that enumerate possible referents (e.g., the Lincoln disambiguation page lists Lincoln Memorial, Lincoln Motor Company, Lincolnshire, Abraham Lincoln, Lincoln in England / Nebraska / New Hampshire / Alabama, etc.).
- **Name variation** — one entity, many surface forms. "Abraham Lincoln" is also "Honest Abe", "A. Lincoln", "President Lincoln", "Abe Lincoln", "Lincoln". The slide notes: the more popular the entity, the more vague the reference and the more synonyms.

**NIL entities (pp. 44, 45).** Some mentions are real people / places / orgs that are simply not in the KB — "Edgar Gonzalez" the shooting victim in the San Benito news article doesn't match any of the Edgar Gonzalez Wikipedia entries (the pitcher, the footballers, the politician). The system should output NIL, not force a wrong link. The Alistair McAlpine example (p. 46) shows what happens when identity mismatch goes wrong in practice — defamation suits and BBC settlements of £185,000.

**Linking methods (p. 47).** Two families:
- **Word-based** — find the candidate whose KB description is most textually similar to the mention's context. Scoring uses text similarity weighted by TF/IDF. Decision is local (one mention at a time). Works against unstructured KBs (Wikipedia text). Example: DBpedia Spotlight.
- **Graph-based** — find candidates that are coherent with each other according to KB connections. All candidates and their KB facts are placed in a graph network and pruned until only one candidate per mention is left. Decision is global (jointly across all mentions in the document). Works against structured KBs (DBpedia, YAGO). Example: AIDA / AGDISTIS.

## 13. Coreference resolution (pp. 48)

Coreference is finding which words or phrases in a text refer to the same entity (p. 48). In the Abraham Lincoln passage, "Abraham Lincoln", "Lincoln" (multiple times), "he", "his", "the 16th President of the United States", "a lawyer", "a member" all refer to the same person. Coreference must figure out that "he" and "his" point to Lincoln and not Douglas. Important for information extraction because facts often hide behind pronouns. Not assessed in detail in this lecture but introduced as the next NLP task downstream of NERC.

---

## Likely exam traps

- NER ≠ NEC. Quiz Q5 swaps the definitions. NER finds the phrase; NEC assigns the type. NEL/NED is yet another task — identifying which entity in a KB.
- BIO encodes *boundaries* so two adjacent same-type entities can be told apart (e.g., "American Airlines" then "AMR Corp." both ORGs but separated by B-ORG). Quiz Q1.
- Word shape preserves capitalisation and digit pattern, not character n-grams. xxxXx for "spaCy" is not a 3-gram or 4-gram representation. Quiz Q8.
- Quiz Q9 says length of the current word is *not* a typical feature, but the Nadeau & Sekine table on p. 16 lists token length under Function features. Go with the quiz answer on the exam.
- Text font size impacts nothing for NER (Q10). It is a pure distractor.
- Metonymy (Q2) is about the *type* changing — same name flips between PER, ORG, LOC depending on context (US the country vs US the government). Don't confuse with ambiguity (Q7), which is about the surface form having multiple unrelated referents.
- Variation (IBM / The Big Blue) and ambiguity ("Apple" org vs fruit) sound similar but are opposites — variation is one entity with many names, ambiguity is one name for many entities.
- Pre-trained transformers disambiguate by contextual embeddings (p. 30). They do not need a hand-built lookup list.
- Entity Linking can fail with NIL entities (p. 44) — the entity exists in the world but not in the KB.

---

## Self-quiz (cover the answers)

1. Which of the following best describes the difference between NER and NEC?
   - A. They are essentially the same thing.
   - B. NER handles proper nouns; NEC handles common nouns.
   - C. NER assigns the entity type; NEC finds the span.
   - D. NER finds the span; NEC assigns the type. **[correct]**

2. Which is *not* a referring expression in the broad sense used in the slides?
   - A. Pronoun ("he" referring to Lincoln).
   - B. A bare punctuation mark on its own. **[correct]**
   - C. Common noun phrase ("the 16th president").
   - D. Proper noun ("Lincoln" the person).

3. In BIO tagging, what does the B in "B-PER" indicate?
   - A. The token begins a person-entity span. **[correct]**
   - B. The token sits between two persons.
   - C. The token is a back-reference pointer.
   - D. The token is binary-encoded internally.

4. Why use BIO over a class-only labelling scheme?
   - A. It is easier for humans to read at a glance.
   - B. All of the above reasons apply equally.
   - C. It encodes entity boundaries, so adjacent same-type entities stay separated. **[correct]**
   - D. It is easier for machines to parse mechanically.

5. The word "Amsterdam" has long word shape:
   - A. dd-dd-dddd
   - B. xxxx (no caps)
   - C. X.x (with period)
   - D. Xxxxxxxxx **[correct]**

6. Which of the following is *not* a typical feature for token-level NERC classification (per the quiz key)?
   - A. Length (in characters) of the current word. **[correct]**
   - B. POS tag of the previous word.
   - C. Lemma of the next word.
   - D. IOB tag of the previous word.

7. Which is an example of metonymy in NERC?
   - A. "may" being used as a person name in social media posts.
   - B. "Apple" the organisation vs "apple" the fruit (different types).
   - C. "New York" being also called "NY" or "The Big Apple".
   - D. "The US announced new tariffs" — US standing for the government. **[correct]**

8. Which is *not* listed as a factor that impacts NERC performance on slide p. 33?
   - A. Genre of the text (news vs tweets).
   - B. Text font size in the source. **[correct]**
   - C. Amount of available training data.
   - D. Annotation of spans and nesting depth.

9. Which of the following is a graph-based entity-linking system?
   - A. AIDA / AGDISTIS. **[correct]**
   - B. DBpedia Spotlight.
   - C. spaCy NER pipeline.
   - D. Flair tagger.

10. The feature families used in NERC include:
    - A. Document & corpus features only.
    - B. Lookup features (gazetteers) only.
    - C. All three families together. **[correct]**
    - D. Word-level features only.

11. A "NIL entity" is:
    - A. An empty (zero-token) span.
    - B. An entity tagged with the null type.
    - C. A mention that has no matching entry in the knowledge base. **[correct]**
    - D. A typo in the source document text.

12. In a Bi-LSTM-CRF NERC model, why add character embeddings on top of word embeddings?
    - A. To recover structural info (word shape, affixes) that word embeddings drop. **[correct]**
    - B. They are not actually used in practice.
    - C. To make training run faster overall.
    - D. To reduce the vocabulary size drastically.

---

## What's in the quiz but NOT (or only weakly) in the slides

- Q3 (balanced evaluation data sets) — the framing "balanced data set so the system performance reflects the linguistic phenomenon adequately" isn't explicit anywhere in the 48 slides. It is general NLP evaluation methodology, most likely from Maynard et al. ch 3 or the lab.
- Q9's premise that word length is *not* a typical feature contradicts p. 16, where the Nadeau & Sekine word-level features table explicitly lists "token length, phrase length" under Function features. The quiz answer treats length as not typical; the slide treats it as a feature. If the exam reuses the quiz wording, defer to the quiz answer.
- Q1's explicit rationale "IOB expresses boundaries better than class-only" is implicit in the BIO encoding shown on pp. 19–21 (and in how adjacent ORGs are separated in the CoNLL American Airlines / AMR Corp. example) but is not stated as a single bullet on a slide.
- The companion literature (Yadav & Bethard 2019 survey) covers the deep-learning architectures (BiLSTM-CRF, character embeddings, affix embeddings) in more detail than the slides; the lecture summarises results on p. 28–29.
