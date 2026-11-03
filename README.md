# Migne Patrologia Cursus Completus (Archival OCR Text Corpus)

An uncurated digital text archive of Jacques-Paul Migne's *Patrologia Cursus Completus*, intended for computational search, rapid lexical lookup (`grep`/`ripgrep`), and locating volume and column references.

```text
migne-patrologia/
├── README.md
├── migne_manifest.json          # Complete JSON index of authors, volumes, and contents
├── Corpus_Augustinianum/        # 283 works of Saint Augustine (64.8 MB)
├── Patrologia_Graeca/           # 161 volumes (PG 1–161) — Raw Historical OCR (723.6 MB)
└── Patrologia_Latina/           # 221 volumes (PL 1–221) — Machine-readable Latin (889.7 MB)
```

---

## 1. Important Notice on Textual Fidelity & Academic Use

> [!CAUTION]
> **This repository is an archival raw OCR corpus, not a proofread critical edition.**
> Do not ingest these texts directly into formal citation databases or critical apparatuses without verifying readings against physical volumes or modern critical editions (such as *Corpus Christianorum*, *Sources Chrétiennes*, or *CSEL*).

### Textual Status by Section:
* **Corpus Augustinianum (High Fidelity)**:
  * 283 distinct treatises, sermons, and letters of Saint Augustine.
  * Formatted with structural section anchors and standard ecclesiastical Latin orthography.
* **Patrologia Latina (Moderate to High Fidelity)**:
  * 221 volumes covering Western Patristic authors from Tertullian through Innocent III.
  * Generally readable Latin text layer suitable for lexical searching and locating citations.
* **Patrologia Graeca (Raw / Uncleaned Historical OCR)**:
  * 161 volumes of Greek Patristic literature.
  * **Textual Reality**: These files originate from early Google Books and Internet Archive digitisation runs (circa 2005–2008). 
  * The OCR software frequently used Latin character sets over complex 19th-century Greek typography, resulting in garbled words, misrecognised accents, and unstripped Google scanning boilerplate in the front matter.
  * Preserved here strictly as a raw search corpus for scholars who need full-text string matching across obscure Greek volumes.

---

## 2. Intended Scholarly Uses

1. **Full-Text Lexical Search**:
   Locating obscure phrases, Patristic authors, or scriptural commentaries using fast local tools:
   ```bash
   rg -i "lex orandi" Patrologia_Latina/
   ```
2. **Bibliographic Orientation**:
   Querying `migne_manifest.json` to map specific treatises and authors to their historical volume numbers.
3. **Drafting and Proof-Checking**:
   Finding the approximate volume and column before verifying the passage against a printed volume or digital facsimile.

---

## 3. Provenance & Public Domain Status
All underlying materials compiled by Abbé Jacques-Paul Migne between 1844 and 1866 are in the worldwide public domain. Digitisation was carried out by various library partners via Google Books and the Internet Archive.
