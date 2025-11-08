#  EPL Player Performance Prediction

*Using data science to reduce transfer market risk and identify undervalued talent in the English Premier League*

---

##  Project Overview

The English Premier League transfer market involves billions in player investments, yet many decisions remain gut-feel based. This project builds a **predictive model** to forecast player performance scores using transfer costs, physical attributes, and club affiliation—helping clubs make smarter, data-driven signing decisions.


---

## Business Problem

EPL clubs face three key challenges:
1. **High Risk:** £50-100M+ signings can flop
2. **Market Inefficiency:** Are expensive players always worth it?
3. **Limited Data Use:** Decisions often rely on traditional scouting alone

**Our Solution:** A statistical model that predicts player scores and identifies undervalued talent before competitors do.

---

##  Dataset

- **202 EPL players** across 3 clubs (Chelsea, Liverpool, Manchester United)
- **12 features** including:
  - Financial: Transfer cost, previous club cost, agent charges
  - Physical: Height, weight, BMI
  - Performance: Goals, shots per game, distance covered
  - Categorical: Club affiliation
- **Target:** Player performance score (0-35 scale)

---

##  Key Findings

### 1. **The Bargain Effect** (Most Important!)
Players from **cheaper previous clubs significantly outperform** expectations when moving to bigger clubs.
- **Each £1M increase** in previous club cost → **-0.99 score points**
- This is HUGE: A player who cost his previous club £30M performs ~20 points better than one who cost £50M (holding current price constant)
- **Strategic Implication:** Target players from lower-tier clubs for massive value

### 2. **You Get What You Pay For (Mostly)**
Current transfer cost positively predicts performance, but the effect is smaller than expected.
- **Each £10M increase** in transfer fee → **+0.33 score points**
- Expensive players are better, but not dramatically so

### 3. **Physical Robustness Matters**
Weight (as a proxy for strength) is highly significant.
- **Each 1kg increase** → **+0.86 score points**
- The EPL's physical style favors stronger players

### 4. **Club Effects Are Real**
- **Manchester United players:** Score ~1 point **higher** than baseline
- **Liverpool players:** Score ~0.5 points **lower** than baseline
- Suggests different player development systems or tactical fits

---

##  Technical Approach

### Models Evaluated
1. **Ordinary Least Squares (OLS)** - Baseline
2. **Ridge Regression** - Handles multicollinearity
3. **Lasso Regression** - Feature selection
4. **ElasticNet** - Best of both


---

##  Model Performance

| Metric | Training | Test | Interpretation |
|--------|----------|------|----------------|
| **R²** | 0.9875 | 0.9891 | Excellent generalization! |
| **RMSE** | 0.690 | 0.648 | ±0.65 points average error |
| **MAE** | 0.511 | 0.489 | Very accurate predictions |

**No overfitting detected** - test performance actually *exceeds* training!


---

##  What I Learned

1. **When to stop optimizing:** ElasticNet was 0.02% better than OLS - not worth the complexity trade-off
2. **Omitted variable bias matters:** Removing PreviousClubCost caused coefficients to change by 500%!
3. **Real data is messy:** Assumption violations are normal; knowing how to handle them matters more than achieving perfection
4. **Business value > statistical perfection:** A 98.9% accurate, interpretable model beats a 99.0% black box

---

**⭐ If you found this project interesting, please star the repo!**

*Built with 🧠 and a love for football analytics*
