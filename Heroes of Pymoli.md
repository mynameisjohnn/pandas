
# Heroes of Pymoli Data Analysis
Obeservations:
1. Of the disclosed genders, males makeup majority of the players at roughly 81%.
2. Age group 20-24, purchased the most items at 338 with a total purchase value of 1,003.03 dollars amonst all age groups.
3. Final Critic is the most popular item with 14 purchases, but it is not a significantlly purchased more than the other top 5 as the firth most popular item has 10 purchases.


```python
# Dependencies
import pandas as pd
import numpy as np
```


```python
# Save file path to variable
data1 = "Resources/purchase_data.json"
data2 = "Resources/purchase_data2.json"
```


```python
# Read with Pandas in to Dataframes
data1_df = pd.read_json(data1)
data2_df = pd.read_json(data2)
```


```python
# Print first five rows in Data 1
data1_df.head()
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
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Print first five rows in Data 2
data2_df.head()
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
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20</td>
      <td>Male</td>
      <td>93</td>
      <td>Apocalyptic Battlescythe</td>
      <td>4.49</td>
      <td>Iloni35</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>12</td>
      <td>Dawne</td>
      <td>3.36</td>
      <td>Aidaira26</td>
    </tr>
    <tr>
      <th>2</th>
      <td>17</td>
      <td>Male</td>
      <td>5</td>
      <td>Putrid Fan</td>
      <td>2.63</td>
      <td>Irim47</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17</td>
      <td>Male</td>
      <td>123</td>
      <td>Twilight's Carver</td>
      <td>2.55</td>
      <td>Irith83</td>
    </tr>
    <tr>
      <th>4</th>
      <td>22</td>
      <td>Male</td>
      <td>154</td>
      <td>Feral Katana</td>
      <td>4.11</td>
      <td>Philodil43</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Merge both Dataframes in to one Dataframe and print
data_all = pd.concat([data1_df,data2_df])
data_all.head()
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
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>



# Player Count


```python
# PLAYER COUNT

# Total Number of Players
players = pd.DataFrame(
        {"Total Players": [data_all["SN"].nunique()]
        }
    )
players
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
      <th>Total Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>612</td>
    </tr>
  </tbody>
</table>
</div>



# Purchasing Analysis (Total)


```python
# PURCHASING ANALYSIS

# Number of Unique Items
unique = data_all["Item Name"].nunique()

# Average Purchase Price
price = data_all["Price"].mean()

# Total Number of Purchases
purchases = data_all["Price"].count()

# Total Revenue
revenue = data_all["Price"].sum()

# Combine all data in to Purchasing Analysis
purchasing_analysis = pd.DataFrame(
        {"Number of Unique Items": [unique],
        "Average Price": [round(price,2)],
        "Number of Purchases": [purchases],
        "Total Revenue": [revenue]}
        )
# Add Formatting
purchasing_analysis['Average Price'] = purchasing_analysis['Average Price'].map('${:,.2f}'.format)
purchasing_analysis['Total Revenue'] = purchasing_analysis['Total Revenue'].map('${:,.2f}'.format)

purchasing_analysis
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
      <th>Average Price</th>
      <th>Number of Purchases</th>
      <th>Number of Unique Items</th>
      <th>Total Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>$2.93</td>
      <td>858</td>
      <td>180</td>
      <td>$2,514.43</td>
    </tr>
  </tbody>
</table>
</div>



# Gender Demographics


```python
# GENDER DEMOGRAPHICS TABLE

# Determine Count and Percent for Male
male_count=data_all.loc[data_all.Gender == 'Male']['SN'].nunique()
male_perc=100*male_count/data_all["SN"].nunique()

# Determine Count and Percent for Female
female_count=data_all.loc[data_all.Gender == 'Female']['SN'].nunique()
female_perc=100*female_count/data_all["SN"].nunique()

# Determine Count and Percent for Other
other_count=data_all.loc[data_all.Gender == 'Other / Non-Disclosed']['SN'].nunique()
other_perc=100*other_count/data_all["SN"].nunique()

