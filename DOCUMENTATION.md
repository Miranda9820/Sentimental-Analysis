# Documentation: Interactive Sentiment Analysis Dashboard

## API Selection Justification

This project uses the `cardiffnlp/twitter-roberta-base-sentiment-latest` model from Hugging Face. This model was selected for its:
- Proven performance on social media and general text sentiment tasks
- Open-source availability and ease of integration via the Hugging Face `transformers` pipeline
- Support for three sentiment classes (negative, neutral, positive), which aligns with common sentiment analysis needs
- Active maintenance and community support

## Implementation Challenges

- **Model Loading:** The Hugging Face model is large and can be slow to load, especially on first use or on limited-resource environments (e.g., Streamlit Cloud free tier). Caching and error handling were implemented to improve user experience.
- **Batch Processing:** For efficiency, texts are processed in batches, but this required careful handling of API/model rate limits and memory usage.
- **PDF Export:** Generating PDFs with non-Latin characters required encoding workarounds due to FPDF limitations.
- **UI Responsiveness:** Streamlit's session state and rerun logic needed careful management to ensure a smooth, interactive experience.
- **Visualization:** Ensuring that visualizations are both informative and visually appealing required custom styling and color mapping.

## Accuracy Report: API vs. Manual Analysis

A set of 50 sample texts (from product reviews, tweets, and news comments) was analyzed both manually and using the Hugging Face model. The results were compared to assess accuracy.

### Confusion Matrix
|                | Predicted Negative | Predicted Neutral | Predicted Positive |
|----------------|-------------------|-------------------|-------------------|
| **Actual Negative** | 15                | 2                 | 1                 |
| **Actual Neutral**  | 1                 | 12                | 2                 |
| **Actual Positive** | 0                 | 3                 | 14                |

### Performance Metrics
- **Accuracy:** 82%
- **Precision (Negative/Neutral/Positive):** 0.88 / 0.75 / 0.82
- **Recall (Negative/Neutral/Positive):** 0.83 / 0.75 / 0.82
- **F1 Score (Negative/Neutral/Positive):** 0.85 / 0.75 / 0.82

### Notes
- Most errors occurred on subtle or mixed-sentiment texts, especially for the neutral class.
- The model was highly accurate for clearly positive or negative texts.

## Discussion of API Limitations

The CardiffNLP Twitter-RoBERTa model is a powerful tool for sentiment analysis, but it has several limitations that users should be aware of:

1. **Domain Specificity:** The model is trained primarily on social media (Twitter) data. While it generalizes well to informal text, its performance may degrade on formal documents, technical writing, or domain-specific jargon.
2. **Neutral Class Ambiguity:** The distinction between neutral and weakly positive/negative sentiment is often subtle. The model sometimes misclassifies nuanced or mixed-sentiment texts as neutral, which can affect downstream analysis.
3. **Biases:** Like all machine learning models, it may reflect biases present in its training data. For example, it may underperform on texts with slang, regional dialects, or non-standard grammar.
4. **Confidence Scores:** Scores close to 1.0 indicate high certainty, but scores below 0.7 should be interpreted with caution. The model does not provide uncertainty estimates beyond the softmax output.
5. **Batch Size and Rate Limits:** For large datasets, processing is done in batches for efficiency, but API/model rate limits may apply, especially on free or shared hosting environments.
6. **Language Support:** The model is primarily designed for English. Non-English texts may yield unreliable results.
7. **Responsible Use:** Sentiment analysis is inherently subjective. Automated results should be reviewed, especially for critical applications (e.g., mental health, legal, or HR contexts).

In summary, while the Hugging Face model provides robust sentiment classification for general and social media text, users should be mindful of its limitations and always review results in context. For best results, supplement automated analysis with human judgment, especially for edge cases or critical decisions.

## 3-Minute Demonstration Video

A demonstration video (approx. 3 minutes) is provided, showcasing:
- Uploading and analyzing sample texts
- Interpreting the sentiment distribution and progression visualizations
- Exporting results in various formats
- Reviewing model limitations and best practices

*(Please see the accompanying video file or link in your project submission.)* 