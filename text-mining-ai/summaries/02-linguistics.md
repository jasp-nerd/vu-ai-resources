# 02 — Linguistics for NLP

**Source slides:** tm-ba-lecture-2-linguistics-nlp.pdf (57 pp.)
**Companion literature:** Kracht *Introduction to Linguistics* (phonetics 12–23, morphology 79–85, syntax 86–98, semantics 154–160); *Essentials of Linguistics* Ch 8 (pragmatics)
**Quiz questions drawn from this material:** Introduction to linguistics (10 Qs)

---

## Cheat sheet (cover the right column, recall the left)


| Term / question                              | Answer                                                                                                                   | Slide            |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ---------------- |
| Five levels of linguistic analysis, in order | Phonetics/phonology → Morphology → Syntax → Semantics → Pragmatics                                                       | p. 2             |
| NLP module for phonetics/phonology           | Automatic Speech Recognition (ASR)                                                                                       | p. 2             |
| NLP modules for morphology                   | Segmentizers, tokenizers, POS-taggers, lemmatizers, compound splitters, multiword detection                              | p. 2             |
| NLP modules for syntax                       | Syntactic parsers, chunkers                                                                                              | p. 2             |
| NLP modules for semantics                    | Semantic parsers, word-sense disambiguation                                                                              | p. 2             |
| NLP modules for pragmatics                   | Context and domain models                                                                                                | p. 2             |
| Number of phonemes in a typical language     | 11–112 (sound units, vowels and consonants)                                                                              | p. 3             |
| Number of morphemes in a typical language    | 4,000–10,000                                                                                                             | p. 3             |
| Number of common words in a typical language | ~50,000 (millions including terminology)                                                                                 | p. 3             |
| Zipf's law formula                           | f(wᵢ) = f(W₁) / rᵢ(wᵢ) — frequency is top frequency divided by rank                                                      | p. 4             |
| Share of any text made up of top words       | ~80% (short, polysemous, frequent words)                                                                                 | p. 4             |
| Why Zipf matters for NLP                     | Most-frequent words are short and ambiguous, so meaning depends heavily on context                                       | p. 4             |
| Morpheme (definition)                        | Smallest meaning-bearing unit; e.g. *walked* = walk + -ed                                                                | p. 5             |
| Free morpheme                                | Stands alone, e.g. *boy*, *walk*                                                                                         | p. 5             |
| Bound morpheme                               | Must attach, e.g. *-ed*, *un-*                                                                                           | p. 5             |
| Inflection (definition)                      | Modifies an existing word's grammatical features (tense, number) — *walk → walked, boy → boys*                           | p. 5             |
| Derivation (definition)                      | Derives a new word from another (often changing class) — *boy → boyish, race → racism*                                   | p. 5             |
| Three affix types                            | Prefix (*un-loved), infix (minister-s-post), suffix (love-able*)                                                         | p. 5             |
| Quiz Q7 morphological example                | Adding a prefix to alter meaning                                                                                         | p. 5             |
| Quiz Q8 grammatical-feature change           | Inflection (tense, number)                                                                                               | p. 5             |
| Open word classes                            | Noun, Verb, Adjective, Adverb — accept neologisms                                                                        | p. 6             |
| Closed word classes                          | Pronouns, Prepositions, Determiners, Conjunctions — small fixed set, change slowly                                       | p. 6             |
| Stopwords — linguistic class?                | NO — they are frequent low-content words from both classes (not a linguistic category)                                   | p. 6             |
| Form/stem ratio English                      | ~2:1                                                                                                                     | p. 7             |
| Form/stem ratio Dutch/German                 | ~5:1                                                                                                                     | p. 7             |
| Form/stem ratio Finnish/Turkish              | >200:1 (morphologically rich)                                                                                            | p. 7             |
| Part-of-Speech tagging task                  | Assign a PoS category (noun/verb/adj…) to every token                                                                    | p. 9             |
| Baseline PoS-tagger accuracy                 | ~90% from choosing the most frequent tag (prior)                                                                         | p. 9             |
| Traditional PoS model                        | Markov model — next state depends on current state                                                                       | p. 9             |
| Universal Dependencies PoS tagsets           | At least 50 different tagsets exist                                                                                      | p. 9             |
| Phrase / constituent (definition)            | A word or group of words functioning as a single grammatical unit, built around a *head* with *modifiers*; can nest      | p. 11            |
| Adjective Phrase (AdjP/AP) example           | *very nice* — head = adjective, modifier = adverb                                                                        | p. 11            |
| Noun Phrase (NP) example                     | *a very nice looping* — head = noun, modifier = AdjP                                                                     | p. 11            |
| Verb Phrase (VP) example                     | *performs a very nice looping* — head = verb, modifier = NP                                                              | p. 11            |
| Prepositional Phrase (PP) example            | *with a long stick* — head = preposition                                                                                 | p. 11            |
| Quiz Q1 — "The Text Mining Course"           | Noun Phrase (NP)                                                                                                         | p. 11            |
| Constituency parsing (what it produces)      | Hierarchical syntax tree with nested NP/VP/PP nodes                                                                      | pp. 14–16        |
| Dependency parsing (what it produces)        | Flat head→dependent arcs between words (no phrase nodes)                                                                 | p. 12            |
| Quiz Q2 — the difference                     | Dependency = flat relations between adj/noun/verb; constituency = hierarchical NP/VP relations                           | p. 12, 16        |
| Root in dependency tree                      | Main verb — no outgoing arrow                                                                                            | p. 12            |
| Quiz Q9 — relation in dependency grammar     | Dependency relations (head ↔ dependents)                                                                                 | p. 12            |
| Grammatical Subject test                     | Number agreement with main verb (boys-plural wave-plural)                                                                | p. 17            |
| Grammatical Object test                      | Obligatory NPs/PPs that make the sentence grammatical with the verb                                                      | p. 17            |
| PP-attachment ambiguity                      | "Krelis waved at the cow with a hat" — does PP modify cow or waving?                                                     | p. 18            |
| Chunking (other name)                        | Shallow parsing                                                                                                          | p. 20            |
| What chunkers produce                        | List of constituents up to a fixed depth (~2), NOT full trees                                                            | p. 20            |
| Quiz Q3 — chunkers                           | Efficiently identify constituents but no full tree, no full dependency structure                                         | p. 20            |
| Quiz Q5 — parsers + chunkers belong to       | Syntax                                                                                                                   | p. 20            |
| Why a parser must be robust                  | Real text contains typos and ungrammatical sentences (tweets, chat)                                                      | p. 19            |
| Polysemy (definition by example)             | Same word form, multiple meanings: *head of department, head set, head of construction, heading, Head by Prince*         | p. 21            |
| WordNet                                      | Lexical database that lists word senses (synsets) and their relations                                                    | p. 22            |
| Meronymy (Quiz Q4)                           | Part-whole relation (*lecture room* is part of *university building*)                                                    | Kracht semantics |
| Hyponymy                                     | Type-of relation (*dog* is a hyponym of *animal*)                                                                        | Kracht semantics |
| Synonymy                                     | Same meaning across different word forms                                                                                 | Kracht semantics |
| Homophony                                    | Same sound, different meanings (and often different spellings)                                                           | Kracht semantics |
| Semantic roles                               | Agent, Patient, Instrument, Recipient, Theme, Source, Path, Goal                                                         | p. 23            |
| Agent                                        | Performer of the action, has control (can stop doing it)                                                                 | p. 23            |
| Patient                                      | Undergoes the action and is changed by it                                                                                | p. 23            |
| Instrument                                   | What the agent uses to perform the action                                                                                | p. 23            |
| Linguistic packaging                         | Same content can be expressed by different words / syntactic structures (active/passive/ergative)                        | p. 23            |
| Quiz Q6 — semantics vs pragmatics            | Semantics = literal word meaning; pragmatics = how context shapes meaning                                                | p. 25            |
| Metaphor                                     | Transfer of a property from one concept to a different, **unrelated** concept ("save in the cloud")                      | p. 25            |
| Metonymy                                     | Refer to something by a **related** concept ("the three pizzas still need to pay")                                       | p. 25            |
| Quiz Q10 — metaphor vs metonymy              | Metaphor crosses to an unrelated concept; metonymy uses a related concept                                                | p. 25            |
| Speech act mismatch (form vs function)       | "Can you close the window?" — question form, request meaning; "It's a bit cold here" — declarative form, request meaning | p. 25            |
| Word embedding                               | Dense high-dimensional vector representing a word (e.g. 768 dims)                                                        | p. 28            |
| Cosine similarity                            | Distance metric used between word vectors                                                                                | p. 29            |
| Word embeddings learn by                     | Predicting words that occur in context, not those that don't                                                             | p. 28            |
| LLM extra mechanism beyond static embeddings | Attention — combines a word's vector with its context's vectors to produce a context-sensitive representation            | p. 34            |
| Transformer components (three)               | Tokenizer, Vocabulary (word embeddings), Model (attention encoder blocks)                                                | p. 45            |
| BERT-base-cased                              | 28,996 vocab, 12 layers, 768 hidden, 12 heads, 110M params                                                               | p. 47            |
| Byte-Pair Encoding (BPE)                     | Statistical sub-word tokenizer; merges frequent adjacent characters/pairs up to k; *not* linguistically informed         | pp. 45–46        |
| Curse of multilinguality                     | Too many languages in one model degrade performance unless capacity/vocabulary grows                                     | p. 55            |


