# GenAI Adoption Text Mining — Replication Code

**Bachelor's Thesis | Kozminski University | 2025**

> *Implementation Gap in German Mittelstand: A TOE Framework Analysis of Why Strategic Intent Fails to Convert into Operational Adoption*
>
> Author: Dominika Butryn (Student ID: 49835)
> Supervisor: PhD Monika Sonta

---

## About this repository

This repository contains the complete replication code and output data for the empirical analysis conducted in the above thesis. The study applies dual-keyword text mining to the annual reports of 20 publicly listed German firms to quantify the distance between strategic AI intent and operational AI deployment, using an original metric called the **Gap Ratio**.

---

## Repository structure

```
thesis_textmining/
│
├── ai_gap_analysis.ipynb        # Main analysis: keyword extraction, Gap Ratio
│                                #   calculation, and cluster assignment for
│                                #   15 Mittelstand firms
│
├── benchmark_comparison.ipynb   # Comparison analysis: 5 large enterprise
│                                #   benchmarks vs Mittelstand sample
│
├── ai_gap_results.csv           # Gap Ratio scores per firm
├── ai_keyword_detail.csv        # Raw strategic and operational keyword counts
├── ai_keyword_contexts.csv      # Matched keyword passages (validation corpus)
├── benchmark_results.csv        # Large enterprise keyword counts and scores
│
├── chart1_grouped_bar.png       # Strategic vs operational keyword counts by firm
├── chart2_gap_ratio.png         # Gap Ratio sorted high to low (Figure 1 in thesis)
├── chart3_quadrant.png          # AI language quadrant map (Figure 2 in thesis)
├── chart4_heatmap.png           # Keyword density heatmap
├── chart5_stacked_share.png     # Share of strategic vs operational language
├── chart6_normalised.png        # Normalised keyword density per 10,000 words
├── chart_mentions_absolute.png  # Absolute keyword mention counts
├── chart_mentions_density.png   # Keyword density across all firms
├── chart_group_comparison.png   # Mittelstand vs large enterprise comparison
├── chart_dotplot.png            # Dot plot of Gap Ratios
└── ai_gap_chart.png             # Summary Gap Ratio chart
```

---

## Methodology

### Dual-keyword classification

Each annual report was processed as full text. Sentences and paragraphs were tokenised, lemmatised, and searched for two keyword categories:

| Category | Keywords |
|---|---|
| **Strategic intent** | AI strategy, generative AI, GenAI vision, AI roadmap, transformation, ambition |
| **Operational adoption** | deployed, in production, rolled out, integrated, use case, pilot, scaled |

All keyword matches were manually reviewed to confirm context and discard false positives.

### The Gap Ratio

The Gap Ratio is an original metric developed for this study. It quantifies the distance between a firm's strategic AI communication and its operational AI evidence:

```
Gap Ratio = (Strategic keyword count + 1) / (Operational keyword count + 1)
```

Both counts are normalised per 10,000 words before calculation to remove length bias across firms of different size. A ratio above 1.0 indicates that strategic language exceeds operational evidence. A ratio above 2.0 signals a significant organisational gap requiring attention before further strategic investment.

### Cluster profiles

Applying the Gap Ratio to the 15 Mittelstand firms produces four empirically distinct adoption profiles:

| Cluster | Firms | Gap Ratio range |
|---|---|---|
| **Strategic-Dominant** | Bechtle, Nemetschek, Dürr, Secunet, Krones | 1.7 – 6.4 |
| **Balanced** | TRUMPF, Jenoptik | ~1.0 – 1.4 |
| **Operational-Dominant** | ATOSS, Heidelberg Druckmaschinen | 0.20 – 0.59 |
| **AI-Silent** | Wacker Neuson, Dermapharm, Deutz, RATIONAL, STRATEC | 0.00 |

10 of 15 Mittelstand firms have a Gap Ratio above 1.

---

## Data sources

The PDF annual reports are not included in this repository due to copyright. All reports are Annual Report FY 2024 and are publicly available from each company's investor relations page:

**Mittelstand sample**

| Company | Investor Relations |
|---|---|
| Bechtle AG | https://www.bechtle.com/investor-relations |
| Nemetschek SE | https://ir.nemetschek.com |
| Dürr AG | https://www.durr-group.com/en/investor-relations |
| Secunet Security Networks AG | https://www.secunet.com/investor-relations |
| Krones AG | https://www.krones.com/en/investor-relations |
| TRUMPF GmbH + Co. KG | https://www.trumpf.com/en_INT/company/trumpf-group/figures-data-facts |
| Jenoptik AG | https://ir.jenoptik.com |
| ATOSS Software AG | https://www.atoss.com/en/investor-relations |
| Heidelberger Druckmaschinen AG | https://www.heidelberg.com/global/en/about_heidelberg/investor_relations |
| Wacker Neuson SE | https://www.wackerneuson.com/en/investor-relations |
| Dermapharm Holding SE | https://www.dermapharm.de/en/investor-relations |
| Deutz AG | https://www.deutz.com/en/investor-relations |
| RATIONAL AG | https://www.rational-online.com/en/investor-relations |
| STRATEC SE | https://www.stratec.com/investor-relations |
| SUSS MicroTec SE | https://www.suss.com/investor-relations |

**Large enterprise benchmarks**

| Company | Investor Relations |
|---|---|
| SAP SE | https://www.sap.com/investors |
| Deutsche Telekom AG | https://www.telekom.com/en/investor-relations |
| Siemens AG | https://www.siemens.com/investor-relations |
| Volkswagen AG | https://www.volkswagen-group.com/en/investor-relations |
| Allianz SE | https://www.allianz.com/en/investor_relations |

---

## Requirements

The notebooks run on Python 3.9 or higher. Install the required packages with:

```bash
pip install -r requirements.txt
```

**Core dependencies:**

```
pdfplumber>=0.9
pandas>=1.5
matplotlib>=3.6
seaborn>=0.12
numpy>=1.23
```

To run the notebooks interactively:

```bash
pip install notebook
jupyter notebook
```

---

## How to replicate

1. Clone this repository
2. Download the annual reports listed above and place the PDFs in a folder called `reports/`
3. Install the dependencies
4. Open `ai_gap_analysis.ipynb` and run all cells — this produces the Gap Ratio scores and cluster assignments
5. Open `benchmark_comparison.ipynb` and run all cells — this produces the large enterprise comparison

The notebooks are fully documented with inline comments explaining each step.

---

## Citation

If you use this code or the Gap Ratio methodology, please cite the thesis:

> Butryn, Dominika. *Implementation Gap in German Mittelstand: A TOE Framework Analysis of Why Strategic Intent Fails to Convert into Operational Adoption*. Bachelor's thesis, Kozminski University, 2025.

---

## Licence

The code in this repository is released under the MIT Licence. The annual report PDFs are the property of their respective companies and are not included here.
