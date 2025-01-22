# Basic-Data-Visualisation-with-Python  
This project focuses on basic data visualization with Python. The project focuses on a Cafe Sales dataset that I cleaned in the [Data Cleaning Project here](https://github.com/joshua024-geek/Data-Cleaning-with-Python).  
The visualization focused on the Total Sales per Item/Product, Total Sales Per Month, and the Total Quantity of Items sold per Item. <br /><br />
### Total Sales per Item
```
#Plot Sales Revenue Per Item
plt.figure(figsize=(8, 6))
sales_per_item = df.groupby('Item')['Total Spent'].sum()
ax = sales_per_item.plot(kind='bar', color ='skyblue')
plt.title('Sales Per Item')
plt.xlabel('Item')
plt.ylabel('Sales Revenue')
plt.xticks(rotation=60)
plt.tight_layout()

# Show values on top of bars
for p in ax.patches:
   ax.annotate(f'{p.get_height():.2f}', 
                (p.get_x() + p.get_width() / 2., p.get_height()), 
                xytext=(0, 5),  # 5 points vertical offset
                textcoords='offset points',
                ha='center', va='bottom')
plt.show()
````
![Sales Revenue per Item](https://github.com/joshua024-geek/Basic-Data-Visualisation-with-Python/blob/main/v%20-%20sales%20per%20item.PNG)

### Total Quantity of Items sold per Item
```
#Items By Quantity Sold

plt.figure(figsize=(8, 6))
quantity_per_item = df.groupby('Item')['Quantity'].sum()
ax = quantity_per_item.plot(kind='bar', color ='purple')
plt.title('Quantity Sold Per Item')
plt.xlabel('Item')
plt.ylabel('Sales Quantity')
plt.xticks(rotation=60)
plt.tight_layout()

# Show values on top of bars
for p in ax.patches:
   ax.annotate(f'{p.get_height():.2f}', 
                (p.get_x() + p.get_width() / 2., p.get_height()), 
                xytext=(0, 5),  # 5 points vertical offset
                textcoords='offset points',
                ha='center', va='bottom')
plt.show()

```
![ Total Quantity of Items sold per Item](https://github.com/joshua024-geek/Basic-Data-Visualisation-with-Python/blob/main/v%20-%20quantity%20sold%20per%20item.PNG)

### Total Sales - Monthly Trends

```
#Plot Monthly Sales in Line Chart

# Extract Year-Month from the Transaction Date
df['Month-Year'] = df['Transaction Date'].dt.to_period('M')
# Group by 'Month-Year' and sum the 'Total Spent'
monthly_sales = df.groupby('Month-Year')['Total Spent'].sum().reset_index()
# Convert 'Month-Year' back to string format for easier plotting
monthly_sales['Month-Year'] = monthly_sales['Month-Year'].astype(str)

# Plot the line chart
plt.figure(figsize=(8, 6))
plt.plot(monthly_sales['Month-Year'], monthly_sales['Total Spent'], marker='o', linestyle='-', color='b')

# Adding labels and title
plt.xlabel('Month-Year')
plt.ylabel('Total Sales (Total Spent)')
plt.title('Total Sales Per Month')
plt.xticks(rotation=45, ha='right')
plt.grid(True)
plt.tight_layout()

# Show the plot
plt.show()
```
![Monthly Sales Trends](https://github.com/joshua024-geek/Basic-Data-Visualisation-with-Python/blob/main/v%20-%20sales%20per%20month.PNG)   

#### NB: View the Jupyter Notebook file for the entire visualization code. 
