```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```


```python
df = pd.read_csv(r"Downloads\weekly-real-estate-newsletter.csv")
df.head()
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
      <th>Date of Contract;Municipality Name;اسم البلدية;Zone Name;اسم المنطقة;Real Estate Type;نوع العقار;Area in Square Meters;Price per Square Foot;Real Estate Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2024-01-11;Doha;الدوحة;Al Thumama 46;الثمامة 4...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2024-01-11;Doha;الدوحة;Old Airport;المطار القد...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2024-01-11;Al Rayyan;الريان;Muaither 53;معيذر ...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2024-01-11;Al Wakrah;الوكرة;Al Wukair;الوكير;R...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2024-01-11;Doha;الدوحة;The Pearl lsland;جزيرة ...</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Loading the DataFrame with proper separator
df = pd.read_csv('Downloads\weekly-real-estate-newsletter.csv', sep=';')
#Removing non useful columns (for my Analysis)
columns_to_remove = ['اسم البلدية','اسم المنطقة','نوع العقار','Zone Name']
df.drop(columns=columns_to_remove , inplace=True )
df.head()
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
      <th>Date of Contract</th>
      <th>Municipality Name</th>
      <th>Real Estate Type</th>
      <th>Area in Square Meters</th>
      <th>Price per Square Foot</th>
      <th>Real Estate Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2024-01-11</td>
      <td>Doha</td>
      <td>Residence</td>
      <td>425</td>
      <td>415.332</td>
      <td>1900000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2024-01-11</td>
      <td>Doha</td>
      <td>Vacant Land</td>
      <td>848</td>
      <td>450.015</td>
      <td>4107644</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2024-01-11</td>
      <td>Al Rayyan</td>
      <td>Residence</td>
      <td>208</td>
      <td>468.982</td>
      <td>1050000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2024-01-11</td>
      <td>Al Wakrah</td>
      <td>Residence</td>
      <td>459</td>
      <td>356.230</td>
      <td>1760000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2024-01-11</td>
      <td>Doha</td>
      <td>Residential Unit</td>
      <td>136</td>
      <td>1018.670</td>
      <td>1500000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Converting "Date of Contract" column to datetime type
df['Date of Contract'] = pd.to_datetime(df['Date of Contract'])

# Filtering the DataFrame to include only dates between 2020 and 2023(No need to add the few weeks of 2024)
df = df[(df['Date of Contract'].dt.year >= 2020) & (df['Date of Contract'].dt.year <= 2023)]

# Reseting index
df.reset_index(drop=True, inplace=True)

# Formating the new columns with two decimal places and removing trailing zeros
df['Price per Square Foot'] = df['Price per Square Foot'].apply(lambda x: '{:,.2f}'.format(x).rstrip('0').rstrip('.'))
df['Real Estate Value'] = df['Real Estate Value'].apply(lambda x: '{:,.2f}'.format(x).rstrip('0').rstrip('.'))
df.head()
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
      <th>Date of Contract</th>
      <th>Municipality Name</th>
      <th>Real Estate Type</th>
      <th>Area in Square Meters</th>
      <th>Price per Square Foot</th>
      <th>Real Estate Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2023-12-28</td>
      <td>Doha</td>
      <td>Residence</td>
      <td>509</td>
      <td>438.05</td>
      <td>2,400,000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2023-12-28</td>
      <td>Al Rayyan</td>
      <td>Vacant Land</td>
      <td>613</td>
      <td>303.11</td>
      <td>2,000,000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2023-12-28</td>
      <td>Al Rayyan</td>
      <td>Vacant Land</td>
      <td>898</td>
      <td>280.05</td>
      <td>2,707,000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2023-12-28</td>
      <td>Doha</td>
      <td>Residential Unit</td>
      <td>152</td>
      <td>919.08</td>
      <td>1,506,189</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2023-12-28</td>
      <td>Al Khor and Al Dakhira</td>
      <td>Vacant Land</td>
      <td>505</td>
      <td>349.54</td>
      <td>1,900,000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Getting unique values in specific columns to make sure that the data is well stractured
columns_to_check = ['Municipality Name', 'Real Estate Type']
for column in columns_to_check:
    unique_values = df[column].value_counts()
    print("Unique values in column '{}':".format(column))
    print(unique_values)
```

    Unique values in column 'Municipality Name':
    Municipality Name
    Al Rayyan                 3810
    Doha                      3787
    Al Daayen                 2686
    Umm Slal                  1552
    Al Wakrah                 1485
    Al Khor and Al Dakhira     850
    Al Shamal                  650
    Al Sheehaniya               43
    Al wakra                    39
    Al Doha                     23
    Umm SlaUmm Slal              3
    Al Khor and Al Khor          3
    Name: count, dtype: int64
    Unique values in column 'Real Estate Type':
    Real Estate Type
    Residence                                 6473
    Vacant Land                               6453
    Residential Building                       616
    Residential Unit                           456
    Multi-purpose Vacant Land                  135
    Multi-purpose Building                     132
    Apartment Complex                          117
    Commercial Building                         65
    Residenc                                    47
    Shops                                       29
    Tower                                        9
    Residential  Tower                           8
    mercial Building                             6
    Residential Building and Shops               3
    Residential commercial building              3
    Commercial and AdministrativeBuilding        3
    Residential Tower                            3
    commercial Building                          2
    Building                                     2
    Palace                                       2
    Hotel Appartments                            2
    Administrative and commercial building       2
    Hotel                                        2
    Vacant  Land                                 1
    Administrative  building                     1
    Residential building                         1
    Commercial and administrative building       1
    mmercial Building                            1
    Residential Buildings                        1
    Multi-Purpose Commerial Building             1
    Name: count, dtype: int64
    


