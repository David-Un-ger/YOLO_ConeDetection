# YOLO_ConeDetection
Create a traffic cone detector using Tensorflow 2

work in progress:
- dataset is cleaned up
- visualization and training works
- still some issues with finding the ideal loss function


Next steps:
- apply transfer learning on 8x8 grid images and just use objectness as loss function
- apply it on 16x16 grid
- further specify the loss function


![image](https://user-images.githubusercontent.com/35065831/139665479-f9fa5295-4345-4d41-b9b5-c11aa58732e7.png)



## Steps:
- basic CNN architecture / class - ok
- input pipeline - ok
- visualisation - ok
- IoU - ok
- 2 BB per cell
- Loss function
- non maxima suppression
- Train/optimizer
- training
- better architecture, batch_norm
- augmentation

- result: sigmoid on center + exponent of w+h

## General steps:
- Yolo on cones / on COCO
- introduce different scales
- Yolo on COCO
- introduce anchor boxes
- CARLA data
- Yolo on Carla

## yolo-format (called label(s) in this notebook:
- each image has its own label file with the same file name
- each cone of an image is described by one line
- Format in txt files: class, x_center, y_center, width_bbox, height_bbox
- Format used in this notebook: [objectness, x_center, y_center, width_bbox, height_bbox, class0, c1, c2, c3, c4, c5, c6]

- 0 blue
- 1 yellow
- 2 orange-small
- 3 orange-big (shown in red)
- 4 yellow-big (shown in white)
- 5 green
- 6 lying

## YOLO-Output (called y / y_pred / y_true in this notebook:

Per S x S grid cell, e.g. 8x8:
x,y, height, width, objectness, prob per class

--> 8x8x(4+1+7) = 8x8x12 = 768 output neurons
