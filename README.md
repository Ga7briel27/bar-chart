
R version 4.4.2 (2024-10-31 ucrt) -- "Pile of Leaves"
Copyright (C) 2024 The R Foundation for Statistical Computing
Platform: x86_64-w64-mingw32/x64

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

[Previously saved workspace restored]

> save.image("C:\\Users\\IU Student\\Documents\\sales_report.RMD")
> install.packages("tidyverse")
Installing package into ‘C:/Users/IU Student/AppData/Local/R/win-library/4.4’
(as ‘lib’ is unspecified)
--- Please select a CRAN mirror for use in this session ---
trying URL 'https://cran.wustl.edu/bin/windows/contrib/4.4/tidyverse_2.0.0.zip'
Content type 'application/zip' length 431704 bytes (421 KB)
downloaded 421 KB

package ‘tidyverse’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
        C:\Users\IU Student\AppData\Local\Temp\RtmpInD1Ks\downloaded_packages
> 
> install.packages("knitr")
Installing package into ‘C:/Users/IU Student/AppData/Local/R/win-library/4.4’
(as ‘lib’ is unspecified)
trying URL 'https://cran.wustl.edu/bin/windows/contrib/4.4/knitr_1.50.zip'
Content type 'application/zip' length 1158552 bytes (1.1 MB)
downloaded 1.1 MB

package ‘knitr’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
        C:\Users\IU Student\AppData\Local\Temp\RtmpInD1Ks\downloaded_packages
> library(tidyverse)
── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
✔ dplyr     1.1.4     ✔ readr     2.1.5
✔ forcats   1.0.0     ✔ stringr   1.5.1
✔ ggplot2   3.5.1     ✔ tibble    3.2.1
✔ lubridate 1.9.4     ✔ tidyr     1.3.1
✔ purrr     1.0.4     
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
Warning messages:
1: package ‘tidyverse’ was built under R version 4.4.3 
2: package ‘lubridate’ was built under R version 4.4.3 
> 
> data("USPersonalExpenditure")
> # Convert to a tibble for easier manipulation
> 
> sales_data <- as_tibble(USPersonalExpenditure, rownames = "Category")
> 
>  
> 
> # View the first few rows
> 
> head(sales_data)
# A tibble: 5 × 6
  Category            `1940` `1945` `1950` `1955` `1960`
  <chr>                <dbl>  <dbl>  <dbl>  <dbl>  <dbl>
1 Food and Tobacco    22.2   44.5    59.6    73.2  86.8 
2 Household Operation 10.5   15.5    29      36.5  46.2 
3 Medical and Health   3.53   5.76    9.71   14    21.1 
4 Personal Care        1.04   1.98    2.45    3.4   5.4 
5 Private Education    0.341  0.974   1.8     2.6   3.64
> # Reshape data from wide to long format
> 
> sales_data <- sales_data %>%
+ 
+   pivot_longer(cols = -Category, names_to = "Year", values_to = "Revenue")
> 
>  
> 
> # Convert Year to numeric for plotting
> 
> sales_data <- sales_data %>%
+ 
+   mutate(Year = as.numeric(Year))
> 
>  
> 
> # View the updated structure
> 
> head(sales_data)
# A tibble: 6 × 3
  Category             Year Revenue
  <chr>               <dbl>   <dbl>
1 Food and Tobacco     1940    22.2
2 Food and Tobacco     1945    44.5
3 Food and Tobacco     1950    59.6
4 Food and Tobacco     1955    73.2
5 Food and Tobacco     1960    86.8
6 Household Operation  1940    10.5
> title: "Monthly Sales Report"
Error in title:"Monthly Sales Report" : NA/NaN argument
In addition: Warning message:
NAs introduced by coercion 
> 
> author: "Your Name"
Error: object 'author' not found
> 
> date: "`r Sys.Date()`"
Error in date:"`r Sys.Date()`" : NA/NaN argument
In addition: Warning message:
NAs introduced by coercion 
> 
> output: html_document
Error: object 'output' not found
> ## Sales Summary 
> 
>  
> 
> This report provides an **automated summary of monthly sales data**. The table below displays total revenue by product category, ensuring that business insights are always up to date.
Error: unexpected symbol in "This report"
> 
>  
> 
> ```{r load-sales-data, echo=FALSE, message=FALSE, warning=FALSE}
Error: attempt to use zero-length variable name
> 
> # Load necessary packages
> 
> library(tidyverse)
> 
> library(knitr)
Warning message:
package ‘knitr’ was built under R version 4.4.3 
> 
>  
> 
> # Example dataset: Replace with actual sales data if available
> 
> sales_data <- tibble(
+ 
+   Category = c("Food", "Clothing", "Personal Care"),
+ 
+   Revenue = c(350.8, 198.5, 75.3)
+ 
+ )
> 
>  
> 
> # Summarize total revenue per category
> 
> sales_summary <- sales_data %>%
+ 
+   group_by(Category) %>%
+ 
+   summarize(Total_Revenue = sum(Revenue))
> 
>  
> 
> # Display table using knitr for better formatting
> 
> knitr::kable(sales_summary, caption = "Total Revenue by Category")


Table: Total Revenue by Category

|Category      | Total_Revenue|
|:-------------|-------------:|
|Clothing      |         198.5|
|Food          |         350.8|
|Personal Care |          75.3|
> (sales_analysis.R):
+ 
+ # Load necessary package for visualization
+ 
+ library(ggplot2)
Error: object 'sales_analysis.R' not found
> 
>  
> 
> # Create a bar plot of total revenue by category
> 
> ggplot(sales_summary, aes(x = reorder(Category, Total_Revenue), y = Total_Revenue, fill = Category)) +
+ 
+   geom_col(show.legend = FALSE) +
+ 
+   coord_flip() +
+ 
+   labs(title = "Total Sales Revenue by Product Category",
+ 
+        x = "Product Category",
+ 
+        y = "Total Revenue ($ Billions)") +
+ 
+   theme_minimal()
> save.image("C:\\Users\\IU Student\\Documents\\Bar chart")
> q()
> 
