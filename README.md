# The Chicago AWS Architecting for ML - Ship Detection

![Alt](/ships_summary_page.jpeg)


## Overview

In this project our team will locate ships in images, and put an aligned bounding box segment around them. 

Here’s the backstory: Shipping traffic is growing fast. More ships increase the chances of infractions at sea like environmentally devastating ship accidents, piracy, illegal fishing, drug trafficking, and illegal cargo movement. This has compelled many organizations, from environmental protection agencies to insurance companies and national government authorities, to have a closer watch over the open seas.


## Datasets

The dataset is based on the Kaggle competion data available at https://www.kaggle.com/c/airbus-ship-detection/data
Many images do not contain ships, and those that do may contain multiple ships. Ships within and across images may differ in size (sometimes significantly) and be located in open sea, at docks, marinas, etc.

For this metric, object segments cannot overlap. There were a small percentage of images in both the Train and Test set that had slight overlap of object segments when ships were directly next to each other. Any segments overlaps were removed by setting them to background (i.e., non-ship) encoding. Therefore, some images have a ground truth may be an aligned bounding box with some pixels removed from an edge of the segment. These small adjustments will have a minimal impact on scoring, since the scoring evaluates over increasing overlap thresholds.

The train_ship_segmentations.csv file provides the ground truth (in run-length encoding format) for the training images. The sample_submission files contains the images in the test images.


## Modeling Strategy

Use of openCV library to preprocess and augment the images and try different object detection approaches in AWS SageMaker and figure out ways to address the presence of:
* clouds near ships
* ships under haze or within clouds
* large wake behind the ship due to its movement
* individual ships in marinas
* sun reflection on water aroud the ship
* confusion with waves caused by wind
* partially visible ships
* individual ships discrimination when two or more ships are coupled together or when other objects are around, e.g. buoys, barges, wind turbines, etc.


## End Goal

Locate ships in images and put an aligned bounding box segment around them. 
