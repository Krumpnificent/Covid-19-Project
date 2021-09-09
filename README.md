# NIGERIA COVID-19 ANALYSIS

## PROJECT DESCRIPTION

   The essence of this project is to analyze the effects of the covid-19 pandemic on the Nigerian economy and Nigerians as well.
In this analysis keys areas and factors and factors were considered and they include:

- impact on initial and revised bugets for the year 2020
- rate of contraction
- confirmed cases, deaths, admission and discharges of infected individuals.
- effects on nigeria's GDP in the year 2020 and also comparison with previous years and so on.
    
    
    
    
    
# PROJECT STEPS


### LOADING DATA SETS

   Firstly, all the necessary libraries and functions required for data manipulation and visulization for the scope of this project were imported; some of these include pandas, numpy, seaborn, matplotlib, beautiful soup, request, warnings etc


going forward, i imported the data sets required for the analysis.
The ndcd dataset was imported using the folllowing approach:

`url = 'https://covid19.ncdc.gov.ng'`

`dfs = pd.read_html(url)`

`ncdc = dfs[0]`


after which is used the following approach to verify that i have loaded the correct dataset.

`ncdc.head()`


then, converting into a csv file using the folowing code:

`ncdc.to_csv('ncdc.csv', index=False)`



subsequently, other datasets' CSV files were imported using the folowing code format:

`var = 'csv file'`

`var1 = pd.read_csv('var')`
    
This method was used for other required global and external datasets.






### DATA EXPLORATION

For all the daframes(df for short), i used the `df.head()` and `df.info()` to get an abridged view if the dataframes and description of data in the dataframes.





### DATA CLEANING AND PREPARATION


I converveted columns to their appropriate types. 
Numerical columns were converted to int type and after commas have been removed from numerical data dor ease of computation. date columns were also converted to the appropriate datetime for bat using `pd.to_datetime()`


columns were renamed using `df.rename()` method for clarity, ease of typing and ease of recognition.

i extracted the daily data for Nigeria  from the global daily cases data using : `Nigeria_daily_confirmed = global_confirmed.loc[(global_confirmed['Country/Region'] == 'Nigeria')]`



I completed the data cleaning tasks listed below

- TODO B - Get a Pandas DataFrame for Daily Confirmed Cases in Nigeria. Columns are Date and Cases
- TODO C - Get a Pandas DataFrame for Daily Recovered Cases in Nigeria. Columns are Date and Cases
- TODO D - Get a Pandas DataFrame for Daily Death Cases in Nigeria. Columns are Date and Cases

the approach for completing this tasks was
- getting the daily confirmed cases in Nigeria from the global data set for daily confirmed cases.
- getting the daily recovered cases in Nigeria frm the global dataset for daily recoverd cases.
- getting the daily death cases in Nigeria from the global dataset for daily deaths.
this was done using the codes 
    - `Nigeria_daily_recovery = global_recovered.loc[(global_recovered['Country/Region'] == 'Nigeria')]`
    
    - `Nigeria_daily_deaths = global_deaths.loc[(global_deaths['Country/Region'] == 'Nigeria')]`
    
    - `Nigeria_daily_confirmed = global_confirmed.loc[(global_confirmed['Country/Region'] == 'Nigeria')]`
    and using df.melt() method to create new dataframes of each with the dates and cases as columns
    
    
    

### ANALYSIS

The first tasks caried out here were the  Generation of plots that shows the Top 10 states in terms of Confirmed, Recovered and Death cases by Laboratory test In Nigeria. This is only acurate if the values were first sorted using the `df.sort_values()` method, sorting in a **descending** order and using the *.head()* method to specify the number of required rows.

A line plot for the total daily confirmed, recovered and death cases in Nigeria was generated for which the `pd.melt()` method came in quite handy and the daily infection rate was evaluated using the `diff` method. From this, the max daily infection rate was deduced as well as its date.


