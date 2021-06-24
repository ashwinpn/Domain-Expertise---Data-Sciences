# Domain-Expertise---Data-Sciences
Domain Expertise - Data Sciences

# Libraries/Packages learned
- AIF 360
- Fairlearn
- SHAP
- LIME

# SQL [Relational and BigQuery]
First Normal Form - No repeating groups OTHERWISE would lead to large rows, wasted space
Second Normal Form - Each column must depend on the entire primary key OTHERWISE redundancy
Third Normal Form - Each column must depend directly on the primary key OTHERWISE data redundancy and update nighmare

Insertion anomaly - The primary key cannot be NULL
Deletion anomaly - We cannot delete an item without losing other valulable information 
Update anomaly - While updating an item we have to update details for every row


1] BigQuery

from google.cloud import bigquery
client = bigquery.Client()
dataset_ref = client.dataset("hacker_news", project="bigquery-public-data")
dataset = client.get_dataset(dataset_ref)
tables = list(client.list_tables(dataset))
for table in tables:
	print(table.table_id)

table_ref = dataset_ref.table("full")
table = client.get_table(table_ref)

table.schema [name, field type, mode, description]

# bigquery has a rowIterator object
# convert to pandas DataFrame object
client.list_rows(table, max_results = 5).to_dataframe()

2] SELECT. FROM, and WHERE

3] Estimate the size of a query
# dry_run = True
# maximum_bytes_billed IN safe-config
# AND set job_config = safe_config

4] GROUP BY, HAVING AND COUNT
- COUNT(column_name)
- Aggregate function: COUNT,SUM,MIN,MAX,AVG
- GROUP BY takes the name of one or more columns, and treats all rows with the 
same value in that column as a single group when you apply aggregate functions like COUNT()
- HAVING is used in combination with GROUP BY 
to ignore groups that don't meet certain criteria.

5] Aliasing - AS
6] Unsure of what to put within count - COUNT(1)
7] ORDER BY is usually the last clause in your query, 
and it sorts the results returned by the rest of your query
- DESC : descending
- EXTRACT(DAY FROM DATE)
8] 
A common table expression (or CTE) is a temporary table that you return within your query. 
CTEs are helpful for splitting your queries into readable chunks, 
and you can write queries against them.
# WITH x AS (QUERY1) QUERY2
- As you can see, common table expressions (CTEs) let you shift a lot of your data cleaning into SQL. 
That's an especially good thing in the case of BigQuery, because it is vastly faster than doing the work in Pandas.
9] 
FROM + AS
INNER JOIN + AS
# LEFT JOIN / RIGHT JOIN / 

# Notebook2 - Restaurants and Health Inspections
![](https://github.com/ashwinpn/Domain-Expertise---Data-Sciences/blob/main/assets/Manhattan_before.png)

# Notebook4 - LIME
![](https://github.com/ashwinpn/Domain-Expertise---Data-Sciences/blob/main/assets/Feature_importance_LIME.png)
![](https://github.com/ashwinpn/Domain-Expertise---Data-Sciences/blob/main/assets/Local_explanation_LIME.png)
