In this project, I have used a custom dataset with 2 classes to achieve object detection using yolov7 in anaconda.
# Yolo : Install & Setup Environment :
Create a folder called yolov7 .
### Creating Virtual Env in Conda :
Use code in anaconda :
conda create -n envyolov7 python=3.9
### Activating Conda Environment
Use code in anaconda :conda activate envyolov7
# Downloading data :
Install siblime text and write the following code and save this file as downoadimages.py :
1. from simple_image_download import simple_image_download as simp
2. response simp.simple_image_download
3. keywords=["cat","dog"]
4. for kw in keywords:
5. response().download(kw, 50)
 ### Install a Image Downloading Library :
 In anaconda run : pip install simple_image_download==0.4 and then : python imagedownloads.py.
 This will start downloading 50 images of cat and dog each in simple images in 2 different folders. Merge the 2 folders into 1 folder called data.
 ### Installing Annotation tool :
 In anaconda, run the command pip install labelImg. This will install your annotation tool.Once the installation is done , run the command: labelImg. This will take you to labelImg. Change Save Dir to your labels folder and select YOLO . Click on Create Rectbox and start annotating your data. Click save and next img. Thus, you have your labels and images.
![WhatsApp Image 2024-05-05 at 18 16 59](https://github.com/AribaAnsari16/YOLO-Object-detection/assets/168963042/aaf3730c-eb96-4cc3-bb1f-ac45ac2f9c49)

 
 # Folder structure and installing libraries :
 1. In yolov7, create a folder called val i.e validation and cut and paste 20% of the images and labels downloaded ( 7 for cat and 7 for dog).![image](https://github.com/AribaAnsari16/YOLO-Object-detection/assets/168963042/e38c6d5f-874e-4dfd-8ee8-c61ea6a661b2)
2. Make another folder called train and paste the remaining images and labels here.
![image](https://github.com/AribaAnsari16/YOLO-Object-detection/assets/168963042/01bb8da9-d92d-4277-a6ac-c7ac17ced813)
3. Download the file from https://github.com/WongKinYiu/yolov7 into target folder and extract it
4. You will get a file called requiremwnts.txt. Run this command in anaconda: pip install –r requirements.txt . This will download all your needed libraries.
5. Go to yolov7_custom folder, Make a copy of coco.yaml file and name it custom_data.yaml . Make changes in this file according to your data.Also change the nc in yolov7custom.yaml file to the number of classes in your data.
# Training :
In anaconda, run the command :python train.py --workers 1 --device cpu --batch-size 1 --epochs 50 --img 128 128 --data data/customdata.yaml --hyp data/hyp.scratch.custom.yaml --cfg cfg/training/yolov7custom.yaml --name yolov7_custom --weights yolov7.pt .You can change the parameters accordingly. I have used cpu , but you can also run this using gpu .
This will give you 2 files called best.pt and last.pt . Chane the name of best.pt to yolov7-custom.pt and copy it to your yolov7 folder.
# To check your model :
Download any image of cat and dog from google and name it 1.jpeg and 2.jpeg .Run the command :python detect.py --weights yolov7-custom.pt --conf 0.4 --img-size 12
8 --source 1.jpeg --view-img --no-trace .
![image](https://github.com/AribaAnsari16/YOLO-Object-detection/assets/168963042/de0fe75d-6ec4-4b54-962c-f648a29a64dc)

This will save the result in detect folder in runs (in yolov7-custom ) 

![1](https://github.com/AribaAnsari16/YOLO-Object-detection/assets/168963042/8d10dc71-bc30-4934-9bfb-e65a9dc4b409)
![2](https://github.com/AribaAnsari16/YOLO-Object-detection/assets/168963042/c7d900fb-5112-4603-a898-50129713768e)

We can see that the model is accurate.






 
