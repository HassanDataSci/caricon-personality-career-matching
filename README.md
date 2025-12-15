# Machine Learning–Driven Personality-to-Career Matching

### Host Company: CARICON

**Challenge Advisors**

* Steve Russell — [srussell@cari-con.org](mailto:srussell@cari-con.org)
* Solomon Perkins — [falexson@gmail.com](mailto:falexson@gmail.com)

**AI Studio Coach**

* Audra Zook — [zook.audra@gmail.com](mailto:zook.audra@gmail.com), [alz43@cornell.edu](mailto:alz43@cornell.edu)

---

## 👥 Team Members

| Name                         | GitHub Handle  | Contribution                                          |
| ---------------------------- | -------------- | ----------------------------------------------------- |
| Jessica Tong                 | @jessicatong8  | Data exploration, EDA, documentation                  |
| Mythri Kishore               | @mkishore3     | Data preprocessing, feature engineering               |
| Muhammad Hassan Butt         | @HassanDataSci | Model development, evaluation, analysis               |
| Samphasnearyroth Chau (Nero) | @nerochau      | Analysis, modeling support, ethics & interpretability |
| Annabel Wen                  | —              | Logistics, analysis, results interpretation           |

---

## 🏗️ Project Overview

### Connection to Break Through Tech AI

This project was completed as part of the **Break Through Tech AI Studio program**, where interdisciplinary student teams collaborate with industry partners to design, build, and evaluate responsible AI solutions for real-world problems.

### About CARICON

CARICON promotes Caribbean literature globally by connecting authors with readers, industry professionals, and publishers.

* **Customers:** Authors, agents, publishers, producers, and those interested in Caribbean stories
* **Industry:** Global literary and cultural sector
* **Stakeholders:** CARICON leadership, recruiters, board members, and candidates who engage with CARICON programs

### Problem Statement

CARICON seeks to better understand how **personality traits align with career paths and roles** in creative and professional settings. The goal of this project is to explore whether machine learning can support *person–role matching* in a way that is ethical, interpretable, and culturally aware.

---

## 🎯 Project Highlights

* Built **unsupervised learning models** to cluster and group similar jobs, and **supervised learning models** to match personality traits to job categories.
* Identified **meaningful personality clusters** using unsupervised learning techniques.
* Evaluated multiple **classification models** and compared performance against baseline approaches.
* Integrated **ethical and interpretability considerations** to support human-centered, assistive hiring decisions.

---

## 📊 Data Exploration

### Datasets

- Personality assessment data (**O*NET and MBTI datasets**)
- Career/role-related outcome labels

**Dataset overview:**
- **MBTI dataset:** shape = **(8,675, 2)**  
  - Contains MBTI personality type labels and associated text data.
- **Human characteristics (O*NET) dataset:** shape = **(1,016, 30)**  
  - Represents job roles described by structured human-characteristic features.

**Data characteristics:**

- Mixed numerical and categorical features
- Sensitive attributes related to personal identity and preferences

---

### Preprocessing & EDA

- Data cleaning and validation (missing values, consistency checks)
- Feature normalization and encoding
- Exploratory analysis of feature distributions and correlations
- Identification of potential biases and imbalances

---

### Key Insights

- Certain personality dimensions show stronger alignment with specific role categories.
- Natural groupings emerge when clustering job roles and personality profiles, suggesting non-random structure.

---

### Challenges & Assumptions

- Personality data may be culturally dependent.
- Labels may reflect historical or systemic bias.
- Models are exploratory and **not prescriptive**.


---

## 🧠 Model Development

### Approaches Used

* **Unsupervised learning:** clustering job roles to identify latent job groupings based on shared characteristics
* **Supervised learning:** classification models to predict job matches from personality traits

### Modeling Details

* Text data transformed using **TF-IDF vectorization**.
* Proper train/validation/test splits applied to prevent leakage.
* Models evaluated using accuracy, per-class precision, recall, and F1 score.
* Class imbalance identified as a primary performance constraint.
* Baseline models established for comparison
* Feature selection informed by domain relevance and correlation analysis
* Hyperparameter tuning via cross-validation

### Training Setup

* Train/validation/test split
* Evaluation metrics chosen based on task (e.g., F1 score for class imbalance)

---

## 📈 Results & Key Findings

### Final MBTI Prediction Results

- **Logistic Regression** achieved **64.5% test accuracy**, making it the best-performing individual model.
- The **ensemble voting model** (Logistic Regression + Random Forest) achieved **61.4% test accuracy**, offering more stable but slightly lower performance.
- Stronger predictive performance was observed for **common MBTI types** (e.g., INFP, INFJ, INTP).
- **Lower recall** was consistently observed for **rare MBTI types** (e.g., ESFJ, ESTJ, ESFP), largely due to class imbalance.
- Classification reports reveal clear **per-type precision and recall trade-offs**, highlighting strengths and limitations across personality groups.

