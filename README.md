# Qatar-Real-Estate-Analysis
## About
The goal of this analysis is to provide an in-depth understanding of the real estate market in Qatar from 2020 to 2023. By examining the prices, types, locations, and trends of real estate properties, this analysis aims to offer valuable insights for stakeholders, investors, and individuals interested in the Qatar real estate market.
## Resources:
[Weekly Real Estate Newsletter](https://www.data.gov.qa/explore/dataset/weekly-real-estate-newsletter/information/?sort=real_estate_value)

[Data.gov.qa](https://www.data.gov.qa/pages/default/)

## Data Cleaning 
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv(r"Downloads\weekly-real-estate-newsletter.csv")
df.head()

.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
