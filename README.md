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
`voc_names.txt` is under `darknet\data\` directory displaying names of all classes. Each line of this txt file is the name of a single class. Change each line to match the names of polyps. See the figure above.
![](https://github.com/Bogerchen/ColonPolyps_Detection/blob/imgs_to_edit_README/voc_names.png)
Or just replace the `voc_names.txt` in `darknet\data\` with the `voc_names.txt` in the master branch of this repository.

* Modify `\cfg\yolov3-voc.cfg`
This file displays the network architecture of YOLOv3. To train on my own colon polyps dataset, I need to change the dimensions of the output layer, that is, change the number of filters from 75 to 18 of the three layers which come before the 'yolo' layers. The number of filters is computed using formula <img src="https://latex.codecogs.com/svg.latex?\Large&space;x=3\times(5+C)" title="\Large x=3\times(5+C)" />, where C denotes number of classes. For example, in my colon polyps detection application, I only have one type of object to detect, so C=1.
A shortcut of the modified cfg file is shown below:
![](https://github.com/Bogerchen/ColonPolyps_Detection/blob/imgs_to_edit_README/yolov3-voc.cfg.png)
Or just replace the `darknet\cfg\yolov3-voc.cfg` with the `\cfg\yolov3-voc.cfg` file in teh master branch of this repository.
