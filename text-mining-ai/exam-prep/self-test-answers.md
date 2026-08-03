# XB_0085 Self-Test Reference

All self-test questions, every option presented, and the correct answer. Titles match the Canvas filenames in `Assignments/`. Fill-in-the-blank items list every accepted answer variant; multiple-choice items mark the correct option with **✓**.

---

## Self test — Command line test

### 1. Fill in the Blank
How do you check in which directory you are?
- **Correct answer(s):** `pwd`

### 2. Fill in the Blank
What command do you use to go to your home dir from anywhere in the system?
- **Correct answer(s):** `cd`, `cd ~`, `cd /path/to/my/dir`, `cd ~/`

### 3. Essay
What effect does pressing the 'tab' key have when you are typing in filenames or commands on the command line?
- **Correct answer:** Tab triggers auto-completion of the partially typed filename or command. If the prefix is unique it is completed in full; if multiple matches exist, pressing Tab a second time lists the candidates.

### 4. Fill in the Blank
What command can you use to create a new directory named NEWDIR?
- **Correct answer(s):** `mkdir NEWDIR`

### 5. Fill in the Blank
You want to find the occurrences of "cat" in a text file that may have capitals in them. What command can you use to find occurrences of "cat", "Cat", "cAt" etc in a text file?
- **Correct answer(s):** `grep -i "cat"`

### 6. Fill in the Blank
What command would you use to append the last 6 lines of file 'input' to the already existing file 'output'?
- **Correct answer(s):** `tail -n6 < input >> output`, `tail -n 6 input >> output`, `sed -e :a -e '$q;N;7,$D;ba' < input >> output`, `tail -6 < input >> output`, `tail -6 input >> output`

### 7. Essay
Explain what the difference is between a command option and an argument and give an example of each.
- **Correct answer:** An option (also called a flag) modifies how the command behaves and usually starts with `-` or `--`; an argument is the input the command operates on. Example: in `ls -l /home`, `-l` is the option (long listing format) and `/home` is the argument (the directory to list).

### 8. Fill in the Blank
What command would you use to execute the script run.sh? (HINT: the extension .sh indicates that this is a bash script)
- **Correct answer(s):** `./run.sh`, `sh run.sh`, `bash run.sh`

### 9. Fill in the Blank
What  command would you use to remove all files in the current directory that both start with temp and end in txt? (note that both conditions need to be fulfilled, so a file named temp.pdf should not be deleted)
- **Correct answer(s):** `rm temp*txt`

### 10. Fill in the Blank
What does the Python interpreter prompt look like (this tells you whether you are in the bash shell or in Python)
- **Correct answer(s):** `>>>`
- *Reference if incorrect:* http://www.greenteapress.com/thinkpython/html/thinkpython002.html#toc4

### 11. Fill in the Blank
How would you create a list in Python named 'wine' that contains the elements 'beaujolais', 'rioja' and 'champagne'?
- **Correct answer(s):** `wine = ['beaujolais', 'rioja', 'champagne' ]`, `wine = ['beaujolais', 'rioja', 'champagne']`
- *Reference if incorrect:* http://www.greenteapress.com/thinkpython/html/thinkpython011.html

### 12. Fill in the Blank
In the previous question, you generated a Python list called 'wine' that contains three elements. How do you print the first element of this list?
- **Correct answer(s):** `print(wine[0])`

### 13. Fill in the Blank
How would you create a dictionary 'wineReviews' in Python that contains the following value pairs: beaujolais : 3 rioja : 5 champagne : 2
- **Correct answer(s):** `wineReviews = {'beaujolais': 3, 'rioja' : 5, 'champagne' : 2}`, `wineReviews={'beaujolais':3, 'rioja':5, 'champagne':2}`
- *Reference if incorrect:* http://www.greenteapress.com/thinkpython/html/thinkpython012.html

### 14. Fill in the Blank
In the previous question you created a dictionary called 'wineReviews' that contains review scores for beaujolais, rioja and champagne. How do you print the score for 'rioja' from this dictionary?
- **Correct answer(s):** `print(wineReviews['rioja'])`
- *Reference if incorrect:* http://www.greenteapress.com/thinkpython/html/thinkpython012.html