# Combine all Data in to Gender Demographics Table
gender_demo = pd.DataFrame(
        {"Gender": ['Male', 'Female', 'Other / Non-Disclosed'],
        "Percentage of Players": [male_perc, female_perc, other_perc],
        "Total Count": [male_count, female_count, other_count]}
        )
# Add Formatting
gender_demo['Percentage of Players'] = gender_demo['Percentage of Players'].map('{:,.2f}%'.format)

gender_demo
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
      <th>Gender</th>
      <th>Percentage of Players</th>
      <th>Total Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Male</td>
      <td>81.37%</td>
      <td>498</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Female</td>
      <td>18.30%</td>
      <td>112</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Other / Non-Disclosed</td>
      <td>1.47%</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



# Purchasing Analysis (Gender)


```python
# PURCHASING ANALYSIS (GENDER)

# Determine Purchase Count by Gender
purc_count_male = data_all.loc[data_all.Gender == 'Male']['SN'].count()
purc_count_female = data_all.loc[data_all.Gender == 'Female']['SN'].count()
purc_count_other = data_all.loc[data_all.Gender == 'Other / Non-Disclosed']['SN'].count()

# Determine Average Purchase Price by Gender
avg_purc_price_male = data_all.loc[data_all.Gender == 'Male']['Price'].mean()
avg_purc_price_female = data_all.loc[data_all.Gender == 'Female']['Price'].mean()
avg_purc_price_other = data_all.loc[data_all.Gender == 'Other / Non-Disclosed']['Price'].mean()

# Determine Total Purchase Value by Gender
tot_purc_val_male = data_all.loc[data_all.Gender == 'Male']['Price'].sum()
tot_purc_val_female = data_all.loc[data_all.Gender == 'Female']['Price'].sum()
tot_purc_val_other = data_all.loc[data_all.Gender == 'Other / Non-Disclosed']['Price'].sum()

# Determine Total Normalized Totals by Gender
norm_tot_male = tot_purc_val_male/purc_count_male
norm_tot_female = tot_purc_val_female/purc_count_female
norm_tot_other = tot_purc_val_other/purc_count_other

# Combine all data into Daraframe
analysis_gender = pd.DataFrame(
                        {"Gender": ['Male', 'Female', 'Other / Non-Disclosed'], 
                         "Purchase Count": [purc_count_male, purc_count_female, purc_count_other],
                         "Purchase Price Average": [avg_purc_price_male, avg_purc_price_female, avg_purc_price_other],
                         "Total Purchase Value": [tot_purc_val_male, tot_purc_val_female, tot_purc_val_other],
                         "Normalized Totals": [norm_tot_male, norm_tot_female, norm_tot_other]}
                        )
# Add Formatting
analysis_gender['Purchase Price Average'] = analysis_gender['Purchase Price Average'].map('${:,.2f}'.format)
analysis_gender['Total Purchase Value'] = analysis_gender['Total Purchase Value'].map('${:,.2f}'.format)
analysis_gender['Normalized Totals'] = analysis_gender['Normalized Totals'].map('${:,.2f}'.format)

analysis_gender
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
      <th>Gender</th>
      <th>Normalized Totals</th>
      <th>Purchase Count</th>
      <th>Purchase Price Average</th>
      <th>Total Purchase Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Male</td>
      <td>$2.94</td>
      <td>697</td>
      <td>$2.94</td>
      <td>$2,052.28</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Female</td>
      <td>$2.85</td>
      <td>149</td>
      <td>$2.85</td>
      <td>$424.29</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Other / Non-Disclosed</td>
      <td>$3.15</td>
      <td>12</td>
      <td>$3.15</td>
      <td>$37.86</td>
    </tr>
  </tbody>
</table>
</div>



# Age Demographics


```python
# AGE DEMOGRAPHICS

# Split into bins of 4 years (i.e. <10, 10-14, 15-19, etc.) 
bins = [0, 10, 15, 20, 25, 30, 35, 40, 100]
age_group = ['<10','10-14','15-19','20-24','25-29','30-34','35-39','40+']

