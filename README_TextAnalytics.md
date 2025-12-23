# Language, Identity, and Polarization: Reddit Text Analysis

A comprehensive NLP study analyzing linguistic markers, pronoun usage, and psychological language features across diverse Reddit communities to understand identity construction, emotional expression, and social dynamics in online discourse.

## Overview

This research examines how linguistic patterns—particularly pronoun usage and psychological language features—vary across thematically distinct Reddit communities. Using data collected via the PRAW API from 12 subreddits categorized into Politics, Mental Health & Life, Discussion & Opinions, and Hobbies & Education, we employ statistical and vector-based similarity metrics to reveal how language reflects and shapes community identity, polarization, and social dynamics.

## Key Findings

- **Mental Health Communities**: High first-person singular pronoun usage (7.8-8.8 per 1,000 words), elevated emotional and polite language, indicative of introspective and supportive discourse

- **Political Communities**: Elevated inclusive pronoun usage (5.6-7.0 per 1,000 words), high assertiveness and rudeness, reflecting ideological positioning and group-based framing

- **Discussion & Opinion Communities**: Moderate pronoun usage patterns, balanced linguistic features, demonstrating neutral and inquisitive tone

- **Hobby & Education Communities**: Lower emotional expression, moderate lexical diversity, informative and neutral communication style

## Features

- **Comprehensive Linguistic Analysis**
  - First-person singular pronouns (I, me)
  - Inclusive pronouns (we, us, our, ours)
  - Exclusive pronouns (they, them, their, theirs)
  - Psychological language features (tentative, assertive, emotional, cognitive, polite, rude)
  - Lexical diversity and engagement metrics

- **Advanced Statistical Methods**
  - Chi-square tests for distributional significance
  - Fisher's exact test for sparse data
  - Cosine similarity for directional pattern alignment
  - Jaccard similarity for proportional overlap

- **Data Collection & Processing**
  - Web scraping via PRAW API
  - Text preprocessing with NLTK
  - Structured CSV outputs
  - Community-level aggregation

## Datasets & Communities

### Subreddit Categories

| Category | Subreddits |
|----------|-----------|
| **Politics** | r/PoliticalDebate, r/Liberal, r/NeutralPolitics, r/Feminism, r/Atheism |
| **Mental Health & Life** | r/mentalhealth, r/Parenting, r/SimpleLiving, r/relationships |
| **Discussion & Opinions** | r/changemyview, r/OutOfTheLoop |
| **Hobbies & Education** | r/books |

