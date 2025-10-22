# Polite or Threatening? How Prompt Tone Influences LLM Responses in Software Engineering
**Supplemental Materials for CHASE 2026 Submission**

This repository hosts the open research artifacts accompanying the manuscript:

> **“Polite or Threatening? How Prompt Tone Influences LLM Responses in Software Engineering”**  
> Anonymous Author(s), CHASE 2026 (under review)

The study examines how prompt tone (polite vs. threatening) influences the linguistic, affective, and safety-related behavior of four state-of-the-art Large Language Models (LLMs) across 60 software engineering (SE) tasks.  
All data, scripts, and documentation provided here enable full replication and secondary analysis.

---

## Repository Structure

📁 root/
├── Dataset_Documentation.txt
├── final_dataset.xlsx
├── Capstone Analysis-20250930T083101Z-1-001.zip
├── Statistical Analysis Scripts.zip
├── LICENSE
└── README.md


### 1. `final_dataset.xlsx`
The primary dataset used for all analyses, containing **480 LLM responses** (60 tasks × 2 tones × 4 models).  
Each record corresponds to one model’s answer to a specific SE task prompt.  
Metrics include verbosity, sentiment, politeness, safety flags, and toxicity probabilities.  
Detailed schema and feature definitions are described in [`Dataset_Documentation.txt`](./Dataset_Documentation.txt):contentReference[oaicite:2]{index=2}.

**Key Columns:**
- `TaskID`, `TaskDescription`, `PromptTone`, `Model`, `ResponseText`
- `ResponseLength`, `Response_SentimentScore`, `Response_ValidatedPolitenessScore`
- `Response_RefusalFlag`, `Response_DisclaimerFlag`
- `RoBERTa_Response_ToxicityScore`, `RoBERTa_Response_ThreatScore`, etc.

The dataset enables:
- **Paired analysis** (Polite vs. Threatening per task)
- **Cross-model comparisons** (GPT-4o, Gemini-2.5-Pro, Claude-Sonnet-4, DeepSeek-Chat)
- **Domain analyses** (Programming Help, Ethical Dilemmas, Writing, Policy Advice)

---

### 2. `Capstone Analysis-20250930T083101Z-1-001.zip`

This repository contains a comprehensive analysis of AI model responses to different prompt tones, split from a Jupyter notebook into modular, reusable Python scripts. It contains:

## 📈 Analysis Details

### 2.1 Basic Stripplot Analysis (`01_basic_stripplots/`)
**Purpose**: Foundational comparison of AI responses across four key metrics
- Creates 2x2 grid of stripplots
- Compares polite vs. threatening prompt responses
- **Generated**: `basic_stripplot_analysis.png`

### 2.2 Faceted Model Analysis (`02_faceted_by_model/`)
**Purpose**: Model-specific response patterns over time/tasks
- Separate line plots for each AI model
- Shows trends across task numbers
- **Generated**: 4 PNG files (sentiment, toxicity, politeness, response length by model)

### 2.3 Categorical Distributions Analysis (`03_categorical_distributions/`)
**Purpose**: Transforms continuous metrics into interpretable categories
- VADER sentiment categories (Negative/Neutral/Positive)
- RoBERTa toxicity levels (Very Low to Very High)
- Politeness categories (Very Impolite to Very Polite)
- **Generated**: `categorical_distributions_analysis.png`

### 2.4 Paired Comparison Analysis (`04_paired_comparison/`)
**Purpose**: Direct comparison of responses to identical tasks with different prompt tones
- Scatter plots with diagonal reference lines
- Emphasizes experimental paired design
- **Generated**: `paired_comparison_analysis.png`

### 2.5 Politeness Strategy Analysis (`05_politeness_strategies/`)
**Purpose**: Examines specific politeness strategies used in responses
- Bar charts of strategy frequency by prompt tone
- Identifies most common politeness mechanisms
- **Generated**: `politeness_strategy_analysis.png`

### 2.6 Raincloud Distributions Analysis (`07_raincloud_distributions/`)
**Purpose**: Statistical testing combined with comprehensive distribution visualization
- Paired t-tests for statistical significance
- Raincloud plots (strip + violin + box plots)
- **Generated**: `raincloud_distributions.png`

### 2.7 Cross-Context Analysis (`08_cross_context_analysis/`)
**Purpose**: Compare sensitivity across different AI models and task categories
- Point plots with confidence intervals
- Model and task category sensitivity rankings
- **Generated**: `cross_context_analysis.png`

### 2.8 Safety Behavior Analysis (`09_safety_behaviors/`)
**Purpose**: Analyzes potential AI safety and defensive behaviors
- Examines response length, toxicity, and sentiment as safety indicators
- Identifies potential refusal or cautious behavior patterns
- **Generated**: `safety_behavior_analysis.png`