# Add new Age Group Column
pd.cut(data_all["Age"], bins, labels=age_group)
data_all["Age Group"] = pd.cut(data_all["Age"], bins, labels = age_group)

# Create Age Demographics dataframe 
age_demo = data_all.groupby('Age Group', sort=False).sum()  
# Purchase Count
age_demo['Purchase Count'] = data_all.groupby(['Age Group'])['Price'].count()
# Average Purchase Price
age_demo['Average Purchase Price'] = data_all.groupby(['Age Group'])['Price'].mean()
# Total Purchase Value
age_demo['Total Purchase Value'] = data_all.groupby(['Age Group'])['Price'].sum()
# Normalized Totals
age_demo['Normalized Totals'] = age_demo['Total Purchase Value']/ age_demo['Purchase Count']

# Delete Columns
age_demo = age_demo.drop('Item ID', 1)
age_demo = age_demo.drop('Age', 1)
age_demo = age_demo.drop('Price', 1)

# Add Formatting
age_demo['Average Purchase Price'] = age_demo['Average Purchase Price'].map('${:,.2f}'.format)
age_demo['Total Purchase Value'] = age_demo['Total Purchase Value'].map('${:,.2f}'.format)
age_demo['Normalized Totals'] = age_demo['Normalized Totals'].map('${:,.2f}'.format)

age_demo
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
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase Value</th>
      <th>Normalized Totals</th>
    </tr>
    <tr>
      <th>Age Group</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>37</td>
      <td>$2.98</td>
      <td>$110.44</td>
      <td>$2.98</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>82</td>
      <td>$2.88</td>
      <td>$236.36</td>
      <td>$2.88</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>204</td>
      <td>$2.86</td>
      <td>$583.43</td>
      <td>$2.86</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>338</td>
      <td>$2.97</td>
      <td>$1,003.03</td>
      <td>$2.97</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>80</td>
      <td>$2.88</td>
      <td>$230.59</td>
      <td>$2.88</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>65</td>
      <td>$3.00</td>
      <td>$194.73</td>
      <td>$3.00</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>49</td>
      <td>$3.00</td>
      <td>$147.21</td>
      <td>$3.00</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>3</td>
      <td>$2.88</td>
      <td>$8.64</td>
      <td>$2.88</td>
    </tr>
  </tbody>
</table>
</div>



# Top Spenders


```python
# TOP SPENDERS

# Create Top 5 Spenders dataframe 
top_spenders = data_all.groupby('SN', sort=False).sum()  
# Purchase Count
top_spenders['Purchase Count'] = data_all.groupby(['SN'])['Price'].count()
# Average Purchase Price
top_spenders['Average Purchase Price'] = data_all.groupby(['SN'])['Price'].mean()
# Total Purchase Value
top_spenders['Total Purchase Value'] = data_all.groupby(['SN'])['Price'].sum()
# Create New Sort by Total Purchase Value
top_spenders.sort_values(['Total Purchase Value'], ascending=False, inplace=True)

# Delete columns
top_spenders = top_spenders.drop('Item ID', 1)
top_spenders = top_spenders.drop('Age', 1)
top_spenders = top_spenders.drop('Price', 1)

# Add Formatting
top_spenders['Average Purchase Price'] = top_spenders['Average Purchase Price'].map('${:,.2f}'.format)
top_spenders['Total Purchase Value'] = top_spenders['Total Purchase Value'].map('${:,.2f}'.format)

top_spenders.head(5)
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
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>SN</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Undirrala66</th>
      <td>5</td>
      <td>$3.41</td>
      <td>$17.06</td>
    </tr>
    <tr>
      <th>Aerithllora36</th>
      <td>4</td>
      <td>$3.77</td>
      <td>$15.10</td>
    </tr>
    <tr>
      <th>Saedue76</th>
      <td>4</td>
      <td>$3.39</td>
      <td>$13.56</td>
    </tr>
    <tr>
      <th>Sondim43</th>
      <td>4</td>
      <td>$3.25</td>
      <td>$13.02</td>
    </tr>
    <tr>
      <th>Mindimnya67</th>
      <td>4</td>
      <td>$3.18</td>
      <td>$12.74</td>
    </tr>
  </tbody>
</table>
</div>



# Most Popular Items


```python
# MOST POPULAR ITEMS

