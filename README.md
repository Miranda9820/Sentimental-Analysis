# Interactive Sentiment Analysis Dashboard

This project is a professional, interactive sentiment analysis dashboard built with Streamlit and Hugging Face Transformers. It allows users to analyze the sentiment of text data (direct entry or file upload), visualize results, and export them in multiple formats.

## Features
- Sentiment analysis using a state-of-the-art Hugging Face model
- Keyword extraction for each text
- Visualizations: sentiment distribution, progression, and confidence
- Export results as CSV, JSON, or PDF
- History tracking and comparative analysis
- Professional UI with gradient background

## Deployment
This app is deployed on [Streamlit Cloud](https://share.streamlit.io/your-username/your-repo/main/ap.py). [Website](https://sentiment-analysis-week.streamlit.app/).

To run locally:
```bash
pip install -r requirements.txt
streamlit run ap.py
```

## Model
- [cardiffnlp/twitter-roberta-base-sentiment-latest](https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment-latest)

## License
MIT 
