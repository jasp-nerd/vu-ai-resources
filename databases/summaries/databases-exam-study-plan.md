# 📌 START HERE — Databases (X_401008) Exam Prep

Your complete, prioritized study kit. Built from the **full course chapters** (not just the practice exam), the **exercise sheets + official solutions**, and the **example exam**. The example exam only *samples* the material — the real exam can pull anything from these chapters, so the notes cover everything, but they're **tagged so you spend time where it pays**.

## How to use this kit
1. Read this file fully (5 min) — it's your map and schedule.
2. For each topic: **read the summary** (`0X-*.md`), then **immediately do the matching practice** (`practice/0X-*-practice.md`) **closed-book**, then check against the `--- SOLUTIONS ---`.
3. **Doing > reading.** Don't re-read a topic you got wrong — re-do the *exercise*.
4. Inside each summary, sections are tagged:
   - **[EXAM-CRITICAL]** — almost certainly tested; master it.
   - **[KNOW]** — likely; understand it.
   - **[SKIM]** — context only; read once, don't drill.
5. The real exam is open-website ("we will use the website on the exam"), so memorizing trivia matters less than being able to *execute the procedures fast*. Optimize for speed on the algorithms (closures, BCNF, precedence graphs, NOT EXISTS).

---

## 🎯 The exam at a glance (≈10 points)

| Q | Topic | Points | Your file |
|---|---|---|---|
| 1a | ER diagram | **1.5** | 01 |
| 1b | Relational schema, keys, FKs, NULLs | 0.5 | 01 |
| 2a | Canonical / minimal cover | 0.5 | 05 |
| 2b | Candidate keys | 0.5 | 05 |
| 2c | BCNF + which FDs lost | 0.5 | 06 |
| 2d | 3NF | 0.5 | 06 |
| 3a | SQL "exactly one" (no GROUP BY) | **1.0** | 03 |
| 3b | SQL "for all"/division (no GROUP BY) | **1.0** | 03 |
| 4a | Recoverable & cascadeless definitions | 0.5 | 07 |
| 4b | Conflict-serializable via precedence graph | 0.5 | 07 |
| 5a | Dynamic SQL string concat (discuss) | 0.5 | 08 |
| 5b | ANSI/SPARC levels + ORMs | 0.5 | 08 |

**The three big rocks are SQL (2.0), Conceptual (2.0), Normalization (2.0).** Transactions (1.0) and APIs (1.0) are smaller and mechanical/memorizable.

---

## ⚖️ Priority matrix — where your hours go

Sorted by **points-per-hour** (do top-down if short on time):

| Rank | Topic | Pts | Effort | Why this rank |
|---|---|---|---|---|
| 1 | **APIs** (08) | 1.0 | ~2h | Easiest points. Two short "discuss/name" answers with known wording. **Lock these in early.** |
| 2 | **Transactions** (07) | 1.0 | ~3h | Pure algorithm (precedence graph) + 2 definitions to memorize. High confidence per hour. |
| 3 | **Normalization** (05+06) | 2.0 | ~7h | Mechanical once `X+` closures click. The single skill (closure) powers all 4 sub-questions. |
| 4 | **SQL** (02+03+04) | 2.0 | ~9h | Biggest topic; you have a head start. The exam's 2 points live in **03** (NOT EXISTS / division). |
| 5 | **Conceptual** (01) | 2.0 | ~4h | Highest single question (1.5) but judgement-heavy; hard to "perfect," easy to get most of. |

**Highest-yield single skills to drill until automatic:**
- Attribute closure `{X}+` → unlocks ALL of normalization (keys, canonical, BCNF, 3NF).
- Double `NOT EXISTS` ("for all"/division) + self-correlated `NOT EXISTS` with `<>` ("exactly one") → the 2 SQL exam points.
- Build precedence graph → find cycle → topological sort → the transactions point.
- ER → relational *optimisation* step (merge `..1` relationships into FK + NOT NULL/UNIQUE) → separates "basic" from full marks on Q1b.

---

## 🗓️ The 2–3 day plan

> Order = **easy wins first** (build momentum + bank guaranteed points), **biggest/hardest last** when you're warmed up. Each block = read summary → do practice closed-book → check solutions.

