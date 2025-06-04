# Scouting Europe’s Next Top Striker: A Machine Learning Approach

This project uses unsupervised machine learning to identify elite strikers from Europe’s top five leagues in the 2024/25 season. The goal: to create a data-driven transfer shortlist — with **Mateo Retegui** emerging as the top recommendation.

## 🎯 The Task

Use Opta player performance data to uncover hidden and elite forward talent, with a special focus on:

- Fair comparison across players using per-90 metrics
- Dimensionality reduction and clustering to group players by performance style
- Creating a shortlist of players based on both output and value potential

---

## 📊 Data Overview

- **Source**: [Opta Stats via Kaggle (2024/25 season)](https://www.kaggle.com/datasets/hubertsidorowicz/football-players-stats-2024-2025)
- **Scope**: Players from Europe’s top 5 leagues
- **Filter criteria**:
  - Position: Forward
  - Minutes played: > 900
  - Goals scored: > 5
- **Dataset size after filtering**: 216 players × ~40 performance metrics
- **Engineered features**: All key stats on a per-90 basis for comparability
- **Exploratory analysis**: Identified outliers and clustered profiles by role & output

---

## 🤖 Modelling Approach

- **Techniques**: 
  - Dimensionality Reduction: `UMAP`
  - Clustering: `HDBSCAN` (final), `KMeans` (baseline)
- **Key metrics used**:
  - `goals_per_90`
  - `shots_on_target_per_90`
  - `non_pen_xg_per_90`
  - `progressive_runs_per_90`
  - `touches_in_pen_per_90`
  - `goals_per_shot_on_target`
  - `goals_minus_exp_goals`
- **Best model result**:
  - 📈 **16 clusters**
  - 💡 **Silhouette Score**: 0.62

![clusterplot](https://github.com/DanMontHell/scouting-elite-goalscorers/blob/main/dbscan.png)
---

## ⭐ Cluster 1: The Elite Scorers

Players in Cluster 1 performed at the highest level across multiple attacking metrics:

| Metric                      | Cluster 1 Avg | Rank (of 12) |
|----------------------------|---------------|--------------|
| Goals per 90               | 0.75          | 🥇 1st       |
| Shots on target per 90     | 1.35          | 🥇 1st       |
| Non-penalty xG per 90      | 0.57          | 🥇 1st       |
| Touches in penalty area    | 6.11          | 🥉 3rd       |
| Aerial duels won per 90    | 1.6           | 4th          |
| Goals per shot on target   | 0.52          | 3rd          |
| Goals minus xG             | 1.5           | 6th          |

Notable players in Cluster 1 include:
- Harry Kane (Bayern)
- Kylian Mbappé (Real Madrid)
- Robert Lewandowski (Barcelona)
- Ousmane Dembélé (Paris SG)
- Alexander Isak (Newcastle)
- Alexander Sørloth (Atlético Madrid)

---

## 🔝 Top Recommendation: **Mateo Retegui**

- 📍 **Club**: Atalanta
- ⚽ **Goals scored**: 25
- 🔥 **Goals minus xG**: +6.1
- 🕐 **Goals per 90**: 0.94
- 🎯 **Shots on target per 90**: 1.21
- 🥅 **Goals per shot on target**: 0.78
- 📊 **Non-penalty xG per 90**: 0.56

Retegui ranked highly across all key metrics and outperformed his xG more than most elite peers — making him a statistically compelling transfer target.

---

## 💼 Additional Considerations (U29 & Non-Elite Clubs)

| Name               | Club           | Value* (€M) | Goals – xG |
|--------------------|----------------|------------|------------|
| Mateo Retegui      | Atalanta       | ~45M       | +6.1       |
| Jonathan Burkardt  | Mainz 05       | ~35M       | +3.2       |
| Nick Woltemade     | Stuttgart      | ~17M       | +1.8       |
| Mika Biereth       | Monaco         | ~30M       | +1.7       |

Estimates from Transfermarkt.com*

---

## 🧰 Tools Used

- **SQL**: Filtering & player selection
- **Python**: EDA, preprocessing, modelling
- **Libraries**: `pandas`, `scikit-learn`, `hdbscan`, `umap-learn`, `matplotlib`, `seaborn`
- **Jupyter Notebooks**: Interactive development
- **PyCharm + GitHub**: IDE and version control

---

## 📂 Repository Structure
```bash
elite-striker-clustering/
├── data/
│ ├── filtered_striker_df.csv
│ ├── striker_df.csv
├── notebooks/
│ ├── 01_data_extraction_and_filtering.ipynb
│ ├── 02_eda.ipynb
│ ├── 03_kmeans.ipynb
│ └── 04_hdbscan_v2_final_model.ipynb
├── model/
│ └── final_model.pkl
├── requirements.txt
├── README.md
├── LICENSE
```

## ⚙️ Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/yourusername/elite-striker-clustering.git
cd elite-striker-clustering
pip install -r requirements.txt

Launch the notebooks:
jupyter notebook
```

## 📬 Contact
For insights, discussions, or collaboration opportunities, connect on [LinkedIn](https://www.linkedin.com/in/danhellmuth/).


## 📜 License
Distributed under the MIT License. See LICENSE for more information.

---

### 📝 `LICENSE` (MIT License)

```txt
MIT License

Copyright (c) 2025 Daniel Hellmuth

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the “Software”), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