### 15. Fill in the Blank
What command do you need to use in Python to also load commands from a module named 'nltk'?
- **Correct answer(s):** `import nltk`, `from nltk import *`
- *Reference if incorrect:* http://www.greenteapress.com/thinkpython/html/thinkpython004.html (section 3.3)

### 16. Fill in the Blank
How would you check the type of a variable named 'unknownType' in Python?
- **Correct answer(s):** `type(unknownType)`, `print(type(unknownType))`
- *Reference if incorrect:* http://www.greenteapress.com/thinkpython/html/thinkpython003.html#toc13

### 17. Fill in the Blank
Assume you have created an ordered list of tokens in python from the saying "When all is said and done more is said than done". How would you get python to print ['more', 'said']?

```python
saying = ['After', 'all', 'is', 'said', 'and', 'done', 'more', 'is', 'said', 'than', 'done']
tokens = set(saying)
tokens = sorted(tokens)
```
- **Correct answer(s):** `tokens[-3:-1]`, `tokens[5:7]`, `print(tokens[-3:-1])`, `print(tokens[5:7])`, `print(tokens[5], tokens[7])`

### 18. Fill in the Blank
How do you loop through the list you have created in the previous question and print every item?
- **Correct answer(s):** `for item in wine: print(item)`

### 19. Essay
By default, Python dictionaries are unordered. How would you sort the dictionary wineReviews by value and print the values such that the highest score is printed first? You want the following output:

```
rioja 5
beaujolais 3
champagne 2
```
- **Correct answer:**
```python
for key, value in sorted(wineReviews.items(), key=lambda item: item[1], reverse=True):
    print(key, value)
```

### 20. Multiple answer
How can you get help on using a command? Please select all correct answers.
- **✓** `command --help`
- **✓** Go to Google.com and type in the command
- **✓** `man command`
- **✓** ask a fellow student
- *Note from source:* "Google is your friend"

---

## Self test — Introduction to linguistics

### 1. Multiple choice
What type of phrase is "The Text Mining Course"?
- Adjective Phrase (AdjP)
- Prepositional Phrase (PP)
- **✓ Noun Phrase (NP)**
- Verb Phrase (VP)

### 2. Multiple choice
What is the difference between dependency parsing and constituent parsing?
- There is no difference
- A dependency parser detects hierarchical relations such as noun phrases and verb phrases, a consituency parser detects flat relations between adjectives, nouns and verbs.
- **✓ A dependency parser detects flat relations between adjectives, nouns and verbs, a consituency parser detects hierarchical relations such as noun phrases and verb phrases.**
- A dependency parser detects relations between morphemes, a constituency parser detects relations between parts-of-speech

### 3. Multiple choice
What are chunkers?
- Chunkers provide an efficient way identify compound nouns in languages such as English (where they are not written as one word, unlike Dutch and German), but no further syntactic information
- **✓ Chunkers efficiently identify constituents but do not provide full sentence structure or syntactic dependencies**
- Chunkers provide phrase structure trees efficiently, but they do not capture all syntactic structures
- Chunkers provide the same information as a parser, but are more robust and have a lower precision

### 4. Multiple choice
What is the lexical relation between 'lecture room' and 'university building'?
- homophony
- synonymy
- **✓ meronymy**
- hyponymy

### 5. Multiple choice
Syntactic parsers and chunkers are natural language processing modules used for which of the following?
- Semantics
- **✓ Syntax**
- Pragmatics
- Morphology

### 6. Multiple choice
What is the primary difference between semantics and pragmatics in linguistics?
- Semantics is related to word order, while pragmatics deals with syntax rules
- Semantics focuses on language evolution, while pragmatics is concerned with language in isolation
- Semantics is concerned with sentence structure, while pragmatics is about sentence correctness
- **✓ Semantics deals with the literal meaning of words, while pragmatics focuses on how context influences meaning**

### 7. Multiple choice
Which of the following is an example of a morphological process?
- Using context to determine word meaning
- Applying tone or stress to modify word meaning
- **✓ Adding a prefix to a word to alter its meaning**
- Changing word order to form a question

### 8. Multiple choice
Which of the following processes involve changes to a word's grammatical features, such as tense or number?
- Derivation
- **✓ Inflection**
- Compounding
- All of the above