---

## 1. Levels of linguistic analysis

Slide p. 2 gives the table that maps each linguistic subdiscipline to its NLP counterpart, and it is probably the single most exam-worthy slide of the lecture:

- **Phonetics / phonology** — audio signals → Automatic Speech Recognition.
- **Morphology** — words and word formation → segmenters, tokenisers, POS-taggers, lemmatisers, compound splitters, multiword detection.
- **Syntax** — sentence structure → parsers, chunkers.
- **Semantics** — sentence and word meaning, compositionality, quantification → semantic parsers, word-sense disambiguation.
- **Pragmatics** — language use in context → context and domain models.

The point of distinguishing the levels is that each one needs its own NLP module, and any text-mining pipeline strings several of these together. The lecture also lists the **methods** linguists use (introspection, behaviourism, neuro-cognitive models, rule systems, empirical/experimental and stochastic methods, mathematical models, classification models, distributional models) and **resources** (lexicons, grammars, annotated text/video/audio collections).

Forms in language (p. 3) — a language has 11–112 phonemes, 4,000–10,000 morphemes, ~50,000 common words, and an infinite number of sentences. Active vocabulary is a small fraction of what we passively recognise. In NLP the terms *word*, *word form* and *token* are used interchangeably.

Zipf's law (p. 4) — frequency f(wᵢ) of the i-th ranked word equals f(W₁)/rᵢ. Most-frequent words are short, polysemous, grammatically light and make up about 80% of any text. The takeaway: **words get meaning in context** — you cannot extract meaning purely from word forms.

