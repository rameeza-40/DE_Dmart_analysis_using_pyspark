# DE_Dmart_analysis_using_pyspark

## *Project Overview*

This project performs data analysis on Dmart sales data using Apache PySpark. The analysis includes data transformation, cleaning, and querying various insights such as total sales, customer purchasing patterns, product performance, and more.


##  *Techologies Used* 
  * *python*
  * *PySpark*
  * *Google Colab*

## *Dataset*
*The project utilizes three datasets:*

1.Product.csv - Contains details about products.

2.Sales.csv - Includes sales transactions.

3.Customer.csv - Holds customer information.

## *Steps Involved*
*1. Setting Up PySpark Connection*

  *A Spark session is created using:*
          
                    spark = SparkSession.builder.appName("Dmart Analysis").getOrCreate()

  *2. Loading Data into PySpark:*
       
  
  *Data is loaded from CSV files:*

                    products_df = spark.read.csv("/content/Product.csv", header=True, inferSchema=True)
                    
                    sales_df = spark.read.csv("/content/Sales.csv", header=True, inferSchema=True)
                    
                    customers_df = spark.read.csv("/content/Customer.csv", header=True, inferSchema=True)

*3. Data Transformation and Cleaning:*

* *Renaming columns for consistency*

* *Handling missing values by dropping null records*

* *Ensuring correct data types*

* *Joining datasets for analysis*


*4. Data Analysis & Querying:*

* *Performed various queries using PySpark functions:*

  *1.Total Sales by Category:*


                   total_sales_category = Product_sales_df.groupBy("Category").sum("Sales")

                   total_sales_category.show()
*2.Customer with the Highest Purchases:*

                   customer_purchases = Customer_sales_df.groupBy("Customer_id").count().orderBy(col("count").desc())
                   
                   customer_purchases.show(1)

*3.Average Discount Given:*

                  avg_discount = Product_sales_df.select(avg("Discount"))
                  
                  avg_discount.show()

 *4.Unique Products Sold per Region:*

                   unique_products_region = all_data_df.groupBy("Region").agg(countDistinct("Product_id").alias("Unique_Products"))
                  
                   unique_products_region.show()
                   
*5.Total Profit generated in each state:*

                   final_df.groupBy("State").agg(sum("Profit").alias("Total_Profit")).show()

*6.Product sub-category with highest sales:
                  
                   highest_sales_subcategory = all_data_df.groupBy("Sub-Category").sum("Sales").orderBy(col("sum(Sales)").desc())
                   
*7.Average age of customers in each segment:*

                   avg_age_segment = all_data_df.groupBy("Segment").avg("Age")
                   
                   avg_age_segment.show()

*8.Orders shipped in each shipping mode:*
                  
                  orders_shipping_mode = all_data_df.groupBy("Ship_Mode").count()
                  
                  orders_shipping_mode.show()
                  
*9.Total quantity of products sold in each city:*
                   total_qty_city = all_data_df.groupBy("City").sum("Quantity")
                   
                   total_qty_city.show()
                   
*10. Customer segment with the highest profit margin:*
                   profit_segment = all_data_df.groupBy("Segment").sum("Profit").orderBy(col("sum(Profit)").desc())
                   
                   profit_segment.show(1)



Stop Spark session:
     
     spark.stop()


## *Conclusion:*
   This PySpark-driven Dmart analysis successfully integrates multiple datasets, cleans and transforms them, and provides valuable insights through business-centric queries.The solution is scalable, fast, and adaptable for enterprise-level analytics.       







```
>>>End
```
