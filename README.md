import tabula
import pandas as pd
import jpype



excel_path = r'SUVENPHARMROHIT_22112023182445_SUVENPHARMBRSRReport2023.csv'
pdf_path = r"TATACOFFEE2_27112023204410_Business_Responsibility_and_Sustainability_Report.pdf"

column_names_df = pd.read_csv(excel_path)
column_names = column_names_df.columns.tolist()

tables = tabula.read_pdf(pdf_path, pages='all', multiple_tables=True)
df = tables[0]

# Ensure the dataframe has the same number of columns as the Excel (adjust as necessary)
df.columns = column_names[:len(df.columns)]

# Path to save the new Excel file
output_path = r'C:\Users\Dhruv Mahabal\Downloads\extracted_data.csv'

# Save to Excel
df.to_csv(output_path, index=False)
