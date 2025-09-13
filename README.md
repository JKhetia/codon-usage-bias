{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "9cb7ec11-108e-48c7-8b13-c5a0d2b43780",
   "metadata": {},
   "outputs": [
    {
     "ename": "SyntaxError",
     "evalue": "invalid character '—' (U+2014) (3496096272.py, line 4)",
     "output_type": "error",
     "traceback": [
      "\u001b[0;36m  Cell \u001b[0;32mIn[1], line 4\u001b[0;36m\u001b[0m\n\u001b[0;31m    - **Human mitochondrion (rCRS, NC_012920.1)** — Vertebrate Mitochondrial code (2)\u001b[0m\n\u001b[0m                                                  ^\u001b[0m\n\u001b[0;31mSyntaxError\u001b[0m\u001b[0;31m:\u001b[0m invalid character '—' (U+2014)\n"
     ]
    }
   ],
   "source": [
    "# Codon Usage Bias — Human mtDNA vs *E. coli* (Beginner → Useful)\n",
    "\n",
    "This project computes **codon usage** from real **CDS (coding sequence) FASTA**:\n",
    "- **Human mitochondrion (rCRS, NC_012920.1)** — Vertebrate Mitochondrial code (2)  \n",
    "- ***Escherichia coli* K-12 MG1655 (NC_000913.3)** — Bacterial code (11)\n",
    "\n",
    "Codon bias affects **translation efficiency** and **gene expression**. If you want to express rejuvenation targets (e.g., **TERT**, **SIRT1**, **OSK**) efficiently, you often **codon-optimize** for the host. This notebook shows how to measure codon preferences in real genomes.\n",
    "\n",
    "---\n",
    "\n",
    "## Goals\n",
    "- Parse multi-FASTA **CDS** and count **codons** (triplets) across all genes  \n",
    "- Compute **relative frequencies** per codon  \n",
    "- Plot **top-used codons** per organism and a **comparison scatter** (organism vs organism)  \n",
    "- Save results as **CSV tables** and **publication-quality PNGs**  \n",
    "\n",
    "---\n",
    "\n",
    "## Methods (brief)\n",
    "- **Data** fetched from NCBI “sviewer” with `report=fasta_cds_na` (multi-FASTA of CDS).  \n",
    "- Custom utilities in Python **parse FASTA** and **count codons** (A/C/G/T only; ambiguous bases skipped; frames trimmed to ×3).  \n",
    "- Frequencies computed as `count / total_codons`.  \n",
    "- Visualizations in **Matplotlib**:\n",
    "  - Horizontal bar charts of **Top-N codons** per organism (with numeric labels)\n",
    "  - **Scatter** of E. coli vs Human mtDNA frequencies with **y=x** reference and the **10 biggest mismatches** annotated.\n",
    "\n",
    "> ⚠️ Genetic code differs: mitochondria (code 2) vs bacteria (code 11). We focus on **codon frequencies**, not translation per se. For AA-aware metrics (e.g., RSCU), map codons via Biopython’s `Bio.Data.CodonTable`.\n",
    "\n",
    "---\n",
    "\n",
    "## Results (example files)\n",
    "- Figures  \n",
    "  - `figures/codon_usage/mt_top_codons.png`  \n",
    "  - `figures/codon_usage/ec_top_codons.png`  \n",
    "  - `figures/codon_usage/compare_scatter.png`  \n",
    "- Tables  \n",
    "  - `results/codon_usage/mt_counts.csv`, `results/codon_usage/mt_freqs.csv`  \n",
    "  - `results/codon_usage/ec_counts.csv`, `results/codon_usage/ec_freqs.csv`\n",
    "\n",
    "---\n",
    "\n",
    "## Reproduce\n",
    "1. Open the notebook in **Jupyter** (Anaconda).  \n",
    "2. Run cells in order: **folders → download → parse/count → CSV → plots**.  \n",
    "3. To analyze other organisms, change the NCBI IDs in the download cell and re-run.\n",
    "\n",
    "---\n",
    "\n",
    "## Data Sources\n",
    "- Human mitochondrion (rCRS) — RefSeq **NC_012920.1**  \n",
    "  FASTA CDS: `https://www.ncbi.nlm.nih.gov/sviewer/viewer.fcgi?id=NC_012920.1&db=nuccore&report=fasta_cds_na`  \n",
    "- *E. coli* K-12 MG1655 — RefSeq **NC_000913.3**  \n",
    "  FASTA CDS: `https://www.ncbi.nlm.nih.gov/sviewer/viewer.fcgi?id=NC_000913.3&db=nuccore&report=fasta_cds_na`\n",
    "\n",
    "---\n",
    "\n",
    "## License\n",
    "MIT (see `LICENSE`).\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "96f60937-5915-47e8-8f6f-b04f58e5d282",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "anaconda-2024.02-py310",
   "language": "python",
   "name": "conda-env-anaconda-2024.02-py310-py"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.10.14"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
