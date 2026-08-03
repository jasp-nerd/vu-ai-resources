# 03b — Machine learning for NLP (Lecture 3 Part 2)

**Source slides:** tm-ba-lecture-3-machine-learning-nlp-part2.pdf (71 pp.)
**Companion literature:** Jurafsky & Martin ch 4 (Naive Bayes & sentiment), ch 6 (vector semantics & embeddings), ch 17 (sequence labelling); Wolf et al. 2020 (Transformers / HuggingFace); Church 2021 (gentle intro to fine-tuning)
**Quiz questions this enables:** answers the macro-averaging stem in Sentiment Q1, the contextual-embedding stem in NER Q7, the catastrophic-forgetting stem in Topic Modelling Q9, and supports NLP quiz Q8/Q9/Q10 (features, feature engineering, supervised ML).

---

## Cheat sheet (cover the right column, recall the left)

| Term / question | Answer | Slide |
|-----------------|--------|-------|
| What is an evaluation metric? | A method for measuring a system's performance during testing | p. 5 |
| What is an evaluation framework? | How to design an experiment so the metrics are reliable | p. 5 |
| Precision formula | TP / (TP + FP) | p. 6 |
| Recall formula | TP / (TP + FN) | p. 6 |
| F1 formula | 2 · (precision · recall) / (precision + recall) — harmonic mean | p. 6 |
| Accuracy formula | (TP + TN) / (TP + FP + TN + FN) | p. 7 |
| Simplest way to get 100% recall in spam detection | Mark every email as spam (catches all real spam, terrible precision) | p. 6 |
| When is accuracy a reliable metric? | Only on **balanced** data; on skewed data a "predict-majority" baseline can score high | p. 7 |
| Spam example: 100 mails, 20 spam, system flags 10 spam (5 correct). Precision? | 5 / (5+5) = 0.5 | p. 8 |
| Same example: recall? | 5 / (5+15) = 0.25 | p. 8 |
| Same example: F1? | 2·0.5·0.25 / (0.5+0.25) = 0.33 | p. 8 |
| Same example: accuracy? | (5+75) / 100 = 0.80 (misleadingly high) | p. 8 |
| one-of (multinomial) classification | Each instance belongs to exactly **one** class out of many | p. 9 |
| any-of classification | An instance can belong to **multiple** categories simultaneously | p. 9 |
| Macro-averaging | Compute P/R per class, then take the unweighted average of those scores | p. 10 |
| Micro-averaging | Pool all TPs / FPs / FNs across classes, then compute one P/R from the pooled counts | p. 10 |
| When does macro vs micro matter? | On imbalanced data macro treats every class equally; micro is dominated by the biggest class | p. 10 |
| Common confusion in sentiment | Don't confuse the *positive class* with a *positive judgement* by the system | p. 11 |
| The three-set framework | Training set → Dev / Dev-test set → Test set, all representative of the problem | p. 13 |
| Why a held-out test set? | Dev tuning leaks information; the test set is the only honest estimate of generalisation | p. 13 |
| k-fold cross-validation | Split the development data into k folds, train on k-1, dev on the remaining; rotate | p. 14 |
| Risk of only doing CV (Church 2021) | You still need the untouched test set; CV-only researchers over-estimate performance | p. 14 |
| Why performance drops on a new test set | Variation, unique properties of the test set not in training, annotation differences | p. 15 |
| Newsreader NERC F1 on CoNLL vs Wikinews | 90.92 → 68.41 (>20% drop, same system) | p. 15 |
| When do you want high recall, low precision? | Tsunami alert / topic search — missing things is worse than false alarms | p. 16 |
| When do you want high precision, low recall? | Auto-delete spam filter — false positives (lost real mail) are worse than missing some spam | p. 16 |
| Common evaluation strategy | First maximise recall (fix variation/sparseness), then improve precision (fix ambiguity/feature selection) | p. 16 |
| Why bag-of-words misses meaning | "the chicken produced an egg" vs "the egg produced a chicken" have identical BoW vectors | pp. 19–20 |
| Sequence labelling task | Predict a label for each individual token given its sequence context | p. 21 |
| Typical sequence output format | IOB tags (B-PER, I-PER, O) — B = beginning, I = inside, O = outside an entity | p. 21 |
| Conditional Random Field (CRF) | Learns sequential dependencies across many features (prev word, prev PoS, gazetteer hits) to label IOB sequences | p. 23 |
| How is a token represented for sequence ML? | Concatenated one-hot vectors: lemma + PoS + dependency + position + prev/next word + prev/next PoS | p. 24 |
| What's a one-hot vector? | A binary vector the size of the vocabulary, with a single 1 marking the word | p. 26 |
| Solution to variable-length sequences | Pad with zeros (or truncate to a fixed length) — described as "an engineering solution" | p. 28 |
| Nice properties of vector representations | Flexible (mixed modalities), memory-efficient, support math (similarity, analogy, average) | p. 35 |
| Why are sparse one-hot vectors a problem? | Vectors are extremely large and mostly empty; hard to generalise; needs rich feature engineering | p. 36 |
| Distributional Hypothesis (Firth, Harris) | "You shall know a word by the company it keeps" — context defines meaning | p. 38 |
| Context vector | Co-occurrence counts of a target word with neighbouring words, from a large corpus | pp. 38–39 |
| Cosine / dot product use | Measures similarity between two context vectors | p. 39 |
| Polysemy problem for context vectors | "bass" the fish and "bass" the voice collapse into one averaged vector | p. 42 |
| Similarity vs relatedness | Vectors mix dimensions of similarity (round, yellow, fruit, celestial) without separating them | p. 42 |
| Word2Vec (Mikolov 2013) | Two-layer neural net trained to predict a word's context; output is a dense 300-dim embedding | p. 46 |
| Word2Vec positive/negative examples | Positive: real (word, context-word) pairs (cat–sat); negative: random pairs (cat–sea) | p. 46 |
| CBOW vs Skip-gram | CBOW predicts the target from context; Skip-gram predicts context words from the target | (mentioned, p. 46) |
| Famous embedding analogy | King − Man + Woman ≈ Queen | p. 41 |
| Embedding visualiser | http://projector.tensorflow.org | p. 40 |
| Why embeddings help classification | Match semantically similar words even if not in training set, as long as they're in the embedding vocabulary | p. 47 |
| Bag-of-embeddings | Average the embeddings of all words in a text → single dense vector for the document | pp. 48–49 |
| doc2vec | Alternative to averaging: learns a single vector for an entire document directly | p. 49 |
| Sparse vs dense vector dims | Sparse = vocabulary length; dense = embedding size (typically 300–500) | p. 51 |
| Static embedding limitation | One vector per word, no matter the sentence — "Apple" the company and "apple" the fruit collide | (problem motivating contextual embeddings) p. 55 |
| Contextual embedding | Each token's vector depends on the surrounding sentence (ELMo, BERT) | pp. 55–56 |
| Self-attention | Each token embedding is reweighted by every other token in the context, learned during training | p. 56 |
| Transformer pre-training objective (BERT) | Masked language modelling — predict the masked-out word from its left and right context | p. 56 |
| Positional encoding | A layer that injects token position into the input because attention is order-blind | p. 56 |
| Q, K, V in self-attention | Query, Key, Value vectors per token; score = Q·K, softmaxed, used to weight V | p. 60 |
| Multi-head attention | BERT base uses 8 heads — each head learns a different attention pattern | p. 61 |
| Encoder-only models | BERT, RoBERTa, DistilBERT, ELECTRA — attend left+right, discriminative, predict masked words | p. 63 |
| Decoder-only models | GPT family, LLaMA, PaLM, GPT-4 — attend only left, autoregressive, predict next word | p. 63 |
| BERT pretraining tasks | (1) Masked language modelling (2) Next-sentence prediction (NSP) | p. 64 |
| Special tokens in BERT input | [CLS] (sentence rep for classification), [SEP] (separator), [MASK] (hidden token to predict) | p. 64 |
| BERT input embedding = sum of what? | Token embedding + sentence (segment) embedding + positional embedding | p. 64 |
| BERT base size | 110 million parameters, 12 encoder layers, hidden size 768, 12 attention heads | p. 65 |
| WordPiece tokeniser | Splits unknown words into known sub-pieces, marked with `##` (e.g. play, ##ing) | pp. 58, 64 |
| GPT-4 size estimate | ~1 trillion parameters | p. 68 |
| Pre-training data examples | Common Crawl, Book Corpus, Billion Word Benchmark, Wikipedia | p. 69 |
| What is fine-tuning? | Take a pre-trained LM and train it further on a small labelled task (text/token classification, QA) | p. 70 |
| Why fine-tuning works | Pre-training (weeks, GPU cluster, unsupervised) gives a strong base; fine-tuning (hours, single GPU, supervised) adapts it | p. 70 |
| Church 2021 description of fine-tuning | "Unreasonably effective" — small labelled set + giant pretrained model beats most from-scratch systems | p. 70 |
| What's added during fine-tuning? | A task-specific head (extra layer) that maps the [CLS] vector (or each token vector) to labels | p. 71 |
| Fine-tuning for text classification (e.g. sentiment) | Predict the label from the [CLS] vector representation of the full text | p. 71 |
| Fine-tuning for sequence labelling (e.g. NER) | Predict a label for each token vector individually | p. 72 |
| Where to find pretrained models | https://huggingface.co (Model Hub, transformers library, inference API) | p. 73 |
| BERT-family models | RoBERTa, DistilBERT, SpanBERT, XLNet, ALBERT, ERNIE, BioBERT, multilingual BERT | p. 67 |

---

## 1. Evaluation metrics

The lecture spends most of its evaluation section on the standard contingency table: TP, FP, FN, TN.

Precision = TP / (TP + FP) — "of everything I predicted positive, how many were actually positive?" (p. 6).

Recall = TP / (TP + FN) — "of everything that was actually positive, how many did I catch?" (p. 6).

F1 = 2·P·R / (P + R) — the harmonic mean. Pulled down hard by whichever of P or R is lower, which is why systems with 99% precision and 1% recall don't get away with it (p. 6).

Accuracy = (TP + TN) / total — looks reasonable but is only honest on balanced data. The slides drive this home with the spam example on p. 8: 100 mails, 20 are spam, the system flags 10 mails of which 5 are correct. Accuracy is 0.80 (because the 75 true negatives dominate), but precision is 0.50, recall 0.25, F1 0.33. Trusting the accuracy here would mean shipping a system that finds only a quarter of the spam.

**Macro vs micro averaging (Sentiment quiz Q1).** The slide (p. 10) uses the urgent / normal / spam example from Jurafsky:

- per-class precision: urgent 0.42, normal 0.52, spam 0.86
- macro-average precision = (0.42 + 0.52 + 0.86) / 3 = 0.60
- micro-average precision = pooled TP / (pooled TP + pooled FP) = 268 / (268+99) = 0.73

Macro treats every class equally regardless of size. Micro pools the counts first, so a large or easy class dominates. The slide note on p. 10: "high score for micro is based on the performance for spam" (the largest class). On imbalanced data the gap can be huge — macro 0.60 vs micro 0.73 is from the same confusion matrix.

**Worked example matching the Sentiment quiz stem.** Imagine 100 reviews, 40 positive and 60 negative. The classifier predicts 50 positive and 50 negative; it gets 10 of the positive predictions right and 20 of the negative predictions right.

- Class = positive: TP=10, FP=40, FN=30 → precision = 10/50 = 0.20, recall = 10/40 = 0.25, F1 = 0.22
- Class = negative: TP=20, FP=30, FN=40 → precision = 20/50 = 0.40, recall = 20/60 = 0.33, F1 = 0.36
- Macro-F1 = (0.22 + 0.36) / 2 = 0.29

The exam stem on macro-averaging always asks you to take the mean of *per-class* scores, never to recombine the counts first.

The lecture also shows a tweet example on p. 12 with 10 tweets that builds two separate per-class contingency tables for positive and negative — this is exactly the layout you draw when computing macro-averaged precision/recall yourself.

## 2. Confusion matrices

Same 2×2 grid as the contingency table on p. 7. Reading it out loud:

- top-left (TP): predicted positive, gold positive
- top-right (FP): predicted positive, gold negative ("Type I error")
- bottom-left (FN): predicted negative, gold positive ("Type II error")
- bottom-right (TN): predicted negative, gold negative

The 3-class extension on p. 9 puts gold labels along the columns and system output along the rows. Per-class precision is "my row's diagonal cell / my row's total" (everything the system labelled that class). Per-class recall is "my column's diagonal cell / my column's total" (everything that was actually that class). The off-diagonal cells tell you the *direction* of confusion — useful for error analysis (e.g. urgent emails get misread as normal more often than as spam).

## 3. Train / dev / test split and cross-validation

Standard three-way split on p. 13: training set, development (or dev-test) set, test set. The slide labels the union of training and dev-test as the "Development Set", and the held-out test set lives outside it.

Why three? You tune hyperparameters on the dev set; if you also touched the test set during tuning you'd be leaking test information and your reported performance would be optimistic. The test set is for one honest measurement at the end.

**k-fold cross-validation** (p. 14) rotates which slice of the dev set acts as the validation fold; with 10 folds you get 10 estimates and you can average them. Useful when the dataset is small. The slide flags a warning that some researchers stop here and never run a separate held-out test — Church 2021 argues this is the "real" test and skipping it inflates reported numbers.

**Overfitting vs underfitting** (background, not in these slides explicitly but assumed):

- *Overfitting:* the model fits the training data too closely, including noise. Training accuracy is high, test accuracy is much lower. Mitigation: more training data, regularisation, smaller / simpler model, early stopping.
- *Underfitting:* the model is too simple to capture the patterns. Training and test accuracy are both low. Mitigation: bigger / more flexible model, more features, less regularisation.

The dev / cross-validation set is what tells you which of the two is happening — you compare train vs dev performance and react accordingly.

**Performance drops on shifted test data.** Slide 15 shows the Newsreader NER F1 going from 90.92 on CoNLL Reuters to 68.41 on Wikinews — over 20% drop with the same system. Reasons listed: variation, unique properties of the test set, annotation differences. This is the practical reason to be sceptical of single-benchmark results.

## 4. Application perspective for evaluation

Slide 16 frames precision vs recall as a deployment trade-off rather than just a number:

- **High recall, low precision**: high risk of missing things, low risk of acting wrongly. Tsunami warnings, topic retrieval for legal discovery — you'd rather flag everything and let a human prune than miss a true positive.
- **High precision, low recall**: low risk of missing things, low risk of acting wrongly. Spam auto-delete — false positives mean lost legitimate mail, which is unacceptable, so the system only acts when very confident.
- **Common dev strategy**: first push recall up (fixes variation and sparseness), then improve precision (handles ambiguity and feature selection).

## 5. Sequence classification

The slides argue (pp. 19–20) that bag-of-words breaks because "the chicken produced an egg" and "the egg produced a chicken" share the same BoW vector, but mean opposite things. Sequence labelling preserves order.

**Sequence labelling task (p. 21):** predict a label for each token given the sequence it lives in. CoNLL-style data shows columns for word, PoS, chunk tag, short shape, and label. Labels follow the **IOB scheme**: B- starts an entity, I- continues it, O is outside any entity. So "American Airlines" becomes B-ORG, I-ORG; the surrounding tokens get O.

**Why context matters:** the same word "Apple" can be ORG or O depending on whether the sentence is about the company or fruit. A classifier looking only at the token can't tell; one that sees "CEO of Apple Inc. resigned" can.

**Conditional Random Fields (p. 23):** the lecture's main sequence model. A CRF learns sequential dependencies across many features simultaneously — previous word, previous PoS, gazetteer membership, word shape — and predicts the IOB label for each token while taking the *neighbouring labels* into account. The diagram shows arrows both vertically (token features → label) and horizontally (previous label → current label).

HMMs are not explicitly covered in this deck; the lecture jumps straight to CRFs, which dominate classical sequence labelling for NER and chunking. If asked about HMMs on the exam, fall back to: directed, generative, models P(words, tags) jointly via emission probabilities (word given tag) and transition probabilities (tag given previous tag), decoded with the Viterbi algorithm. HMMs make strong independence assumptions — the next word depends only on the current tag, not on neighbouring words or syntactic context. CRFs are discriminative, model P(tags | words) directly, and tend to outperform HMMs because they can incorporate arbitrary overlapping features (word shape, gazetteer hits, prefixes, suffixes, surrounding tokens) without needing them to be conditionally independent.

**Why sequence models matter:** in token-by-token classification with an independent classifier, two consecutive tokens can be labelled in an inconsistent way (e.g. I-PER following an O — which is invalid IOB). Sequence models enforce constraints on adjacent labels and weight features that span multiple tokens.

**Representing a sequence as vectors (pp. 24–30):**

- each token is represented by a vector of one-hot encodings concatenated together
- features include lemma, PoS, dependency role, position, previous and next words, previous and next PoS
- the document becomes a *sequence of vectors*, one per token (p. 26)
- different documents have different lengths → pad shorter sequences with zero vectors, or truncate longer ones to a fixed length (p. 28, called "an engineering solution")

The NERC sample on p. 33 is a Kaggle dataset where each token is annotated with about twenty features: id, lemma, next-lemma, next-next-lemma, next-next-pos, next-next-shape, next-next-word, next-pos, next-shape, next-word, pos, prev-iob, prev-lemma, prev-pos, prev-prev-iob, prev-prev-lemma, prev-prev-pos, prev-prev-shape, prev-prev-word, prev-shape, prev-word, sentence_idx, shape, word, tag. In practice you do feature ablation to find which of these actually help.

**Nice properties of vector representations (p. 35):** any feature can be turned into a vector — words, PoS, dependencies, word shape, morphology, even pixels (mixed modalities). You can assign scalar values between 0 and 1 (frequencies, association strengths). Memory-efficient. Supports mathematical operations: similarity, analogy, multiplication, concatenation, averaging, weighting, subtraction.

## 6. Problems with sparse vectors

Slide 36 lists what goes wrong with one-hot encodings at scale:

- Thousands of documents may hold hundreds of thousands of distinct tokens.
- Each token vector reserves a slot for every possible feature value, so the vectors become huge (tens of thousands of dimensions) and mostly empty.
- Generalisation is hard: the model has no notion that "doctor" and "physician" are related, because their one-hot vectors are orthogonal.
- You compensate with rich feature engineering — gazetteers, regexes, hand-crafted patterns.

This motivates the move to dense word embeddings.

## 7. Word embeddings

**The intuition (p. 38, Firth 1957 / Harris 1954):** "You shall know a word by the company it keeps". Build a vector for each word by counting which words appear near it in a large corpus. The lecture's example contrasts "bass" the musical range (co-occurs with voice, register, C, G, key) and "bass" the fish (co-occurs with lake, family, fishing, trout).

A naive **context vector** has length = vocabulary size, with co-occurrence counts (or frequencies) as entries (p. 39). The dot product `a·b = Σ aᵢbᵢ` measures how similar two such vectors are.

In two dimensions (p. 40) you can plot the words and see "bass" and "trout" cluster together (both "fish" related), while "alto" sits far from them along the "range" axis.

**Word2Vec (Mikolov et al. 2013, pp. 46):** a small neural net that learns dense embeddings instead of counting co-occurrences directly.

- Break the contexts of every word into pairs: positive (real co-occurrences in the corpus, e.g. cat–sat) and negative (random pairs, e.g. cat–sea).
- A hidden layer with ~300 nodes; for each input word the weight vector from input to hidden becomes the word's embedding.
- Train so that the hidden layer predicts the *positive* context words and rejects the *negative* ones, adjusting weights with gradient descent.
- After enough passes over enough data, words that share contexts end up with similar weight vectors.

The slide on p. 43 shows the result: cat and dog have similar embedding values (similar contexts: sing, eat, sat, hunt); car and bike likewise; cat and car do not.

**CBOW vs Skip-gram** (not labelled explicitly in this deck but standard Word2Vec variants): CBOW predicts the centre word given a window of context words; skip-gram predicts the surrounding context words given the centre word. Skip-gram tends to work better on rare words; CBOW is faster.

**Embedding dimensionality** (p. 40): "dense, lengths of the number of nodes in the embedding layer (300–500 nodes)". So instead of a one-hot vector of length 50,000 you get a dense vector of length 300.

**Other embedding families (mentioned briefly, p. 67):** GloVe (Pennington et al., based on global co-occurrence matrix factorisation — the embedding is the result of factorising a matrix whose entries are log-co-occurrence counts, so it combines the "count-based" and "predict-based" approaches) and FastText (Bojanowski et al., builds embeddings from character n-grams so it can handle out-of-vocabulary and morphologically rich words — useful for languages like Finnish or Turkish where the same stem produces hundreds of word forms). Both are static embeddings, both not given dedicated slides here. The lecture focuses on Word2Vec as the prototypical static embedding.

**Where embeddings come from in practice:** you rarely train them yourself. Pre-trained vectors are downloaded — Google's Word2Vec, Stanford's GloVe, Facebook's FastText, or the language-specific equivalents. For Dutch you'd use a Dutch-trained Word2Vec or FastText, or one of the multilingual BERT variants.

**Analogy (p. 41):** the famous `King − Man + Woman ≈ Queen` — embedding space captures gender, royalty, plurality as roughly linear directions.

**Problems with context vectors (p. 42):**
- Similarity vs relatedness — round, yellow, fruit, celestial all collapse into one similarity score. The lemon, moon, banana and sun all end up "near" each other but for different reasons.
- Polysemy — "star" the celestial body and "star" the celebrity, "bass" the fish and "bass" the voice, "bat" the animal and "bat" the equipment all share a single vector.

This is exactly the limitation that contextual embeddings (BERT et al.) were built to solve.

**Using embeddings for classification (p. 47):**

- Replace each word in training and test data with its embedding.
- Short dense vectors instead of long sparse one-hots → easier for downstream classifiers.
- Better generalisation for semantically related words.
- Matches words in the test set even if they didn't appear in the training data (as long as they're in the embedding vocabulary).

