```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns; sns.set()
import bokeh as bk
import datetime

%matplotlib inline
```


```python
df16 = pd.read_csv('/Users/chiaravercellone/Desktop/CODE/w16.csv')
```


```python
df16.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CAND_ID</th>
      <th>CAND_SURNAME</th>
      <th>CAND_NAME</th>
      <th>CAND_ICI</th>
      <th>PTY_CD</th>
      <th>CAND_PTY_AFFILIATION</th>
      <th>TTL_RECEIPTS</th>
      <th>TRANS_FROM_AUTH</th>
      <th>TTL_DISB</th>
      <th>TRANS_TO_AUTH</th>
      <th>...</th>
      <th>PRIM_ELECTION</th>
      <th>RUN_ELECTION</th>
      <th>GEN_ELECTION</th>
      <th>GEN_ELECTION_PRECENT</th>
      <th>OTHER_POL_CMTE_CONTRIB</th>
      <th>POL_PTY_CONTRIB</th>
      <th>CVG_END_DT</th>
      <th>INDIV_REFUNDS</th>
      <th>CMTE_REFUNDS</th>
      <th>Unnamed: 31</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>H6AK00045</td>
      <td>YOUNG</td>
      <td>DONALD E</td>
      <td>I</td>
      <td>2</td>
      <td>REP</td>
      <td>1103561.86</td>
      <td>0.0</td>
      <td>1322055.12</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>459603.99</td>
      <td>0</td>
      <td>12/31/16</td>
      <td>2250</td>
      <td>3000.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>H6AK00235</td>
      <td>LINDBECK</td>
      <td>STEVE</td>
      <td>NaN</td>
      <td>1</td>
      <td>DEM</td>
      <td>1102309.77</td>
      <td>0.0</td>
      <td>1098098.09</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>67074.61</td>
      <td>5000</td>
      <td>12/31/16</td>
      <td>884.01</td>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>H4AL01123</td>
      <td>BYRNE</td>
      <td>BRADLEY ROBERTS</td>
      <td>I</td>
      <td>2</td>
      <td>REP</td>
      <td>1367469.77</td>
      <td>33152.0</td>
      <td>1172750.28</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>843200.00</td>
      <td>0</td>
      <td>12/31/16</td>
      <td>1100</td>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>H6AL01060</td>
      <td>YOUNG JR</td>
      <td>LARRY DEAN</td>
      <td>C</td>
      <td>2</td>
      <td>REP</td>
      <td>178766.88</td>
      <td>0.0</td>
      <td>178474.16</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>4/14/16</td>
      <td>0</td>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>H6AL02167</td>
      <td>MATHIS</td>
      <td>NATHAN</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>36844</td>
      <td>0.0</td>
      <td>36844.00</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>11/16/16</td>
      <td>0</td>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>H0AL02087</td>
      <td>ROBY</td>
      <td>MARTHA</td>
      <td>I</td>
      <td>2</td>
      <td>REP</td>
      <td>1404260.12</td>
      <td>0.0</td>
      <td>1850535.64</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>828775.00</td>
      <td>0</td>
      <td>12/31/16</td>
      <td>17550</td>
      <td>4283.03</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>H6AL02142</td>
      <td>GERRITSON</td>
      <td>REBECCA (BECKY)</td>
      <td>C</td>
      <td>2</td>
      <td>REP</td>
      <td>206908.19</td>
      <td>0.0</td>
      <td>206908.19</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11500.00</td>
      <td>0</td>
      <td>9/30/16</td>
      <td>1845</td>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>H6AL02159</td>
      <td>ROGERS</td>
      <td>ROBERT L</td>
      <td>C</td>
      <td>2</td>
      <td>REP</td>
      <td>25382</td>
      <td>0.0</td>
      <td>32492.00</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>4/15/16</td>
      <td>0</td>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>H4AL03061</td>
      <td>SMITH</td>
      <td>JESSE TREMAIN</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>9810</td>
      <td>0.0</td>
      <td>7348.00</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>12/31/16</td>
      <td>0</td>
      <td>0.00</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>H2AL03032</td>
      <td>ROGERS</td>
      <td>MICHAEL DENNIS</td>
      <td>I</td>
      <td>2</td>
      <td>REP</td>
      <td>1139022.37</td>
      <td>0.0</td>
      <td>1071289.42</td>
      <td>167500.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>660800.00</td>
      <td>14850</td>
      <td>12/31/16</td>
      <td>1000</td>
      <td>200.00</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 32 columns</p>
</div>




```python
df16.shape
```




    (1898, 32)




```python
df16.dtypes
```




    CAND_ID                    object
    CAND_SURNAME               object
    CAND_NAME                  object
    CAND_ICI                   object
    PTY_CD                     object
    CAND_PTY_AFFILIATION       object
    TTL_RECEIPTS               object
    TRANS_FROM_AUTH           float64
    TTL_DISB                  float64
    TRANS_TO_AUTH             float64
    COH_BOP                   float64
    COH_COP                   float64
    CAND_CONTRIB              float64
    CAND_LOANS                float64
    OTHER_LOANS               float64
    CAND_LOAN_REPAY           float64
    OTHER_LOAN_REPAY          float64
    DEBTS_OWED_BY             float64
    TTL_INDIV_CONTRIB          object
    CAND_OFFICE_ST             object
    CAND_OFFICE_DISTRICT       object
    SPEC_ELECTION             float64
    PRIM_ELECTION             float64
    RUN_ELECTION              float64
    GEN_ELECTION              float64
    GEN_ELECTION_PRECENT      float64
    OTHER_POL_CMTE_CONTRIB    float64
    POL_PTY_CONTRIB            object
    CVG_END_DT                 object
    INDIV_REFUNDS              object
    CMTE_REFUNDS              float64
    Unnamed: 31               float64
    dtype: object




```python
df18 = pd.read_csv('/Users/chiaravercellone/Desktop/CODE/w18.csv')
```


```python
df18.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CAND_ID</th>
      <th>CAND_SURNAME</th>
      <th>CAND_NAME</th>
      <th>CAND_ICI</th>
      <th>PTY_CD</th>
      <th>CAND_PTY_AFFILIATION</th>
      <th>TTL_RECEIPTS</th>
      <th>TRANS_FROM_AUTH</th>
      <th>TTL_DISB</th>
      <th>TRANS_TO_AUTH</th>
      <th>...</th>
      <th>PRIM_ELECTION</th>
      <th>RUN_ELECTION</th>
      <th>GEN_ELECTION</th>
      <th>GEN_ELECTION_PRECENT</th>
      <th>OTHER_POL_CMTE_CONTRIB</th>
      <th>POL_PTY_CONTRIB</th>
      <th>CVG_END_DT</th>
      <th>INDIV_REFUNDS</th>
      <th>CMTE_REFUNDS</th>
      <th>Unnamed: 31</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>H8AK00132</td>
      <td>SHEIN</td>
      <td>DIMITRI</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>209916.04</td>
      <td>0.00</td>
      <td>209574.16</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>0</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>H6AK00045</td>
      <td>YOUNG</td>
      <td>DONALD E</td>
      <td>I</td>
      <td>2</td>
      <td>REP</td>
      <td>1234680.31</td>
      <td>0.00</td>
      <td>1387687.05</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>559861.90</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>2700</td>
      <td>500.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>H8AK01031</td>
      <td>NELSON</td>
      <td>THOMAS JOHN</td>
      <td>C</td>
      <td>2</td>
      <td>REP</td>
      <td>9288.48</td>
      <td>0.00</td>
      <td>8821.97</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>600</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>H8AK00140</td>
      <td>GALVIN</td>
      <td>ALYSE</td>
      <td>C</td>
      <td>3</td>
      <td>IND</td>
      <td>1949643.68</td>
      <td>154.70</td>
      <td>1943398.59</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>114833.97</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>8166.36</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>H8AL01066</td>
      <td>KENNEDY</td>
      <td>ROBERT JR.</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>166845.21</td>
      <td>0.00</td>
      <td>166845.21</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7750.00</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>0</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>H8AL01082</td>
      <td>MCCONNELL</td>
      <td>LIZZETTA HILL</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>5127</td>
      <td>0.00</td>
      <td>6021.00</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>6/30/18</td>
      <td>0</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>H4AL01123</td>
      <td>BYRNE</td>
      <td>BRADLEY ROBERTS</td>
      <td>I</td>
      <td>2</td>
      <td>REP</td>
      <td>1463187.12</td>
      <td>63923.25</td>
      <td>834780.43</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1054650.00</td>
      <td>663.98</td>
      <td>12/31/18</td>
      <td>3050</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>H8AL02163</td>
      <td>WILLIAMS</td>
      <td>AUDRI SCOTT 1955</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>35365.02</td>
      <td>0.00</td>
      <td>35210.22</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>6/30/18</td>
      <td>0</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>H8AL02197</td>
      <td>ISNER</td>
      <td>TABITHA KAY</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>524941.35</td>
      <td>0.00</td>
      <td>524941.35</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8605.00</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>4796.05</td>
      <td>1000.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>H0AL02087</td>
      <td>ROBY</td>
      <td>MARTHA</td>
      <td>I</td>
      <td>2</td>
      <td>REP</td>
      <td>2573681.12</td>
      <td>85734.19</td>
      <td>2277448.83</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1672691.24</td>
      <td>7000</td>
      <td>12/31/18</td>
      <td>6674</td>
      <td>2000.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 32 columns</p>
