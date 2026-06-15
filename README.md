# Basic Language Model

An n-gram language model trained on weather report text, with a Gradio chat interface for interactive text generation.

## How it works

The model builds n-gram frequency tables (up to 5-grams by default) from a training corpus. To predict the next token, it looks up the longest matching context it has seen, falling back to shorter n-grams and finally unigrams if needed. This is called **backoff**.

Text generation works by repeatedly predicting and appending the next token to the growing sequence.

Perplexity is computed on a held-out test set (last 10% of the corpus) using add-1 (Laplace) smoothing for unseen tokens.

## Requirements

```bash
pip install gradio numpy
```

## Run

```bash
python basic_language_model.py
```

Open the local URL printed in your terminal (e.g. `http://127.0.0.1:7860`) in your browser. Type a weather-related prompt and the model will continue it.

## Files

| File | Description |
|------|-------------|
| `basic_language_model.py` | N-gram model: training, prediction, perplexity, Gradio UI |
| `data/weather_data.txt` | Training corpus of weather report text |

## Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| `n_params` | `5` | Maximum n-gram order |

90% of the corpus is used for training, 10% for evaluation.
