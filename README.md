# Medical Device Service Records — DSL Project

## Setup

```bash
# 1. Create virtual environment
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# 2. Install dependencies
pip install -r requirements.txt
python -m spacy download en_core_web_sm

# 3. Put DATA.xlsx in this folder
```

## Run Order

| Notebook | Input | Output | Time |
|---|---|---|---|
| `01_data_cleaning.ipynb` | `DATA.xlsx` | `DATA_cleaned.xlsx` | ~5 min |
| `02_topic_modelling.ipynb` | `DATA_cleaned.xlsx` | `DATA_with_topics.xlsx`, `topic_modelling_output.xlsx` | ~15-20 min |
| `03_classification.ipynb` | `DATA_with_topics.xlsx` | `classification_output.xlsx` | ~20-60 min (GPU faster) |

## Key Fixes vs Previous Code

| Issue | Old Code | New Code |
|---|---|---|
| Noise removal | Only caught 5+ zeros (`00he` slipped through) | Catches 2+ zeros |
| Notes in concerns | Only used `desc1_clean_bert` | Uses `desc1 + notes_problem_desc` |
| BERTopic labels | Used `And / Impact` etc. | Filters artifact words |
| BERTopic topics assigned | Pre-reduction topics saved | Post-reduction topics saved |
| XGBoost calibration | Raw probabilities (threshold=0.146) | `CalibratedClassifierCV` |
| BERT input length | `max_length=128` | `max_length=256` (more notes captured) |
| LDA topic labels | Never filled in | Auto-generated from top words |
| BERT in ensemble | Single val split, inflated weight | Correctly weighted |
| SMOTEENN | Not compared | Side-by-side comparison with/without |
| Optimization target | F1 | Recall (with min_precision guard) |

## Outputs
- `lda_coherence_sweep.png` — pick best k
- `lda_topics_words.png` — top words per LDA topic
- `lda_event_rate.png` — which LDA topics have most Important Events
- `bertopic_event_rate.png` — which BERTopic clusters are high-risk
- `bertopic_intertopic.html` — interactive topic map (open in browser)
- `bertopic_hierarchy.html` — topic dendrogram (open in browser)
- `holdout_evaluation.png` — recall/F1/PR curves with/without SMOTEENN
- `classification_output.xlsx` — full results + error analysis tabs
