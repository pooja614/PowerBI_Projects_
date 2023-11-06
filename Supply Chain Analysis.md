# Supply Chain Analysis 

Supply chain analysis is the process of evaluating every stage of a supply chain starting from the time the business acquires raw materials or supplies from its suppliers, to the delivery of final products to the customers. 

![logistics-3125131_640](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/2e1d00bc-c371-422e-8390-8580fd5257a7)

## Descriptive analytics
This project aims at descriptive analysis. It is a type of analytics where data is used to describe trends and relationships, such as supply chain performance or a warehouse’s inventory levels. Logistics professionals use descriptive analytics, consequently, to understand how a supply chain and its parts are currently working.  
### About the Data 
* The dataset of Supply Chains used by the company DataCo Global is used for the analysis.
* The dataset is obtained from kaggle.
* Provisioning , Production , Sales , Commercial Distribution are some of the areas of analysis included in this project. 
## Planning 
* Data columns are grouped for understanding of the data.
* Excel is used to understand the relation between different columns and categorize them to create schema.
   ![plan](https://github.com/pooja614/supply_chain/assets/69869583/1c8f0244-b240-49e0-bfb0-21e5c4465613)
## Data Preprocessing and Data Modelling
* The data type of the relevant columns are changed to respective types.
* Dublicates are removed. 
* The data columns are grouped and seperated into different tables.
* Different transformation steps are applied. 
* ![etl_2](https://github.com/pooja614/supply_chain/assets/69869583/775714a3-d6e0-4c46-8982-586ed23165eb)
* Tables are merged to assign IDs' in  Fact table. 
* The data is modelled to 'Star Schema'. 
* New IDs' are assigned to few columns after creating table.
![data_model](https://github.com/pooja614/supply_chain/assets/69869583/f7a220ca-9653-4fdc-8c50-8fa29f2aaf1b)
* Relationship is assigned between primary key and foreign key. 
* Date table is newly populated for efficient plotting of graph.



## DAX and Measures
* Different measures are created using DAX for analysis<br>
* DAX functions are used to produce effective calculations and analysis.
<pre>
 

<b>Creating Date Column: </b>
Dates = CALENDAR(DATE(YEAR(MIN('DIM-order'[order date])),1,1), DATE(YEAR(MAX('DIM-order'[order date])), 1,31))

<b>DAX Queries: </b>
Net Sales = SUM('FACT-CoSupplyChain'[Net Sales])
Net Revenue = SUM('FACT-CoSupplyChain'[Net Sales])
Revenue Contribution % = 
  DIVIDE(
  [Net Revenue], 
  CALCULATE(
  [Net Revenue], ALL('DIM-category'), All('DIM-customers'), All('DIM-order'), ALL('DIM-product')
  )
  )


Total Profit Margin = sum('FACT-CoSupplyChain'[Order Profit Per Order])
Profit Margin % = [Total Profit Margin]/[Net Revenue] 
Profit Margin Contribution % =
  DIVIDE(
  [Total Profit Margin], 
  CALCULATE([Total Profit Margin], ALL('DIM-category'), All('DIM-customers'), All('DIM-order'), ALL('DIM-product')
  )
  )

Sales LM = CALCULATE( [Net Sales],DATEADD('FACT-CoSupplyChain'[order date],-1,MONTH))  
Sales Monthly Change% = DIVIDE([Net Sales],[Sales LM])



Quantity = 
CALCULATE(
[Total Quantity],
ALL('DIM-order'[Order Region]))

Total Orders = COUNT('FACT-CoSupplyChain'[Order Id])


Consumer Net Revenue = 
CALCULATE(
    [Net Revenue], 
    'DIM-customers'[Customer Segment] = "Consumer"
)

Corporate Net Revenue = 
CALCULATE(
    [Net Revenue], 
    'DIM-customers'[Customer Segment] = "Corporate"
)

Home Office Net Revenue = 
CALCULATE(
    [Net Revenue], 
    'DIM-customers'[Customer Segment] = "Home Office"
)

Loss Sales = CALCULATE(SUM('FACT-CoSupplyChain'[Net Sales]),'FACT-CoSupplyChain'[Order Item Profit Ratio]<0)
Loss % = DIVIDE([Loss Sales],[Net Sales])

Loss Sales LY % = 
VAR Sales_ = 
CALCULATE(
    [Loss %], 
    DATEADD(
        Dates[Date], 
        -1, 
        Year
    )
)

RETURN 
COALESCE(
    Sales_ , 
    "-"
)

</pre>
## Tooltips and Filters
Tooltips and filters are used. 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/d94edc56-01fd-4c64-a300-82f79bfcbda4)

## Visualizations 
The below slides are the non-interactive version of the Interactive PowerBI Dashboard. 
### Geography and Market Sales Analysis
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/71f4babd-ea09-4e1f-8943-039de7f446ac) 
<pre>
- Europe and LATUM are top markets. 
- Western Europe, Central America has highest sales worth supplied. 
- We observe in Central America Mexico has the highest worth ordered. 
</pre>
### Net Sales VS Category
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/f730bb53-cb58-45b2-a7f8-9e9d35dfac35)
<pre>
- Fishing, cleats, camping & Hiking, Cardio Equipement have most demands. 
- LATUM is top market for Accessories and 'Baseball & Softball' 
- Department Fan Shop, Golf, Apparel have more number of quantities but, w.r.to revenu Apparel is above Golf items. 
</pre> 
### Revenue Insights
![sc_ex](https://github.com/pooja614/supply_chain/assets/69869583/94fb0e99-5b1a-4c85-8cb7-da22251f89cc)
<pre>
- Europe, LATUM are high revenue contribution %. 
- Profit Margin % is slightly more in USCA, Africa even though the market value is less. 
- Europe, LATUM have high Profit Margin Contribution. 
</pre>

![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/c15a4dda-f160-4270-ba50-30f5a452d916) 
<pre>
- 10 countires have negetive Profit Margin %. 
- Revenue Contribution% Trends and Profit Margin Contribution% trends are not same. 
</pre>

### Customer Segment Insights
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/27790315-8ae9-4402-b039-2b33d5ca1321)
<pre>
- Caguas is the top Revenue generating city followed by Chicago. 
- PR, NY, CA are top performing state 
- Consumer revenue is highest followed by corporate and home office customers. 
- EE.UU Country has more revenue contribution. 
</pre>
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/c7ddca71-8b51-4704-84fd-0bf0c84af28c) 
<pre>
Top preforming customers are visualized. 
</pre>
### Yearly, Quarterly, Monthly Analysis 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/504ffdfa-fa30-4c01-a3ce-4b36a7206844) 
<pre>
- There is dip in total sales in February and then there is a gradual increase. 
- After october there is decline. 
- Other filters generates different results.
</Pre>
### Timing Trends by Category
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/5a2dd401-dcf6-4278-8c57-6ecab56c06ed) 
<pre>
- Book category is the applied filter. 
- Books are most sold afternoon. 
- Can be used for offers and advertisements. 
</pre>
### Loss Sales 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/6c08f628-020e-4e8f-9961-63ab6b3ca4c8)
### Order and Payment 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/b0256445-66fe-4d1a-89c5-20a5b01a96e8)

### Shipment and Delivery 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/d61de4c2-eaae-4bf5-a250-d2b73ab83662)
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/401236de-f000-4adb-920a-c2c670e41fb9) 
<pre>
- Most category fall under late delivery. 
- Advanse shipping has delivered faster than the days scheduled. 
</pre> 

<pre>
This is non-interactive version of the interactive PowerBI dashboard. Sample insights are presented through the slide. 
</pre>
### Conclusion 
Thus these insights can be used 
![image](https://github.com/pooja614/PowerBI_Projects_/assets/69869583/7269b782-9f44-4ef2-9402-c4c7a98e61b5)
