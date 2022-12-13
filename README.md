# Streamlit_download_excel

#Sample of how make download button for csv or xlsx file

```
def to_excel(df):
    output = BytesIO()
    writer = pd.ExcelWriter(output, engine='xlsxwriter')
    df.to_excel(writer, index=False, sheet_name='Sheet1')
    workbook = writer.book
    worksheet = writer.sheets['Sheet1']
    format1 = workbook.add_format({'num_format': '0.00'})
    worksheet.set_column('A:A', None, format1)
    writer.save()
    processed_data = output.getvalue()
    return processed_data


df_xlsx = to_excel(df_upload)
st.download_button(label='📥 Download Current Result',
                   data=df_xlsx,
                   file_name='df_result.xlsx')
```
