# Optimizing Supplier Quality and Downtime Reduction through Data Analytics for Enterprise Manufacturers Limited

# Project Overview:
## Background:
Enterprise Manufacturers Limited is on a mission to revamp their procurement processes and ensure top-notch quality of raw materials from their various vendors across different plants. With no standardized procurement system in place, the company has been facing issues with vendor performance, plant operations, and process efficiency. However, the company has recently collected valuable data on material, vendor, plant location, defect quantity, and downtime caused by defective materials.

The main goal of this project is to dive into the consolidated data and extract crucial insights regarding supplier quality and operational downtime. By making use of Power BI for data visualization, the project aims to provide actionable insights that will empower management to make well-informed decisions, leading to increased revenue, reduced costs, and enhanced process efficiency

## Objectives:
1. Identify Poor-Performing Vendors and Plants: Analyze which vendors and plants are associated with the highest quantity of defective materials and the most downtime, to help focus improvement efforts.
2. Vendor-Material Analysis: Determine if specific combinations of vendors and materials consistently lead to poor performance, enabling more strategic procurement decisions.
3. Plant-Vendor Relationship: Identify how the same vendors and materials perform across different plants, and pinpoint any discrepancies in performance that could impact efficiency.
4. Downtime Impact Assessment: Analyze the value of downtime caused by defective materials, and identify the vendors and plants that contribute the most to operational inefficiencies and cost overruns.
5. Propose Solutions: Provide data-driven recommendations for improving procurement processes, including identifying poor-performing vendors, improving supplier relationships, and minimizing downtime, ultimately driving cost savings and operational improvements.
   
## Key Questions:
Here are the burning questions that will guide the project and meet the expectations of the company stakeholders:

- Which vendors and plants are causing the greatest defect quantity?
- Which vendors and plants are causing the greatest downtime?
- Are there specific combinations of materials and vendors that perform poorly?
- Are there specific combinations of vendors and plants that result in poor performance?
- How do the same vendor and material perform across different plants?

# Data Description 
The dataset consists of 5,226 rows and 9 columns. Here's a breakdown of the columns:

1. Date: The date of recording defects and downtime
2. Vendor: The supplier of the materials
3. Plant Location: The geographical location of the production facility
4. Category: The classification of the materials supplied
5. Material Type: The type of material supplied
6. Defect Type: The severity of the defect in the material (e.g., Impact, No Impact, Rejected)
7. Defect: A summary of the flaw in the material
8. Total Defect Quantity: The quantity of defective material received
9. Total Downtime Minutes: The duration of plant inactivity due to defective materials
    
# Data Normalization:
The dataset was in good shape, but I optimized it by creating dimension tables and a fact table for better performance, organization, and analysis.

The dimensions table held categorical data which helped to describe the business processes or events which will be represented in the fact table. The first step involved duplicating the original table, Supplier Quality, six times. Each of the duplicated tables was uniquely renamed using identifiers such as Vendor, Plant, Category, Material Type, Defect, and Defect Type. Then, in the Vendor table, the column relevant to the dimension was selected using the choose-columns feature. Thereafter, duplicates were removed using the remove-duplicates feature to retain unique data. Finally, the primary key was created by using the add-column feature to add an index column starting from 1. The primary key was renamed to the ID version of the categorical column, such as VendorID. The data type was changed to the text data type. This process was repeated in the Plant, Category, Material Type, Defect, and Defect Type tables. 

After the successful creation of the dimension tables, the final stage in this data normalization step is to create the fact table. The fact table is the central table that contains quantitative data about business processes. They are typically numeric values and contain foreign keys that link to dimension tables. The first step in the creation of the fact table is to use the merge-queries-as-new feature to merge the Supplier Quality table with the Vendor table. In the merge tab, the Vendor column was selected on both tables and joined using the inner join kind. The new merged query was renamed as Supplier Fact. The new column added to the fact table was expanded to select the foreign key, VendorID. This process was repeated by using the merge-queries feature to merge the Plant, Category, Material type, Defect, and Defect type to the fact table. The foreign keys were changed to the text data type.  Finally, only the following columns were retained: Date, Total defect quantity, Total downtime minutes, and the columns associated with the foreign keys.

The date table was created using a DAX measure for time intelligence calculations and the date column was marked as a date table using table tools. The date table is an important step for enabling time intelligence calculations, such as month-over-month (MoM), year-over-year (YoY), or cumulative totals. 

# Data Modelling:
The data modeling process involved connecting primary keys in the dimension tables to foreign keys in the fact table using the one-to-many cardinality to achieve a star schema model. 
