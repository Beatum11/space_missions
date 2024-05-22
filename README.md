# Space Missions Analysis

This repository contains an analysis of space missions from 1957 onwards. The dataset used for this analysis is sourced from [Kaggle: All Space Missions from 1957](https://www.kaggle.com/datasets/agirlcoding/all-space-missions-from-1957).

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Data Cleaning](#data-cleaning)
- [Analysis](#analysis)
- [Conclusions](#conclusions)
- [How to Use](#how-to-use)
- [Dependencies](#dependencies)

## Introduction
This project aims to analyze space missions conducted by various organizations worldwide since the inception of space exploration. We focus on trends in successful and unsuccessful missions, changes over time, and the impact of specific companies on mission success.

## Dataset
The dataset includes details of space missions such as:
- Company name
- Location
- Date and time of the mission
- Rocket and mission details
- Rocket status
- Mission status

Source: [Kaggle: All Space Missions from 1957](https://www.kaggle.com/datasets/agirlcoding/all-space-missions-from-1957)

## Data Cleaning
The dataset required some cleaning and preprocessing before analysis:
1. I just filled missing values in the `Price` column with 0.

```python
df['Date'] = pd.to_datetime(df['Date'])
df['Price'] = df['Price'].fillna(0)
```

## Analysis
The analysis is divided into several sections:
1. **Trend Analysis**: Examining the number of successful and unsuccessful missions over time.
2. **Company Analysis**: Investigating the performance of different companies in terms of mission success.

### Trend Analysis
I analyzed the trends in space missions from 1957 to the present. Key observations include:
- Significant increase in missions during the 1960s and 1970s (Cold War period).
- A period of stagnation from the 1980s to early 2000s.
- A recent surge in missions since 2015, driven by private companies like SpaceX.

```python
status_by_year.plot(kind='bar', stacked=True, figsize=(14, 6))
plt.xlabel('Year')
plt.ylabel('Number of Missions')
plt.title('Number of Successful and Unsuccessful Missions Over Time')
plt.legend(title='Mission Status')
plt.show()
```

### Company Analysis
I evaluated whether the success of a mission depends on the company conducting it. The analysis showed:
- The RVSN USSR had the highest number of successful missions during its operational period.
- Companies like SpaceX and CASC have shown a significant increase in successful missions in recent years.

```python
success_missions_df = df[df['MissionStatus'] == 'Success']
company_success = success_missions_df.groupby('Company').size().reset_index(name='TotalSuccess')
company_success = company_success.sort_values(by='TotalSuccess', ascending=False).head(10)
```

## Conclusions
1. **Cold War Impact**: The Cold War era saw a peak in space missions, driven by the USA and USSR.
2. **Modern Era**: There is a resurgence in space missions, particularly by private companies, highlighting advancements in technology and increased investments.

## Dependencies
The analysis was performed using Python and the following libraries:
- pandas
- matplotlib

Ensure you have these installed before running the notebook.

```bash
pip install pandas matplotlib
```

## Acknowledgements
The dataset used in this analysis is sourced from [Kaggle: All Space Missions from 1957](https://www.kaggle.com/datasets/agirlcoding/all-space-missions-from-1957).
