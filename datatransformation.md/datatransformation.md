# Perform the JOIN and aggregation
merged_data = customer_data.merge(orders_data, on='customer_id', how='left')

summary_data = merged_data.groupby(['customer_id', 'customer_name']).agg(
    order_count=pd.NamedAgg(column='order_id', aggfunc='count'),
    total_spent=pd.NamedAgg(column='order_amount', aggfunc='sum')
).reset_index()

customer_orders_view = merged_data[['customer_id', 'customer_name', 'order_id', 'order_amount', 'order_date']]
