

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```


```python
grad_student_df = pd.read_excel("~/Desktop/Competition Data and Guidelines/1.Graduate Earning.csv", sheet_name = None)
education_exp_df = pd.read_excel("~/Desktop/Competition Data and Guidelines/2.Expenditure on Education.csv", sheet_name = None)
econ_growth_df = pd.read_excel("~/Desktop/Competition Data and Guidelines/3.Economic Growth.csv", sheet_name = None)
enrol_prov_df = pd.read_excel("~/Desktop/Competition Data and Guidelines/4.Enrollment By Prov.csv", sheet_name = None)
enrol_prgm_df = pd.read_excel("~/Desktop/Competition Data and Guidelines/5.Enrollment by Prgm.csv", sheet_name = None)
grads_year_df = pd.read_excel("~/Desktop/Competition Data and Guidelines/6.Grads By Year.csv", sheet_name = None)
tuition_prov_df = pd.read_excel("~/Desktop/Competition Data and Guidelines/7.Tuition By Province and Program.csv", sheet_name = None)
perm_res_df = pd.read_excel("~/Desktop/Competition Data and Guidelines/8.Perm App Res by Country.csv", sheet_name = None)
conv_country_df = pd.read_excel("~/Desktop/Competition Data and Guidelines/9.Conversion by Country.csv", sheet_name = None)

```


```python
grad_student_df.describe()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Graduate Earnings($)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>36.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>52663.888889</td>
    </tr>
    <tr>
      <th>std</th>
      <td>17429.271811</td>
    </tr>
    <tr>
      <th>min</th>
      <td>24000.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>40600.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>50500.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>65250.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>96000.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
grad_student_df.groupby(["LEVEL", "Percentile"]).agg("mean")
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Graduate Earnings($)</th>
    </tr>
    <tr>
      <th>LEVEL</th>
      <th>Percentile</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">Bachelor's</th>
      <th>25th percentile</th>
      <td>35900.000000</td>
    </tr>
    <tr>
      <th>75th percentile</th>
      <td>57533.333333</td>
    </tr>
    <tr>
      <th>Median</th>
      <td>45666.666667</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">College</th>
      <th>25th percentile</th>
      <td>28233.333333</td>
    </tr>
    <tr>
      <th>75th percentile</th>
      <td>46766.666667</td>
    </tr>
    <tr>
      <th>Median</th>
      <td>35933.333333</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">Doctorate</th>
      <th>25th percentile</th>
      <td>49500.000000</td>
    </tr>
    <tr>
      <th>75th percentile</th>
      <td>81833.333333</td>
    </tr>
    <tr>
      <th>Median</th>
      <td>65366.666667</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">Master's</th>
      <th>25th percentile</th>
      <td>47266.666667</td>
    </tr>
    <tr>
      <th>75th percentile</th>
      <td>77300.000000</td>
    </tr>
    <tr>
      <th>Median</th>
      <td>60666.666667</td>
    </tr>
  </tbody>
</table>
</div>




```python
date_sorted = grad_student_df.sort_values("Ref_Date")
date_sorted[date_sorted["LEVEL"] == "Master's"].hist("Graduate Earnings($)")
plt.show()
```


![png](Int%20Students%20Analysis_files/Int%20Students%20Analysis_4_0.png)



```python
college_students = date_sorted[date_sorted["LEVEL"] == "College"]
plt.scatter(college_students["Ref_Date"].tolist(), college_students["Graduate Earnings($)"].tolist())
plt.show()
```


![png](Int%20Students%20Analysis_files/Int%20Students%20Analysis_5_0.png)



```python
master_students = date_sorted[date_sorted["LEVEL"] == "Master's"]
plt.scatter(master_students["Ref_Date"].tolist(), master_students["Graduate Earnings($)"].tolist())
plt.show()
```


![png](Int%20Students%20Analysis_files/Int%20Students%20Analysis_6_0.png)



