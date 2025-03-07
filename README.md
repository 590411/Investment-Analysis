
# Analysis and performance of  stock  porfolio

## Company activity/ field : Capital partners , an investment bank

## Table of Content
-  [Project Overview](#project-overview)
-  [Data Sources](#data-sources)
-  [Tools](#tools)
-    
### Project overview
--- 
---- **Delivrables**

The sales and trading team need  customer power bi report to assist in the security and portfolio analysis

     *In the transformation and modelling stage , I establish the foundation for our stock analysis , a data model that allow us to analyse :
      -The price and volume of our stock
      -The exchanges on which they are traded
      -How we combine them into our investment portfolio

    *The aim of the  Analyse and  visualize stage , is to create two report page  namely : exchange and securities & portfolio
     - Exchange report : provide insight for the changes in the dataset
		 - Which exchange do securities comes from
		 - Where are securities located geographically
		 - which exchanges are most popular in term of volume  traded
     - Securities & portfolio report :  provide insight for the changes in individual security and investment portfolio
		 - what are some relationships between securities that can provide insights into high performance 
		 - What is the security performance over time
		 - Which securities performed  well or which ones underperformed

    * Regarding the user experience , we shall highlight the insights from our stock analysis and make our report easier to work with

![Data model](https://github.com/user-attachments/assets/0871e6db-10f0-410e-96ea-957129208e69)

![Dashboard](https://github.com/user-attachments/assets/91e9c950-2c17-4cbe-ba44-002ca861fa15)

![Dashbord 2](https://github.com/user-attachments/assets/ab1b2f92-228d-4b07-b8e4-a556c32a6a53)


 ## Data sources 
 ---
 
* The dataset use for this analysis is found in the factActivity folder , dimExchange.xlsx and dimSecurity.xlsx files. we have data on date , security , company , industry,exchange.... and is for  the daily metrics of security from  Capital partners

## Tools
---

  - Excel-power query : Data cleaning , transformation and loading
  - Power BI - DAX : Measures
  - Power BI : Data model and visualisation
    

- ## DAX MEASURE
 
```
	----- To create  measure folder :   #Measures = GENERATESERIES(1,1,1)

	----- Average price change = AVERAGE(factActivity[Price change] )

	----- Average price range = AVERAGE(factActivity[Price range])

	----- count security = COUNT(dimSecurity[Security_ID]) 

	----- Total close price = SUM(factActivity[Close])

	----- Total volume = SUM(factActivity[Volume]) 

	----- Avg daily volume = AVERAGEX(dimDate, [Total volumn])

	----- Min daily volume = MINX(dimDate,[Total volumn])

	----- Max daily volume = MAXX(dimDate, [Total volume])

	----- YTD Avg daily volume = CALCULATE([Avg daily volume], DATESYTD(dimDate[Date])) 

	----- YTD Min daily volume = CALCULATE([Min daily volume], DATESYTD(dimDate[Date])) 

	----- YTD Max daily volume = CALCULATE([Max daily volume], DATESYTD(dimDate[Date])) 

	----- YTD Max daily volume = CALCULATE([Max daily volume], DATESYTD(dimDate[Date])) 

	----- Total weighting = SUM(dimSecurity[Weighting])

	----- Total porfolio value = SUM(factActivity[Porfolio value])

	----- current close price = CALCULATE([Total close price],LASTNONBLANK(dimDate[Date],[Total close price]))

	----- Current pofolio value = [current price] *[Total weighting]
```

- ## calculated columns
```
weighting = RELATED(dimSecurity[Weighting])
Porfolio value = factActivity[weighting]*factActivity[Close] 
        
```


💻💻  

