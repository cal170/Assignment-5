import pandas as pd

# Load customer data from an Excel file
customer_data = pd.read_excel("superstore1.xlsx", sheet_name="customer_sheet")

# Load orders data from an Excel file
orders_data = pd.read_excel("superstore2.xlsx", sheet_name="orders_sheet")
