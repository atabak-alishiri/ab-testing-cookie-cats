# A/B Test Design: Cookie Cats Gate Placement

## Overview

**About Cookie Cats:** Cookie Cats is a popular mobile puzzle game developed by Tactile Entertainment where players match tiles to progress through levels. The game features a match-3 gameplay mechanic similar to games like Candy Crush. At certain points in the game, players encounter "gates" (barriers that require them to either wait for a timer to expire or make an in-app purchase to continue playing.) These gates are a key monetization feature that balances player progression with revenue generation.

This A/B test evaluates whether moving the first "gate" (a feature that requires players to wait or make an in-app purchase to continue) from level 30 to level 40 improves player retention and engagement in the Cookie Cats mobile game.

## A/B Testing Methodology & Statistical Considerations

### Experimental Setup

From a data science perspective, this A/B test follows rigorous experimental design principles to ensure valid and reliable results:

**1. Randomization & Assignment**
- Users are randomly assigned to either the control group (gate_30) or treatment group (gate_40) upon installation
- Randomization ensures that both groups are statistically equivalent at baseline, eliminating selection bias
- The dataset contains 90,189 users with approximately equal distribution (~45,000 per group), ensuring balanced group sizes

**2. Sample Size & Statistical Power**
- **Total Sample Size:** 90,189 users provides sufficient statistical power
- **Per-Group Sample Size:** ~45,000 users per group

**3. Data Quality & Completeness**
- **No Missing Values:** The dataset is complete with 100% data quality across all variables
- **Data Types:** Properly structured with binary retention metrics (Boolean) and continuous engagement metrics (Integer)

**4. Statistical Testing Approach**
- **Primary Analysis:** Two-sample proportion test (z-test) for binary retention metrics
- **Significance Level:** α = 0.05 (two-tailed) to control Type I error rate

**5. Assumptions Validation**
- **Independence:** Each user is independent (no user appears in both groups)
- **Random Sampling:** Users are randomly assigned, satisfying the random sampling assumption
- **Large Sample Size:** With n > 30,000 per group, the Central Limit Theorem applies, allowing use of normal approximation for proportion tests
- **Binary Outcomes:** Retention metrics are binary (True/False), appropriate for proportion tests

**6. Guardrail Metrics**
- Day-1 retention serves as a safety check to ensure the treatment doesn't harm early user experience
- This prevents deploying changes that improve long-term metrics at the expense of initial engagement

**7. Secondary Metrics**
- Engagement (game rounds) provides additional context and validation
- Continuous metrics allow for more granular analysis and can reveal patterns not captured by binary retention

This experimental design ensures that any observed differences between groups can be attributed to the gate placement change rather than confounding factors or random variation.

## Hypothesis

**Hypothesis:** Moving the gate from level 30 to level 40 will improve player retention, particularly day-7 retention, by allowing players to experience more of the game before encountering their first monetization barrier.

**Rationale:**
- Players who reach higher levels before hitting a gate may be more engaged and invested in the game
- Delaying the gate allows players to form stronger habits and positive associations with the game
- Early gates may interrupt the flow and cause players to churn before they become committed users

## Experimental Design

- **Control Group (gate_30):** Players encounter the first gate at level 30
- **Treatment Group (gate_40):** Players encounter the first gate at level 40
- **Randomization:** Users are randomly assigned to one of the two groups
- **Sample Size:** ~90,189 users (approximately 45,000 per group)

## Metrics

### Primary Metric

**Day-7 Retention (Binary)**
- **Definition:** Percentage of players who return to play the game seven days after installing
- **Type:** Binary (True/False)
- **Why:** Day-7 retention is a strong indicator of long-term player engagement and habit formation. It captures whether players have developed a sustainable relationship with the game beyond the initial novelty period.

### Guardrail Metric

**Day-1 Retention (Binary)**
- **Definition:** Percentage of players who return to play the game one day after installing
- **Type:** Binary (True/False)
- **Why:** Day-1 retention serves as a guardrail to ensure that moving the gate doesn't harm the early player experience. If day-1 retention decreases significantly, it indicates that the change may be negatively impacting initial engagement or onboarding.

### Secondary Metric

**Engagement: Total Game Rounds Played**
- **Definition:** Total number of game rounds played by each user (`sum_gamerounds`)
- **Type:** Continuous (Integer)
- **Why:** Engagement metrics provide additional context about player behavior. Higher engagement (more rounds played) often correlates with better retention and can indicate whether players are enjoying the game experience more.

## Success Criteria

The test will be considered successful if:
1. **Primary Metric:** Day-7 retention increases by at least 0.3pp in the treatment group (gate_40) compared to control (gate_30)
2. **Guardrail Metric:** Day-1 retention does not decrease by more than 0.5pp (to ensure we're not harming early experience)
3. **Secondary Metric:** Engagement (game rounds) shows improvement or remains stable

## Statistical Considerations

- **Test Type:** Two-sample proportion test for binary retention metrics
- **Significance Level:** α = 0.05 (two-tailed)

## Notes

- This is a one-sided hypothesis test (expecting improvement), but we use two-tailed tests to be conservative and detect potential negative effects
- Results should be interpreted in the context of the overall user experience and business objectives
