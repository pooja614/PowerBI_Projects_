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
## Measures 
* Different measures are created using DAX for analysis<br>

### DAX 

<pre>
DAX functions are used to produce effective calculations and analysis. 

Creating Date Column: 
Dates = CALENDAR(DATE(YEAR(MIN('DIM-order'[order date])),1,1), DATE(YEAR(MAX('DIM-order'[order date])), 1,31))

DAX Queries: 
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



  
### Net Revenue Insights
![sc_ex](https://github.com/pooja614/supply_chain/assets/69869583/94fb0e99-5b1a-4c85-8cb7-da22251f89cc)



