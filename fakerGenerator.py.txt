from datetime import date,datetime,timedelta
from faker import Faker
import random
import xlsxwriter
fake=Faker()

invoiceNumber=10000
rowindex=2

workbook=xlsxwriter.Workbook("./FakeData.xlsx")
worksheet=workbook.add_worksheet("Fake_data_experiment")
worksheet.write("A1","Name")
worksheet.write("B1","Invoice Number")
worksheet.write("C1","PO Number")
worksheet.write("D1","Invoice Date")
worksheet.write("E1", "Net Due date")
worksheet.write("F1","Open Amount")
worksheet.write("G1","Currency")
worksheet.write("H1","Preferred Language")
worksheet.write("I1","Customer Region")	

for x in range(1,100):
    name=fake.name()
    invoiceNumber=invoiceNumber+1
    productOrder=random.randint(100,1000)+random.randint(10000,100000)
    InvoiceDate=fake.date_between_dates("-1y","now")
    Net_due_date=(datetime.combine(InvoiceDate, datetime.min.time())+timedelta(days=30+random.randint(1,30))).date()
    Open_amount=fake.random_int()*10
    Currency=fake.currency()
    Preferred_language=fake.language_name()
    Customer_region=fake.country()
    worksheet.write("A"+str(rowindex),name)
    worksheet.write("B"+str(rowindex),invoiceNumber)
    worksheet.write("C"+str(rowindex),productOrder)
    worksheet.write("D"+str(rowindex),str(InvoiceDate))
    worksheet.write("E"+str(rowindex),str(Net_due_date))
    worksheet.write("F"+str(rowindex),Open_amount)
    worksheet.write("G"+str(rowindex),str(Currency))
    worksheet.write("H"+str(rowindex), Preferred_language)
    worksheet.write("I"+str(rowindex),Customer_region)
    rowindex += 1

    print(name, invoiceNumber, productOrder, InvoiceDate, Net_due_date, Open_amount, Currency, Preferred_language, Customer_region)
	
	workbook.close()
	
	Net_due_date=(datetime.combine(InvoiceDate, datetime.min.time())+timedelta(days=random.randint(1,30))).date()
print(Net_due_date)

InvoiceDate=fake.date_between_dates(datetime.now().date().replace(month=1, day=1),"now")
print(InvoiceDate)

print(datetime.now().date().replace(month=1, day=1))