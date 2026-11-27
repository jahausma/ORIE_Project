# ORIE 5530 Project: NYC Citi Bike
 
Jacob Hausmann (jdh389), Caleb Bettcher (cb2223)
 
## Files
 
- `ORIE_5530_Notebook.ipynb`: **main notebook.** Produces every figure and table in the report.
- `part2_additional_analysis.ipynb`: additional checks for Part II (exact vs. simulated probabilities, sensitivity to the starting state, exact best starting level). Self-contained; reloads the data itself.
- `images/`: figures written by the notebooks and included in the report.
## Software
 
Python 3.10 or newer, with:
 
```
pip install pandas numpy matplotlib scipy jupyter
```
 
## Data
 
August 2026 NYC Citi Bike trip data, `202608-citibike-tripdata.zip`, from
https://s3.amazonaws.com/tripdata/index.html (the NYC archive, not the `JC-` Jersey City file).
Unzip it and put all of its CSV files in a folder named `Data/` next to the notebooks:
 
```
Data/
  202608-citibike-tripdata_1.csv
  202608-citibike-tripdata_2.csv
  ...
ORIE_5530_Notebook.ipynb
part2_additional_analysis.ipynb
```
 
## Reproducing the report
 
1. Open `ORIE_5530_Notebook.ipynb` and run all cells from top to bottom (Kernel → Restart & Run All). Cells must run in order as the Part I data-consolidation cell filters `df` down to the three selected stations, so the warm-up cells above it must run first.
2. Figures are saved to `images/`. Tables in the report are copied from the printed cell outputs.
3. Optionally, run `part2_additional_analysis.ipynb` for the supplementary checks.
## Settings and random seeds
 
All model settings are defined in the "Selected Variables" cell of the main notebook:
 
| Setting | Value |
|---|---|
| Stations | W 21 St & 6 Ave, 11 Ave & W 41 St, S 2 St & Kent Ave |
| Capacities (docks) | 63, 48, 44 |
| AM block | weekdays 6:00–10:59 |
| PM block | weekdays 15:00–19:59 |
| Time step | 10 minutes (30 steps per block) |
| Simulation runs | 10,000 per station and block (best-start search: 2,000 per starting level) |
| Starting state (baseline) | half capacity, `capacity // 2` |
| Random seed | `SEED = 0`, via `np.random.default_rng(SEED)` |
 
The supplementary notebook also uses `SEED = 0` but runs its own simulations so its values differ from the main notebook's within the Monte Carlo error range.
