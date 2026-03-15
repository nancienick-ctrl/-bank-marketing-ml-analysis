# Bank Marketing Campaign — Term Deposit Subscription Predictor

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

## Project Overview

A European retail bank runs direct phone marketing campaigns to get clients to subscribe 
to term deposits. The problem: only **11.3% of clients** actually subscribe, meaning 
agents spend the vast majority of their time calling people who will say no.

This project builds a predictive model to identify which clients are most likely to 
subscribe **before** the call is made, so the bank can prioritize the right people, 
at the right time, and stop wasting resources on resistant prospects.

## The Business Question

*"Which clients should we call first — and which ones are we wasting time on?"*

---

## Repository Structure
bank-marketing-churn/
│
├── bank_marketing_analysis.ipynb   # Full analysis notebook
└── README.md                       # You are here


## Dataset

**Source:** UCI Machine Learning Repository — Bank Marketing Dataset
**Size:** 41,188 client contacts from a Portuguese retail bank (2008–2010)
**Features:** 20 variables including demographics, campaign history, and financials
**Target:** `y` — whether the client subscribed to a term deposit (yes/no)
**Class Imbalance:** 88.7% No / 11.3% Yes — requires careful metric selection


## Key Findings (The Discovery)

### Finding 1 — Demographics Matter
Students and retired clients subscribe at **2–3x the average rate**. Clients aged 
18–25 and 65+ are the highest-converting segments yet are underrepresented in 
current call lists.

### Finding 2 — Less Calling = More Converting
Subscription rates drop sharply after the first contact. Clients called 3+ times 
convert at less than **half the rate** of first-contact clients. The bank is 
over-calling resistant prospects while missing fresh leads.

### Finding 3 — Timing Is Everything
March, September, and October convert at nearly **3x the rate of May** — yet May 
has the highest call volume of any month. The campaign calendar is misaligned with 
client receptivity.

### Finding 4 — Past Behavior Predicts Future Behavior
Clients who subscribed in a previous campaign convert at **3–4x the rate** of 
clients with no prior history. A dedicated warm re-engagement list should be 
worked before every new campaign begins.


## Model Results

| Model | Accuracy | Recall | Notes |

| Gaussian Naive Bayes | 86.4% | 40.3% | Below baseline accuracy |
| Decision Tree | 82.5% | 31.7% | Tends to overfit |
| Logistic Regression | 89.4% | 18.1% | Best overall |

> **Why Recall over Accuracy?** With an 88.7% "no" baseline, a model that predicts 
> "no" every time scores higher on accuracy than our trained model — making accuracy 
> meaningless here. Recall tells us what % of actual subscribers we successfully 
> identify, which directly maps to revenue captured vs. missed.



## Recommendations

### 1.Cap Contacts at 2 Per Campaign
Stop calling clients more than twice per cycle. Every call beyond two converts at 
half the rate and damages the relationship. Redirect freed capacity to fresh leads.

### 2.Build a Warm List — Call Previous Subscribers First
Clients who said yes before convert at 3–4x the average. Pull this list before 
every campaign and work it first. Same budget, dramatically better results.

### 3.Restructure the Campaign Calendar
Shift 15% of May volume into March and September. Based on observed conversion 
rate differences, this alone could generate an estimated **€500K–€1M in additional 
deposits** per campaign cycle at no extra cost.

### 4.Deploy Logistic Regression as a Pre-Call Scoring Tool
Score every client before dialing. Work the list highest-to-lowest. Set a cutoff 
threshold below which agents don't call. Recovering even 150 previously missed 
subscribers per campaign = **€180,000 in incremental deposit value**.


## Tools & Libraries

**Python 3.12** — core language
**Pandas & NumPy** — data manipulation
**Matplotlib & Seaborn** — visualizations
**scikit-learn** — model building and evaluation
**ucimlrepo** — dataset loading

How to Run

1. Open `bank_marketing_analysis.ipynb` in Google Colab
2. Run `!pip install ucimlrepo` in the first cell
3. Run all cells top to bottom (`Runtime → Run all`)


## Author

**Nancy Nomathemba Shumba**  
Predictive Analytics and Machine Learning 
03/14/2026

---

*Dataset source: UCI Machine Learning Repository — Bank Marketing (ID: 45)*
