**Introduction**

Vaccines developed against viruses have saved many lives, however,
safety concerns and efficacy are potential problems in current vaccines.
Because of these unresolved problems with current vaccines, there have
been increasing concerns about teenagers’ vaccination, resulting in
anti-vaccination movement across the world. The anti-vaccination
movement has a long history, and the widespread anti-vaccination
movement in the United States began in 2007. One consequence of the
anti-vaccination movement is the recent Measles Outbreak in the United
States. In 2014, after 14 years of Measles being eradicated in America,
there was a Measles Outbreak started in California. The recent outbreak
indicated that the number of people that are choosing not to vaccinate
their children is too great to maintain herd immunity. In this report,
the vaccination rates in different families across the United States are
analyzed, and the families with higher vaccination rates will be
identified. The differences in the vaccination coverage rates in
different families are useful to increase teenagers’ vaccinated rates by
targeting lower vaccination rate families.

**Data Processing**

The dataset comes from The National Immunization Survey – Teen
(NIS-Teen) in 2017, the NIS-Teen is a list-assisted random-digit-dialing
telephone survey of households followed by a mailed survey to teens’
immunization providers to monitor teen immunization coverage. The
original dataset contains 43591 observations of 691 variables, only the
information from the telephone survey is used in the final analysis,
because there are a large portion of missing values and unrelated
information in the mailed survey.

Only 12 variables are included in the final report, which is shown in
Table 1. The response variable is “Vaccinated”, which is defined as 1
when the child is vaccinated to all the vaccines included in the survey.
Other variables are mostly demographic characteristics, such as age,
sex, race, state, and region. Family-related variables are useful to
infer family impact on vaccination rates, including family size,
children number, the income of the household, and mother’s education
level. One other important variable is “Provider” if the child has
adequate provider information, then the child is categorized as 1.
“Provider” is a useful identifier because a child with adequate provider
information has a higher probability to get vaccinated, and also
indicating parents paying more attention to child’s immunity protection.

*Table. 1 Code Book*

<table>
<colgroup>
<col style="width: 26%" />
<col style="width: 36%" />
<col style="width: 36%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: center;">Variable</th>
<th style="text-align: center;">Type</th>
<th style="text-align: center;">Explanation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">id</td>
<td style="text-align: center;">Identifier</td>
<td style="text-align: center;">Unique Tenn Identifier</td>
</tr>
<tr class="even">
<td style="text-align: center;">Vaccinated</td>
<td style="text-align: center;">Binary</td>
<td style="text-align: center;">1: Vaccinated to all vaccines 0: Not vaccinated to all vaccines</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Age</td>
<td style="text-align: center;">Factor</td>
<td style="text-align: center;">Teen’s age (13 to 17)</td>
</tr>
<tr class="even">
<td style="text-align: center;">Sex</td>
<td style="text-align: center;">Binary</td>
<td style="text-align: center;">Male or Female</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Family Size</td>
<td style="text-align: center;">Factor</td>
<td style="text-align: center;">Number of people in household (1 to 8)</td>
</tr>
<tr class="even">
<td style="text-align: center;">Children</td>
<td style="text-align: center;">Factor</td>
<td style="text-align: center;">Number of children in household (1, 2 or 3, and 3 more)</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Race</td>
<td style="text-align: center;">Factor</td>
<td style="text-align: center;">Race of teen (Hispanic, White, Black and Other)</td>
</tr>
<tr class="even">
<td style="text-align: center;">Income</td>
<td style="text-align: center;">Factor</td>
<td style="text-align: center;">Family Income (Above Poverty &gt;75K,Above Poverty &lt;=75K, Below Poverty, Unknown)</td>
</tr>
<tr class="odd">
<td style="text-align: center;">State</td>
<td style="text-align: center;">Factor</td>
<td style="text-align: center;">True state of residence</td>
</tr>
<tr class="even">
<td style="text-align: center;">Provider</td>
<td style="text-align: center;">Binary</td>
<td style="text-align: center;">Adequate provider data or not</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Momedu</td>
<td style="text-align: center;">Factor</td>
<td style="text-align: center;">Education level of mother (&lt;12 years, high school, some college and college)</td>
</tr>
<tr class="even">
<td style="text-align: center;">Region</td>
<td style="text-align: center;">Factor</td>
<td style="text-align: center;">Census Region ( Northeast, Midwest, South and West)</td>
</tr>
</tbody>
</table>

**Exploratory Data Analysis**

Explanatory data analysis (EDA) was first performed to analyze the data
set to summarize the main characteristics. The overall vaccination rates
in this dataset of 32.94%, and since all the variables in this dataset
are categorical, tables are used for the conditional probabilities of
factor variables to see how the probability of vaccinated changes for
different levels of factor variables, which in other words are the
probabilities for vaccinated given each level of factor variables. Take
family size for example (shown in Table 2), the vaccination rate
decreases with the increase of family size. Or, a chi-squared test could
be performed to test the independence between vaccinated and each other
factor variable. The results from chi-squared tests which evaluate the
independence of each factor variable with the response variable, and
there might be differences between levels in demographic variables and
family-related variables regarding the vaccination rate. The
relationship between state is unclear just by a chi-square test, it
could be further determined in the model assessment. From the
vaccination rate alone, Kansas, Mississippi, and Wyoming are of the
lowest coverage rates, while Rhode Island, North Dakota and District of
Columbia are the highest.

