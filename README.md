# Codon Usage Bias — Human mtDNA vs *E. coli* (Beginner → Useful)

This project computes **codon usage** from real **CDS (coding sequence) FASTA**:
- **Human mitochondrion (rCRS, NC_012920.1)** — Vertebrate Mitochondrial code (2)  
- ***Escherichia coli* K-12 MG1655 (NC_000913.3)** — Bacterial code (11)

Codon bias affects **translation efficiency** and **gene expression**. If you want to express rejuvenation targets (e.g., **TERT**, **SIRT1**, **OSK**) efficiently, you often **codon-optimize** for the host. This notebook shows how to measure codon preferences in real genomes.

---

## Goals
- Parse multi-FASTA **CDS** and count **codons** (triplets) across all genes  
- Compute **relative frequencies** per codon  
- Plot **top-used codons** per organism and a **comparison scatter** (organism vs organism)  
- Save results as **CSV tables** and **publication-quality PNGs**  

---

## Methods (brief)
- **Data** fetched from NCBI “sviewer” with `report=fasta_cds_na` (multi-FASTA of CDS).  
- Custom utilities in Python **parse FASTA** and **count codons** (A/C/G/T only; ambiguous bases skipped; frames trimmed to ×3).  
- Frequencies computed as `count / total_codons`.  
- Visualizations in **Matplotlib**:
  - Horizontal bar charts of **Top-N codons** per organism (with numeric labels)
  - **Scatter** of E. coli vs Human mtDNA frequencies with **y=x** reference and the **10 biggest mismatches** annotated.

> ⚠️ Genetic code differs: mitochondria (code 2) vs bacteria (code 11). We focus on **codon frequencies**, not translation per se. For AA-aware metrics (e.g., RSCU), map codons via Biopython’s `Bio.Data.CodonTable`.

---

## Results (example files)
- Figures  
  - `mt_top_codons.png`  
  - `ec_top_codons.png`  
  - `compare_scatter.png`  
- Tables  
  - `mt_counts.csv`, `mt_freqs.csv`  
  - `ec_counts.csv`, `ec_freqs.csv`

---

## Reproduce
1. Open the notebook in **Jupyter** (Anaconda).  
2. Run cells in order: **folders → download → parse/count → CSV → plots**.  
3. To analyze other organisms, change the NCBI IDs in the download cell and re-run.

---

## Data Sources
- Human mitochondrion (rCRS) — RefSeq **NC_012920.1**  
  FASTA CDS: `https://www.ncbi.nlm.nih.gov/sviewer/viewer.fcgi?id=NC_012920.1&db=nuccore&report=fasta_cds_na`  
- *E. coli* K-12 MG1655 — RefSeq **NC_000913.3**  
  FASTA CDS: `https://www.ncbi.nlm.nih.gov/sviewer/viewer.fcgi?id=NC_000913.3&db=nuccore&report=fasta_cds_na`

---

## License
MIT (see `LICENSE`).
