```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```


```python
plt.style.use('ggplot')
```

## Import Dataset for buyer


```python
buyer_df = pd.read_csv('/content/sample_data/EB_Purchases_Updated.csv')
buyer_df.drop('Sr No.', axis=1, inplace=True)
buyer_df.head()
```





  <div id="df-1e769f68-ee81-427b-a652-5f42528d4200" class="colab-df-container">
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
      <th>Reference No (URN)</th>
      <th>Journal Date</th>
      <th>Date of Purchase</th>
      <th>Date of Expiry</th>
      <th>Name of the Purchaser</th>
      <th>Prefix</th>
      <th>Bond Number</th>
      <th>Denominations (INR)</th>
      <th>Issue Branch Code</th>
      <th>Issue Teller</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1201900000000000000</td>
      <td>12-Apr-19</td>
      <td>12-Apr-19</td>
      <td>26-Apr-19</td>
      <td>A B C INDIA LIMITED</td>
      <td>TL</td>
      <td>11448</td>
      <td>10,00,000</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1201900000000000000</td>
      <td>12-Apr-19</td>
      <td>12-Apr-19</td>
      <td>26-Apr-19</td>
      <td>A B C INDIA LIMITED</td>
      <td>TL</td>
      <td>11447</td>
      <td>10,00,000</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1201900000000000000</td>
      <td>12-Apr-19</td>
      <td>12-Apr-19</td>
      <td>26-Apr-19</td>
      <td>A B C INDIA LIMITED</td>
      <td>TL</td>
      <td>11441</td>
      <td>10,00,000</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1201900000000000000</td>
      <td>12-Apr-19</td>
      <td>12-Apr-19</td>
      <td>26-Apr-19</td>
      <td>A B C INDIA LIMITED</td>
      <td>OL</td>
      <td>1113</td>
      <td>1,00,000</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1201900000000000000</td>
      <td>12-Apr-19</td>
      <td>12-Apr-19</td>
      <td>26-Apr-19</td>
      <td>A B C INDIA LIMITED</td>
      <td>OL</td>
      <td>1118</td>
      <td>1,00,000</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-1e769f68-ee81-427b-a652-5f42528d4200')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-1e769f68-ee81-427b-a652-5f42528d4200 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-1e769f68-ee81-427b-a652-5f42528d4200');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
buyer_df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 18871 entries, 0 to 18870
    Data columns (total 11 columns):
     #   Column                 Non-Null Count  Dtype 
    ---  ------                 --------------  ----- 
     0   Reference No (URN)     18871 non-null  object
     1   Journal Date           18871 non-null  object
     2   Date of Purchase       18871 non-null  object
     3   Date of Expiry         18871 non-null  object
     4   Name of the Purchaser  18871 non-null  object
     5   Prefix                 18871 non-null  object
     6   Bond Number            18871 non-null  int64 
     7   Denominations (INR)    18871 non-null  object
     8   Issue Branch Code      18871 non-null  int64 
     9   Issue Teller           18871 non-null  int64 
     10  Status                 18871 non-null  object
    dtypes: int64(3), object(8)
    memory usage: 1.6+ MB



```python
buyer_df.describe()
```





  <div id="df-d093b528-b02c-412d-859f-9729944bcf28" class="colab-df-container">
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
      <th>Bond Number</th>
      <th>Issue Branch Code</th>
      <th>Issue Teller</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>18871.000000</td>
      <td>18871.000000</td>
      <td>1.887100e+04</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>12181.003338</td>
      <td>480.065550</td>
      <td>5.895737e+06</td>
    </tr>
    <tr>
      <th>std</th>
      <td>6573.754865</td>
      <td>395.446834</td>
      <td>1.825395e+06</td>
    </tr>
    <tr>
      <th>min</th>
      <td>8.000000</td>
      <td>1.000000</td>
      <td>1.013030e+06</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>8317.500000</td>
      <td>1.000000</td>
      <td>5.054982e+06</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>12350.000000</td>
      <td>509.000000</td>
      <td>6.405134e+06</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>14764.000000</td>
      <td>813.000000</td>
      <td>7.273126e+06</td>
    </tr>
    <tr>
      <th>max</th>
      <td>71548.000000</td>
      <td>1355.000000</td>
      <td>8.492239e+06</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-d093b528-b02c-412d-859f-9729944bcf28')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-d093b528-b02c-412d-859f-9729944bcf28 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-d093b528-b02c-412d-859f-9729944bcf28');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
buyer_df.isna().sum()
```




    Reference No (URN)       0
    Journal Date             0
    Date of Purchase         0
    Date of Expiry           0
    Name of the Purchaser    0
    Prefix                   0
    Bond Number              0
    Denominations (INR)      0
    Issue Branch Code        0
    Issue Teller             0
    Status                   0
    dtype: int64



Observation : No null values


```python
buyer_df.rename(mapper={'Reference No (URN)': 'rfno'}, axis=1, inplace=True)
buyer_df.columns
```




    Index(['rfno', 'Journal Date', 'Date of Purchase', 'Date of Expiry',
           'Name of the Purchaser', 'Prefix', 'Bond Number', 'Denominations (INR)',
           'Issue Branch Code', 'Issue Teller', 'Status'],
          dtype='object')



Convert datatype of Journal Date, Date of Purchase and Date of Expiry to datetime datatype.


```python
obj_col = ['Journal Date', 'Date of Purchase', 'Date of Expiry']
for col in obj_col:
    buyer_df[col] = pd.to_datetime(buyer_df[col], format="%d-%b-%y")

# Check datatype after transformation
for col in obj_col:
    print(buyer_df[col].dtype)
