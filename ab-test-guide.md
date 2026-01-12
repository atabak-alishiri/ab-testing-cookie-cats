# 🧪 The Modern Guide to Scientific A/B Testing in Business

A/B testing (or split testing) is the gold standard for data-driven decision-making. It transforms "I think" into "I know" by subjecting product changes to controlled, randomized experiments.

This guide outlines a rigorous, scientific framework for running A/B tests, ensuring your business decisions are based on signal, not noise.

---

## 📑 Phase 1: Experiment Design

Before writing a single line of code, you must define *what* you are testing and *why*.

### 1. The Hypothesis
A good hypothesis is a falsifiable statement connecting a specific change to a specific outcome.

*   **Format:** "By [changing X], we expect [metric Y] to [increase/decrease]."
*   **Example:** "By moving the monetization gate from level 30 to 40, we expect Day-7 retention to increase."

### 2. Metric Selection
Choose metrics that capture the full picture of user behavior.

*   **🌟 Primary Metric (The Goal):** The one metric that determines success.
    *   *Examples:* Conversion rate, Retention rate (Day-1/Day-7), Average Revenue Per User (ARPU).
    *   *Requirement:* Must be sensitive enough to move and stable enough to measure.
*   **🛡️ Guardrail Metrics (The Safety Net):** Metrics you must *not* harm.
    *   *Examples:* Latency, app crash rate, unsubscribe rate, Day-1 retention (if optimizing for long-term).
    *   *Rule:* If the primary metric wins but a guardrail metric tanks, the test fails.
*   **Secondary Metrics (The Context):** Help explain *why* the primary metric moved.
    *   *Examples:* Time on site, pages per session, clicks on specific features.

### 3. Power Analysis (Sample Size)
You cannot just "run it for a week." You must calculate how many users you need to detect a meaningful difference.

*   **Inputs for Calculation:**
    *   **Baseline Conversion Rate:** Your current performance (e.g., 20%).
    *   **Minimum Detectable Effect (MDE):** The smallest improvement you care about (e.g., +1% absolute change). *Smaller MDE = Larger Sample Size.*
    *   **Statistical Power ($1 - \beta$):** Probability of detecting an effect if it exists (Standard: 80%).
    *   **Significance Level ($\alpha$):** Probability of a false positive (Standard: 5% or 0.05).
*   **Tool:** Use a sample size calculator (e.g., Evans Miller) or Python's `statsmodels`.

---

## 🚀 Phase 2: Execution

### 1. Randomization
Users must be randomly assigned to groups to eliminate selection bias. The only difference between Group A and Group B should be the feature you are testing.

### 2. Sample Ratio Mismatch (SRM) Check
Before analyzing results, check if the ratio of users in Control vs. Treatment matches your design (usually 50/50).
*   **The Check:** If you expected a 50/50 split but got 48/52, you likely have a bug (e.g., the treatment is crashing the app before the event is logged).
*   **Action:** If SRM exists, **do not analyze the results.** Fix the bug and restart.

### 3. Duration
*   **Seasonality:** Run tests for full weeks (e.g., 1 week, 2 weeks) to account for weekend vs. weekday behavior.
*   **Novelty Effect:** Be wary of initial spikes caused by users just exploring a "new" thing.

---

## 📊 Phase 3: Statistical Analysis

Once data is collected, we use statistics to distinguish real effects from random chance.

### 1. Choosing the Right Test
*   **For Proportions (Conversion, Retention):**
    *   **Z-Test:** Standard for large samples (N > 30).
    *   **Chi-Square Test:** Good for A/B/C testing or smaller samples.
*   **For Means (Revenue, Time Spent):**
    *   **T-Test:** Compares the means of two groups.

### 2. The P-Value
The probability of seeing these results if the Null Hypothesis (no difference) were true.
*   **Threshold ($\alpha$):** Typically 0.05.
*   **Interpretation:** If p < 0.05, the result is "Statistically Significant."

### 3. Confidence Intervals (CI)
Often more useful than P-values. The CI tells you the *range* of the likely effect.
*   *Example:* "We are 95% confident the lift is between +0.5% and +2.5%."
*   **Decision:** If the interval includes 0, the result is not significant. If the entire interval is positive, you have a winner.

---

## 🏁 Phase 4: The Decision

Statistical significance does not always equal business value.

### 1. Practical Significance
Is the "statistically significant" lift worth the cost?
*   *Scenario:* You found a statistically significant 0.01% increase in revenue, but maintaining the feature costs $10k/month.
*   *Decision:* Do not launch. The ROI isn't there.

### 2. Launch Criteria
*   ✅ **Primary Metric:** Statistically significant improvement (or flat, if it's a strategic infrastructure change).
*   ✅ **Guardrail Metrics:** No statistically significant negative impact.
*   ✅ **Practical Significance:** The lift justifies the maintenance cost.

### 3. Documentation
Document every test, win or lose.
*   **Learning:** "We learned that users do not like X."
*   **Institutional Knowledge:** Prevents re-running the same failed ideas next year.

---

## 🧠 Example Checklist (Cookie Cats Case)

Using the Cookie Cats project as a template:

1.  **Hypothesis:** Moving the gate to Level 40 improves retention.
2.  **Groups:** Control (Gate @ 30), Treatment (Gate @ 40).
3.  **Sanity Check:** Validated sample split (approx 50/50).
4.  **Analysis:**
    *   *Day-7 Retention:* Treatment was **lower** than Control.
    *   *P-value:* < 0.05 (Significant difference).
5.  **Conclusion:** Do **not** launch. Moving the gate actually *hurts* retention.

---

*“If we have data, let’s look at data. If all we have are opinions, let’s go with mine.”*  
— **Jim Barksdale, former Netscape CEO**