### Day 1 — bank the easy points + normalization (~8h)
| Block | What | File |
|---|---|---|
| 1 (1.5h) | **APIs** — read + drill, memorize 5a/5b skeletons | 08 + practice |
| 2 (3h) | **Transactions** — precedence graph + recoverable/cascadeless wording | 07 + practice |
| 3 (3.5h) | **Normalization pt.1** — FDs, **closures**, candidate keys, minimal cover | 05 + practice |

### Day 2 — finish normalization + most of SQL (~9h)
| Block | What | File |
|---|---|---|
| 4 (3h) | **Normalization pt.2** — BCNF + 3NF + "which FDs lost" | 06 + practice |
| 5 (2h) | **SQL basics & joins** (you know some — go fast, focus self-joins/outer joins) | 02 + practice |
| 6 (4h) | **SQL subqueries** — NOT EXISTS, division, "exactly one" (THE 2 exam points) | 03 + practice |

### Day 3 — conceptual + SQL aggregation + full mock (~8h)
| Block | What | File |
|---|---|---|
| 7 (2h) | **SQL aggregation** — GROUP BY/HAVING + *when the exam wants NOT EXISTS instead* | 04 + practice |
| 8 (4h) | **Conceptual design** — ER + translation; do all practice in the editor | 01 + practice |
| 9 (2h) | **Full mock**: do the real example exam under time (see below), then review weak spots |

### ⏳ Only have ~1 day? (minimum viable path)
Do in this order, stop when time runs out — you'll have banked the most points:
1. APIs (08) — 1.5h → +1.0
2. Transactions (07) — 2h → +1.0
3. SQL subqueries (03) only — 2.5h → +2.0
4. Normalization (05+06), skim then drill the exam set — 3h → +2.0
5. Conceptual (01) — skim summary, do 1 practice — 1h → partial of 2.0

---

## 📝 Final mock exam
The real example exam is at `../ExerciseExam.pdf` (questions) with full solutions in `../X_401008/Extracted_Files/ExerciseExamSolutions.pdf`. **Do the whole thing closed-book in ~2h, then grade yourself.** The two SQL queries and the normalization Q2 set are reproduced (worked) inside files 03, 05, and 06 — but try the PDF cold first.

Other official exercise sheets (more practice, with solutions) live in:
- `../X_401008/Files/Exercises/` (sheets) and `../X_401008/Extracted_Files/` (solutions)

---

## 🧠 Day-before / exam-morning quick review
- **APIs:** 5a = injection + no compile checks + plan caching → *prepared statements fix it*. 5b = **Conceptual / Logical / Physical**; ORMs at **Conceptual** (highest); purpose = data independence. *(Use these exact words — the grader's solution uses non-standard naming; see file 08.)*
- **Transactions:** edge direction = earlier-op → later-op; acyclic ⇔ conflict-serializable; **recoverable** = commit after all you read-from commit; **cascadeless** = only read committed values.
- **Normalization:** in BCNF you **maximize RHS** then split on violations (may lose FDs — *state which*); in 3NF you **synthesize** from minimal cover (loses none). Attributes never on any RHS are in **every** key.
- **SQL:** "all/every/only/no" → `NOT EXISTS`, never GROUP BY. Division = double `NOT EXISTS`. NOT IN breaks on NULL.
- **Conceptual:** write the *design-choices/assumptions* paragraph and the *"constraints the relational model can't enforce"* note — both are explicitly graded and easy to skip.

---

## File index
| File | Topic |
|---|---|
| 01-conceptual-design.md | ER modeling + relational translation + keys/FKs/NULLs |
| 02-sql-basics-joins.md | SELECT/WHERE, joins, self-joins, inner/outer, duplicates |
| 03-sql-subqueries.md | NOT IN/EXISTS, "for all"/division, ALL/ANY/SOME, nested |
| 04-sql-aggregation.md | aggregation, GROUP BY, HAVING, CASE/UNION, ORDER BY |
| 05-normalization-fds-keys.md | FDs, closures, covers, candidate keys, minimal cover |
| 06-normalization-normal-forms.md | 1NF/BCNF/3NF + transformation algorithms |
| 07-transactions.md | schedules, conflicts, serializability, 2PL, recoverability |
| 08-database-apis.md | dynamic SQL, ANSI/SPARC, ORMs, JDBC/cursors |
| practice/ | matching exercises with worked solutions for each |
