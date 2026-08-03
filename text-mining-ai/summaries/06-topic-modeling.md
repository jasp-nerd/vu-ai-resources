# 06 — Text categorisation & topic modeling

**Source slides:** tm-ba-lecture-6-topic-modelling.pdf (40 pp.)
**Companion literature:** Saigal & Khanna 2020 (skip SVM math, keep setup/evaluation); Sun et al. 2019 (fine-tune BERT); Churchill & Singh 2021 (skip section 5 on variants)
**Carve-outs (NOT on exam):** Vayansky & Kumar mathematical background, Churchill & Singh §5, SVM variant differences
**Quiz questions drawn from this material:** Text categorisation and Topic modeling (10 Qs) — every quiz Q maps to a specific slide

---

## Cheat sheet (cover the right column, recall the left)

| Term / question | Answer | Slide |
|-----------------|--------|-------|
| What is a topic? | Main area of interest a text is about (events, activities, situations, people, organisations, places, abstract concepts); not a strict definition | p. 2 |
| Why no universal topic set? | Topics are subjective, cultural, and both the world and our view on it change continuously | p. 2 |
| Genre vs topic | Genres are conventional styles of communication (tweet, news, blog, debate), not topics | p. 5 |
| Why longer text is harder for topic detection | Long texts such as news may contain different topics, creating ambiguity | p. 6 |
| Reuters-21578 example topics | grain, wheat, oilseed, soybean, veg-oil; labels for supervised classification | p. 7 |
| Granularity depends on... | Data usage and specific application; not fixed | p. 8 |
| Reuters-21578 size | 120 categories | p. 9 |
| Units for assigning a topic | Sentences, short texts, documents, complete books — depends on final use | p. 5, 10 |
| How to represent topics from clusters | Keyword extraction with TF-IDF | p. 10 |
| Two ways to assign topics | Supervised text classification (label given) and unsupervised clustering (no label) | p. 10 |
| IPTC MediaTopic taxonomy | 1,200 terms, 17 top levels, 4 levels deep; in multiple languages; never complete | p. 3 |
| New topic example | Cybercrime — topics develop continuously | p. 4 |
| Features for supervised classification | BoW, word n-grams, character n-grams, fine-tuned LM | p. 10 |
| Tweet vs news as input | Tweet: short, referential, needs context. News: longer, stories with several events, still referential | p. 6, 7 |
| LSA purpose | Group words with similar distributions to reduce data sparseness (e.g., king/queen/rook/pawn → chess) | p. 13 |
| Supervised classification pipeline | Data acquisition → label → feature construction → data representation → feature selection → train → classifier → evaluation | p. 14 |
| EU JRC EuroVoc Indexer (JEX) | Multi-label categorisation tool with European thesaurus labels | p. 16 |
| JRC-Acquis | Manually labelled legislative texts in 22 EU languages | p. 16 |
| Supervised advantages | Control over topics; high performance when sufficient training data exists | p. 17 |
| Supervised disadvantages | New topics cannot be detected; biased toward training-data distribution; manual effort to maintain topics + data | p. 17 |
| Q6 trap | Control over the topics is an ADVANTAGE, not a disadvantage | p. 17 |
| Topic modelling definition | Clustering task that groups documents on the basis of shared word associations | p. 18 |
| Why do unsupervised topic modelling | No labelled data available, or labels are not appropriate | p. 18 |
| How to label unsupervised clusters | Extract most distinctive keywords with TF-IDF | p. 18 |
| LDA in one line | Generative matrix-factorisation approach: number of topics K fixed in advance | p. 21 |
| LDA two reduced matrices | Document-topic matrix and topic-word matrix derived from document-word matrix | p. 21 |
| LDA improvement over random init | Sampling using proportion of words in D assigned to K, and proportion of word W assigned to K over all docs | p. 21 |
| LDA limitation: instability | Random initialisation + internal sampling → results differ each run | p. 22 |
| Q8 — why is random init a limitation? | Causes unstable topic modelling results (NOT overfitting, NOT computational inefficiency) | p. 22 |
| LDA limitation: topic independence | Topics assumed independent; larger texts mix topics (finance and sports together) | p. 22 |
| LDA limitation: word independence | Bag-of-words ignores semantic drift (queen's gambit vs queen's throne) | p. 22 |
| CTM | Correlated Topic Model — words from related topics more likely to co-occur (covariance matrix); solves topic-independence | p. 22 |
| Hierarchical LDA | Directed graph of topics, grouping into high-level topics | p. 22 |
| Short-text topic models | Assume single topic per message; use meta-data (hashtags, geocodes, user names, dates); little co-occurrence info | p. 23 |
| Dynamic topic modeling | Used when topics change over time (temporal patterns not of interest) | p. 23 |
| BERT fine-tuning three steps (Sun et al.) | (1) further pre-train on within-task or in-domain data; (2) optional multi-task fine-tuning; (3) fine-tune for target task | p. 26 |
| Best BERT layer for classification | Top (last) layer — captures semantic info; lower layers capture morphology/syntax | p. 30, 32 |
| Best fragment strategy on long docs | head+tail beats head-only or tail-only on IMDb/Sogou | p. 30 |
| Catastrophic forgetting (Q9) | Model forgets pretrained info when exposed to new fine-tuning data; mitigate with decreased learning rate | p. 32 |
| ITPT / FiT / MFiT / CDPT | Within-task pretraining / fine-tuning / multitask / cross-domain pretraining | p. 31 |
| Lessons from Sun et al. | Top layers best; lower LR avoids catastrophic forgetting; within-task and in-domain pretraining boost; multi-task only marginal; fine-tuning effective with little data | p. 32 |
| BERTopic pipeline | (1) S-BERT encode (max 512 tokens) → (2) cluster the embeddings → (3) extract keywords with c-TF-IDF (cluster frequency × 1/Nr of clusters) | p. 33, 34 |
| c-TF-IDF | Cluster frequency divided by number of clusters; topic-labelling technique used in BERTopic | p. 34 |
| Evaluation methods (qualitative) | Eye-balling: keyword inspection, visualisation, reading samples per cluster | p. 35 |
| Evaluation: topic recall | Are all topics in a collection identified (against ground truth)? | p. 37 |
| Evaluation: accuracy | Proportion of documents correctly labelled for a topic | p. 37 |
| Evaluation: purity | Accuracy when considering the dominant (highest scoring) topic | p. 37 |
| Evaluation: KL-divergence | Difference between topic probability distributions of model A vs model B | p. 37 |
| Evaluation: perplexity | How well a generative model predicts hold-out documents given a topic | p. 37 |
| Coherence: PMI | Co-occurrence frequency higher than expected from individual frequencies; no ground truth needed | p. 38 |
| Coherence: diversity | Percentage of unique words across topics given top-k words per topic | p. 38 |
| Churchill & Singh factors (Q10) | Dataset Size, Document Length, Noise Level, Noise Types, Expected Setting, Downstream Tasks, Word Co-Occurrence, Data Source — NOT algorithm complexity | p. 36 |

