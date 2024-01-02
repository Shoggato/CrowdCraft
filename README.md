# CrowdCraft: Unleashing Creative Campaigns

This project involves the extraction, transformation, and loading (ETL) of crowdfunding data into a structured relational database. The data includes information about crowdfunding campaigns, contacts, categories, and subcategories.

## Data Sources

### Crowdfunding Data
The crowdfunding data is sourced from an Excel file (`crowdfunding.xlsx`) containing information about various crowdfunding campaigns. The data includes details such as campaign ID, company name, goal, pledged amount, outcome, country, currency, launch date, deadline, and more.

### Contacts Data
Contact information is sourced from an Excel file (`contacts_original.xlsx`). The file includes details about individuals involved in the crowdfunding campaigns, such as contact ID, first name, last name, and email address.

## Data Processing

### Crowdfunding Data Processing
The `crowdfunding.xlsx` data is read into a Pandas DataFrame in Python. The DataFrame is then processed to create separate DataFrames for categories and subcategories. Unique category and subcategory IDs are generated and assigned. The processed data is exported to CSV files (`category.csv` and `subcategory.csv`). The main campaign data is cleaned, converted to appropriate data types, and merged with category and subcategory information. The final cleaned campaign data is exported as `campaign.csv`.

### Contacts Data Processing
The `contacts_original.xlsx` data is read into a Pandas DataFrame in Python. The DataFrame is processed to extract contact details, including first name, last name, and email address. The processed data is exported as `contacts.csv`.

## Database Schema

The relational database schema includes four tables:

1. **subcategory:**
   - subcategory_id (Primary Key, VARCHAR)
   - subcategory (VARCHAR)

2. **category:**
   - category_id (Primary Key, VARCHAR)
   - category (VARCHAR)

3. **contacts:**
   - contact_id (Primary Key, INT)
   - first_name (VARCHAR)
   - last_name (VARCHAR)
   - email (VARCHAR)

4. **campaign:**
   - cf_id (Primary Key, INT)
   - contact_id (Foreign Key referencing contacts(contact_id), INT)
   - company_name (VARCHAR)
   - description (VARCHAR)
   - goal (FLOAT)
   - pledged (FLOAT)
   - outcome (VARCHAR)
   - backers_count (INT)
   - country (VARCHAR)
   - currency (VARCHAR)
   - launched_date (DATE)
   - end_date (DATE)
   - category_id (Foreign Key referencing category(category_id), VARCHAR)
   - subcategory_id (Foreign Key referencing subcategory(subcategory_id), VARCHAR)

## Usage

1. **Crowdfunding Data Processing:**
   - Run the Python script to process the crowdfunding data and export CSV files.
   ```bash
   python process_crowdfunding_data.py
    ```
2. **Contacts Data Processing:**
   - Run the Python script to process the contacts data and export the CSV file.
  ```bash
  python process_contacts_data.py
  ```
3. **Data Import:**
   - Execute the SQL script ('database_schema.sql') to set up the database schema.
4. **Data Import:**
   - Use a database management tool or SQL command line to import the CSV files into their respective tables.

## Dependencies
* Python (>=3.6)
* Pandas
* NumPy

## Contributors
Erika Walker

## License
This project is licensed under the MIT License.