```

    datetime64[ns]
    datetime64[ns]
    datetime64[ns]



```python
# buyer_df.sort_values(by='Date of Purchase', inplace=True)
```

## Extract Year, Month, Day and Quarter from `Date of Purchase`


```python
buyer_df['Year'] = buyer_df['Date of Purchase'].dt.strftime('%Y')
buyer_df['Month'] = buyer_df['Date of Purchase'].dt.strftime('%m')
buyer_df['Day'] = buyer_df['Date of Purchase'].dt.strftime('%d')
buyer_df['Quarter'] = buyer_df['Date of Purchase'].dt.to_period('Q').dt.strftime('%Y-Q%q')
```


```python
buyer_df.head(5).T
```





  <div id="df-4112167c-cacd-440d-947b-35c732c47145" class="colab-df-container">
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>rfno</th>
      <td>1201900000000000000</td>
      <td>1201900000000000000</td>
      <td>1201900000000000000</td>
      <td>1201900000000000000</td>
      <td>1201900000000000000</td>
    </tr>
    <tr>
      <th>Journal Date</th>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-12 00:00:00</td>
    </tr>
    <tr>
      <th>Date of Purchase</th>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-12 00:00:00</td>
    </tr>
    <tr>
      <th>Date of Expiry</th>
      <td>2019-04-26 00:00:00</td>
      <td>2019-04-26 00:00:00</td>
      <td>2019-04-26 00:00:00</td>
      <td>2019-04-26 00:00:00</td>
      <td>2019-04-26 00:00:00</td>
    </tr>
    <tr>
      <th>Name of the Purchaser</th>
      <td>A B C INDIA LIMITED</td>
      <td>A B C INDIA LIMITED</td>
      <td>A B C INDIA LIMITED</td>
      <td>A B C INDIA LIMITED</td>
      <td>A B C INDIA LIMITED</td>
    </tr>
    <tr>
      <th>Prefix</th>
      <td>TL</td>
      <td>TL</td>
      <td>TL</td>
      <td>OL</td>
      <td>OL</td>
    </tr>
    <tr>
      <th>Bond Number</th>
      <td>11448</td>
      <td>11447</td>
      <td>11441</td>
      <td>1113</td>
      <td>1118</td>
    </tr>
    <tr>
      <th>Denominations (INR)</th>
      <td>10,00,000</td>
      <td>10,00,000</td>
      <td>10,00,000</td>
      <td>1,00,000</td>
      <td>1,00,000</td>
    </tr>
    <tr>
      <th>Issue Branch Code</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Issue Teller</th>
      <td>5899230</td>
      <td>5899230</td>
      <td>5899230</td>
      <td>5899230</td>
      <td>5899230</td>
    </tr>
    <tr>
      <th>Status</th>
      <td>Paid</td>
      <td>Paid</td>
      <td>Paid</td>
      <td>Paid</td>
      <td>Paid</td>
    </tr>
    <tr>
      <th>Year</th>
      <td>2019</td>
      <td>2019</td>
      <td>2019</td>
      <td>2019</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>Month</th>
      <td>04</td>
      <td>04</td>
      <td>04</td>
      <td>04</td>
      <td>04</td>
    </tr>
    <tr>
      <th>Day</th>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <th>Quarter</th>
      <td>2019-Q2</td>
      <td>2019-Q2</td>
      <td>2019-Q2</td>
      <td>2019-Q2</td>
      <td>2019-Q2</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-4112167c-cacd-440d-947b-35c732c47145')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-4112167c-cacd-440d-947b-35c732c47145 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-4112167c-cacd-440d-947b-35c732c47145');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>




Convert `Denominations (INR)` to int type


```python
buyer_df['Denominations (INR)'] = buyer_df['Denominations (INR)'].apply(lambda x: x.replace(',', ''))
buyer_df['Denominations (INR)'] = pd.to_numeric(buyer_df['Denominations (INR)'])
buyer_df['Denominations (INR)'] = buyer_df['Denominations (INR)'].divide(10000000)
buyer_df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 18871 entries, 0 to 18870
    Data columns (total 15 columns):
     #   Column                 Non-Null Count  Dtype         
    ---  ------                 --------------  -----         
     0   rfno                   18871 non-null  object        
     1   Journal Date           18871 non-null  datetime64[ns]
     2   Date of Purchase       18871 non-null  datetime64[ns]
     3   Date of Expiry         18871 non-null  datetime64[ns]
     4   Name of the Purchaser  18871 non-null  object        
     5   Prefix                 18871 non-null  object        
     6   Bond Number            18871 non-null  int64         
     7   Denominations (INR)    18871 non-null  float64       
     8   Issue Branch Code      18871 non-null  int64         
     9   Issue Teller           18871 non-null  int64         
     10  Status                 18871 non-null  object        
     11  Year                   18871 non-null  object        
     12  Month                  18871 non-null  object        
     13  Day                    18871 non-null  object        
     14  Quarter                18871 non-null  object        
    dtypes: datetime64[ns](3), float64(1), int64(3), object(8)
    memory usage: 2.2+ MB



