![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/header.png "Header")

# Creating an MNIST Classifier using Watson Machine Learning and TensorFlow

This repository acts as a tutorial showing how to quickly get up and running using GPUs in the IBM Cloud via Watson Studio, and Watson Machine Learning (WML). 

We are going to walk through the set up of a simple MNIST classifier. This use case serves as an easy introduction to those newer to deep learning, while allowing more experienced developers to focus on the nuances of the Watson offerings. If you are tired of MNIST examples then there is a [style transfer example here](https://github.com/ChrisParsonsDev/wml-pytorch-style-transfer), which is an alternate way to get hands-on. 

This repository will contain: 
1. TensorFlow model
2. Jupyter notebook which executes the TensorFlow model via the WML service

The flow of this tutorial is as follows:
1. Create a Watson Studio instance 
2. Add a Deep Learning project
3. Hook up the Jupyter notebook
4. Get the data, and upload it to your storage bucket
5. Add your credentials to the template notebook
6. Train the model- monitoring progress and results
7. Deploy the model, and the test the endpoint

# Tutorial
## Step 1. Create a Watson Studio instance 
Visit the [IBM Cloud](https://cloud.ibm.com), and login or sign up. The account you create will be able to access a selection of free services- dubbed "Lite plans". 

Next, click the Catalog tab and search "Watson Studio". 

![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/1_watson_studio_search.png "Watson studio")

Create a "Lite" Watson Studio instance and select "Get Started".

![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/2_watson_studio_instance.png "Watson studio creation")

So far so simple right?

## Step 2. Add a Deep Learning Project
In the Watson Studio landing page select "Create a project", and then "Deep Learning". 

![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/3_create_a_project.png "Create a project")

![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/4_deep_learning_project_selection.png "Deep Learning")

This will create two new cloud services at your disposal:
1. **Cloud Object Storage (COS)**- An S3 storage bucket for your files
2. **Watson Machine Learning (WML)**- Providing you access to IBM Cloud's hosted GPUs

Name your project e.g. *mnist-classifier*. As the project creates it will automatically connect to your COS and WML services.

Nifty. 

![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/5_watson_studio_project_creation.png "Watson studio project creation")

## Step 3. Hook up the Jupyter notebook
