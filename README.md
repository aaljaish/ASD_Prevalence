# Analysis to estimate autism prevalence among Canadian adults
The code is manipulating a dataset based on ASD (Autism Spectrum Disorder). It's iterating through groups of data by province and sex, calculating various statistics such as ASD prevalence, mortality rate, number of ASD cases, ASD survival rate, rho_adj, and gamma_adj, and appending these values to respective lists.

**Methods**
We used a Monte Carlo simulation to estimate the prevalence of Autism Spectrum Disorder (ASD) across various Canadian provinces. This involved considering a range of factors such as age, sex, population sizes, age-specific mortality rates,  and relative rate of mortality for those with ASD compared to those without.

Initially, we categorized our dataset into distinct groups based on province and sex, with each group encapsulating data associated with age, population, and several ASD-related parameters.

Within each simulation run, the hazard ratio for death was recalculated by selecting a value from a normal distribution defined by a specific mean and standard error. This technique facilitated the simulation of a plausible level of random variation. For every province-sex group, the initial calculation of ASD prevalence was based on a presumed normal distribution centred around the given prevalence value and its standard error. 

Following this, within each age category of a group, we calculated several variables. These included the ASD mortality rate, calculated as the product of the group's hazard ratio for death and the survival rate of the general population. The number of ASD cases was also calculated, using the group's population and the ASD prevalence. An adjusted ASD prevalence was computed to reflect the probable effect of the ASD survival rate on the prevalence. Lastly, the adjusted number of ASD cases in the population was estimated by multiplying the group's population by the adjusted ASD prevalence.

This procedure was repeated across all age groups within each province-sex grouping. The data from each simulation run, including the calculated values and the province, sex, age, and population data, was then aggregated. 

This approach was conducted over a pre-set number of simulations, each iteration generating a unique data scenario, thereby constructing a wide array of plausible outcomes. This extensive collection of scenarios enabled a comprehensive understanding of the variability and potential range of ASD prevalence across Canadian provinces.

This simulation-based approach provided a robust mechanism for estimating ASD prevalence, taking into account inherent uncertainties in population-based studies and potential random variation in key parameters such as the hazard ratio for death and ASD prevalence.

# Description of columns in "Clean ASD Dataset.csv" file.

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