# Create Top 5 Popular Items by Count dataframe 
popular_item = data_all.groupby('Item Name', sort=False).sum()  
# Purchase Count
popular_item['Purchase Count'] = data_all.groupby(['Item Name'])['Price'].count()
# Total Purchase Value
popular_item['Total Purchase Value'] = data_all.groupby(['Item Name'])['Price'].sum()
# Create New Sort by Count
popular_item.sort_values(['Purchase Count'], ascending=False, inplace=True)

#Delete columns
popular_item = popular_item.drop('Age', 1)

# Add Formatting
popular_item['Price'] = popular_item['Price'].map('${:,.2f}'.format)
popular_item['Total Purchase Value'] = popular_item['Total Purchase Value'].map('${:,.2f}'.format)

popular_item.head(5)
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
      <th>Item ID</th>
      <th>Price</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Final Critic</th>
      <td>1342</td>
      <td>$38.60</td>
      <td>14</td>
      <td>$38.60</td>
    </tr>
    <tr>
      <th>Stormcaller</th>
      <td>1410</td>
      <td>$40.19</td>
      <td>12</td>
      <td>$40.19</td>
    </tr>
    <tr>
      <th>Arcane Gem</th>
      <td>1008</td>
      <td>$29.34</td>
      <td>12</td>
      <td>$29.34</td>
    </tr>
    <tr>
      <th>Betrayal, Whisper of Grieving Widows</th>
      <td>429</td>
      <td>$25.85</td>
      <td>11</td>
      <td>$25.85</td>
    </tr>
    <tr>
      <th>Crucifer</th>
      <td>120</td>
      <td>$25.49</td>
      <td>10</td>
      <td>$25.49</td>
    </tr>
  </tbody>
</table>
</div>



# Most Profitable Items


```python
# MOST PROFITABLE ITEMS

# Create Top 5 Most Profitable Items by dataframe 
profit_item = data_all.groupby('Item Name', sort=False).sum()  
# Purchase Count
profit_item['Purchase Count'] = data_all.groupby(['Item Name'])['Price'].count()
# Total Purchase Value
profit_item['Total Purchase Value'] = data_all.groupby(['Item Name'])['Price'].sum()
# Create New Sort by Count
profit_item.sort_values(['Total Purchase Value'], ascending=False, inplace=True)

#Delete columns
profit_item = profit_item.drop('Age', 1)

# Add Formatting
profit_item['Price'] = profit_item['Price'].map('${:,.2f}'.format)
profit_item['Total Purchase Value'] = profit_item['Total Purchase Value'].map('${:,.2f}'.format)

profit_item.head(5)
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
      <th>Item ID</th>
      <th>Price</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Stormcaller</th>
      <td>1410</td>
      <td>$40.19</td>
      <td>12</td>
      <td>$40.19</td>
    </tr>
    <tr>
      <th>Final Critic</th>
      <td>1342</td>
      <td>$38.60</td>
      <td>14</td>
      <td>$38.60</td>
    </tr>
    <tr>
      <th>Retribution Axe</th>
      <td>306</td>
      <td>$37.26</td>
      <td>9</td>
      <td>$37.26</td>
    </tr>
    <tr>
      <th>Splitter, Foe Of Subtlety</th>
      <td>963</td>
      <td>$33.03</td>
      <td>9</td>
      <td>$33.03</td>
    </tr>
    <tr>
      <th>Spectral Diamond Doomblade</th>
      <td>805</td>
      <td>$29.75</td>
      <td>7</td>
      <td>$29.75</td>
    </tr>
  </tbody>
</table>
</div>


