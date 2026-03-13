# Star Power Index: Quantifying Actor Impact on Movie Success in Bollywood Cinema

A data-driven research project that quantifies Bollywood actor influence through a novel **Star Power Index (SPI)** — emphasizing quality consistency over output volume. Published as an IEEE-format research paper.


## Key Results

| Metric | Value |
|--------|-------|
| Dataset | 1,619 Bollywood films (2001–2019) |
| Actors analyzed | 2,556 unique actors |
| Actor-movie pairs | 7,574 |
| SPI vs Success correlation | Pearson r = 0.223, p < 0.0001 |
| Variance explained | 7.4% (R²) |
| Highest SPI actor | Aamir Khan (0.627) — 15 films |


## What is the Star Power Index?

Most star power studies treat popularity as volume — how many films an actor has done, how famous they are commercially. This project challenges that assumption.

We built SPI as a weighted quality-consistency metric:

SPI = 0.25 × Experience + 0.30 × Quality + 0.25 × Consistency + 0.15 × RecentForm + 0.05 × Longevity


All features are **backward-looking** — computed using only films released *before* the current movie, preventing data leakage.

### Key finding
Aamir Khan (15 selective films, SPI = 0.627) ranks higher than Shah Rukh Khan (45 films, SPI = 0.499). Quality consistency beats prolific output.



## Methodology

### Dataset
- Source: [Bollywood Movies Dataset (2001–2019)](https://www.kaggle.com/datasets/nilesh2042/bollywood-movies-datasets) via Kaggle
- Attributes used: IMDb ratings, vote counts, awards, release dates, genres, cast lists

### Success Metric
Since box office revenue is unavailable for most Bollywood films, we constructed a composite score:

```
S = 0.5 × Rating_norm + 0.3 × Votes_norm + 0.2 × Awards_norm
```

### Feature Engineering
15 temporal career features per actor per movie, including:
- `career_avg_rating` — mean rating of all prior films
- `career_hit_ratio` — proportion of prior films with rating ≥ 7.0
- `recent_avg_rating_3` — mean of last 3 films
- `peak_rating` — highest rating achieved so far
- `genre_diversity` — number of genres worked in

### Validation
- PCA confirmed quality metrics load highest; volume metrics load near-zero
- Both Pearson (r=0.223) and Spearman (ρ=0.228) correlations significant at p<0.0001
- Genre-specific analysis: Biography (r=0.35) → Romance (r=0.12)

---

## Genre Analysis

| Genre | Correlation | Sample Size |
|-------|-------------|-------------|
| Biography | 0.35 | 47 |
| Drama | 0.28 | 389 |
| Action | 0.20 | 145 |
| Comedy | 0.18 | 312 |
| Romance | 0.12 | 264 |

Star power matters most in credibility-driven genres (biography, drama) and least in concept-driven ones (romance, fantasy).

---

## Repo Structure

```
star-power-index/
├── code/
│   └── star_power_index.ipynb   # Full analysis notebook
├── dataset/
│   └── movies.csv               # Cleaned Bollywood dataset
└── IEEE_Format_Report
```

---

## How to Run

```bash
# Clone the repo
git clone https://github.com/yourusername/star-power-index.git
cd star-power-index

# Install dependencies
pip install pandas numpy scikit-learn matplotlib seaborn

# Open the notebook
jupyter notebook code/star_power_index.ipynb
```



## Authors

- Jahnavi Srinath — PES University, CSE (AIML)
- **Mahima R Shetty** — PES University, CSE (AIML)
- Vivian Philip Varghese — PES University, CSE (AIML)

