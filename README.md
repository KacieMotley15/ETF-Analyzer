# ETF Analysis

## Introduction
This repository contains code for analyzing a FinTech ETF. It utilizes SQL queries with Python, Pandas, and hvPlot to analyze the performance of different assets within the ETF.

## Installation
To run the code in this repository, you need to have the following libraries and dependencies installed:

- numpy
- pandas
- hvplot.pandas
- sqlalchemy

You can install the required libraries by running the following command:

## Usage
To analyze a single asset in the FinTech ETF, follow these steps:

1. Create a temporary SQLite database and populate it with content from the `etf.db` seed file.
2. Establish a connection to the SQLite database using the database connection string: `sqlite:///etf.db`.
3. Confirm the table names contained in the SQLite database using the `engine.table_names()` method.
4. Write a SQL SELECT statement to read the data for a specific asset (e.g., PYPL) from the database into a Pandas DataFrame.
5. Use the head and tail functions to review the first five and last five rows of the DataFrame to get an idea of the available data.
6. Use hvPlot to create interactive visualizations for the daily returns and cumulative returns of the asset.
7. Optimize SQL queries by accessing specific data from the database efficiently.
8. Use advanced SQL queries to retrieve specific information, such as closing prices above a certain threshold or top daily returns.

## Example Code
Here's an example of how to perform some of the tasks mentioned above:

```python
# Import the required libraries and dependencies
import numpy as np
import pandas as pd
import hvplot.pandas
import sqlalchemy

# Create a temporary SQLite database and populate it with content from the `etf.db` seed file
database_connection_string = 'sqlite:///etf.db'

# Create an engine to interact with the SQLite database
engine = sqlalchemy.create_engine(database_connection_string)

# Confirm the table names contained in the SQLite database
print(engine.table_names())

# Write a SQL SELECT statement to read the PYPL data from the database into a Pandas DataFrame
query = "SELECT * FROM PYPL;"
pypl_dataframe = pd.read_sql_query(query, con=engine)

# View the first 5 rows of the DataFrame
print(pypl_dataframe.head())

# Create an interactive visualization for the PYPL daily returns using hvPlot
pypl_dataframe['daily_returns'].hvplot(x='time', xlabel='Days', ylabel='Daily Returns', title='PYPL Daily Returns')

# Create an interactive visualization for the PYPL cumulative returns using hvPlot
(1 + pypl_dataframe['daily_returns']).cumprod().hvplot(x='time', ylabel='Cumulative Returns', xlabel='Days', title='PYPL Cumulative Returns')

## Conclusion
This repository provides code for analyzing a FinTech ETF using SQL queries, Python, Pandas, and hvPlot. By following the instructions and examples, you can gain insights into the performance of individual assets within the ETF and optimize SQL queries to access specific data efficiently.

Feel free to explore the code and adapt it to suit your needs!