### Data Collection Metrics
- **Total Subreddits**: 12
- **Data Source**: PRAW API (Reddit's official API)
- **Content**: Top posts and top-level comments
- **Filtering**: Minimum 10 character comments to ensure substantive content
- **Storage Format**: CSV with structured fields (Subreddit, Comment ID, Parent ID, Comment Text)

## Methodology

### 1. Pronoun Usage Analysis

**Text Preprocessing:**
- NLTK stopword removal
- Lowercasing and punctuation stripping
- Tokenization and cleaning
- Custom pronoun counting

**Frequency Calculation:**
- Absolute counts per subreddit
- Relative frequency (per 1,000 words)
- Frequency band categorization (Frequent ≥30, Moderate 5-29.9, Rare <5)

### 2. Linguistic Style & Psychological Features

**Extracted Features:**

| Feature | Description | Examples |
|---------|-------------|----------|
| **Tentative Language** | Hedging, uncertainty, indirectness | maybe, perhaps, I think, not sure |
| **Assertive Language** | Certainty, rhetorical dominance | clearly, definitely, without a doubt, in fact |
| **Emotional Terms** | Affective expressions | happy, sad, angry, grateful, frustrated |
| **Cognitive Terms** | Reflective/analytical language | think, believe, because, analyze |
| **Polite Expressions** | Cooperative, empathetic markers | please, thank you, kind, respect |
| **Rude Expressions** | Hostile, uncivil language | stupid, idiot, hate, moron |
| **Questions** | Engagement and inquiry frequency | ? count per 1,000 words |
| **Lexical Diversity** | Vocabulary richness | Type-Token Ratio (unique words / total words) |

All features normalized to per 1,000 word basis for cross-community comparison.

### 3. Statistical Evaluation Metrics

**Chi-square Test (χ²)**
```
χ² = Σ (O - E)² / E
```
Assesses significance of pronoun usage differences between community groups.

**Fisher's Exact Test**
Provides exact significance for binary categorical variables, especially useful for sparse data.

**Cosine Similarity**
```
Cosine Similarity = (A · B) / (||A|| × ||B||)
```
Measures directional alignment of pronoun patterns regardless of magnitude.

**Jaccard Similarity**
```
Jaccard Similarity = Σmin(Aᵢ, Bᵢ) / Σmax(Aᵢ, Bᵢ)
```
Emphasizes proportional overlap in pronoun usage between communities.

## Project Structure

```
reddit-text-analytics/
├── README.md
├── LICENSE
├── data/
│   ├── raw/
│   │   ├── books-og.csv
│   │   ├── changemyview-og.csv
│   │   ├── mentalhealth-og.csv
│   │   ├── relationships-og.csv
│   │   └── ... (other subreddits)
│   └── processed/
│       ├── *-cleaned.csv
│       ├── *-frequency.csv
│       └── * (other processed files)
├── scripts/
│   ├── reddit_scraper.py
│   ├── text_preprocessing.py
│   ├── pronoun_analysis.py
│   ├── linguistic_features.py
│   ├── statistical_tests.py
│   └── similarity_metrics.py
├── analysis/
│   ├── pronoun_results.csv
│   ├── statistical_results.csv
│   ├── similarity_results.csv
│   └── linguistic_features_results.csv
├── visualizations/
│   ├── pronoun_comparison.png
│   ├── chi_square_results.png
│   ├── similarity_metrics.png
│   └── linguistic_features.png
└── paper/
    └── Language_Identity_Polarization_Reddit_Analysis.pdf
```

## Installation & Usage

### Prerequisites
```bash
Python 3.8+
pip package manager
```

### Dependencies
```bash
pip install praw
pip install nltk
pip install pandas
pip install numpy
pip install scipy
pip install matplotlib
pip install seaborn
```

### Setup

1. **Clone the Repository**
```bash
git clone https://github.com/yourusername/reddit-text-analytics.git
cd reddit-text-analytics
```

2. **Install Dependencies**
```bash
pip install -r requirements.txt
```

3. **Configure Reddit API Credentials**
- Visit https://www.reddit.com/prefs/apps
- Create a new application (select "script")
- Note your credentials (client_id, client_secret, user_agent)
- Create `config.py` with:
```python
REDDIT_CLIENT_ID = "your_client_id"
REDDIT_CLIENT_SECRET = "your_client_secret"
REDDIT_USER_AGENT = "your_user_agent"
```

### Running Analysis

1. **Scrape Reddit Data**
```bash
python scripts/reddit_scraper.py --subreddit mentalhealth --limit 1000
```

2. **Preprocess Text**
```bash
python scripts/text_preprocessing.py --input data/raw/mentalhealth-og.csv
```

3. **Analyze Pronouns**
```bash
python scripts/pronoun_analysis.py --input data/processed/mentalhealth-cleaned.csv
```

4. **Extract Linguistic Features**
```bash
python scripts/linguistic_features.py --input data/processed/mentalhealth-cleaned.csv
```

5. **Run Statistical Tests**
```bash
python scripts/statistical_tests.py --category Politics --compare MentalHealth_Life
```

6. **Calculate Similarity Metrics**
```bash
python scripts/similarity_metrics.py --groups all
```

## Key Results Summary

### Pronoun Usage Patterns

| Community Type | Inclusive | Exclusive | First-Person | Pattern |
|----------------|-----------|-----------|--------------|---------|
| Mental Health | 2.1 | 1.4 | 7.8 | Introspective |
| Politics | 6.0 | 1.5 | 1.4 | Group-aligned |
| Discussion | 4.2 | 1.2 | 2.1 | Balanced |
| Hobbies | 2.1 | 1.3 | 3.2 | Informative |

### Statistical Significance

- **Highest Chi-square**: Politics vs. Mental Health Life (χ² > 60)
  - Indicates statistically significant differences in pronoun usage
  
- **Politics vs. Discussion**: χ² ≈ 0
  - Linguistically indistinguishable pronoun patterns

### Linguistic Feature Highlights

**Mental Health Communities:**
- Emotional language: 5.9/1,000 words
- Polite expressions: 2.9/1,000 words
- Lexical diversity: 0.56 (highest)
- Questions per 1,000: 1.5

**Political Communities:**
- Assertive language: 4.8/1,000 words
- Rude expressions: 1.6/1,000 words
- Lexical diversity: 0.48 (lowest)
- Questions per 1,000: 0.6

## Research Questions & Answers

**RQ1**: Do ideological subreddits use significantly fewer exclusive pronouns relative to inclusive pronouns than support subreddits?
-  Yes. Political communities show 6.0x inclusive vs 1.5x exclusive (ratio 4:1), while Mental Health shows 2.1x inclusive vs 1.4x exclusive (ratio 1.5:1)

**RQ2**: How does first-person singular pronoun frequency differ between ideological and support communities?
-  Substantially. Mental Health: 7.8/1,000 vs Politics: 1.4/1,000 (5.5x higher in support communities)

**RQ3**: How do linguistic style features vary across subreddit categories?
-  Significantly. Mental Health emphasizes emotion/politeness; Politics emphasizes assertiveness/rudeness; Discussion/Hobbies balance approaches

## Technologies Used

- **Web Scraping**: PRAW (Python Reddit API Wrapper)
- **NLP**: NLTK (Natural Language Toolkit)
- **Data Processing**: Pandas, NumPy
- **Statistical Analysis**: SciPy
- **Visualization**: Matplotlib, Seaborn
- **Data Storage**: CSV, JSON

## Future Work

1. **Advanced NLP**
   - Transformer-based models (BERT, RoBERTa) for sentiment analysis
   - Topic modeling (LDA, NMF)
   - Named Entity Recognition (NER)

2. **Temporal Analysis**
   - Track linguistic change over time
   - Analyze impact of external events on community discourse
   - Study user behavior evolution

3. **Multimodal Integration**
   - User metadata analysis (posting frequency, karma patterns)
   - Upvote/downvote dynamics
   - Temporal activity patterns
   - User interaction networks

4. **Polarization Studies**
   - Measure community cohesion metrics
   - Track echo chamber effects
   - Analyze cross-community linguistic divergence

5. **Expanded Scope**
   - Additional social media platforms (Twitter, Facebook, Discord)
   - Non-English communities
   - Real-time streaming analysis

## References

Key citations in research:
- Liu, B. (2014). Sentiment Analysis and Opinion Mining. Cambridge University Press.
- Bamman, D., Eisenstein, J., & Schnoebelen, T. (2014). Gender identity and lexical variation in social media.
- Garten, J., et al. (2019). Dictionaries and distributions: Combining expert knowledge and large scale textual data content analysis.
- An, J., Kwak, H., & Ahn, Y.-Y. (2021). Emotional contagion and linguistic divergence in polarized online communities.

See paper for complete references.

## License

This project is licensed under the MIT License - see LICENSE file for details.

## Ethical Considerations

- Data sourced from Reddit's public API with proper authentication
- No personal user information retained beyond pseudonymized comment data
- Analysis respects Reddit's Terms of Service
- Research conducted for academic purposes
- No user profiling or tracking beyond linguistic analysis

