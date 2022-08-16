# Program Structure Confirmation
## Since CNN involved too much computation power in CPU, we decide to run it in Google Colab Pro using pytorch lib.
## Other 3 models (RF,SVM,MLP) also run on Colab Pro, to make the file structure consistent and make the shared files accessible to the models, also easier for crew members to check the files later.
## Google Drive structure:
dataset
 ┗ train
 ┃ ┣ clean
 ┃ ┣ eval
 ┃ ┣ model
 ┃ ┣ origin
 ┃ ┗ transformed
 ┃ ┃ ┣ clustered
 ┃ ┃ ┗ raw
### Every notebook file is in Colab folder outside this folder, this dataset folder only contains runtime data or input data
- "clean" contains every classes of images constructed by their landmark id as the parent folder name, these images are manually filter out by crew members from 400 images to 120 for each class with unrelevant or bad images been removed, only images describe the corresponding landmark with different angle are preserved, the size of each image is not equal, so they are still raw data, but clean.
- "eval" contains all runtime files that can contribute to evaluation part of our report, it can be a source data for final graph or a table recording complete evaluation values for a model to use to plot a graph.
- "model" contains trained model file from pytorch, we don't save sklearn model because the runtime for sklearn models are acceptable, they are all simple models but CNN cost too much time to train. In this folder, the name of saved model is corresponding to the hyperparameters of the CNN model in training.
- "origin" contains all of the downloaded raw image bad or good from kaggle dataset with 10 classes randomly chosed, waiting for manually clean.
- "transformed/raw" contains transformed dataset from "clean" folder, all the images will be compress to a single line of numpy array called X_data, and the final array will be a 4D array with the first position the total image count. Each label of the image will be compressed to a file called y_data. The X_train,y_train,X_val,y_val,X_test,y_test are all come after a train test split function call from pytorch, to make the later cross validation consistent.
- "transformed/clustered" contains all the kmeans,hist,inertia from k equals to 1 to 45, trying to find the best k and plot it. And as input for the later model training. (RF,SVM,MLP) will all use kmeans to train.
## We have at total 5 notebooks for this project, they are CNN.ipynb, kmeans.ipynb, MLP.ipynb, RF.ipynb, SVM.ipynb, each notebook has their own comment between code which can self explain well.
# The google drive link for all project file and dataset is here: https://drive.google.com/drive/folders/1J1paqLB1TGwpvOCAl9jsnf6bkAf_Kksq?usp=sharing