---

## 1. Text and topics

A topic is the main area of interest a text is about. There is no strict definition. A text can be about events (9/11, invasion in Ukraine — many different spreading events, hard to figure out what belongs to the topic, mix of insignificant and important sub-events), activities (socially defined events: soccer, elections, Olympics, traffic, tourism), situations (pandemic), people, organisations, places, or abstract concepts (freedom of speech, democracy, consumer trust, corruption). Each of these can be a topic and the set is open-ended (p. 2).

There is no a-priori definition of all topics because topics are subjective, cultural, and the world plus our view on the world changes continuously (Q2, p. 2). Information brokers such as LexisNexis or Bloomberg make a business out of building personal/company topic profiles to deliver relevant news on demand, but no fixed list captures every topic.

The IPTC MediaTopic taxonomy (International Press Telecommunications Council) tries anyway: 1,200 terms, 17 top levels, 4 levels deep, available in multiple languages (p. 3). Each MediaTopic ID has first digits for the main category and further positions for the subdivisions, e.g. 'conflict, war and peace', 'crime, law and justice'. New topics appear over time (e.g., cybercrime) — it is a continuous process and never complete (p. 4).

Genres are not topics. Genres are conventional styles of communication: bursts of tweets, news articles, blogs, educational/scientific texts, Wikipedia, conversations and debates, product reviews, books/songs/movies, historical analysis, tweets/fora/Reddit/WhatsApp/Facebook/Instagram/TikTok. Texts can be short, long, noisy, time-dependent, dynamic, in large volumes, etc. All of this impacts the technology used to identify topics (p. 5).

### Why longer text is harder (Q1)

Short texts such as tweets are referential and need outside context to identify the topic ("The new US president has said he believes that vaccines are harmful…" — topics might be vaccines, autism, Trump, radicalisation — hard to tell without wider context). News is longer, contains several events, more self-contained but still referential to the world. Longer texts (news in particular) may contain different topics, which creates ambiguity (Q1, p. 6).

Referential means related to a context (here and now), but it can also be a fictional world (GoT, StarTrek) (p. 6).

A Reuters example article on LDC food aid (p. 7) is labelled with topics 'grain, wheat, oilseed, soybean, veg-oil' but other potentially relevant topics are missing: food, food aid, food needs, drought, crops, civil strife, palm oil, food consumption. This is the **granularity** problem.

The article mixes a USDA report on food-aid needs in 69 developing countries (Africa, Middle East, Asia) with grain production in sub-Saharan Africa, wheat consumption, drought-reduced crops in Central America, civil strife, wheat varieties not adapted to tropical climates, vegetable-oil consumption, soybean oil, palm oil — many candidate topics in a single short article. The labels that Reuters chose tell you the audience: a financial wire service whose readers care about commodities.

## 2. Granularity and units

**Granularity depends on data usage and specific application** (Q4, p. 8). It is not fixed in advance. The example Reuters article shows that one editor's chosen labels (grain, wheat, oilseed, soybean, veg-oil) leave out plausible topics like food aid or drought. The choice of topics also tells you something about who annotated the data — Reuters is a financial wire service so commodity labels dominate (p. 9, 120 categories).