**Bag-of-embeddings (pp. 48–49):** average the embedding vectors of every word in the document into one summary vector. Information is lost but every dimension is informed by every word. Feed the average vector into a classifier (NB, SVM, logistic regression). The alternative is **doc2vec**, which learns document-level vectors directly during training.

**Sequence representation with embeddings (p. 50):** instead of one-hot vectors per token, replace the word slot with a 300-d embedding while keeping PoS and dependency one-hot slots. The token vector becomes shorter and denser, and similar words (medicine, antibiotics, penicillin, insulin) now sit close in vector space.

**Summary of vector units (p. 51):**

- BoW with label: sparse, dimension = vocabulary length
- Averaged embeddings with label: dense, dimension = embedding size
- Sequence-of-tokens with label: sparse one-hot per token, dimension = vocabulary + PoS + dependency labels + previous and next vocabulary

## 8. Contextual embeddings and transformers

The fundamental shift: static embeddings give one vector per word forever; contextual embeddings give a vector that depends on the surrounding sentence. "Apple" in *Apple Inc.* and *I ate an apple* now get different vectors.

**Deep learning vs classical ML (p. 53):** in classical ML you do explicit feature extraction first, then classification. In deep learning, feature extraction and classification are combined into a stack of neural layers that learn the features end-to-end.

