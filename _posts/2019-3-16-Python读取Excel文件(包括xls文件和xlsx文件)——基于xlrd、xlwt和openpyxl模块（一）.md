## Python读取Excel文件(包括xls文件和xlsx文件)——基于xlrd、xlwt和openpyxl模块（一）

### 一.使用xlrd模块对xls文件进行读操作
1.导入模块，获取工作簿对象
```python 
# 导入模块
import xlrd
# 获取excel工作簿对象
workbook = xlrd.open_workbook('file_name')  # file_name为excel表路劲
```
2.获取工作表(sheet)对象
```python 
# 获取所有的sheet
names = workbook.sheet_names()
# 通过工作表的索引获取sheet对象
worksheet = workbook.sheet_by_index('index')
# 通过工作表名字获取sheet对象
worksheet = workbook.sheet_by_name('sheet_name')
```
3.对sheet的操作
```python 
# 获取当前sheet的名字
name = worksheet.sheet_name()
# 获取该表总行数
nrows = worksheet.nrows  
# 获取该表总列数
ncols = worksheet.ncols  
# 获取行内容，行号为int
row_text = worksheet.row_values('行号')
# 获取列内容，列号为int
col_text = worksheet.col_values('列号')
# 获取单元格的数据
cell_value1 = worksheet.cell_value(0,0)
cell_value1=worksheet.cell(0,0).value
cell_value1=worksheet.row(0)[0].value
```
用例(以字典形式输出)：
```python 
def xl2json(file):
    workbook = xlrd.open_workbook(file)
    names = workbook.sheet_names()
    data_list = []
    for i in range(len(names)-1):
        data = {}
        name = names[i]
        data["sheet_name"] = name
        data["d"] = []
        worksheet = workbook.sheet_by_name(names[i])
        nrows = worksheet.nrows
        for j in range(2, nrows):
            d1 = worksheet.row_values(1)
            d = worksheet.row_values(j)
            a = {}
            for k in range(2, len(d)):
                a[d1[k]] = d[k]
            data["d"].append(a)
        data_list.append(data)
    return data_list
```
