# Measuring-Information-Entropy-in-Hierarchical-Ultra-long-Novel-Generation

# 📚 Project: Novel LLM Pipeline

A complete multi-stage pipeline for analyzing, expanding, compressing, and evaluating long-form novels using LLMs such as Gemini, OpenAI, or OpenRouter.

---

## 📁 Directory Structure & File Purpose

```
project/
├── /content/novel/                # Input folder for raw `.txt` novels (Colab path)                          # Input folder with raw novels (.txt)
├── novel_normalization.ipynb      # Preprocessing and cleaning of novel text
├── novel_analysis.ipynb           # Text structure analysis and statistics
├── Translate-Reconstruct.ipynb    # Translation and paragraph reconstruction
├── two_stage_compression.ipynb    # Step 1: compress -> Step 2: global outline
├── two_stage_compression-globaloutline.ipynb  # Follow-up summarization/compression
├── two_stage_expansion.ipynb      # Expand outline into full passages
├── two_stage_expansion-novel.ipynb# Final expansion into long-form chapters
├── longwriter.ipynb               # High-quality longform generation
├── evaluation.ipynb               # LLM-based evaluation of generated content
├── evaluation-Copy1.ipynb         # Evaluation variant (e.g. for ablation)
├── 1000_word_expansion.ipynb      # Experimental short expansion (1K words)
├── 1000_word_outline.ipynb        # Outline planning version for 1K target
├── 10000_word_expansion.ipynb     # Full expansion to 10K+ length output
├── 10000_word_outline.ipynb       # Planning and scaffolding for 10K writing
```

---

## 🧩 Pipeline Stages

### 1. **Input Preparation**

* Place `.txt` novel files in `/content/novel` if using Colab (or `data/` if local)
* Ensure encoding is UTF-8 (you can use a `GB18030 ➔ UTF-8` batch converter if needed)

### 2. **Text Normalization**

`novel_normalization.ipynb`

* Removes special symbols, blank lines
* Filters short/low-quality texts
* Output: Cleaned `.txt` files

### 3. **Novel Analysis**

`novel_analysis.ipynb`

* Analyzes model evaluation results rather than raw novels
* Aggregates scores from `evaluation.ipynb` outputs
* Visual/textual summaries (e.g., coherence, creativity distributions)

### 4. **Translate & Reconstruct**

`Translate-Reconstruct.ipynb`

* Optional translation step (ZH ➔ EN)
* Can include paragraph smoothing & alignment
* Output: token-aligned, cleaned paragraphs

### 5. **Two-Stage Compression**

`two_stage_compression.ipynb`

* Stage 1: Paragraph compression
* Stage 2: Chapter/section summarization

`two_stage_compression-globaloutline.ipynb`

* Further compresses entire book into outlines for control
* Output: Hierarchical outline JSON/markdown

### 6. **Two-Stage Expansion**

`two_stage_expansion.ipynb`

* Expands section summaries into full paragraphs

`two_stage_expansion-novel.ipynb`

* Expands to full novel-length passages
* Uses style conditioning, coherence chaining

### 7. **Longwriter**

`longwriter.ipynb`

* Implements a reproduction of a public baseline method for longform generation
* Uses predefined outline + example-driven in-context learning
* Aims to benchmark model behavior for high-quality structured continuation

### 8. **Evaluation**

`evaluation.ipynb`

* Runs automated LLM evaluation on generated outputs
* Criteria: relevance, coherence, fluency, creativity

`evaluation-Copy1.ipynb`

* Variation with different scoring models or prompts

### 9. **Experimental Expansion/Outline**

`1000_word_expansion.ipynb`

* LLM-based generation of concise 1K-word narrative from prompts or outline

`1000_word_outline.ipynb`

* Planning and skeleton outline for short-format content

`10000_word_expansion.ipynb`

* Longform expansion targeting 10K+ words based on prior structure

`10000_word_outline.ipynb`

* Framework for detailed 10K-length novel outline, suitable for creative control

---

## ⚙️ Usage Guide

1. Upload your `.txt` novels to `/content/novel/`
2. Run the notebooks in your order.
3. Ensure LLM API keys are set via `os.environ` or manually passed in prompts (e.g., Gemini, OpenAI)

### 🔐 API Keys Format

```python
os.environ["OPENAI_API_KEY"] = "your-key"
```