**CNN for text (p. 54):** a convolutional net slides a context window across the embedding matrix, multiple layers stack on top, and the output predicts sentiment, entities, or topics. Backpropagation updates the embedding matrix and the weights based on whether the prediction was right or wrong.

**LSTM (p. 55):** stacked recurrent encoder and decoder, the classic neural MT architecture before transformers. The deck shows the Google neural MT diagram translating German to English.

**Transformers — self-attention (p. 56):**

- Each token embedding can be modified by any other token embedding in its context (sentence).
- During training the model learns which context tokens are important for which target token, because attending to the right neighbours helps it predict the masked context word.
- Position in the sequence is encoded in a separate layer (positional encoding) — self-attention itself is order-blind.
- Many encoding blocks are stacked on top of each other.

**Transformer block architecture (p. 57):** sentence → tokenizer (WordPiece or byte-pair) → subtoken IDs → input embedding + positional encoding → N stacked layers of (multi-head attention → add & norm → feed-forward → add & norm) → linear projection → softmax → output probabilities. The Vaswani et al. 2017 figure shows both encoder (left) and decoder (right) stacks.

**WordPiece tokeniser (p. 58):** the multilingual BERT vocabulary mixes English, Spanish, Arabic, Chinese and Japanese fragments. Tokens prefixed with `##` are continuations of a previous wordpiece (e.g. `play` + `##ing` for "playing"). This handles unseen words by chunking them into known pieces.

