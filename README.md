# HindiFSA
# Hindi Financial News Headlines Sentiment Dataset

## Overview
A comprehensive dataset of 9,860 Hindi financial news headlines with entity-aware sentiment annotations, systematically collected from authoritative Hindi news sources. This dataset provides a valuable resource for researchers and practitioners working on financial sentiment analysis, natural language processing, and Indian market analysis.

## Dataset Structure
The dataset is provided as an XLSX file with the following columns:
- **Hindi**: Contains the financial news headlines in Hindi text
- **Sentiment_Annotation**: JSON formatted string containing entity-sentiment pairs
  - Format: `{"entity_name": "sentiment_class"}`
  - Sentiment classes: "positive", "negative", "neutral"

Example:
```
Hindi: "Lux इंडस्ट्रीज़ होजरी निर्माक NSE पर उच्य करेगा"
Sentiment_Annotation: {"Lux इंडस्ट्रीज़": "positive"}
```

## Usage

### Loading the Dataset
```python
import pandas as pd

# Load the dataset
df = pd.read_excel('hindi_financial_sentiment.xlsx')

# Access headlines
headlines = df['Hindi'].tolist()

# Access sentiment annotations
sentiments = df['Sentiment_Annotation'].tolist()

# Convert sentiment annotations from string to dictionary (if needed)
import json
parsed_sentiments = [json.loads(sent) for sent in sentiments]
```

### Basic Analysis Example
```python
# Get sentiment distribution
sentiment_counts = {
    'positive': 0,
    'negative': 0,
    'neutral': 0
}

for sent_dict in parsed_sentiments:
    for entity, sentiment in sent_dict.items():
        sentiment_counts[sentiment] += 1

# Print distribution
print("Sentiment Distribution:")
for sentiment, count in sentiment_counts.items():
    print(f"{sentiment}: {count}")
```

## License
This dataset is released under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

## References
1. The Economic Times Hindi. (2024). Accessed: 14/08/2024: https://hindi.economictimes.com/
2. Financial Express. (2024). Accessed: 16/08/2024: https://hindi.financialexpress.com/
3. Money Control. (2024). Accessed: 11/08/2024: https://hindi.moneycontrol.com/
4. Business Standard. (2024). Accessed: 16/08/2024: https://hindi.business-standard.com/finance
5. Aaj Tak Business. (2024). Accessed: 20/08/2024: https://www.aajtak.in/business
6. Hindustan. (2024). Accessed: 28/08/2024: https://www.livehindustan.com/business/news

## Acknowledgments
- We gratefully acknowledge the contributions of the above-mentioned news sources for providing the raw data that made this dataset possible.

## Citation
If you use this dataset in your research, please cite it as:
```
@dataset{hindi_financial_sentiment_2024,
  author       = {[Your Name]},
  title        = {Hindi Financial News Headlines Sentiment Dataset},
  year         = {2024},
  publisher    = {GitHub},
  version      = {1.0},
  url          = {[Your GitHub Repository URL]}
}
```
