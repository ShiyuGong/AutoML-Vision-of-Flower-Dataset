# AutoML-Vision-of-Flower-Dataset

## Overview 
AutoML Vision enables us to train machine learning models to classify images according to our own defined labels. For this project, we will utilize free tier AutoML to train our own model of the flower dataset (the publicly available dataset of flower images from gs://cloud-ml-data/img/flower_photos/), evaluate the model performance and then predict two flower pictures with Vision API.

## Technique 
### Configure project environment
reference: https://cloud.google.com/vision/automl/docs/tutorial

1. In the GCP console, go to the Manage resources page and select or create a project,

2. then make sure that billing is enabled for the Google Cloud Platform project and enable the AutoML Vision APIs.

3. After that, a service account needs to be created and a key file should be downloaded and stored in the Google Drive. 

4. In the following steps, set the GOOGLE_APPLICATION_CREDENTIALS environment variable to the path to the service account key file that we downloaded when we created the service account. 

5. Add the new service account to the AutoML Editor IAM role to allow the AutoML Vision service accounts to access the Google Cloud project resources. 

6. Then, set the PROJECT_ID and REGION_NAME environment variables. 

7. Create a Google Cloud Storage bucket to store the documents that we will use to train your custom model.

8. Copy the publicly available dataset of flower images into our Google Cloud Storage bucket.

### Train your own model (using free tier of AutoML) of the flower dataset

After 3667 flower images are imported, we could use free tier of AutoML to train our model. The evaluation results provided are as follows. The average precision is 0.996; Based on a score threshold of 0.5, Precision is 98.466% and Recall is 96.396%. (A high precision model produces fewer false positives, and a high recall model produces fewer false negatives.) Overall, the AutoML Vision trained model of flower dataset has a really good performance.

![image](https://user-images.githubusercontent.com/43686840/54245122-cafc1700-44ec-11e9-9ad3-a6b16138af22.png)
![image](https://user-images.githubusercontent.com/43686840/54245412-f9c6bd00-44ed-11e9-81fb-fe2189d25f35.png)

### Predict with Vision API

In this step, we will go further to predict two flower pictures (one is daisy and the other is sunflower) with Vision API. After setting the project id, compute region, model id, file name and score threshold, we could get the full path of the model and create client for prediction service and then read the images and assign to payload. 

The predicted results for both images are really good. The predicted class names are correct with high predicted class scores, which are 0.99986732006073 and 0.9999873638153076 respectively for daisy and sunflower.

![image](https://user-images.githubusercontent.com/43686840/54245376-cedc6900-44ed-11e9-9f19-0c3afea85a03.png)
![image](https://user-images.githubusercontent.com/43686840/54245378-d13ec300-44ed-11e9-9a28-9a33cbb118e6.png)

## Conclusion 
AutoML Vision, a graphical drag-and-drop tool that lets users leverage Google’s cloud computing backend to train self-learning object recognition and image detection models, is really useful for data analysis, which saves us time to train the model by ourselves and provides high-performance models. What we need to do is only to learn how to call APIs. 


