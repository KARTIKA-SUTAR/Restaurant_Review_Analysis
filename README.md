# 📝 Text Generation with Transformers (FLAN-T5)

A hands-on project demonstrating how to use a pre-trained **transformer model** — Google's **FLAN-T5** — to generate natural-language text from instruction-style prompts, using the Hugging Face `transformers` library and PyTorch.

![Text Generation Pipeline](assets/workflow_diagram.png)

---

## 📌 Overview

This project walks through the full text-generation pipeline end-to-end:

- Loading a pre-trained instruction-tuned transformer (**FLAN-T5**) and its tokenizer
- Tokenizing raw text into model-readable input
- Running inference to generate output tokens
- Decoding tokens back into human-readable text
- Wrapping the pipeline into a single reusable function
- Comparing outputs across prompts to explore how **prompt design** affects response quality

## 🎯 Objective

To build a clear, minimal, and reusable example of a transformer-based text-generation workflow, and to illustrate — through a series of test prompts — how instruction phrasing and added context materially change model output quality.

## 🔁 Project Workflow

| Step | Description |
|------|-------------|
| 1. Install Dependencies | Install the `transformers` library |
| 2. Load Model & Tokenizer | Load `google/flan-t5-large` and its tokenizer from the Hugging Face Hub |
| 3. Define Input Prompt | Write the natural-language instruction/question |
| 4. Tokenize Input | Convert text into numeric token IDs |
| 5. Generate Output Tokens | Run model inference to produce output token IDs |
| 6. Decode to Text | Convert output token IDs back into readable text |
| 7. Final Output | Reusable `generate_response()` function returns the generated text |

## 🛠️ Tech Stack

- **Python 3**
- [Hugging Face Transformers](https://huggingface.co/docs/transformers)
- **PyTorch**
- **Model:** [`google/flan-t5-large`](https://huggingface.co/google/flan-t5-large)

## 📂 Repository Structure

```
├── Text_Generation_with_Transformers.ipynb   # Main notebook
├── assets/
│   └── workflow_diagram.png                  # Project workflow diagram
├── requirements.txt                          # Python dependencies
└── README.md
```

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebook
```bash
jupyter notebook Text_Generation_with_Transformers.ipynb
```

> 💡 A GPU is not required, but will significantly speed up generation.

## 💬 Example

**Prompt:**
> "List the steps to prepare lasagna."

**Generated Response:**
> A step-by-step list of lasagna preparation instructions, generated entirely by the model from the natural-language prompt above (see the notebook for the live output).

## 🔍 Key Takeaway

Output quality depends heavily on **prompt design**. Vague prompts can lead the model off-topic, while specific, context-rich prompts guide it toward accurate, relevant responses — the foundation of *prompt engineering* when working with instruction-tuned LLMs.

## 📄 License

This project is intended for educational and portfolio purposes.