### 9. Multiple choice
In dependency grammar, what term refers to the relationship between a head word and the words that depend on it within a sentence?
- Coordination
- **✓ Dependency relations**
- Subordination
- Agreement relations

### 10. Multiple choice
Which of the following describes the difference between metaphors and metonymy in pragmatics?
- A metaphor refers to literal meanings, while metonymy involves abstract concepts
- **✓ Metaphors transfer a property from one concept to a different, unrelated concept, while metonymy uses a word to refer to a related concept**
- A metaphor always involves exaggeration, while metonymy involves understatement
- A metaphor substitutes one word for another based on association, while metonymy compares two unrelated things

---

## Self test — Natural Language Processing

### 1. Multiple choice
How do different tokenenisers split hyphenated terms such as 'state-of-the-art'?
- four tokens
- **✓ It depends on the setup of the tokeniser**
- one token
- three tokens

### 2. Multiple choice
What type of approaches were used in early NLP tools?
- Hybrid approaches
- **✓ Rules**
- Deep learning
- Statistical models

### 3. Multiple choice
How many words in the English language can be used to make reference to movements according to WordNet?
- between 300 and 3000
- **✓ more than 3000**
- between 30 and 300
- between 3 and 30

### 4. Multiple choice
Which statement best describes the structure of NLP pipelines?
- NLP pipelines always process text directly without requiring preprocessing steps
- NLP pipelines typically consist of entirely distinct modules for different tasks without any shared components
- **✓ NLP pipelines are likely to share basic processing steps (such as tokenization) while including specific modules for higher-level interpretations**
- NLP pipelines are rigid sequences of modules that cannot be modified or customized

### 5. Multiple choice
Which of the following is an example of language variation rather than ambiguity?
- A sentence that can be interpreted in two ways due to its structure
- The phrase "I saw her duck" referring to either an action or an animal
- **✓ Differences in how British and American English spell the word "color/colour"**
- The word "bank" meaning both a financial institution and the side of a river

### 6. Multiple choice
What is the key difference between inline annotations and stand-off annotations?
- **✓ Inline annotations are inserted directly within the text, while stand-off annotations are stored in a separate file or a different layer**
- Inline annotations are stored in a separate file or a different layer, while stand-off annotations are embedded directly within the text
- Inline annotations require no additional processing, while stand-off annotations require more complex processing to be applied
- Inline annotations are used for image data, while stand-off annotations are used for text data

### 7. Multiple choice
What is the difference between Gold, Silver, and Bronze data?
- Gold data is the data collected through user feedback, Silver data is generated using machine learning algorithms, and Bronze data is the data gathered from surveys
- **✓ Gold data is manually labeled by humans, Silver data is semi-automatically labeled with some human verification, and Bronze data is automatically labeled with minimal or no human intervention**
- Gold data refers to the raw, unprocessed data, Silver data refers to the processed data, and Bronze data refers to aggregated data
- Gold data is data used for training, Silver data is used for validation, and Bronze data is used for testing machine learning models

### 8. Multiple choice
What can be considered as features of a text in Natural Language Processing (NLP)?
- Gold labels
- Number of pages, font style, print quality
- Author's handwriting, page layout, text color
- **✓ Sentence length, punctuation marks, part-of-speech tags**

### 9. Multiple choice
What is the primary goal of feature engineering in Natural Language Processing (NLP)?
- **✓ To transform raw data into features that can be used for machine learning models**
- To improve the quality of raw data by manually cleaning and correcting it
- To enhance the performance of the model by increasing its complexity
- To minimize the amount of data needed for analysis by reducing the data size

### 10. Multiple choice
What is a disadvantage of supervised machine learning in Natural Language Processing (NLP)?
- It is unable to generalize well to unseen data
- **✓ It needs annotated data, which can be expensive and time-consuming to create**
- It requires a large amount of unannotated data for training
- It does not work well with text data

---

## Self test — Sentiment

### 1. Multiple choice
Assume you have 100 movie reviews of which 40 are positive and 60 are negative.

Your classifier classifies 50 reviews as positive and 50 reviews as negative.

