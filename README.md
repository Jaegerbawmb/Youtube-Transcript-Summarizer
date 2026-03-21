# YouTube Transcript Summarizer

A Python notebook that fetches YouTube video transcripts and summarizes them using multiple NLP techniques — from classical graph-based ranking to modern transformer models.

---

## Summarization Methods

| Method | Type | Model / Library |
|---|---|---|
| **TextRank** | Extractive | NLTK (unsupervised graph-based ranking) |
| **Pegasus** | Abstractive | `google/pegasus-large` |
| **BART** | Abstractive | `sshleifer/distilbart-cnn-12-6` |
| **T5** | Abstractive | `t5-small` |

---

## Setup

### 1. Download the Notebook

Save `Youtube_Transcript_Summarizer.ipynb` to your working directory.

### 2. Install Dependencies

```bash
pip install nltk youtube-transcript-api transformers torch
```

### 3. NLTK Data

The notebook will automatically download the required NLTK datasets (`punkt` and `stopwords`) on first run.

> **Note:** A stable internet connection is required to fetch transcripts and download transformer models.

---

## Usage

Open the notebook and run cells sequentially — they handle dependency installation, imports, model loading, and summary generation in order.

To summarize a specific video, update the `youtube_url` variable in the final code cell:

```python
youtube_url = "https://www.youtube.com/watch?v=your_video_id"
```

---

## Function Reference

| Function | Description |
|---|---|
| `extract_video_id(youtube_url)` | Parses and returns the video ID from a YouTube URL |
| `get_youtube_transcript(youtube_url)` | Fetches the full transcript of a YouTube video |
| `textrank_summarize(text, summary_length=1)` | Summarizes using TextRank; `summary_length` controls number of top sentences returned |
| `summarize_text(tokenizer, model, text)` | General-purpose summarizer for Hugging Face models (Pegasus, BART) |
| `t5_summarize(text, max_length=100)` | T5-based summarizer with chunking support for long transcripts |

---

## Notes

- **Long videos** may produce more generalized summaries due to input length constraints.
- **T5** includes a chunking mechanism to handle transcripts that exceed the model's maximum input length.
- Summarization quality varies by model and transcript length — transformer models generally produce more fluent, abstractive output than TextRank.