**Q, K, V mechanics (p. 60, jalammar illustrated transformer):**

- Each token x₁ generates three vectors: q₁ = x₁·W^Q (query), k₁ = x₁·W^K (key), v₁ = x₁·W^V (value).
- The attention score from token 1 to token 2 = q₁·k₂.
- Scores are scaled by √d_k, softmaxed (so they sum to 1), and used to weight the v vectors.
- The output for token 1 is a weighted sum of all v vectors — the token's new representation reflects its whole context.

**Multi-head attention (p. 61):** BERT base has 8 attention heads per layer, each learning a different attention pattern. The visualisation shows the word "it" attending to "the animal" several layers deep — the model has effectively resolved the pronoun's referent.

**Two types of attention (p. 62):**

- **Encoder models** (BERT, RoBERTa): bidirectional self-attention — every token attends both left and right. Used for understanding tasks.
- **Decoder models** (GPT family): masked / causal self-attention — every token can only attend to tokens to its left. Used for generation, because at inference time you don't yet have the right-hand tokens.

**Encoder-only vs decoder-only families (p. 63, Yang et al. 2023):**

- Encoder-only / BERT-style: discriminative, trained with masked language modelling, predicts masked words. Examples: ELMo, BERT, RoBERTa, DistilBERT, BioBERT, XLM, XLNet, ALBERT, ELECTRA, T5, GLM.
- Decoder-only / GPT-style: generative, autoregressive language modelling, predicts the next word. Examples: GPT-3, OPT, PaLM, BLOOM, MT-NLG, GLaM, Gopher, Chinchilla, LaMDA, GPT-J, LLaMA, GPT-4, BloombergGPT.

