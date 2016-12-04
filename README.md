# HDP_Test_Q3
# Out put data of hadoop question 3

Find out each employee who have had a lateral or vertical movement in their career and provide their EmpID, Name, Old_designation, Old_dept, New_designation, New_dept. Please upload the final CSV along with the code and jar files(if any) to your github and provide the link below.

# Result:

To get the above required out put records we have used HIVE, and the  query to get such employee who has old department, old designation, and new department and new desgnation from avaialble data in deifferent tables.

to get the output here reuired to get the data from multiple tables for here performed left join on tables in query on emp.no column and the required columns from such tables.

Here get the employee record from available tables from where the reqired department, designation information captured using one query.

# I have used below Query:

hive> INSERT OVERWRITE LOCAL DIRECTORY '/home/vishnu/Documents/Q3_output_csv' SELECT de.emp_no,d.dept_name,t.title,e.first_name,e.last_name,de.from_date,de.to_date FROM dept_emp as de left join departments d on(d.dept_no = de.dept_no) left join employees e on (de.emp_no = e.emp_no ) LEFT JOIN titles t  on (t.emp_no = e.emp_no) WHERE e.emp_no IN (SELECT emp_no FROM dept_emp GROUP BY emp_no HAVING COUNT(*) >1) ORDER BY de.emp_no,de.from_date;



The Query and the terminal actual execuation uloaded/provided in text file for more details.

# Here for Q3, I have genrated output in following format:

empolyee_no department designation first_name last_name from_date to_date

Here I have shown old designation,old department,new designation,new department in multiple record format except in one row i.e Following two records from output is for the same user.

In following output the user 10010 having first record as department:prodution its his old department & the second record as department: Quality Management its his current department.in this patteren I have shown result.

10010�Production�Engineer�Duangkaew�Piveteau�1996-11-24�2000-06-26 10010�Quality Management�Engineer�Duangkaew�Piveteau�2000-06-26�9999-01-01



** Added Directroy , File details as:

1. "Q3_Output_CSV" under this directroy I have exported the used query result  in CSV file "000000_0"
2. "Q3quearyandterminaloutput" file added with the actual terminal result along with query and map reduce execuation details.