The classifier correctly identifies 10 positive and 20 negative reviews. Which of the following statements is correct, considering macro averaging?
- **✓ The recall & precision are both 0.3.**
- The precision and recall are both 0.5
- The precision is 0.3 and the recall is 0.5
- The precision is 0.15 and the recall is 0.3

### 2. Multiple choice
Consider the sentence "These guys are terrible."

What is the opinion target in this sentence?
- terrible
- the speaker or writer of the sentence
- **✓ These guys**
- are

### 3. Multiple choice
In sentiment analysis, which of the following sets consists of typical negation words that can reverse the polarity of an opinion?
- hardly, scarcely, barely, slightly
- always, completely, absolutely, certainly
- **✓ not, never, no, neither**
- good, excellent, fantastic, delightful

### 4. Multiple choice
Who is the opinion holder in the sentence: "Emma believes that the new restaurant is fantastic"?
- Fantastic
- The new restaurant
- **✓ Emma**
- The listener of the sentence

### 5. Multiple choice
What is the role of aspect in Aspect-Based Sentiment Analysis?
- It refers to the emotional tone of the entire sentence
- **✓ It refers to a specific feature or attribute of the product or service being evaluated**
- It refers to the syntactic structure of the sentence
- It is the opinion holder's overall sentiment

### 6. Multiple choice
Which of the following is an example of figurative language?
- **✓ All of the above**
- Metonymy
- Similes
- Metaphors

### 7. Multiple choice
According to Ekman et al. (1976), which of the following are among the six basic human emotions?
- **✓ Happiness, sadness, anger, fear, surprise, disgust**
- None of the above
- Love, jealousy, pride, excitement, boredom, shame
- Gratitude, embarrassment, curiosity, hope, frustration, admiration

### 8. Multiple choice
Which of the following can be used as features in sentiment analysis?
- **✓ All of the above**
- Part-of-speech (POS) tags
- Modal verbs
- Words or n-grams

### 9. Multiple choice
According to Ravi & Ravi (2015), which approach was the most commonly used for sentiment classification?
- Logistic Regression (LR)
- Latent Dirichlet Allocation (LDA)
- Dictionary-based approaches (DBA)
- **✓ Support Vector Machines (SVM)**

### 10. Multiple choice
VADER (Valence Aware Dictionary and sEntiment Reasoner) is specifically attuned to sentiments expressed in which of the following?
- News articles
- Scientific reports
- **✓ Social media**
- All of the above

---

## Self test — Named Entities

### 1. Multiple choice
What is the main reason to express sequential tags using the BIO (or also called IOB) format over only providing the class name?
- **✓ The IOB format can better expresses the boundaries of an entity or chunk**
- all of the above
- The IOB format is easier to interpret for machines
- The IOB format is easier to read

### 2. Multiple choice
What is the effect of metonymy for named entity classification?
- Metonymy is not relevant for detection the type of entity
- Parts of entities are being referred to
- Locations can be ambiguous because they have the same name
- **✓ The same name is used for different types such as locations, people and governments**

### 3. Multiple choice
Why is it important to create balanced evaluation data sets for NLP research?
- When an evaluation data set is not balanced, it is too small to measure the system performance
- Unbalanced evaluation data sets provide too little information for training a supervised NLP application.
- When a dataset is not balanced it doesn't adequately reflect the linguistic phenomenon it purports to represent.
- **✓ When an evaluation data set does not contain a realistic sample of the linguistic phenomenon, it doesn't allow one to measure a system's performance on that phenonemon adequately.**

### 4. Multiple choice
What can be considered a referring expression in Named Entity Recognition and Classification (NERC)?
- A communicative act to identify an entity
- **✓ Common noun phrases, pronouns, and in some cases, verbs, verb phrases, and adjectives (e.g., for events and properties)**
- Only adjectives that describe entities
- Only proper nouns, such as person or organization names

### 5. Multiple choice
What is the key difference between Named Entity Recognition (NER) and Named Entity Classification (NEC)?
- NER assigns entity types such as person, location, or organization, while NEC involves identifying phrases that refer to named entities
- NER deals with proper nouns, while NEC focuses on common nouns
- NER recognizes the context of an entity within a sentence, while NEC focuses on the structure of the entity itself
- **✓ NER involves identifying phrases that refer to named entities, while NEC assigns entity types such as person, location, or organization**

