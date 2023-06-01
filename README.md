# Sales-Analysis Overview 
PROJECT OVERVIEW:
In this project, my main objective was to develop a comprehensive ETL (Extract, Transform, Load) pipeline that facilitated the extraction, transformation, and loading of data from diverse sources into Staging and Production SQL Server Databases. To accomplish this, I employed optimized SQL queries and data extraction scripts within SQL Server Management Studio (SSMS). Furthermore, I utilized SQL Server Analysis Services (SSAS) to construct cubes for multi-dimensional analysis. These summary cubes played a vital role in generating interactive dashboards and data visualizations, enabling informed decision-making based on insightful data analysis.

1. Business Scenario:
An ETL Developer is needed by a Grocery store to carry out data migration from various sources to a centralized data warehouse. Additionally, the developer is tasked with creating a dashboard that will assist the Sales Manager in achieving the following objectives:

a. Tracking Product Movement and Analyzing Sales Impact:
The Sales Manager requires the ability to monitor the movement of products and assess how sales are influenced by promotional activities. The dashboard should provide insights into product performance, allowing the Sales Manager to make informed decisions regarding promotions and optimize sales strategies.

b. Understanding Customer Market Basket Composition:
The Sales Manager seeks to comprehend the combination of products present in a customer's market basket. By analyzing the composition of customer purchases, the dashboard should provide visibility into product affinities, cross-selling opportunities, and consumer behavior patterns.

c. Identifying Popular Products Based on Time of Day:
The Sales Manager needs to determine the most in-demand products during specific times of the day.

2. STEPS USED TO COMPLETE THE PROJECT
a. Restore the Existing Backup Database:
To begin the restoration process, I initiated the database restore procedure, ensuring that the backup was successfully restored to its original state. Once the database was restored, I proceeded with the creation of conceptual, logical, and physical relational models that aligned with the specified requirements. Figure 1 below displays the conceptual data model, illustrating the high-level representation of the database structure and relationships.

