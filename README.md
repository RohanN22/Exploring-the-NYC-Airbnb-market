# Exploring-the-NYC-Airbnb-market  
code import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
file_path = r"C:\Users\rohan\OneDrive\Desktop\excel files\AB_NYC_2019.csv"
df = pd.read_csv(file_path)

# Display basic information about the dataset
print(df.info())
print(df.head())

# Clean the dataset
df.dropna(subset=['name', 'host_name'], inplace=True)

# Analyze the data
neighbourhood_group_counts = df['neighbourhood_group'].value_counts()
print(neighbourhood_group_counts)

# Visualize the data
plt.figure(figsize=(10, 6))
sns.countplot(x='neighbourhood_group', data=df)
plt.title('Number of Listings by Neighbourhood Group')
plt.xlabel('Neighbourhood Group')
plt.ylabel('Number of Listings')
plt.show()

# Price distribution
plt.figure(figsize=(10, 6))
sns.histplot(df['price'], bins=50, kde=True)
plt.title('Price Distribution')
plt.xlabel('Price')
plt.ylabel('Frequency')
plt.show()

# Average price by neighbourhood group
avg_price_neighbourhood_group = df.groupby('neighbourhood_group')['price'].mean()
print(avg_price_neighbourhood_group)

# Visualize the average price
plt.figure(figsize=(10, 6))
avg_price_neighbourhood_group.plot(kind='bar')
plt.title('Average Price by Neighbourhood Group')
plt.xlabel('Neighbourhood Group')
plt.ylabel('Average Price')
plt.show()
