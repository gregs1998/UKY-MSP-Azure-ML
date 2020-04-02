# University of Kentucky MSP - Azure Machine Learning Workshop

This readme contains a tutorial for attendees of the University of Kentucky MSP Azure Machine Learning Workshop. To register, visit this link: https://bit.ly/AzureMLUKY

## Step 1: Register for Azure for Students

Azure for Students gives K-12 and higher education students across the globe access to hundreds of Azure resources, including those needed for Azure Machine Learning Studio. 

## Step 2: Download and Import "train.csv" Dataset

Follow the link: ---------- to download the "train.csv" dataset. This is the dataset which we will use to train and test the model.
Select "New" then select Dataset and follow the on-screen instructions to upload the downloaded dataset from your computer. Then under the "Select Datasets" experiment item, drag your "train.csv" tab into the workspace.

## Step 3: Exclude the unused Columns



## DELETE: All the ML Steps (but not pretty)

1. Create a new experiment
2. Add "select columns in dataset" -> "Exclude: PassengerId, Name, Ticket, Cabin"
3. Add "clean missing data" -> Cleaning mode: Remove entire row
4. Add "Edit metadata" -> Pclass, Sex, Survived, Embarked -> Categorical: Make categorical
5. Add "Edit metadata" -> Survived -> Fields: label
6. Add "Split Data" -> Fraction of rows = 0.7 -> Stratified split: True, on "Survived"
7. Add 2 "Train model" -> select column: Survived
8. Add two-class neural network and two-class SVM, wire to train model
9. Add 2 "Score model"
10. Add "evaluate model"
11. Run and visualize output -> show which model is more accurate

1. Set up web service -> Predictive web service [Recommended]
2. Run predictive experiment
3. Deploy web service

1. Next to "Request/Response" , click "Test"
2. Submit a random sample of data
3. Look at the last part of the JSON that's returned: integer 0=died, 1=survived, decimal is probability


## Steps on New Platform:

1. Visit aka.ms/AzureForStudents
2. Click *Activate Now* and sign in with your LinkBlue credentials
3. Enter your email address and phone number when prompted - you may have to verify one of them
4. Open the azure portal
5. Click the menu on the left-hand side, go to resource groups
6. Add a new resource group, we'll call it "MSPAprilML"
7. Review+Create, then Create
8. Now, in portal search bar, go to "Machine Learning"
9. Give it a name, choose your resource group you just made, choose pricing "ENTERPRISE"
*Note: You won't be billed - this draws from your Azure for Students credit*
10. Review + Create, then Create

### Let's go get the dataset

1. Go to bit.ly/AzureMLWorkshopData