```python
buyer_df.describe()
```





  <div id="df-c41456e0-b845-49f9-a2ca-13077c3f2467" class="colab-df-container">
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
      <th>Journal Date</th>
      <th>Date of Purchase</th>
      <th>Date of Expiry</th>
      <th>Bond Number</th>
      <th>Denominations (INR)</th>
      <th>Issue Branch Code</th>
      <th>Issue Teller</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>18871</td>
      <td>18871</td>
      <td>18871</td>
      <td>18871.000000</td>
      <td>18871.000000</td>
      <td>18871.000000</td>
      <td>1.887100e+04</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2022-03-15 00:27:55.714058496</td>
      <td>2022-03-15 00:28:27.763234304</td>
      <td>2022-03-29 00:28:27.763234304</td>
      <td>12181.003338</td>
      <td>0.644137</td>
      <td>480.065550</td>
      <td>5.895737e+06</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-12 00:00:00</td>
      <td>2019-04-26 00:00:00</td>
      <td>8.000000</td>
      <td>0.000100</td>
      <td>1.000000</td>
      <td>1.013030e+06</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2021-04-09 00:00:00</td>
      <td>2021-04-09 00:00:00</td>
      <td>2021-04-23 00:00:00</td>
      <td>8317.500000</td>
      <td>0.100000</td>
      <td>1.000000</td>
      <td>5.054982e+06</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2022-07-06 00:00:00</td>
      <td>2022-07-06 00:00:00</td>
      <td>2022-07-20 00:00:00</td>
      <td>12350.000000</td>
      <td>1.000000</td>
      <td>509.000000</td>
      <td>6.405134e+06</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2023-07-10 00:00:00</td>
      <td>2023-07-10 00:00:00</td>
      <td>2023-07-24 00:00:00</td>
      <td>14764.000000</td>
      <td>1.000000</td>
      <td>813.000000</td>
      <td>7.273126e+06</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2024-01-11 00:00:00</td>
      <td>2024-01-11 00:00:00</td>
      <td>2024-01-25 00:00:00</td>
      <td>71548.000000</td>
      <td>1.000000</td>
      <td>1355.000000</td>
      <td>8.492239e+06</td>
    </tr>
    <tr>
      <th>std</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6573.754865</td>
      <td>0.453895</td>
      <td>395.446834</td>
      <td>1.825395e+06</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-c41456e0-b845-49f9-a2ca-13077c3f2467')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-c41456e0-b845-49f9-a2ca-13077c3f2467 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-c41456e0-b845-49f9-a2ca-13077c3f2467');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
buyer_df.head()
```





  <div id="df-8b0a5260-dc45-4822-9dab-3c620fbc7df9" class="colab-df-container">
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
      <th>rfno</th>
      <th>Journal Date</th>
      <th>Date of Purchase</th>
      <th>Date of Expiry</th>
      <th>Name of the Purchaser</th>
      <th>Prefix</th>
      <th>Bond Number</th>
      <th>Denominations (INR)</th>
      <th>Issue Branch Code</th>
      <th>Issue Teller</th>
      <th>Status</th>
      <th>Year</th>
      <th>Month</th>
      <th>Day</th>
      <th>Quarter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1201900000000000000</td>
      <td>2019-04-12</td>
      <td>2019-04-12</td>
      <td>2019-04-26</td>
      <td>A B C INDIA LIMITED</td>
      <td>TL</td>
      <td>11448</td>
      <td>0.10</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1201900000000000000</td>
      <td>2019-04-12</td>
      <td>2019-04-12</td>
      <td>2019-04-26</td>
      <td>A B C INDIA LIMITED</td>
      <td>TL</td>
      <td>11447</td>
      <td>0.10</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1201900000000000000</td>
      <td>2019-04-12</td>
      <td>2019-04-12</td>
      <td>2019-04-26</td>
      <td>A B C INDIA LIMITED</td>
      <td>TL</td>
      <td>11441</td>
      <td>0.10</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1201900000000000000</td>
      <td>2019-04-12</td>
      <td>2019-04-12</td>
      <td>2019-04-26</td>
      <td>A B C INDIA LIMITED</td>
      <td>OL</td>
      <td>1113</td>
      <td>0.01</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1201900000000000000</td>
      <td>2019-04-12</td>
      <td>2019-04-12</td>
      <td>2019-04-26</td>
      <td>A B C INDIA LIMITED</td>
      <td>OL</td>
      <td>1118</td>
      <td>0.01</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-8b0a5260-dc45-4822-9dab-3c620fbc7df9')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-8b0a5260-dc45-4822-9dab-3c620fbc7df9 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-8b0a5260-dc45-4822-9dab-3c620fbc7df9');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
print("Total amount of bonds Encashed :",buyer_df['Denominations (INR)'].sum())
```

    Total amount of bonds Encashed : 12155.5132


## Top 10 buyers


```python
top_10_buyers = (buyer_df
                 .groupby(by="Name of the Purchaser")
                 .agg({"Denominations (INR)": "sum"})
                 .reset_index()
                 .sort_values("Denominations (INR)", ascending=False, ignore_index=True))[:10]
top_10_buyers
```





  <div id="df-e8c92d7c-fa97-4bad-8423-6cf33ff30c2d" class="colab-df-container">
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
      <th>Name of the Purchaser</th>
      <th>Denominations (INR)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>FUTURE GAMING AND HOTEL SERVICES PR</td>
      <td>1208.00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>MEGHA ENGINEERING AND INFRASTRUCTURES LI MITED</td>
      <td>821.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>QWIKSUPPLYCHAINPRIVATELIMITED</td>
      <td>410.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>HALDIA ENERGY LIMITED</td>
      <td>377.00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>VEDANTA LIMITED</td>
      <td>375.65</td>
    </tr>
    <tr>
      <th>5</th>
      <td>ESSEL MINING AND INDS LTD</td>
      <td>224.50</td>
    </tr>
    <tr>
      <th>6</th>
      <td>WESTERN UP POWER TRANSMISSION COMPANY LI MITED</td>
      <td>220.00</td>
    </tr>
    <tr>
      <th>7</th>
      <td>KEVENTER FOODPARK INFRA LIMITED</td>
      <td>195.00</td>
    </tr>
    <tr>
      <th>8</th>
      <td>MADANLAL LTD.</td>
      <td>185.50</td>
    </tr>
    <tr>
      <th>9</th>
      <td>BHARTI AIRTEL LIMITED</td>
      <td>183.00</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-e8c92d7c-fa97-4bad-8423-6cf33ff30c2d')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-e8c92d7c-fa97-4bad-8423-6cf33ff30c2d button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-e8c92d7c-fa97-4bad-8423-6cf33ff30c2d');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
fig, ax = plt.subplots(figsize=(16, 6))

