# RealismCNN
Project webpage: http://www.eecs.berkeley.edu/~junyanz/projects/realism/  
Contact: Jun-Yan Zhu (junyanz at eecs dot berkeley dot edu)


## Paper
Learning a Discriminative Model for the Perception of Realism in Composite Images  
Jun-Yan Zhu, Philipp Krähenbühl, Eli Shechtman and Alexei A. Efros  
IEEE International Conference on Computer Vision (ICCV). 2015.  


## Overview
This is the authors' implementation of (1) visual realism prediction and (2) color adjustment methods, described in the above paper. Please cite our paper if you use our code and data for your research.


## Installation
* Download and unzip the code.

* Install caffe from https://github.com/BVLC/caffe
  - Compile both caffe and matcaffe.
  - Set MATCAFFE_DIR in our code "SetPaths.m".

* Install libsvm (included): run "make.m" if you cannot use precompiled mex files.

* Download realismCNN models and test dataset:
  - RealismCNN models: http://www.eecs.berkeley.edu/~junyanz/projects/realism/realismCNN_models.zip    
  - For realism prediction: http://www.eecs.berkeley.edu/~junyanz/projects/realism/human_evaluation.zip  
  - For color adjustment: http://www.eecs.berkeley.edu/~junyanz/projects/realism/color_adjustment.zip  

* To run our method on your own data, please modify **EXPR_NAME**, **MODEL_DIR**, **DATA_DIR**, **WEB_DIR**. See each script for further details.


## MATLAB functions
* Realism Prediction:
  - **EvaluateRealismCNN.m**: apply RealismCNN model directly on human evaluation dataset. This script can reproduce RealismCNN results in Table 1.
  - **EvaluateRealismCNN_SVM.m**: train a SVM model on top of fc6/fc7 layer's features extracted by our RealismCNN model. This script can reproduce RealismCNN+SVM results in Table 1.
  - **PredictRealism.m**: Given a collection of composite images as input, this script will compute the visual realism scores for all the images, and display the top/bottom ranked images by their realism scores.

* Color Adjustment:
  - **ColorAdjustmentScript.m**: reproduce color adjustment results reported in the paper.
  - **OptimizeColorAdjustment.m**: recolor a single image given a source image (i.e. object), a target image (i.e. background), and an object mask. We assume that the image sizes of source, target, and mask are the same.
  - **ColorAdjustmetnBatch.m**: recolor multiple images by calling "OptimizeColorAdjustment.m" in batch mode.