The Reuters-21578 category list (p. 9) is dominated by commodities and economic indicators: bfr, castorseed, citruspulp, corn-oil, cottonseed, cruzado, dkr, hk, lin-meal, peseta, rape-meal, red-bean, ringgit, rupiah, skr, castor-oil, cornglutenfeed, fishmeal, groundnut-oil, lin-oil, linseed, rye, sun-meal, wool, can, copra-cake, cotton-oil, dfl, f-cattle, lit, nkr, palladium, palmkernel, rand, saudriyal, sfr, austdlr, cpu, nzdlr, plywood, pork-belly, tapioca, coconut, potato, propane, coconut-oil, instal-debt, inventories, naphtha, jet, rape-oil, sun-oil, l-cattle, groundnut, nickel, platinum, oat, dmk, tea, lei, lumber, sunseed, income, housing, stg, heat, soy-oil, hog, retail, soy-meal, fuel, orange, strategic-metal, wpi, tin, lead, rapeseed, sorghum, silver, pet-chem, palm-oil, zinc, meal-feed, rubber, barley, alum, cotton, gas, ipi, iron-steel, rice, yen, carcass, jobs, copper, reserves, cpi, livestock, bop, soybean, nat-gas, gold, veg-oil, coffee, gnp, sugar, money-supply, oilseed, dlr, corn, ship, wheat, interest, sugar, trade, grain, crude, money-fx, acq, earn. The numbers next to each are document counts — heavily skewed toward earn (3987), acq (2448), money-fx (801), crude (634), grain (628), trade (513).

**Units at which a topic can be assigned** (Q5, p. 10):
- Sentences (e.g., titles)
- Short texts (tweets)
- Documents (news article, blog post)
- Complete books

→ All of the above. The unit depends on the final use.

## 3. Text categorisation (supervised)

Topic classification is a kind of text classification. Text classification is a broader term covering any association between a label and a text — sentiment, genre, language, intent, topic (p. 10). So topic categorisation is a specific instance of the broader text-classification problem.

The supervised setup needs labels at the document level. Workflow (p. 14):
1. Data acquisition → dataset
2. Data analysis and labelling → labelled dataset (labels can be sentiment, topic, genre, etc.)
3. Feature construction and weighting
4. Data representation
5. Feature selection and projection
6. Training a classification model → classifier
7. Solution evaluation

Features (p. 10):
- Explicit feature extraction: bag-of-words, word n-grams, character n-grams
- Fine-tuning of language models (covered in section 8)

Bag-of-words (BoW) ignores word order. Word n-grams (bigrams, trigrams) capture short-range order. Character n-grams are robust to spelling variation and morphology and useful for noisy social-media text.

TF-IDF weights give the information value of a word for a document (p. 13). High TF-IDF means a word is frequent in this document but rare across the corpus — exactly the words that are distinctive for the document's topic. Dimensionality reduction via Latent Semantic Analysis (LSA) groups words with similar distributions to decrease data sparseness — e.g., king, queen, rook, pawn, bishop, knight all vote for the concept of chess so any of them counts toward the same concept (p. 13). LSA precedes LDA historically; it factorises the document-word matrix with singular value decomposition and is appropriately listed in the topic-model survey table as one of the older static approaches.

Multi-label classification is one-against-all: a text can carry several topic labels at once.

### Q3 — most important difference between text categorisation and topic modelling

For text categorisation the topics are given a priori (you have a label list). Topic modelling does not assume an a-priori definition of topics — the topics emerge from the data (p. 14, 18).

### Q6 — advantages and disadvantages of supervised topic classification (p. 17)

**Advantages:**
- Control over the topics (you decide the label set)
- High performance, given sufficient training data for the relevant topics

**Disadvantages:**
- New topics cannot be detected (model only knows training labels)
- Biased towards the distribution of training data
- Manual effort to maintain topics and training data

The Q6 trap: "control over the topics" is an **advantage**, not a disadvantage. The other three answer options ARE disadvantages.

Examples of supervised tools (p. 16):
- JRC EuroVoc Indexer (JEX) — multi-label categorisation tool, labels from the European thesaurus of topics for European politicians
- JRC-Acquis — manually labelled EU legislative texts in 22 official EU languages
- European Joint Research Centre Newsbrief (p. 15) — live clustering of news per language

## 4. Topic modelling (unsupervised)

Topic modelling is a **clustering task** that groups documents on the basis of their shared word associations (p. 18). The pipeline is: take a collection of documents → compute some representation of each document (BoW, TF-IDF vector, or sentence embedding) → cluster the documents on similarity → label each cluster with the words that are most distinctive of that cluster.

Why use it? When there is no labelled data, or when labels are not appropriate for your data. Assumes that any set of documents can be split into groups/clusters that use similar words.

How to label clusters? Extract the most distinctive keywords from the cluster, typically with TF-IDF (Q7, p. 18). This is the standard cluster-labelling technique. The Q7 distractor "domain experts manually assign labels" is plausible but the lecture's answer is TF-IDF keyword extraction.

The National Science Agenda example (p. 19, 20): 11K research questions with titles, descriptions and keywords; term extraction plus hierarchical clustering; visualised in the VU Topic Browser (NWO Wetenschapsagenda). A selected cluster of 133 questions shows top words like 'fossiele_brandstoffen', 'energie', 'opwarming_van_de_aarde', 'duurzame_energie', 'energiebronnen', 'brandstof' — clearly an energy/climate cluster. The visualisation also shows neighbouring clusters connected by edges, so you can see which topics are related without anyone having defined the labels in advance.

### Topic-modelling intuition (p. 20)

1. Input is a collection of documents in which particular words occur (dog, animal, cat, Olympics, AI, ...).
2. Build a vocabulary of individual words, treated as occurring independently in a document (BoW).
3. Map words to an arbitrary intrinsic representation of a topic, then map a document to a topic on the basis of how many of its words are assigned to that topic.
4. Iteratively increase the relationship between a word and a hidden topic, and use this to pool a document to a hidden topic.

This is contrastive learning at the word level and at the document level: the model learns "probability of words given a topic" and "probability of topics given a word". The slide's toy example uses three latent topics (Animals, Sports, Tech) and shows how documents about dogs and cats both pool toward Animals, while a document about AI bots beating Dota players pools toward Sports + Tech.

