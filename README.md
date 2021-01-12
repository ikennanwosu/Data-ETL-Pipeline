# Data Extraction, Transformation and Loading (ETL)
Many organisations face a common problem of how to gather data from multiple data sources, in diverse formats, and be able to efficiently move the data to one or more data stores. The requirements for the destination and the format of the data at the destination may sometimes not be the same as the source, or the data may require cleaning or reshaping before loading it to the final destination.

This is where ETL pipelines come in handy. ETL is a general procedure for moving data from one or more sources, transforming the data according to business rules and loading it into a data store.

In this project, I ran a GDP dataset from World Bank in csv format through the ETL pipeline, and loaded the transformed data to a table in a database created in MS SQL Management Studio on my local machine.

The jupyter notebook begins by defining a problem, the purpose of the project and the source of data. Then connects to a database and creates a table to hold the transformed data. Three functions were defined to extract, transform and load the data. Lastly, the ETL pipeline was executed and a verification script run to check that the table was populated with the transformed data.


## Table of Contents

1. [Installation](#installation)
2. [Purpose of Project](#purpose-of-project)
3. [Description of Functions](#description-of-functions)
4. [Results](#results)
5. [Acknowledgement](#acknowledgement)


## Installation
Most of the code in this project will run with the Anaconda distribution of Python version 3.*. However, the Python module for connecting to ODBC databases needs to be installed by running:

- pip install pyodbc


## Purpose of Project
This project was undertaken to demonstrate construction of a typical ETL pipeline, to extract, transform and load data from a csv file to an MS SQL database using Python.


## Function Descriptions
The functions used in this project are:
1. `extract_lines` - a Python generator that takes the dataset as input, and lets the ETL pipeline read in the data one row at a line. This is useful for preventing the whole dataset from being loaded into RAM, especially if the dataset is large. 
2. `transform_indicator_data` -  the function receives a row of data from the GDP csv file and transforms the data in preparation for the loading step. It checks that the country names in the "Country Name" column is an actual country name, reshapes the row data, creates a dataframe with the reshaped row data, transforms the row dataframe from a wide to long format, and appends the result to a list.
3. `load_indicator_data` - it loads the list of trasnformed data into a defined table in a specific database.


## Results
The table and database were successfully created and loaded with the transformed data.


## Acknowledgements
I will like to thank UDACITY for providing the dataset and the structure for this project. This was an exercise as part of the requirements for the Udacity Data Scientist Nanodegree. 



       
