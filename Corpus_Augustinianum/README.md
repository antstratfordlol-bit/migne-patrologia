# Aug corpus MD — Augustine in Latin, 281 files

**What this is:** the Latin works of Augustine as Markdown, one file per work,
converted 2026-09-04. **66 MB, 281 files.**

**Filenames carry the attribution, so the folder sorts into three blocks:**

| Prefix | Files | Meaning |
|---|---:|---|
| **`Aug - `** | 203 | genuine Augustine |
| **`Ps-Aug - `** | 45 | pseudo-Augustine — transmitted under his name, *auctor incertus*. **Do not cite as Augustine.** |
| **`Other - `** | 33 | a different author entirely (Prosper, Orosius, Possidius, Eugippius, Petrarch…), printed in Migne's Augustinian section because the work concerns him or travelled with his corpus |

` [CSEL]` is appended where the source is the critical edition. Each file also
carries `attribution: genuine | pseudo | other` in its frontmatter, and the
non-genuine ones open with an explicit warning banner.

**What it is for:** machine search across the whole Augustinian corpus. 

> ## Layer 1 — find here, cite elsewhere
>
> **No page or column numbers exist anywhere in this material.** Cite by the work's
> own divisions (book, chapter, section), then verify against the printed edition.
> Nothing here is citable by page.
>
> ⚠️ **And read §3 before quoting from a CSEL file** — the critical apparatus is
> mixed into the running text, and a careless copy will splice editorial matter into
> Augustine's words.

---

## 1. Where it came from

