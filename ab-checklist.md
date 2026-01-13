# 📋 A/B Test Project Checklist

Use this checklist to define your A/B test clearly and scientifically before writing code or launching.

## 1. Experiment Design & Hypothesis
- [ ] **Problem Statement:** What specific problem are you trying to solve?
- [ ] **Hypothesis:** Complete this sentence: "By changing [X], we expect [Metric Y] to [increase/decrease] because [Reason Z]."
- [ ] **Business Value:** Why does this test matter? What is the potential ROI?

## 2. Metrics Definition
- [ ] **Primary Metric:** What is the *one* key metric that determines success? (e.g., Conversion Rate, Retention)
- [ ] **Guardrail Metrics:** What metrics must *not* negatively change? (e.g., Latency, Crash Rate, Unsubscribes)
- [ ] **Secondary Metrics:** What other metrics help explain user behavior?

## 3. Power Analysis & Sampling
- [ ] **Baseline Rate:** What is the current performance of the primary metric?
- [ ] **Minimum Detectable Effect (MDE):** What is the smallest improvement that is practically worth detecting?
- [ ] **Sample Size:** Have you calculated the required sample size per group? (Aim for Power=80%, Alpha=5%)
- [ ] **Target Audience:** Who is eligible for this test? (All users, new users only, specific region?)

## 4. Execution Plan
- [ ] **Variants:** Clearly define the Control (A) and Treatment (B) groups.
- [ ] **Randomization:** How will users be randomly assigned? (e.g., User ID hash)
- [ ] **Duration:** How long will the test run to capture full weeks/cycles? (Avoid stopping early!)
- [ ] **Sanity Checks:** How will you verify that the split is even (50/50) and no bias exists? (Sample Ratio Mismatch)

## 5. Success Criteria & Risks
- [ ] **Launch Criteria:** What specific result dictates a "Go" decision?
- [ ] **Rollback Plan:** If the test breaks something critical, how quickly can we revert?
- [ ] **Practical Significance:** If the result is statistically significant but small, is it worth the engineering cost to maintain?
