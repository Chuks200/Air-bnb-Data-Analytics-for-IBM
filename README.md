# Air-bnb Data Analysis using Python

## Table of Content

  - [Project Overview](#project-overview)
  - [Data Source](#data-source)
  - [Tool used](#tool-used)
  - [Results and Findings](#results-and-findings)
  - [Recommendation](#recommendation)
  - [Reference](#reference)
  - [Python codes worked with](#python-codes-worked-with)

### Project Overview
People's main criteria when visiting new places are reasonable accommodation and food. Airbnb (Air-Bed-Breakfast) is an online
marketplace created to meet this need of people by renting out their homes for a short term. They offer this facility at a relatively lower
price than hotels. Further people worldwide prefer the homely and economical service offered by them. They offer services across
various geographical locations

### Data Source
The dataset for this project is gotten using  using the following link: https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata
This dataset contains information such as the neighborhood offering these services, room type, price,avaliabilty, reviews, service fee,
cancellation policy and rules to use the house. This analysis will help airbnb in improving its services.
### Tool used
- Python: It was used for Data Cleaning, Data Transformation, Data Visualization.
### Task 1: Data Loading (Python)
- Read the csv file and load it into a pandas dataframe.
- Display the first five rows of your dataframe.
- Display the data types of the columns.
### Task 2a: Data Cleaning with python
- Drop some of the unwanted columns. These include host id , id , country and country code from the dataset.
- State the reason for not including these columns for your Data Analytics.
### Task 2b: Data Cleaning (Python)
- Check for missing values in the dataframe and display the count in ascending order. If the values are missing, impute the values
as per the datatype of the columns.
- Check whether there are any duplicate values in the dataframe and, if present, remove them.
- Display the total number of records in the dataframe before and after removing the duplicates.
### Task 3: Data Transformation (Python)
- Rename the column availability 365 to days_booked
- Convert all column names to lowercase and replace the spaces in the column names with an underscore "_".
- Remove the dollar sign and comma from the columns price and service_fee . If necessary, convert these two columns to the
appropriate data type.
### Task 4: Exploratory Data Analysis (Python)
- List the count of various room types avaliable in the dataset.
- Which room type has the most strict cancellation policy?
- List the average price per neighborhood group, and highlight the most expensive neighborhood to rent from.
### Task 5a: Data Visualization (Python)
- List the count of various room types avaliable with Airnb
- Which room type adheres to more strict cancellation policy
- List the prices by neighborhood group and also mention which is the most expensive neighborhood group for rentals
- List the top 10 neighborhoods in the increasing order of their price with the help of a horizontal bar graph. Which is the cheapest
neighborhood.
- List the neighborhoods which offer short term rentals within 10 days. Illustrate with a bar graph
- List the prices with respect to room type using a bar graph and also state your inferences.
- Create a pie chart that shows distribution of booked days for each neighborhood group .Which neighborhood has the highest
booking percentage
### Task 5b: Data Visualization (Python)
- Does service price and room price have an impact on each other. Illustrate this relationship with a scatter plot and state your
inferences
- Using a line graph show in which year the maximum construction of rooms took place.

### Task 5c: Data Visualization (Python)
 -With the help of box plots illustrate the following
- Effect of Review Rate number on price
- Effect of host identity verified on price
### Results and Findings.
##### Counts of Air bnb room types
<img width="519" alt="ibm 5av" src="https://github.com/Chuks200/Air-bnb-Data-Analytics-for-IBM/assets/150162291/45551da3-8dc4-4a75-9b7e-6420e9fc972b">

  ##### Reasons for not including host id , id , country and country code columns for my Data Analytics.?
- Host ID and ID: These columns most likely contain the host's and
  the listing's individual IDs. These kinds of unique IDs are typically
  abandoned in data analytics because they don't offer useful
  information for analysis. A distinct 'id' for each row is there, but it
  has no bearing on patterns or trends. Likewise, 'host id' is unique
  to a single host and does not contribute to a more comprehensive
  study.
- Country and Country Code: These columns become unnecessary
  if the dataset is restricted to a single nation or if all of the data
  originates there. The 'country' and 'country code' columns can be
  safely removed in this instance, as they neither vary nor offer new
  information for analysis within a single-country context.
##### Inferences from task 5a, The following conclusions are suggested by the bar graph created using the Airbnb dataset:
<img width="564" alt="ibm 5a" src="https://github.com/Chuks200/Air-bnb-Data-Analytics-for-IBM/assets/150162291/2cadd929-fb8e-4668-84d0-41f4bab350ca">

- The average price of 'hotel rooms' is the highest, which makes sense given that these types of lodging frequently come with extra features and services. According to the data, 'shared rooms' have the
  second-highest average cost. This is uncommon because, because of their shared area and decreased privacy, shared rooms are usually the least costly.
  The third-highest average price is shown for 'entire homes and apartments'. This is a little surprising, as shared areas typically attract lower costs than full homes or apartments because of the
  solitude and space they provide.
  The average price of 'private rooms' is the lowest, which is consistent with the widely held belief that they are more costly than shared rooms but less expensive than a full house')
##### Inferences from task 5b:'
<img width="530" alt="ibm 5c" src="https://github.com/Chuks200/Air-bnb-Data-Analytics-for-IBM/assets/150162291/d9d1df56-455b-466c-838c-e918c6f62fa5">

- It is nevertheless evident that the two variables have a positive association. The price of the accommodation tends to rise in tandem with the service charge, meaning that rooms that are more expensive typically have larger service costs. This lends more credence to the theory that service costs represent a portion of the room charge, which is a standard pricing tactic in the hospitality sector' )
  

### Recommendation 

### Reference
[kaggle](https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata)


  
  ### Python codes worked with
  ``` python jupyter notebook
  ### Task 1
  import necessary libraries
  import pandas as pd
  import seaborn as sns
  import numpy as np
  import matplotlib.pyplot as plt
  from sklearn.cluster import KMeans
  Read the csv file
  df = pd.read_csv ("C:/Users/agbat/OneDrive/Mystry project DA202.2/IBM AIR BNB PROJECT/archive/Airbnb_Open_Data.csv"
  Display the first 5 rows
  df.head()

  
  .Task 2
  df.drop (columns= ["host id", "id", "country", "country code"] , inplace= True )
  (df.head())
  Task 2b: Data cleaning
  #check for missing values in the data frame and display the count in ascending order
  missing_values = df.isnull().sum()
  missing_values_sorted = missing_values.sort_values()
  print("Missing values count in each column (ascending order):")
  print(missing_values_sorted)
  #Impute missing values
  for column in df.columns:
  if df[column].dtype == 'float64' or df[column].dtype == 'int64':
  For numerical columns, replace missing values with the mean
  df[column].fillna(df[column].mean(), inplace=True)
  else:
  #For non-numerical columns, replace missing values with the mode (most frequent value)
  df[column].fillna(df[column].mode()[0], inplace=True)
  Display the dataframe after imputation
  print("Dataframe after imputation:")
  (df.head())
  #Check for duplicate rows
  duplicate_rows = df[df.duplicated()]
  print("Number of duplicate rows: ", duplicate_rows.shape[0])
  Remove duplicate rows
  df = df.drop_duplicates()
  #Verify that duplicates are removed
  print("Number of duplicate rows after removal: ", df[df.duplicated()].shape[0])
  Display the total number of records in the dataframe after removing the duplicates.
  print("Total number of records after removing duplicates: ", df.shape[0])


  .Task 3: Data Transformation
  #Rename the column availability 365 to days_booked.
  #Renaming the column
  df.rename(columns={'availability 365': 'days_booked'}, inplace=True)
  Display the DataFrame
  (df.head())
  Convert all column names to lowercase and replace the spaces with an underscore "_"
  df.columns = [col.lower().replace(' ', '_') for col in df.columns]
  Display the DataFrame to verify changes
  (df.head())
  #Remove the dollar sign and comma from the columns. If necessary, convert these two columns to the appropriate
  datadf['service_fee'] = df['service_fee'].str.replace('$', '').str.replace(',', '').astype(float)
  df['price'] = df['price'].str.replace('$', '').str.replace(',', '').astype(float)
  #Display the first few rows of the DataFrame
  df.head()


  .Task 4: Exploratory Data Analysis
  #List the count of various room types avaliable in the dataset.
  Group by the 'room_type' column and count the occurrence
  room_type_counts = df['room_type'].value_counts()
  Display the counts of each room type
  print(room_type_counts)
  #Which room type adheres to more strict cancellation policy
  #Filter the data to include only rows with a strict cancellation policy
  strict_policy_df = df[df['cancellation_policy'] == 'strict']
  Group by room type and count the occurrences
  strict_policy_count = strict_policy_df.groupby('room_type').size()
  Display the results
  print(strict_policy_count)
  print ('most strict cancellation policy room type is:', 'Entire home/apt with 17239')
  #List the prices by neighborhood group and also mention which is the most expensive neighborhood group for rentals# Group by neighborhood group and calculate average price
  average_prices = df.groupby('neighbourhood_group')['price'].mean()
  Display the average prices by neighborhood group
  print("Average Prices by Neighborhood Group:")
  print(average_prices)
  Sort the average prices in descending order
  sorted_average_prices = average_prices.sort_values(ascending=False)
  Display the sorted average prices by neighborhood group
  print("Average Prices by Neighborhood Group (Descending):")
  print(sorted_average_prices)
  #The most expensive neighborhood group is now the first one in the sorted list
  most_expensive = sorted_average_prices.index[0]
  print ('The most expensive neighborhood to rent:', 'Queens at an average of $628.668822')


  .Task 5a: Data Visualization
  #List the count of various room types avaliable with Airnb
  #Count the number of listings for each room type
  room_type_counts = df['room_type'].value_counts()
  Print the counts
  print(room_type_counts)
  #Visualization
  plt.figure(figsize=(10, 6))
  sns.barplot(x=room_type_counts.index, y=room_type_counts.values)
  plt.title('Count of Airbnb Room Types')
  plt.xlabel('Room Type')
  plt.ylabel('Number of Listings')
  plt.show()
  #Which room type adheres to more strict cancellation policy
  Filter the data to include only rows with a strict cancellation policy
  strict_policy_df = df[df['cancellation_policy'] == 'strict']
  Group by room type and count the occurrences
  strict_policy_count = strict_policy_df.groupby('room_type').size()
  Display the results
  print(strict_policy_count)
  #Visualization
  plt.figure(figsize=(10, 6))
  sns.barplot(x=strict_policy_count.index, y=strict_policy_count.values)
  plt.title('strict_cancellation_policy_count')
  plt.xlabel('Room Type')
  plt.ylabel('Number of Listings')
  plt.show()
  #List the prices by neighborhood group and also mention which is the most expensive neighborhood group for rentals
  grouped_prices = df.groupby('neighbourhood_group')['price'].mean()
  Identify the most expensive neighborhood group
  most_expensive = grouped_prices.idxmax()
  Print the most expensive neighborhood group and its average pric
  print(f"The most expensive neighbourhood group is {most_expensive} with an average price of {grouped_prices[most_expe# Visualization
  plt.figure(figsize=(10, 6))
  sns.barplot(x=grouped_prices.index, y=grouped_prices.values)
  plt.title('Average Price by Neighbourhood Group')
  plt.xlabel('Neighborhood Group')
  plt.ylabel('Average Price')
  plt.xticks(rotation=45)
  plt.show()
  #List the top 10 neighborhoods in the increasing order of their price with the help of a horizontal bar graph. Which# Aggregate and sort data
  neighbourhood_prices = df.groupby('neighbourhood')['price'].mean().sort_values()
  top_10_neighborhoods = neighbourhood_prices.head(10)
  # Plotting
  plt.figure(figsize=(10, 6))
  top_10_neighborhoods.plot(kind='barh')
  plt.xlabel('Average Price')
  plt.ylabel('Neighborhood')
  plt.title('Top 10 Cheapest Neighborhoods by Average Price')
  plt.show()
  print ('Cheapest Neigbourhood:', 'Lighthouse Hill')
  #List the neighborhoods which offer short term rentals within 10 days. Illustrate with a bar graph
  Filter the dataset for listings that require 10 or fewer nights
  short_term_rentals = df[df['minimum_nights'] <= 10]
  Count the number of listings in each neighborhood
  neighbourhood_counts = short_term_rentals['neighbourhood_group'].value_counts()
  Create a bar graph
  plt.figure(figsize=(12, 6))
  neighbourhood_counts.plot(kind='bar')
  plt.title('Short Term Rentals (10 Nights or Less) by Neighbourhood')
  plt.xlabel('Neighbourhood_group')
  plt.ylabel('Number of Listings')
  plt.show()
  #List the prices with respect to room type using a bar graph and also state your inferences
  Group by room type and calculate average price
  room_prices = df.groupby('room_type')['price'].mean()
  Plotting
  plt.figure(figsize=(10,6))
  room_prices.plot(kind='bar')
  plt.title('Average Prices by Room Type')
  plt.xlabel('Room Type')
  plt.ylabel('Average Price')
  plt.xticks(rotation=45)
  plt.show()
  #Create a pie chart that shows distribution of booked days for each neighborhood group .Which neighborhood has the h# Group and Aggregate Data
  grouped_data = df.groupby('neighbourhood_group')['minimum_nights'].sum()
  Calculate Percentages
  total_booked_days = grouped_data.sum()
  percentages = grouped_data / total_booked_days * 100
  Create the Pie Chart
  plt.figure(figsize=(10, 6))
  plt.pie(percentages, labels=percentages.index, autopct='%1.1f%%')
  plt.title('Distribution of Booked Days by Neighbourhood Group')
  Show the plot
  plt.show()
  Identify Highest Booking Percentage
  highest_booking = percentages.idxmax()
  print(f"The neighbourhood with the highest booking percentage is {highest_booking}")

  .Task 5b: Data Visualization
  Does service price and room price have an impact on each other. Illustrate this relationship with a scatter plot and# Scatter plot
  plt.figure(figsize=(10, 6))
  sns.scatterplot(x='service_fee', y='price', data=df)
  Adding titles and labels
  plt.title('Relationship between Service Price and Room Price')
  plt.xlabel('Service Price')
  plt.ylabel('Room Price')
  Show plot
  plt.show()
  print ('Inferences :', 'It is nevertheless evident that the two variables have a positive association. The price
  #Using a line graph show in which year the maximum construction of rooms took place.
  # Aggregate data
  yearly_data = df.groupby('construction_year')['room_type'].count()
  # Plotting
  plt.figure(figsize=(10, 6))
  yearly_data.plot(kind='line')
  plt.title('Yearly Room Construction')
  plt.xlabel('Construction Year')
  plt.ylabel('Number of Rooms Constructed')
  plt.grid(True)
  plt.show()
  # Identifying the year with maximum construction
  max_year = yearly_data.idxmax()
  print(f"The year with maximum room construction is: {max_year}")


  .Task 5c: Data Visualization
  #Effect of Review Rate number on price
  plt.figure(figsize=(12, 6))
  sns.boxplot(x='review_rate_number', y='price', data=df)
  plt.title('Effect of Review Rate on Price')
  plt.xlabel('Review Rate')
  plt.ylabel('Price')
  plt.show()
  #Effect of host identity verified on price
  plt.figure(figsize=(12, 6))
  sns.boxplot(x='host_identity_verified', y='price', data=df)
  plt.title('Effect of Review Rate on Price')
  plt.xlabel('Review Rate')
  plt.ylabel('Price')
  plt.show()
```
   
