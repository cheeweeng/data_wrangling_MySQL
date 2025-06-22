## 🧮 Service User Feedback Analysis
This [repository](https://github.com/cheeweeng/data_wrangling_MySQL) contains the code and documentation submitted in March 2025 for Data Wrangling assignment at the Singapore University of Social Sciences (SUSS). 
The assignment focuses on importing, transforming, and analysing survey data collected from users of public services provided by four organisations.

## 🛠️ Technologies Used  
Language: SQL (MySQL)   
Tools: MySQL Server, MySQL Workbench, Microsoft Word  

## 🎯 Project Objective
Import survey data collected from 4,858 users across four public-funded organisations.

Clean and enhance the data:

1. Replace numerical codes with human-readable labels.

2. Convert date codes (days since 9 Aug 1965) into MySQL DATE format.

3. Optimise the table for efficient storage using appropriate ALTER TABLE statements.

4. Generate summary tables to uncover meaningful relationships in the dataset.

5. Explain insights through commentary based on SQL outputs.

# Code explained:
To map the numeric values with their corresponding text labels according to the data dictionary, CASE statements were used in SQL query in Table Plus. The transformed columns are ‘urgency’ , ‘subsidy’, ‘gender’, ‘coordinated’, ‘similarity_to_ideal’ and ‘willingness_to_recommend’.    

  
# Code explained:
To map the numeric values with their corresponding text labels according to the data dictionary, CASE statements were used in SQL query in Table Plus. The transformed columns are ‘urgency’, ‘subsidy’, ‘gender’, ‘coordinated’, ‘similarity_to_ideal’, and ‘willingness_to_recommend’.    


# Code explained:
To map the numeric values with their corresponding text labels according to the data dictionary, CASE statements were used in SQL query in Table Plus. The transformed columns are ‘urgency’, ‘subsidy’, ‘gender’, ‘coordinated’, ‘similarity_to_ideal’, and ‘willingness_to_recommend’.

<div style="display: block; margin-bottom: 20px;">
  <img src="https://github.com/user-attachments/assets/ebcf333c-de10-4c92-9c99-f033e4dc3a37" alt="Urgency Mapping" width="200" style="display: block; margin-bottom: 10px;">
  <p><strong>For the ‘urgency’ variable</strong>, when the value is <code>1</code>, then the corresponding text label is <code>P1</code>, and so on and so forth.</p>
</div>

<div style="display: block; margin-bottom: 20px;">
  <img src="https://github.com/user-attachments/assets/8d4c3e21-f5d9-4e2e-8fc1-025c7c94c21f" alt="Subsidy Mapping" width="220" style="display: block; margin-bottom: 10px;">
  <p>For ‘subsidy’ variable, when the value is <code>1</code>, then the corresponding text label is <code>Y</code>, so on and so forth.</p>
</div>

<div style="display: block; margin-bottom: 20px;">
  <img src="https://github.com/user-attachments/assets/e9c1f81e-871a-4f2b-9b11-066d664d70a5" alt="Coordinated Mapping" width="220" style="display: block; margin-bottom: 10px;">
  <p><strong>For ‘coordinated’ variable</strong>, when the value is <code>1</code>, then the corresponding text label is <code>Never</code>,</p>
  <p>when value is <code>2</code>, then <code>Sometimes</code>, so on and so forth.</p>
</div>
  <img src="https://github.com/user-attachments/assets/cdbdf3c5-04aa-40ca-b40c-5efe05c24488" alt="Image" width="220" style="display: block; margin-bottom: 15px;">  
    <div>
      For the similarity_to_ideal variable, the valid values are in numeric 0 – 10. The CASE statement was used to map when the value is 11, then the corresponding text label is ‘Unsure’ and ‘NA’ when the value is 999. In the query, “ELSE similarity_to_ideal” tells MySQL to keep 0-10 as is if the value is not 11 or 999.
    </div>
  <img src="https://github.com/user-attachments/assets/44f19bde-3361-4c55-a85f-a9b64d900182" alt="Image" width="220" style="display: block; margin-bottom: 15px;">
    <div>
      For the willingness_to_recommend variable, when the value is 1, then the corresponding text label is ‘Definitely No’, </div>
      <div>when value is 2, then ‘Probably No’, so on and so forth.
    </div>
</div>
      
## Convert org_date to calendar date variable    
      
The ‘org_date’ column was converted into a calendar date variable named ‘caldate’ using DATE_ADD() function.  
<img src="https://github.com/user-attachments/assets/68d35be7-e555-473e-9d89-37e4374d2829" alt="Image" style="display: block; margin-bottom: 15px;">
<div>According to the data dictionary, the ‘org_date’ shows the “Number of days since 9 Aug 1965”. This means the base date is 1965-08-09 and the numeric values in each field shows the number of days since the base date. Using DATE_ADD() function, this code convert the column into a DATE type.</div>

The numeric values in the identified columns have been mapped to their corresponding text labels and a new column named ‘caldate’ with MySQL DATE type ‘2022-04-01’ has been added.   
<img src="https://github.com/user-attachments/assets/b00fbf66-8850-433a-9cf7-cb45734cbfa5" alt="Image" style="display: block; margin-bottom: 15px;">
<div></div>  

## Optimise the table for efficient storage  

The DESCRIBE TMA_data_labelled statement must be run separately from the ALTER TABLE query and the result is as follows:
<img src="https://github.com/user-attachments/assets/c5f00572-2aba-4694-b85b-e52ab99fb37c" alt="Image" style="margin-right: 15px;">  

The ALTER TABLE statement was used to modify the data type in order to save storage space while not losing any information.  
The valid values in column ‘org’ are ‘Org A’ to ‘Org D’, the maximum length is 5. Hence, using VARCHAR(5) is optimal   
The valid values in column ‘dept’ are ‘Dept 1 to ‘Dept 3’, the maximum length is 6. Hence, using VARCHAR(6) is optimal   
The valid values in column ‘subsidy’ are ‘Y’ and ‘N’. using CHAR(1) is more storage-efficient than VARCHAR for single-character field.  
For the ‘age’ variable, tinyint UNSIGNED was used as UNSIGNED ensures that it only holds non-negative values. In the data dictionary, the valid values of age variable are “any integer greater than zero”.  
The caldate variable is assigned the DATE type.  
The valid values in column ‘gender’ are ‘M’ and ‘F’. hence, using CHAR(1) is more storage-efficient than VARCHAR for single-character field.  
In the ‘coordinated’ variable, the maximum length of the valid values is ‘Sometimes’, which is 9 characters, hence VARCHAR(9) was applied.  
In the ‘similarity_to_ideal’ variable, the maximum length of the valid values is ‘Unsure’, which is 6 characters, hence VARCHAR(6) was applied.  
For the ‘willingness_to_recommend’ variable, the maximum length of the valid values is ‘Definitely Yes’, which is 14 characters, hence VARCHAR(14) was applied.  




## 📊 Summary Tables
Two summary tables are generated using GROUP BY queries to explore relationships, each table is accompanied by a brief interpretation in the main report.

## Summary table #1 – Coordination influenced Willingness to Recommend.  
This table investigate how the coordination level among the different parts of the organisation (measured by the column ‘coordinated’) influenced users’ willingness to recommend the services. I also tracked the result by each year so as to see the trend over time.  
![Image](https://github.com/user-attachments/assets/4ff1267c-5f42-4f61-a57f-e709b45c7a1c)  
The results revealed that when different parts of the organisations are coordinated (shown as ALWAYS), the average willingness score (which is average willingness_to_recommend) are the highest over the two surveyed year in 2022 and 2023.  
On the other hand, when the different parts of the organisations are not coordinated (shown as NEVER), the average willingness score are the lowest (2.24 in 2022 and 2.52 in 2023).
As willingness to recommend can be linked to users’ satisfaction level, this table revealed that better coordination among different parts and departments correlates to the willingness_to_recommend score among users. There were not significant differences among the score for each coordinated category in each year.  
This query provides actionable insights into the relationships between the coordination level among different departments and the users’ willingness_to_recommend and helping the organisation make data-driven decisions.

## Summary table #2 – Age Group and Gender based perception of services
This table investigate the average similarity_to_ideal score among users of various age groups and by their genders.  
![Image](https://github.com/user-attachments/assets/a0259048-42eb-429a-b844-f80eed034c3a)  
The results reveal how the different age groups and genders influence their perception of the services rendered by the organisations relative to their ideal. Generally the average similarity to ideal scores are quite high, suggesting the services rendered are relatively close to the perception of the users. However, if we zoomed in further, the lower age groups have higher scores than the older age groups. This could suggest that younger users have lower expectations than their older peers.  
Across the different age groups, the differences in the scores between genders are rather small, and quite insignificant. This could suggest that the services provided by the organisations are not gender-specific.  

