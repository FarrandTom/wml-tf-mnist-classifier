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
3. Get the data, and upload it to your storage bucket
4. Add your credentials to the template notebook
5. Train the model- monitoring progress and results
6. Deploy the model, and the test the endpoint

# Tutorial
## Step 1. Create a Watson Studio instance 
Visit the [IBM Cloud](https://cloud.ibm.com), and login or sign up. The account you create will be able to access a selection of free services- dubbed "Lite plans". 

Next, click the Catalog tab and search "Watson Studio". 
![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/1_watson_studio_search.png, "Watson studio")
