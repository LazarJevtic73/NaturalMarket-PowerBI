# NaturalMarket-PowerBI

<img width="1273" height="707" alt="image" src="https://github.com/user-attachments/assets/c7ff5288-0490-43bf-a0d6-042938b11199" />


In this Power BI assignment, I handled the full data preparation and transformation workflow for Natural Market, a retail chain operating in the USA, Mexico, and Canada. The main goal was to clean, merge, and enrich multiple datasets so that they could support detailed reporting and analytics. Below is an overview of the main steps and techniques applied during the process.

Data Loading and Transformation

At the start, I imported all CSV files into Power BI and shaped them in the Power Query Editor. Each table was carefully inspected to verify data types and completeness. In the Customer table, I created a “full_name” column by combining “first_name” and “last_name.” I also derived the year from the “birthdate” column, producing a new “birth_year” field. Furthermore, I added a conditional column called “has_children,” which is “N” if “total_children” equals 0, and “Y” otherwise.

Within the Products table, I used statistical functions to count distinct brands and product names, resulting in 111 brands and 1,560 products. I then created a calculated column “discount_price” set to 90% of the retail price. Null values in the “recyclable” and “low-fat” columns were replaced with zeros.

For the Stores table, a “full_address” column was constructed by concatenating “store_city,” “store_state,” and “store_country,” separated by commas. Additionally, I extracted the prefix of the “store_phone” field (characters before the dash) into a new column called “area_code.”

In the Calendar table, I used the query editor’s date functions to add several time-related columns: Start of Week (Sunday-based), Day Name, Start of Month, Month Name, Quarter, and Year.

Finally, I merged the 1997 and 1998 datasets using a connected folder approach. All date fields were standardized to the MM/DD/YYYY format via the modelling tab, and all price and cost columns were formatted as currency.


Creating the Data Model

In the Relationships view, I linked the transaction table to the customer, product, and store lookup tables using primary and foreign keys. An active and inactive relationship was established between the transaction table and the calendar lookup table. Similarly, the return table was connected to the product, calendar, and store tables through primary and foreign keys.

I also connected the store table to the region lookup table, forming a snowflake schema. All relationships were configured as one-to-many, with filters flowing in a single direction toward the primary fact table. Finally, I ensured that all data tables were connected through shared lookup tables, rather than directly to each other, to maintain a clean and scalable model.

<img width="1080" height="700" alt="image" src="https://github.com/user-attachments/assets/a1b47376-6c96-4e0c-86da-d1a74cd916b6" />

