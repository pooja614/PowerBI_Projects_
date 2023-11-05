# Vrinda Store Analysis 
Objective:<br>
Vrinda Store' wants to  understand their customers and purchase trends for better growth of the business in the year 2023. <br><br>
The project focuses on understanding the customers of 'Vrinda Store' and the purchase trends for better growth of the business. <br>
The sales for year 2022 is analyzed. 
## Data Preprocessing  
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/269c5344-8fe4-4564-b480-105cf8332e2f)
<pre> 
Removing duplicate data, and useless columns. 
Relevant preprocessing is done. 
</pre>
## Data Modelling 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/abd7a744-21fd-4472-a4c0-3c8bfb1c381a)

- Data is modelled to 'Star Schema'.
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/2ccc0de9-d318-48c4-97bf-d136cdc82faf)

## DAX Calculations 
DAX functions are used for efficient analysis. The following are few DAX codes coded for the project. 
<pre> 
Total Sales = SUM('Fact-VrindaStores'[Amount]) 
  
Overall Sales = 
CALCULATE(
    [Total Sales], 
    ALL('Fact-VrindaStores'[ship-city]), 
    ALL('Dim-Category'[Category]), 
    ALL(Dates), 
    ALL('Dim-Gender'[Gender]
))

% Sales = 
DIVIDE(
    [Total Sales],
    [Overall Sales],
    "0"
) 


% of Sales by Females = 
VAR fem_sales = 
    CALCULATE(
        [Total Sales],
        'Dim-Gender'[Gender] = "Women"
    )
VAR ratio = 
DIVIDE(
    fem_sales,
     [Total Sales],
     0
     )
return ratio 

Refunded % = 
VAR Refunded = 
CALCULATE(
    [Total Sales], 
    'Dim-DeliveryStatus'[Status] = "Refunded"
) 

VAR ratio = 
    DIVIDE(
        Refunded,
        [Total Sales],
        0
    )
return ratio  

% Share in their State = 
CALCULATE(
    [Total Sales], 
    'Fact-VrindaStores'[ship-city]
    ) 

Average Monthly Sales = 
AVERAGEX(
    Dates, 
    [Total Sales]
)

Last Month's Sales = 
CALCULATE(
    [Total Sales], 
    PARALLELPERIOD(
        Dates[Date], 
        -1, 
        MONTH
    )
) 

Sales MoM% Change = 
DIVIDE(
    ([Total Sales]-[Last Month's Sales]), 
    [Last Month's Sales], 
    BLANK()
) 


</pre>
- DAX measures is used for applying suitable filtering and generating aggregate values. 
### Overall Analysis 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/32003330-471a-461e-b087-80c102bc2409)
<pre>
- The slide is filtered to show the statistics for sales that has been sucessfully delivered. 
- Amazon has highest sales for the store products followed by Myntra and Flipkart. 
- Middle Age adults are highest purchasers. 
- Women have highest rate of purchase. 
- Maharastra, Karnataka, Uttarpradesh are top states. 
</pre>


### Top 50 high performing City and trends
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/8071da8a-4058-45c7-9df8-6cbc7ccf9b13)
<pre>
- 2M sales are B2B
- M, L, XL are the sizes high in demand overall.
- Top 50 performing states are visualized.
- Bengaluru, Hyderabad, New Delhi are having highest sales %.
</pre>

### Channel Trends
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/ec2e95bf-7f95-4163-b240-eab7d8fd6816)
- 64% of sales are sold to women.
- 93% of sales are delivered overall, 2.3% of sales are cancelled, 1.3% are refunded and 3.4% are returned.
- Flipkart and Myntra has 3M sales returned,  5M sales in Amazon is returned.  

### Category and Sales of not delivered Items
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/4c192e5c-9b42-4eb6-9804-ad543a3c1771)

<pre> 
  - Depicts total sales of undelivered : Refunded, cancelled, returned.
  - Men have western dress the highest followed by 'set'. 
  - Women have Kurta highest followed by 'set'. 
  - Blouse and bottom are completely delivered at Amazon.
</pre> 
### Purchase Trends 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/5f781db2-b597-408f-8f19-983b0f4f451e)

<pre>
On filter on women, 
- February to April is peak time for Set purchases, with peak on March. 
- Further sales are increased in October. 
- Kurta has peak sales during February, May, September, November. 
- March, September, November is peak time for western dress of women. 
</pre> 

### Date and Sales 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/6a76fa48-601c-4c0e-8cd0-f5c77de007cd)

<pre>
- Qtr 1 has highest sales and Qtr 4 has lowest sales. 
- March- April has peak sales followed by July- August. 
- July has highest MoM% change and September has lowest. 
- Overall sales has a decreasing trend. 
</pre>
### Delivery Status Analysis 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/1e524177-be4a-4ca2-bdf8-74608d820ea3)

<pre>
- Top table shows the category wise status. 
- 'Kurta' has highest refund rate, 'Set' has highest cancellation and return rate campared to other categories. 
- Monthly trends indicate May and November had highest cancellation rate
- February, June, November had more refunds. 
- July October, December had highest returning of products. 
- 'Top', 'Set' has high delivery rate. 
- 'Bottom' has highest cancellation rate. 
- 'Ethnic dress', 'kurta' are mostly refunded. 
- 'Western Dress' and 'Bottom' are returned more. 
</pre> 

<pre>
This is non-interactive sample of the interactive dashboard.
Interactive dashboard will generate further insights. 
</pre>
## Conclusion 
- This analysis will be useful for taking relevant business decisions.
- Understanding the low performing areas and taking appropriate steps will serve the cause.
- Trends and patterns of purchases and preferences can be used for targetted marketing and offer announcements.
<pre>

  
</pre> 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/593f982e-5df1-4363-8663-741c6b992a5a)




