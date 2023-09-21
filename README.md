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
![data_model](https://github.com/pooja614/supply_chain/assets/69869583/f7a220ca-9653-4fdc-8c50-8fa29f2aaf1b)
* Relationship is assigned between primary key and foreign key. 
* Date table is newly populated for efficient plotting of graph.
### Measures 
* Different measures are created using DAX for analysis<br>
Sample:                          
* Total Sales = SUM('FACT-CoSupplyChain'[Sales])
* Other Sales = CALCULATE(SUM('FACT-CoSupplyChain'[Sales]),'FACT-CoSupplyChain'[Order Item Profit Ratio]>=0)
* Loss Sales = CALCULATE(SUM('FACT-CoSupplyChain'[Sales]),'FACT-CoSupplyChain'[Order Item Profit Ratio]<0)
* Revenue Contribution % = DIVIDE([Net Revenue], CALCULATE([Net Revenue], ALL('DIM-category'), All('DIM-customers'), All('DIM-order'), ALL('DIM-product')))

## Visualizations

### Geographical Insights
*	Western Europe has highest sales order amount followed by central and south America. 
*	Europe and LATAM has 29% and 28% shares in total sales. 
*	Western Europe is highest in Europe, Oceania is highest in Pacific Asia,  West USA and West Africa is highest in USCA and Africa respectively. 
*	Highest sales by category, order country and region is depicted.  
*	Fishing category has greater demands followed by cleats.  
*	Estados Unidos is highest order country. 
* ![tl_1](https://github.com/pooja614/supply_chain/assets/69869583/e2819a62-ab4e-479a-8d94-5e79e776bd54)
* Tooltip is used for detailed visualization.

  
### Net Revenue Insights
![sc_ex](https://github.com/pooja614/supply_chain/assets/69869583/94fb0e99-5b1a-4c85-8cb7-da22251f89cc)
### Customer Insights
*	Consumer segments has highest sales. 
*	Field & Stream Sportsman 16 gun fire safe’ is the highest sold product. 
*	Customer country is more based on EE. UU. 
*	Caguas, Chicago Los Angeles has more sales. 
### Yearly Sales
* There is decrease in sales from 2016 to 2017.
### Monthly Sales
*	There is dip in sales in February, June and October. 
*	Sales after September has a decrease and consistent reduced sales till December. 
*	Computers sales is observed from October to December. 
*	Different category slicer can be applied for category wise sales analysis.
### Quartely Sales
*	There is slight increasing trend from Quarter 1 to Quarter 3, after which the sales is decreased for top sales categories.  
*	Other categories have different patterns. 
### Time Trends
*	The timings of order is analysed. 
*	Women clothing has highest order during 3.00 to 6.00 early hours and most sales are from 2:00(14:00) to evening 6.00(18:00) and night 9.00 to 10:00 has few sales. 
*	Different categories has different pattern of sales. 
### Profit Ratio Analysis
* Profit ratio is highest for cleats, followed by Men’s Footwear and  Women’s apparel. 
* Safe margin for positive profit ratio  is total sales above 3,50,000. 
* Profit ratio is highest during September.
*	6.17 million sales are yielding negative profit ratio. 
*	The loss% is 18.67%. 
*	1.2million and 0.7million  sales are yielding loss in fishing and cleats category respectively. 
*	Category wise losses are depicted. 
*	Monthly  loss is analysed filtered by category. 
*	We observe that fishing has highest loss% during June and December. 
### Payment Analysis
![scc1](https://github.com/pooja614/supply_chain/assets/69869583/30c080b2-15c7-4ed7-9e30-2f4e9e1b8f5c)
### Shipping and Delivery Analysis
*	![scc2](https://github.com/pooja614/supply_chain/assets/69869583/fd319191-bd9a-4643-9b70-e4bd18b0503d)
### Purchase Quantity Analysis
* There is decrease in quantity of item ordered since September. 
### Shipping Mode
*	There is raise in first class shipping mode in March and May where as second class has raise in April and August-September. 
*	Same day shipping has raise in March and July. 
* This is non-interactive report of the interactive powerbi dashboard. Further insights and knowledge can be extracted by applying the filters. 

