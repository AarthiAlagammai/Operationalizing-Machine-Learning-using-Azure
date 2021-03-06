
# Operationalizing Machine Learning

Here we use bank marketing dataset [Dataset link](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv).This dataset is related to direct marketing campaigns of a Portuguese banking sector. The campaigns were based on phone calls.The goal is to classify whether a client will subscribe to a term deposit or not.The goal of this project is to use Azure to configure a cloud-based machine learning production model, deploy it to an end point, and consume it using an HTTP API.Then also create, publish, and consume a pipeline.

## Architectural Diagram

![Architecture](Screenshots_from_the_workspace/architecural-diagram1.png)

![Architecture](Screenshots_from_the_workspace/architecural-diagram.png)
The following are the major steps used in the project

1.Authentication

2.Automated ML Experiment

3.Deploy the best model

4.Enable logging

5.Swagger Documentation

6.Consume model endpoints

7.Create and publish a pipeline

### Authentication

Authentication is crucial for the continuous flow of operations. Continuous Integration and Delivery system (CI/CD) rely on uninterrupted flows. When authentication is not set properly, it requires human interaction and thus, the flow is interrupted. An ideal scenario is that the system doesn't stop waiting for a user to input a password. So whenever possible, it's good to use authentication with automation.Authentication types 1. Key Based 2.Token based 3. Interactive

### Automated ML Experiment

To ship a model into production we need the best model for the problem statement. Here we use AutomatedMl feature of Azure to determine the best model 

### Deploy the best model

Deployment is about delivering a trained model into production so that it can be consumed by others. Configuring deployment settings means making choices on cluster settings and other types of interaction with a deployment. Deployment can be done in both Azure ML Studio and the Python SDK 

### Enable logging

Logging is the core pillar for MLOps. It helps to determine anomalities , irregularities and also visualize the performance. This done using Application Insights which is modifiable with Azure SDK

### Swagger Documentation

Swagger is a tool that helps build, document, and consume RESTful web services like the ones we are deploying in Azure ML Studio. It further explains what types of HTTP requests that an API can consume, like POST and GET.It simplifies and normalizes the documentation of HTTP APIs.Azure provides a swagger.json that is used to create a web site that documents the HTTP endpoint for a deployed model.

### Consume Model Endpoints

We can consume a deployed service via an HTTP API. An HTTP API is a URL that is exposed over the network so that interaction with a trained model can happen via HTTP requests.
Users can initiate an input request, usually via an HTTP POST request. HTTP POST is a request method that is used to submit data. The HTTP GET is another commonly used request method. HTTP GET is used to retrieve information from a URL. The allowed requests methods and the different URLs exposed by Azure create a bi-directional flow of information.
The APIs exposed by Azure ML will use JSON (JavaScript Object Notation) to accept data and submit responses. It served as a bridge language among different environments.
Documentation


### Create and publish a pipeline

Pipeline form a basis of automation.Publishing a pipeline is the process of making a pipeline publicly available. We can publish pipelines in Azure Machine Learning Studio and also  with the Python SDK.When a Pipeline is published, a public HTTP endpoint becomes available, allowing other services, including external ones, to interact with an Azure Pipeline.Pipelines can perform  

1.Data Preparation

2.Training 

3.Validation

4.Deployment

5.Combined tasks



## Key Steps
1.Make sure the dataset is available in the Registered dataset list in MLStudio

![Registereddataset](Required_Screenshots/Registereddataset2.PNG)

2.Create an AutoMl run and wait till the run is completed

![automl](Required_Screenshots/automl_completed.PNG)

3.Find the best algorithm for the problem statement. From the below image we can see that Voting Ensemble is the best algorithm for the problem statement 

![Best model](Screenshots_from_the_workspace/automlbestmodel.PNG)


4.Deploy the best model using ACI(Azure Container Instance and Enable Authentication)

![ACI Deployment](Screenshots_from_the_workspace/successful-deployment.PNG)


5.Enable Application Insights using the logs.py file and make sure that Endpoints section in Azure ML Studio, showing that “Application Insights enabled” says “true”.

![Application Insights](Screenshots_from_the_workspace/appinights_enabled1.PNG)

6.Logging is enabled by running the provided logs.py script

![Application Insights enabled](Screenshots_from_the_workspace/appinsights-enabled.PNG)

![](Required_Screenshots/appinsights_log.PNG)


7.Use Swagger Documentation to get a smpilifed document to consume the HTTP API.wagger runs on localhost showing the HTTP API methods and responses for the model

![Swagger Documentation](Screenshots_from_the_workspace/swagger_bank_marketing_post1.PNG)


8.Consume the model using a RestEnpointAPI and Primary key. Update it in the endpoints.py file and run it against the API producing JSON output from the model.

![endpoint_consume](Screenshots_from_the_workspace/endpoint_consume1.PNG)

![endpoint_consume](Screenshots_from_the_workspace/endpoint_consume2.PNG)


9. Benchmarking HTTP APIs is used to find the average response time for a deployed model.A benchmark is used to create a baseline or acceptable performance measure.Here Apache Benchmark (ab) runs against the HTTP API using authentication keys to retrieve performance results

![Benchmarking](Screenshots_from_the_workspace/bench3.PNG)

10.Make sure the pipeline creation is completed

![pipeline ](Required_Screenshots/completed_status.PNG)

11.Check the status of endpoint in SDK 

![active_endpoint](Required_Screenshots/active_endpoint.PNG)


12.Consume and publish the API using Azure SDK

![Consume](Screenshots_from_the_workspace/pipeline_endpoint.PNG)

13.Status of run widget
![](Required_Screenshots/run_widget3.PNG)

![](Required_Screenshots/run_widget4.PNG)

14.The Bankmarketing dataset with the AutoML module

![](Required_Screenshots/pipeline_automl.PNG)


## Overall Work flow 

 ![](Required_Screenshots/architecturedia.png)

## Future Works
1.The exit criterion of the automl model is reduced to 1hour to save compute powe and resources which by increasing can lead to finding a better perofrming model

2.The accuracy of the model can be improved by solving the class imbalance issue of the bank-marketing datatset

3.Increasing the  number of cross validation can help in achieving better accuracy

