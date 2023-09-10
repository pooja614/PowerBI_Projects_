# Supply Chain Analysis

### About the Data 
* The dataset of Supply Chains used by the company DataCo Global is used for the analysis.
* The dataset is obtained from kaggle.
* Provisioning , Production , Sales , Commercial Distribution are some of the areas of analysis.
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
![data_model](https://github.com/pooja614/supply_chain/assets/69869583/3043c88c-3397-432d-9278-00c48450e4e4)
* Relationship is assigned between primary key and foreign key. 
* Date table is newly populated for efficient plotting of graph.
### Measures 
* Different measures are created using DAX for analysis<br>
Eg:
* Total Sales = SUM('FACT-CoSupplyChain'[Sales])
* Other Sales = CALCULATE(SUM('FACT-CoSupplyChain'[Sales]),'FACT-CoSupplyChain'[Order Item Profit Ratio]>=0)
* Loss Sales = CALCULATE(SUM('FACT-CoSupplyChain'[Sales]),'FACT-CoSupplyChain'[Order Item Profit Ratio]<0)
* Loss % = DIVIDE([Loss Sales],[Total Sales]) 

## Visualizations

### Geographical Insights
![sc1](https://github.com/pooja614/supply_chain/assets/69869583/5d7f8911-bd40-4838-8de1-acc00fcd6319)
*	Western Europe has highest sales order amount followed by central and south America. 
*	Europe and LATAM has 29% and 28% shares in total sales. 
*	Western Europe is highest in Europe, Oceania is highest in Pacific Asia,  West USA and West Africa is highest in USCA and Africa respectively. 
<br></br>
<br></br>

![sc_2](https://github.com/pooja614/supply_chain/assets/69869583/e9ccb79a-5b1b-49ac-87c3-1cedd3487cd4)
*	Highest sales by category, order country and region is depicted.  
*	Fishing category has greater demands followed by cleats.  
*	Estados Unidos is highest order country. 
<br></br>
<br></br>
![tl_1](https://github.com/pooja614/supply_chain/assets/69869583/ef47abf1-234b-40e8-999d-58e97daa1888)
![tl_2](https://github.com/pooja614/supply_chain/assets/69869583/66c65f85-0990-46ae-bb3e-a3e3fe74964d)
* Tooltip is used for detailed visualization.
  <br></br>
<br></br>
### Customer Insights
![sc_3](https://github.com/pooja614/supply_chain/assets/69869583/22d8bf82-2d65-49b1-8966-f4a5fc68a5ff)
*	Consumer segments has highest sales. 
*	Field & Stream Sportsman 16 gun fire safe’ is the highest sold product. 
*	Customer country is more based on EE. UU. 
*	Caguas, Chicago Los Angeles has more sales. 
<br></br>
<br></br>
### Yearly Sales
![sc_4](https://github.com/pooja614/supply_chain/assets/69869583/c3f1bb0d-a6c6-43ba-9fb8-f7f6162ffcab)
* There is decrease in sales from 2016 to 2017.
  <br></br>
<br></br>
### Monthly Sales
![sc_5](https://github.com/pooja614/supply_chain/assets/69869583/edcbea1d-b7b5-40c1-a6ad-af479899d738)
*	There is dip in sales in February, June and October. 
*	Sales after September has a decrease and consistent reduced sales till December. 
*	Computers sales is observed from October to December. 
*	Different category slicer can be applied for category wise sales analysis.
  <br></br>
<br></br>
### Quartely Sales
![sc_6](https://github.com/pooja614/supply_chain/assets/69869583/264a5891-94fb-4945-aef8-8562b946458b) 
*	There is slight increasing trend from Quarter 1 to Quarter 3, after which the sales is decreased for top sales categories.  
*	Other categories have different patterns. 
<br></br>
<br></br>
### Time Trends
![sc_7](https://github.com/pooja614/supply_chain/assets/69869583/5afd343d-54d7-43d2-8a4f-e7a44440c5eb) 
*	The timings of order is analysed. 
*	Women clothing has highest order during 3.00 to 6.00 early hours and most sales are from 2:00(14:00) to evening 6.00(18:00) and night 9.00 to 10:00 has few sales. 
*	Different categories has different pattern of sales. 
<br></br>
<br></br>
### Sales and Discount Rate
![image](https://github.com/pooja614/supply_chain/assets/69869583/f71b767f-b0f2-4f14-ab87-ea3997a53977)
*	There is raise in total overall sales for 3%, 13% discount rate, little raise for 20% discount. 25% discount has relatively more total overall sales. 
*	The pattern is different for different categories. 
<br></br>
<br></br>
### Profit Ratio Analysis
![sc_n](https://github.com/pooja614/supply_chain/assets/69869583/08446218-35c2-4b1b-8ba1-e66e45866319) 
* Profit ratio is highest for cleats, followed by Men’s Footwear and  Women’s apparel. 
* Safe margin for positive profit ratio  is total sales above 3,50,000. 
<br></br>
<br></br>
![image](https://github.com/pooja614/supply_chain/assets/69869583/23142a7d-dc85-4b8a-996a-5ceab2160bb2)
* Profit ratio is highest during September.
  <br></br>
<br></br> 
![image](https://github.com/pooja614/supply_chain/assets/69869583/dc910510-7c58-4222-8585-9591329d2e2b)
*	6.87 million sales are yielding negative profit ratio. 
*	The loss% is 18.68%. 
*	1.3million and 0.8million  sales are yielding loss in fishing and cleats category respectively. 
*	Category wise losses are depicted. 
<br></br>
<br></br>

![image](https://github.com/pooja614/supply_chain/assets/69869583/0f6eb045-5cf2-4cce-b514-08cde703e1ff)
*	Monthly  loss is analysed filtered by category. 
*	We observe that fishing has highest loss% during June and December. 
<br></br>
<br></br> 
### Payment Analysis
![sc_n2](https://github.com/pooja614/supply_chain/assets/69869583/5fbe9e9a-d8a4-46b4-8533-5a8fda4b82db) 
*	5.43% of payment is on hold and 2.25% suspected to be fraud. 
*	22% of customers has pending payment and 12% payment are processing. 
*	Debit is the highest preferred payment mode followed by transfer. 
*	11% prefer cash. 
*	2.0M sales transaction are in hold(debit), 0.8M transactions are suspected to be fraud(transfer)
<br></br>
<br></br>
### Shipping and Delivery Analysis
![sc_13](https://github.com/pooja614/supply_chain/assets/69869583/8fb140e1-45ca-43b6-acbd-2fe568c2ce6d) 
*	Late delivery is almost double the number of days scheduled. 
*	8.5M sales is advanced shipping mode and standard class. 
*	All the market has later delivery risk. 
*	Standard class and second class shipping mode is used with 59.69% and 19.51% count of sales respectively. 
*	Sales worth 1.57M sales has shipping cancelled. 

### Purchase Quantity Analysis
![image](https://github.com/pooja614/supply_chain/assets/69869583/00b43f8d-8101-4e08-a047-bf521eb12ac6)
* There is decrease in quantity of item ordered since September. 
<br></br>
<br></br>
### Shipping Mode
![sc_15](https://github.com/pooja614/supply_chain/assets/69869583/9e6a6576-d688-4ab0-8cb9-66340e145ef8) 
*	There is raise in first class shipping mode in March and May where as second class has raise in April and August-September. 
*	Same day shipping has raise in March and July. 
<br></br>
<br></br>
* This is non-interactive report of the interactive powerbi dashboard. Further insights and knowledge can be extracted by applying the filters. 

