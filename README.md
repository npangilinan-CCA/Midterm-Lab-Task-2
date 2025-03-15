# [Midterm Lab Task 2 - Data Cleansing and Preparation using Power Query](https://github.com/user-attachments/files/19259702/Book1.xlsx)
For this task we are given an uncleaned raw data from Excel and we are tasked to perform Data CLeaning and Preparation using Power Query

### Step 1: Download and Load Data  
1. Download the dataset (Uncleaned_DS_jobs.csv)  
2. Open Excel  
3. Go to Data → New Query → Open File → Text/CSV  
4. Click Load and then Edit using Power Query Editor  

### Step 2: Duplicate Raw Data  
1. Right-click the dataset in the Queries pane  
2. Select Duplicate  

### Step 3: Clean Salary Data  
1. Select the Salary Estimate column  
2. Go to Transform Menu → Extract → Text Before Delimiter  
3. Type "(" and click OK  
4. Create two new columns: Min Salary and Max Salary  
   - Select Salary Estimate column → Add Column Menu → Column from Examples → From Selections  
   - Type the first min salary value and press Enter (all rows will auto-fill)  
   - Rename the column to "Min Sal"  
   - Repeat the process for Max Salary  

### Step 4: Add Role Type Column  
1. Go to Add Column Menu → Custom Column  
2. Rename the column to "Role Type"  
3. Use this logic:  
   - If Job Title contains "Data Scientist" → Assign "Data Scientist"  
   - If Job Title contains "Data Analyst" → Assign "Data Analyst"  
   - If Job Title contains "Data Engineer" → Assign "Data Engineer"  
   - If Job Title contains "Machine Learning" → Assign "Machine Learning Engineer"  
   - Otherwise, assign "Other"  
4. Change the column type to Text  

### Step 5: Split Location Column  
1. Select the Location column  
2. Add a Custom Column with corrections:  
   - If Location = "New Jersey" → Assign ", NJ"  
   - If Location = "Remote" or "United States" → Assign ", Other"  
   - If Location = "Texas" → Assign ", TX"  
   - If Location = "California" → Assign ", CA"  
3. Click OK, then select the new column  
4. Go to Transform → Split Column → By Delimiter (comma ",")  
5. Click OK  
6. Rename the second split column to "State Abbreviations"  
7. Check and replace incorrect values (e.g., "Anne Rundell" → "MA")  

### Step 6: Split Size Column  
1. Create two new columns: MinCompanySize and MaxCompanySize  
2. Use the same method as Salary Estimate to split values  

### Step 7: Handle Negative Values  
1. Filter out -1s from the Competitors column  
2. Filter out 0s from the Revenues column  
3. Remove -1s from the Industry column  

### Step 8: Clean Company Names  
1. Remove any extra characters or ratings after company names  

### Step 9: Copy Cleaning Steps as Proof  
1. Go to Home Menu → Click Advanced Editor  
2. Copy and save the code in your portfolio  

## Here's the Output for Part 1
<!-- Uploading "duplicate.PNG"... -->

### Step 10: Reshape and Group Data  
#### Group by Role Type  
1. Duplicate the raw data → Rename it as "Sal By Role Type dup"  
2. Select only Role Type, Min Salary, and Max Salary columns  
3. Change Min and Max Salary type to currency  
4. Multiply values by 1000 (Numbers Column → Standard → Multiply → Type 1000)  
5. Group rows by Role Type and get the average for Min and Max Salary  

#### Group by Company Size  
1. Create a reference of raw data → Rename it as "Sal By Role Size ref"  
2. Select only Size, Min Salary, and Max Salary columns  
3. Change Min and Max Salary type to currency  
4. Multiply values by 1000  
5. Group rows by Size and get the average for Min and Max Salary  


### Step 11: Merge State Mapping  
1. Click Unclean DS Jobs  
2. Right-click in the Queries pane → New Query → Open Workbook State Mapping  
3. Select the columns and click OK  
4. Select Uncleaned DS Jobs query  
5. Choose the State Abbreviation column in both queries  
6. Click Merge → Click OK  
7. Rename the merged column as "State Full Name"  
8. Remove nulls and blanks  



### Step 12: Group by State  
1. Create a reference of raw data → Rename it as "Sal By State ref"  
2. Select only State Full Name, Min Salary, and Max Salary columns  
3. Change Min and Max Salary type to currency  
4. Multiply values by 1000  
5. Group rows by State Full Name and get the average for Min and Max Salary  



### Step 13: View Query Dependencies  
1. Go to View Menu → Click Dependencies  
2. Check if all queries are correctly linked
## Here's the screenshot of my output before I started data cleaning
![Image](https://github.com/user-attachments/assets/c45e215d-debc-473f-807a-f3eed521d884)
## Here's the screenshot of my output after I started data cleaning 
![Image](https://github.com/user-attachments/assets/f03d5f75-0315-4d61-8040-d717a165b44c)
## Here's my Uncleaned_DSjobs Duplicate
![Image](https://github.com/user-attachments/assets/35564e0b-8ae7-4851-b7ff-5b9fc4718bf4)
## Here's my Advanced Editor
![Image](https://github.com/user-attachments/assets/390429fd-15ac-421e-9d21-5b073b8ae9ce)
## Here's my Sal By Role Type dup
![Image](https://github.com/user-attachments/assets/7f7c1b37-b44b-44d0-9c12-128976f893b5)
## Here's my Sal By Role Size ref
![Image](https://github.com/user-attachments/assets/8af980b1-11f4-42a6-9326-3bcfbea04f8a)
## Here's my Sal By State ref
![Image](https://github.com/user-attachments/assets/2f223eaf-3336-4a05-86fc-670de58e3000)
## Here are the Query Dependencies
![Image](https://github.com/user-attachments/assets/bf7b5f5f-357f-4a53-9954-818d9c1edd19)
