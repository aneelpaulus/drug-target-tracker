# Drug Target Tracker

Type a drug target, such as CD38, BCMA, or KRAS, and see every drug aimed at it with its development stage, plus the latest research from PubMed, preprint servers, and major cancer and hematology meetings.

**[Try it live](https://aneelpaulus.github.io/drug-target-tracker/)**

## What you get

**Drugs aimed at the target**, each labeled by stage:

| Label | Meaning |
|---|---|
| FDA-approved | An FDA approval or license record exists. The earliest approval date is shown when the record has one. |
| Approved outside US | Approved by another regulator (for example in Europe, Japan, or China), with no FDA record found. |
| Clinical / investigational | Tested in people but not approved anywhere. The highest trial phase is shown. |
| Preclinical | Lab or animal work only. |

**Research activity over the last 10 years**, with yearly counts for PubMed articles, preprints, and meeting abstracts.

**The latest items** from each, linked to the source.

You can also add the target's other names (for example CS1 for SLAMF7) with one tap, filter drugs by stage, and download the drug list as a CSV file.

## Where the data comes from

All sources are free and public, and the page queries them directly from your browser.

| What | Source |
|---|---|
| Curated drugs for the target and their highest stage | [Open Targets Platform](https://platform.opentargets.org) (drawing on ChEMBL) |
| FDA approval dates | openFDA Drugs@FDA, with openFDA drug labels as a backup for cell and gene therapies |
| Newer agents found by code name (for example STI-6129, GEN3014) | [ClinicalTrials.gov](https://clinicaltrials.gov) |
| PubMed articles and preprints (bioRxiv, medRxiv, Research Square, and others) | [Europe PMC](https://europepmc.org) |
| Meeting abstracts | Crossref, using each meeting's journal supplement: ASCO (*Journal of Clinical Oncology*), ASH (*Blood*), AACR (*Cancer Research*), AACR-NCI-EORTC (*Molecular Cancer Therapeutics*), ESMO (*Annals of Oncology*), EHA (*HemaSphere*, through 2023) |

## How the drug list is built

1. Open Targets supplies drugs that experts have linked to the target, with each drug's highest stage for any disease.
2. Every drug that has reached approval somewhere is checked against FDA records. If the FDA has a record, it's "FDA-approved". If not, it's "Approved outside US".
3. ClinicalTrials.gov fills in newer agents that curated databases haven't caught up with. A trial drug is listed only when it has a code name and the trial describes it as acting on the target ("anti-CD38", "KRAS G12C inhibitor", "BCMA CAR-T"). A trial that only names the target as patient context ("for KRAS-mutant tumors") doesn't count. Trial drugs that match a known drug are folded into that drug.

## Limitations

- **Preclinical agents rarely appear in the drug table.** Curated databases mostly track drugs once they reach trials, so early agents usually show up only in the research feeds (preprints and AACR abstracts especially).
- **Trial-derived agents need checking.** Code names are pulled automatically, so a few may be unrelated or vaguely named. Each one links to its trials.
- **Meeting abstracts are matched on title only.** An abstract that mentions the target only in its body won't be found.
- **SITC abstracts, and EHA abstracts from 2024 on, aren't individually indexed** in any free database. The page links to search them directly instead.
- **ASCO meeting abstracts** are covered through the *Journal of Clinical Oncology* supplements, which hold the annual meeting and the major symposia.
- Very busy targets (like KRAS in AACR abstracts) hit a cap of 1,000 items per meeting, which the page marks with a "+".
- Crossref allows one request per second, so a search takes 10 to 30 seconds.
- The "Approved outside US" label depends on the FDA lookup. A drug approved in the US under an unusual name could be mislabeled. The details column says which record was used.

## Run your own copy

The whole tool is one file, `index.html`. To host it free on GitHub:

1. Create a new public repository and upload `index.html`, `README.md`, and `LICENSE`.
2. In the repository, open **Settings**, then **Pages**.
3. Under "Build and deployment", choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
4. After a minute or two, the page shows your live link.

## Disclaimer

For research and education only. Not medical or investment advice. Not affiliated with any of the data providers.

## License

MIT. See `LICENSE`.

Built by Aneel Paulus, MD, MS.
