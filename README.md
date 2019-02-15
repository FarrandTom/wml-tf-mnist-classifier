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
5. Obtain the credentials for both COS and WML
**6. Add your credentials to the template notebook**
**7. Train the model- monitoring progress and results**
**8. Deploy the model, and the test the endpoint**

The steps highlighted in **bold** will be ran in the template Jupyter notebook provided within the Watson Studio development environment.

# Tutorial
## Step 1. Create a Watson Studio instance 
Visit the [IBM Cloud](https://cloud.ibm.com), and login or sign up. The account you create will be able to access a selection of free services- dubbed "Lite plans". 

**Note:** You'll be asked what region you'd like to create your Watson Machine Learning Service Instance in. While any region is suitable for this code lab, I'd recommend the US South region.

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
Within your new deep learning project, select the "Add to project" button and then select a "Notebook" asset. 

![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/6_add_deep_learning_notebook.png "Jupyter notebook asset")

Select "From URL" from the tabs along the top, and insert the URL to the Jupyter notebook in this repository. 

`https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/wml-mnist-classifier.ipynb`

![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/7_notebook_from_url.png "Notebook URL")

Selecting the "Default Python 3.5 Free (1 vCPU and 4GB RAM)" option will provision a virtual machine to run your Jupyter notebook from. 

**Note:** The dialogue may change in the future. Simply select the free vCPU option. 

![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/8_notebook_python_version.png "Python version")

You will then see a loading screen as the virtual CPU is created. 

## Step 4. Get the data and upload it to your storage bucket
The dataset we'll be using to train our TensorFlow classification model in this instance is the [MNIST Dataset](http://yann.lecun.com/exdb/mnist/). 

Either visit the link above, select and download all of the four files available, or download the four files from the list below:
1. [train-images-idx3-ubyte.gz](http://yann.lecun.com/exdb/mnist/train-images-idx3-ubyte.gz):  training set images (9912422 bytes) 
2. [train-labels-idx1-ubyte.gz](http://yann.lecun.com/exdb/mnist/train-labels-idx1-ubyte.gz):  training set labels (28881 bytes) 
3. [t10k-images-idx3-ubyte.gz](http://yann.lecun.com/exdb/mnist/t10k-images-idx3-ubyte.gz):   test set images (1648877 bytes) 
4. [t10k-labels-idx1-ubyte.gz](http://yann.lecun.com/exdb/mnist/t10k-labels-idx1-ubyte.gz):   test set labels (4542 bytes)

Once you have the four files on your local system, then you will need to navigate to your freshly created Cloud Object Storage bucket. This can be done by [clicking here](https://cloud.ibm.com/resources)- this will navigate you to your IBM Cloud Resource list. This is simply a list of all the provisioned services within your IBM Cloud account. You should be able to find your Watson Studio, Cloud Object Storage, and Watson Machine Learning instances under one of the various headings. 

![alt text](https://github.com/FarrandTom/wml-tf-mnist-classifier/blob/master/readme-images/12_resource_list.png "Resource list")

If you select the Cloud Object Storage instance (it is likely to have a name similar to *cloud-object-storage-dsx*), you can then create two new buckets.

(BUCKET CREATION SCREENSHOT)

One bucket will hold our training data, the other will contain the results. I have named mine `mnist-classifier-training` and `mnist-classifier-results` respectively. 

You can then drag and drop the MNIST data and labels into your training bucket i.e. `mnist-classifier-training`. The resulting bucket should then be a list of 4 `.gz` files as below. 

(SCREENSHOT OF MNIST-CLASSIFIER-TRAINING BUCKET FILES)

## 5. Obtain the credentials for both COS and WML
While still in the user interface for your Cloud Object Storage instance we will retrieve the service credentials. These act as the Cloud Object Storage's passport- allowing it to verify itself as belonging to your account, and laying out how other services can communicate to it. 