| | |
|---|---|
| **Dataset** | [CatholicCorpus/catholiccorpus-text](https://huggingface.co/datasets/CatholicCorpus/catholiccorpus-text) (Hugging Face) |
| **Sub-tree** | `02_corpus_corporum/Patrologia Latina (Migne)` — the Augustine slice, 281 files |
| **Upstream** | [Corpus Corporum](https://mlat.uzh.ch), Universität Zürich — TEI-derived, **no OCR at any stage** |
| **Raw copy kept** | `_archive/catholiccorpus-raw/02_corpus_corporum/Patrologia Latina (Migne)/` (+ a `_PROVENANCE` note) |
| **Licence** | Public domain |
| **Retrieved / converted** | 2026-09-04 |

## 2. What is here

| | Files | Edition |
|---|---:|---|
| **CSEL** | 63 | Corpus Scriptorum Ecclesiasticorum Latinorum, Österreichische Akademie — **the critical edition** |
| **Migne** | 218 | Patrologia Latina |
| *of which genuine Augustine* | 203 | see the prefix table above |

⚠️ **Attribution needed a second pass.** Some upstream filenames are truncated at
80 characters, which cuts the `(Author)` field off entirely — so a test that read the
filename could not see the author at all. Five files were misclassified on the first
run and corrected by title: *De peccatorum meritis* [CSEL] and *Excerpta ex Augustini
de natura et gratia* are **genuine Augustine**; the *Indiculus* (Possidius), the
*Prologus in abbreviationem* (Eugippius) and the *Rescriptum beati Gregorii* (Gregory I)
are **not**. If you extend this set, do not trust a truncated filename for attribution.

**27 works exist in both recensions.** Where both are present the CSEL is the better
text but carries the apparatus problem; the Migne is cleaner to read but is the older
edition. Both are kept so you can choose.

**In CSEL:** *De civitate Dei* · *Confessiones* · *De Genesi ad litteram* ·
*Epistulae* (three volumes) · *Quaestiones in Heptateuchum* · *Locutiones in
Heptateuchum* · *De consensu evangelistarum* · *Retractationes* · *De Baptismo* ·
*Contra Cresconium* · *Contra Litteras Petiliani* · *De peccatorum meritis* ·
*Contra duas epistulas Pelagianorum* · *De natura et origine animae* ·
*De spiritu et littera* · *De ordine* · *De beata vita* · *Contra Academicos*, and more.

**Only in Migne** (never edited in CSEL): *De Trinitate* · *Enarrationes in Psalmos* ·
*In Ioannis evangelium tractatus CXXIV* · the *Sermones* · *Contra Faustum Manichaeum* ·
*Opus imperfectum contra Iulianum*.

## 3. ⚠️ The CSEL apparatus problem

**The CSEL files interleave the editors' critical apparatus into the running prose.**
It is not in footnotes or an appendix — it sits mid-sentence. Three forms:

1. **Apparatus runs.** The prose stops and several hundred characters of sigla, folio
   and line references follow before it resumes:
   *"…quod in Genesi scriptum est: `5 cf. Matth. 13, 52 15 I Cor. 10, 11 2 Incipit
   li[be]r [primus] de genesi ad li[tteram]; haec inscriptio codicis E a m. 2 profecta
   est…`"*
2. **Intra-word fusions** — a variant glued inside a word: `nullus christianusChristianus`,
   `contiiigebantcontingebant`. **3,361 across the CSEL set.** (Control: 2 in 60 Migne files.)
3. **Manuscript sigla** in the text stream: `P`, `BPQ`, `E2S`, `QVl`, `m. 2`, `fol. 36b`.

**Why it was left in.** A window-by-window scan (200-word windows) shows the apparatus
is **distributed throughout the text, not confined to separable blocks** — in
*Confessiones* only 7% of windows are clean and 64% carry some. So an automatic strip
would have deleted real words. Leaving it in, loudly flagged, is the honest option:
you can see the sigla and know to check.

Each file's frontmatter carries `apparatus: heavy | light | none` plus counts
(`apparatus_intraword_fusions`, `apparatus_siglum_tokens`), and every `heavy` file
opens with an explicit warning. **68 files are `heavy`.**

**Practically:** for reading and searching, all files are fine. For quoting, prefer the
Migne twin where one exists, or read the CSEL passage carefully and check it against
the printed volume.

## 4. How the conversion worked

Upstream files are **a single line each, no newlines**.

- **Migne files (218)** were restructured: `LIBER N`, `CAPUT N`, `Tractatus N`,
  `Sermo N`, `Epistola N`, `PRAEFATIO`, `Prologus` became `##` headings, and `§ N`
  section marks became bold labels. A marker counted as a division only when preceded
  by end-of-sentence punctuation.
- **CSEL files (63) were NOT restructured** — emitted verbatim. Their apparatus quotes
  manuscript incipits (*"EXPLICIT LIBER III … INCIPIT LIBER IIII BCFW"*), so division
  words appear inside apparatus notes and cannot be distinguished from real divisions.
  An earlier attempt to split them dropped words; that is why they are left flat.

**Verification: all 281 files are character-identical to their sources**
(whitespace-insensitive comparison after removing only the markup the converter adds).
**67,290,373 characters verified. Zero text lost.**

Script: `aug_convert.py`, in this session's scratchpad.

## 5. Two things a later session should know

- **Filename collisions were a real hazard.** Distinct works share a title — there are
  two different *Vita S. Augustini* (Gocelinus; Philippus de Harveng) — and an early
  run silently overwrote 4 files. The converter now disambiguates non-genuine works by
  author and refuses to reuse a path. If you extend this, keep that guard.
- **Patrologia Graeca from the same dataset is unusable and was rejected** — see the
  conversion tracker. It is uncorrected Internet Archive OCR: the Greek was read with a
  Latin-only character model and survives only as meaningless Latin strings (`thv` for
  τὴν, `Oávatov` for θάνατον), 0.0% Greek codepoints across six sampled volumes, with
  Migne's two columns read straight across. Not recoverable by post-processing. Source
  the Greek Fathers from SC/CCSG/TLG instead.

## 6. Not indexed

These files are **not in the semantic index** — deliberately, for now. A 66 MB addition
is a long index run (the last one took 5.5 h for 60k chunks). Grep and the existing
index still work; decide later whether the whole corpus should be embedded or only the
works actually searched.