## 2. Phonetics / phonology

The slides barely touch this — only mentioned in the p. 2 table as the level handled by ASR. For text mining this level is usually skipped because the input is already text. Just remember the unit (phonemes) and the NLP module (ASR).

## 3. Morphology

Morphology studies the form and structure of words. The smallest meaning-bearing units are **morphemes**, e.g. *walked* = *walk* (activity) + *-ed* (past). Arbitrary sub-strings like *wa*, *alk*, *lke* are not morphemes.

- **Free morpheme** — stands alone (*boy*, *walk*).
- **Bound morpheme** — must attach to another morpheme (*-ed*, *-s*, *un-*).

Bound morphemes split into two functions:

- **Inflection** modifies an existing word's grammatical features without creating a new lexical item:
  - tense — *walk → walked*
  - number — *boy → boys*
- **Derivation** builds a new word from another (often shifting POS):
  - *-ish*, *-ism*, *-ity*, *-ial* → *boyish, racism, necessity, essential*

This inflection/derivation contrast is exactly what quiz Q8 tests: tense and number are inflection, not derivation, not compounding.

**Affixes** come in three positions:

- **prefix** — *un-loved*, *be-loved*
- **infix** — *minister-s-post* (position of a minister) — rare in English
- **suffix** — *love-able*

