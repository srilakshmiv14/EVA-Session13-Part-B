# EVA-Session-13

Single Object Detection using YOLOv3

Steps: 
1.	Collecting an own dataset of 500 images. Here we downloaded 500 images of Chota Bheem.
2.	Annotated the images using Annotation Tool which has been referred from https://github.com/miki998/YoloV3_Annotation_Tool. After annotation done, processed the images so that getting proper labels and images of our datatset.
3.	Created a Folder name as “YoloV3” . downloaded weights from the specified link and placed in yolov3 folder ‘weights”. 
4.	Also placed yolov3-spp-ultralytics.pt in weights file inside the YoloV3 folder.
5.	Prepared custom.data file in the strucrure given as :
customdata  Images and Labels folders in it which has been processed and taken from annotated imageset.
custom.names  having class name in it. Here we took class name as Chota_Bheem.
custom.txt  as its custom data arranged in an order.
6.	Placed all the remaining files in YoloV3 folder such as models.py, train.py, test.py and detect.py etc..
7.	For COCO's 80 classes, VOLOv3's output vector has 255 dimensions ( (4+1+80)*3). Now we have 1 class, so we would need to change it's architecture.
8.	Copy the contents of 'yolov3-spp.cfg' file to a new file called 'yolov3-custom.cfg' file in the data/cfg folder.
9.	In cfg file , Replace the filters entries to 15 whichever was 255. Because its of only 1 class we have taken here. (Change 255 to 18 = (4+1+1)*3)
10.	Replace for classes = 1 in place of 'classes=80' in all the 3 entries of file. 
11.	Set burn_in to 100
12.	Set max_batches to 5000
13.	Set steps to 4000,4500
14.	Run this command python train.py --data data/customdata/custom.data --batch 10 --cache --cfg cfg/yolov3-custom.cfg --epochs 3 –nosave
15.	Here we trained the custom dataset for 300 epochs.
16.	Then downloaded a Chota Bheem video of short time, using ffmpeg converted into frames and kept in a folder inside YoloV3.
17.	Then after getting trained , ran the command
“python detect.py  –source  --filename  --conf-thres 0.3 --output output_folder_name”	
18.	The video with the object (Chota Bheem) detection was in the output folder.
19.	Then processed the video with audio using ffmpeg.

Here the Github Project : Chota_Bheem – single object detection using YoloV3. 


