    REAL TIME STOCK DATA PRICE PREDICTION - PROJECT 

Hadoop Version :(hadoop version):3.3.1

Python Version:(python3 --version):3.8.10

Spark Version :(spark-shell --version):3.1.2


USE CASES:

1. Use Spark to fetch the stocks data in real time.

2. Move data to a centralised data store in the cloud for further analysis in the data pipeline.

3. Preprocess the data (Python + Spark).

4. Store the cleaned data on HDFS

5. Carry out the prediction using Mllib

6. Visualization using flask

 1) start the hadoop servers:
               ~$ start-all.sh
                 ~$ jps
                 
2) install filezilla and flask:
	pip3 install flask:

Download filezilla and extract it and in terminal :sudo apt-get install filezilla

2 )  Create a spark session and import the required libraries

3) Fetch the real time stock data using API key into csv file and place that file in hadoop(HDFS)

Reading the stock data from hdfs to process and clean it using pySpark

Clean , Preprocess and build ML model

Performing linear regression on cleaned data:

Preprocessing the data to clean it
 1.Create a python notebook and create a spark session 

 2.Clean the data Removing the quotes,change datatypes 

 3.Splitting the data into train and test data using rank. 

 4.Write test data to parquet file for further use test_df.write.parquet('testdata')

 5.Create model with linear regression algorithm 
 
 6.Making predictions by transforming data into model
 
  predDF= lr_model.transform(test_df)  predDF.select("Features","close","prediction").show(5)

 7.Evaluating the model RMSE: It is the square root of the mean of the square of all the errors ie. it is the standard deviation of the residuals(predicted errors). 

from pyspark.ml.evaluation import RegressionEvaluator regressionEvaluator = RegressionEvaluator( predictionCol="prediction", labelCol="close", metricName="rmse") rmse = regressionEvaluator.evaluate(predDF) print(f"Root Mean Square Error (RMSE) is {rmse:.1f}")

8.Save model
    lr_model.save(“hdfs://localhost:9000/prediction_stock_price_data_model”)

DOWNLOAD TESTDATA AND PREDICTION_STOCK_PRICE_DATA_MODEL FROM HDFS INTO LOCAL SYSTEM:

Stock data visualization :using flask

Run the app.py---> stock data visualisation can be visible on web.



  DEPLOYING ON AWS EC2:
  
  Create the AWS EC2 INSTANCE 
  
  GIVE THE SECURITY GROUP PERMISSIONS AS ALL TRAFFIC AND ANYWHERE AND CONNECT INSTANCE
  
  CREATE THE REQUIREMENTS.TXT FILE AND ENV ENVIRONMENT:
   
   sudo apt install python3-venv

   python3 -m venv env

   pip freeze > requirements.txt
   
   Installations to be done on Ec2 instance:

sudo apt-get update && sudo apt-get install python3-pip

sudo apt-get install default.jre

Use filezilla to transfer files from local to Ec2 instance:


Install requirements.txt file 

pip3 install -r requirements.txt

Execute app.py file:(python3 app.py)









  






