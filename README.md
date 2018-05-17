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
### Step 2: Create neccessary files
First, create folder `VOCdevkit\Colonpolyps\` in the current directory. Then, go to the `VOCdevkit\Colonpolyps\` directory, and create four folders: `Annotations\`, `ImageSets\`, `JPEGImages\`, `labels\`. Details of the four folders are shown below:
* `Annotations\`
Contains xml documents of the images
![](https://github.com/Bogerchen/ColonPolyps_Detection/blob/imgs_to_edit_README/Annotations.png)
Each xml document displays labels of an image. Labels includes size of the image, names of the objects, locations of the objects.  See an example below:
![](https://github.com/Bogerchen/ColonPolyps_Detection/blob/imgs_to_edit_README/xml_example.png)
