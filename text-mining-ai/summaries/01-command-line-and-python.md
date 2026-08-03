# 01 — Command line & Python basics

**Source slides:** Unixforpoets.pdf (25 pp.) is the only lecture source. Basic shell navigation and all Python syntax come from Lab 1 + the Think Python textbook.
**Quiz questions drawn from this material:** Command line test (20 Qs in quiz_answers.md)

A note on scope: only the Unix material has a real "slide" source (the Church chapter). Every Python question (Q1.10–Q1.19) references the Think Python textbook directly in the quiz answer key. Q1.1–Q1.4 (`pwd`, `cd`, tab completion, `mkdir`) are not in Unix for Poets either — they're presumed-known shell basics. So treat this summary as "two halves": Unix-for-Poets atoms, then Lab-1/Think-Python atoms.

---

## Cheat sheet (cover the right column, recall the left)

| Concept / question | Answer | Source |
|--------------------|--------|--------|
| Print current directory | `pwd` | shell basics (Q1.1) |
| Go to home directory | `cd`, `cd ~`, `cd ~/` | shell basics (Q1.2) |
| Effect of Tab key | One tab = autocomplete; two tabs = list candidates | shell basics (Q1.3) |
| Make a new directory `NEWDIR` | `mkdir NEWDIR` | shell basics (Q1.4) |
| Find "cat", "Cat", "cAt" in a file | `grep -i "cat"` | Unixforpoets p. 10 (Q1.5) |
| Append last 6 lines of `input` to `output` | `tail -n 6 input >> output` | Unixforpoets p. 7 (Q1.6) |
| Difference: option vs argument | option (`-l`) modifies behaviour; argument (`/home`) is what the command acts on | shell basics (Q1.7) |
| Run a bash script `run.sh` | `./run.sh`, `sh run.sh`, `bash run.sh` | Unixforpoets p. 8 (Q1.8) |
| Remove files starting with `temp` and ending in `txt` | `rm temp*txt` | Unixforpoets p. 8 (Q1.9) |
| Python interpreter prompt | `>>>` | Think Python (Q1.10) |
| Create list `wine` with three strings | `wine = ['beaujolais', 'rioja', 'champagne']` | Think Python ch. 10 (Q1.11) |
| Print first element of `wine` | `print(wine[0])` | Think Python (Q1.12) |
| Create dict `wineReviews` | `wineReviews = {'beaujolais': 3, 'rioja': 5, 'champagne': 2}` | Think Python ch. 11 (Q1.13) |
| Print rioja's review | `print(wineReviews['rioja'])` | Think Python (Q1.14) |
| Import the `nltk` module | `import nltk` or `from nltk import *` | Think Python §3.3 (Q1.15) |
| Check type of a variable | `type(unknownType)` or `print(type(unknownType))` | Think Python (Q1.16) |
| Slice last-two-but-one from sorted list | `tokens[-3:-1]` or `tokens[5:7]` | Think Python (Q1.17) |
| Loop and print every list item | `for item in wine: print(item)` | Think Python (Q1.18) |
| Sort dict by value, descending | `sorted(wineReviews.items(), key=lambda item: item[1], reverse=True)` | Think Python (Q1.19) |
| Get help on a command | `man cmd`, `cmd --help`, Google, ask a classmate | Unixforpoets p. 5 (Q1.20) |
| Pipe symbol meaning | `|` connects stdout of one command to stdin of the next | Unixforpoets p. 3 |
| `<` symbol | Read input from a file (replace stdin) | Unixforpoets p. 3 |
| `>` symbol | Redirect stdout to a file (overwrite) | Unixforpoets p. 3 |
| `>>` symbol | Redirect stdout to a file (append) | shell basics |
| `tr -sc '[A-Z][a-z]' '[\012*]'` | Tokenise: replace any run of non-letters with a newline | Unixforpoets p. 2, 5 |
| `tr -c` | Complement the source set (translate everything NOT in it) | Unixforpoets p. 5 |
| `tr -s` | Squeeze repeats of the translated char | Unixforpoets p. 5 |
| `sort -n` / `-nr` / `-d` / `-f` / `-u` | numeric / reverse-numeric / dictionary / fold-case / unique | Unixforpoets p. 6 |
| `uniq -c` | Collapse adjacent duplicate lines, prefix count (sort first!) | Unixforpoets p. 2 |
| `sed 5q` | Quit after the 5th line (i.e. print first 5) | Unixforpoets p. 3 |
| `sed 's/light/dark/g'` | Substitute all "light" with "dark" | Unixforpoets p. 11 |
| `grep -v PATTERN` | Print lines that do NOT match | Unixforpoets p. 9 |
| `grep -c PATTERN` | Count matching lines (don't print them) | Unixforpoets p. 10, 11 |
| `grep -i PATTERN` | Case-insensitive match | Unixforpoets p. 10 |
| `grep '^con'` / `grep 'ing$'` | Anchored to start / end of line | Unixforpoets p. 9 |
| `tail +2 file` | All lines from line 2 onward (drop first line) | Unixforpoets p. 7 |
| `paste file1 file2` | Glue files side-by-side, tab-separated | Unixforpoets p. 7 |
| `rev` | Reverse each line character-wise | Unixforpoets p. 6 |
| `awk '{print $1}'` | Print first whitespace-separated field | Unixforpoets p. 12 |
| `awk '$1 > 300'` | Print lines whose first field exceeds 300 | Unixforpoets p. 13 |
| `wc -l` | Line count | Unixforpoets p. 11 |
| Negative index `tokens[-1]` | Last element of the list | Think Python |
| Half-open slice `tokens[5:7]` | Indices 5 and 6 (length = 2) | Think Python |

---

## Part A — Shell & Unix for Poets

### A1. Navigation & files

These are the questions the syllabus assumes you already know — none of them are in the Unix-for-Poets chapter itself (which jumps straight into text-processing pipelines).

- **`pwd`** — "print working directory." Tells you where you are in the filesystem. Q1.1.
- **`cd`** — change directory. With no argument, or `cd ~`, or `cd ~/`, it goes home. With a path (`cd /Users/jasp/School`) it goes there. Q1.2.
- **`ls`** — list directory contents. `ls -l` is the long format (permissions, owner, size, date). `ls /home` lists a specific directory.
- **`mkdir NEWDIR`** — create a directory. Q1.4.
- **`rm`** — remove. Unix-for-Poets p. 8 warns: "rm is basically the same as 'del' in DOS, but be careful! Don't expect to be asked for confirmation." There's no Recycle Bin.
- **Wildcards.** `*` matches any string. So `rm temp*txt` deletes every file whose name starts with `temp` and ends with `txt`. That matches `temp.txt`, `temp_2024.txt`, `tempfoo.txt`. It does NOT match `temp.pdf` (wrong ending) or `mytemp.txt` (wrong start). This is exactly what Q1.9 tests.
- **Tab completion.** Type a prefix, press Tab. If it's unambiguous, the shell fills in the rest. If ambiguous, one Tab does nothing visible; pressing Tab a second time lists the candidates. Q1.3.

### A2. Redirection & pipes

From Unixforpoets p. 3:

- **`<`** — read stdin from a file. `sort < genesis` is the same data as `sort genesis` for most commands, but `<` is the explicit redirection operator.
- **`>`** — write stdout to a file (overwrites). `uniq -c > genesis.hist` creates or replaces `genesis.hist`.
- **`>>`** — write stdout to a file, **appending** (preserves existing content). This is the operator Q1.6 hinges on: "append the last 6 lines of `input` to the already existing file `output`."
- **`|`** — pipe stdout of the left command into stdin of the right. Pipelines are the whole point of Unix-for-Poets: small tools chained together do big work.

By default, stdin is the keyboard and stdout is the terminal window (p. 3).

**The `tail` / `head` quirks.** Unix-for-Poets p. 7 introduces `tail +2 genesis.words` — that's "from line 2 onwards", i.e. drop the first line. Note the leading `+`, not `-`. The minus form `tail -6 file` (or `tail -n 6 file`) prints the **last** 6 lines. All of these are accepted on Q1.6:

```bash
tail -n 6 input >> output    # arg form
tail -n6 < input >> output   # arg form with input redirect
tail -6 input >> output      # legacy short form
tail -6 < input >> output    # legacy short form with input redirect
```

There's even a sed one-liner in the answer key (`sed -e :a -e '$q;N;7,$D;ba'`) — you do not need to memorise that; it's there as proof there's more than one way.

### A3. Text-processing pipeline (Unix for Poets)

The whole chapter is built around one running example: count words in Genesis. The canonical three-line program from p. 2:

```bash
tr -sc '[A-Z][a-z]' '[\012*]' < genesis |
sort |
uniq -c > genesis.hist
```

Read it as: tokenise (one word per line) → sort → collapse runs and prepend a count.

**`tr` — translate characters.** p. 5.
- `tr '[a-z]' '[A-Z]'` lowercases-to-uppercase, character by character.
- `tr -c SET REPL` **complements** the source set, so `tr -c '[a-zA-Z]' '[\012*]'` replaces every non-letter with a newline (`\012` octal = newline).
- `tr -s SET REPL` **squeezes** runs of the replaced char, so you don't get fifty blank lines in a row.
- The Unix-for-Poets tokeniser combines both: `tr -sc '[A-Z][a-z]' '[\012*]'`.

**`sort` — sort lines.** p. 6.
- `sort -d` dictionary order (letters/digits/spaces only)
- `sort -f` fold case (treat upper/lower as same)
- `sort -n` numeric
- `sort -nr` numeric, reversed (highest first — used after `uniq -c` to get a frequency list)
- `sort -u` unique (dedupe at the same time)
- `sort +1` sort by field 1 (zero-indexed)

**`uniq -c` — count adjacent duplicates.** p. 2. Critical detail: `uniq` only collapses *adjacent* lines, so you must `sort` first. The output is `count word`.

**`grep` — pattern matcher.** p. 8–11.
- `grep 'the land of' genesis` — print lines containing the literal string
- `grep -i '[aeiou]'` — case-insensitive (Q1.5 is this exact flag)
- `grep -v PATTERN` — invert: print lines that do NOT match
- `grep -c PATTERN` — count matching lines (don't print them)
- `grep '^con'` — lines starting with "con" (anchor `^`)
- `grep 'ing$'` — lines ending with "ing" (anchor `$`)
- `grep '[^aeiou]'` — inside brackets, `^` *negates*: any char that is not a vowel
- `grep -vi '[aeiou]'` from p. 22 finds words with no vowels in Genesis (My, Thy, by, cry, dry, myrrh, …).

**`sed` — stream editor.** p. 11.
- `sed 5q` quits after the 5th line — equivalent to `head -5`.
- `sed 's/light/dark/g'` substitutes all "light" with "dark" on every line (the trailing `g` = global within a line).
- `sed '/light/q'` quits at the first line matching the regex.

**`awk` — field-oriented mini-language.** p. 12–17.
- `awk '{print $1}'` prints field 1, `$2` field 2, `$NF` last field, `$0` the whole line.
- `awk '$1 > 300'` filters: print lines where field 1 exceeds 300. The default action when you omit `{...}` is `{print $0}`.
- Predicates from p. 13: `>`, `<`, `>=`, `<=`, `==`, `!=`, `&&`, `||`, `!`, `~` (regex match), `!~` (regex mismatch).

**`paste` and `rev`.** p. 6–7.
- `paste a b` glues two files side-by-side with a tab between them. Used in the bigram example: paste `genesis.words` with `genesis.nextwords` (which is `tail +2 genesis.words`) and you get pairs of consecutive words on each line. Sort + `uniq -c` and you've counted bigrams.
- `rev` reverses each line. Used for the "rhyming order" exercise (p. 6, p. 21): `sort | uniq -c | rev | sort | rev`. You sort words spelled backwards so suffix-rhyming words end up adjacent.

**Canonical examples to recognise:**

1. *Word frequency in Genesis* (p. 2): `tr | sort | uniq -c`.
2. *Top-5 bigrams* (p. 7): `tr` → `genesis.words`, `tail +2` → `genesis.nextwords`, `paste` → `sort | uniq -c | sort -nr | sed 5q`.
3. *Lines containing "the land of"* (p. 8–9): `grep 'the land of' genesis`.
4. *Words with no vowels (hapax-like quirk)* (p. 22): `tr -sc '[A-Z][a-z]' '[\012*]' < genesis | grep -vi '[aeiou]' | sort | uniq -c`.

### A4. Running scripts

Unix-for-Poets p. 8 introduces `sh trigram < genesis > genesis.bigram`, i.e. invoke a shell script by passing it to `sh`. Three equivalent ways to run `run.sh` (Q1.8):

- `./run.sh` — execute it as a program. Requires execute permission (`chmod +x run.sh`). The leading `./` is needed because the current directory is normally not on `$PATH` — without it, the shell wouldn't find `run.sh`.
- `sh run.sh` — explicitly hand the file to `sh`.
- `bash run.sh` — same idea but using bash specifically.

The shebang line (`#!/usr/bin/env bash` or `#!/bin/sh` as the first line of the script) tells the kernel which interpreter to use when you do `./run.sh`. Not directly tested, but worth knowing why the three forms behave differently.

### A5. Getting help

Q1.20 is a multiple-answer that wants every box ticked. All of these count as "getting help":

- `man cmd` — the manual page (Unix-for-Poets references `man tr`, p. 5; `man comm`, p. 14; `man join`, p. 18)
- `cmd --help` — short usage summary built into most modern tools
- Google
- ask a classmate

The Church chapter itself says (p. 1): "when all else fails consult the documentation. (But hopefully, that shouldn't be necessary too often, since we all know how boring the documentation can be.)" The quiz cites this as "Google is your friend."

### A6. Option vs argument

Q1.7 essay. Definition:
- An **option** (also called a flag) modifies the behaviour of the command; usually starts with `-` (short) or `--` (long).
- An **argument** is the data the command operates on — typically a filename, a directory, or a string.

Canonical example: `ls -l /home`
- `ls` — command
- `-l` — option (long-listing format)
- `/home` — argument (the directory to list)

You can have multiple of each, e.g. `grep -i -c 'cat' genesis exodus` (two options, three arguments).

---

## Part B — Python basics (from Lab 1 + Think Python)

### B1. The REPL and modules

The Python prompt is `>>>` (Q1.10). That's how you know whether you're in bash (`$` or `%`) or in Python (`>>>`). Inside a Jupyter notebook cell you don't see the prompt at all, but `type()` and `print()` behave the same way.

Importing a module (Q1.15):
```python
import nltk           # then call nltk.word_tokenize(...)
from nltk import *    # pulls every public name into the current namespace
```

Both are accepted on the quiz. `import nltk` is the form Lab 1 uses; `from nltk import *` is discouraged in real code because it pollutes the namespace, but the textbook mentions it and the quiz key accepts it.

Checking the type of something (Q1.16):
```python
type(unknownType)            # interactive: prints in the REPL
print(type(unknownType))     # explicit print, works in scripts too
```

### B2. Lists

Create a list of strings (Q1.11):
```python
wine = ['beaujolais', 'rioja', 'champagne']
```

The quiz accepts both `'beaujolais', 'rioja', 'champagne' ]` (extra space) and the tight `]` — whitespace is irrelevant.

Indexing (Q1.12):
```python
print(wine[0])     # 'beaujolais'  — Python is 0-indexed
print(wine[-1])    # 'champagne'   — negative indices count from the end
```

**Slicing (Q1.17).** The list is built like this:
```python
saying = ['After', 'all', 'is', 'said', 'and', 'done', 'more', 'is', 'said', 'than', 'done']
tokens = set(saying)         # remove duplicates (becomes a set)
tokens = sorted(tokens)      # convert to sorted list
# tokens == ['After', 'all', 'and', 'done', 'is', 'more', 'said', 'than']
```

After the sort, indices look like this:

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|---|
| 'After' | 'all' | 'and' | 'done' | 'is' | 'more' | 'said' | 'than' |

The target `['more', 'said']` is at positions 5 and 6 (length-2 slice). Every accepted answer pulls those two elements:

- `tokens[5:7]` — half-open: indices 5 and 6
- `tokens[-3:-1]` — same two, counted from the right (`-3 = 'more'`, `-2 = 'said'`, slice excludes `-1 = 'than'`)
- `print(tokens[5], tokens[7])` — note the answer key includes this oddity. It works because the list is length 8 (`tokens[7] = 'than'`)… actually re-checking the key: it accepts `tokens[5], tokens[7]`, which would print `'more' 'than'`. That looks like a typo in the answer key (should presumably be `tokens[5], tokens[6]`). Memorise `tokens[5:7]` and `tokens[-3:-1]` — those are the safe answers.

Useful list/set helpers from the same question: `set(...)` dedupes, `sorted(...)` returns a new sorted list.

### B3. Dictionaries

Create (Q1.13):
```python
wineReviews = {'beaujolais': 3, 'rioja': 5, 'champagne': 2}
```

Access by key (Q1.14):
```python
print(wineReviews['rioja'])   # 5
```

**Sorting a dict by value, descending (Q1.19 — the only essay-length Python question):**
```python
for key, value in sorted(wineReviews.items(), key=lambda item: item[1], reverse=True):
    print(key, value)
```

Things to unpack here:
- `wineReviews.items()` gives `dict_items([('beaujolais', 3), ('rioja', 5), ('champagne', 2)])` — a sequence of `(key, value)` tuples.
- `key=lambda item: item[1]` tells `sorted` to compare by the second element of each tuple (the value).
- `reverse=True` flips ascending to descending.
- The `for key, value in ...` form unpacks the tuple in the loop header.

Expected output:
```
rioja 5
beaujolais 3
champagne 2
```

### B4. Loops

The simplest Python loop (Q1.18):
```python
for item in wine:
    print(item)
```

The quiz accepts the one-line form `for item in wine: print(item)`. Both forms are identical in behaviour.

---

## Likely exam traps

- **`>` vs `>>`.** Q1.6 is explicitly testing append. If you write `tail -6 input > output`, you've wiped `output` and replaced it with just six lines. Read the verb in the prompt — "append" → `>>`.
- **`tail` arg forms.** All of `tail -n 6 input`, `tail -n6 input`, `tail -6 input`, and the same with `< input` instead of `input` are accepted. Only the option form differs syntactically — the data is the same.
- **`rm temp*txt`.** The wildcard `*` matches any string (including the empty one). So `temp.txt` matches (`*` = `.`), `tempfoo.txt` matches (`*` = `foo.`), but `temp.pdf` doesn't (wrong suffix). Don't write `rm temp*` — that would delete `temp.pdf` too.
- **Tab completion.** One tab completes if unambiguous; two tabs lists candidates. Don't say "tab autocompletes" without mentioning the disambiguation list — the essay Q1.3 expects both.
- **Python slicing is half-open on the right.** `tokens[5:7]` includes 5 and 6, excludes 7. `tokens[-3:-1]` includes -3 and -2, excludes -1.
- **`uniq` without `sort` first.** `uniq -c` only collapses *adjacent* duplicates. Forgetting the `sort` step is a classic Unix-for-Poets trap.
- **`grep` anchors.** `^` outside brackets = start of line. `^` inside brackets = negation. So `grep '[^aeiou]'` finds lines with a non-vowel; `grep '^[aeiou]'` finds lines starting with a vowel. Confusing the two costs points.
- **Option vs argument.** Don't say "options start with a dash" without giving a concrete example — the essay expects `ls -l /home` or similar.
- **Python `import`.** Both `import nltk` and `from nltk import *` are accepted; `import nltk.word_tokenize` is wrong (that's not a module).

---

## Self-quiz (cover the answers — recall first, then check)

**Q1.** What does `tail -n 6 file >> output` do that `tail -n 6 file > output` does not?
<details><summary>Answer</summary>`>>` appends to `output`, preserving everything already in it. `>` overwrites `output`, discarding its previous contents. Both write the last 6 lines of `file`.</details>

**Q2.** You want to delete every file in the current directory whose name starts with `log_` and ends with `.txt`, but keep `log_2024.csv`. Which of the following commands does this correctly?
(a) `rm log_*.*`
(b) `rm *log_*txt*`
(c) `rm log_*`
(d) `rm log_*txt`
<details><summary>Answer</summary>(d). (c) also deletes the CSV. (b) matches files containing `log_…txt` anywhere in the name, too broad. (a) deletes the CSV too.</details>

**Q3.** In `grep -i 'cat' file.txt`, which is the option and which is the argument?
<details><summary>Answer</summary>`-i` is the option (case-insensitive flag). `'cat'` and `file.txt` are both arguments (the pattern, then the file).</details>

**Q4.** What does pressing Tab twice in a row do at the shell prompt when your typed prefix is ambiguous?
<details><summary>Answer</summary>Lists the candidate completions. (A single tab on an ambiguous prefix does nothing visible.)</details>

**Q5.** Which of the following is NOT a valid way to run a script called `pipeline.sh`?
(a) `bash pipeline.sh`
(b) `sh pipeline.sh`
(c) `pipeline.sh`
(d) `./pipeline.sh`
<details><summary>Answer</summary>(c). Without `./`, the shell looks for `pipeline.sh` in `$PATH`, and the current directory isn't normally on `$PATH`. (a)/(b)/(d) all work.</details>

**Q6.** You're in Python. You have `wineReviews = {'rioja': 5, 'beaujolais': 3, 'champagne': 2}`. What is the output of:
```python
for k, v in sorted(wineReviews.items(), key=lambda x: x[1]):
    print(k, v)
```
<details><summary>Answer</summary>
```
champagne 2
beaujolais 3
rioja 5
```
Ascending by value (no `reverse=True`).</details>

**Q7.** Given `tokens = ['A', 'After', 'all', 'and', 'done', 'is', 'more', 'said', 'than']`, what does `tokens[-3:-1]` evaluate to?
<details><summary>Answer</summary>`['more', 'said']`. `-3` = 'more', `-2` = 'said', `-1` = 'than' is excluded by the half-open right end.</details>

**Q8.** Which of these is NOT a way to get help on the `tr` command?
(a) `tr --help` in your shell
(b) Search "tr command unix" on Google
(c) `man tr` in your shell
(d) `help tr` in a Python REPL
<details><summary>Answer</summary>(d). `help` in Python is for Python objects, not shell commands. Everything else is fair game per Q1.20.</details>

**Q9.** Write a Python one-liner that creates a dictionary mapping each item of `wine = ['beaujolais', 'rioja', 'champagne']` to its index.
<details><summary>Answer</summary>`{w: i for i, w in enumerate(wine)}`. (Not directly tested, but exercises the same dict-comprehension muscle as Q1.13/Q1.19.)</details>

**Q10.** What's the output of:
```bash
echo "hello world" | rev | rev
```
<details><summary>Answer</summary>`hello world`. Two `rev`s cancel out — see Unixforpoets p. 6.</details>

**Q11.** You write `tail -6 file > output` instead of `tail -6 file >> output` when the prompt said "append." What was wrong?
<details><summary>Answer</summary>`>` overwrites `output`, deleting whatever was there before. "Append" requires `>>`.</details>

**Q12.** Which of the following is NOT equivalent to the others?
(a) `nltk.import()` (then `nltk.word_tokenize(...)`)
(b) `from nltk import word_tokenize` (then `word_tokenize(...)`)
(c) `from nltk import *` (then `word_tokenize(...)`)
(d) `import nltk` (then `nltk.word_tokenize(...)`)
<details><summary>Answer</summary>(a). `nltk.import()` is not Python syntax. (b)–(d) all give you access to `word_tokenize` one way or another; the quiz accepts (c) and (d) verbatim.</details>

---

## What's in the quiz but NOT in any slide

Be honest with yourself: most of this quiz is presumed-knowledge, not lecture material.

**Unix-for-Poets slides actually cover:**
- Q1.5 (`grep -i`) — p. 10
- Q1.6 (`tail -n 6 ... >> output`) — p. 7 for `tail`, p. 3 for `<` / `>`, append (`>>`) is shell-basics
- Q1.8 (running shell scripts) — p. 8
- Q1.9 (`rm temp*txt`) — `rm` mentioned p. 8, wildcards are shell-basics
- Q1.20 (`man cmd`) — p. 5

**Not in any slide (shell-basics presumed-knowledge):**
- Q1.1 `pwd`
- Q1.2 `cd`
- Q1.3 Tab completion
- Q1.4 `mkdir`
- Q1.7 option vs argument (mentioned implicitly throughout Unix-for-Poets but never defined)

**Not in any slide — from Think Python textbook + Lab 1 notebooks:**
- Q1.10 the `>>>` prompt — Think Python §2 (cited in the quiz answer key)
- Q1.11 list literal syntax — Think Python ch. 10
- Q1.12 list indexing
- Q1.13 dict literal syntax — Think Python ch. 11
- Q1.14 dict access
- Q1.15 `import nltk` — Think Python §3.3
- Q1.16 `type(...)` — Think Python §2
- Q1.17 list slicing
- Q1.18 `for ... in ...: print(...)`
- Q1.19 sorting a dict by value with `sorted(..., key=lambda)`

The course relies on Lab 1's three intro notebooks (`Lab1.1-introduction.ipynb`, `Lab1.2-introduction-to-NLTK.ipynb`, `Lab1.3-introduction-to-spaCy.ipynb`) to bring everyone up to a baseline Python level, and the quiz tests that baseline directly against Think Python references rather than course-specific slides. If the exam reuses this material, the testable atoms are the literal syntax patterns above — practise them by typing them once into a notebook cell.
