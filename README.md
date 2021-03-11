# vehicle-Recognition-using-deep-learning-algorithm-
vehicle recognition using YOLO-V3

## Discription
> in this project,in summary,first we use vehicle image dataset about ~18000 iamges,in 123 various classes,and lebel them then we train our dataset with YOLO-V3 Object Detection model,and test model with our weights,we found that due to imbalance dataset (is not equal number of images in our classes),we get ~0.6 accuracy in our traiing dataset,so we try that by decreasing the imbalance dataset and decrease our classes to 35 vehicle model,approximately,we get ~0.8 accuracy by balancing dataset,the summary of our result is documented in this github repo.in below you see our compact model architecture:

> ![Capture1](https://user-images.githubusercontent.com/53394692/110747263-5a12a580-8253-11eb-998d-2fab96ff9515.PNG)

## DATASET
> our dataset was captured by group of people in the car trading company in Tehran,so by their authority and permit,we accessed their dataset about ~18000 images,about ~123 various classes of vehicle brand,in different conditions such as (light,illumination,angle,camera distance,different weather conditions(snowy,foggy,rainy,...)) and captured with  different phone cameras with different resolution quality,we have prepared dataset for training process.below,you see sample of our datset:

|                         dataset                                       | 
| --------------------------------------------------------------------- | 
| ![Capture2](https://user-images.githubusercontent.com/53394692/110747559-ce4d4900-8253-11eb-90b3-0077f2b2aeeb.jpg) | 
| ![Capture3](https://user-images.githubusercontent.com/53394692/110747616-ddcc9200-8253-11eb-9606-cef4d51e7377.jpg) |
| ![Capture4](https://user-images.githubusercontent.com/53394692/110747654-ed4bdb00-8253-11eb-8100-9a595ba61421.jpg) |

## Preprocess
> for preparing image dataset for training phase,i labeled my images helping by [Make Sense](https://www.makesense.ai/) online website,with easy tools i labeled my `Vehicle`  and saved their bounding box coordinates in `.txt` files,i downloaded them from website,so each image in my dataset had one `.txt` label.with compelet detailes,we will explain this procedure in another `repo` in my github.

## training procedure
* for training license-plate and character recognition phase,you must set a few files,so follow below instructions:

  * 1. put `.cfg` files related to YOLO-V3 of LP `yolov3-1cls.cfg` and Character recognition `yolov31clstochar.cfg` in `cfg` directory,for getting more information about `.cfg` file,follow this [link](https://medium.com/analytics-vidhya/custom-object-detection-with-yolov3-8f72fe8ced79) about configuring YOLOV3 for your object detection task.
  
  * 2. put your dataset images and labels in `training/images` directory `training/labels` directory.
  
  * 3. set label names in two files `object.names` and `objecttochar.names` in `training` directory.
  
  * 4. set splitted dataset of train and test iamges in format of `.txt` as `train.txt` and `test.txt` in `training` directory.for splitting data set run to codes as `train_test.py` and `train_testtochar.py` ,for getting better information go to this [link](https://medium.com/analytics-vidhya/custom-object-detection-with-yolov3-8f72fe8ced79)
  
  * 5. set pathes of `train.txt`,`test.txt` and `object.names` for both of two YOLO-V3 as `trainer.data` and `trainertochar.data` in `training` directory. 
   
  * 6. put pretrained of YOLO-V3 weights as `yolov3.weights` in `weights` directory. 

* after confuiguring,then you run `train.py` below command for training in `YoloV3-Custom-Object-Detection-master` directory:
```
python3 train.py --epochs 110 --data training/trainertomodels.data --cfg training/yolov3-123clstomodels.cfg --batch 8 --accum 1
```
* after ending programs,you must run these instructions for converting `pytorch` format to `darknet` format,after that the `converted.weights` is build in root directory.
```
python3  -c "from models import *; convert('training/yolov3-1cls.cfg', 'weights/best.pt')"




## LICENSE
> this project was done by me `behnoud shafizadeh` and my co-worker `navid pourhadi` in the kharazmi university lab,supervised by `DR.Farshad Eshghi` and `DR.Manoochehr KelarEstaghi`,so the full source of code and dataset in this project are out authority and relatede to `kharazmi university of tehran`,so if you would like to contiribute with our group and access to out document,please contact with our emails : `behnud.shafizadeh@gmail.com` and `npourhadi1998@gmail.com`,thanks for your consideration.