container = ax.barh(y=top_10_buyers['Name of the Purchaser'], width=top_10_buyers['Denominations (INR)'])
ax.set_xlabel('Denominations in crore')
ax.set_ylabel('Name of Purchaser')
ax.invert_yaxis()
```


    
![png](electoral_files/electoral_22_0.png)
    


Top 10 buyers are:
1. FUTURE GAMING AND HOTEL SERVICES PR
2. MEGHA ENGINEERING AND INFRASTRUCTURES LI MITED
3. QWIKSUPPLYCHAINPRIVATELIMITED

## Yearly and quarterly purchase of electoral bonds


```python
years_df = (buyer_df
                 .groupby(by="Year")
                 .agg({"Denominations (INR)": "sum"})
                 .reset_index())
years_df['Denominations (INR)'] = years_df['Denominations (INR)']
years_df
```





  <div id="df-f58a7d17-2cd8-4dff-8d0e-a5d3de596e9c" class="colab-df-container">
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
      <th>Year</th>
      <th>Denominations (INR)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2019</td>
      <td>1766.1280</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020</td>
      <td>363.9601</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021</td>
      <td>1502.2927</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2022</td>
      <td>3704.8576</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2023</td>
      <td>4246.4745</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2024</td>
      <td>571.8003</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-f58a7d17-2cd8-4dff-8d0e-a5d3de596e9c')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-f58a7d17-2cd8-4dff-8d0e-a5d3de596e9c button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-f58a7d17-2cd8-4dff-8d0e-a5d3de596e9c');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
fig, ax = plt.subplots(figsize=(8, 6))

container = ax.bar(x=years_df['Year'], height=years_df['Denominations (INR)'])
ax.set_ylabel('Denominations in crore')
ax.set_xlabel('Year');
```


    
![png](electoral_files/electoral_26_0.png)
    


In year 2023 maximum in terms of denomination bought.


```python
quarter_df = (buyer_df
                 .groupby(by="Quarter")
                 .agg({"Denominations (INR)": "sum"})
                 .reset_index())
quarter_df['Denominations (INR)'] = quarter_df['Denominations (INR)']
quarter_df
```





  <div id="df-514bdb66-68f0-4f0d-9684-78d42638d8d2" class="colab-df-container">
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
      <th>Quarter</th>
      <th>Denominations (INR)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2019-Q2</td>
      <td>1488.8180</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019-Q3</td>
      <td>45.3800</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2019-Q4</td>
      <td>231.9300</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-Q1</td>
      <td>81.6700</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-Q4</td>
      <td>282.2901</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2021-Q1</td>
      <td>42.1000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2021-Q2</td>
      <td>695.3402</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2021-Q3</td>
      <td>150.5130</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2021-Q4</td>
      <td>614.3395</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2022-Q1</td>
      <td>1213.2601</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2022-Q2</td>
      <td>648.4870</td>
    </tr>
    <tr>
      <th>11</th>
      <td>2022-Q3</td>
      <td>389.5005</td>
    </tr>
    <tr>
      <th>12</th>
      <td>2022-Q4</td>
      <td>1453.6100</td>
    </tr>
    <tr>
      <th>13</th>
      <td>2023-Q1</td>
      <td>308.7626</td>
    </tr>
    <tr>
      <th>14</th>
      <td>2023-Q2</td>
      <td>970.5000</td>
    </tr>
    <tr>
      <th>15</th>
      <td>2023-Q3</td>
      <td>812.8002</td>
    </tr>
    <tr>
      <th>16</th>
      <td>2023-Q4</td>
      <td>2154.4117</td>
    </tr>
    <tr>
      <th>17</th>
      <td>2024-Q1</td>
      <td>571.8003</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-514bdb66-68f0-4f0d-9684-78d42638d8d2')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-514bdb66-68f0-4f0d-9684-78d42638d8d2 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-514bdb66-68f0-4f0d-9684-78d42638d8d2');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
fig, ax = plt.subplots(figsize=(12, 6))

container = ax.bar(x=quarter_df['Quarter'], height=quarter_df['Denominations (INR)'])
ax.set_ylabel('Denominations in crore')
ax.set_xlabel('Quarter')
plt.xticks(rotation=45);
```


    
![png](electoral_files/electoral_29_0.png)
    


## Yearly Top 3 purchaser


```python
buyer_df.head(2)
```





  <div id="df-6856c96e-1ada-4833-a694-60c6e0ec9db9" class="colab-df-container">
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
      <th>rfno</th>
      <th>Journal Date</th>
      <th>Date of Purchase</th>
      <th>Date of Expiry</th>
      <th>Name of the Purchaser</th>
      <th>Prefix</th>
      <th>Bond Number</th>
      <th>Denominations (INR)</th>
      <th>Issue Branch Code</th>
      <th>Issue Teller</th>
      <th>Status</th>
      <th>Year</th>
      <th>Month</th>
      <th>Day</th>
      <th>Quarter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1201900000000000000</td>
      <td>2019-04-12</td>
      <td>2019-04-12</td>
      <td>2019-04-26</td>
      <td>A B C INDIA LIMITED</td>
      <td>TL</td>
      <td>11448</td>
      <td>0.1</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1201900000000000000</td>
      <td>2019-04-12</td>
      <td>2019-04-12</td>
      <td>2019-04-26</td>
      <td>A B C INDIA LIMITED</td>
      <td>TL</td>
      <td>11447</td>
      <td>0.1</td>
      <td>1</td>
      <td>5899230</td>
      <td>Paid</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-6856c96e-1ada-4833-a694-60c6e0ec9db9')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-6856c96e-1ada-4833-a694-60c6e0ec9db9 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-6856c96e-1ada-4833-a694-60c6e0ec9db9');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
test_df = buyer_df.groupby(['Year', 'Name of the Purchaser']).agg({'Denominations (INR)': 'sum'}).reset_index()
test_df.sort_values(by=['Year', 'Denominations (INR)'], ascending=[True, False], inplace=True, ignore_index=True)
test_df
```





  <div id="df-f95bd7b7-c1ff-4ef4-8dcd-365b3883a9e9" class="colab-df-container">
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
      <th>Year</th>
      <th>Name of the Purchaser</th>
      <th>Denominations (INR)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2019</td>
      <td>KEVENTER FOODPARK INFRA LIMITED</td>
      <td>195.0000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019</td>
      <td>MADANLAL LTD.</td>
      <td>185.5000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2019</td>
      <td>MEGHA ENGINEERING AND INFRASTRUCTURES LI MITED</td>
      <td>130.0000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2019</td>
      <td>VEDANTA LIMITED</td>
      <td>52.6500</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2019</td>
      <td>ESSEL MINING AND INDS LTD</td>
      <td>50.0000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1587</th>
      <td>2024</td>
      <td>AMAN  JAISWAL</td>
      <td>0.1000</td>
    </tr>
    <tr>
      <th>1588</th>
      <td>2024</td>
      <td>MRPANKAJKUMARGUPTA</td>
      <td>0.1000</td>
    </tr>
    <tr>
      <th>1589</th>
      <td>2024</td>
      <td>RAJ KAMAL DRUGS</td>
      <td>0.0500</td>
    </tr>
    <tr>
      <th>1590</th>
      <td>2024</td>
      <td>MR. BISWAJIT  GHOSH</td>
      <td>0.0002</td>
    </tr>
    <tr>
      <th>1591</th>
      <td>2024</td>
      <td>KUNAL GUPTA</td>
      <td>0.0001</td>
    </tr>
  </tbody>
