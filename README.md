# The 90-Minute Engine: How “Physical Resilience”  Won the Match

## Overview
This project analyzes professional football tracking data to investigate how **physical resilience** and **recovery efficiency** influence match outcomes. By processing over 145,000 data points from a professional match, the study uncovers the physical story behind a multi-goal victory.


---

## Data Source
- Metrica Sports Sample Data

---

## Dataset Overview
The raw data was initially obtained from Metrica Sports' Github account in **CSV format**.

It consists of high-frequency **optical tracking data** and **event logs**:
- Duration: 96 minutes and 40 seconds of play.
- Frequency: 25 frames per second (total 145,006 rows).
- Scope: Normalized X,Y coordinates for all 28 players and the ball throughout the game.
  
Event Data: Action logs including passes, shots, ball recoveries, and goal instances.

---

## Data Transformation
Before conducting my analysis, I performed several critical data transformation steps on the raw tracking data to ensure its accuracy:
- **Playing Direction Normalization**: I accounted for teams switching sides at halftime by flipping the second-half coordinates. This ensured the game appeared to move in a single direction throughout the entire dataset.
- **Coordinate Scaling**: I scaled the raw normalized X,Y coordinates, which ranged from 0 to 1, to the actual dimensions of the pitch (105m x 68m). This allowed me to calculate real-world physical distances.
- **Velocity Calculation**: I derived instantaneous player velocities and speeds by measuring the change in player positions over time. I used the data's frequency of 25 frames per second (dt = 0.04s) to perform these calculations.
- **Data Smoothing**: To remove "noise" and frame-by-frame jitters that could have artificially inflated running statistics, I applied a filter, such as a Savitzky-Golay filter or Moving Average, to the calculated velocities.

---

## Key Metrics to evaluate Stamina
The following metrics were used to evaluate performance decay and recovery efficiency:
- **Total Distance Covered**: Baseline work rate for each half (elite players typically cover 10–13 km per match).
- **High-Speed Running (HSR)**: Distance covered above 7 m/s, indicating explosive capacity and neuromuscular exhaustion.
- **Metres per Minute (m/min)**: Average intensity analyzed over 15-minute segments to identify performance degradation over time.
- **Repeat Sprint Ability (RSA)**: Measurement of the frequency and recovery time required between high-speed efforts.


---

## Key Findings
- **"Chasing Shadows" Paradox**: The Away Team’s total distance increased in the second half due to reactive "shuttling" to cover gaps, leading to faster burnout compared to the Home Team's proactive efficiency.
- **Neuromuscular Exhaustion**: The Away Team's primary threats suffered a crash in high-speed running (HSR) capacity, while the Home Team's "engines" maintained explosive power until the final whistle.
- **Substitution Impact**: The Home Team’s introduction of Player 13 created a decisive speed mismatch, as the sub sprinted at 113m/min against an exhausted defense.
- **Recovery Speed**: Most Home starters achieved low median recovery times, whereas Away players were physically erratic with much longer recovery gaps.

---

## Tools Used
- Python
- pandas
- matplotlib
- numpy
- seaborn
- scipy
- Google Colab

---
