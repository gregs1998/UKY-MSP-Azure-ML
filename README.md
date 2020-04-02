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
10. Review + Create, then Create [ ~ 3 minutes ]

### Let's go get the dataset

1. Go to https://1drv.ms/u/s!Au6UHXKoFRQhuy0aqH-LP2z9rziy?e=yie0He
2. From Excel online, go to File -> Save As -> Download a Copy : Let's look at the CSV and see what data we have
3. Go back to Azure portal (portal.azure.com), search for Machine Learning and open that panel
4. Open your ML workspace resource
5. Click "Launch Now" inside the *New Machine Learning Studio* dialog box
6. You may have to sign back in
7. Manage Compute
8. Training Clusters -> New -> VM Size: Standard_D1 -> Min number: 0 -> Max number: 1 -> CREATE
9. Inference Clusters -> New -> Central US -> DevTest -> Create

### Dataset Upload
1. Designer -> Prebuilt -> give it a name
7. First, we need to upload our dataset. From the left sidebar, go to "Dataset" this is a GUI that allows us to build interactive ML. Create Dataset -> From local files.
Give it a name
Leave tabular
Leave datastore option default, browse to downloaded file and upload
Column headers -> choose "use headers from first files"
Next all the way through
8. Back to designer, open previous pipeline
9. Select compute target -> choose what you created earlier
9. Drop down datasets, drag in in titanic
10. Drag in "select column in dataset", wire titanic output to input of this module, then edit "select columns" for the following: ALL EXCEPT:
- PassengerId, Name, Ticket, Cabin
11. Submit, select compute target, create new, predefined (give it a name), submit
12. Submit, create new experiment, give name, submit
On the backend, Azure is dynamically assigning a cluster of virtual machines to run your experiment. So, this may take a LOT of time.
13. Add "clean missing data" -> Select columns: edit columns (By Name: Add all) -> Cleaning mode: Remove entire row, submit
14. Add "Edit metadata" -> Pclass, Sex, Survived, Embarked -> Categorical: Make categorical :: SUBMIT
15. Add "Edit metadata" -> Survived -> Fields: label :: SUBMIT
16. Add "split data" -> stratified split: true, on "Survived" -> 0.7 :: SUBMIT
17. Add 2 "Train Model" blocks -> Edit label column: survived
18. Add "2-class neural net" and "2-class SVM", wire to train model blocks 
19. Add 2 "Score Model" blocks and wire
20. Add an "Evaluate Model" block and wire :: SUBMIT
21. Click on "Evaluate Model" -> Output -> We can visualize and see evaluation results
22. Click on higher scored "train model" -> create real-time inference pipeline
23. Once run is finished, DEPLOY
24. Create new Kubernetes cluster: region Central US, VM size Standard_A2_v2, Dev-test, 1 node
25. Choose compute target, click deploy
26. Once done, "view live endpoint" -> Test
27. Enter some data, see results!
