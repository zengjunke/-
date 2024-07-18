import pandas as pd
import math
import xlwings as xw

r = 12.5  #风机基础圆半径
file_path = r'C:\...\file_name.xlsx'  #风机点位坐标文件路径
wb =xw.Book(file_path)
new_sheet = wb.sheets.add('风机八角坐标')

points = pd.read_excel(file_path)
print(points)
points_number = len(points)
print(points_number)

for i in range(points_number):
    point_name = points.iloc[i, 0]
    x0 = float(points.iloc[i, 1])
    y0 = float(points.iloc[i, 2])

    r0 = r/math.cos(math.pi/8)
    r1 = r0*math.cos(math.pi/4)
    d = r*math.tan(math.pi/8)
        
    p1 = (x0, y0+r0)
    p2 = (x0+r1, y0+r1)
    p3 = (x0+r0, y0)
    p4 = (x0+r1, y0-r1)
    p5 = (x0, y0-r0)
    p6 = (x0-r1, y0-r1)
    p7 = (x0-r0, y0)
    p8 = (x0-r1, y0+r1)
    pnts = [p1, p2, p3, p4, p5, p6, p7, p8, p1]
    
    q1 = (x0+d, y0+r)
    q2 = (x0+r, y0+d)
    q3 = (x0+r, y0-d)
    q4 = (x0+d, y0-r)
    q5 = (x0-d, y0-r)
    q6 = (x0-r, y0-d)
    q7 = (x0-r, y0+d)
    q8 = (x0-d, y0+r)
    qnts = [q1, q2, q3, q4, q5, q6, q7, q8, q1]

    new_sheet[i*10, 0].value = point_name

    for j in range(9):

        new_sheet[i*10+j+1, 0].value = qnts[j][0]
        new_sheet[i*10+j+1, 1].value = qnts[j][1]

wb.save()
