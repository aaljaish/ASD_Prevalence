# Analysis to estimate autism prevalence among Canadian adults
The code is manipulating a dataset based on ASD (Autism Spectrum Disorder). It's iterating through groups of data by province and sex, calculating various statistics (e.g., ASD prevalence, mortality rate, number of ASD cases, ASD survival rate)and appending these values to respective lists.

## Methods
**Design**: A Monte Carlo simulation modelling approach was employed. Input parameters included adult population estimates and mortality rates; autism population all-cause mortality risk ratios; and autism prevalence estimates derived from child and youth data due to the lack of adult data. This approach was executed through 10 000 simulations, with each iteration generating a distinct data scenario. Prevalence estimates were reported as the mean with the 2.5th and 97.5th percentiles, corresponding to a 95% simulation interval (SI).

**Setting**: Where possible, Canadian data sources were used, including the 2019 Canadian Health Survey on Children and Youth and Statistics Canada mortality rates and population estimates.

**Primary outcome**: National prevalence estimates of autistic adults living in private dwellings in Canada, with variations in prevalence by sex at birth and province/territory considered.

**Please see full details of methods here**: https://doi.org/10.1136/bmjopen-2024-089414

## Description of columns in "Clean ASD Dataset.csv" file.

data=pd.read_csv('Clean ASD Dataset.csv')
data.head()

* province = The name of Canadain province
* sex = sex Male/Female
* Age = Age of group increasing by 1 year increments
* population = Population size for the respective province, sex, and age group. This 2019 data was obtained from Statistics Canada.
* mortality_rate = Mortality rate per 1000 individuals from the general population. This 2019 data was obtained from Statistics Canada.
* asd_prevalence = asd prevalence from 2019 CHSCY for those 1-17 years of age.
* asd_prevalence_se = standard error for asd prevalence from 2019 CHSCY for those 1-17 years of age.
* hazard_ratio = hazard ratio for death for the respective sex. We assumed constant hazard ratio for all ages and all provinces.
* se = standard error for the hazard ratio for death in the respective sex. We assumed constant hazard ratio for all ages and all provinces.
* pop_survival = probability of survival for the respective province, sex, and age group. This variable was derived from mortality_rate column.
