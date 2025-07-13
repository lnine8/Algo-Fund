# 📊 Performance Dashboard Template (Streamlit + Plotly)

This Streamlit dashboard visualizes key performance metrics of the DeltaNeutral Vault including NAV, APY, Sharpe Ratio, and Drawdown over time. It's designed to be run locally or hosted on Streamlit Cloud for real-time visibility.

## 📁 Folder Structure

```
/dashboard/
└── streamlit_app.py
```

## 🧠 Code: `streamlit_app.py`

```python
import streamlit as st
import pandas as pd
import plotly.express as px

# Load backtest or live performance data
df = pd.read_csv('vault_performance.csv')

st.title("DeltaNeutral Vault Performance")

st.subheader("NAV Over Time")
st.line_chart(df['NAV'])

st.subheader("APY Distribution")
st.bar_chart(df['APY'])

st.subheader("Sharpe Ratio: {:.2f}".format(df['Sharpe'].iloc[-1]))

st.subheader("Drawdown Tracker")
fig = px.area(df, x='Date', y='Drawdown')
st.plotly_chart(fig)
```

## 🚀 Deployment

To run locally:

```bash
streamlit run streamlit_app.py
```

To host online:

1. Sign in to [Streamlit Cloud](https://share.streamlit.io/)
2. Upload this file with the dataset `vault_performance.csv`
3. Deploy and monitor your strategy in real time.
