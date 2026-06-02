# 00 — Exam overview & study plan

## Logistics (from Canvas: "Final exam May 27")

| Item | Detail |
|------|--------|
| Date | **May 27 2026, 08:30 start** — be on time |
| Location | **Emergohal Amstelveen**, Langs de Akker 3, 1186DA — off campus |
| Travel | ~30 min by bike from VU |
| Format | Digital, **TestVision**, **multiple choice**, monitored by invigilators |
| Weight | **60% of final grade** (project poster = 40%) |
| Resit | **July 3 2026 23:59** if needed |
| Pass rule | Each component ≥ 5, average ≥ 5.5 (syllabus §Grading) |

## What is examined

Quoting the syllabus directly:

> "The multiple choice exam will be based on **the literature and the lecture slides**."

> "With each lecture, a few self-test questions are available through Canvas as a quiz. **These questions are similar to the ones you can expect at the exam.**"

> "There will **NOT (!!!!)** be a separate practice exam in addition to the quizzes" — use the six quizzes as your exam-style practice.

## What is NOT examined (explicit carve-outs)

These appear in the Canvas module pages and override the general syllabus:

- **Vayansky & Kumar 2020** (topic modeling review) — "Mathematical background … **NOT FOR EXAM**" (Week 6 page)
- **Churchill & Singh 2021 §5** — "You can skip section 5" (Week 6 page)
- **SVM variant differences** — "You do not need to understand the different versions of SVM" (Week 6 page, applies to Saigal & Khanna 2020)

Everything else from the syllabus literature list is fair game.

## Scope at a glance (six topic blocks)

| Block | Lecture(s) | Companion literature |
|-------|-----------|-----------------------|
| Command line + Python | Lab 1 notebook, *Unix for Poets* (Church), Think Python intro chapters | — |
| Linguistics | Lecture 2 | Kracht *Introduction to Linguistics* (phonetics, morphology, syntax, semantics); *Essentials of Linguistics* Ch 8 (pragmatics) |
| NLP & ML | Lecture 3 part 1 + part 2 | Maynard ch 2; Jurafsky ch 4 (Naive Bayes / sentiment classification), ch 5 (embeddings — implied by ch 6 vector semantics in the week-3 page), ch 6 (vector semantics); NLTK ch 6 (learning to classify), ch 8 (sentence structure); Wolf et al. (transformers); Church 2021 (fine-tuning) |
| Sentiment | Lecture 4 | Maynard ch 7; Jurafsky ch 22 (sentiment lexicons) |
| Named entities | Lecture 5a | Maynard ch 3; Jurafsky ch 17 (sequence labeling for POS and NER); NLTK ch 7 §1, 2, 5, 6; Yadav & Bethard 2019 (NER deep-learning survey) |
| Text categorisation & topic modeling | Lecture 6 | Saigal & Khanna 2020 (SVM — high-level only); Sun et al. 2019 (fine-tune BERT); Churchill & Singh 2021 (skip §5) |

## MCQ exam strategy (general, not topic-specific)

1. **Read the stem first, predict the answer, then look at the options.** Reduces the influence of distractor wording on your reasoning.
2. **Eliminate two clearly wrong options first**, then choose between the remaining two — this is what the quizzes train you to do.
3. **Watch for "All of the above" / "None of the above"** — both appear in the official quizzes (e.g. Sentiment Q6 figurative language; NER Q6 features). They are usually correct *if* every individual option is plausible.
4. **Negative-phrased stems** ("which is NOT", "which does NOT") appear in the quizzes too (e.g. Topic Q6, Q10; NER Q9, Q10). Read them twice — the trap is answering the positive question.
5. **Distractors are usually built from the same lecture's vocabulary** — e.g. confusing dependency vs constituency parsing, NER vs NEC, inline vs stand-off annotations, inflection vs derivation, gold vs silver vs bronze data. If two options sound like they could both be true, identify the precise definition difference.
6. **Numerical / definition options** (Ekman's 6 emotions, ">3000 movement words", "Ravi & Ravi 2015 — SVM") are pure recall. Make flashcards for these and drill them.

## Recommended cadence (cognitive-science basis)

The most evidence-based combo for an MCQ exam in this time-frame:

- **Active recall**: each summary ends with a self-quiz. Don't read the answer until you have committed to one.
- **Spaced retrieval** with shrinking intervals: redo each self-quiz again 24 h after first attempt, then 48 h, then on exam morning.
- **Interleaving**: on day 4, shuffle questions across all six topic blocks rather than re-reading one block at a time. This is how the real exam will present material.

## Things to bring / check before exam day

- Student ID
- Charged laptop (TestVision is browser-based) — check Canvas the night before in case of last-minute updates
- Travel time buffer (Amstelveen, not VU; allow ~45 min total)
- Water + watch — TestVision usually has a built-in timer but a wristwatch is allowed
