# Network Intrusion Detection using Machine Learning (NSL-KDD)

This project implements a network intrusion detection system using the NSL-KDD dataset. It was developed as a reproduction and evaluation of the methodology described in the paper "A Subset Feature Elimination Mechanism for Intrusion Detection System" (Nkiama, Said & Saidu, 2016).

## Project Overview

Network intrusion detection involves classifying network traffic as either normal or an attack. This project trains and evaluates two machine learning models — Decision Tree and Random Forest — on the NSL-KDD dataset, following the feature selection approach proposed in the reference paper, and critically evaluates how well the paper's reported results could be reproduced.

## Reference Paper

Nkiama, H., Said, S. M., & Saidu, M. (2016). *A Subset Feature Elimination Mechanism for Intrusion Detection System*. International Journal of Advanced Computer Science and Applications (IJACSA).
Paper link: https://thesai.org/Publications/ViewPaper?Volume=7&Issue=4&Code=ijacsa&SerialNo=45

## Dataset

**NSL-KDD Dataset** — an improved version of the KDD Cup 1999 dataset that removes duplicate records and provides a more balanced set of attack categories (DoS, Probe, R2L, U2R).

Dataset link: https://www.unb.ca/cic/datasets/nsl.html

## Reference GitHub Repository

This project also references the implementation approach used in:
Cynthia Koopman's Network-Intrusion-Detection repository: https://github.com/CynthiaKoopman/Network-Intrusion-Detection

## Repository Structure

```
Network-Intrusion-Detection-ML/
│
├── data/
│   └── raw/                                  # NSL-KDD dataset files (KDDTrain.csv, KDDTest.csv)
│
├── notebooks/
│   └── Network_Intrusion_Detection.ipynb     # Main analysis and modeling notebook
│
├── images/
│   └── plots/                                # Exported charts (EDA, ROC, confusion matrix)
│
├── requirements.txt
└── README.md
```

## How to Run

**1. Clone the repository**

```bash
cd Network-Intrusion-Detection-ML
```

**2. Install dependencies**

```bash
pip install -r requirements.txt
```

**3. Add the dataset**

Place `KDDTrain.csv` and `KDDTest.csv` inside the `data/raw/` folder.

**4. Launch Jupyter Notebook**

```bash
jupyter notebook
```

Open `notebooks/Network_Intrusion_Detection.ipynb` and run all cells in order.

## Required Libraries

| Library | Purpose |
|---|---|
| pandas | Data manipulation and analysis |
| numpy | Numerical computations |
| matplotlib | Data visualization |
| seaborn | Statistical data visualization |
| scikit-learn | Machine learning models and evaluation |
| jupyter | Notebook environment |

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

## Models Used

**Decision Tree** — a single tree-based classifier that splits data based on feature values.

**Random Forest** — an ensemble of decision trees whose predictions are combined by majority voting.

## Results

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|
| Decision Tree | 79.09% | 96.51% | 65.64% | 78.14% |
| Random Forest | 77.52% | 96.66% | 62.67% | 76.04% |

## Key Findings

- Both models achieved high precision (above 96%), meaning normal traffic was rarely misclassified as an attack.
- Recall was noticeably lower (62–66%), meaning a meaningful portion of actual attacks were missed.
- The Decision Tree performed slightly better than Random Forest on the test set, despite Random Forest achieving higher accuracy during training.
- Error analysis showed that a large share of misclassifications came from attack types present in the test set but never seen during training. This is discussed in detail in the project report's Critical Evaluation section.

## References

1. Nkiama, H., Said, S. M., & Saidu, M. (2016). A Subset Feature Elimination Mechanism for Intrusion Detection System. IJACSA.
2. NSL-KDD Dataset — Canadian Institute for Cybersecurity, University of New Brunswick. https://www.unb.ca/cic/datasets/nsl.html
3. Koopman, C. Network-Intrusion-Detection (reference implementation). https://github.com/CynthiaKoopman/Network-Intrusion-Detection