*Table 2. Conditional Probability of Vaccinated in Different Family
Size*

<table>
<thead>
<tr class="header">
<th style="text-align: center;">（Vaccinated）</th>
<th style="text-align: center;">2</th>
<th style="text-align: center;">3</th>
<th style="text-align: center;">4</th>
<th style="text-align: center;">5</th>
<th style="text-align: center;">6</th>
<th style="text-align: center;">7</th>
<th style="text-align: center;">8+</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">No</td>
<td style="text-align: center;">0.67</td>
<td style="text-align: center;">0.66</td>
<td style="text-align: center;">0.66</td>
<td style="text-align: center;">0.68</td>
<td style="text-align: center;">0.70</td>
<td style="text-align: center;">0.72</td>
<td style="text-align: center;">0.72</td>
</tr>
<tr class="even">
<td style="text-align: center;">Yes</td>
<td style="text-align: center;">0.33</td>
<td style="text-align: center;">0.34</td>
<td style="text-align: center;">0.34</td>
<td style="text-align: center;">0.32</td>
<td style="text-align: center;">0.30</td>
<td style="text-align: center;">0.28</td>
<td style="text-align: center;">0.28</td>
</tr>
</tbody>
</table>

<img src="/assets/img/final-project_files/figure-markdown_strict/unnamed-chunk-1-1.png" >
In terms of interaction, interesting interactions include provider with
other family-related variables regarding vaccination rates, and region
with some family-related variables in terms of vaccination rates.
Figure. 2 shows the vaccination count in different children number\*
provider data level, which suggests that families have 2 or 3 children
with adequate provider data are most likely to get children vaccinated.

Figure. 3 shows the vaccination count in different income \* region
level, and south families with the highest income have the highest
vaccinated counts. These interactions could be further investigated by
either interaction terms or a potential hierarchical model.

<img src="/assets/img/final-project_files/figure-markdown_strict/unnamed-chunk-2-1.png" >
**Model and Results**

Vaccinated was treated as the response variable and the others were
treated as potential explanatory variables. Since Vaccinated is a binary
variable, so a logistic regression model with multiple predictors is
used here.
<img src="/assets/img/final-project_files/figure-markdown_strict/equation.png" >
This final model was refined from the model generalized from EDA
analysis. Originally, there were nine possible variables from the EDA
model. The data is randomly selected in an 8:2 ratio to training and
test group. A stepwise BIC selection is used to finalize model, the full
model includes all 9 variables and all possible interactions and null
model only includes provider, which is of high importance according to
EDA. BIC is used here to avoid possible overfitting by adding a larger
penalty term for the number of parameters in the model compared to AIC. After
this stepwise selection, only provider, momedu, age, sex, race, and
interaction between age and sex were kept in the final model.

To further test the final model from EDA, an F-test between a full model
with all the variables after EDA and the selected model was performed to
see if all the dropped variables were truly non-significant. Similarly,
a model with all the variables and all the interactions terms were
compared with the selected model. The F-test returns a high p-value
which confirmed our final model.

From the EDA, the vaccination rates in different provider level and
state level show different trends regarding other predictors, so a
multi-level model by provider and region is also evaluated. Region is
used instead of state, firstly because region can cover the most
characteristics from state but with fewer categories, and R can handle
at most 50 levels in multi-level. The final multi-level model only
includes random slopes of mother’s education by region.

**Model Assessment**

*Figure 4. Binned Residual Plots of Predicted Probabilities*
<img src="/assets/img/final-project_files/figure-markdown_strict/unnamed-chunk-3-1.png" >

Binned residual plots of the multi-level model were performed to assess
the selected model. The residuals were well spread out, and not many
observations outside the SD lines. The trends were different for
different sections of each variable, but not much else to worry about.

**Model Validation**

Another binary classification learning algorithm, Random Forest is used
to comparing with the result from the logistic model. The sensitivity of
a model is defined as the true positive rate (TPR), and specificity is
the true negative rate (TNR). In these models, when set confusion matrix
threshold as the marginal percentage in the data, then the sensitivity,
specificity, and accuracy of training and test are summarized in the
table below. The results from the training and test data are pretty
similar, with accuracies around 0.6, which suggests no overfitting is
observed.The ROC curve is pretty tight to the line with an accuracy of
around 0.6, which suggests a not strongly predictive logistic
regression. The accuracy from the random forest is higher (0.66), but
the sensitivity is very low (&lt;0.1) which suggests random forest does
not accurately predict child who vaccinated.