```python
enrol_prov_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ref_Date</th>
      <th>Geo</th>
      <th>Level</th>
      <th>Registration status</th>
      <th>Gender</th>
      <th>Student Type</th>
      <th>Num of Students</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>Canadian students</td>
      <td>5151</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>International students</td>
      <td>765</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>Canadian students</td>
      <td>8091</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>International students</td>
      <td>462</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Full-time student</td>
      <td>Sex unknown</td>
      <td>Canadian students</td>
      <td>6</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Full-time student</td>
      <td>Sex unknown</td>
      <td>International students</td>
      <td>6</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>Canadian students</td>
      <td>1419</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>International students</td>
      <td>60</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>Canadian students</td>
      <td>2316</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>International students</td>
      <td>45</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Part-time student</td>
      <td>Sex unknown</td>
      <td>Canadian students</td>
      <td>3</td>
    </tr>
    <tr>
      <th>11</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>University</td>
      <td>Part-time student</td>
      <td>Sex unknown</td>
      <td>International students</td>
      <td>0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>Canadian students</td>
      <td>3654</td>
    </tr>
    <tr>
      <th>13</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>International students</td>
      <td>30</td>
    </tr>
    <tr>
      <th>14</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>Not reported</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>Canadian students</td>
      <td>3516</td>
    </tr>
    <tr>
      <th>16</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>International students</td>
      <td>21</td>
    </tr>
    <tr>
      <th>17</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>Not reported</td>
      <td>0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Sex unknown</td>
      <td>Canadian students</td>
      <td>0</td>
    </tr>
    <tr>
      <th>19</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Sex unknown</td>
      <td>International students</td>
      <td>0</td>
    </tr>
    <tr>
      <th>20</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>Canadian students</td>
      <td>1482</td>
    </tr>
    <tr>
      <th>21</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>International students</td>
      <td>6</td>
    </tr>
    <tr>
      <th>22</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>Not reported</td>
      <td>0</td>
    </tr>
    <tr>
      <th>23</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>Canadian students</td>
      <td>1455</td>
    </tr>
    <tr>
      <th>24</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>International students</td>
      <td>6</td>
    </tr>
    <tr>
      <th>25</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>Not reported</td>
      <td>0</td>
    </tr>
    <tr>
      <th>26</th>
      <td>2010-09-01</td>
      <td>Newfoundland and Labrador</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Sex unknown</td>
      <td>Canadian students</td>
      <td>0</td>
    </tr>
    <tr>
      <th>27</th>
      <td>2010-09-01</td>
      <td>Prince Edward Island</td>
      <td>University</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>Canadian students</td>
      <td>1227</td>
    </tr>
    <tr>
      <th>28</th>
      <td>2010-09-01</td>
      <td>Prince Edward Island</td>
      <td>University</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>International students</td>
      <td>159</td>
    </tr>
    <tr>
      <th>29</th>
      <td>2010-09-01</td>
      <td>Prince Edward Island</td>
      <td>University</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>Canadian students</td>
      <td>2058</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1485</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>International students</td>
      <td>3048</td>
    </tr>
    <tr>
      <th>1486</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>Not reported</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1487</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Sex unknown</td>
      <td>Canadian students</td>
      <td>9</td>
    </tr>
    <tr>
      <th>1488</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Sex unknown</td>
      <td>International students</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1489</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>Canadian students</td>
      <td>19623</td>
    </tr>
    <tr>
      <th>1490</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>International students</td>
      <td>1515</td>
    </tr>
    <tr>
      <th>1491</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>Not reported</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1492</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>Canadian students</td>
      <td>29298</td>
    </tr>
    <tr>
      <th>1493</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>International students</td>
      <td>1278</td>
    </tr>
    <tr>
      <th>1494</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>Not reported</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1495</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Sex unknown</td>
      <td>Canadian students</td>
      <td>75</td>
    </tr>
    <tr>
      <th>1496</th>
      <td>2014-09-01</td>
      <td>British Columbia</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Sex unknown</td>
      <td>International students</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1497</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>Canadian students</td>
      <td>417</td>
    </tr>
    <tr>
      <th>1498</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>International students</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1499</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Males</td>
      <td>Not reported</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1500</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>Canadian students</td>
      <td>900</td>
    </tr>
    <tr>
      <th>1501</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>International students</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1502</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Females</td>
      <td>Not reported</td>
      <td>9</td>
    </tr>
    <tr>
      <th>1503</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Sex unknown</td>
      <td>Canadian students</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1504</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Sex unknown</td>
      <td>International students</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1505</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Full-time student</td>
      <td>Sex unknown</td>
      <td>Not reported</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1506</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>Canadian students</td>
      <td>915</td>
    </tr>
    <tr>
      <th>1507</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>International students</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1508</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Males</td>
      <td>Not reported</td>
      <td>69</td>
    </tr>
    <tr>
      <th>1509</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>Canadian students</td>
      <td>1443</td>
    </tr>
    <tr>
      <th>1510</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>International students</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1511</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Females</td>
      <td>Not reported</td>
      <td>63</td>
    </tr>
    <tr>
      <th>1512</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Sex unknown</td>
      <td>Canadian students</td>
      <td>117</td>
    </tr>
    <tr>
      <th>1513</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Sex unknown</td>
      <td>International students</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1514</th>
      <td>2014-09-01</td>
      <td>Territories</td>
      <td>College</td>
      <td>Part-time student</td>
      <td>Sex unknown</td>
      <td>Not reported</td>
      <td>45</td>
    </tr>
  </tbody>
</table>
<p>1515 rows × 7 columns</p>
</div>




```python
provincial_stats = enrol_prov_df.groupby(["Geo","Gender"]).agg({"Num of Students":"sum"})
```


```python
tuition_program_df = enrol_prov_df.merge(tuition_prov_df, how = 'inner', left_on= ["Ref_Date","Geo"], right_on=["Ref_Date","GEO"]).drop_duplicates(subset = ["Program of Study","Gender","GEO"])
```


```python
tuition_grouped = tuition_program_df.groupby(["Program of Study","Geo"]).agg({"Tuition":"mean"})
```


```python
plotted = tuition_grouped.groupby("Geo").agg({"Tuition":"mean"}).sort_values("Tuition").reset_index()

plt.figure(figsize = (22,5))
plt.scatter(plotted["Geo"].tolist(), plotted["Tuition"].tolist(), c = 'teal')
plt.title("avg tuition by province")
plt.xlabel("province")
plt.ylabel("avg tuition")
plt.show()
```


![png](Int%20Students%20Analysis_files/Int%20Students%20Analysis_11_0.png)



```python
from IPython.display import Image
from IPython.core.display import HTML 
Image(url= "http://www.dofactory.com/Images/sql-joins.png")
```




<img src="http://www.dofactory.com/Images/sql-joins.png"/>