```python
# I noticed that there's many misspeled Municipalities Names & Real Estate Type so i had to rewrite them 
df['Municipality Name'] = df['Municipality Name'].replace({'Doha': 'Al Doha', 'Al wakra': 'Al Wakrah', 'Umm SlaUmm Slal': 'Umm Slal', 'Al Khor and Al Khor': 'Al Khor', 'Al Khor and Al Dakhira': 'Al Khor'})
df['Real Estate Type'] = df['Real Estate Type'].replace({'Residenc':'Residence','Residential  Tower':'Residential Tower','mercial Building':'Commercial Building','commercial Building':'Commercial Building','Residential Building and Shop':'Residential Building and Shops ','Residential commercial building':'Residential and commercial building','Commercial and AdministrativeBuilding':'Commercial and Administrative Building','Commercial and administrative Building':'Commercial and Administrative Building','Administrative and commercial building':'Commercial and Administrative Building','Vacant  Land':'Vacant Land','Administrative  building':'Administrative building','Residential Buildings':'Residential Building','mmercial Building':'Commercial Building','commercial Building':'Commercial Building','Multi-Purpose Commerial Building':'Multi-Purpose and Commerial Building','Residential building':'Residential Building'})
```


```python
# And My Mission is done here by cleaning all the data and make it ready for visualization
df.head()
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
      <th>Date of Contract</th>
      <th>Municipality Name</th>
      <th>Real Estate Type</th>
      <th>Area in Square Meters</th>
      <th>Price per Square Foot</th>
      <th>Real Estate Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2023-12-28</td>
      <td>Al Doha</td>
      <td>Residence</td>
      <td>509</td>
      <td>438.05</td>
      <td>2,400,000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2023-12-28</td>
      <td>Al Rayyan</td>
      <td>Vacant Land</td>
      <td>613</td>
      <td>303.11</td>
      <td>2,000,000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2023-12-28</td>
      <td>Al Rayyan</td>
      <td>Vacant Land</td>
      <td>898</td>
      <td>280.05</td>
      <td>2,707,000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2023-12-28</td>
      <td>Al Doha</td>
      <td>Residential Unit</td>
      <td>152</td>
      <td>919.08</td>
      <td>1,506,189</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2023-12-28</td>
      <td>Al Khor</td>
      <td>Vacant Land</td>
      <td>505</td>
      <td>349.54</td>
      <td>1,900,000</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Downloading the data as a csv file
from pathlib import Path
filepath = Path('./Real Estate Qatar.csv')
filepath.parent.mkdir(parents=True, exist_ok=True)
df.to_csv(filepath)
```


```python

```
