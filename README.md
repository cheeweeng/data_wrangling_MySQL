## 🧮 Service User Feedback Analysis
This [repository](https://github.com/cheeweeng/data_wrangling_MySQL) contains the code and documentation submitted in March 2025 for Data Wrangling assignment at the Singapore University of Social Sciences (SUSS). 
The assignment focuses on importing, transforming, and analysing survey data collected from users of public services provided by four organisations.

## 🛠️ Technologies Used  
Language: SQL (MySQL) 

## 🎯 Project Objective
Import survey data collected from 4,858 users across four public-funded organisations.

Clean and enhance the data:

1. Replace numerical codes with human-readable labels.

2. Convert date codes (days since 9 Aug 1965) into MySQL DATE format.

3. Optimise the table for efficient storage using appropriate ALTER TABLE statements.

4. Generate summary tables to uncover meaningful relationships in the dataset.

5. Explain insights through commentary based on SQL outputs.

To map the numeric values with their corresponding text labels according to the data dictionary, CASE statements were used in SQL query in Table Plus. The transformed columns are ‘urgency’ , ‘subsidy’, ‘gender’, ‘coordinated’, ‘similarity_to_ideal’ and ‘willingness_to_recommend’.    

![Image](https://github.com/user-attachments/assets/ebcf333c-de10-4c92-9c99-f033e4dc3a37) For the ‘urgency’ variable, when the value is 1,  
then the corresponding text label is ‘P1’ so on and so forth.



Tools: MySQL Server, MySQL Workbench, Microsoft Word  
## 📊 Summary Tables
Two summary tables are generated using GROUP BY queries to explore relationships such as:

Recommendation likelihood vs. perceived coordination

Age group & gender-based vs. perceptions of services

Each table is accompanied by a brief interpretation in the main report.