Quiz Q7 asks for an example of a morphological process and the answer is "adding a prefix to a word to alter its meaning." Stress/tone and word order are not morphology, and using context is not morphology either.

**Word forms** (p. 7) are all the inflected variants of a word. The ratio of forms to stems varies wildly by language: English ~2:1, Dutch/German ~5:1, Finnish/Turkish >200:1. Slides p. 8 list 18 Turkish forms of *gelmek* "to come" as a demonstration — Turkish is highly agglutinative.

**Types of words** (p. 6):

- **Open class** — accepts neologisms: Noun, Verb, Adjective, Adverb. New words like *chin diaper* are invented and forgotten easily.
- **Closed class** — small fixed set (<~100 words), changes slowly across generations: pronouns (*he, she, it, this, who*), prepositions (*in, at, from, in front of*), determiners, conjunctions. The slide flags *sher* as an attempted new pronoun to illustrate how slow the change is.
- **Stopwords are NOT a linguistic class** — they are a NLP-engineering category: frequent words with little content, drawn from both open and closed classes (*a, the, in, for, case, me, you, I, are, is, be, have, good*). The "good" example shows that stopword lists are constructed, not linguistic.

**Part-of-Speech (POS) tagging** (p. 9) is the morphology-layer NLP module that assigns a category (Det, Adj, NN, VB, Prep…) to every token. Two facts worth remembering:

- Just picking the most frequent tag for each word ("the prior") already gives ~90% accuracy.
- Traditional POS tagging uses a **Markov model** — a sequence model where the next state depends on the current one. There are at least 50 different tagsets; the Universal Dependencies project tries to harmonise them.

## 4. Syntax

Syntax is about sequences of words exhibiting structures and patterns. We experience sentences as complete and have strong intuitions when they are not. Words combine freely into **phrases / constituents**, producing infinitely many sentences.

### Phrases and heads (p. 11)

A phrase is a word or group of words functioning as a single unit in the grammatical structure. Every phrase is built around a **head** word, with one or more **modifiers**, and phrases can nest:

- **AdjP / AP** — *very nice* — head = adjective, modifier = adverb.
- **NP** — *a very nice looping* — head = noun, modifier = AP.
- **VP** — *performs a very nice looping* — head = verb, modifier = NP.
- **PP** — *with a long stick* — head = preposition.
- **S** (sentence) — *the cow performs a very nice looping with a long stick*.

Quiz Q1 — "The Text Mining Course" is an NP (head: noun *Course*).

### Constituency parsing vs dependency parsing

This is the most-tested distinction in the lecture.

- **Constituency parsing** produces a **hierarchical** tree with internal nodes labelled S, NP, VP, PP, AP. Slides pp. 14–16 build up the *Krelis waved at the cow with a hat* tree step by step, ending with a full S → NP, VP structure where the VP dominates the second PP.
- **Dependency parsing** (p. 12) produces **flat head→dependent arcs** between words directly. There is no NP/VP node — only labelled relations:
  - root → main verb (no outgoing arrows)
  - subject → depends on main verb
  - object → depends on main verb
  - adjunct → depends on main verb
  - modifier → depends on the noun/adjective it modifies

Quiz Q2 phrases this with the labels flipped to trap you: the correct answer is "**a dependency parser detects flat relations between adjectives, nouns and verbs; a constituency parser detects hierarchical relations such as noun phrases and verb phrases**." Quiz Q9 names the actual relation a dependency grammar uses: **dependency relations**.

### Syntactic functions (p. 17)

