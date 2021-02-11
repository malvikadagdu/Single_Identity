# Single_Identity

This is a project basically involves examining customer information, improving customer experience. Here what I have done is a part of the ETL process to provide clean data for further processing. A runb through how the data pipeline was created in this scenario.

I have used a sample data to work on this project, and utilized the tools in a similar fashion. Firstly, I acquired the dataset from kaggle which is a telecommunication data. I used AWS EC2 machine along with Kinesis Firehose, to push in the information into S3 buckets. For that firstly, I had to create an EC2 machine on the AWS console and connect it to my terminal with the SSH client. After the machine is connected, I turned on the aws-kinesis-agent, so that it could push whatever data it could see from the source location to the destination location. 

After the data got pushed into the S3 buckets, for the transformation of the data, AWS Glue and Athena was used along with the integration to Hive. Using AWS Glue, a crawler was created and ran that crawler to get the schema for the database and the required tables for processing. The tables were already present in the Athena due to the internal connection between Glue and Athena. Then integrated it with Hive to run the transformations on the Hive Cluster. Here I created partitions and buckets on the dataset based on the segregation needed. 

After this stage, the next stage is to ingest streaming data and processing it. For that Kinesis Data Streaming and Apache Spark was used. Spark code was developed to batch process and real time processing of the data. 

After all the required transformations done, Amazon QuickSight was used for a minimalistic visualistion of the developed and modelled dataset, just to make sure the trend was present and all the required data was merged and available in the required tables. 