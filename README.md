说明：
pandas：用于数据处理和读取Excel文件。
math：用于数学运算。
xlwings：用于操作Excel文件。
定义常量：

r：风机基础圆的半径，值为12.5。
定义文件路径：

file_path：存储风机点位坐标的Excel文件的路径。
打开Excel文件：

使用xlwings.Book()打开指定路径的Excel文件，并创建一个新的工作表命名为“风机八角坐标”。
读取Excel数据：

使用pd.read_excel(file_path)读取Excel文件中的数据，存储在变量points中。
打印数据和数据条数：

打印读取的数据和数据的条数（即风机点位的数量）。
循环处理每个风机点位：

通过for i in range(points_number)循环，处理每个风机点位。
提取风机点位信息：

point_name：提取风机点位的名称。
x0和y0：提取风机点位的原始坐标。
计算八角坐标：

使用数学公式计算出风机点位的八角坐标。这里涉及到一些几何计算：
r0：计算一个辅助半径。
r1：计算另一个辅助半径。
d：计算一个辅助距离。
计算八个点的坐标（p1到p8），形成一个八角形。
计算外接圆的八个点的坐标（q1到q8）。
将风机点位名称写入新工作表：

new_sheet[i*10, 0].value = point_name：将风机点位名称写入新工作表的对应行。
将八角坐标写入新工作表：

通过循环for j in range(9)，将外接圆的八个点的坐标写入新工作表的对应行和列。
保存Excel文件：

wb.save()：保存修改后的Excel文件。