</table>
<p>1592 rows × 3 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-f95bd7b7-c1ff-4ef4-8dcd-365b3883a9e9')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-f95bd7b7-c1ff-4ef4-8dcd-365b3883a9e9 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-f95bd7b7-c1ff-4ef4-8dcd-365b3883a9e9');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
yearly_df = test_df.groupby('Year').apply(lambda x: x.nlargest(3, 'Denominations (INR)')).reset_index(drop=True)
yearly_df
```





  <div id="df-8bacc8f9-bb36-43af-a1dc-270249b6e132" class="colab-df-container">
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
      <th>Year</th>
      <th>Name of the Purchaser</th>
      <th>Denominations (INR)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2019</td>
      <td>KEVENTER FOODPARK INFRA LIMITED</td>
      <td>195.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019</td>
      <td>MADANLAL LTD.</td>
      <td>185.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2019</td>
      <td>MEGHA ENGINEERING AND INFRASTRUCTURES LI MITED</td>
      <td>130.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020</td>
      <td>FUTURE GAMING AND HOTEL SERVICES PR</td>
      <td>150.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020</td>
      <td>HALDIA ENERGY LIMITED</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2020</td>
      <td>ESSEL MINING AND INDS LTD</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2021</td>
      <td>FUTURE GAMING AND HOTEL SERVICES PR</td>
      <td>334.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2021</td>
      <td>MEGHA ENGINEERING AND INFRASTRUCTURES LI MITED</td>
      <td>178.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2021</td>
      <td>HALDIA ENERGY LIMITED</td>
      <td>105.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2022</td>
      <td>FUTURE GAMING AND HOTEL SERVICES PR</td>
      <td>405.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2022</td>
      <td>QWIKSUPPLYCHAINPRIVATELIMITED</td>
      <td>360.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>2022</td>
      <td>VEDANTA LIMITED</td>
      <td>228.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>2023</td>
      <td>MEGHA ENGINEERING AND INFRASTRUCTURES LI MITED</td>
      <td>415.0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>2023</td>
      <td>FUTURE GAMING AND HOTEL SERVICES PR</td>
      <td>256.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>2023</td>
      <td>WESTERN UP POWER TRANSMISSION COMPANY LI MITED</td>
      <td>190.0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>2024</td>
      <td>FUTURE GAMING AND HOTEL SERVICES PR</td>
      <td>63.0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>2024</td>
      <td>BHARTI AIRTEL LIMITED</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>2024</td>
      <td>RUNGTA SONS P LTD</td>
      <td>50.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-8bacc8f9-bb36-43af-a1dc-270249b6e132')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-8bacc8f9-bb36-43af-a1dc-270249b6e132 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-8bacc8f9-bb36-43af-a1dc-270249b6e132');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
import matplotlib.pyplot as plt
for year in yearly_df['Year'].unique():
    temp_df = yearly_df[yearly_df['Year'] == year]
    fig, ax = plt.subplots(figsize=(6, 2))
    container = ax.barh(y=temp_df['Name of the Purchaser'], width=temp_df['Denominations (INR)'])
    ax.set_xlabel('Denominations in crore')
    ax.set_ylabel('Name of the Purchaser')
    ax.set_title(f'Top 3 Purchasers in {year}')
    ax.invert_yaxis()
    plt.show()

```


    
![png](electoral_files/electoral_34_0.png)
    



    
![png](electoral_files/electoral_34_1.png)
    



    
![png](electoral_files/electoral_34_2.png)
    



    
![png](electoral_files/electoral_34_3.png)
    



    
![png](electoral_files/electoral_34_4.png)
    



    
![png](electoral_files/electoral_34_5.png)
    


## Import dataset of receivers


