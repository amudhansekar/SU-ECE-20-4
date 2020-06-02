# SU-ECE-20-4

This repository holds the final deliverables of Seattle University Team ECE 20.4 for Panthera.

This will include a user guide for both the local version of Recognition.py as well as  

## Contents

The folder "Databricks_Spark_notebook" contains a user guide for the Azure Datbricks
version of Recognition.py. The Azure Databricks version is available in both ".py" and ".ipynb" if you are running
python notbook software.

The folder "Image_Sets" contains different sets of images that vary in size. They range from a set of 3 images to 
larger sets of 32 images. In these folders, a config.json file that relates to each individual photo set will be
there as well as its corresponding score_matrix.csv file. 

The folder "Recognition" contains both easy_run.py as well as Recognition.py. Also in this folder there is 
a user guide for how to set up and run Recognition.py

## Setup
Certain software needs to be installed in order to be able to run Recognition.py. Changes also need to be made
in Recognition.py to write to the correct folder, or depending on the operating system. 

#### OpenCV:
  If you are running python 2, install OpenCV with 
  ```bash
  pip install opencv-contrib-python==3.3.1.11
  ```

  If you are running python 3, install OpenCV with 
  ```bash
  pip install opencv-contrib-python==3.4.2.16
  ```

#### Tensorflow 
Tensorflow needs to be installed on your system as well and can be downloaded at this website: 
[Tensorflow](https://www.tensorflow.org/install)

#### Markov Clustering
In order to install the correct software for markov clustering onto the system use the command:
  ```bash
  pip install markov_clustering"
  ```

## Usage

#### config.json
One config.json files belongs to each individual image set. Here is where changes can be made for the type of templating
that Recognition.py uses. A in templating will call for a manual ROI to be inserted. A 1 will use the automatic templates
that were generated and uploaded by Matlab, and a 2 will use the Mask R-CNN templates generated during runtime. 

![config.json](https://github.com/caballe4/SU-ECE-20-4/blob/master/Images_For_README/Screen%20Shot%202020-06-01%20at%2011.18.22%20AM.png)

#### easy_run.py
The template that will can be seen below needs to be filled out with the correct path. Replacing the tilde (~) with the
path will allow Recognition.py to read these correctly and run properly. Without the correct path, Recognition.py will
not run properly. 

![easy_run.py tempalte](https://github.com/caballe4/SU-ECE-20-4/blob/master/Images_For_README/Screen%20Shot%202020-06-01%20at%202.55.57%20PM.png)

A complete version of easy_run.py can be seen below for reference. This was completed using MacOS. When using 
Windows it may be necessary to replace "/" with either "//" or "\". 

![Complete easy_run.py](https://github.com/caballe4/SU-ECE-20-4/blob/master/Images_For_README/Screen%20Shot%202020-06-01%20at%202.59.57%20PM.png)

#### Line Changes
Specific paths must be changed depending on the operating system
If running recognition on Windows, line 72 needs to be commented out, and line 74 needs to be uncommented.
![](https://github.com/caballe4/SU-ECE-20-4/blob/master/Images_For_README/Screen%20Shot%202020-06-01%20at%208.30.17%20PM.png)


In line 945, the image path needs to be updated to the current image directory path.
![](https://github.com/caballe4/SU-ECE-20-4/blob/master/Images_For_README/Screen%20Shot%202020-06-01%20at%208.33.29%20PM.png)


In line 1087, after the editing of the images takes place, the format that it is in, isn't recognized by the
Mask R-CNN template generator. Therefore, comment out 1087 if you would like to run with Mask R-CNN. 
![](https://github.com/caballe4/SU-ECE-20-4/blob/master/Images_For_README/Screen%20Shot%202020-06-01%20at%208.33.56%20PM.png)

#### Command Line
Once all this has been complete, Recognition.py can be run in a MacOS terminal or Windows Powershell with the command

```bash
python easy_run.py
```

## TODOs

#### Multiple Templates
Currently, if the Mask R-CNN detects an image that has two leopards, or it generats two different templates, than the output will only a blank black template. This is because Recognition.py isn't set up to handle the matching of two snow leopards in one image. This is one change that will need to occur.

#### Image Enhancement and Mask R-CNN
Mask R-CNN and the image enhancement cannot be run at the same time because of the changes that occur to the image. There 
is a dimension error that Mask R-CNN cannot match. A solution could be to move the image enhancement elsewhere in the code, or find a way to convert the dimensions of the enhanced image so that it will be accepted by Mask R-CNN.

#### Clustering Tests and Feature Extraction
The clustering algorithms need further testing to determine the accuracy that they currently have. One method to make
the algorithms more accurate while clustering SIFT descriptors is to use a Bag of Words method. Using this type of feature
extraction could make the clustering algorithms more accurate. 

#### Azure Databricks
Implement multiprocessing into the Databricks version of Recognition.py to decrease the runtime of the program. After this
is complete, fully integrate Recognition.py into Databricks to be able to run larger datasets. 
