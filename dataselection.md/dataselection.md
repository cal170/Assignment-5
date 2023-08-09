import pandas as pd

# Load customer data from an Excel file
customer_data = pd.read_excel("superstore1.xlsx", sheet_name="customer_sheet")

# Load orders data from an Excel file
orders_data = pd.read_excel("superstore2.xlsx", sheet_name="orders_sheet")

# Perform the rest of the steps (Data Transformation, Loading, and View creation)
merged_data = customer_data.merge(orders_data, on='customer_id', how='left')

summary_data = merged_data.groupby(['customer_id', 'customer_name']).agg(
    order_count=pd.NamedAgg(column='order_id', aggfunc='count'),
    total_spent=pd.NamedAgg(column='order_amount', aggfunc='sum')
).reset_index()

customer_orders_view = merged_data[['customer_id', 'customer_name', 'order_id', 'order_amount', 'order_date']]

# Print the summary_data and customer_orders_view if needed
print(summary_data)
print(customer_orders_view)
