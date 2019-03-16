## Python读取Excel文件(包括xls文件和xlsx文件)——基于xlrd、xlwt和openpyxl模块（二）

### 二.使用openpyxl模块对xlsx文件进行读操作
1.导入模快，获取工作簿对象
```python
import openpyxl
# 获取工作簿对象
workbook = openpyxl.load_workbook("file_name")
```
2.获取工作表(sheet)对象
```python
# 获取工作簿 workbook的所有工作表
shenames = workbook.get_sheet_names()
# 获取工作表对象
worksheet = workbook["sheet_name"]
# 通过索引获取表对象
worksheet = workbook.worksheets[0]
```
3.对工作表操作
```python
# 获取当前工作表名
name = worksheet.title 
#获取该表相应的行数和列数
rows = worksheet.max_row
columns = worksheet.max_column
# 按行获取内容
for row in worksheet.rows:
    for cell in row:
        print(cell.value,end=" ")
    print()
# 按列获取内容
for col in worksheet.columns:
    for cell in col:
        print(cell.value,end=" ")
    print()
# 输出特定的行
for cell in list(worksheet.rows)[3]:  #获取第四行的数据
    print(cell.value,end=" ")
print()
# 输出特定的列
for cell in list(worksheet.columns)[2]:  
    print(cell.value,end=" ")
print()
```
用例：
```python 
pass
```