### 2.9 Model Comprehensive Analysis (`12_model_comprehensive/`)
**Purpose**: In-depth model-specific analysis across four dimensions
- Sentiment category distributions by model
- Toxicity proportions by model
- Politeness metrics and feature counts by model
- Top politeness strategy usage by model
- **Generated**: 4 PNG files (sentiment, toxicity, politeness, strategies by model)

### 2.10 Task Comprehensive Analysis (`13_task_comprehensive/`)
**Purpose**: In-depth task-category-specific analysis across four dimensions
- Sentiment category distributions by task type
- Toxicity proportions by task type
- Politeness metrics and feature counts by task type
- Top politeness strategy usage by task type
- **Generated**: 4 PNG files (sentiment, toxicity, politeness, strategies by task)

### 2.11 Response Length Analysis (`14_response_length/`)
**Purpose**: Detailed analysis of response verbosity patterns
- Statistical testing of length differences
- Model-specific length patterns
- **Generated**: `response_length_analysis.png`

## 🔧 Technical Details

### Dependencies
- pandas
- matplotlib
- seaborn
- scipy (for statistical tests)
- numpy

### Features
- **Non-interactive plotting**: Uses Agg backend for headless execution
- **Modular design**: Shared utilities in `shared/` directory
- **Error handling**: Comprehensive error checking and reporting
- **Statistical analysis**: Includes t-tests, effect sizes, and descriptive statistics

### File Structure
Each analysis directory contains:
- `*.py`: Main analysis script
- `README.md`: Detailed explanation of the analysis
- `*.png`: Generated visualization files


## 🎯 Usage Scenarios

1. **Academic Research**: Understanding AI behavior under different prompt conditions
2. **Safety Evaluation**: Assessing AI robustness to adversarial prompts
3. **Model Comparison**: Benchmarking different AI models' behavioral patterns
4. **Prompt Engineering**: Informing best practices for prompt design

## 📝 Documentation

Each analysis directory contains detailed README files explaining:
- Purpose and methodology
- Visualization interpretation
- Expected patterns and research questions
- Files generated and their meaning

## 🔬 Statistical Rigor

- **Paired Design**: Utilizes the paired nature of the experimental design
- **Effect Sizes**: Includes Cohen's d for practical significance
- **Multiple Metrics**: Comprehensive behavioral assessment
- **Model Comparison**: Systematic comparison across AI systems

---

**Generated from Jupyter notebook**: `capstone_expirement_graphs.ipynb`
**Dataset**: `final_dataset.csv`
**Total Analyses**: 11 completed successfully
**Generated Visualizations**: 21 PNG files


---

### 3. `Statistical Analysis Scripts.zip`
  This folder contains 15 Python scripts. They can be run in the same order. We used Google Co-lab to run the scripts. Whe nprompted, please upload the final_dataset.xls file.

All scripts are modular, well-commented, and directly callable from notebooks or command line.

---

### 4. `Dataset_Documentation.txt`
Comprehensive schema reference explaining every variable, its computation, and validation approach.  
Includes:
- Computational politeness features (based on Brown & Levinson, 1987; Danescu-Niculescu-Mizil et al., 2013)
- Sentiment scoring using VADER
- Safety indicators (refusals, disclaimers)
- Toxicity metrics using Unitary RoBERTa (Detoxify library)
- Planned human evaluation metadata structure (accuracy, helpfulness, tone perception)

---

## Reproduction Environment

### Requirements
```bash
Python >= 3.10
pandas >= 2.2
numpy >= 1.26
scipy >= 1.13
statsmodels >= 0.14
matplotlib >= 3.9
nltk >= 3.9
detoxify >= 0.6
vaderSentiment >= 3.3

Setup
git clone https://github.com/<username>/threatening-llms.git
cd threatening-llms
pip install -r requirements.txt

Running the Analysis
# Run core statistics
python Statistical\ Analysis\ Scripts/paired_tests.py
# Launch Jupyter for figure replication
jupyter notebook Capstone\ Analysis/Exploratory_Analysis.ipynb

## Research Summary

Study Design: Within-task paired experiment comparing polite vs. threatening prompt variants across four LLMs.

Sample: 60 SE tasks × 4 models × 2 tones = 480 total responses.

Measures: Verbosity, sentiment, politeness, refusals, disclaimers, and toxicity.

### Key Findings:

Polite prompts produced longer, warmer responses (+18% length, +0.25 sentiment).

Threatening tone shortened replies but did not compromise safety.

Effects were domain-dependent and model-specific—most pronounced in ethical tasks.

GPT-4o exhibited strongest tone stability; DeepSeek showed the largest sentiment shifts.

Safety behaviors and toxicity remained unaffected by tone.

Full interpretation and discussion appear in the main manuscript
