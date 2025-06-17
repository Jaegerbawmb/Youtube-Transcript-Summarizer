# Youtube-Transcript-Summarizer

This project provides a Python script to summarize YouTube video transcripts using various summarization techniques: NLTK's TextRank, Pegasus, BART, and T5 models.


YouTube Transcript Extraction: Fetches the transcript of a given YouTube video URL.


Multiple Summarization Methods:

NLTK TextRank: An unsupervised graph-based ranking algorithm for text summarization.
Pegasus: A transformer-based model known for abstractive summarization.
BART: A denoising autoencoder for pretraining sequence-to-sequence models, effective for summarization.
T5: A "Text-to-Text Transfer Transformer" that frames all NLP tasks as a text-to-text problem, including summarization.


Setup:

Save the Youtube_Transcript_Summarizer.ipynb file.
Install the required libraries: nltk, youtube-transcript-api, transformers, and torch.
Download NLTK data: The script will automatically attempt to download punkt and stopwords.


Usage:

The core logic is within the provided Jupyter Notebook (Youtube_Transcript_Summarizer.ipynb). You can run the cells sequentially to install dependencies, import libraries, define functions, load pre-trained models, and generate summaries.
To use, modify the youtube_url variable in the last code cell of the notebook with the desired YouTube video URL.


Functions:

extract_video_id(youtube_url): Extracts the video ID from a given YouTube URL.
get_youtube_transcript(youtube_url): Fetches the transcript of a YouTube video using its URL.
textrank_summarize(text, summary_length=1): Summarizes text using the TextRank algorithm, where summary_length determines the number of top sentences to return.
summarize_text(tokenizer, model, text): A general function to summarize text using Hugging Face transformer models (like Pegasus and BART).
t5_summarize(text, max_length=100): Summarizes text using the T5 model, handling longer texts by chunking.


Models Used:

Pegasus: google/pegasus-large
BART: sshleifer/distilbart-cnn-12-6
T5: t5-small


Notes:

For transformer-based models (Pegasus, BART, T5), summarization quality can vary based on input text length and the model's capabilities.
Longer videos/transcripts might result in more generalized summaries.
The T5 summarization includes a basic chunking mechanism for texts longer than the model's maximum input length.
A stable internet connection is required to download models and fetch transcripts.
