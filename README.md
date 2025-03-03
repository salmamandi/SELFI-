# ProxyLabel
ProxyLabel is a framework to predict the future emotion self-report labels from past emotion self-report labels and the current facial image. It takes past self-report label and current facial image as input. It consists of two different input blocks. In the first block, it calculates self-report features based on the past self-reported label. In the second block, it takes facial image and extract all facial landmarks as facial features using different feature extraction tool such as Amazon Rekognition, Google Vision, Microsoft Azure. Then feature reduction tool (for example KPCA, KDA) is applied which reduces the dimension of facial features. Finally, it leverages the extracted self-reported features and facial features to develop a personalize machine learning model which predicts emotion label at time instance. <br/>
<br/> 
![frame](https://user-images.githubusercontent.com/49473497/164719590-e702fef0-458c-4a44-87aa-70b3d79d3b15.jpg)
# File Structure
* The code file self_report.ipynb is the implementation of the framework.<br/>
* The Data folder contain two folders: <br/>
1. FacialData contain 3 folders for Amazon, Google and Microsoft image analysis tool. Each of these folders contain a file that stores facial feature values for each image of a particular user.<br/>
2. Self_reports folder contain 2 folders (Valence and Arousal) , where each folder has a file contain the sequence of self-reports for a particuler user. <br/>
* File_Processing folder contain codes to extract features from images using different tool.  
# Input Files
To predict emotion self-report label (valence/arousal), 2 files are required.<br/>
1. self-report file located in Valence and Arousal folder to predict valence and arousal self-report label, respectively. It has the following format:<br/>

|past_emo|current_emo|curr_img_id|elap_time|
|-------|:-----------:|--------:|---------|
|1	|1	|user_12/IMG_20210902_172538.jpg  |	2.28154166666667|
|1	|0	|user_12/IMG_20210902_194304.jpg  |	2.29043722222222|

past_emo and current_emo represent past and current self-reported emotion label, respectively. The curr_img_id represents the name of image file corresponding to the current emotion label. The elap_time is the elapsed time between past emotion and current emotion label in hour.<br/>
2. Facial feature file located in subfolder within the FacialData folder. <br/>
# Run the code
To run the code, specify
* user_no indicates used id. 
* input files name.
* run the code block written for a particuler image analysis tool to list facial features it returns.
* In the last code block, comment or uncomment specific lines of the code to select feature reduction tool.
# Pipeline for Data Preparation
Use files in File_Processing folder to extract features from image using different tool: Amazon Rekognition, Google Vision, Microsoft Azure. 
* **Prepare data using Amazon Rekognition** <br/>
   * run GetFeatures_AWS.ipynb to extract features from image. <br/>
   * run data_preprocessing.ipynb to break the composite features into simple feature.<br/>
   * run data_encoding.ipynb to encode the categorical features. <br/>
* **Prepare data using Google Vision** 
   * run GetFeatures_Vision.ipynb to extract features from image. <br/>
   * run BreakingComplexFeatureVision.ipynb to break the composite features into simple feature. <br/>
* **Prepare data using Microsoft Azure** 
   * run GetFeatures_Azure.ipynb to extract features from image. <br/>
   * run BreakingComplexFeaturesAzure.ipynb to break the composite features into simple feature.<br/>

