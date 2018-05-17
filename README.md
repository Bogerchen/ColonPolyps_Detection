# ColonPolyps_Detection
Codes and key procedures to construct a ColonPolyps detection system based on [YOLOv3 architecture](https://pjreddie.com/darknet/yolo/). All procedures below are on `Linux` with CUDA installed.
## Preparatory Steps
### Step 1: Download the pre-trained YOLOv3 model
Run the codes below in the command line to have Darknet installed:
```Bash
git clone https://github.com/pjreddie/darknet
cd darknet
make
```
### Step 2: Create necessarry files
First, create folder `VOCdevkit\Colonpolyps\` in the current directory. Then, go to the `VOCdevkit\Colonpolyps\` directory, and create three folders: `Annotations\`, `ImageSets\`, `JPEGImages\`. Details of the three folders are shown below:

* `Annotations\` Contains xml documents of the images
![](https://github.com/Bogerchen/ColonPolyps_Detection/blob/imgs_to_edit_README/Annotations.png)
Each xml document displays labels of an image. Labels includes size of the image, names of the objects, locations of the objects.  See an example below:
![](https://github.com/Bogerchen/ColonPolyps_Detection/blob/imgs_to_edit_README/xml_example.png)

* `ImageSets\` Contains txt files that save the ids of images
Create directory `Main\` under the `ImageSets\`, then put txt files into `ImageSets\Main\` . The txt files save ids of the images for the train set, validation set and test set, respectively. The following two figures shows the outline of `ImageSets\Main\` and the txt file of the test set respectively.
![](https://github.com/Bogerchen/ColonPolyps_Detection/blob/imgs_to_edit_README/outline_of_ImageSets_Main.png)
![](https://github.com/Bogerchen/ColonPolyps_Detection/blob/imgs_to_edit_README/test_ids.png)

* `JPEGImages\` Contains all images for training. validating and testing.
Worth mentioning that images can be not only .jpeg or .jpg format but also .png format. Maybe other formats like .gif, .bmp are ok.
![](https://github.com/Bogerchen/ColonPolyps_Detection/blob/imgs_to_edit_README/JPEGImages.png)

Second, run `voc_label.py` in `darknet/` for converting xml documents to yolov3 readable labels. Before running `voc_label.py`, we need to modify voc_label.py, that is, change directories of files. voc_label.py generates labels for each image and txt files displaying paths and ids of train, validation and test images. For more details see `voc_label.py`.

### Step 3: Modify corresponding files
* Change `voc_names.txt`