further more, i combined the external dataset and the NCDC COVID-19 dataset on the States column for purpose of comparison as a new dataframe and sorted according to the atstes with the top 10 condirmed cases in descending order using `nlargest` method. the Overall CCVI Index and confirmed cases were ploted on the same axes and agaist the states to show how the vulnerablity of a states plays a role in the Covid-19 impact in it.


In order to further undertsand the correclation of the various factors considered, i used a regression plot to to analyze the correlation of a number of facotrs and with every plot, my insight/observations were carefully outlined.


I analyzed the impact of Covid-19 on the Nigerian economy.
to achieve this, i plotted a bar plot of GDP against years(ranging from 2014 - 2020) while using Q1, Q2, Q3 and Q4 as hue. the aim is to examine the gdp growth on quaterly basis from the year 2014 - 2020.
I added an axhline to the Q2 value for 2020 see compare the gdp level with other quaters of other years(bearing their second quaters in mind.


Lastly, i computed the different between the initial and revised budgets and summed up the total amount deducted from the initial budget for the revised budget as a result of Covid-19 impact and i obtained the value **3889.7299999999996 BN** which is approximately **4TN**. This only implies that projects or areas of projects must be suspended given the revenue allocated.




### RESULTS

**'Confirmed Cases' vs 'Population Density'**

* I deduced from the regression plot that there is a possitive correlation between the population desntity and the Confirmed Cases. This shows that the more the number of people in a given space, the higher the rate of transmission if anyone comes in contact with an infected person. this is the reason the impoertance of social distancing could not be overemphasized.

* However, the fact that the correclation is not a strong one, tells us that there are other factors involved as regards the the high number of confirmed cases.




**'Health System' vs 'Deaths'**

* Drom this plot, i deduced that inadequate health care plays a huge role is reducing the number of deaths. There is a better chance of survival when a patient is admitted to a well-equiped health care facility.




**'Confirmed Cases' vs 'Socio-Economic'**

I deduced from this plot that the higher the average socio-economic class of a state, the lower the number of cases. 

To give a few practical examples:
Car owners are less likely to contract the disease than people who use comercial transport.

People who own smart devices are better informed about preventive measures that people don't and people who get informed through word of mouth; and the list goes on.





**'Acute IHR' vs 'Deaths'**

The plot showed a negative correlation between 'Acute IHR' and 'Deaths', it shows that a country must adhere to the International Health Regulations provided and also, health organisations must be encouraged to do better to improve these regulations and save more lives.





**'Year' vs 'GDP'**

Nigeria's GDP in the first quater of 2020 was the highest of all first quaters since 2014 but the positive momentum was impeeded due to the impact of the COVID-19 outbreak whose effect is seen in the second quater of the year 2020 which also corresponds with the lockdown period.

The 2020 Q2 was the first time Nigerias GDP didn't increase on a quaterly basis since 2014 and is also recorded as the 3rd least GDP since 2014(with data for 2020 Q4 yet to be collated/recorded).





### CONCLUSION

This project was carried out to analyze the general impact of the covid-19 outbreak on Nigeria; ranging from the number of confirmed cases, admissions, discharges and deaths recorded around the 36 states and Federal Capital Teritory in Nigeria.

The economic Impact of the pandemic was also analyzed, with Nigeria seeing a decline in its real gdp in the second quater of the year 2020 as a result of the lockdown. from the analysis provided, it was shown that Nigeria failed to maintain its quaterly gdp uptrend for the first time since 2014 in the year 2020 with the real gdp of the 2nd quater being significantly less than that of the first quater.

Some other factors which contributed to the spread of the virus were also analyzed ranging from the total population, population indeces, socia-economic factors etc from the various states in nigeria. These analysis was carried from combined datasets.

Detailed plots were provided for easy visualization and understanding of anaylytical findings in this project. 

Through this analysis, a lot of key 'what', 'why', 'when' questions have been answered.