## 5. LDA — intuition only (math is carve-out)

Latent Dirichlet Allocation (Vayansky & Kumar, 2020 — math is NOT on the exam, but the conceptual story is).

LDA is generative: how likely is a document for a hidden/latent topic? It is a **matrix factorisation** technique. The number of topics K must be set in advance (p. 21).

A collection of documents is represented as a document-word matrix. From this, two reduced matrices are derived:
- **Document-topic matrix** (which topics are in which document)
- **Topic-word matrix** (which words belong to which topic)

K is fixed. Random initialisation of the reduced matrices is improved using sampling on:
- The proportion of words in a document D assigned to topic K
- The proportion of a word W assigned to topic K over all documents in which W occurs

By optimising the probability and iterating, the model clusters documents based on word associations over topics. The output you actually use is the document-topic matrix (each row of which tells you the probability distribution over topics for that document) and the topic-word matrix (each row of which tells you the probability distribution over words for that topic). Topic labels for humans are then derived by taking the top-N words from each row of the topic-word matrix.

A "topic" in LDA is therefore not a label string but a probability distribution over the vocabulary. The same vocabulary word can appear in several topic distributions with different probabilities. A document is not assigned to one topic — it is assigned a mixture of topics.

### LDA limitations (p. 22)

- Fixed number of topics → must run many times to find optimal K. There is no single right K, and the user has to experiment or use heuristics like topic coherence to pick one.
- **Random initialisation and internal sampling → results differ for each run** (Q8 answer: this causes unstable topic modelling results, NOT overfitting, NOT computational inefficiency). Run LDA twice on the same data with the same K and you can get two different topic sets. This is a reproducibility problem.
- Topics independent of each other → larger texts that exhibit mixed topics (e.g., finance and sports together) are not modelled well. An article about a footballer's contract negotiation should activate both finance and sports topics but LDA treats them as separate axes with no co-variation.
- Words treated as independent → bag-of-words ignores semantic drift across documents (queen's gambit vs queen's throne — same surface word, different topic).

A "topic" in LDA is therefore a probabilistic object, not a string label. The labels you see in published papers are just the top words from the topic-word distribution — the model never produces a human label by itself.

### Alternatives mentioned (do not memorise math)

- **Correlated Topic Model (CTM):** uses a covariance matrix so words from related topics are more likely to co-occur in a topic. Solves the topic-independence problem.
- **Hierarchical LDA:** a directed graph of topics grouped into high-level topics.
- **Embedding-based representations:** for every word add related words to topics, which solves data sparseness.
- **Short-text topic models:** each message has a single topic (few words → one topic); use meta-data (hashtags, geocodes, user names, dates); little co-occurrence info.
- **Time-based topic modelling:** temporal buckets, or continuous rise and fall of topics.
- **Dynamic topic modelling:** when topics change over time but the temporal pattern itself is not of interest.

None of these works out of the box. Each one is a patch on a specific LDA weakness, but adopting them always introduces new hyperparameters and new failure modes. The takeaway is that LDA-family models are not a finished tool — they are a starting point that needs to be picked carefully for your data.

The Churchill & Singh 2021 Table 1 (p. 24) compares many topic models on Methodology (generative / graph-based / matrix-based / NLP-aided), Designed For (static / online / temporal), and Document Type (short / long). The list includes LSI, pLSI, DMM, LDA, HDP, CTM, DTM, TOT, SWB, Online LDA, Online HDP, MTTM, cDTM, NMF, ETM, TS, TFM, PTM, BTM, SATM, LF-DMM, LF-LDA, NVDM, lda2vec, GSDMM, GPUDMM, GPUPDMM, DREx, CSTM, WELDA, LapDMM, CluWords, CluHTM, D-ETM, TND. Don't memorise these names — just know that the survey landscape is large and diverse.

Vayansky & Kumar's Fig. 8 (p. 25) gives a decision tree on choosing between LDA, Pachinko Allocation, CTM, Mixture of Unigrams, Pseudo-document Topic Model, Self-Aggregating Topic Model, Topics over Time, or Dynamic Topic Model. The decision tree itself is carve-out math — only the existence of the choice problem matters. The first branch is "average words per document ≥ 50?" — if yes you start in the long-document branch (LDA, CTM, Pachinko, DTM territory), if no you go to the short-document branch (Mixture of Unigrams, Pseudo-document, Self-Aggregating).

## 6. Fine-tuning BERT for text classification (Sun et al. 2019)

This is the modern supervised-classification track. Pre-trained BERT (or any transformer LM) replaces hand-built features. The Sun et al. paper describes three ways to fine-tune BERT for text classification (p. 26):

1. **Further pre-train BERT** on within-task training data or in-domain data (unsupervised, masked task)
2. **Optional multi-task fine-tuning** with several related supervised tasks (e.g., NERC, sentiment, topic) — adapting internal representations to capture more aspects
3. **Fine-tune BERT for the target task** (supervised, with topic labels)

The diagrams on p. 27 and p. 28 show how unsupervised masked-task pre-training (terrabytes of text) feeds into a transformer language model, and how labelled data (topic labels, NERC, sentiment) is used in supervised fine-tuning. The target representation is the CLS token of title, first sentence, or tail.

Datasets used (p. 29): IMDb, Yelp P, Yelp F, TREC, Yahoo Answers, AG's News, DBPedia, Sogou News. Sentiment / Question / Topic classification. Some documents exceed BERT's 512-token limit, so the head/tail strategy matters.

