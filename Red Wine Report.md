<div align='center'>

|Course|:|SENG 207 - Programming for Engineers|
|----|----|---|
|Name|:|Edem Ablorde|
|Index Number|:|11039190|
|Class|:|MTEN|
</div>

<h2 align='center'>COURSE PROJECT REPORT</h2>
<h3 align='center'><u>RED WINE</u></h3>
<h5><u>INTRODUCTION</u></h5>
For this project, a modified red_wine dataset was provided. This dataset which consisted of 1599 entries on various defining features of red wine which included physical and chemical attributes such as:

1. fixed acidity
2. volatile acidity
3. citric acid
4. residual sugar
5. chlorides
6. free sulfur dioxide
7. total sulfur dioxide
8. density
9. pH
10. sulphates
11. alcohol
12. quality
    
The above features/variables of red_wine had numerical data pertaining to each which correlated with another faeture of wine and how they possibly influenced the quality of wine. 

----------------------------

<h5>DATA OVERVIEW AND ANALYSIS</h5>

The **_.head(10)_** method was used to preview the first 10 rows of the dataset and likewise, **_.tail(20)_** was used to preview the final 20 rows. It was observed that some columns had missing values which was further expolred using **_.info()** method

```python
dataset.tail(20)
dataset.head(10)
dataset.info()

```

Upon using the **_.info()_** method to obtain an overwiew of the data provided, it was observed that some columns had missing values. This was further investigated using the **_.isna().any()_** method. It was observed that _'fixed acidity', 'chlorides', 'free sulfur dioxide', 'density' and 'quality'_ had missing values. 

- As a fix, the missing values were replaced with their respective mean values obtained from arithmetic operations.
  
```python
    mean_fixed_acidity = dataset['fixed acidity'].mean()
    mean_volatile_acidity = dataset['volatile acidity'].mean()
    mean_chlorides = dataset['chlorides'].mean()
    mean_free_sulfur_dioxide = dataset['free sulfur dioxide'].mean()
    mean_density = dataset['density'].mean()
    mean_quality = dataset['quality'].mean()
```
<h6>Rounding off all obtained values to match respective data in the dataset</h6>

```python
    mean_fixed_acidity = mean_fixed_acidity.round(2)
    mean_volatile_acidity = mean_volatile_acidity.round(2)    
    mean_chlorides = mean_chlorides.round(3)
    mean_free_sulfur_dioxide = mean_free_sulfur_dioxide.round(1)
    mean_density = mean_density.round(4)
    mean_quality = mean_quality.round(1)
 ```
 <h6>And finally, replacing all null values</h6>

```python
    dataset['fixed acidity'] = dataset['fixed acidity'].filln(mean_fixed_acidity)
    dataset['volatile acidity'] = dataset['volatile acidity'].fillna(mean_volatile_acidity)
    dataset['chlorides'] = dataset['chlorides'].fillna(mean_chlorides)
    dataset['free sulfur dioxide'] = dataset['free sulfur dioxide'].fillna(mean_free_sulfur_dioxide)
    dataset['density'] = dataset['density'].fillna(mean_density)
    dataset['quality'] = dataset['quality'].fillna(mean_quality)

```


- Descriptive data was generated using the **_.describe()_** method, providing a summary of tendencies and distribution. This included 
  
  1. count
  2. mean
  3. standard deviation
  4. minimum values
  5. lower, half and upper quartile values
  6. maximum values

----------------------------

<h5>PLOTS AND DATA VISUALIZATIONS</h5>
Multiple graphs were plotted in order to help visualize the data graphically and make easier to read and deduce.

--------
<h6>NUMERICAL DATA SERIES HISTOGRAM </h6>

![histogram plot 1](/dataCol%20histogram%20graph.png)

The following may be deduced from the various subplots shown above;
1. **Fixed Acidity:**
    With respect to the dataset, the fixed acidity ranges from 4.5 to 16; with **4.6** being low fixed acid content and **15.9**, of high acidity level for red wine. The most recorded being **7.2**.

2. **Volatile Acidity:**
    With respect to the dataset, volatile acidity ranges from 0.1 to 1.6; with **0.12** being lowest volatile acid content and **1.6**, of high acid volatility for red wine. The most recorded value for volatile acidity being **0.6**.
    