### Model Comparison

| Model               | Validation Accuracy | Test Accuracy | Strengths                                         | Limitations                                                       |
|--------------------|---------------------|---------------|---------------------------------------------------|------------------------------------------------------------------|
| Logistic Regression | 0.616               | **0.645**     | Fast and efficient for high-dimensional TF-IDF text | Linear decision boundary; weaker performance on rare classes     |
| Random Forest       | 0.551               | 0.582         | Captures non-linear patterns; robust to noise     | Poor performance on sparse TF-IDF features                       |
| Ensemble (Voting)   | —                   | 0.614         | More stable predictions; balances model strengths | Slightly below best individual model; rare-class recall remains low |

### Key Takeaways

- Linear models performed best on sparse, high-dimensional text representations.
- **Class imbalance significantly impacted recall** for underrepresented MBTI types.
- Ensemble methods improved prediction stability but did not outperform the strongest individual model.
- Performance disparities highlight the need for **class balancing techniques and expanded datasets**.

---

## ✅ Success Metrics

- **Model performance:** Accuracy, F1 score, AUROC *(task-dependent, multi-class where applicable)*
- **Business impact (potential):**
  - Faster and easier role-matching support
  - Improved candidate–role alignment insights
  - Potential contributions to improved retention and team dynamics

---

## ⚖️ Ethical Considerations

* Avoid bias against underrepresented personality types
* Account for cultural context in personality measurement
* Protect sensitive applicant data
* Ensure the system **assists rather than replaces** human judgment

---

## 👩🏽‍💻 Setup & Installation

This project was developed and run primarily using **Google Colab**, so no local installation is required.

### Option 1: Run in Google Colab (Recommended)

1. Open Google Colab: [https://colab.research.google.com/](https://colab.research.google.com/)

2. Select **File → Open notebook → GitHub**

3. Enter the repository name:

   ```
   caricon-personality-career-matching
   ```

4. Choose the desired notebook from the `notebooks/` directory.

5. Follow the setup cells at the top of each notebook to:

   * Mount Google Drive (for secure data access)
   * Install required Python packages

Example setup cell:

```python
from google.colab import drive
drive.mount('/content/drive')
```

### Option 2: Local Setup (Optional)

1. **Clone the repository**

   ```bash
   git clone https://github.com/<org-or-user>/caricon-personality-career-matching
   cd caricon-personality-career-matching
   ```

2. **Create and activate a virtual environment**

   ```bash
   python -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Run notebooks locally**

   ```bash
   jupyter notebook
   ```
---

## 🗂️ Repository Guide

This repository contains:

- Code for data preparation, modeling, and evaluation
- Google Colab–based development environment for exploratory analysis and prototyping
- Documentation, briefs, and reports

## 📁 Repository Structure
```
├── data/                  # Raw and processed datasets
├── CariCon_ML.ipynb       # Google Colab notebook for analysis and modeling
├── README.md              # Project overview, instructions, and documentation
└── requirements.txt       # Python dependencies and environment setup
```
---

## 🗓️ Workplan

**Milestones**

* **Sept 30:** Data Preprocessing and identify model ideas
* **Oct 31:** Baseline models and interpretability testing
* **Nov 30:** Final report delivery

**Tools**

* GitHub (private repository)
* Google Drive (secure data storage)
* Google Colab

---

## 🧩 Discussion & Reflection

### What Worked Well
- Linear models (Logistic Regression) performed strongly on sparse TF-IDF features.
- Unsupervised clustering revealed meaningful job groupings aligned with human characteristics.
- Ethical framing helped keep the system assistive rather than prescriptive.

### What Didn’t Work as Expected
- Ensemble models did not outperform the strongest single model.
- Rare MBTI types suffered from consistently low recall.
- Tree-based models struggled with high-dimensional sparse text data.

### Why
- Class imbalance limited the model’s ability to learn minority classes.
- Sparse feature representations favor linear decision boundaries.
- Dataset size constrained generalization for underrepresented personality types.

___

## 🚀 Next Steps

* Integrate **social media text** as an additional input source for MBTI prediction.
* Connect and align recommendations with **CariCon2A’s solution** for a unified workflow.
* Design and implement a **user-facing UI** to make career recommendations easier to explore.
* Present career suggestions with **clear reasoning and rationale** to support transparency.
* Leverage **top distinguishing feature analysis** to explain why specific careers are recommended.
* Expand and enrich feature sets beyond TF-IDF (e.g., linguistic, semantic, or behavioral features).

---

## 🙏 Acknowledgements

Thank you to CARICON, Challenge Advisors, AI Studio staff, and Break Through Tech for their guidance and support throughout this project.