**BERT encoder block (p. 64, Devlin et al. 2018):**

- Pre-training tasks: predict the masked word in the sentence + next-sentence prediction (NSP) from sampled positive and negative sentence pairs in Wikipedia.
- The special `[CLS]` token at the start of the input gets a sentence-level representation used for downstream classification. `[SEP]` separates the two sentences in NSP. `[MASK]` marks tokens to predict.
- Input embedding = token embedding + sentence (segment) embedding + transformer positional embedding, summed.

**BERT structure (p. 65):** BERT base has ~110 million parameters, 12 encoder layers, 12 attention heads, hidden size 768. The illustration shows the keys, queries and values being produced by linear projections, processed by 12 self-attention heads, recombined, passed through a feed-forward layer, and stacked 12 times.

**BERT's family of language models (p. 66):** ELMo → BERT splits into ULMFiT, MultiFiT (multilingual), XLM/UDify (cross-lingual), MT-DNN (multi-task) → MT-DNN-KD (knowledge distillation), MASS/UniLM (+generation), SpanBERT (span prediction, remove NSP), RoBERTa (longer training, remove NSP, more data), XLNet (permutation LM), ERNIE (+knowledge graph), VideoBERT / ViLBERT / VisualBERT (cross-modal), BERT-wwm (whole word masking).

**The evolutionary tree of LLMs (p. 67):** three branches — encoder-only (pink: BERT, RoBERTa, ALBERT, DeBERTa, ELECTRA), encoder-decoder (green: T5, mT5, BART, FLAN-T5, GLM), decoder-only (blue: GPT-3/4, ChatGPT, LLaMA, PaLM, BLOOM, GPT-J, Chinchilla, Gopher, Claude). Decoder-only dominates 2022–2023.

**Does size matter? (p. 68)** Roughly log-linear growth in parameter count from ELMo (94M, 2018) → BERT-Large (340M, 2018) → GPT-2 (1.5B) → Megatron-LM (8.3B) → T5 (11B) → Turing-NLG (17.2B) → GPT-3 (175B) → Megatron-Turing NLG (530B) → GPT-4 (~1 trillion). Bigger models tend to perform better, but the deck just observes the trend without making a strong claim.

**ELMo (briefly mentioned on p. 66 as the ancestor of BERT):** uses a bidirectional LSTM rather than a transformer to produce contextual embeddings. Released slightly before BERT, conceptually similar — each token gets a contextual representation built from the surrounding sentence — but architecturally LSTM-based. BERT replaced it because transformers scale better and can be pre-trained on much more data.

## 9. Pre-training and fine-tuning

Two-stage paradigm, the central insight of modern NLP (p. 70):

1. **Pre-training:** weeks on a GPU cluster, *unsupervised*, on terabytes of text. The model is trained on a masked task — predict the missing word, predict the next word. Out of this you get a Transformer language model with 110 million+ parameters that has internalised statistical regularities about language.
2. **Fine-tuning:** hours on a single GPU, *supervised*, on megabytes of annotated/labelled text (sentiment labels, NER tags, QA pairs). You add a small task-specific head and adapt the pretrained weights to the new task.

