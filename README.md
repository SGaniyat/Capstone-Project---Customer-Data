# Capstone-Project---Customer-Data
This project involves analyzing customer data for a subscription service to identify segments and trends. The goal is to understand customer behavior, track subscription types, and identify key trends in cancellations and renewals. The final deliverable is a Power BI dashboard that presents the analysis.


### Data Analysis tools Used
- Microsoft Excel
- SQL
- Power BI

## Using Microsoft Excel as a Data Analysis tool
Steps
<h3>1. Data cleaning </h3><br/>
    <ol type="i"> 
     <li>The Data was cleaned by delecting all duplicate of records. This was accheived by selecting the sheet and click Data-Data Tool- Remove Duplicate. 40,079 duplicate value was found and removed. Ehile 9921 Unique values remains. </li>
     <li> Create Revenue column by Multiplying Quantity by Unit price</li>
    </ol>

 <h3>2. Use Excel formulas to calculate metrics such as average sales per product and
total revenue by region.</h3><br/>

=AVERAGEIF(range,criteria[average_range])</h3><br/>
 =sUMIF((range,criteria[sum_range])</h3><br/>
 =Sum(Number 1,(Number......)








     
### Using SQL as a Data Analysis tool.
Steps
<ol type="i">
<li> Cleaning data in excel and save file in CSV.</li>
<li> Create Database on Management Studio </li>
    <strong>Create Capstoneproject table</strong>
<li> Import your file by Right click on your Database created and select task and click Import Flat file. follow the prompt accordingly to import your file.</li>
</ol>

1.Customer Data table
```SQL
 select*from [dbo].[LITA_CApstones Customerdata].
 ```
![Customer Data table](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/2bab10a2b8ccb952bdb7d700529550198da4b0b3/Customer%20table.png)

2.Retrieve the total number of customers from each region
```SQL
 Select Region, Sum(customerID) as TotalCustomer_Region from [dbo].[LITA_CApstones Customerdata]
Group by Region 
 ```
![Retrieve the total number of customers from each region](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/2bab10a2b8ccb952bdb7d700529550198da4b0b3/CustomerID%20by%20Region.png)

3.find the most popular subscription type by the number of customers
```SQL
Select SubscriptionType, Sum(customerID) as HighestSubcription_Region from [dbo].[LITA_CApstones Customerdata]
Group by SubscriptionType
Order by 2 desc
 ```
![find the most popular subscription type by the number of customers](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/2bab10a2b8ccb952bdb7d700529550198da4b0b3/Most%20popular%20Sub%20By%20Region.png)

4.Find customers who canceled their subscription within 6 months
```SQL
 Select customerID as CanceledSub from [dbo].[LITA_CApstones Customerdata]
 where subscription_Duration < 180
 Group by CustomerID
 ```
![find customers who canceled their subscription within 6 months](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/2bab10a2b8ccb952bdb7d700529550198da4b0b3/Canceled%20within%206months.png)

5.Calculate the average subscription duration for all customers
```SQL
Select customerID, AVG(Subscription_Duration) as Average_subDuration from [dbo].[LITA_CApstones Customerdata]
Group by customerID
Order by 2 desc
 ```
![calculate the average subscription duration for all customers](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/2bab10a2b8ccb952bdb7d700529550198da4b0b3/Avg.%20sub%20duration.png)

6.Find customers with subscriptions longer than 12 months
```SQL
Select CustomerName, count(Subscription_Duration) as HighersubDuration from [dbo].[LITA_CApstones Customerdata]
where Subscription_Duration > 365
Group by CustomerName
Order by 2 desc
 ```
![find customers with subscriptions longer than 12 months.](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/8381e12046a10e7c00c40a1f7943ee24784640d3/Sub%20over%2012months.png)

7.Calculate total revenue by subscription type
```SQL
Select SubscriptionType, SUM(Revenue) as Revenue_Subcription from [dbo].[LITA_CApstones Customerdata]
Group by SubscriptionType
Order by 2 desc
 ```
![calculate total revenue by subscription type](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/2bab10a2b8ccb952bdb7d700529550198da4b0b3/Revenue%20by%20Sub%20Type.png)

8.Find the top 3 regions by subscription cancellations.
```SQL
Select  top 3  region, count(Canceled) as Cancelled_Subcription from [dbo].[LITA_CApstones Customerdata]
where Canceled = 0
Group by Region
Order by Cancelled_Subcription desc
 ```
![find the top 3 regions by subscription cancellations.](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/2bab10a2b8ccb952bdb7d700529550198da4b0b3/Top%20Region%20by%20Canceletion.png)

9.Find the top 3 regions by subscription Active]
```SQL
Select  top 3  region, count(Canceled) as Active_Subcription from [dbo].[LITA_CApstones Customerdata]
where Canceled = 1
Group by Region
Order by Active_Subcription desc
 ```
![find the top 3 regions by subscription Active](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/2bab10a2b8ccb952bdb7d700529550198da4b0b3/Top%20Region%20for%20Active%20sub.png)

10.Find the total number of active and canceled subscriptions.
................find the total number of active and canceled subscriptions.
```SQL
SELECT 
    SubscriptionType,
    COUNT(CASE WHEN Canceled = '0' THEN 1 END) AS Canceled,
    COUNT(CASE WHEN Canceled = '1' THEN 1 END) AS Active
FROM  [dbo].[LITA_CApstones Customerdata]
GROUP BY SubscriptionType
 ```
![find the total number of active and canceled subscriptions.](https://github.com/SGaniyat/Capstone-Project---Customer-Data/blob/2bab10a2b8ccb952bdb7d700529550198da4b0b3/Active%20and%20Canceled%20Sub.png)
