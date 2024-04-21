# ETL Pipeline for Grab Delivery Data Insights
A data engineering project on extracting and transform dataset from a kaggle dataset on 16000 grab restaurant analysis

This project for the Grab Delivery Data Insights ETL Pipeline, which is a crucial component of the data engineering responsibilities within the Junior Data Engineer Program. The primary objective of this pipeline is to facilitate the extraction, transformation, and loading (ETL) process of Grab delivery data. By focusing on data engineering tasks, this project aims to enable comprehensive analysis of establishment locations and cuisine diversity. The ultimate goal is to identify underserved areas and potential expansion opportunities for both business owners and food delivery services. The dataset utilized for this project is sourced from Kaggle.com

## Team project participated by :
Hassan Hosain, Hong Eng, Sailaja ,Rosni

## Tools used for this project:
- Python version 3.11 or higher (Jupyter)
 - Postgresql 
 - VS code 
 - Git /GitBash
- Github 
- Power BI 
- Canva

## Python Libraries used in this project :

- Pandas : used for data manipulation and analysis in Python.
  
- SQLAlchemy: for SQL database interaction and management.​

- Nbformat: for working with Jupyter Notebook file formats.​

- NumPy: for numerical computing, particularly for handling arrays and matrices.​

- Ast: for parsing Python abstract syntax trees (AST).​

- Json_normalize: for normalizing semi-structured JSON data into a flat table.​

- Psycopg2: for interacting with PostgreSQL databases from Python.​

- Re:  for regular expression operations in Python.​

- Folium: for creating interactive maps in Python, particularly with Leaflet.js.​

- Seaborn: used for statistical data visualization in Python.

## Extraction :
The first step involved extracting data by reading API from kaggle dataset on 16000 Grab Restaurants. The dataset was extracted into CSV format.  

Extraction was done via a KaggleApi() to download the csv dataset from the 16000-grab-restaurants-in-singapore kaggle dataset. 

## Transformation :

- During the transformation phase, maintaining data quality and consistency was paramount, aligning with fundamental principles of data engineering.
- Ensured data quality and consistency throughout transformation phase
- Divided team to tackle transformation of four dataset segments
- Implemented cleaning, normalization, and formatting procedures
- Key tasks included reconciling variations in naming conventions across team members' code implementations, thereby enforcing uniformity and consistency in data processing.
- This approach not only optimized the transformation workflow but also upheld data integrity, a core concern in data engineering practices.

### establishment_df (Saila)
- Data Cleaning on 'address' column. 
- Which involved data inspection, Data correction, Data standardization and Data transformation.
  
- Removed duplicates - the address column values were keyed in together with the establishment name separated by "-".

- Standardized the wordings - values had inconsistent cases. Example : 'Vivocity' , 'VivoCity'. 

- Inconsistent entry - for the same address that was entered inconsistently. Example: 'Vivocity', 'Vivo City' , 'Vivocity Shopping mall'.
  
- Filtered and transformed the address entries to avoid unnecessary distinct values.
  
- The distinct values were successfully reduced  from original 4883 to 3971.
  
- Standardization is currently limited to the alphabet 'a'. Moving forward, more comprehensive cleaning efforts are necessary to enhance address standardization, allowing for better categorization and grouping. 


  
  ![Screenshot 2024-04-02 235240](https://github.com/Kahanee/Grab_ETL_and_Analysis/assets/123168455/24285af8-1ffd-4dc8-a202-0d4877aa038d)

## Load :
Utilized and verified two methodologies for loading our DataFrame into pgAdmin database using the sqlalchemy ( Python Library)

PostgreSQL was selected as the relational database management system (RDBMS) for its robust architecture and efficient querying capabilities, aligning 
with data engineering requirements.


![Screenshot 2024-04-03 072225](https://github.com/Kahanee/Grab_ETL_and_Analysis/assets/123168455/7c36b0f0-55bb-480f-940d-317fa822a769)


## ERD / Database Schema :

![Screenshot 2024-04-02 065846](https://github.com/Kahanee/Grab_ETL_and_Analysis/assets/123168455/794be18b-f502-47a9-b775-2be87334311b)


## Transformation by Team members:

### cuisine_df:	(by Hassan)  

- Selected columns id_source, cuisine from the main dataframe to be transformed into a new dataframe cuisine_df. 

- Data Cleaning of null values in the cuisine category and replaced the values. 

- Cleaned up the cuisine column to remove commas, apostrophes, [] and set it lower case. 

- Sorted the cuisine columns in alphabetical order A-Z. 

- Exploded the cuisine category into multiple columns i.e. cuisine_1, … , cuisine_5. 

- Created a new primary key called cuisine_id as cus_1, cus_2 .. etc.
  
- Did a check to explore the top 3 popular cuisine category. 

### deliver_df : (by Rosni)

- Selected the following column from the main data frame : id_source, delivery_cost,radius, delivery_options , promo. 

- In the promo columns, all the missing values are replaced by the string “no promotion available”. 

- There were test restaurants with no names, so these rows were dropped.. 
- Split the delivery column into 3: delivery, take away and dine in.

- Added 3 columns with boolean values False. 

- Checked if the delivery column contained the words ’delivery’,’take’, ‘dine’ using .stri.contains( ) function. 

- Using .loc on corresponding column,  update to True if the words were present. 

- New index added which will act as primary key

### openinghour_df: (by Hong Eng)

- Subsetting opening hours column. 

- Cleaning opening_hours which consisted JSON objects/ dictionaries. 

- Expanded the dictionaries into 10 separate columns: 

- Using ast module’s ast.literal_eval function to ensure that the column is in a proper list of dictionaries format. 

 - Using json_normalize function to convert the dictionaries into separate columns. 

- Added index column with prefix. 

- Set new index column to be the first column. 

- Investigated null/NaN values and replaced with relevant values. 

- There were 12849 - 7155 = 5694 establishments with open==NaN and tempClosed==NaN. 

- Based on checking on first 5 establishments at time of interim project, they are currently open, meaning they were not permanently closed at time of dataset. Therefore, for sake of analysis in our project, it is assumed that all entries with open=NaN and tempClosed=NaN are not closed permanently and therefore included in the analysis of the dataset. 

### Analysis using python libraries (Seaborn , matplotlib)
![Screenshot 2024-04-03 082558](https://github.com/Kahanee/Grab_ETL_and_Analysis/assets/123168455/76efb994-7d80-452c-a311-be3a3f73b474)





![Screenshot 2024-04-03 082632](https://github.com/Kahanee/Grab_ETL_and_Analysis/assets/123168455/938a259c-dc9a-49d4-a756-0b033ff654c3)
4-a1c9-6d524f6ad050)


### Link to intrim project ppt at canva  

https://www.canva.com/design/DAGBKTv81AQ/NU_B_3Db1EL5hFlgIMxJVA/edit?utm_content=DAGBKTv81AQ&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