Church 2021 calls fine-tuning "unreasonably effective" because a tiny labelled dataset combined with a giant pretrained model beats most from-scratch systems by a wide margin (p. 70).

**Pre-training datasets (p. 69):** Billion Word Benchmark (a billion English words), Common Crawl (open web), Book Corpus (with text-speech alignment), ImageNet (for vision), LibriSpeech, LJ Speech, AISHELL-2.

**Fine-tuning for text classification (p. 71):** feed a sentence through the LM, take the `[CLS]` token's final-layer vector, pass it through one extra linear layer ("head"), softmax to a label like positive/negative. During fine-tuning the entire model (CLS head + all transformer weights) is updated, although you usually use a small learning rate so the pre-trained weights aren't destroyed.

**Fine-tuning for sequence labelling / NER (p. 72):** same setup but predict a label per token instead of one for `[CLS]`. The token's contextual embedding flows into a per-token classifier head; the model can label `Apple` as `B-ORG` when the sentence is *The CEO of Apple Inc. resigned.*

**Catastrophic forgetting** (testable in Topic Modelling Q9): if you fine-tune too aggressively on the new task, the model overwrites the general linguistic knowledge it learned during pre-training and performs worse on anything outside the fine-tuning data. Mitigated by:
- using a small learning rate during fine-tuning,
- freezing earlier layers and only fine-tuning the top layers,
- adding a regularisation term that penalises moving too far from the pretrained weights (elastic weight consolidation),
- multi-task fine-tuning so the model still sees diverse data.

Note: the slides themselves don't define catastrophic forgetting in this deck. It's mentioned implicitly through the "internal representation of a transformer is adapted" line on p. 70. The explicit term appears in the Church 2021 paper and in the Topic Modelling lecture; flag this gap when revising.

**HuggingFace (p. 73):** library + Model Hub where researchers upload pretrained models, plus an inference API ("pipelines") that wraps a model with task-specific configuration. https://simpletransformers.ai is mentioned as a higher-level wrapper.

**Practical fine-tuning recipe (Church 2021, summary):**

1. Pick a pre-trained model that matches your domain (BERT-base for general English, BioBERT for biomedical, multilingual BERT for non-English, etc.).
2. Add a small head — a linear layer + softmax for classification, or per-token classifier for NER.
3. Fine-tune on the labelled task data for a few epochs (usually 2–4 is enough).
4. Use a small learning rate (~2e-5) and a warmup schedule to avoid catastrophic forgetting.
5. Evaluate on a held-out test set — never on data you peeked at during fine-tuning.

## 10. Supervised classification algorithms — what the deck actually covers

This part 2 deck does **not** spend dedicated slides on the classical supervised algorithms (Naive Bayes, logistic regression, SVM, decision trees, random forests, MLP). They live in lecture 3 part 1 and in Jurafsky chapter 4. The companion literature you should fall back on for an exam stem about these:

- **Naive Bayes:** generative, assumes feature independence given the class. For text, you compute P(class) × Π P(word | class) for each candidate class and pick the highest. Works surprisingly well for text despite the violated independence assumption because errors tend to cancel and the *ranking* of classes is preserved even if probabilities are miscalibrated. Fast to train (one pass over the data, no iterative optimisation), robust on small data, hard to beat as a sentiment baseline. Standard tricks: add-one (Laplace) smoothing for unseen words, work in log space to avoid underflow.
- **Logistic regression (maximum entropy):** discriminative, models P(class | features) directly with a linear weighted sum followed by sigmoid (binary) or softmax (multiclass). No independence assumption — it can give correlated features the right *combined* weight. Trained by gradient descent on cross-entropy loss with L1 or L2 regularisation. Usually wins over NB when you have enough labelled data because it can downweight correlated redundant features.
- **SVM:** finds the hyperplane that *maximally* separates classes (largest margin between the closest training points and the decision boundary). The kernel trick lets it model non-linear decision boundaries by implicitly projecting features into higher-dimensional space. Strong baseline for high-dimensional sparse text features — linear SVM on TF-IDF was the dominant text classifier from roughly 2000 to 2015. The slides don't go into SVM kernels; assume linear if the exam doesn't specify.
- **Decision trees and random forests:** split feature space recursively along feature thresholds (does the word "great" appear? > go right). Trees are interpretable but tend to overfit. Random forests average many trees trained on bootstrap samples of the data, which reduces variance dramatically. Gradient-boosted trees (XGBoost, LightGBM) are the descendant family that dominates non-text tabular ML.
- **MLP / feed-forward neural net:** stack of linear layers and non-linear activations (ReLU, sigmoid), trained by backpropagation. Can model arbitrary functions if wide and deep enough (universal approximation theorem). The CNN and LSTM diagrams on pp. 54–55 in this deck are specific neural architectures that respect the *structure* of text (sliding windows for CNN, sequential state for LSTM).

The classifier you actually use on top of bag-of-embeddings is mentioned only on p. 49: "Train a classifier (e.g. NB, SVM) to predict labels for the averaged embeddings."

**When to use which (rule of thumb for the exam):**

- Small labelled set, sparse features: Naive Bayes or linear SVM.
- Medium labelled set, want calibrated probabilities and interpretable weights: logistic regression.
- Token-level tagging with neighbour dependencies: CRF (or BiLSTM-CRF, or BERT for token classification).
- Document-level classification with dense embeddings: a simple feed-forward classifier on top of averaged embeddings, or fine-tuned BERT.
- Anything where lots of labelled data and compute are available: fine-tune a pre-trained transformer.

## 11. Vector spaces and TF-IDF (background, not in this deck)

For completeness, since the NLP and Sentiment quizzes assume you know what a vector representation is. The deck on p. 17–18 alludes to bag-of-words representations but doesn't define TF-IDF; that lives in lecture 3 part 1 and in Jurafsky ch 6.

