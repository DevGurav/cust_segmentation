# Customer Segmentation — KMeans + Streamlit

A small data-analysis project that segments customers using **KMeans clustering** and exposes the trained model through an interactive **Streamlit** dashboard.

> **Status:** Academic / learning project. Functional end-to-end but kept intentionally small in scope — see my pinned repositories for production-grade work.

## What it does

- Loads a customer dataset (`Age`, `Annual_Income`, `Spending_Score`, `Purchase_Frequency`, `Total_Spending`, `Family_Size`, `Gender`, `Marital_Status`).
- Cleans the data, scales numeric features with a saved `StandardScaler`, and assigns each customer to a cluster using a pre-trained KMeans model.
- Lets a user upload their own customer CSV through the Streamlit UI and explore the clusters with radar charts, scatter plots, and a pie-segmentation chart.
- Exposes downloadable cluster assignments as a CSV.

## Repository layout

```text
cust_segmentation/
├── cust_segment.ipynb                  EDA + clustering notebook (training pipeline)
├── dataset/
│   ├── customer_data.csv               Raw input
│   ├── cleaned_customers.csv           After preprocessing
│   ├── df_scaled.csv                   Feature-scaled data
│   └── sample_customer_upload.csv      Sample file for the Streamlit upload UI
├── model/
│   ├── customer_segment_model.joblib   Trained KMeans model
│   ├── scaler.joblib                   Fitted StandardScaler
│   └── streamlit_app.py                Streamlit dashboard
├── output/                             Cluster visualizations (radar, scatter, pie, etc.)
│   ├── clustered_customers.csv
│   └── *.jpeg
└── requirements.txt
```

## Run locally

```bash
git clone https://github.com/DevGurav/cust_segmentation.git
cd cust_segmentation
pip install -r requirements.txt
streamlit run model/streamlit_app.py
```

The app opens at `http://localhost:8501`. Upload the included `dataset/sample_customer_upload.csv` to see the dashboard work end-to-end.

## Tech stack

- **Python** — pandas, scikit-learn (`KMeans`, `StandardScaler`), joblib
- **Streamlit** — interactive UI
- **matplotlib**, **seaborn** — charts in the notebook and output gallery

## Notes

- The notebook (`cust_segment.ipynb`) contains the EDA, feature engineering, KMeans cluster-count selection (elbow method), and model persistence.
- The app currently assumes the input CSV uses the exact column names listed above. Flexible column mapping is a planned improvement.

## Authors

- **Devendra Gurav** ([@DevGurav](https://github.com/DevGurav))
- **Pankaj Bhandari**