### Best layer and best fragment (p. 30)

- The **last (top) layer** of BERT is most effective for the text-classification task. Top layers capture semantic information; lower layers capture morphological/syntactic info.
- Table 3 in Sun et al. (slide p. 30) shows the test error dropping monotonically from Layer-0 (11.07%) to Layer-11 (5.42%) on IMDb. Concatenating, mean-pooling, or max-pooling the last 4 layers gives essentially the same result as just using Layer-11.
- Head+tail beats head-only or tail-only on IMDb and Sogou — combining the start and end of the document captures more relevant context. On IMDb, head+tail gives 5.42% error while head-only gives 5.63% and tail-only 5.44%. On Sogou the difference is sharper: head+tail 2.43%, head-only 2.58%, tail-only 3.17%.

### Pre-training: in-domain vs cross-domain (p. 31)

In-domain further pre-training (sentiment task pre-trained on sentiment data) gives the lowest test error rates. "all" further pre-training (combine all training sets) helps in some cases but in-domain wins for the domain you target. Without pre-training (the "w/o pretrain" row), error rates are systematically higher — confirming the value of an extra in-domain pretraining pass before fine-tuning.

A concrete example from the table on p. 31: IMDb (sentiment domain) fine-tuned after further pretraining on IMDb itself gives 4.37% test error, the best in its column. Same model with cross-domain further pretraining (e.g., further pretrained on TREC question data) gives 5.65%. Without any further pretraining, 5.40%. The pattern repeats across most datasets.

### Multi-task and proportion of training data (p. 32)