Figure 1: Conceptual Data Model
![image](https://user-images.githubusercontent.com/99350558/234389121-bc526e05-3f7d-46f8-b21b-d8cf11eaf995.png)




b. Designing the Data Warehouse:
To design the Data Warehouse, I employed the widely recognized dimensional modeling technique pioneered by Ralph Kimball. This approach involved denormalizing the OLTP (Online Transaction Processing) system to create a star schema consisting of a central fact table (such as Sales fact) surrounded by dimensional tables. Figure 4 showcases an example of the star schema implemented in the design.

During the design process, I followed a systematic approach comprising four essential steps. Firstly, I carefully selected the relevant business process to be represented in the Data Warehouse. Secondly, I declared the granularity, specifying the level of detail at which the data would be captured. Thirdly, I identified the key dimensions that provide additional context and perspectives to the facts. Lastly, I determined the appropriate facts to be included, representing the measurable data points. 

ETL Process and Data Quality:
To ensure the successful migration of data from the OLTP system to the Data Warehouse, I crafted optimized SQL queries to efficiently extract the required data. Subsequently, I performed necessary transformations on the data and loaded it into the staging environment. A separate data pipeline was established to handle the loading and truncation of data from the staging area to the Data Warehouse.

To maintain data integrity and account for any potential data loss throughout the ETL (Extract, Transform, Load) process, I implemented several tracking mechanisms. These included data pre-count, destination count, current count, Type 1 count (representing updates), Type 2 count (representing inserts), and post count. These counts provided valuable insights into the movement of data at different stages, enabling effective monitoring and quality control.

Figure 2: Star Schema showing the fact and some of the associated dimension tables.
![image](https://user-images.githubusercontent.com/99350558/234393970-71de0994-e926-4e5a-aa08-223061cdcf27.png)



c. Deployment of the Model:
To ensure seamless execution of the ETL process, I established a comprehensive control framework that encompassed key aspects of data migration. This control framework was designed to handle the movement of data between different environments, namely the staging area and the Data Warehouse.

Within this framework, I specified the frequency at which data would be migrated, ranging from daily to weekly, monthly, and yearly intervals. I categorized the data into two types: dimensions and facts, each representing a specific package. A package served as a container for the data to be transferred.

Furthermore, to accurately measure and track the volume of data being moved, I incorporated metrics within the control framework. These metrics captured information on a daily, weekly, monthly, and yearly basis, providing valuable insights into the quantity and patterns of data migration.

To automate and streamline the data migration process, I leveraged the SQL Server agent. This agent played a pivotal role in scheduling and maintaining the execution of the ETL tasks according to the predefined control framework. By utilizing the SQL Server agent, I ensured timely and efficient data migration while minimizing manual intervention.

d. Creating Analysis Cubes:
After establishing a robust data warehouse, I proceeded to leverage the power of SQL Server Analysis Services (SSAS) to perform in-depth analysis of the data. By connecting SSAS to the data warehouse, I unlocked the capability to generate valuable insights and summaries from the accumulated data.

To optimize the analysis process, I strategically designed partitions within the cubes. These partitions allowed for efficient data retrieval and processing by dividing the data into manageable segments based on specific criteria. Additionally, I implemented aggregations to enhance query performance and accelerate data retrieval for analytical purposes.

To provide a holistic view of the data and facilitate decision-making, I incorporated Key Performance Indicators (KPIs) into the analysis cubes. These KPIs acted as measurable metrics that quantified the performance and progress of the business, offering valuable insights into key aspects such as sales, profitability, and customer behavior.

Furthermore, I utilized perspectives to organize and present the data in a logical and intuitive manner. Perspectives served as customized views of the cubes, enabling different stakeholders to access and analyze the data from their respective perspectives, based on their roles and responsibilities.

Through these processes, I harnessed the capabilities of SSAS to transform raw data into meaningful information, empowering users to gain valuable insights and make informed decisions based on the summarized and insightful analysis provided by the analysis cubes.

e. Creating Dashboard Visualizations:
To effectively present the analyzed data and address the analytical challenges at hand, I seamlessly integrated Power BI with the previously developed analysis cubes. This integration allowed me to harness the powerful visualization capabilities of Power BI and create compelling and interactive dashboards.

By connecting Power BI to the analysis cubes, I gained access to the summarized and insightful data, which served as the foundation for designing meaningful visualizations. I leveraged Power BI's wide range of visualization options, including charts, graphs, tables, and maps, to effectively communicate trends, patterns, and key insights derived from the data.

Using a user-friendly interface, I designed intuitive dashboards that presented the data in a visually appealing and interactive manner. These dashboards enabled end-users, including sales managers and other stakeholders, to easily explore and analyze the data, gain valuable insights, and make informed decisions.

I customized the visualizations based on the specific requirements of the analytical problems I aimed to solve. This involved selecting the appropriate chart types, configuring filters and slicers for data segmentation, and creating drill-down capabilities to explore the data at various levels of detail.

Furthermore, I incorporated interactive features such as tooltips, highlighting, and drill-through actions to enhance the user experience and provide additional context and details when interacting with the visualizations.

Overall, by integrating Power BI with the analysis cubes, I successfully transformed complex data into visually engaging and insightful dashboards. These dashboards provided a powerful tool for decision-makers to explore the data, uncover trends, and make data-driven decisions to address the analytical challenges and drive business success. The visuals displayed below provide examples of some of the visualizations created.

Figure 3: Sales Analysis
![image](https://github.com/okwoli200/Sales-Analysis/assets/99350558/5a8c5f5a-6a24-4f09-baaa-ee8e9f8458ea)

Figure 4: Tooltip Net Pay by Days
![image](https://github.com/okwoli200/Sales-Analysis/assets/99350558/edfff77c-3964-4157-beca-b362c1fbfcc5)


Figure 5: Customer Basket Analysis
![image](https://github.com/okwoli200/Sales-Analysis/assets/99350558/79c9e54e-0076-424f-b7d8-3bb9a4d41989)

