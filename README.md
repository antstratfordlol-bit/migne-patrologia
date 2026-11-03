# Migne Patrologia Cursus Completus (Markdown Edition)

Complete digital text collection of Jacques-Paul Migne's *Patrologia Cursus Completus*, formatted in clean UTF-8 Markdown for search, computational philology, academic citations, and AI-assisted theological research.

```text
migne-patrologia/
├── README.md
├── migne_manifest.json          # Complete JSON index of authors, volumes, and contents
├── Corpus_Augustinianum/        # 283 works of Saint Augustine (64.8 MB)
├── Patrologia_Graeca/           # 161 volumes (PG 1–161) in Polytonic Greek (723.6 MB)
└── Patrologia_Latina/           # 221 volumes (PL 1–221) in Ecclesiastical Latin (889.7 MB)
```

---

## 1. Contents & Scope

* **Patrologia Latina (PL)**:
  * 221 volumes covering Western Patristic and early medieval authors from Tertullian (c. 160 – c. 220) through the death of Pope Innocent III (1216).
  * Includes the major Latin Fathers: Ambrose, Jerome, Augustine, Gregory the Great, Isidore of Seville, Bede, and Bernard of Clairvaux.

* **Patrologia Graeca (PG)**:
  * 161 volumes covering Eastern Patristic literature from the Apostolic Fathers (Clement of Rome, Ignatius of Antioch, Polycarp) through the Council of Florence (1439).
  * Encoded in full UTF-8 polytonic Greek orthography with accents, breathings, and iota subscripts.
  * Includes Athanasius, Basil the Great, Gregory of Nazianzus, Gregory of Nyssa, John Chrysostom, Cyril of Alexandria, Maximus the Confessor, and John Damascene.

* **Corpus Augustinianum**:
  * 283 distinct treatises, sermons (*sermones*), letters (*epistolae*), and polemical works of Saint Augustine of Hippo, indexed with standard structural anchors.

* **Catalogue & Manifest (`migne_manifest.json`)**:
  * Machine-readable metadata file mapping every volume number (`PL_001` to `PL_221`, `PG_001` to `PG_161`) to author names, individual treatises, and file paths.

---

## 2. Text Features & Architecture

* **Pure Plaintext & Markdown**: All volumes are stored as standard `.md` files, free from proprietary binary wrappers or database locks.
* **Structural Compatibility**: Fully compatible with modern search engines (grep, ripgrep, SQLite FTS5), vector embedding pipelines, and LLM agentic tools (Claude Code, Antigravity).
* **Open Scholarship**: All underlying texts are in the public domain.
