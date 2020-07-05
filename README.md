# Disaster Response Pipeline Project

![](https://github.com/ObinnaIheanachor/Disaster-Response/blob/master/My-Video2-1%20low.gif)


## Introduction
During a disaster, millions of messages either via social media, email, etc. are sent to disaster response organizations and they have limited capacity to filter and then pull out the messages which are the most important. Machine learning is critical to helping different organizations understand which messages are relevant to them, and which messages to prioritize.

In this project, using disaster data from [Figure Eight](https://www.figure-eight.com/), which contains pre-labeled tweets and text messages from real-life disasters,  I built and deployed a model that classifies disaster messages.

## Prerequisites
To install the flask app, you will need:

python3
python packages in the [requirements.txt file](https://github.com/ObinnaIheanachor/Disaster-Response/blob/master/requirements.txt)
Install the packages with

pip install -r requirements.txt
To create an environment using: conda create --name --file requirements.txt

## Project Components
There are three components for this project:

**ETL Pipeline**:This ETL pipeline pre-processes the messages and category data from CSV file and load them into SQLite database. In the Python script, process_data.py, you will find the data cleaning pipeline that:

* Loads the messages and categories datasets
* Merge the two datasets
* Cleans the data
* Stores it in a SQLite database

**ML Pipeline**: The Machine Learning pipeline reads the data from the SQLite database to create and save a multi-output supervised learning model. In the Python script, train_classifier.py, you will find the machine learning pipeline that:

* Loads data from the SQLite database
* Splits the dataset into training and test sets
* Builds a text processing and machine learning pipeline
* Trains and tunes the model
* Outputs results on the test set
* Exports the final model as a pickle file

**Flask Web App**: The Flask web application, uses the trained model(the pickle file) to classify incoming messages where an emergency worker can input a new message and get classification results in several categories.

## Structure
Below you can find the file structure of the project:



      disaster_response_pipeline
          |-- app
                |-- templates
                        |-- go.html
                        |-- master.html
                |-- run.py
          |-- data
                |-- disaster_message.csv
                |-- disaster_categories.csv
                |-- DisasterResponse.db
                |-- process_data.py
          |-- models
                |-- classifier.pkl
                |-- train_classifier.py
          |-- Preparation
                |-- categories.csv
                |-- ETL Pipeline Preparation.ipynb
                |-- ETL_Preparation.db
                |-- messages.csv
                |-- ML Pipeline Preparation.ipynb
          |-- License
          |-- My-Video2-1 low.gif
          |-- README
          |-- requirements.txt
## Instructions:
1. Run the following commands in the project's root directory to set up your database and model.

    - To run ETL pipeline that cleans data and stores in database
        `python data/process_data.py data/disaster_messages.csv data/disaster_categories.csv data/DisasterResponse.db`
    - To run ML pipeline that trains classifier and saves
        `python models/train_classifier.py data/DisasterResponse.db models/classifier.pkl`

2. Run the following command in the app's directory to run your web app.
    `python run.py`

3. Go to http://0.0.0.0:3001/

## Licence
The contents of this repository are covered under the [MIT License](https://github.com/ObinnaIheanachor/Disaster-Response/blob/master/LICENSE)