</div>




```python
df18.shape
```




    (2679, 32)




```python
df18.dtypes
```




    CAND_ID                    object
    CAND_SURNAME               object
    CAND_NAME                  object
    CAND_ICI                   object
    PTY_CD                     object
    CAND_PTY_AFFILIATION       object
    TTL_RECEIPTS               object
    TRANS_FROM_AUTH           float64
    TTL_DISB                  float64
    TRANS_TO_AUTH             float64
    COH_BOP                   float64
    COH_COP                   float64
    CAND_CONTRIB              float64
    CAND_LOANS                float64
    OTHER_LOANS               float64
    CAND_LOAN_REPAY           float64
    OTHER_LOAN_REPAY          float64
    DEBTS_OWED_BY             float64
    TTL_INDIV_CONTRIB          object
    CAND_OFFICE_ST             object
    CAND_OFFICE_DISTRICT       object
    SPEC_ELECTION             float64
    PRIM_ELECTION             float64
    RUN_ELECTION              float64
    GEN_ELECTION              float64
    GEN_ELECTION_PRECENT      float64
    OTHER_POL_CMTE_CONTRIB    float64
    POL_PTY_CONTRIB            object
    CVG_END_DT                 object
    INDIV_REFUNDS              object
    CMTE_REFUNDS              float64
    Unnamed: 31               float64
    dtype: object