Sun et al. acronyms:
- ITPT = within-task pre-training (further pretrain on the target task's training data, unsupervised)
- FiT = fine-tuning (supervised, on the target task labels)
- MFiT = multi-task fine-tuning (fine-tune on several related supervised tasks together)
- CDPT = cross-domain pre-training (further pretrain on related but not identical domain data)

BERT-CDPT-MFiT-FiT achieves the best IMDb result (4.96% test error). The blue ITPT line in Fig. 4 stays well below the red FiT-only line for all training-data proportions — within-task pre-training helps especially when little training data is available. At 0.4% of the training examples, FiT-only is around 17% error while ITPT+FiT is around 9%. At 100% of training data the gap is still there but narrower (~5.4% vs ~4.4%).

Takeaway for the exam: more pre-training = lower error; multi-task fine-tuning adds only marginal gains; even with very little labelled data, fine-tuning still works as long as you do in-domain pre-training first.

### Catastrophic forgetting (Q9, p. 32)

Catastrophic forgetting is **the tendency of a model to forget information learned during pre-training when exposed to new data during fine-tuning**. If the model takes big steps it can completely change the internal representations learned in pre-training.

Mitigation: decrease the learning rate during fine-tuning. Smaller updates → less overwriting of pre-trained weights. Intuitively, the pretrained weights encode a lot of general linguistic knowledge built up from terrabytes of text; aggressive gradient updates during fine-tuning can wipe that knowledge out and leave a model that only knows its tiny labelled task.

This is a fine-tuning phenomenon. It is NOT about learning multiple tasks. It is NOT about being effective with little data (that is a separate finding). And it is NOT the same as overfitting — overfitting is about the model memorising training examples; catastrophic forgetting is specifically about losing the prior pretraining knowledge.

### Sun et al. lessons learned (p. 32)

- Top layer(s) are most useful for text classification
- Decreasing learning rate overcomes catastrophic forgetting
- Within-task and in-domain pre-training boost performance
- Multi-task fine-tuning helps marginally
- Fine-tuning is already effective with little training data

## 7. Embedding-based topic modelling (BERTopic)

BERTopic (Grootendorst 2020) is an unsupervised topic-modelling pipeline that uses a pretrained transformer (p. 33–34):

1. Represent each text as up to 512 tokens with a contextual transformer model (S-BERT — Sentence-BERT — has a fine-tuned CLS token to represent a sentence).
2. Apply clustering (e.g., LDA-style) to learn a relation between the embedding representations and topics.
3. Extract keywords from each cluster using **c-TF-IDF** = term frequency × (1 / number of clusters). Words that are frequent in one cluster but rare across clusters become the topic label.

This is unsupervised throughout: masked-task pre-training of the transformer, then unsupervised clustering of sentence representations, then unsupervised keyword extraction (p. 34). The diagram on p. 34 shows terrabytes of text feeding into a masked task → S-BERT (max 512 tokens) → sentence representations from target texts → clustering → clusters K → keywords via cluster frequency × 1/Nr of clusters.

Why this can beat LDA:
- Semantically coherent topics because embeddings encode semantic similarity (queen's gambit and queen's throne are no longer the same word).
- Less sensitive to vocabulary choice and to surface-form variation.
- The CLS token of S-BERT is already optimised to represent a whole sentence, so even short texts get meaningful representations.
- No need to fix K in advance the same way LDA does — clustering algorithms like HDBSCAN can find K from the data.

## 8. Evaluation

Evaluation of topic models is harder than evaluation of supervised classifiers because there is often no ground truth. Three families of approach exist: qualitative, quantitative with ground truth, and quantitative without ground truth (coherence-style).

### Qualitative (p. 35)
- Explicitly labelled documents (ground-truth topics) — compare predictions to gold
- Eye-balling: keyword extraction and inspection, visualisation (National Research Agenda, Newsbrief — graph with connections), reading samples per cluster

### Quantitative — needs ground truth (p. 37)
- **Topic recall:** are all topics in a collection identified to the true degree (ground truth)?
- **Accuracy:** proportion of documents correctly labelled for a topic
- **Purity:** accuracy considering the dominant (highest scoring) topic
- **KL-divergence:** difference between topic probability distribution of model A and model B (B may be ground truth or another approach)
- **Perplexity:** how well a generative model predicts hold-out documents given a topic

### Quantitative — coherence (p. 38)

How noisy or unintelligible are topics?

- **Precision:** proportion of top-scoring (keyword) words from the approximated topic that are in the ground-truth topic. Needs ground truth. A high precision means the topic the model found really is the topic.
- **Pointwise Mutual Information (PMI):** co-occurrence frequency of words in a topic higher than expected given their individual overall frequency. No ground truth needed. Measures the frequency of the combination of two words relative to the frequency of the individual words. If "wheat" and "grain" co-occur more than chance would predict, they cohere as a topic.
- **Diversity:** word overlap across topics; percentage of unique words in the topic set given the top-k words of each topic. No ground truth needed. Tells you how many words are unique to a topic and don't occur in other topics. Low diversity = topics are repeating themselves; high diversity = topics genuinely cover different parts of the vocabulary.

A practical rule: combine PMI (within-topic coherence) and diversity (across-topic distinctness) when no ground truth exists. Use precision/recall/accuracy/purity when you do have a labelled gold standard. Use KL-divergence to compare two model outputs against each other.

## 9. Choosing a topic model (Churchill & Singh 2021, Fig. 6, p. 36)

The eight factors are arranged as petals around a central "Data Source" (Research Articles, Newspapers, Webpages, Social Media, Survey Responses, Blogs):

1. **Data Set Size** (Small, Medium, Large, Very Large) — different models scale differently; some struggle on small data, some struggle on very large data.
2. **Document Length** (Phrases, Sentences, Paragraphs, Pages) — short-text topic models (assuming one topic per message) only make sense when documents are short.
3. **Noise Level** (Low, Moderate, High) — research articles are low noise, social media is high noise.
4. **Noise Types** (Random, Biased, Domain-specific) — different mitigation strategies apply to each.
5. **Expected Setting** (Static, Online, Temporal, Streaming) — a static dataset uses LDA; an evolving dataset over time uses Dynamic Topic Model or Online LDA.
6. **Downstream Tasks** (Text Classification, Conversation Dynamics) — what you do with the topics shapes which model you pick.
7. **Word Co-Occurrence** (Low, Moderate, High) — short texts have low co-occurrence, which hurts vanilla LDA.
8. **Data Source** (centre of the diagram) — the meta-factor: research articles, newspapers, webpages, social media, survey responses, blogs.

### Q10 trap

"Complexity of the algorithm" is NOT one of the listed factors. It sounds reasonable but Churchill & Singh's set is the eight above. The quiz lists Dataset Size, Noise Level, Document Length as legitimate factors, and "the complexity of the algorithm" as the non-mentioned distractor.

---

## Likely exam traps

- **Q6 trap:** control over topics is an ADVANTAGE of supervised classification, not a disadvantage. The other three options (manual effort, new topics cannot be detected, bias toward training distribution) are disadvantages.
- **Q10 trap:** "complexity of the algorithm" sounds plausible but is NOT in Churchill & Singh's factor list. Dataset Size, Document Length, Noise Level, Noise Types, Expected Setting, Downstream Tasks, Word Co-Occurrence, Data Source — these are the eight.
- **Q3 swap trap:** text categorisation has topics GIVEN; topic modelling does NOT assume given topics. Don't reverse them.
- **Q8 trap:** LDA instability comes from random initialisation + internal sampling. The wrong answers are "overfitting" and "computationally inefficient" — both sound technical but don't fit.
- **Q9 trap:** catastrophic forgetting happens during FINE-TUNING (the model overwrites pretrained knowledge). It is not about learning multiple tasks, not about needing little data, and not about enhancing performance.
- **Q1 distractor:** "longer texts have more variation in words to express topics" is plausible-sounding but the correct framing is that long texts can carry multiple topics → ambiguity.
- **Q7 trap:** TF-IDF keyword extraction beats domain-expert manual labelling as the answer, even though both work in practice — the lecture explicitly highlights TF-IDF as the standard.
- **Q4:** granularity is NOT always fixed and NOT always fine- or coarse-grained — it depends on data usage and the application.
- **Q5:** at what unit can topics be assigned? All of: sentences, short texts, documents, books → all of the above.
- **Q2:** the reason for no universal topic set is subjectivity + continuous change of the world. Not "limited set with many descriptions" and not "topic keywords vary text to text."

---

## Self-quiz (cover the answers)

**1.** Why is it harder to detect topics in longer text than in shorter text?
a) Long texts have more vocabulary variation across paragraphs
b) Long texts provide more detail per topic
c) Long texts express stronger opinions throughout
d) Long texts can contain several different topics, creating ambiguity ✓

**2.** Which of the following is NOT a disadvantage of supervised topic classification?
a) Results biased toward the training data distribution
b) Manual effort to maintain training data and topics
c) Having direct control over the chosen topics ✓
d) New topics absent from training data cannot be detected

(Negative-stem trap: read the "NOT".)

**3.** What is the main difference between text categorisation and topic modelling?
a) Categorisation has given topics; topic modelling does not ✓
b) Topic modelling produces finer-grained topic groupings
c) Topic modelling is hierarchical, categorisation is not
d) Topic modelling uses full texts, categorisation uses keywords

