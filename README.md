# Sales-Analysis Overview 
PROJECT OVERVIEW: This project involved creating an end-to-end ETL pipeline to extract, transform and load data from different sources to Staging and Production SQL Server Databases. To achieve the above, I wrote optimized SQL queries, and data extraction scripts in SSMS. Additionally, I used SSAS to create cubes for multi-dimensional analysis. These summary cubes were used to create dashboards and analyze data visualizations that drive decisions.
1. Business Scenario: A Grocery store requires an ETL Developer to migrate all the data from different sources to a central warehouse and develop dashboard that would help Sales Manager to:
a.	track product movement, as well as to see how sales are impacted by promotions.
b.	understand the mix of products in a customer’s market basket.
c. 	frequency of channel POS device replacement
d.	know the effects of product rebranding on sales.
e. 	perform sales analysis on overall product brand sales and rebrand product sales.
f.	needs to know what the most demanded products for each time of the day are.
2. STEPS USED TO COMPLETE THE PROJECT

a. Restore the existing backup database:
The first step I took was to restore the database and create a conceptual, logical and the physical relational models to conform to requirements specification.

Figure 1: Conceptual Data Model
![image](https://user-images.githubusercontent.com/99350558/234389121-bc526e05-3f7d-46f8-b21b-d8cf11eaf995.png)



Figure 2: Logical Data Model
![image](https://user-images.githubusercontent.com/99350558/234389231-402c6897-9c93-4a75-9087-2def739b073e.png)



Figure 3: Physical Data Model
![image](https://user-images.githubusercontent.com/99350558/234393596-60789efb-1e16-4f2e-acdc-d0d768b6134d.png)


b. Create the ETL pipelines:
I used the dimensional modelling technique invented by Ralph Kimball to design my Data Warehouse. This involved denormalization of the OLTP to create a star schema that comprise fact (Sales fact) and dimensions. An example of the star schema is shown in the Figure 4. I followed the following four steps in the design of my Data Warehouse. (i)Selection of the business process, (ii)Declare the grain, (iii)Identify the dimensions, and (iv)Identify the facts. Figure 5 shows a summary of this process.

Next, I wrote optimized SQL queries to extract the data from the OLTP, transform and then loaded the data into the staging environment. I then created another pipeline to load and truncate the data from the staging into the Data Warehouse. To account for any data loss during the ETL process, we included a data pre-count, destination count, current count, Type 1 count, type 2 count, and a post count to help track the data movement.

Figure 4: Star Schema showing the fact and the associated dimension tables.
![image](https://user-images.githubusercontent.com/99350558/234393970-71de0994-e926-4e5a-aa08-223061cdcf27.png)


Figure 5: Template showing the steps taken in the design of the Data Warehouse.
![image](https://user-images.githubusercontent.com/99350558/234394317-843b3dcf-17d4-4f00-a53c-809bb2ee87f6.png)


c. Deploy the model: I then created a control framework that specify the environment (staging or Data Warehouse), the frequency at which this data would be migrated (daily, weekly, monthly and yearly), the package type (Dimension or facts), the package which is a container that holds the data to be moved and the metrics to account for the volume of data that is been moved on daily, weekly, monthly or yearly bases. This control framework was deployed using the SQL Server agent. The agent was responsible for scheduling and maintain the data migration.