- **Bag of words (BoW):** the document is represented by a vector whose i-th entry is the count of vocabulary word i in the document. Order is lost; "the chicken produced an egg" and "the egg produced a chicken" become identical vectors (this deck's p. 20 example).
- **Term frequency (TF):** raw count of the word in the document, sometimes normalised by document length.
- **Document frequency (DF):** how many documents in the corpus contain the word.
- **Inverse document frequency (IDF):** log(N / DF) — high for rare words, low for common ones. Common formulations multiply TF × IDF so that words frequent in *this* document but rare in the *corpus* get high weight.
- **TF-IDF weighted bag of words:** the standard sparse-vector representation for documents before dense embeddings took over. Each entry is TF(term, doc) × IDF(term).
- **One-hot encoding:** binary version where you just record presence/absence (1/0) instead of frequencies. Used token-by-token in the sequence representations of this deck (pp. 26–32).
- **Cosine similarity:** the angle between two vectors, used to compare documents or words. cos(a, b) = (a·b) / (|a| · |b|). Insensitive to magnitude, only sensitive to direction.

These representations all break down for semantics — words that mean the same thing get orthogonal vectors. Word embeddings (Section 7) were the response.

---

## Likely exam traps

- **Precision and recall are not the same.** Precision = "of what I called positive, how many really were"; recall = "of what was really positive, how many did I catch". The asymmetry between FP (in the precision denominator) and FN (in the recall denominator) is the whole point.
- **Accuracy on imbalanced data is misleading.** The 100-mails-with-20-spam example on p. 8 gets 80% accuracy from a system that catches only a quarter of the spam. If the exam mentions imbalanced data, accuracy is almost certainly the wrong metric.
- **Macro-F1 vs micro-F1.** Macro = mean of per-class scores (every class counts equally regardless of frequency). Micro = pool the counts first, then compute one score (the biggest class dominates). On the sentiment quiz, macro is what's tested.
- **F1 is the harmonic mean, not the arithmetic mean.** F1 = 2PR / (P+R). A precision of 1.0 and a recall of 0.0 give F1 = 0, not 0.5.
- **CRF is sequence labelling, not document classification.** If the stem mentions IOB tags or token-level prediction, the right answer is CRF (or BiLSTM-CRF, or BERT for token classification), not Naive Bayes.
- **Word2Vec produces static embeddings.** Same vector for "Apple" in every context. If the stem asks how to disambiguate sense in context, the answer is contextual embeddings (ELMo, BERT), not Word2Vec.
- **BERT is bidirectional, GPT is left-to-right.** BERT attends to both sides because it's solving masked LM, where the answer is in the middle. GPT attends only to the left because it's generating the next word and doesn't have the right-hand context yet.
- **BERT is a transformer *encoder*.** Not a generic transformer "model". The decoder-style architecture (GPT) is autoregressive.
- **Pre-training is unsupervised on huge text; fine-tuning is supervised on a small labelled task.** Swap these two and the question is wrong.
- **Catastrophic forgetting happens during fine-tuning, not pre-training.** Pre-training is what builds the knowledge; fine-tuning can overwrite it if done too aggressively.
- **CLS token is for sentence-level classification.** Per-token tasks (NER, PoS) take each token's final-layer vector instead.
- **NSP (next sentence prediction) is part of BERT pre-training, alongside masked LM.** RoBERTa later dropped it and got better results, but that detail is beyond this deck.
- **Padding to equal length is "an engineering solution"** (p. 28) — not a linguistic insight. The slide explicitly highlights this so an exam stem might point at it.
- **One-hot vectors are sparse and large** (size = vocabulary). Embeddings are dense and small (size = 300–500). Mixing these up on a stem about vector representations is a common error.

---

## Self-quiz (cover the answers)

1. **Multiple choice.** A spam classifier processes 1,000 emails of which 100 are actually spam. It flags 80 emails as spam, of which 50 are correct. What is the recall?
   a) 0.625
   b) 0.40
   c) 0.80
   d) 0.50
   *Answer: d. Recall = TP / (TP + FN) = 50 / (50 + 50) = 0.50; 0.625 is the precision.*

2. **Multiple choice.** In the same example, what is the precision?
   a) 0.50
   b) 0.80
   c) 0.625
   d) 0.95
   *Answer: c. Precision = TP / (TP + FP) = 50 / 80 = 0.625.*

3. **Multiple choice (negative stem).** Which of the following is **NOT** a reliable metric on heavily imbalanced data?
   a) Macro-averaged F1
   b) Overall accuracy
   c) Per-class precision and recall
   d) Class-weighted micro-F1
   *Answer: b. On skewed data a "predict-majority" baseline can score very high accuracy while missing the minority class entirely.*

4. **Multiple choice.** A three-class classifier scores precision 0.30 on class A, 0.50 on class B, 0.70 on class C. What is the macro-averaged precision?
   a) 0.50
   b) 0.40
   c) Cannot be determined without micro counts
   d) 0.60
   *Answer: a. Macro precision = (0.30 + 0.50 + 0.70) / 3 = 0.50.*

5. **Multiple choice.** Why do researchers use a held-out test set in addition to dev / cross-validation?
   a) Because Sklearn's pipeline API requires three splits
   b) To meaningfully increase the size of the training corpus
   c) Tuning on dev data leaks information; the test set is the only honest measure of generalisation
   d) Because cross-validation is computationally too expensive
   *Answer: c. Dev tuning leaks information into the model; the untouched test set gives the only honest estimate of generalisation.*

6. **Multiple choice.** Which scheme labels tokens with `B-` for the beginning of an entity, `I-` for the inside, and `O` for outside?
   a) BEMO tagging
   b) IOB tagging
   c) BIO-2 tagging
   d) BILOU tagging
   *Answer: b. IOB is the standard CoNLL-style sequence-labelling scheme with B-, I-, and O tags.*