```python
receiver_df = pd.read_csv('/content/sample_data/EB_Redemptions_Updated.csv')
receiver_df.drop('Sr No.', axis=1, inplace=True)
receiver_df.head()
```





  <div id="df-986893d9-a284-4282-aca5-d3c29d67558d" class="colab-df-container">
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
      <th>Date of Encashment</th>
      <th>Name of the Political Party</th>
      <th>Account no. of Political Party</th>
      <th>Prefix</th>
      <th>Bond Number</th>
      <th>Denominations (INR)</th>
      <th>Pay Branch Code</th>
      <th>Pay Teller</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>12-Apr-19</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>OC</td>
      <td>775</td>
      <td>1,00,00,000</td>
      <td>800</td>
      <td>2770121</td>
    </tr>
    <tr>
      <th>1</th>
      <td>12-Apr-19</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>OC</td>
      <td>3975</td>
      <td>1,00,00,000</td>
      <td>800</td>
      <td>2770121</td>
    </tr>
    <tr>
      <th>2</th>
      <td>12-Apr-19</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>OC</td>
      <td>3967</td>
      <td>1,00,00,000</td>
      <td>800</td>
      <td>2770121</td>
    </tr>
    <tr>
      <th>3</th>
      <td>12-Apr-19</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>TL</td>
      <td>10418</td>
      <td>10,00,000</td>
      <td>800</td>
      <td>2770121</td>
    </tr>
    <tr>
      <th>4</th>
      <td>12-Apr-19</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>TL</td>
      <td>126</td>
      <td>10,00,000</td>
      <td>800</td>
      <td>2770121</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-986893d9-a284-4282-aca5-d3c29d67558d')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-986893d9-a284-4282-aca5-d3c29d67558d button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-986893d9-a284-4282-aca5-d3c29d67558d');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
receiver_df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 20421 entries, 0 to 20420
    Data columns (total 8 columns):
     #   Column                          Non-Null Count  Dtype 
    ---  ------                          --------------  ----- 
     0   Date of Encashment              20421 non-null  object
     1   Name of the Political Party     20421 non-null  object
     2   Account no. of Political Party  20421 non-null  object
     3   Prefix                          20421 non-null  object
     4   Bond Number                     20421 non-null  int64 
     5   Denominations (INR)             20421 non-null  object
     6   Pay Branch Code                 20421 non-null  int64 
     7   Pay Teller                      20421 non-null  int64 
    dtypes: int64(3), object(5)
    memory usage: 1.2+ MB



```python
receiver_df['Date of Encashment'] = pd.to_datetime(receiver_df['Date of Encashment'], format="%d-%b-%y")
receiver_df['Year'] = receiver_df['Date of Encashment'].dt.strftime('%Y')
receiver_df['Month'] = receiver_df['Date of Encashment'].dt.strftime('%m')
receiver_df['Day'] = receiver_df['Date of Encashment'].dt.strftime('%d')
receiver_df['Quarter'] = receiver_df['Date of Encashment'].dt.to_period('Q').dt.strftime('%Y-Q%q')
```


```python
receiver_df['Denominations (INR)'] = receiver_df['Denominations (INR)'].apply(lambda x: x.replace(',', ''))
receiver_df['Denominations (INR)'] = pd.to_numeric(receiver_df['Denominations (INR)'])
receiver_df['Denominations (INR)'] = receiver_df['Denominations (INR)'].divide(10000000)
receiver_df.head()
```





  <div id="df-ad4eb73f-743d-459e-880a-3f3facd76dea" class="colab-df-container">
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
      <th>Date of Encashment</th>
      <th>Name of the Political Party</th>
      <th>Account no. of Political Party</th>
      <th>Prefix</th>
      <th>Bond Number</th>
      <th>Denominations (INR)</th>
      <th>Pay Branch Code</th>
      <th>Pay Teller</th>
      <th>Year</th>
      <th>Month</th>
      <th>Day</th>
      <th>Quarter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2019-04-12</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>OC</td>
      <td>775</td>
      <td>1.0</td>
      <td>800</td>
      <td>2770121</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019-04-12</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>OC</td>
      <td>3975</td>
      <td>1.0</td>
      <td>800</td>
      <td>2770121</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2019-04-12</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>OC</td>
      <td>3967</td>
      <td>1.0</td>
      <td>800</td>
      <td>2770121</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2019-04-12</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>TL</td>
      <td>10418</td>
      <td>0.1</td>
      <td>800</td>
      <td>2770121</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2019-04-12</td>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>*******5199</td>
      <td>TL</td>
      <td>126</td>
      <td>0.1</td>
      <td>800</td>
      <td>2770121</td>
      <td>2019</td>
      <td>04</td>
      <td>12</td>
      <td>2019-Q2</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-ad4eb73f-743d-459e-880a-3f3facd76dea')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-ad4eb73f-743d-459e-880a-3f3facd76dea button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-ad4eb73f-743d-459e-880a-3f3facd76dea');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