3. **Citric Acid:**
    With respect to the dataset, citric acid level ranges from 0 to 1.0; with *0* being lowest citric acid content and *1*, of high acid content for red wine. The most recorded value, *0.2*.

4. **Residual Sugar:**
    With respect to the dataset, residual suagr levels ranges from 0.5 to 16.0; with *0.9* being lowest and *15.6*, being the highest recorded for red wine. The mode *= 2.0**.

5. **Chlorides:**
    Chloride levels range from 0 to 1.0; with a low recording of *0.012* and high record of *0.611* for red wine. The most recorded value, *0.2*.

6. **pH:**
    pH levels range from 2.5 to 4.5; with a low recordin of *2.74* and high record of *4.01* for red wine. The mode, *0.6*.
    
7. **Density:**
    Dnsity range from 0.9 to 1.0; with a low recording of *0.9* and high record of *1.0* for red wine. The mode, *0.99*.

8. **free sulfur dioxide:**
    free dulfur dioxide levels range from 1.0 to 72.0; with a low recording of *1* and high record of *72* for red wine. The mode, *28.0*.

9. **total sulfur dioxide:**
    total sulfur dioxide levels range from 0 to 289.0; with a low recordin of *6.0* and high record of *289.0* for red wine. The mode, *3.3*.

10. **Alcohol:**
    min alcohol level, *8.40*, max alcohol level, *14.90*. mode *= 9.50*

11. **QUality:**
    Quality, which may be the target variable, has its value to be *3.00* and its highest *8.00*. The higher value represents good/high grade red wine wine and vice versa. For this dataset, most recorded wine have quality of *5.0*.

 -------
 <h6>STATISTICAL DATA PLOT</h6>

These graphs describe the behaviour of the tendencies of different variables. 

![statistical data plot](/output.describe.plot.png)

1. **count:** the count value remains the same for all variables at *1599*
2. **mean:** the highest  recorded mean value is for that of total sulfur dioxide
3. **std:** This indicates standard deviation. The values of the variable *total sulfur dioxide* deviate more than the others
4. **min:** Represents the minimum value. *Alcohol* recorded the lowest value.
5. **25%, 50% & 75%:** This represents the lower quartile/25 percentile, median & upper quartile/75 percentile. The highest of all these were recorded by *total sulfur dioxide*
6. **max:** Represents the maximum value. *Total sulfur dioxide recorded the highest data input. 

------------
<h6>ALCOHOL CONTENT DISTRIBUTION HISTOGRAM</h6>


![alcohol content hist](/output.alcohol.content.hist.png)

The above plot represents a graphical representation of the distribution of alcohol content in different recorded red wine ranging from 8.4 to 14.9. Lower values represent less alcohol content and higher values, represent otherwise. With respect to this dataset, most red wine have alcohol content of about 9.5%

-------------
<h6>CORRELATION WITH QUALITY</h6>

![quality corr bar.plot](/output.quality.correlation.bar.png)

This plot provides into the correlation of different variables with quality. Inferring from the graph, the various correlation figures;

  VARIABLE|VALUE
  ------|-----
fixed acidity| 0.17
volatile acidity|-0.4
citric acid|0.22
residual sugar|0.01
chlorides|-0.14
free sulfur dioxide|-0.04
total sulfur dioxide|-0.19
density|-0.18
pH|-0.06
sulphates|0.23
alcohol|0.45
quality|1.0


From the data provided, 

-**Positive correlation:**
    Features such as *Alcohol*, *citric acid* and *sulphates* exhibit a positive correlation with quality. Higher alcohol content and the others mentioned tend to be associated with higher quality wines.

-**Negative correlation:**
    *Volatile acidity*, *density*, *total sulfur dioxide* and *chlorides* show a negative correlation with wine quality. Wines with higher volatile acidity and chloride levels are likely to have lower quality.

-**Weak or No Correlation:**
    Features like 'Residual Sugar' and 'free sulfur dioxide'  exhibit weak correlation with wine quality. These attributes may have limited impact on determining wine quality.

---------

<h5>CONCLUSION</h5>
The analysis revealed important insights into the dataset, throwing light on potential relationships between different features and the quality of wines.