- **Grammatical Subject** — number-agrees with the main verb. *The boys wave at the cow* (both plural); *the books were given by me* (both plural); *the boys were kicked by the cow* (both plural).
- **Grammatical Object** — obligatory NPs or PPs that make the sentence grammatical with a particular verb (*the teacher gives ...?* fails without an object).

### Syntax: real-world headaches (pp. 18–19)

The slides spend two pages emphasising that real syntax is messy:

- Constituents can be tiny or huge: *He* (NP) vs *The very nice black and white cows with red hats on their head* (also NP).
- Languages with little morphology (English) are very ambiguous: *flies like sailing ships*.
- **PP-attachment** is context-dependent: *Krelis waved at the cow with a hat* — does the hat belong to the cow or the waving?
- **Scope** is context-dependent: *Old women and men can be annoying*; *Mary did not believe John murdered Bill with a knife*.
- **Meaning** is context-dependent: *I count on my computer*.
- Sentences contain typos and are often ungrammatical (especially tweets and chat). The conclusion: **a parser should be robust**.

### Chunking (p. 20)

If you don't need full parse trees, do **chunking** (also called **shallow parsing**):

- Cheap and robust alternative to parsing.
- Produces a **list of constituents up to a certain depth (typically 2)** — chunks are like constituents but no full tree, no full dependency structure.
- Example output: `[Krelis] [quickly waved] [at [the cow]] [with [a hat]]`.
- A second classifier then labels the chunks: `[Krelis]NP [quickly waved]VP [at [the cow]NP]PP [with [a hat]NP]PP`.

Quiz Q3's answer is the textbook formulation: "Chunkers efficiently identify constituents but do not provide full sentence structure or syntactic dependencies." Quiz Q5 confirms parsers and chunkers both belong to **syntax**, not morphology/semantics/pragmatics.

## 5. Semantics

Semantics is about word meaning and sentence meaning. Two slides drive this home.

**Words have meanings** (p. 21) — *The head of the department lost his head set after hitting his head against the head of the construction while heading for his meeting and enjoying the song Head by Prince.* — the same form *head* covers multiple senses (polysemy). The Wikipedia disambiguation page and WordNet (p. 22) list dozens of senses, e.g. WordNet lists head#1 (body part), head#2 (cattle counter), head#4 (chief), head#8 (source of a stream), head#9 (grammatical head), head#11 (height unit), head#13 (school principal)…

**Lexical relations** — the slides do not give a formal taxonomy of meronymy / hyponymy / synonymy / homophony. The companion Kracht semantics chapter (pp. 154–160) is where this comes from. Quiz Q4 asks for the relation between *lecture room* and *university building* — the answer is **meronymy** (part-of-whole). Useful definitions to memorise (from general linguistic knowledge):

- **Meronymy** — part-of-whole (*finger* is a meronym of *hand*; *lecture room* of *university building*).
- **Hyponymy** — type-of (*dog* is a hyponym of *animal*).
- **Synonymy** — same meaning, different form (*car* / *automobile*).
- **Homophony** — same pronunciation, different meanings (*bare* / *bear*).

**Sentences have meanings — who did what to whom, when, where, how** (p. 23). The lecture introduces semantic roles using *The man opened the door with a key*:

- *the man* = NP (phrase), subject (dependency), **agent** (semantic role).
- *the door* = NP, direct object, **patient**.
- *with a key* = PP, adjunct, **instrument**.

Standard semantic roles:

- **Agent** — performs the action with control (can stop doing it).
- **Patient** — undergoes the action and is changed by it.
- **Instrument** — what the agent uses.
- Others — recipient, theme, source, path, goal.

The same propositional content can be **packaged linguistically** in different ways: *The door was opened by the man with the key*, *The man stood before the door. The key opened the door*, *The man took the key. The door opened*. For text mining you have to handle all of these.

**Semantic parsing** (p. 24) labels which constituent fills which role. The slide shows colour-coded examples — *The boy ran from the shop across the street to his mummy* exposes agent / source / path / goal; *Harvey bought her flowers* / *She got flowers from Harvey* / *Flowers were given to her by Harvey* shows the same agent–theme–recipient template under three different syntactic packagings.

