# Hidden Business Activity Detection

Mastercard x AIESEC Data Quest project for identifying consumer cards with transaction behavior similar to confirmed business-card activity.

## Objective

The goal is to rank consumer cards by their business-like transaction behavior.

The model is designed for lead prioritization, SME onboarding, business-card offers, and merchant acquiring opportunities. It is not designed for enforcement or for proving that a customer is definitely running a business.

Final output format:

```text
card_number,score
```

Higher scores indicate stronger business-like behavior.

## Project Structure

```text
mastercard 2/
|-- main.ipynb
|-- README.md
|-- data/
|   |-- business_cards_MDQ.parquet
|   |-- consumer_cards_MDQ.parquet
|   `-- merchants_reference.parquet
`-- outputs/
    `-- submission_final.csv
```

## Data

The project processes synthetic transaction data provided for the case:

- 12.8M+ transaction records
- 80,000 consumer cards for inference
- 25,000 business cards as confirmed positive examples
- 2,165 merchant references
- 31 final behavioral features after diagnostics

Consumer cards are treated as unlabeled, not as true negatives, because hidden business activity may exist inside the consumer population.

## Methodology

The solution uses Positive-Unlabeled Learning (PU-Learning).

### 1. Feature Engineering

Transaction logs are aggregated into card-level behavioral features. Main feature groups include:

- transaction volume and amount intensity
- merchant concentration and merchant entropy
- MCC/category diversity
- high-value transaction share
- time-based behavior
- transaction regularity and activity density

The feature set focuses on behavioral structure rather than customer identity labels.

### 2. Reliable Negative Selection

Business cards are used as confirmed positive examples. Consumer cards are unlabeled.

An iterative PU-learning process scores consumer cards by business-likeness and selects the lowest-scoring consumers as reliable proxy negatives. These proxy negatives are used only as an approximation, not as guaranteed real negatives.

### 3. Model Training and Selection

The project trains and compares:

- XGBoost
- LightGBM
- XGBoost + LightGBM ensemble strategies

Model selection is based on isolated hold-out AUC-ROC.

Final selected strategy:

```text
50/50 Ensemble: XGBoost + LightGBM
```

## Validation Results

Hold-out validation is proxy-based: it measures separation between confirmed business cards and proxy consumer negatives.

| Strategy | Hold-out ROC-AUC | Notes |
|---|---:|---|
| XGBoost | 0.965254 | Strong single-model baseline |
| LightGBM | 0.962658 | Stable alternative model |
| Ensemble 50/50 | 0.965299 | Final selected strategy |

Additional metrics from the validation stage include PR-AUC, F1-optimal threshold analysis, feature importance, and SHAP-based explainability.

Important: these metrics validate the proxy modeling task, not real-world hidden-business detection accuracy, because true hidden-business labels are unavailable.

## Output

The final prediction file is saved as:

```text
outputs/submission_final.csv
```

Expected format:

```text
card_number,score
```

The file contains scores for all 80,000 consumer cards.

## Score Interpretation

Scores should be used as ranking signals for business prioritization:

- Top score segment: priority SME onboarding and relationship-manager review
- P80-P95 segment: soft in-app business-product offers
- P60-P80 segment: watchlist or low-cost retargeting
- Lower-score segment: no immediate action

Thresholds should be recalibrated using real campaign outcomes and manual review feedback.

## How to Run

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the notebook:

```bash
jupyter notebook main.ipynb
```

Recommended steps:

1. Place the parquet files in the `data/` directory.
2. Open `main.ipynb`.
3. Run all cells from top to bottom.
4. Check the generated files in `outputs/`.

## Requirements

Core data processing:
numpy
pandas
scipy

Machine learning:
scikit-learn
xgboost
lightgbm
optuna
shap

Visualization:
matplotlib
seaborn

Notebook environment:
jupyter
notebook


## Explainability

The notebook includes feature importance and SHAP analysis to explain which behavioral signals drive the model score. The strongest signals are mainly related to merchant concentration, spending intensity, and business-like transaction structure.

## Limitations

- True hidden-business labels are not available for consumer cards.
- Reliable negatives are proxy negatives, not guaranteed real negatives.
- Hold-out metrics measure a proxy task, not true production accuracy.
- Synthetic data may exaggerate class separability.
- Strong features such as `amount_per_merchant` require careful monitoring and calibration in real deployment.
- Scores are ranking signals, not proof of commercial activity.
- Production deployment would require campaign feedback, manual review, drift monitoring, and periodic retraining.

## Business Value

The solution turns raw transaction behavior into an actionable prioritization layer for SME growth.

It helps identify consumer cards that look commercially active, rank them by business-like behavior, and support targeted business-product activation while keeping the final decision process calibrated and reviewable.
