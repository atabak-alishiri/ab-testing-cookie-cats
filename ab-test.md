# A/B Test Design: Cookie Cats Gate Placement

## Overview

This A/B test evaluates whether moving the first "gate" (a feature that requires players to wait or make an in-app purchase to continue) from level 30 to level 40 improves player retention and engagement in the Cookie Cats mobile game.

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

## Minimum Practical Effect (MPE)

**MPE: +0.3 percentage points (pp) for day-7 retention**


## Success Criteria

The test will be considered successful if:
1. **Primary Metric:** Day-7 retention increases by at least 0.3pp in the treatment group (gate_40) compared to control (gate_30)
2. **Guardrail Metric:** Day-1 retention does not decrease by more than 0.5pp (to ensure we're not harming early experience)
3. **Secondary Metric:** Engagement (game rounds) shows improvement or remains stable

## Statistical Considerations

- **Test Type:** Two-sample proportion test for binary retention metrics
- **Significance Level:** α = 0.05 (two-tailed)
- **Power:** 80% to detect the MPE

## Notes

- This is a one-sided hypothesis test (expecting improvement), but we use two-tailed tests to be conservative and detect potential negative effects
- Results should be interpreted in the context of the overall user experience and business objectives