**Word embeddings** (pp. 28–33) — dense high-dimensional vectors (typically 768 dimensions) learned from a neural network. Training objective: make the vector for a word similar to the vectors of words that occur in its context (e.g. *actor* near *movie*, *act*, *play*) and dissimilar from words that don't (*cat*, *planet*, *moon*). Cosine similarity is the distance metric. After training, semantically related words cluster: *actor / movie / celebrity / actress* together, *sun / planet / moon* together, *stiff / rigid* together.

**Polysemy in vector space** (p. 33) — *star* sits between the celebrity cluster and the astronomical cluster because both senses share contexts. Static embeddings struggle with polysemy, which motivates **contextualised** representations in Large Language Models.

**Large Language Models** (pp. 34–44) build a context-sensitive representation by stacking **attention** layers on top of token embeddings. The mechanism in slogan form: query × key produces an attention weight, which determines how much of each value vector flows into the masked position. Stacking 12 or 24 encoder blocks lets a token like *star* end up close to *celebrity* in one context (*a Hollywood star*) and close to *planet/sun* in another (*a bright galactic star*).

**Transformer components** (p. 45) — the three things that determine the semantic representation of words in sentences:

1. **Tokenizer (T)** — derives the subword vocabulary statistically (WordPiece, BytePiece, SentencePiece). Not linguistically informed.
2. **Vocabulary (V) / word embeddings** — maps subwords to their initial embeddings.
3. **Model (M)** — encoder blocks that modify word/token embeddings using attention over context.

**Byte-Pair Encoding** (p. 46) — start from all single-byte characters in training data; repeatedly merge the most frequent adjacent pair until you hit a max vocabulary size *k*, staying inside word boundaries. Frequent words end up as single tokens; rare words split into frequent subwords. Used by RoBERTa, GPT-2.

Vocabularies in real LLMs (pp. 47–49): BERT-base-cased = 28,996 tokens, 12 layers, 768 hidden, 12 heads, 110M parameters. Dutch BERTje = 30K. Multilingual BERT-cased = 119,547 across 104 languages. XLM-RoBERTa = 250K. The vocabulary includes special tokens [PAD], [UNK], [CLS], [SEP], [MASK] plus subword fragments marked ##.

**Curse of multilinguality** (p. 55) — adding more languages helps low-resource languages up to a point, then performance degrades (transfer-interference trade-off). Mitigations: increase model capacity and vocabulary size, use more training data.

## 6. Pragmatics

Pragmatics is about language use in context — language stretched to serve a purpose because people always try to make sense (p. 25). The slide gives four canonical examples:

- *Save your data up in the cloud.* — **metaphor**. *Cloud* (atmospheric phenomenon) is borrowed to describe remote storage (an unrelated concept).
- *The three pizzas still need to pay.* — **metonymy**. *Pizzas* refers to the people who ordered them (a related concept).
- *Can you close the window, please?* — **form: question, meaning: request**.
- *It is a bit cold here, isn't it?* — **form: declarative, meaning: request**.

The metaphor / metonymy contrast is what quiz Q10 tests, and the textbook formulation (from Essentials of Linguistics Ch 8) is: a metaphor transfers a property from one concept to a different, **unrelated** concept; metonymy uses a word to refer to a **related** concept (the cloud is unrelated to remote disk storage; the pizzas are related to the people who ordered them).

Other pragmatic phenomena typically covered in a linguistics unit (background, not on the slides verbatim):

- **Deixis** — context-dependent pointing words: *here, there, now, then, I, you*. They have no fixed referent without knowing the speech situation.
- **Speech acts** — what an utterance *does* (request, promise, threat, apology) rather than what it literally says, which is what the *can you close the window* example illustrates.
- **Implicature** — what is conveyed without being said, governed by Grice's maxims of quantity, quality, relation and manner.