*Table. 3 Confusion Matrix Summary*

<table>
<thead>
<tr class="header">
<th style="text-align: center;">Model</th>
<th style="text-align: center;">Data</th>
<th style="text-align: center;">Sensitivity</th>
<th style="text-align: center;">Specificity</th>
<th style="text-align: center;">Accuracy</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">Logistic</td>
<td style="text-align: center;">Training</td>
<td style="text-align: center;">0.5701</td>
<td style="text-align: center;">0.5553</td>
<td style="text-align: center;">0.5602</td>
</tr>
<tr class="even">
<td style="text-align: center;">Logistic</td>
<td style="text-align: center;">Test</td>
<td style="text-align: center;">0.4955</td>
<td style="text-align: center;">0.6314</td>
<td style="text-align: center;">0.5850</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Multi-level</td>
<td style="text-align: center;">Training</td>
<td style="text-align: center;">0.5841</td>
<td style="text-align: center;">0.5662</td>
<td style="text-align: center;">0.5721</td>
</tr>
<tr class="even">
<td style="text-align: center;">Multi-level</td>
<td style="text-align: center;">Test</td>
<td style="text-align: center;">0.5052</td>
<td style="text-align: center;">0.6182</td>
<td style="text-align: center;">0.5797</td>
</tr>
<tr class="odd">
<td style="text-align: center;">RandomForest</td>
<td style="text-align: center;">Training</td>
<td style="text-align: center;">0.0834</td>
<td style="text-align: center;">0.9425</td>
<td style="text-align: center;">0.6588</td>
</tr>
<tr class="even">
<td style="text-align: center;">RandomForest</td>
<td style="text-align: center;">Test</td>
<td style="text-align: center;">0.0826</td>
<td style="text-align: center;">0.9457</td>
<td style="text-align: center;">0.6642</td>
</tr>
</tbody>
</table>

**Model Interpretations**

Intuitively, we have an overall “average” regression line for all
vaccination rates across all families. This general estimated line
suggests that for a Hispanic 13 years old male child, with adequate
provider data, and mother’s education level is high school, if the child
does not have adequate provider data, then the vaccination probability
will decrease by 30%, and each year increase results in a 6.69%
increase. Female has a 54% lower probability of getting vaccinated, and
Black children have the highest vaccination rates.

From the final model, the unexplained within-region variation was
attributed to only random slope by mom’s education. Table.2 summarizes
the random effects in different regions. In the northeast region, when
the mother’s education is in college, the children have the highest
vaccination rate.

*Table. 4 Random Effects of Different Regions*

<table>
<thead>
<tr class="header">
<th style="text-align: center;">Region</th>
<th style="text-align: center;">High school</th>
<th style="text-align: center;">Some college</th>
<th style="text-align: center;">College</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">NORTHEAST</td>
<td style="text-align: center;">0.1581</td>
<td style="text-align: center;">0.1587</td>
<td style="text-align: center;">0.1405</td>
</tr>
<tr class="even">
<td style="text-align: center;">MIDWEST</td>
<td style="text-align: center;">-0.0042</td>
<td style="text-align: center;">-0.0360</td>
<td style="text-align: center;">-0.0133</td>
</tr>
<tr class="odd">
<td style="text-align: center;">SOUTH</td>
<td style="text-align: center;">-0.0598</td>
<td style="text-align: center;">0.0302</td>
<td style="text-align: center;">-0.0260</td>
</tr>
<tr class="even">
<td style="text-align: center;">WEST</td>
<td style="text-align: center;">-0.0938</td>
<td style="text-align: center;">-0.1527</td>
<td style="text-align: center;">-0.10010</td>
</tr>
</tbody>
</table>

*Figure 5. Random Effects in Different Regions*
<img src="/assets/img/final-project_files/figure-markdown_strict/unnamed-chunk-4-1.png" >{ width: 200px; }

**Limitations and Conclusions**

The model successfully explains the differences in the vaccination
coverage rates in different families, but the accuracy of the models are
not perfect. Even though the project is more focused on inference, there
are some possible solutions to improve accuracy. Firstly, the vaccines
covered in this survey are only 4, and there are in total of 12 vaccines
required by CDC. If a more complete vaccination survey could be
performed, a more accurate analysis could be generated. Also, the
multi-level logistics model is grouping by region instead of state, even
though region is important in explaining the different vaccination
rates, state should be a better predictor. The performance of the
logistics model could be better if a reasonable re-grouping of the 50
states is used.

The multi-level model suggests that the vaccination rates are different
in regions by mother’s education, even while controlling for other
predictors and random effects. State-wise conclusion is that Rhode
Island has the highest vaccination rate, Mississippi has the lowest
vaccination rate; considering region, the northeast region has the
highest vaccination rates while the west is the lowest. This is helpful
to explain why the measles outbreak started in California. To increase
the vaccination coverage rates across the country, the less-educated
parents need to be convinced to vaccinate their children.
