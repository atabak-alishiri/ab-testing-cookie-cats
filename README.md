# 🍪 Cookie Cats A/B Testing Analysis

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A comprehensive A/B testing analysis of the **Cookie Cats** mobile game, examining how gate placement (at level 30 vs. level 40) affects user retention and engagement. This project demonstrates end-to-end experimental analysis using real-world game data.

## 📋 Table of Contents

- [Overview](#overview)
- [About Cookie Cats](#about-cookie-cats)
- [The Experiment](#the-experiment)
- [Key Findings](#key-findings)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Analysis Results](#analysis-results)
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)
- [License](#license)

## 🎯 Overview

This project analyzes an A/B test conducted on the popular mobile puzzle game **Cookie Cats** by Tactile Entertainment. The experiment tested whether moving the first "gate" (a feature that requires players to wait or make an in-app purchase to continue) from level 30 to level 40 would improve player retention.

**Research Question:** Does delaying the first gate from level 30 to level 40 improve 1-day and 7-day retention rates?

## 🎮 About Cookie Cats

Cookie Cats is a popular mobile puzzle game where players match tiles to progress through levels. At certain points in the game, players encounter "gates" that require them to either wait for a timer to expire or make an in-app purchase to continue playing.

## 🧪 The Experiment

### Experimental Design

- **Control Group (gate_30):** Players encounter the first gate at level 30
- **Treatment Group (gate_40):** Players encounter the first gate at level 40

### Metrics Analyzed

1. **1-Day Retention:** Percentage of players who return to play the game one day after installing
2. **7-Day Retention:** Percentage of players who return to play the game seven days after installing
3. **Game Rounds:** Total number of game rounds played by each user

### Sample Size

- **Total Users:** 90,189
- **Control Group (gate_30):** ~45,000 users
- **Treatment Group (gate_40):** ~45,000 users

## 📊 Key Findings

### Retention Analysis

- **1-Day Retention:**
  - gate_30: **44.82%**
  - gate_40: **44.23%**
  - **Difference:** gate_30 performs slightly better (+0.59 percentage points)

- **7-Day Retention:**
  - gate_30: **19.02%**
  - gate_40: **18.20%**
  - **Difference:** gate_30 performs better (+0.82 percentage points)

### Engagement Analysis

- **Mean Game Rounds:**
  - gate_30: **52.46 rounds**
  - gate_40: **51.30 rounds**
  - gate_30 shows slightly higher engagement

### Critical Insights

1. **Early Engagement is Key:** Players who complete just 10 rounds show a dramatic increase in retention, jumping from ~12% to over 50% for 1-day retention. This identifies the first 10 levels as the critical "hook" for user loyalty.

2. **Gate Placement Impact:** Moving the gate from level 30 to level 40 does not improve retention. In fact, the original placement (level 30) shows marginally better performance across all metrics.

3. **Zero-Play Users:** Approximately 4.3-4.5% of users in both groups never play a single round, indicating the gate placement has minimal impact on initial user acquisition.

## 📁 Dataset

The dataset (`dataset/cookie_cats.csv`) contains 90,189 rows and 5 columns:

| Column           | Description                                      | Type    |
| ---------------- | ------------------------------------------------ | ------- |
| `userid`         | Unique identifier for each user                 | Integer |
| `version`        | A/B test group (`gate_30` or `gate_40`)         | String  |
| `sum_gamerounds` | Total number of game rounds played               | Integer |
| `retention_1`    | Whether user returned 1 day after install        | Boolean |
| `retention_7`    | Whether user returned 7 days after install       | Boolean |

### Dataset Statistics

- **No missing values:** Complete dataset with 100% data quality
- **Right-skewed distribution:** Mean game rounds (51.87) is higher than median (16), indicating many casual players and a few highly engaged users
- **Outliers present:** Maximum game rounds reaches 49,854 (extreme outlier)

## 🚀 Installation

### Prerequisites

- Python 3.8 or higher
- Conda (recommended) or pip

### Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/yourusername/ab-testing-cookie-cats.git
   cd ab-testing-cookie-cats
   ```

2. **Create and activate the conda environment:**

   ```bash
   conda env create -f environment.yml
   conda activate cookie-cats
   ```

   Or install dependencies with pip:

   ```bash
   pip install pandas numpy matplotlib seaborn jupyter notebook
   ```

3. **Launch Jupyter Notebook:**

   ```bash
   jupyter notebook
   ```

## 💻 Usage

1. **Open the analysis notebook:**

   ```bash
   jupyter notebook EDA.ipynb
   ```

2. **Run all cells** to reproduce the complete analysis, or run cells individually to explore specific analyses.

3. **Key sections in the notebook:**
   - Data loading and overview
   - Descriptive statistics
   - Retention analysis by version
   - Engagement analysis
   - Distribution analysis
   - Zero-plays analysis
   - Retention overlap analysis

## 📈 Analysis Results

### Summary Statistics

| Version   | Mean Game Rounds | Median Game Rounds | 1-Day Retention | 7-Day Retention |
| --------- | ---------------- | ------------------ | ---------------- | ---------------- |
| **gate_30** | 52.46            | 17.0               | 44.82%           | 19.02%           |
| **gate_40** | 51.30            | 16.0               | 44.23%           | 18.20%           |

### Visualizations

The analysis includes several key visualizations:

- **Retention Rates by Version:** Bar chart comparing 1-day and 7-day retention between groups
- **Mean Game Rounds:** Comparison of engagement levels
- **Distribution Analysis:** Histogram of game rounds distribution (0-200 rounds)
- **Retention by Engagement:** Heatmap showing retention rates across different engagement buckets
- **Retention Overlap:** Cross-tabulation analysis of 1-day vs. 7-day retention

## 📂 Project Structure

```
ab-testing-cookie-cats/
│
├── dataset/
│   └── cookie_cats.csv          # A/B test dataset
│
├── EDA.ipynb                    # Main analysis notebook
├── environment.yml              # Conda environment file
├── README.md                    # Project documentation
└── LICENSE                      # License file
```

## 🛠️ Technologies Used

- **Python 3.8+**
- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical computing
- **Matplotlib** - Data visualization
- **Seaborn** - Statistical data visualization
- **Jupyter Notebook** - Interactive analysis environment

## 📝 Key Takeaways

1. **Gate placement at level 30 is optimal** - The original placement shows better retention metrics
2. **Early engagement matters most** - The first 10 levels are critical for player retention
3. **Small differences can be meaningful** - Even small percentage point differences can translate to significant revenue impact at scale
4. **Comprehensive analysis is essential** - Examining multiple metrics (retention, engagement, distribution) provides a complete picture

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/yourusername/ab-testing-cookie-cats/issues).

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Tactile Entertainment** for making the Cookie Cats dataset publicly available
- The data science community for inspiration and best practices

## 📧 Contact

For questions or suggestions, please open an issue or contact the project maintainer.

---

**Note:** This analysis is for educational and demonstration purposes. The dataset represents a real A/B test scenario, providing valuable insights into experimental design and statistical analysis in the gaming industry.
