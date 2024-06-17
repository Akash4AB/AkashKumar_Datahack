Hello, I am Akash Kumar, a second-year M.Sc. student in the Mathematics and Computing branch at IIT Guwahati.

I received a dataset from the Consulting & Analytics Club at IIT Guwahati. My task is to predict how likely individuals are to receive their xyz and seasonal flu vaccines. Specifically, I will be predicting two probabilities: one for the xyz_vaccine and one for the seasonal_vaccine. This is a binary classification problem.

Here's a step-by-step description of how I approached this task using Google Colab:

1) Data Preparation:
  > I uploaded the provided zip file to Google Colab and unzipped it using a code snippet. This created a directory containing all the necessary CSV files: train, test, and level datasets.
  > I used the Pandas library to load these CSV files into dataframes.

2) Data Cleaning:
  > I checked for missing values in both the training and test datasets. I found some missing values.
  > I separated the numerical and categorical features before dealing with the missing values.
    Numerical missing values were filled with the mean of the corresponding feature, while categorical missing values were filled with the mode (the most frequent value) of that feature.

3) Data Integration:
    I concatenated the test dataset with the level dataset. Since the "respondent_id" feature appeared twice, I transposed the dataset and removed duplicate columns.

4) Encoding Categorical Features:
    For categorical features, I used One-Hot Encoding to convert them into numerical values. For features with many categories, I used Binary Encoding.

5) Finalizing the Datasets:
  > I removed the level dataset from the encoded test dataset as it was not at the end of the dataframe.
  > I concatenated the level dataset with the encoded training dataset and dropped the repeated "respondent_id" feature.

6) Splitting the Data:
    Using sklearn.model_selection, I split the data into training and testing sets. The independent features (X) included all features except those in the level dataset. The dependent features (y) included only the target features from the level dataset, excluding "respondent_id".

7) Handling Label Encoding:
    I encountered some issues with the data type of the y_train and y_test datasets. To resolve this, I used Label Encoding on these features.

8) Training the Model:
    I used the Random Forest Classifier algorithm to train the model.

9) Model Evaluation:
    I evaluated the model's performance using the ROC AUC score and achieved a mean ROC AUC score of around 0.8585.

10) Making Predictions:
    For predictions on the test dataset, I used the predict_proba() method, which returns an array of probabilities for each class.

11) Creating the Submission File:
  > I created a DataFrame with the respondent IDs and the predicted probabilities for both vaccines.
  > I saved this DataFrame to a CSV file named submission.csv without including the DataFrame index.

Conclusion:
Through this process, I developed a model to predict the likelihood of individuals receiving the xyz and seasonal flu vaccines with a decent accuracy reflected by a mean ROC AUC score of 0.8585. This work demonstrates the practical application of data cleaning, feature engineering, model training, and evaluation in solving a real-world binary classification problem.