Quiz Q6 sums up the semantics vs pragmatics split: semantics is about the literal meaning of words; pragmatics is about how context shapes meaning.

## 7. Why linguistics matters for NLP

The lecture's recurring theme: there is no such thing as "simple text". Variation, ambiguity and context appear at every linguistic level, and each level demands its own NLP module:

- Phonetics → ASR.
- Morphology → tokeniser, segmenter, lemmatiser, POS-tagger, compound splitter, multiword detector.
- Syntax → constituency parser, dependency parser, chunker.
- Semantics → word-sense disambiguation, semantic role labelling, semantic parser, word embeddings.
- Pragmatics → context/domain models, coreference resolution, metaphor/metonymy detection.

Even with LLMs (pp. 27, 56–57), the slides argue you still need linguistic concepts: LLMs model form, syntax and meaning *implicitly*, but they make mistakes, they break when the input gets too noisy, and the curse of multilinguality means the more languages they juggle, the higher the risk of confusion. The ChatGPT bias example on p. 56 — asked who drinks coffee given "*She has a tea and he drinks coffee. What does the doctor drink?*", ChatGPT (Nov 2023) assumed the doctor must be male even though the pronouns make the nurse female — shows that without linguistic reasoning about pronoun reference, even a frontier LLM gets it wrong.

The conclusion slide (p. 57):

1. Linguistic concepts are essential to understand what language understanding and generation entails.
2. LLMs model linguistic properties (form, syntax, meaning) implicitly.
3. LLMs perform well on linguistic, semantic and reasoning tasks but are not perfect.
4. More languages → more confusion (curse of multilinguality).
5. Linguistic concepts help understanding LLMs, and LLMs can help understanding how language works.

---

## Likely exam traps

- **Constituency vs dependency parsing — the swap.** Quiz Q2 reverses the labels in one of the wrong answers. Constituency = hierarchical NP/VP/PP nodes; dependency = flat head→dependent arcs. If you remember which one has the tree nodes, you can never be tricked.
- **Chunkers ≠ parsers.** Chunkers identify constituents up to depth ~2 only. They give you a list, not a full tree, and no full dependency relations. The wrong-answer distractors in Q3 try to sell you "full phrase-structure trees efficiently" — that's not a chunker.
- **Inflection vs derivation.** Tense, number, case, gender = inflection. New word from old word, often with class change (*race → racism*) = derivation. Compounding is a third thing entirely. Quiz Q8.
- **Stopwords are not a linguistic class.** The slides explicitly flag this on p. 6.
- **Metaphor uses an *unrelated* concept; metonymy uses a *related* one.** Both are non-literal, so distractors will say "both involve abstract concepts" or "metaphor is always exaggeration" — those are wrong.
- **Semantics vs pragmatics.** Semantics = literal word meaning. Pragmatics = context. Distractors try to mix in word order or sentence structure, which is syntax.
- **POS-tagging baseline.** Choosing the prior (most frequent tag) already gives 90%, but this is *not* the full POS-tagging algorithm — Markov models still win.
- **WordNet and lexical relations.** The named lexical-relation taxonomy (meronymy/hyponymy/synonymy/homophony) is not explicitly defined in the slides; if a question asks for the part-whole relation specifically, the answer is meronymy.
- **The "head" terminology has two uses.** In morphology/syntax it's the central word of a phrase that determines its type. In semantics/lexicography it's a word with many senses (the *head* polysemy example). Don't confuse them.

---

## Self-quiz (cover the answers)

1. The phrase *very angry students* is which type?
  - a) PP
  - b) VP
  - c) AdjP
  - d) NP
  - **Answer: d) NP — the head is the noun *students*.**
2. Which of the following is **not** a morphological process?
  - a) Adding the suffix *-able* to *love*
  - b) Adding *-s* to make a noun plural
  - c) Switching word order to form a question
  - d) Adding the prefix *un-* to *loved*
  - **Answer: c) — that's a syntactic process.**
