*this project was originally hosted on an enterprise Github account. I moved it here to make it public. 

# Octopus Group Project: Predict Recidivism
*Collaborators: Abhay A., Gabby C., Scott T., and Yadan T.*

## Problem Statement
**Can we use machine learning models to predict recidivism within a period of three years?**

### Initial Research and Project Path
We started off wanting to find a correlation between mental health spending and incarceration rates. We then reviewed state-level data to find if states could reduce incarceration rates using mental health services. During the latter part of discovery, we found a recidivism challenge from the US Department of Justice and that influenced how we approach recidivism, mental health, and incarceration.

We hope to understand the **risks associated with recidivism.** We’re also hoping to find possible correlations between mental health spending and incarceration rates, which might provide insight into which states should invest more in mental healthcare services.

### Overview: Mental Health and Incarceration
There are 1.2 million individuals living with mental illness are in jail and prison. Typically, imprisonment begins with low-level offenses. Previous studies have shown a positive correlation between rates of adults in the criminal justice system and lack of access to mental health care. In other words, states with less access to mental health care have more adults in the criminal justice system. ([*link to source*](https://www.apa.org/monitor/2019/03/mental-heath-inmates))

COMPAS (Correctional Offender Management Profile for Alternative Sanctions) is an existing and widely used criminal risk assessment tool. This software does not include race, but other data correlated to race could lead to racial disparities. COMPAS appeared to favor white defendants over black defendants by underpredicting recidivism for whites and overpredicting for blacks.
 ([*link to source*](https://www.science.org/doi/10.1126/sciadv.aao5580))

This analysis is important as about 37% of prisoners have a history of mental health disorders and prisoners can often lose their access to mental health services during imprisonment. Thomas Fagan of Nova Southeastern University states that “we lock up people with mental health problems when we should really be treating these people in the community.”
 ([*link to source*](https://www.apa.org/monitor/2019/03/mental-heath-inmates))

## Assumptions  
Over 10% of the data in gang affiliation and prison offenses is missing. There are columns that are unreasonable to impute (we cannot assign gang affiliation and/or prison offense to individuals). In this study we are using recidivism score as a measurement of successful and effective state mental health spending.

---

## Original Datasets
|Data description|link|
|---|---|
|Census_incarceration_data|🔗[link](https://observablehq.com/@themarshallproject/adults-in-correctional-facilities-from-decennial-census)
|Public_health_spending_data|🔗[link](https://knoema.com/SHPCPHF2020/per-capita-public-health-funding-in-u-s-states)
|Mental_health_spending_data|🔗[link](https://rehabs.com/explore/mental-health-spending-by-state-across-the-us/)
|Recidivism_data|🔗[link](https://data.ojp.usdoj.gov/stories/s/daxx-hznc)

## Code 📁
The "code" markdown file in the code folder contains links to all five of the Colab notebooks, but for good measure they are listed here as well.
- **Colab Notebooks**
    - [Initial discovery, datasets, and EDA](https://colab.research.google.com/drive/1jK4M9pc_FpdObrVaaim9pQZajSRE44AG?usp=sharing)
    - [Predict recidivism datasets (missing data, EDA, etc.)](https://colab.research.google.com/drive/1w9IANHhwLdke0Wx9ytWmr_5OU-PvNcd_?usp=sharing)
    - [Model template for Neural Network](https://colab.research.google.com/drive/13MjCsRTrewGnB8dqYIRTWh-5OAUmcJlu?usp=sharing)
    - [XGBoost model](https://colab.research.google.com/drive/1YXlwr6YFaRKPbAEv7Q3zd5UdaIXhQfFd?usp=sharing)
    - [Random Forest model](https://colab.research.google.com/drive/19iyntxHoeT1rpQFUWXhLeQhBqsTbc1eO?usp=sharing)

## Data 📁
We worked through and cleaned a few versions of training and test data. (Older versions can be found in the "archive" folder.) The final versions of training and testing data are "**train_cleaned_yt.csv**" and "**test_cleaned_yt**". 


---

## EDA and Models
* Correlations and visualizations:
   * recidivism by gender and race had show low correlation with recidivism. --Model is not biased toward race and gender therefore there is less chance of enthical issue.
   * recidivism by prison offense is showing property offense has the highest chance for recommiting within 3 years
   * Inmates with confirmed gang affiliation record showed a much higher rate of recommitting
* Missing data handling:
   * Over 10% of the data in gang affiliation and prison offenses is missing.
   * There are columns that are unreasonable to impute.
   * We cannot assign gang affiliation and/or a prison offense to individuals.
* In this study we are using recidivism score as a measurement of successful and effective state mental health spending.
* Correlations between
* For the remaining features, not a very strong correlation with target variable.
## Modeling approach
### Baseline model accuracy
* baseline model has about 57% accuracy
### ML models
* KNN model:
   * Neural network modeling performed moderately well.
   * KNN analysis yielded a score of ~68.6% with grid searching over neurons and 1 or 2 layers. And Model was slightly overfitted.
   * Additional and “deeper” grid searching over parameters and 4 hidden and dropout layers with (drop rate 0.2) achieved a score of ~68.74%, not improvement on accuracy score, but model is not overfitted.
   * F1_score: 75.2%
   * Recall_score: 81.7%
* XGBoost model:
   * XGBoost model had an accuracy score of 67.2%, before hyperparameter tuning.
   * F1_score: 69%
   * Recall_score: 63%
   * Grid Search results showed overfitting.
* Random Forest:
   * Random Forest was the worst model performed.
   * It achieved a score of ~66.70% with no hyperparameter tuning
   * After grid searching over parameters, it was able to achieve a score of ~67.71% which only went up 1%
   * F1 score: 74.9%
   * Recall score: 82.4%
   * Both models were definitely an overfit.*

## Conclusions
We found a negative or low correlation between select features (gender, age, race, etc.) and recidivism within three years. The next steps for this study would be to find similar recidivism data for another state in order to compare mental health spending with incarceration rates and recidivism predictions between states.
