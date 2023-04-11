### Determining what factors of a building affect it’s Energy Use Intensity (measured in units billed for gas and electricity)

**Angad Deep Singh**

#### Executive summary

The purpose of the analysis is to determine what factors affect the energy use intensity of a building, so that we can design better buildings and operate them more efficiently. Furthermore, I used past data to predict energy use intensity of buildings given existing parameters so that we can plan and operate our grid energy sources in a manner that their perfomance can be optimized ( since we would know the output needed).

Ridge regression with polynomial degree of 3 gave the lowest mean squared error and hence was used to create the final model. This would allows us to get maximum accuracy in our predictions. 

Results:

    a)Energy star rating had the biggest impact on energy use intensity with 20% of energy being used in the building that had the highest rating vs the lowest rating
    b) In-patient health care facilities had the higest mean energy use intensity of 232 units
    c) Heating degree days had the higest impact on EUI. The peak mean EUI is at 6863- total heating and cooling degree days from where there is a decline. The peak total heating and cooling degree days perfectly coincides with peak heating degree days
    d) Highest Energy Use Intensity occured when the average temperature was between 55-60F, with 124 units being consumed at 50F
    e) State 6 has the highest median EUI of 84 units and the largest spread of EUI among its building stock, followed by state 10
    f) EUI has seen a rapid decline post the year 2000. The EUI drop from 1999 to 2014 is ~ 50 units of electricity and gas consumed ( 50% reduction)
    
Recommendations:

Recommendations for each stakeholder are as follows:

    a) Designers: 
            1) Design buildings and retrofit them to get the highest energy star rating. The increased cost will pay itself back with 80% reduction in energy use.
            2) In-patient health care facilities need to have the most energy efficiency measures in design like LED lights, high coefficient of performance equipment, excellent insulation, double pane windows etc
            3) Design buildings to maximize heat gain as heating is the dominant use of energy, with 50F being the temperature where all heat loss should be calculated as it is the temperature at which EUI is maximum.
          
    b) Building operators:
            1) In-patient health care facilities should get energy efficiency retrofits ( lower energy usage equipment, lights, better insulation etc)
            2) Retrofit older buildings ( built before 2000) with newer equipment since equipment post 2000 seems to consume less energy as overall energy use post 2000 has decreased
            3) When predicted temperature is between 55-60F, building operators should try to use on-site renewable sources of energy to lower energy demand from the grid
            
    c) Lawmakers/policy makes: 
            1) Incentivize lower energy use among buildings and target regions with high median EUI, like state 6 and state 10.
            2) Provide cheap financing to make retrofits to more energy efficient equipment in regions with high median EUI. 

The next steps can be as follows:

    a) Improve the presented models (increased epochs in deep learning models, higher polynomials of data) to improve outcomes. Ensemble techniques may also be attempted to see if there is any improvement in performance
    b) Measure the results of the test data with actual field data to validate this model and refine it further.



#### Rationale

Buildings play a critical role in our overall energy consumption. 40% of all our energy consumption comes from our building stock, which often has a life of ~50-70 years. In a world where we are facing climate change, energy uncertainity and growing need for energy independence for each country, knowing what factors can reduce energy needs of our building would allow designers to account for those factors to reduce overall energy needs. Furthermore, it would allow building operators to operate buildings while accounting for these factors to minimize energy use. 


#### Research Question

The research question is : What factors affect energy use intensity of a building such that we can optimize building energy use?


#### Data Sources

I would be using data from the following source: https://www.kaggle.com/competitions/widsdatathon2022/data

#### Methodology

###### Modeling method:

I used Linear Regression, Ridge regression, Lasso regression and Sequential Deep Learning using Keras for linear regression, to create models of various polynomial degrees on the features, to determine the best fit for predicting the outcome. 

To determine the appropriate parameters I used GridsearchCV and determined the optimal parameters for each of the models. 

The basis for picking the model was the model with the lowest mean squared error as this allowed for maximizing the accuracy of the prediction

