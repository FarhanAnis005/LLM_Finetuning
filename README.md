# Assessing the Impact of QLoRA Fine-Tuning on Sub-10B LLMs 🚀

This repository contains the code, data, and benchmarks for the research paper: **"Assessing the Impact of QLoRA Fine-Tuning on Sub-10B Parameter LLMs for Reasoning and Fact Recall."**

## 📝 Overview

This project evaluates the impact of **QLoRA (Quantized Low-Rank Adaptors)** fine-tuning on seven state-of-the-art Large Language Models (LLMs) with fewer than 10 billion parameters. The study focuses on enhancing two key capabilities:

  * **Fact Recall** in the BioMedical domain 🩺
  * **Reasoning** in Math Word Problems 🔢

By leveraging computationally efficient techniques like 4-bit quantization and LoRA, we fine-tuned models such as **Llama 3.1, Mistral, and Gemma 2** on specialized datasets. Our findings highlight the trade-offs between a model's baseline performance, gains from fine-tuning, and potential for overfitting, offering insights for optimizing smaller LLMs for domain-specific tasks.

## 📊 Key Findings

  * **For Math Tasks 🧮:** **Llama 3.1** showed the most significant performance improvement, achieving the top score of 4.97 after three epochs of fine-tuning.
  * **For BioMedical Tasks 🧬:** **Mistral** and **Llama 3.1** demonstrated the most stability and consistency, making them reliable choices. Many models had strong baseline scores, and extended fine-tuning sometimes led to overfitting (e.g., Qwen, Gemma).
  * **Overfitting Risk ⚠️:** Models like **Qwen** and **Gemma 2** exhibited sensitivity to extended fine-tuning, with performance declining after the first epoch in some cases, indicating a risk of overfitting.

-----

## 🛠️ Methodology

### Models Tested

We selected seven state-of-the-art, sub-10B parameter models, using their 4-bit quantized versions from Unsloth.

1.  Llama 2 (7B)
2.  Llama 3 (8B)
3.  Llama 3.1 (8B)
4.  Gemma 1 (7B)
5.  Gemma 2 (9B)
6.  Mistral v3 (7.3B)
7.  Qwen 2 (7B)

### Datasets

  * **Orca-Math-200k**: Used for fine-tuning on mathematical reasoning tasks. We used the first 10,000 samples for training.
  * **BioInstruct**: A dataset with over 25,000 instructions for a wide range of biomedical NLP tasks. We used the first 10,000 samples for training.

### Fine-Tuning Process

  * **Frameworks**: We used **QLoRA** for memory-efficient fine-tuning combined with the **Unsloth** library for a 30x speedup and 60% memory reduction.
  * **Hardware**: Training was conducted on **Kaggle's T4 GPUs (16GB VRAM)**.
  * **Epochs**: Models were trained for an initial epoch, evaluated, and then fine-tuned for two additional epochs.

-----

## 📁 Repository Structure

```
.
├── Code/
│   ├── train_math.ipynb            # Jupyter notebook for training models on the Orca-Math dataset.
│   ├── train_bio.ipynb             # Jupyter notebook for training models on the BioInstruct dataset.
│   └── Automated_benchmarking.ipynb  # Notebook to run and evaluate all models.
│
├── Benchmarks/
│   ├── Base Model Benchmarks/      # Evaluation results for the original, non-finetuned models.
│   └── QLoRA Benchmarks/           # Evaluation results for the fine-tuned models (Epoch 1 & 3).
│
├── Benchmark Data/
│   ├── Llama-math.xlsx             # Human evaluation scores for Llama models on math tasks.
│   ├── Qwen-bio.xlsx               # Human evaluation scores for Qwen models on bio tasks.
│   └── ...                         # (And so on for all models and tasks).
│
└── Questions with solutions/
    ├── Maths_Benchmark.txt         # The set of questions used for evaluating math reasoning.
    └── bio_benchmark.txt           # The set of questions used for evaluating biomedical recall.
```

-----

## 🚀 How to Reproduce

1.  **Setup**: Ensure you have a suitable environment (like Kaggle or Google Colab with a T4 GPU).
2.  **Train Models**:
      * Run the `train_math.ipynb` notebook to fine-tune the models on the math dataset.
      * Run the `train_bio.ipynb` notebook to fine-tune the models on the biomedical dataset.
3.  **Evaluate Performance**:
      * Use the `Automated_benchmarking.ipynb` notebook to generate responses from both the base and fine-tuned models using the questions in the `Questions with solutions/` directory.
4.  **Analyze Results**: The raw model outputs are saved in the `Benchmarks/` directory, and the compiled human-rated scores are available in the `Benchmark Data/` spreadsheets.


  publisher={Institute of Engineering Management}
}
```
