# Team-25
## 1. Question
How does the relationship between political misinformation and life satisfaction change across demographics?

## 2. Dataset Information 
Politifact Dataset: With 2520 claims that have been curated from Politifact, a prominent fact-checking organisation in the United States.

YouGov Poll: Life satisfaction poll from 2020 to 2026, split by age bracket, ethnicity, education and gender. 

## 3. Dataset Cleaning
### Politifact Dataset
- Checked dataset for missing values
- Renamed 'barely-true' to 'mostly-false' as it was a barely used label
- Removed 'full-flop' and 'half-flip' as it measures change in position, not accuracy of statement
- Changed the format of the date column into ISO 8601 (YYYY-MM-DD)
- Recoded the fact-o-meter data into numbers represented as such:

| Fact-o-meter | Score|
|--------------|------|
| true         | 6    |
| mostly-true  | 5    |
| half-true    | 4    |
| mostly-false | 3    |
| false        | 2    |
| pants-fire   | 1    |

- The percentage of false claims with score 1-3 out of all evaluated claims were calculated for every month

### YouGov Poll 
- Checked for missing values and impossible entries
- Took the mean weighted by score of all responses to produce one data point per month of average life satisfaction for that demographic
- Demographics covered are:
  - Age: 18-29, 30-44, 45-64, 65-79
  - Gender: Male, Female
  - Education: No high school, high school grad, some college, 2 years (of college), 4 years (of college), post grad
  - Ethnicity: White, Black, Hispanic, Asian, Native American, Middle Eastern, 2 or more ethnicities, Other

### Merging the datasets
- Datasets were (inner) joined on month to obtain a table of the percentage of false claims and average life satisfaction for that demographic
