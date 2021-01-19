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


# Disaster Response Pipelines
The focus of this project is to apply data engineering skills to analyze disaster data from [Figure Eight](https://appen.com/) containing real messages that were sent during disaster events to disaster response organizations. The final product is a web application that an emergency worker can input new messages received during such events and get classification results of 1 or more of 36 different categories depending on the aid required.

![alt text](disaster_image.JPG)

## Table of Contents

1. [Installation](#installation)
2. [Purpose of Project](#purpose-of-project)
3. [Description of Functions](#description-of-functions)
4. [Results](#results)
5. [Acknowledgement](#acknowledgement)


## Project Structure
The project is divided into three parts;
1. Data Processing Pipeline: The datasets for this project is run through an ETL (Extract, Transform & Load) process that reads the csv datasets, cleans the data, and stores it in an SQLite database. To load the data into an SQLite database, pandas dataframe `.to_sql()` method is applied to the transformed data, with the aid of SQLAlchemy engine.
2. Machine Learning (ML) Pipeline: The transformed data is loaded from the SQLite database, and split into training and test sets. These are then fed into an ML pipeline that uses NLTK (Natural Language Toolkits) and GridSearchCV to predict classifications for 36 categories. This is a multiclass/multi-output classification problem. The trained model is serialzed and exported to a pickle file that the API will use for the classification task.
3. Web Application: The model that performs the classification task is deployed in a Flask web application, which also visualises the dataset.


## Installation
Most of the code in this project will run with the Anaconda distribution of Python version 3.*. 

## Data Description


## File Descriptions
- app
| - template
| |- master.html           # main page of web app
| |- go.html               # classification result page of web app
|- run.py                  # Flask file that runs app

- data
|- disaster_categories.csv  # data to process 
|- disaster_messages.csv    # data to process
|- process_data.py          # Python script to perform the ETL process on the Terminal
|- DisasterResponse.db      # database to save clean data to

- models
|- train_classifier.py      # Python script to perform the ML process on the Terminal
|- classifier.pkl           # saved model 

- README.md
- disaster_image.JPG        # picture used for the README file
- requirements.txt          # files required to run the above Python scripts


       
