# -import streamlit as st
import pandas as pd
import matplotlib.pyplot as plt

st.title("CSV分析アプリ📊")

uploaded_file = st.file_uploader("CSVファイルをアップロードしてください", type=["csv"])

if uploaded_file is not None:
    df = pd.read_csv(uploaded_file)
    st.subheader("データプレビュー")
    st.dataframe(df)

    st.subheader("基本統計情報")
    st.write(df.describe())

    st.subheader("列を選んでグラフ表示")
    selected_column = st.selectbox("列を選んでください", df.columns)

    fig, ax = plt.subplots()
    df[selected_column].plot(kind='line', ax=ax)
    st.pyplot(fig)