# list of political party which encashed electoral bonds
print(receiver_df['Name of the Political Party'].unique())
print(receiver_df['Name of the Political Party'].nunique())
```

    ['ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM' 'BHARAT RASHTRA SAMITHI'
     'BHARATIYA JANATA PARTY' 'PRESIDENT, ALL INDIA CONGRESS COMMITTEE'
     'SHIVSENA' 'TELUGU DESAM PARTY'
     'YSR  CONGRESS PARTY  (YUVAJANA SRAMIKA RYTHU CONGRESS PARTY)'
     'DRAVIDA MUNNETRA KAZHAGAM (DMK)' 'JANATA DAL ( SECULAR )'
     'NATIONALIST CONGRESS PARTY MAHARASHTRA PRADESH'
     'ALL INDIA TRINAMOOL CONGRESS' 'BIHAR PRADESH JANTA DAL(UNITED)'
     'RASHTRIYA JANTA DAL' 'AAM AADMI PARTY' 'ADYAKSHA SAMAJVADI PARTY'
     'SHIROMANI AKALI DAL' 'JHARKHAND MUKTI MORCHA'
     'JAMMU AND KASHMIR NATIONAL CONFERENCE' 'BIJU JANATA DAL'
     'GOA FORWARD PARTY' 'MAHARASHTRAWADI GOMNTAK PARTY'
     'SIKKIM KRANTIKARI MORCHA' 'JANASENA PARTY' 'SIKKIM DEMOCRATIC FRONT']
    24


## top political party in terms of electoral bond enchased


```python
top_receiver_df = receiver_df.groupby(by='Name of the Political Party').agg({'Denominations (INR)': 'sum'}).reset_index()
top_receiver_df.sort_values(by='Denominations (INR)',ascending=False, inplace=True, ignore_index=True)
top_receiver_df
```





  <div id="df-1963c768-f266-4b96-a53b-e235166234d7" class="colab-df-container">
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
      <th>Name of the Political Party</th>
      <th>Denominations (INR)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>BHARATIYA JANATA PARTY</td>
      <td>6060.5111</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ALL INDIA TRINAMOOL CONGRESS</td>
      <td>1609.5314</td>
    </tr>
    <tr>
      <th>2</th>
      <td>PRESIDENT, ALL INDIA CONGRESS COMMITTEE</td>
      <td>1421.8655</td>
    </tr>
    <tr>
      <th>3</th>
      <td>BHARAT RASHTRA SAMITHI</td>
      <td>1214.7099</td>
    </tr>
    <tr>
      <th>4</th>
      <td>BIJU JANATA DAL</td>
      <td>775.5000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>DRAVIDA MUNNETRA KAZHAGAM (DMK)</td>
      <td>639.0000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>YSR  CONGRESS PARTY  (YUVAJANA SRAMIKA RYTHU C...</td>
      <td>337.0000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>TELUGU DESAM PARTY</td>
      <td>218.8800</td>
    </tr>
    <tr>
      <th>8</th>
      <td>SHIVSENA</td>
      <td>159.3814</td>
    </tr>
    <tr>
      <th>9</th>
      <td>RASHTRIYA JANTA DAL</td>
      <td>73.5000</td>
    </tr>
    <tr>
      <th>10</th>
      <td>AAM AADMI PARTY</td>
      <td>65.4500</td>
    </tr>
    <tr>
      <th>11</th>
      <td>JANATA DAL ( SECULAR )</td>
      <td>43.5000</td>
    </tr>
    <tr>
      <th>12</th>
      <td>SIKKIM KRANTIKARI MORCHA</td>
      <td>36.5000</td>
    </tr>
    <tr>
      <th>13</th>
      <td>NATIONALIST CONGRESS PARTY MAHARASHTRA PRADESH</td>
      <td>31.0000</td>
    </tr>
    <tr>
      <th>14</th>
      <td>JANASENA PARTY</td>
      <td>21.0000</td>
    </tr>
    <tr>
      <th>15</th>
      <td>ADYAKSHA SAMAJVADI PARTY</td>
      <td>14.0500</td>
    </tr>
    <tr>
      <th>16</th>
      <td>BIHAR PRADESH JANTA DAL(UNITED)</td>
      <td>14.0000</td>
    </tr>
    <tr>
      <th>17</th>
      <td>JHARKHAND MUKTI MORCHA</td>
      <td>13.5000</td>
    </tr>
    <tr>
      <th>18</th>
      <td>SHIROMANI AKALI DAL</td>
      <td>7.2600</td>
    </tr>
    <tr>
      <th>19</th>
      <td>ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM</td>
      <td>6.0500</td>
    </tr>
    <tr>
      <th>20</th>
      <td>SIKKIM DEMOCRATIC FRONT</td>
      <td>5.5000</td>
    </tr>
    <tr>
      <th>21</th>
      <td>MAHARASHTRAWADI GOMNTAK PARTY</td>
      <td>0.5500</td>
    </tr>
    <tr>
      <th>22</th>
      <td>JAMMU AND KASHMIR NATIONAL CONFERENCE</td>
      <td>0.5000</td>
    </tr>
    <tr>
      <th>23</th>
      <td>GOA FORWARD PARTY</td>
      <td>0.3500</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-1963c768-f266-4b96-a53b-e235166234d7')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-1963c768-f266-4b96-a53b-e235166234d7 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-1963c768-f266-4b96-a53b-e235166234d7');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
import matplotlib.pyplot as plt
fig, ax = plt.subplots(figsize=(12, 6))

container = ax.barh(y=top_receiver_df['Name of the Political Party'][:10], width=top_receiver_df['Denominations (INR)'][:10])
ax.set_xlabel('Denominations in crore')
ax.set_ylabel('Name of Political Party')
ax.invert_yaxis()

```


    
![png](electoral_files/electoral_43_0.png)
    


Top 3 political parties are:
1. BHARATIYA JANATA PARTY
2. ALL INDIA TRINAMOOL CONGRESS
3. PRESIDENT, ALL INDIA CONGRESS COMMITTEE


```python
import matplotlib.pyplot as plt

# Extract top 10 parties from top_receiver_df
top_10_parties = top_receiver_df[:8]['Name of the Political Party']

# Extract denominations for top 10 parties
top_10_denominations = top_receiver_df[:8]['Denominations (INR)']

# Create a pie chart
fig, ax = plt.subplots()
ax.pie(top_10_denominations, labels=top_10_parties, autopct="%1.1f%%", startangle=40)

# Equal aspect ratio ensures a circular pie chart
ax.axis('equal')

# Add title
ax.set_title("Top 10 Political Parties by Electoral Bond Encashment")

# Show the pie chart
plt.show()

```


    
![png](electoral_files/electoral_45_0.png)
    



```python
years_df = (receiver_df
                 .groupby(by="Year")
                 .agg({"Denominations (INR)": "sum"})
                 .reset_index())
years_df['Denominations (INR)'] = years_df['Denominations (INR)']
years_df
```





  <div id="df-6236bc3b-9431-4d0a-acf8-ebeb380117f4" class="colab-df-container">
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
      <th>Year</th>
      <th>Denominations (INR)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2019</td>
      <td>2385.0886</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020</td>
      <td>363.9600</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021</td>
      <td>1502.2625</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2022</td>
      <td>3701.4569</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2023</td>
      <td>4246.2713</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2024</td>
      <td>570.0500</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-6236bc3b-9431-4d0a-acf8-ebeb380117f4')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-6236bc3b-9431-4d0a-acf8-ebeb380117f4 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-6236bc3b-9431-4d0a-acf8-ebeb380117f4');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>




