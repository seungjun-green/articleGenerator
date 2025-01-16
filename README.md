# Llama Fine-Tuning on SQuAD Dataset

This repository provides a streamlined solution for fine-tuning Llama models on the SQuAD (Stanford Question Answering Dataset). The implementation is modular, enabling easy integration and usage.

---

## 🚀 Features

- Fine-tune Llama models efficiently.
- Designed for SQuAD Dataset out-of-the-box.
- Modular structure for seamless integration into your workflow.

---

## 📋 How to Use This Repository

### 1. Clone the Repository

```bash
git clone https://github.com/seungjun-green/llama-finetuning.git
cd llama-finetuning
```

### 2. Import Required Modules

```python
import sys
sys.path.append("/content/llama-finetuning")
from models.base_model import load_base_model
from scripts.train import fine_tune
```

### 3. Load the Base Model and Tokenizer

```python
tokenizer, model = load_base_model("meta-llama/Llama-3.2-1B")
```

### 4. Fine-Tune the Model

```python
fine_tune(model,
          tokenizer,
          config_path='/content/config.json',
          train_file_path="/content/train-v1.1.json",
          dev_file_path="/content/dev-v1.1.json")
```

---

## 📂 Config Structure
```bash
{
    "base_model_name": "meta-llama/Llama-3.2-1B",
    "lora_rank": 8,
    "lora_alpha": 16,
    "learning_rate": 1e-4,
    "batch_size": 16,
    "max_seq_length": 512,
    "num_epochs": 3,
    "output_dir": "./fine_tuned_checkpoints",
    "log_steps": 1000,
    "device": "cuda",
    "use_fp16": false,
    "warmup_ratio": 0.5,
    "train_file_path": "",
    "dev_file_path": ""
}
```

---
## 📂 Directory Structure

```
llama-finetuning/
├── configs/
│   ├── __init__.py
│   ├── llama-3.2-1B_lora_finetune.json # Configuration for fine-tuning
│   ├── squad_config.py
├── data/
│   ├── __init__.py
│   ├── squad_data.py  # Data preprocessing for SQuAD
│   ├── fine_tuned_checkpoints/ # Directory for storing checkpoints
├── models/
│   ├── __init__.py
│   ├── base_model.py  # Code for loading base Llama models
│   ├── lora.py        # LoRA (Low-Rank Adaptation) implementation
│   ├── loss.py        # Loss functions for fine-tuning
├── scripts/
│   ├── eval.py        # Script for evaluating fine-tuned models
│   ├── train.py       # Fine-tuning script
├── utils/
│   ├── __init__.py
│   ├── checkpoint.py  # Utilities for saving/loading checkpoints
│   ├── helpers.py     # Helper functions
│   ├── keys.py        # Key management for models and APIs
```

---

## 🔮 Future Plans

While the current implementation focuses on fine-tuning with the SQuAD Dataset, we plan to expand its capabilities, including:

- Support for additional datasets (e.g., text classification, summarization, etc.).
- Compatibility with other Llama model variants.
- Enhanced training utilities for distributed and large-scale fine-tuning.

---

## 🛠 Requirements

- Python 3.8+
- PyTorch
- Transformers Library
- SQuAD Dataset JSON files (`train-v1.1.json` and `dev-v1.1.json`)

Install dependencies using:

```bash
pip install -r requirements.txt
```

---

## 🤝 Contributions

Contributions are welcome! Feel free to open an issue or submit a pull request for suggestions, bug fixes, or new features.

---

Happy fine-tuning! 🎉