### 6. Multiple choice
Which of the following features can be used in Named Entity Recognition and Classification (NERC)?
- Lookup features
- Word-level features
- Document & corpus features
- **✓ All of the above**

### 7. Multiple choice
Which of the following is an example of ambiguity in Named Entity Recognition (NER)?
- "New York, "NY", and "The Big Apple" referring to the same location
- **✓ "Apple" referring to the organization vs. "apple" as a fruit**
- "Holland" and "The Netherlands" used as metonyms for the same country
- "Paris" as a location vs. "Paris" as a person

### 8. Multiple choice
The representation 'xxxXx' for the word 'spaCy' is an example of which of the following features?
- Character n-gram feature
- **✓ Word shape feature**
- Digit pattern
- Case feature

### 9. Multiple choice
Which of the following typically does not serve as a feature for token-level classification?
- POS tag of the previous word
- Lemma of the next word
- **✓ Length of the current word**
- IOB tag of the previous word

### 10. Multiple choice
Which of the following factors does not impact performance for Named Entity Recognition and Classification (NERC)?
- **✓ Text font size**
- Genre of text
- Amount of training data
- The annotation of the spans

---

## Self test — Text categorisation and Topic modeling

### 1. Multiple choice
What makes topic detection more difficult for longer text compared to short text?
- Longer texts have more variation in words to express topics
- Longer texts such as news have stronger opinions than shorter texts
- Longer texts provide more details than shorter texts about a topic
- **✓ Longer texts such as news may contain different topics which creates ambiguity.**

### 2. Multiple choice
Why is it so difficult to agree on a set of universal topics?
- There is a limited set of topics but there are many different ways to describe them.
- There is too much variation in the keywords that can be extracted from topics.
- **✓ Topics are subjective categories and both the world and our view on the world changes continuously.**
- Topics are based on the keywords that are different from text to text.

### 3. Multiple choice
What is the most important difference between topic modelling and text categorisation?
- Topic modelling is more fine-grained than text categorisation.
- **✓ For text categorisation the topics are given whereas topic modelling does not assume an a priori definition of topics.**
- Text categorisation uses key words and topic modelling uses complete texts.
- Topic modelling is hierarchical and text categorisation is not.

### 4. Multiple choice
What determines the level of granularity when assigning topics to a text?
- The number of topics is always fixed and does not vary
- **✓ Depends on data usage and specific application**
- Topics should be fine-grained to capture all details
- Topics should be coarse-grained to capture only main topics

### 5. Multiple choice
At what unit level can a topic be assigned in topic modeling or classification?
- Sentences
- Complete books
- **✓ All of the above**
- Short texts

### 6. Multiple choice
Which of the following is not a disadvantage of supervised topic classification?
- Manual effort is required to maintain the topics and training data
- New topics that are not in the training data cannot be detected
- **✓ Control over the topics**
- The results can be biased towards the distribution of training data

### 7. Multiple choice
What approach is commonly used to label clusters in topic modeling?
- Using the most frequent words across all clusters as labels for each individual cluster
- Random words from each cluster are chosen as labels
- Domain experts manually assign labels based on the most relevant terms in each cluster
- **✓ Extracting the most distinctive keywords from the clusters using techniques like TF-IDF**

### 8. Multiple choice
Why is random initialization and internal sampling considered a limitation in Latent Dirichlet Allocation (LDA)?
- Random initialization and internal sampling are not considered a limitation in LDA
- **✓ It can lead to unstable topic modeling results**
- It leads to overfitting, making the model less generalizable
- It makes LDA computationally inefficient

### 9. Multiple choice
What is catastrophic forgetting during fine-tuning?
- The ability of a model to learn multiple tasks during fine-tuning
- **✓ The tendency of a model to forget information learned during pre-training when exposed to new data during fine-tuning**
- The process of enhancing model performance by learning new tasks during fine-tuning
- The ability of a model to remain effective with little data available for fine-tuning

### 10. Multiple choice
Which of the following factors is not mentioned as one to be considered when choosing a topic model, according to Churchill & Singh (2021)?
- Dataset size
- **✓ The complexity of the algorithm**
- Noise level
- Document length
