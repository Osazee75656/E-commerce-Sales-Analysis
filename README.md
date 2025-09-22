# E-commerce-Sales-Analysis

## Table of Content
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Findings](#findings)
- [Recommendation](#recommendation)
- [Limitation](#limitation)
- [Reference](#reference)
  

### Project Overview  
This analysis offers a detailed summary of e-commerce sales performance from [2014] to [2021]. The purpose of this report is to highlight major trends, assess the success of sales strategies, and deliver actionable insights to improve future business decisions.

### Data Sources  
- Sales Data: The primary dataset used in this analysis is the Sales data set (fact_table), which contains comprehensive details about the company's sales from 2014 to 2021.  
- Country Data: This secondary dataset (item_dim) includes information about locations, suppliers, and other columns, supplementing the primary dataset to map geographical sales distribution.  
- Time Data: The time_dim data was modelled with a one-to-many relationship to link sales data and provide an accurate project timeline.  
- Transaction Data: The trans_type data was also modelled to the fact_table date using a one-to-many relationship to offer transactional insights for the project.

### Tools  
- Power Query: Used to import and load the "text/csv file," including cleaning the dataset, changing data types, removing duplicates, handling missing data, and replacing values.  
- PowerBI: Utilized for writing DAX measures and creating the report.  
- PowerPoint: Employed to design the wireframe uploaded as the background of the PowerBI report.  
- Natural Earth: This website provided files needed to customise the PowerBI shape map. [Download here](https://www.naturalearthdata.com/)  
- Map Shaper: This site converted maps to the correct format for customising the map. [Download here](https://mapshaper.org/)  
- Colour Picker: Used to select desired colours from images and convert them to Hex codes. [Download here](https://imagecolorpicker.com/)  
- Icons: This website was used to choose the desired icons for the wireframe. [Download here](https://www.flaticon.com/)

### Data Cleaning  

During data preparation, the following steps were undertaken:  
1. Data loading and inspection  
2. Handling missing values  
3. Data cleaning and formatting  
4. Checking column distribution and quality  
5. Changing data types  
6. Removing duplicates

### Exploratory Data Analysis  
This phase involved examining the overall data to answer key questions such as:  
- What is the overall sales trend?  
- What is the monthly sales trend?  
- How is sales distributed geographically?  
- Who are the top-performing customers?  
- What are the top five performing units?  
- How do sales compare year on year?

### Data Analysis  
Below is an example of a measure used: 

- #### Year on Year Measures %
```DAX  
% YOY SALES =  
    var a = DIVIDE([Total Sales],[PY Sales]) - 1  
    var label = FORMAT(a, "#0.0%")  
    RETURN label & IF(a > 0, "▲", "▼")  
```

```DAX  
% YOY Qty = 
    var a = DIVIDE([Total Qty],[PY Qty])-1
    var label = FORMAT(a, "#0.0%")
    RETURN label & IF(a>0, "▲","▼") 
```

```DAX  
% YOY Customer = 
    var a = DIVIDE([Customers],[PY Customers])-1
    var label = FORMAT(a, "#0.0%")
    RETURN label & IF(a>0, "▲","▼")
```

```DAX  
% YOY Customer = 
    var a = DIVIDE([Customers],[PY Customers])-1
    var label = FORMAT(a, "#0.0%")
    RETURN label & IF(a>0, "▲","▼")
```

```DAX  
% YOY Avg Price = 
    var a = DIVIDE([Avg Unit Price],[PY Price])-1
    var label = FORMAT(a, "#0.0%")
    RETURN label & IF(a>0, "▲","▼")
```


- #### Previous Year Measure

```DAX
PY Sales = CALCULATE([Total Sales],SAMEPERIODLASTYEAR(time_dim[Date]), REMOVEFILTERS())
```

```DAX
PY Qty = CALCULATE([Total Qty],SAMEPERIODLASTYEAR(time_dim[Date]), REMOVEFILTERS())
```

```DAX
PY Price = CALCULATE([Avg Unit Price],SAMEPERIODLASTYEAR(time_dim[Date]), REMOVEFILTERS())
```

```DAX
PY Customers = CALCULATE([Customers],SAMEPERIODLASTYEAR(time_dim[Date]), REMOVEFILTERS())
```

- #### Main Measure

```DAX
Total Sales = SUM(fact_table[Sales])
```

```DAX
Total Qty = SUM(fact_table[quantity])
```

```DAX
Customers = DISTINCTCOUNT(customer_dim[coustomer_key])
```

```DAX
Avg Unit Price = AVERAGE(fact_table[unit_price])
```

- #### Colour Code

```DAX
Sales Color = IF([Total Sales]>[PY Sales],"#85BD5F", "#A83F22")
```

```DAX
Qty Color = IF([Total Qty]>[PY Qty],"#85BD5F", "#A83F22")
```

```DAX
Price Color = IF([Avg Unit Price]>[PY Price],"#85BD5F", "#A83F22")
```

```DAX
Customer Color = IF([Customers]>[PY Customers],"#85BD5F", "#A83F22")
```

- #### Base Measure

```DAX
Base = 0
```

### Findings
The Analysis result is summerised below
- The company total sales has remained flat from 2015 to 2020, then abruptly dropped in 2021, There was a noticeable huge fall in quantity as well 
- The top five countries with the highest sales for the company are Bangladesh, India, Poland, Germany, and Finland.  
- The total number of customers has remained stable over the years, with no new customers added between 2014 and 2015.  
- The leading five units in sales performance are CT, cans, bottles, oz, and bags, respectively.  
- Additionally, it was found that the top five spenders have remained consistent throughout the years. 

### Recommendation 
Based on the analysis of the e-commerce sales dataset from [2014] to [2021], we have identified several key areas for improvement. The following recommendations are designed to capitalize on existing strengths and address observed weaknesses, thereby optimizing revenue and enhancing the customer experience.

- The company needs to allocate more resources to a stronger marketing campaign and promotional efforts to attract new customers efficiently.  
- The company ought to concentrate on increasing sales of the Top 5 units and enhancing the promotion of these products, as they are the best-performing items in the company.

### Limitation 

I needed to substitute values in the dataset as they would have impacted the accuracy of the analysis. For 2021, we only possessed data for January, which accounts for the decline in revenue from $15 million to $884,000.

### Reference 
[Freedom Oboh](https://drive.google.com/drive/folders/14PlrT2DCYY5reeurPlv1v4zLdWPL1fIk)

  