```python
frames = [df18, df16]
```


```python
result = pd.concat(frames, sort=False)
```


```python
result.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CAND_ID</th>
      <th>CAND_SURNAME</th>
      <th>CAND_NAME</th>
      <th>CAND_ICI</th>
      <th>PTY_CD</th>
      <th>CAND_PTY_AFFILIATION</th>
      <th>TTL_RECEIPTS</th>
      <th>TRANS_FROM_AUTH</th>
      <th>TTL_DISB</th>
      <th>TRANS_TO_AUTH</th>
      <th>...</th>
      <th>PRIM_ELECTION</th>
      <th>RUN_ELECTION</th>
      <th>GEN_ELECTION</th>
      <th>GEN_ELECTION_PRECENT</th>
      <th>OTHER_POL_CMTE_CONTRIB</th>
      <th>POL_PTY_CONTRIB</th>
      <th>CVG_END_DT</th>
      <th>INDIV_REFUNDS</th>
      <th>CMTE_REFUNDS</th>
      <th>Unnamed: 31</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>H8AK00132</td>
      <td>SHEIN</td>
      <td>DIMITRI</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>209916.04</td>
      <td>0.0</td>
      <td>209574.16</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>0</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>H6AK00045</td>
      <td>YOUNG</td>
      <td>DONALD E</td>
      <td>I</td>
      <td>2</td>
      <td>REP</td>
      <td>1234680.31</td>
      <td>0.0</td>
      <td>1387687.05</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>559861.90</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>2700</td>
      <td>500.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>H8AK01031</td>
      <td>NELSON</td>
      <td>THOMAS JOHN</td>
      <td>C</td>
      <td>2</td>
      <td>REP</td>
      <td>9288.48</td>
      <td>0.0</td>
      <td>8821.97</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>600</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>H8AK00140</td>
      <td>GALVIN</td>
      <td>ALYSE</td>
      <td>C</td>
      <td>3</td>
      <td>IND</td>
      <td>1949643.68</td>
      <td>154.7</td>
      <td>1943398.59</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>114833.97</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>8166.36</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>H8AL01066</td>
      <td>KENNEDY</td>
      <td>ROBERT JR.</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>166845.21</td>
      <td>0.0</td>
      <td>166845.21</td>
      <td>0.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7750.00</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>0</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 32 columns</p>
</div>




```python
result.shape
```




    (4577, 32)




```python
result.dtypes
```




    CAND_ID                    object
    CAND_SURNAME               object
    CAND_NAME                  object
    CAND_ICI                   object
    PTY_CD                     object
    CAND_PTY_AFFILIATION       object
    TTL_RECEIPTS               object
    TRANS_FROM_AUTH           float64
    TTL_DISB                  float64
    TRANS_TO_AUTH             float64
    COH_BOP                   float64
    COH_COP                   float64
    CAND_CONTRIB              float64
    CAND_LOANS                float64
    OTHER_LOANS               float64
    CAND_LOAN_REPAY           float64
    OTHER_LOAN_REPAY          float64
    DEBTS_OWED_BY             float64
    TTL_INDIV_CONTRIB          object
    CAND_OFFICE_ST             object
    CAND_OFFICE_DISTRICT       object
    SPEC_ELECTION             float64
    PRIM_ELECTION             float64
    RUN_ELECTION              float64
    GEN_ELECTION              float64
    GEN_ELECTION_PRECENT      float64
    OTHER_POL_CMTE_CONTRIB    float64
    POL_PTY_CONTRIB            object
    CVG_END_DT                 object
    INDIV_REFUNDS              object
    CMTE_REFUNDS              float64
    Unnamed: 31               float64
    dtype: object




```python
result.describe(include='all')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CAND_ID</th>
      <th>CAND_SURNAME</th>
      <th>CAND_NAME</th>
      <th>CAND_ICI</th>
      <th>PTY_CD</th>
      <th>CAND_PTY_AFFILIATION</th>
      <th>TTL_RECEIPTS</th>
      <th>TRANS_FROM_AUTH</th>
      <th>TTL_DISB</th>
      <th>TRANS_TO_AUTH</th>
      <th>...</th>
      <th>PRIM_ELECTION</th>
      <th>RUN_ELECTION</th>
      <th>GEN_ELECTION</th>
      <th>GEN_ELECTION_PRECENT</th>
      <th>OTHER_POL_CMTE_CONTRIB</th>
      <th>POL_PTY_CONTRIB</th>
      <th>CVG_END_DT</th>
      <th>INDIV_REFUNDS</th>
      <th>CMTE_REFUNDS</th>
      <th>Unnamed: 31</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>4577</td>
      <td>4577</td>
      <td>4577</td>
      <td>4509</td>
      <td>4577</td>
      <td>4575</td>
      <td>4577</td>
      <td>4.577000e+03</td>
      <td>4.577000e+03</td>
      <td>4.577000e+03</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.000000</td>
      <td>4.570000e+03</td>
      <td>4577</td>
      <td>4577</td>
      <td>4577</td>
      <td>4.574000e+03</td>
      <td>7.000000</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>3903</td>
      <td>2856</td>
      <td>2823</td>
      <td>9</td>
      <td>8</td>
      <td>37</td>
      <td>4249</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>516</td>
      <td>479</td>
      <td>1656</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>top</th>
      <td>H8CA05035</td>
      <td>SMITH</td>
      <td>JOHN</td>
      <td>C</td>
      <td>1</td>
      <td>DEM</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>12/31/18</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>2</td>
      <td>32</td>
      <td>46</td>
      <td>2249</td>
      <td>2107</td>
      <td>2107</td>
      <td>233</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3550</td>
      <td>1583</td>
      <td>2258</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.234605e+05</td>
      <td>1.354678e+06</td>
      <td>9.511723e+03</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3833.333333</td>
      <td>2.119938e+05</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.768984e+03</td>
      <td>775.000000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.159226e+06</td>
      <td>1.128696e+07</td>
      <td>1.007939e+05</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6639.528096</td>
      <td>4.671020e+05</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.616696e+04</td>
      <td>2050.457266</td>
    </tr>
    <tr>
      <th>min</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000e+00</td>
      <td>-1.268564e+04</td>
      <td>0.000000e+00</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.000000e+00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-2.000000e+03</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000e+00</td>
      <td>1.491951e+04</td>
      <td>0.000000e+00</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.000000e+00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000e+00</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000e+00</td>
      <td>1.197709e+05</td>
      <td>0.000000e+00</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>5.000000e+02</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000e+00</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000e+00</td>
      <td>9.180382e+05</td>
      <td>0.000000e+00</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5750.000000</td>
      <td>1.778801e+05</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000e+00</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.607600e+08</td>
      <td>5.853463e+08</td>
      <td>3.642535e+06</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11500.000000</td>
      <td>4.134430e+06</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.025588e+06</td>
      <td>5425.000000</td>
    </tr>
  </tbody>