###### Assumptions of the analysis:

    a)Highly correlated factors were dropped to improve performance of the model and reduce compute expense. The factors that had been dropped and the reasons are as follows:
                a.Days_below_20F, Days_below_10F, Days_below_0F: Days below 30F incorporates all this information.
                b.Days_above_90F, Days_above_100F, Days_above_110F: Days above 80F incorporates all this information.
                c.January_min_temp,  February_min_temp, March_min_temp, April_min_temp, May_min_temp, June_min_temp, July_min_temp, August_min_temp, September_min_temp, October_min_temp, November_min_temp and December_min_temp  : Each of these are highly correlated with heating degree days and hence have been dropped   
                d.January_max_temp, February_max_temp, March_max_temp, April_max_temp, May_max_temp, June_max_temp, July_max_temp, August_max_temp, September_max_temp, October_max_temp, November_max_temp and December_max_temp:  Each of these are highly correlated with cooling degree days and hence have been dropped.

    b)The analysis was carried out to minimize mean squared error of the model so that we can the most accurate prediction of EUI. 

###### Modeling results:
Ridge regression with polynomial degree of 3 gave the lowest mean squared error and hence was used to create the final model. 

#### Results

The results of the data analysis is as follows: 

    a)The factors that affected the EUI the most are as follows:
                a.Energy star rating
                b.Facility type
                c.Heating degree days 
                d.Days below 30F
                e.Days above 80 F
                f.Snowfall in inches
                g.Average temperature

    b)There is an inverse relationship between energy star rating and energy use intensity, with energy use intensity decreasing as the star rating increases. The highest energy star rating (100) used 20% (34 units of gas and electricity) compared to the lowest energy star rating building (1) that used (157 units of gas and electricity)
    c)In-patient health care facilities were the most energy intensive buildings with an EUI of 240 units of gas and electricity. This is closely followed by Grocery store, with an average EUI of 232 units, and data center with an average EUI of 183 units.
    d)Heating degree days resulted in an overwhelming amount of Energy use intensity increase as compared to cooling degree days. The total degree days that resulted in the most energy use intensity perfectly coincided with the peak of heating degree days. The peak mean EUI is at 6863- total heating and cooling degree days from where there is a decline. 
    e) Highest Energy Use Intensity occured when the average temperature was between 55-60F, with 124 units being consumed at 50F 
    f)State 6 has the highest median EUI of 84 units and the largest spread of EUI among its building stock, followed by state 10
    g)EUI has seen a rapid decline post the year 2000 and prior to the building energy use intensity remained "flat" with some localized peaks and troughs. The EUI drop from 1999 to 2014 is ~ 50 units of electricity and gas consumed ( 50% reduction).



#### Recommendations:

Recommendations for each stakeholder are as follows:

    a) Designers: 
            1) Design buildings and retrofit them to get the highest energy star rating. The increased cost will pay itself back with 80% reduction in energy use.
            2) In-patient health care facilities need to have the most energy efficiency measures in design like LED lights, high coefficient of performance equipment, excellent insulation, double pane windows etc
            3) Design buildings to maximize heat gain as heating is the dominant use of energy, with 50F being the temperature where all heat loss should be calculated as it is the temperature at which EUI is maximum.
          
    b) Building operators:
            1) In-patient health care facilities should get energy efficiency retrofits ( lower energy usage equipment, lights, better insulation etc)
            2) Retrofit older buildings ( built before 2000) with newer equipment since equipment post 2000 seems to consume less energy as overall energy use post 2000 has decreased
            3) When predicted temperature is between 55-60F, building operators should try to use on-site renewable sources of energy to lower energy demand from the grid
            
    c) Lawmakers/policy makes: 
            1) Incentivize lower energy use among buildings and target regions with high median EUI, like state 6 and state 10.
            2) Provide cheap financing to make retrofits to more energy efficient equipment in regions with high median EUI. 


#### Link to the notebook

- [Link to notebook: https://github.com/adsingh1912/Report-and-Presentation.git ] 



##### Next Steps:


The next steps can be as follows:

    a) Improve the presented models: 
         1) increased epochs in deep learning models, 
         2) higher polynomials of data to improve outcomes. 
         3) using wnsemble techniques to see if combination of models can give more accurate results.
     
     Each of the above mentioned steps can be attempted but may be very computationally expensive so the cost must be weighed against the expenses.  
     
    b) Measure the results of the test data with actual field data to validate this model and refine it further.


##### Contact and Further Information

Contact: Angad Deep Singh