**4.** Which factor is NOT listed by Churchill & Singh (2021) when choosing a topic model?
a) Overall noise level
b) Document length
c) Algorithm complexity ✓
d) Word co-occurrence

**5.** At what unit can a topic be assigned in topic modelling?
a) Short texts (like tweets)
b) Individual sentences
c) Books or longer documents
d) All of the choices above ✓

**6.** Why is random initialisation considered a limitation of LDA?
a) It produces unstable results across runs ✓
b) It causes the model to overfit training data
c) It is not really a meaningful limitation
d) It makes LDA computationally inefficient

**7.** Catastrophic forgetting refers to:
a) Becoming more effective with little fine-tuning data
b) A model losing pretrained knowledge during fine-tuning ✓
c) Improved performance gained from learning new tasks
d) Forgetting how to learn across multiple new tasks

**8.** Which is NOT true of cluster labelling in topic modelling?
a) BERTopic uses c-TF-IDF for label extraction
b) Random cluster words are picked as the labels ✓
c) TF-IDF can extract distinctive keywords
d) Domain experts can also assign labels

(Negative stem.)

**9.** Granularity of topics depends on:
a) Data usage and specific application ✓
b) The number of topics (always fixed)
c) Always being fine-grained in practice
d) Always being coarse-grained in practice

**10.** Why is it hard to agree on a universal topic set?
a) Too much keyword variation across different documents
b) Topics are subjective; views and the world keep changing ✓
c) Topics depend on keywords that vary text to text
d) Limited topics but many ways to describe them

**11.** Which statement about fine-tuning BERT is correct?
a) Top layers capture semantic info, best for classification ✓
b) Lower BERT layers are best for text classification
c) Within-task pre-training hurts overall performance
d) Multi-task fine-tuning yields massive performance gains

**12.** In BERTopic, which sequence is correct?
a) Cluster first, then embed with S-BERT, then extract keywords
b) Use bag-of-words, cluster with k-means, label with PMI
c) Embed with S-BERT, cluster, extract keywords via c-TF-IDF ✓
d) Train LDA first, then embed with BERT, then label manually

---

## Slide-by-slide compact map

| Slide | Title | Key takeaway |
|-------|-------|--------------|
| 1 | Title | Lecture 6 — Topic Modelling and Text Classification, Ilia Markov |
| 2 | What is a topic? | Events, activities, situations, people, places, abstract concepts; no a-priori definition |
| 3 | IPTC | 1,200 terms, 17 top levels, 4 levels deep, multilingual |
| 4 | IPTC | New topics keep appearing (cybercrime), continuous process |
| 5 | What is (not) a topic | Genres are not topics; communication styles |
| 6 | Text and topics | Tweet vs news; referential to a context (real or fictional) |
| 7 | Text and topics | Reuters food-aid example; topics highlighted in red |
| 8 | Text and topics | Granularity depends on data usage |
| 9 | Reuters-21578 | 120 categories; choice tells you about annotators |
| 10 | How to assign a topic | Supervised vs unsupervised; units; TF-IDF for keyword extraction |
| 11 | Literature | Saigal & Khanna, Churchill & Singh, Vayansky & Kumar, Sun et al. |
| 12 | Supervised topic classification | Training data with text and labels |
| 13 | Supervised | BoW, TF-IDF, LSA (group similar-distribution words) |
| 14 | Supervised | Pipeline: acquire → label → features → train → evaluate |
| 15 | Newsbrief JRC | Live topic clustering over news |
| 16 | EuroVoc / JRC-Acquis | EU thesaurus and 22-language legislative corpus |
| 17 | Supervised pros/cons | Pros: control, performance. Cons: new topics, bias, manual effort |
| 18 | Unsupervised topic modeling | Clustering on shared word associations; TF-IDF labels |
| 19 | National Science Agenda | 11K questions; hierarchical clustering visualisation |
| 20 | Topic modeling intuition | Document-word, topic-document, topic-word mappings |
| 21 | LDA | Matrix factorisation; K fixed in advance |
| 22 | LDA limitations | Fixed K, random init, topic independence, word independence; CTM and hierarchical LDA |
| 23 | LDA alternatives | Embeddings, short-text models, dynamic topic modeling |
| 24 | Churchill & Singh table | Survey of many topic models |
| 25 | Vayansky & Kumar decision tree | Pick a model based on doc length and topic relationships |
| 26 | Pretrained models | Sun et al. — three ways to fine-tune BERT |
| 27 | Fine-tuning + continued pretraining | Unsupervised mask → supervised fine-tune diagram |
| 28 | Fine-tuning on multiple tasks | NERC, sentiment, topic — multi-task |
| 29 | Datasets | IMDb, Yelp, TREC, Yahoo, AG, DBPedia, Sogou |
| 30 | Layers and fragments | Top layer best; head+tail best fragment |
| 31 | In-domain vs cross-domain | In-domain pre-training wins for the target domain |
| 32 | Multi-task + % data; lessons | ITPT, FiT, MFiT, CDPT; catastrophic forgetting; small data still works |
| 33 | BERTopic | S-BERT embeddings + cluster + c-TF-IDF |
| 34 | BERTopic diagram | Masked task → S-BERT → clustering → keywords |
| 35 | Evaluation qualitative | Eye-balling, keyword inspection, visualisation, reading samples |
| 36 | Choosing a topic model | Eight Churchill & Singh factors |
| 37 | Evaluation quantitative | Recall, accuracy, purity, KL-divergence, perplexity |
| 38 | Coherence | Precision, PMI, diversity |
| 39 | Master's programs | Language and AI; Research Master's in Linguistics |
| 40 | (final / blank) | — |

