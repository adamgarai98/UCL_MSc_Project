# Computer vision for the Digitisation of Pinned Insect Specimens

![Video0](https://github.com/adamgarai98/UCL_MSc_Project/blob/main/Misc/video0.gif)

-
This repository contains all the associated code (Jupyter notebooks implemented in Google Colabs)  and data for my Masters (Ecology and Data Science) thesis at UCL, partnered with the Natural History Museum, London.
-

Using a small subset of ALICE generated data containing images of pinned insect specimens, I built proof-of-concept models that achieved high performance in image classification with a dorsal model average F1-score of 0.96 and lateral model average F1-score of 0.99 on the test set, and high performance is also shown in the instance segmentation model with an AP0.5:0.95 of 72.0 for bounding box predictions and 62.9 for segmentation masks for single class specimen predictions. Following these results I built a pipeline to combine these models. Both approaches were also tested on a new data source of images and videos I took of specimen drawers at the NHM. Implementation and results can be seen in the associated notebooks.

# Dataset Creation and Analysis
  
  These notebooks contain the code used to process and analyse my given data. To use the notebooks please download a ZIP file stored in Google Drive, containing the images below:
 
[Download ALICE Data here.](https://drive.google.com/file/d/1e0UFL_vnp1OShL90CNA_9ci6WYUIc28x/view?usp=sharing)

# Model Training and Evaluation
These notebooks were used to train and evaluate my models. Saved models are also included within this repository however the segmentation model must be downloaded from the Google Drive link below:

[Download Segmentation model here.](https://drive.google.com/file/d/1u2TuhlPGwn5A3oZDE6HO_wXwz0gxnorl/view?usp=sharing)

## Classification
Based on the view angle of the specimen (lateral or dorsal) two Xception models were built using partial transfer learning to classify the specimens in the images at a species level. All results are shown within the notebooks.

The notebooks show how to load and use the models.

## Segmentation
ADD image
I manually annotated and drew associated polygon masks around the specimen in each image using the [VGG Image Annotator (VIA)](https://www.robots.ox.ac.uk/~vgg/software/via/) tool. The annotations are then exported to [RoboFlow](https://roboflow.com/) for random image augmentations, and then exported for use within the notebook. Using [Detectron2,](https://github.com/facebookresearch/detectron2) an instance segmentation model was built and trained to segment specimens within the images. 

The notebook shows how to load and use the model, and also has functionality for running predictions on videos.

# Combined Pipeline
This notebook contains the code to first segment all specimens in an image, then pass the predicted bounding box images to the classification model.
ADD Image
