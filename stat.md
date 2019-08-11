## 4. Quantitative research (STATA)

### Do real GDP per capita, and CO2 emissions from manufacturing industries and construction predict energy consumption per capita?

#### **Data sources** 

The data from the World Bank’s World Development Index 2013 was utilized for this cross-sectional analysis. This study examines the relationship between impact of GDP on Energy consumption on a subset of 153 out of 231 cities and countries from seven regions. Cases with missing data are omitted in regression analysis, therefore, 78 regions and countries are excluded.  It is noted that aggregated data and countries with no data available are omitted from the total 264 observations in the dataset. Nauru and Kosovo are the two countries without available data.

#### **Result**

![STATA_scatter_power_gdp_pc](F:/Wai/kristykawai.github.io/assets/STATA_scatter_power_gdp_pc.png)

![STATA_regress](F:/Wai/kristykawai.github.io/assets/STATA_regress.png)

#### **STATA script**

```
use "./World development index\All_countries_WDIS_2013.dta", clear
drop if region=="Aggregates"
drop if region==""
g log_EnergyUse=log(eg_use_elec_kh_pc)
g log_RealGDP=log(ny_gdp_pcap_pp_kd)
sum eg_use_elec_kh_pc ny_gdp_pcap_pp_kd, detail
sum log_EnergyUse log_RealGDP en_co2_manf_zs, detail
encode region, g(regionnum) lab(regionlab)
regress log_EnergyUse log_RealGDP 
regress log_EnergyUse log_RealGDP en_co2_manf_zs  
by region, sort : regress log_EnergyUse log_RealGDP en_co2_manf_zs  
ssc install estout, replace
est clear 
eststo: quietly reg log_EnergyUse log_RealGDP
eststo: quietly reg log_EnergyUse log_RealGDP en_co2_manf_zs  
esttab, p scalars(F df_m df_r) r2 ar2
```

_It is a research project (coursework) tutored by Crawford School PhD scholar Chi-hoong Leong in Research Methods for Environmental Management (EMDV8102) in 2017._

## 5. Quantitative research (SPSS)

### Perceived Housing Correlates of Fertility Intention among Hong Kong people aged between 18 and 35

#### **Theoretical Framework**

![SPSS_framework](F:/Wai/kristykawai.github.io/assets/SPSS_framework.png)

#### Methodology

Before data for this report were gathered from January to February 2016, a pilot test
with 20 respondents was conducted in early November 2015. It helped to modify the
questionnaire design and enhance reliability of data retrieved. The questionnaires were
distributed to a total of 225 Hong Kong citizens aged between18 and 35 years old. The
response rate was 80 % (198 questionnaires).

- Sampling Method
  Non-probability sampling, quota sampling was adopted. The ratio of four items were
  controlled according to the official population data including sex, age, employment, and marital status.
- Instrument Designs
  There are two sets of questionnaires, one is for parents (Part A) and one is for nonparents
  (Part B). Part A contains 7 sections with 52 questions and Part B are composed of 50 questions. All questions are written in Traditional Chinese. Translations work for borrowing scales and questions from foreign researches were first completed by a researcher and passed to a group of five researchers for further modifications.

#### Data Processing and Analysis

After screening out suspect questionnaires with straight line answers, 172 questionnaires were counted as valid and used for data analysis. Valid questionnaires were firstly coded by a researcher, then double checked by another research. The data entry process was completed by a third research with SPSS 22.0. All predictors in regression models passed the Collinearity test (Variance inflation factor <10). As there were three outcome variables of fertility intention, separate analysis was employed. There were three sets of regression model completed.

#### **Result**

![SPSS_regress](F:/Wai/kristykawai.github.io/assets/SPSS_regress.jpg)

_It is an honour research project supervised by Dr. Bai Xue at the Hong Kong Polytechnic University in 2015._