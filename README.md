# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** N.Varsha  
**Student ID    :** 2310040127  
**Date Submitted:** 09/03/2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

```
The fitness() function returns the total value of selected items. If the total weight exceeds the knapsack capacity, it returns 0 to penalize invalid solutions.
```
**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
tournament_select() chooses one individual from a small random group of individuals in the population. The individual with the highest fitness in that group is selected, so better solutions have a higher chance of being chosen.
```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**
```
This line copies the best chromosome from the current generation into the next generation. This technique is called elitism. It is important because it preserves the best solution found so far and prevents it from being lost during crossover or mutation.
```
---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations |50 |
| Best value at generation 1 |60 |
| Final best value |77 |
| Total weight of best solution (kg) |14.4 |
| Is solution valid (Yes / No) |yes |

**Copy the printed packing list here:**
```
[  Best Packing List
--------------------------------------
  + Water bottle
  + First aid kit
  + Sleeping bag
  + Torch
  + Energy bars (x6)
  + Rain jacket
  + Map & compass
  + Cooking stove
  + Rope (10 m)
  + Sunscreen
  + Power bank
--------------------------------------
  Weight : 14.4 / 15.0 kg
  Value  : 77
  Valid  : Yes ]
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
[ The plot shows a rapid increase in fitness during the early generations, indicating quick improvement in solutions. The biggest improvement occurs in the first few generations as the algorithm identifies strong combinations. After that, the curve gradually flattens, showing convergence as fewer improvements are found ]
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-----------------|-------------|--------|----------------|
| 0.01         |    75             |   14.9          |   Yes     | Smooth, early flat               |
| 0.05         |    77             |   14.4          |   Yes     |  Steady improvement              |
| 0.30         |    78             |   14.1          |   Yes     |  Noisy/Unstable              |

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
[ When the mutation rate is too low (0.01), there isn’t much diversity, so the algorithm may get stuck early and stop improving. When the mutation rate is too high (0.30), many genes change randomly, making the search unstable. A moderate mutation rate (0.05) works best because it keeps some diversity while still allowing steady improvement. ]
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
[ The mutation rate 0.30 gave the best final value (78) in this experiment. This is because higher mutation adds more variation, helping the algorithm explore more solutions. However, the results were a bit more unstable compared to a moderate mutation rate. ]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 |77 |GA improves quickly and converges |
| 2 — Mutation rate | mutation_rate = ___ |78 |Higher mutation found slightly better solution |

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
[ From these experiments, I learned that mutation rate strongly affects the performance of Genetic Algorithms. A low mutation rate reduces diversity and may cause the algorithm to get stuck, while a high mutation rate increases exploration. In this experiment, a higher mutation rate produced the best result, but it also made the search less stable. Overall, I understood how GA gradually evolves better solutions across generations. ]
```

---

## Submission Checklist

- [☑️] Student name and ID filled in
- [☑️] Q1, Q2, Q3 answered
- [ ☑️] Experiment 1: table filled, packing list pasted, plot observation written
- [ ☑️] Experiment 2: results table filled (3 rows), observation and answer written
- [ ☑️] Summary table completed and reflection written
- [ ☑️] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
