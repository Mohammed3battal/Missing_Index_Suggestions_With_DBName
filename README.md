## Script: Top 20 Missing Index Suggestions with Database Name

**Description**:
This script queries SQL Server's missing index DMVs to identify the top 20 recommended indexes across all databases. It calculates an estimated improvement score and generates dynamic `CREATE INDEX` statements for each entry.

**Columns Returned**:
- `runtime`: Time when the query was executed
- `DatabaseName`: The database where the index is missing
- `estimated_improvement`: A relative score indicating the potential performance gain
- `create_index_statement`: Auto-generated T-SQL command to create the missing index

**How estimated_improvement is calculated**:
```sql
avg_total_user_cost × avg_user_impact × (user_seeks + user_scans)