7. **Multiple choice.** A Conditional Random Field for NER differs from a token-level Naive Bayes classifier mainly because:
   a) CRFs model dependencies between neighbouring labels, while Naive Bayes treats each token independently
   b) CRFs are an unsupervised learning method
   c) CRFs require pre-trained word embeddings as input
   d) CRFs are restricted to English-language data
   *Answer: a. CRFs jointly model sequences of labels and capture transition dependencies that Naive Bayes ignores.*

8. **Multiple choice.** According to the distributional hypothesis (Firth 1957, Harris 1954):
   a) Word meaning is innate and universal across speakers
   b) Word meaning is fixed entirely by grammatical structure
   c) Words are essentially random sequences of phonemes
   d) You shall know a word by the company it keeps — meaning emerges from co-occurrence patterns
   *Answer: d. Firth's slogan captures the idea that distributional context defines lexical meaning.*

9. **Multiple choice.** Word2Vec (Mikolov 2013) trains a neural network to:
   a) Translate individual words between languages
   b) Predict context words for a given input word (or vice versa) using positive and negative examples
   c) Classify whole documents into topics
   d) Compute exact corpus co-occurrence counts
   *Answer: b. Word2Vec uses CBOW or skip-gram with negative sampling to learn dense embeddings.*

10. **Multiple choice.** The key limitation of static word embeddings that motivated contextual embeddings is:
    a) Static embeddings can only handle English vocabulary
    b) Static embeddings are too small to be useful in practice
    c) Static embeddings require large labelled training datasets
    d) One vector per word regardless of context — polysemous words like "bass" or "Apple" collapse into a single average
    *Answer: d. Static embeddings produce a single vector per type, blending all senses; contextual models give one vector per token.*

11. **Multiple choice.** Self-attention in a Transformer works by:
    a) Sliding a fixed convolutional window across the input
    b) Computing exact co-occurrence frequencies between tokens
    c) Recurrently processing the sequence left-to-right
    d) Reweighting each token's representation as a learned weighted sum of all tokens in the context (Q·K → softmax → weighted V)
    *Answer: d. Each token's new representation is a weighted average of value vectors, with weights from softmax(Q·K / √dₖ).*

12. **Multiple choice.** Which family of models uses *bidirectional* self-attention and is trained with masked language modelling?
    a) Decoder-only models (GPT, LLaMA, PaLM)
    b) Recurrent neural networks (LSTM, GRU)
    c) Encoder-only models (BERT, RoBERTa, DistilBERT)
    d) Convolutional neural networks (CNNs)
    *Answer: c. Encoder-only BERT-family models attend both left and right and are trained with masked LM.*

13. **Multiple choice.** The `[CLS]` token in BERT is used because:
    a) It is randomly masked during pre-training as a target
    b) It separates two input sentences within a pair
    c) It marks the end of a sentence input
    d) Its final-layer vector summarises the whole input and is fed to a classifier head during fine-tuning
    *Answer: d. The `[CLS]` final-layer vector is the standard sentence representation for classification heads.*

14. **Multiple choice (negative stem).** Fine-tuning a pre-trained BERT does **NOT** typically involve:
    a) Training on a small labelled dataset for a specific downstream task
    b) Re-running the original masked-language-modelling pre-training from scratch
    c) Adding a small task-specific head (e.g. a linear layer + softmax)
    d) Using a small learning rate to avoid catastrophic forgetting
    *Answer: b. Fine-tuning reuses the pretrained weights and only adapts them; it does not redo pre-training.*

15. **Multiple choice.** Catastrophic forgetting refers to:
    a) A pretrained model losing its general knowledge when fine-tuned too aggressively on a small task
    b) Forgetting to save model checkpoints during training
    c) The model failing to converge during fine-tuning
    d) A model crashing partway through training
    *Answer: a. Aggressive fine-tuning can overwrite the broad linguistic knowledge captured during pre-training.*

16. **Multiple choice.** Why does fine-tuning a 110-million-parameter BERT work well on a tiny labelled dataset?
    a) The pre-training already captured general linguistic knowledge; fine-tuning only needs to specialise it to the new task
    b) Because 110 million is not actually a large parameter count
    c) Because BERT memorises the training labels exactly
    d) Because gradient descent magically generalises to new data
    *Answer: a. Pre-training builds reusable linguistic structure; the task head only needs a small labelled set to specialise it.*

---

## What's in this deck but not directly in the NLP quiz

The NLP quiz (10 Qs) is mostly answered by part 1 of lecture 3, not this deck. Part 2 mainly adds:

- Evaluation metrics (precision, recall, F1, accuracy, macro vs micro averaging) — answers **Sentiment quiz Q1** about macro-averaged F1. This metric is not explained in the NLP quiz questions but lives in this deck on pp. 6–10 and in Jurafsky ch 4. **Flag this:** without this material, the Sentiment macro-averaging stem is unanswerable from any other deck.
- Train/dev/test splits and cross-validation — useful background for any quiz about training data.
- Sequence labelling and IOB tagging — explicitly tested in the NER quiz (B-, I-, O), and the CRF answer is the standard sequence model.
- Word embeddings (Word2Vec, GloVe, FastText) and the distributional hypothesis — useful for the NER deck and Topic Modelling discussion of vector representations.
- Contextual embeddings (ELMo, BERT) and the transformer architecture — answers **NER quiz Q7** ("Apple" disambiguation) and supports any question about modern NLP architectures.
- Pre-training and fine-tuning paradigm — answers **Topic Modelling quiz Q9** about catastrophic forgetting (although the term itself isn't explicitly defined in these slides; Church 2021 paper and Topic Modelling deck explain it).
- Encoder-only vs decoder-only model families — useful trivia for any "which architecture is BERT/GPT" stem.

If the exam features a calculation question on macro-averaged P/R/F1, this deck plus Jurafsky ch 4 is your reference. The NLP self-test does not exercise it directly.

If a stem references *specific transformer model names* (RoBERTa, DistilBERT, T5, GPT-4) without further definition, treat them as members of either the encoder-only or decoder-only family — the lecture slides only require knowing the family, not each model's internal differences.
