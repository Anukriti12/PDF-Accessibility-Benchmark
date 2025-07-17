# PDF Accessibility Benchmark Dataset

**The first comprehensive benchmark dataset for evaluating PDF accessibility across multiple criteria with expert-validated annotations.**


## Overview

This repository contains a benchmark dataset of **125 PDF documents** with expert-validated accessibility annotations across **7 key accessibility criteria** aligned with WCAG 2.2 and PDF/UA standards. The dataset enables systematic evaluation of automated accessibility checkers, LLM-based evaluation approaches, and hybrid assessment frameworks.

## Accessibility Criteria

| Criterion | Description | WCAG 2.2 Alignment | Documents |
|-----------|-------------|-------------------|-----------|
| **Alternative Text Quality** | Quality and appropriateness of image descriptions | 1.1.1 Non-text Content | 20 docs |
| **Color Contrast** | Sufficient contrast ratios for text and elements | 1.4.3, 1.4.6 Contrast | 15 docs |
| **Font Readability** | Font accessibility including size and style | 1.4.4, 1.4.8, 1.4.12 | 15 docs |
| **Functional Hyperlinks** | Link accessibility and descriptiveness | 2.4.4, 2.4.9 Link Purpose | 20 docs |
| **Logical Reading Order** | Document structure and reading sequence | 1.3.1, 1.3.2 Sequence | 15 docs |
| **Semantic Tagging** | Proper semantic markup and structure | 1.3.1 Relationships | 20 docs |
| **Table Structure** | Table accessibility with headers and relationships | 1.3.1 Relationships | 20 docs |


### Basic Usage

```python

import os
import json

# Get all documents for a criterion
def get_criterion_documents(criterion):
    documents = []
    criterion_path = f"data/inputs/{criterion}"
    for label in ['passed', 'failed', 'not_present', 'cannot_tell']:
        label_path = os.path.join(criterion_path, label)
        if os.path.exists(label_path):
            documents.extend([
                {'path': os.path.join(label_path, d), 'label': label}
                for d in os.listdir(label_path) 
                if os.path.isdir(os.path.join(label_path, d))
            ])
    return documents
```

### Accessibility Labels

- **Passed** (P): Document fully meets accessibility requirements
- **Failed** (F): Document has clear accessibility violations  
- **Not Present** (NP): Accessibility feature is not applicable
- **Cannot Tell** (CT): Insufficient information to determine compliance


## 🛠️ Pipeline Scripts and Tools

**Coming Soon**: We are currently developing comprehensive pipeline scripts and Jupyter notebooks that will be added to this repository shortly. These will include:

- **Data Loading Utilities** (`scripts/data_loader.py`)
- **LLM Evaluation Framework** (`scripts/llm_evaluator.py`)
- **Interactive Jupyter Notebooks** (`scripts/notebooks/`)
- **Requirements File** (`requirements.txt`)

These tools will provide:
- Easy dataset navigation and loading
- Standardized evaluation metrics computation
- Integration with popular accessibility checkers
- LLM-based evaluation pipelines
- Comparison frameworks for different approaches
- Comprehensive documentation and examples

**Check back soon for updates!**

## LLM Evaluation

### Supported Models

- **GPT-4-Turbo**: Text-based accessibility analysis
- **GPT-4o-Vision**: Visual accessibility evaluation  
- **Claude-3.5**: Document structure assessment
- **Gemini-1.5**: Multimodal accessibility analysis
- **Llama-3.2**: Open-source accessibility evaluation


## Baseline Results

### LLM Performance (Average Accuracy)

| Model | Overall | Alt Text | Color | Fonts | Links | Reading | Semantic | Tables |
|-------|---------|----------|-------|-------|-------|---------|----------|--------|
| GPT-4-Turbo | **0.85** | 0.70 | 0.93 | 1.00 | 0.80 | 0.67 | 0.85 | 1.00 |
| GPT-4o-Vision | 0.81 | 0.50 | **1.00** | 0.93 | 0.75 | **0.87** | 0.85 | 0.75 |
| Claude-3.5 | 0.74 | 0.50 | 0.67 | 0.73 | 0.80 | **1.00** | **0.90** | 0.55 |
| Gemini-1.5 | 0.75 | 0.50 | 0.60 | **1.00** | **0.85** | 0.93 | 0.80 | 0.55 |
| Llama-3.2 | 0.42 | 0.40 | 0.53 | 0.47 | 0.50 | 0.27 | 0.35 | 0.45 |

### Automated Tools Comparison

| Tool | Coverage | Speed | Accuracy | False Positives |
|------|----------|-------|----------|----------------|
| Adobe Acrobat Pro | High | Fast | Medium | Low |
| PAC 2024 | Very High | Medium | High | Medium |
| axesPDF | High | Fast | Medium | High |
| CommonLook | Very High | Slow | High | Low |

### Key Files and Their Purpose

| File Type | Purpose | Example |
|-----------|---------|---------|
| `*.pdf` | Source PDF documents | `W2460269320_0.pdf` |
| `*.html` | HTML conversions for analysis | `W2460269320_0.html` |
| `*.png` | Full page renderings | `W2460269320_0.png` |
| `*.jpg` | Figure/table extractions | `W2460269320_0#0.jpg` |
| `*.txt` | Text content and alt text | `W2460269320_0#0.txt` |
| `*.json` | Structured metadata | `W2904322054.json` |
| `*.zip` | Document packages | `W2772922866.zip` |
| `structuredData.json` | Document structure data | Various documents |

### Academic Fields Covered

- **Computer Science**: HCI, software engineering, machine learning
- **Medicine**: Clinical research, medical imaging, healthcare informatics  
- **Biology**: Molecular biology, genetics, ecological studies
- **Physics**: Theoretical physics, experimental studies
- **Chemistry**: Organic chemistry, materials science
- **Engineering**: Civil, mechanical, electrical engineering
- **Mathematics**: Pure mathematics, applied mathematics, statistics


## License
This dataset is released under the [MIT License](LICENSE). Please cite our paper when using this dataset in your research.

## Contact
**Anukriti Kumar** - anukriti@uw.edu - University of Washington

**Citation**: If you use this dataset in your research, please cite our ASSETS '25 paper (full citation coming soon).
