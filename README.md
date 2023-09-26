import pandas as pd
import matplotlib.pyplot as plt

# Sample data (you should replace this with your own dataset)
data = {
    'Product': ['Laptop', 'Phone', 'Tablet', 'Headphones', 'TV'],
    'Category': ['Electronics', 'Electronics', 'Electronics', 'Accessories', 'Electronics'],
    'Price (INR)': [45000, 25000, 12000, 1500, 55000],
    'Discount (%)': [10, 15, 5, 20, 12],
    'Units Sold': [100, 200, 150, 300, 50]
}

# Create a DataFrame from the sample data
df = pd.DataFrame(data)

# Calculate total sales for each product
df['Total Sales (INR)'] = df['Price (INR)'] * df['Units Sold']

# Calculate discounted price
df['Discounted Price (INR)'] = df['Price (INR)'] - (df['Price (INR)'] * df['Discount (%)'] / 100)

# Calculate total discounted sales for each product
df['Total Discounted Sales (INR)'] = df['Discounted Price (INR)'] * df['Units Sold']

# Visualize total sales by product
plt.figure(figsize=(10, 6))
plt.bar(df['Product'], df['Total Sales (INR)'])
plt.title('Total Sales by Product')
plt.xlabel('Product')
plt.ylabel('Total Sales (INR)')
plt.xticks(rotation=45)
plt.show()

# Visualize total discounted sales by product
plt.figure(figsize=(10, 6))
plt.bar(df['Product'], df['Total Discounted Sales (INR)'])
plt.title('Total Discounted Sales by Product')
plt.xlabel('Product')
plt.ylabel('Total Discounted Sales (INR)')
plt.xticks(rotation=45)
plt.show()

# Calculate and display summary statistics
summary_stats = df.describe()

# Print the summary statistics
print(summary_stats)

# Group products by category and calculate total sales
category_sales = df.groupby('Category')['Total Sales (INR)'].sum()

# Visualize total sales by category
plt.figure(figsize=(8, 5))
category_sales.plot(kind='bar')
plt.title('Total Sales by Category')
plt.xlabel('Category')
plt.ylabel('Total Sales (INR)')
plt.xticks(rotation=45)
plt.show()

# Calculate average price by category
average_price = df.groupby('Category')['Price (INR)'].mean()

# Visualize average price by category
plt.figure(figsize=(8, 5))
average_price.plot(kind='bar')
plt.title('Average Price by Category')
plt.xlabel('Category')
plt.ylabel('Average Price (INR)')
plt.xticks(rotation=45)
plt.show()
