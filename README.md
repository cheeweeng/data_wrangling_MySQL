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

  <div style="display: flex; align-items: flex-start;">
  <img src="https://github.com/user-attachments/assets/ebcf333c-de10-4c92-9c99-f033e4dc3a37" alt="Image" width="200" style="margin-right: 10px;">
  <div>
    <strong>For the ‘urgency’ variable</strong>, when the value is <code>1</code>, then the corresponding text label is <code>P1</code>, and so on and so forth.
  </div>
</div>







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

