# Extract, Transform, Load - Movie Data

## Project Overview
The purpose of this project is to provide a cleaned dataset from three data sources on movies. Results of this project is an automated pipeline that can take in new data, performs the defined transformations, and load the data into existing tables in SQL. 

## Results 
The final program extracts data from three sources: a CSV file from Kaggle, a CSV file from MovieLens and a JSON file from Wikipedia. The program executes two functions. 

The first funstion, clean_movie, creates a non-destructive copy of a movie datasest and adds data from specified columns that provide alternative titles into a new column, 'alt_titles'. The specified columns are then deleted. Within this function, an inner function, change_column_name, consolidates similar data from one column to another.

The second function, extract_transform_load, reads the CSV files as Pandas DataFrames and reads the JSON file. A list comprehension filters out TV shows that have been included in the data. Another list comprehenion iterates through the filtered list and pushes the list through the first function. This list is then read as a DataFrame. A try-except block extracts IMBd IDs and drops any duplicates. If there is an error, the exception is printed. A list comprehension keeps columns in the Wikipedia movies data if the column has less than 90% null values. The function then formats the box office, budget, release date, and running time columns to a uniform format. An inner function, parse_dollars, uses regex to converts different formats for a given dollar value to a float-type value. This inner function is applied to the box office and budget columns. The Kaggle data is cleaned by removing corrupted data and using Pandas built-in functions to convert data into specified data types. The Wikipedia and Kaggle data are merged. Columns are dropped from the merged DataFrame, based on analysis of similar columns. An inner funciton, fill_missing_kaggle_data, fills in missing Kaggle data with Wikipedia data. The columns of the merged DataFrame are filtered and finally renamed. The function then transforms and merges the ratings with the movies DataFrame. The movies and ratings DataFrames are added to the SQL database. 

## Note to grader
CSV files and JSON file were not uploaded to GitHub due to size of the files. 
