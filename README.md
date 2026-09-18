# Restaurant Review Sentiment Analysis with Mistral-7B

LLM-powered sentiment analysis of restaurant reviews using prompt engineering — overall sentiment, aspect-level breakdown, feature extraction, and auto-generated customer responses, built on Mistral-7B-Instruct.

## Overview

An end-to-end sentiment analysis pipeline for restaurant reviews, built entirely with **prompt engineering** — no fine-tuning, no RAG — on top of the open-source **Mistral-7B-Instruct-v0.1** model, run locally via Hugging Face.

## Features

- **Overall sentiment** — classifies each review as Positive, Negative, or Neutral
- **Aspect-level sentiment** — breaks sentiment down by Food Quality, Service, and Ambience
- **Feature extraction** — pulls out the specific things customers liked or disliked within each aspect
- **Auto-generated responses** — drafts a tone-appropriate reply to the customer for every review

## Tech Stack

- Python, pandas
- Hugging Face `transformers`, `accelerate`, `bitsandbytes` (8-bit quantized model loading)
- `mistralai/Mistral-7B-Instruct-v0.1`

## Dataset

20 restaurant reviews (`restaurant_reviews.csv`) with three columns:

| Column | Description |
|---|---|
| `restaurant_ID` | Unique restaurant identifier |
| `rating_review` | Numeric rating (1–5) |
| `review_full` | Full text of the customer review |

## Project Structure

```
├── Restaurant_Review_Analysis_Notebook.ipynb   # Main notebook
├── restaurant_reviews.csv                      # Dataset (add your own)
└── README.md
```

## Setup

1. Clone the repo and open the notebook (a GPU runtime is required, e.g. Google Colab).
2. Install dependencies:
   ```bash
   pip install transformers==4.53.2 accelerate==1.8.1 bitsandbytes==0.46.1 pandas torch
   ```
3. Get a Hugging Face access token with access to the gated `mistralai/Mistral-7B-Instruct-v0.1` model, and make it available to the notebook as `HF_TOKEN`.
4. Run the notebook cells sequentially.

## How It Works

1. **Load & inspect data** — read the CSV, check shape and missing values.
2. **Load the model** — Mistral-7B-Instruct loaded in 8-bit quantization for memory efficiency.
3. **Overall sentiment** — a single prompt classifies each review.
4. **Aspect-level sentiment** — a second prompt scores Food Quality, Service, and Ambience independently, returning `"Not Applicable"` when an aspect isn't mentioned.
5. **Feature extraction** — a third prompt pulls out the specific liked/disliked features behind each aspect's sentiment.
6. **Response generation** — a final prompt drafts a customer-facing reply, tone-matched to the review's sentiment.

## Key Findings

- Negative sentiment slightly outweighs positive and neutral overall (8 vs. 6 vs. 6).
- **Service** was the most criticized aspect (10 negative mentions).
- **Ambience** was the strongest positive driver (8 positive mentions).

## Notes

- The sample dataset is small (20 rows) and meant for demonstration; results are illustrative, not statistically robust.
- To evaluate model accuracy, manually label a subset of reviews and compare against the model's output.

## License

MIT
