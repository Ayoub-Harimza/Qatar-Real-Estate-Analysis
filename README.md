# About
The goal of this analysis is to provide an in-depth understanding of the real estate market in Qatar from 2020 to 2023. By examining the prices, types, locations, and trends of real estate properties, this analysis aims to offer valuable insights for stakeholders, investors, and individuals interested in the Qatar real estate market.

# Resources
[Data.gov.qa](https://www.data.gov.qa/pages/default/)

[Weekly Real Estate Newsletter](https://www.data.gov.qa/explore/dataset/weekly-real-estate-newsletter/information/)

## Data Preprocessing Steps

This README provides an overview of the preprocessing steps conducted on a real estate dataset for analysis. For the detailed analysis and code implementation, please refer to the accompanying Jupyter Notebook available [here](https://github.com/Ayoub-Harimza/Qatar-Real-Estate-Analysis/blob/main/Qatar%20Real%20Estate%20Dataset.ipynb).

In this project, I performed several preprocessing steps on a real estate dataset to ensure its cleanliness and readiness for analysis. Below is a summary of the steps undertaken:

1. **Data Loading**: Initially, I loaded the dataset using Pandas' `read_csv()` function, specifying the appropriate separator (';') as the data was semi-colon separated.

2. **Column Removal**: Non-essential columns such as 'اسم البلدية', 'اسم المنطقة', 'نوع العقار', and 'Zone Name' were identified and removed using the `drop()` method to streamline the dataset for analysis.

3. **Date Conversion**: The 'Date of Contract' column was converted into a datetime format using the `pd.to_datetime()` function to enable temporal analysis.

4. **Date Filtering**: I filtered the dataset to include only entries within the timeframe of interest, specifically between 2020 and 2023, using boolean indexing.

5. **Index Resetting**: After filtering, the index was reset to ensure consistency and reflect the new filtered dataset accurately.

6. **Decimal Formatting**: The 'Price per Square Foot' and 'Real Estate Value' columns were formatted to display two decimal places and remove any trailing zeros using lambda functions and string formatting for better presentation.

7. **Data Validation**: To ensure data integrity, I checked for unique values in specific columns, such as 'Municipality Name' and 'Real Estate Type', using the `value_counts()` method.

8. **Data Cleaning**: Identified many misspelled municipality names and real estate types, so I conducted research and corrected them using the `replace()` method to standardize the dataset.

9. **Data Export**: Finally, the cleaned dataset was exported to a CSV file named 'Real Estate Qatar.csv' for further analysis and sharing.

These preprocessing steps were crucial in preparing the dataset for subsequent analysis and visualization, ensuring that the data was accurate, consistent, and ready for exploration.

# Data Visualization with Tableau
The data was visualized using Tableau. The interactive version of the dashboard can be found on [Tableau's website](https://public.tableau.com/app/profile/ayoub.harimza/viz/QatarRealEstateAnalysis2020-2023/Dashboard1)

![Image](https://github.com/Ayoub-Harimza/Qatar-Real-Estate-Analysis/blob/main/Tableau%20Visualization/Real%20Estate%20Dashboard.PNG)

# Key Insights:

1. **Top Priciest Properties**: 
   - The top five priciest real estate properties are all located in Al Doha, indicating it as a prime area for high-value investments.
   - Multi-purpose buildings and residential units dominate the list of expensive properties, with transactions ranging from 2020 to 2023.

2. **Average Property Prices by Type**:
   - Hotels and towers are the most expensive property types on average, with prices exceeding 300 million QAR.
   - Residential buildings, administrative buildings, and vacant land are relatively more affordable, with prices ranging from millions to tens of millions of QAR.

3. **Total Value of Sold Properties by Municipality**:
   - Al Doha stands out as the leading municipality in terms of total value of sold properties, indicating robust real estate activity and high demand in this area.
   - Other significant municipalities include Al Rayyan, Al Daayen, and Al Wakrah, suggesting diverse investment opportunities across Qatar.

4. **Total Value of Sold Properties by Year of Contract**:
   - The total value of sold properties fluctuates over the years, with a peak in 2021 followed by a slight decline in 2022 and 2023.
   - Despite fluctuations, the real estate market remains lucrative, with billions of QAR worth of properties being transacted annually.

By leveraging these insights, stakeholders can make informed decisions regarding investments, development projects, and market strategies in the Qatar real estate sector. This analysis serves as a valuable resource for understanding market dynamics and identifying potential opportunities for growth and profitability.
 
## Contact

Feel free to reach out if you have any questions or would like to discuss this project further:

- **Email:** Ayoubharimza21@gmail.com
- **LinkedIn:** [Ayoub Harimza](https://www.linkedin.com/in/ayoub-harimza-4926a22a7/)