</table>
<p>11 rows × 32 columns</p>
</div>




```python
del result['SPEC_ELECTION']
del result['PRIM_ELECTION']
del result['RUN_ELECTION']
del result['GEN_ELECTION']
del result['GEN_ELECTION_PRECENT']
```


```python
result.shape
```




    (4577, 27)




```python
pd.to_datetime(result['CVG_END_DT'])
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/dateutil/parser/_parser.py in parse(self, timestr, default, ignoretz, tzinfos, **kwargs)
        654         try:
    --> 655             ret = self._build_naive(res, default)
        656         except ValueError as e:


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/dateutil/parser/_parser.py in _build_naive(self, res, default)
       1240 
    -> 1241         naive = default.replace(**repl)
       1242 


    ValueError: day is out of range for month

    
    The above exception was the direct cause of the following exception:


    ParserError                               Traceback (most recent call last)

    pandas/_libs/tslib.pyx in pandas._libs.tslib.array_to_datetime()


    pandas/_libs/tslibs/parsing.pyx in pandas._libs.tslibs.parsing.parse_datetime_string()


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/dateutil/parser/_parser.py in parse(timestr, parserinfo, **kwargs)
       1373     else:
    -> 1374         return DEFAULTPARSER.parse(timestr, **kwargs)
       1375 


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/dateutil/parser/_parser.py in parse(self, timestr, default, ignoretz, tzinfos, **kwargs)
        656         except ValueError as e:
    --> 657             six.raise_from(ParserError(e.args[0] + ": %s", timestr), e)
        658 


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/six.py in raise_from(value, from_value)


    ParserError: day is out of range for month: 0

    
    During handling of the above exception, another exception occurred:


    TypeError                                 Traceback (most recent call last)

    pandas/_libs/tslib.pyx in pandas._libs.tslib.array_to_datetime()


    TypeError: invalid string coercion to datetime

    
    During handling of the above exception, another exception occurred:


    ValueError                                Traceback (most recent call last)

    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/dateutil/parser/_parser.py in parse(self, timestr, default, ignoretz, tzinfos, **kwargs)
        654         try:
    --> 655             ret = self._build_naive(res, default)
        656         except ValueError as e:


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/dateutil/parser/_parser.py in _build_naive(self, res, default)
       1240 
    -> 1241         naive = default.replace(**repl)
       1242 


    ValueError: day is out of range for month

    
    The above exception was the direct cause of the following exception:


    ParserError                               Traceback (most recent call last)

    <ipython-input-18-0edb47ed8101> in <module>
    ----> 1 pd.to_datetime(result['CVG_END_DT'])
    

    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/pandas/core/tools/datetimes.py in to_datetime(arg, errors, dayfirst, yearfirst, utc, format, exact, unit, infer_datetime_format, origin, cache)
        722                 result = result.tz_localize(tz)
        723     elif isinstance(arg, ABCSeries):
    --> 724         cache_array = _maybe_cache(arg, format, cache, convert_listlike)
        725         if not cache_array.empty:
        726             result = arg.map(cache_array)


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/pandas/core/tools/datetimes.py in _maybe_cache(arg, format, cache, convert_listlike)
        150         unique_dates = unique(arg)
        151         if len(unique_dates) < len(arg):
    --> 152             cache_dates = convert_listlike(unique_dates, format)
        153             cache_array = Series(cache_dates, index=unique_dates)
        154     return cache_array


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/pandas/core/tools/datetimes.py in _convert_listlike_datetimes(arg, format, name, tz, unit, errors, infer_datetime_format, dayfirst, yearfirst, exact)
        438         assert format is None or infer_datetime_format
        439         utc = tz == "utc"
    --> 440         result, tz_parsed = objects_to_datetime64ns(
        441             arg,
        442             dayfirst=dayfirst,


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/pandas/core/arrays/datetimes.py in objects_to_datetime64ns(data, dayfirst, yearfirst, utc, errors, require_iso8601, allow_object)
       1861             return values.view("i8"), tz_parsed
       1862         except (ValueError, TypeError):
    -> 1863             raise e
       1864 
       1865     if tz_parsed is not None:


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/pandas/core/arrays/datetimes.py in objects_to_datetime64ns(data, dayfirst, yearfirst, utc, errors, require_iso8601, allow_object)
       1846 
       1847     try:
    -> 1848         result, tz_parsed = tslib.array_to_datetime(
       1849             data,
       1850             errors=errors,


    pandas/_libs/tslib.pyx in pandas._libs.tslib.array_to_datetime()


    pandas/_libs/tslib.pyx in pandas._libs.tslib.array_to_datetime()


    pandas/_libs/tslib.pyx in pandas._libs.tslib.array_to_datetime_object()


    pandas/_libs/tslib.pyx in pandas._libs.tslib.array_to_datetime_object()


    pandas/_libs/tslibs/parsing.pyx in pandas._libs.tslibs.parsing.parse_datetime_string()


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/dateutil/parser/_parser.py in parse(timestr, parserinfo, **kwargs)
       1372         return parser(parserinfo).parse(timestr, **kwargs)
       1373     else:
    -> 1374         return DEFAULTPARSER.parse(timestr, **kwargs)
       1375 
       1376 


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/dateutil/parser/_parser.py in parse(self, timestr, default, ignoretz, tzinfos, **kwargs)
        655             ret = self._build_naive(res, default)
        656         except ValueError as e:
    --> 657             six.raise_from(ParserError(e.args[0] + ": %s", timestr), e)
        658 
        659         if not ignoretz:


    ~/.local/share/virtualenvs/chiaravercellone-jRa3eUrx/lib/python3.8/site-packages/six.py in raise_from(value, from_value)


    ParserError: day is out of range for month: 0



```python
resultd.types
