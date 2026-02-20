Question 1. Q1: dbt run --select int_trips_unioned builds which models?
stg_green_tripdata, stg_yellow_tripdata, and int_trips_unioned
dbt will build the requested model and all its dependencies.

Question 2. Q2: New value 6 appears in payment_type. What happens on dbt test?
dbt fails the test with a non-zero exit code
If the test is checking accepted enum values and a new unhandled value appears, dbt fails the test (not skip).

Question 3. Q3: Count of records in fct_monthly_zone_revenue?
12,998

```sql
SELECT COUNT(*) FROM analytics-engineering-487514.dbt_bgomes.fct_monthly_zone_revenue;
```

Question 4. Q4: Zone with highest revenue for Green taxis in 2020?
Morningside Heights

```sql
SELECT zone
FROM analytics-engineering-487514.dbt_bgomes.fct_monthly_zone_revenue
WHERE taxi_type = 'green' AND year = 2020
ORDER BY revenue DESC
LIMIT 1;
```

Question 5. Q5: Total trips for Green taxis in October 2019?
350,891

```sql
SELECT SUM(trip_count)
FROM analytics-engineering-487514.dbt_bgomes.fct_monthly_zone_revenue
WHERE taxi_type = 'green' AND year=2019 AND month=10;
```

Question 6. Q6: Count of records in stg_fhv_tripdata (filter dispatching_base_num IS NULL)?
44,112,187

```sql
SELECT COUNT(*)
FROM analytics-engineering-487514.dbt_bgomes.stg_fhv_tripdata
WHERE dispatching_base_num IS NULL;
```
