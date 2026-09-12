# Exploratory data analysis — portfolio

A set of self-contained exploratory analyses. Each folder is one project with its
own README, notebook, and exported figures. Finished notebooks are also published
to Kaggle.

Shared environment: [`requirements.txt`](requirements.txt).

---

### [03 — What does a world university ranking actually reward?](03-FInal-DS-project/)

An audit of the CWUR 2018–19 rankings that asks what the ranking is made of
rather than which universities are good. `World Rank` turns out to be `Score`
sorted descending, `Score` is reproducible from its seven indicator columns at
R² = 0.98 with the research block driving ~60% of it, and — because `Score` is
published to one decimal place — sixteen universities share the score 69.9 while
being handed ranks 971 through 986. Below the top 200 the ordering is largely
tie-breaking.

→ [README](03-FInal-DS-project/README.md) ·
[notebook](03-FInal-DS-project/01-what-the-ranking-rewards.ipynb)

---

### [02 — Every anomaly in this dataset was the same bug](02-Heart-disease/)

The Cleveland Heart Disease data (UCI), 303 patients referred for diagnostic
workup. Written as a medical translation guide — what does each column measure,
which direction is bad — until five separate things refuse to make sense. Joining
the file against the UCI original shows why: the target is inverted and every
ordinal column was reversed. Three columns had *looked* correct precisely because
they contained two compensating errors. Decoded, `ca` becomes a clean
dose-response and men turn out to be diseased at twice the rate of women, which
is the opposite of what my first pass concluded.

→ [README](02-Heart-disease/README.md) ·
[notebook](02-Heart-disease/01-every-anomaly-was-one-bug.ipynb)

---

### [01 — Why does nothing correlate with potability?](01-water-potability-eda/)

A water-quality dataset where every feature correlates with the target at
|r| < 0.04. Three answers: the file is generated rather than measured (every
value distinct to 15 decimal places, dissolved solids above seawater), seven of
the eight published guideline bands carry no information, and — the part worth
keeping — there *is* real signal, in an interaction Pearson correlation cannot
see. Water is labelled potable when pH and sulfate sit on opposite sides of their
means: 49.2% against 31.8%. A random forest reaches AUC 0.71 where logistic
regression reaches 0.48, and handing that linear model the 36 pairwise products
recovers 88% of the gap.

→ [README](01-water-potability-eda/README.md) ·
[notebook](01-water-potability-eda/01-why-nothing-correlates.ipynb)

---

## Running any of these

```bash
pip install -r requirements.txt
jupyter lab
```

Each notebook runs top to bottom on a fresh kernel and reads its data from its
own project folder.

Projects 01 and 02 include interactive Plotly charts. These load plotly.js from a
CDN, so they need an internet connection the first time a notebook is opened, and
**they do not render in GitHub's `.ipynb` preview** — open those notebooks in
Jupyter, nbviewer, or on Kaggle.