## Quick-revision recall sheet

These are the ten one-liners you should be able to produce from memory before the exam.

1. **Topic** = main area of interest a text is about; no strict definition; open-ended set.
2. **Why long text is harder:** long texts contain multiple topics → ambiguity.
3. **Why no universal topic set:** topics are subjective; world and view on world change continuously.
4. **Granularity** depends on data usage and specific application — not fixed.
5. **Categorisation vs modelling:** categorisation has topics given a priori (supervised); modelling does not (unsupervised).
6. **Supervised advantages:** control over topics, high performance with enough training data.
7. **Supervised disadvantages:** can't detect new topics, biased toward training distribution, manual maintenance effort.
8. **Cluster labelling:** distinctive keywords via TF-IDF (or c-TF-IDF in BERTopic).
9. **LDA instability:** random initialisation + sampling → different topics per run.
10. **Catastrophic forgetting:** model loses pretraining knowledge during fine-tuning; mitigate with lower learning rate.
11. **Churchill & Singh factors:** Dataset Size, Document Length, Noise Level, Noise Types, Expected Setting, Downstream Tasks, Word Co-Occurrence, Data Source. NOT algorithm complexity.

## Mapping every quiz question to a slide

| Quiz # | Topic | Slide | Answer keyword |
|--------|-------|-------|----------------|
| 1 | Why is long text harder? | p. 6 | Multiple topics → ambiguity |
| 2 | No universal topic set | p. 2 | Subjective + world changes |
| 3 | Categorisation vs modelling | p. 14, 18 | Topics given vs not given |
| 4 | Granularity depends on | p. 8 | Data usage and application |
| 5 | Units a topic can be assigned to | p. 5, 10 | All of the above |
| 6 | NOT a disadvantage of supervised | p. 17 | Control over topics (= advantage) |
| 7 | Cluster labelling | p. 10, 18 | TF-IDF distinctive keywords |
| 8 | LDA random init limitation | p. 22 | Unstable results |
| 9 | Catastrophic forgetting | p. 32 | Forgets pretraining when fine-tuned |
| 10 | NOT a Churchill & Singh factor | p. 36 | Algorithm complexity |

## What's in the quiz but NOT in the slides

All 10 Topic quiz questions map cleanly to specific slides (p. 2, 6, 8, 10, 14, 17, 18, 22, 32, 36). No outside knowledge needed beyond what is stated in the lecture, the Sun et al. lessons, and the Churchill & Singh factor list. This is the most thorough alignment of any of the six quizzes for this course.

## Common confusions to clear up before the exam

- **Topic vs genre.** A topic is what a text is *about* (vaccines, autism, climate change). A genre is *how* it is communicated (tweet, blog, news article, scientific paper, Wikipedia article, debate). Genres are about communication style; topics are about content. The lecture explicitly distinguishes them (p. 5).
- **Topic vs document.** A topic is not a document and not a string; in LDA a topic is a probability distribution over the vocabulary. A document is a probability distribution over topics. These are different mathematical objects.
- **Supervised vs unsupervised.** Supervised needs labelled training data; unsupervised does not. Topic modelling is the unsupervised branch. Topic classification is the supervised branch.
- **TF-IDF vs c-TF-IDF.** TF-IDF weights a word's information value for a single document. c-TF-IDF (used in BERTopic) weights a word's information value for a whole cluster — frequency in cluster × 1/number-of-clusters. Same idea, different unit.
- **Pre-training vs fine-tuning.** Pre-training is unsupervised on huge text corpora (masked language modelling). Fine-tuning is supervised on a small labelled dataset for your target task. Sun et al. discusses a middle step — further pre-training on in-domain data — between these two.
- **Catastrophic forgetting vs overfitting.** Catastrophic forgetting is losing pretrained knowledge. Overfitting is memorising the training set. Both are failure modes of fine-tuning, but they are not the same thing.
- **Cluster labelling vs cluster creation.** Creating clusters is the clustering algorithm. Labelling them with human-readable words is a separate step — TF-IDF (or c-TF-IDF) is the standard.

## One-paragraph exam summary

Topic detection covers two modes. **Text categorisation** is supervised: labels are given in advance, you train a classifier, you get control over the topics and high performance but you can't detect new topics and the model is biased toward the training distribution. **Topic modelling** is unsupervised: documents are clustered on shared word associations, and clusters are labelled with distinctive keywords (TF-IDF, or c-TF-IDF in BERTopic). LDA is the classical generative approach — fixed K, two reduced matrices, random initialisation that makes results unstable across runs, plus topic-independence and word-independence assumptions that fail on longer texts. CTM, hierarchical LDA, embedding-based methods, and short-text/dynamic topic models exist to patch each weakness. BERTopic embeds with S-BERT, clusters the embeddings, labels with c-TF-IDF. BERT fine-tuning (Sun et al.) uses three steps — further pre-train, optional multi-task, target fine-tune — and benefits from top-layer outputs, in-domain pre-training, and decreased learning rate to avoid catastrophic forgetting. Choosing a topic model depends on Churchill & Singh's eight factors: dataset size, document length, noise level, noise types, expected setting, downstream tasks, word co-occurrence, data source — not algorithm complexity.