3. A chunker:
  - a) Produces a list of constituents up to a fixed depth, without a full tree or dependency relations
  - b) Produces a full constituency tree faster than an ordinary parser does
  - c) Splits compound words into their constituent morphemes
  - d) Produces a dependency parse without giving you a constituency tree
  - **Answer: a).**
4. *Hand* and *finger* are related by:
  - a) Homophony
  - b) Hyponymy
  - c) Meronymy
  - d) Synonymy
  - **Answer: c) — finger is part of hand.**
5. Which is **not** an example of inflection?
  - a) *walk → walked*
  - b) *boy → boys*
  - c) *cat → cats*
  - d) *race → racism*
  - **Answer: d) — that's derivation, not inflection.**
6. In dependency grammar, the main verb is:
  - a) A modifier of the object
  - b) The root, with no outgoing arrows
  - c) The subject of the sentence
  - d) Always a closed-class word
  - **Answer: b).**
7. Which statement about open vs closed word classes is **true**?
  - a) Stopwords are essentially the same thing as closed-class words
  - b) Pronouns and adjectives both belong to the open class of words
  - c) Open-class words accept neologisms, closed-class words change slowly
  - d) Closed-class words form an infinitely extensible set in any language
  - **Answer: c).**
8. *The three pizzas still need to pay* is an example of:
  - a) Metonymy
  - b) Hyperbole
  - c) Metaphor
  - d) Homophony
  - **Answer: a) — *pizzas* refers to the people who ordered them, a related concept.**
9. Which best describes the difference between semantics and pragmatics?
  - a) There is no real difference between them
  - b) Semantics is about syntax, while pragmatics is about morphology
  - c) Semantics is the literal meaning of words; pragmatics is how context shapes meaning
  - d) Semantics is about sound, while pragmatics is about word order
  - **Answer: c).**
10. Word embeddings learn semantic similarity by:
  - a) Predicting which words occur in the context of a target word and which don't
  - b) Counting morphemes in each individual word
  - c) Applying hand-written grammar rules from a linguist
  - d) Looking up entries in a dictionary of word definitions
  - **Answer: a).**
11. All of the following are NLP modules at the **syntax** level **except**:
  - a) Constituency parser
  - b) Lemmatiser
  - c) Dependency parser
  - d) Chunker
  - **Answer: b) — lemmatisation is morphology.**
12. Choosing the most frequent POS tag for every token (the prior) gives roughly what accuracy?
  - a) ~70%
  - b) ~50%
  - c) ~99%
  - d) ~90%
  - **Answer: d) ~90%.**
13. Which is **not** a semantic role?
  - a) Agent
  - b) Patient
  - c) Determiner
  - d) Instrument
  - **Answer: c) — that's a POS / closed-class category.**
14. The form/stem ratio in Finnish or Turkish is approximately:
  - a) 2:1
  - b) More than 200:1
  - c) 20:1
  - d) 5:1
  - **Answer: b).**
15. In a transformer model, the three components that determine the semantic representation of words in context are:
  - a) Tokeniser, word embeddings, attention
  - b) Lemmatiser, POS-tagger, parser
  - c) Dictionary, grammar, ontology
  - d) Phonetic encoder, morphological analyser, semantic parser
  - **Answer: a).**

---

## What's in the quiz but NOT in the slides

- **Q4 (meronymy)** — the lecture demonstrates polysemy of *head* and shows WordNet, but it does not formally define the lexical-relation taxonomy (meronymy / hyponymy / synonymy / homophony). The Kracht semantics chapter (pp. 154–160) is where the named relations come from; the answer "meronymy" for *lecture room → university building* is derivable from the general definition of part-of-whole.
- **Q10 (metaphor vs metonymy distinguishing principle)** — the slides give the canonical examples (*save in the cloud*, *the three pizzas still need to pay*) but the formal principle (transfer to an unrelated concept vs reference via a related concept) comes from Essentials of Linguistics Ch 8.
- **Deixis, speech acts, implicature** — touched by the *can you close the window?* example but not labelled with those terms on the slides. If the exam asks for the label, it is drawn from the pragmatics literature.