## Yealy and Quarterly plot


```python
fig, ax = plt.subplots(figsize=(8, 6))

container = ax.bar(x=years_df['Year'], height=years_df['Denominations (INR)'])
ax.set_ylabel('Denominations in crore')
ax.set_xlabel('Year');
```


    
![png](electoral_files/electoral_48_0.png)
    



```python
quarter_df = (receiver_df
                 .groupby(by="Quarter")
                 .agg({"Denominations (INR)": "sum"})
                 .reset_index())
quarter_df['Denominations (INR)'] = quarter_df['Denominations (INR)']
quarter_df
```





  <div id="df-850bc457-bc8e-4ebe-93db-9f1e7dae9bb6" class="colab-df-container">
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
      <th>Quarter</th>
      <th>Denominations (INR)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2019-Q2</td>
      <td>2107.7786</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019-Q3</td>
      <td>45.3800</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2019-Q4</td>
      <td>231.9300</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-Q1</td>
      <td>81.6700</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-Q4</td>
      <td>282.2900</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2021-Q1</td>
      <td>42.0700</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2021-Q2</td>
      <td>695.3400</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2021-Q3</td>
      <td>150.5130</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2021-Q4</td>
      <td>614.3395</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2022-Q1</td>
      <td>1212.8600</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2022-Q2</td>
      <td>648.4870</td>
    </tr>
    <tr>
      <th>11</th>
      <td>2022-Q3</td>
      <td>389.5000</td>
    </tr>
    <tr>
      <th>12</th>
      <td>2022-Q4</td>
      <td>1450.6099</td>
    </tr>
    <tr>
      <th>13</th>
      <td>2023-Q1</td>
      <td>308.7600</td>
    </tr>
    <tr>
      <th>14</th>
      <td>2023-Q2</td>
      <td>970.3500</td>
    </tr>
    <tr>
      <th>15</th>
      <td>2023-Q3</td>
      <td>812.7501</td>
    </tr>
    <tr>
      <th>16</th>
      <td>2023-Q4</td>
      <td>2154.4112</td>
    </tr>
    <tr>
      <th>17</th>
      <td>2024-Q1</td>
      <td>570.0500</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-850bc457-bc8e-4ebe-93db-9f1e7dae9bb6')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-850bc457-bc8e-4ebe-93db-9f1e7dae9bb6 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-850bc457-bc8e-4ebe-93db-9f1e7dae9bb6');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>

    </div>
  </div>





```python
fig, ax = plt.subplots(figsize=(12, 6))

container = ax.bar(x=quarter_df['Quarter'], height=quarter_df['Denominations (INR)'])
ax.set_ylabel('Denominations in crore')
ax.set_xlabel('Quarter')
plt.xticks(rotation=45);
```


    
![png](electoral_files/electoral_50_0.png)
    



```python
receiver_df['Name of the Political Party'].unique()
```




    array(['ALL INDIA ANNA DRAVIDA MUNNETRA KAZHAGAM',
           'BHARAT RASHTRA SAMITHI', 'BHARATIYA JANATA PARTY',
           'PRESIDENT, ALL INDIA CONGRESS COMMITTEE', 'SHIVSENA',
           'TELUGU DESAM PARTY',
           'YSR  CONGRESS PARTY  (YUVAJANA SRAMIKA RYTHU CONGRESS PARTY)',
           'DRAVIDA MUNNETRA KAZHAGAM (DMK)', 'JANATA DAL ( SECULAR )',
           'NATIONALIST CONGRESS PARTY MAHARASHTRA PRADESH',
           'ALL INDIA TRINAMOOL CONGRESS', 'BIHAR PRADESH JANTA DAL(UNITED)',
           'RASHTRIYA JANTA DAL', 'AAM AADMI PARTY',
           'ADYAKSHA SAMAJVADI PARTY', 'SHIROMANI AKALI DAL',
           'JHARKHAND MUKTI MORCHA', 'JAMMU AND KASHMIR NATIONAL CONFERENCE',
           'BIJU JANATA DAL', 'GOA FORWARD PARTY',
           'MAHARASHTRAWADI GOMNTAK PARTY', 'SIKKIM KRANTIKARI MORCHA',
           'JANASENA PARTY', 'SIKKIM DEMOCRATIC FRONT'], dtype=object)



## Comparision of bjp, tmc and congress on quarterly basis


```python
bjp_df = receiver_df[receiver_df['Name of the Political Party'] == 'BHARATIYA JANATA PARTY']
tmc_df = receiver_df[receiver_df['Name of the Political Party'] == 'ALL INDIA TRINAMOOL CONGRESS']
congress_df = receiver_df[receiver_df['Name of the Political Party'] == 'PRESIDENT, ALL INDIA CONGRESS COMMITTEE']

bjp_quarter_df = bjp_df.groupby('Quarter').agg({'Denominations (INR)': 'sum'}).reset_index()
tmc_quarter_df = tmc_df.groupby('Quarter').agg({'Denominations (INR)': 'sum'}).reset_index()
congress_quarter_df = congress_df.groupby('Quarter').agg({'Denominations (INR)': 'sum'}).reset_index()

fig, ax = plt.subplots(figsize=(12, 6))

ax.plot(bjp_quarter_df['Quarter'], bjp_quarter_df['Denominations (INR)'], label='BJP')
ax.plot(tmc_quarter_df['Quarter'], tmc_quarter_df['Denominations (INR)'], label='TMC')
ax.plot(congress_quarter_df['Quarter'], congress_quarter_df['Denominations (INR)'], label='Congress')

ax.set_xlabel('Quarter')
ax.set_ylabel('Denominations (INR) in crore')
ax.legend()
plt.xticks(rotation=45);

```


    
![png](electoral_files/electoral_53_0.png)
    



```python

```
