# Table Creation

## The script, create_tables.py, runs in the terminal without errors. The script successfully connects to the Sparkify database, drops any tables if they exist, and creates the tables.

Good work.
The create_tables.py runs without errors and creates all five tables if they don't exist.

## CREATE statements in sql_queries.py specify all columns for each of the five tables with the right data types and conditions.

Great job choosing the correct data type for most columns.

There are a few adjustments left:

Add NOT NULL constraints where necessary. Think of it as a column that we don't want to accept NULL values. For example, the columns user_id and start_time for songplays table. Can you think of other columns? For more info, check this link
If you set the songplay_id column as TEXT and use the index as its value, you'll end up with many duplicate values that are lost using the DO NOTHING clause.
Instead, you should set the songplay_id column as SERIAL. This data type is an auto-increment that will increase its value every time a new row is added. And it won't be necessary to pass a value to its INSERT anymore. If you want to learn more about it, check this link.
Set a primary key to the time table as well.

# ETL

## The script, etl.py, runs in the terminal without errors. The script connects to the Sparkify database, extracts and processes the log_data and song_data, and loads data into the five tables.

Since this is a subset of the much larger dataset, the solution dataset will only have 1 row with values for value containing ID for both songid and artistid in the fact table. Those are the only 2 values that the query in the sql_queries.py will return that are not-NONE. The rest of the rows will have NONE values for those two variables.

It’s okay if there are some null values for song titles and artist names in the songplays table. There is only 1 actual row that will have a songid and an artistid.

The etl.py runs without errors, however, as you might have noticed all rows in the songplays table have no values on the columns song_id and artist_id.

There should be one row in songplays with values on artist_id and song_id columns. It's just one because we're working with a subset of a much larger dataset and not all rows are included.

Once you fix the songplay_id column and stop having duplicates, you should see this one row.

## INSERT statements are correctly written for each table, and handle existing records where appropriate. songs and artists tables are used to retrieve the correct information for the songplays INSERT.

The INSERT statements are mostly correct. Great job dealing with the DUPLICATE values using ON CONFLICT clauses.
However, using DO NOTHING is not always the best approach. Even though there's no correct answer here, sometimes we don't want to lose all values.

For the users table, this is especially important. The level column has information about the user membership (free/paid).

Please update your ON CONFLICT clause for this table and update the column level in case of conflicts.
If you want to learn how to deal with conflicts, check this link