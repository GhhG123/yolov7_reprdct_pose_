# 深度学习论文复现过程：

1.确定找论文的平台：<https://paperwithcode.com>

2.确定研究方向：复现一篇人物姿势、关节关键点识别方向相关的论文

启发：https://youtu.be/1gZ-KaWjhGY AI外挂&FPS游戏，头部位置反馈

3.寻找符合作业要求的相关论文，整理复现流程



## 1.论文及源码

**选定论文：**[YOLOv7: Trainable bag-of-freebies sets new state-of-the-art for real-time object detectors](https://paperswithcode.com/paper/yolov7-trainable-bag-of-freebies-sets-new)

**论文源码：**https://paperswithcode.com/paper/yolov7-trainable-bag-of-freebies-sets-new#code

具体复现分支为pose的代码：https://github.com/WongKinYiu/yolov7/tree/pose#citation

<img src='Untitled Folder/Pose_estimation.png' width=500 align=left>

## 2.平台选择及环境配置

论文训练的数据集为coco：

​		1.coco数据集介绍：[COCO (Microsoft Common Objects in Context)](https://paperswithcode.com/dataset/coco)

​		[coco2017_download](https://github.com/ultralytics/yolov5/releases/download/v1.0/coco2017labels.zip)

平台：		

​		因为此数据集的大小为25GB，在bitahub平台上找不到，所以我选择了另外一个平台：[AutoDL](https://www.autodl.com/home)

​		选择原因：1.此平台在上传数据方面可以用阿里云盘作为中介，速度较快

​							2.有JupyterLab界面，文件目录可视化，可以直接用终端命令交互，反馈快

​							3.文件可以直接下载到本地等

环境配置：

​		**镜像：**PyTorch 1.11.0  Python 3.8(ubuntu20.04)  Cuda 11.3

​		**GPU：**RTX 4090(24GB) * 1升降配置 

​		**CPU：**22 vCPU AMD EPYC 7T83 64-Core Processor

​		**内存：**90GB

​		**硬盘系统盘：**30 GB

​		**数据盘：**免费:50GB  付费:30GB

## 3.复现结果与label对比

​	

​	label结果：

<img src='Untitled Folder/000000006471_labels_副本-9948577.jpg' width=600>

​		epochs=19结果：

<img src='Untitled Folder/000000006471_pred_副本.jpg' width=600>

详细对比：

​								**Labels**                                                                              **19**

<img src='Untitled Folder/截屏2023-07-21 22.13.55.png' width=350 align=left><img src='Untitled Folder/截屏2023-07-21 22.24.50.png' width=352>



<img src='Untitled Folder/截屏2023-07-21 22.14.05.png' width=350 align=left><img src='Untitled Folder/截屏2023-07-21 22.24.59.png' width=350 align=left>





















<img src='Untitled Folder/截屏2023-07-21 22.48.05.png' width=350 align=left><img src='Untitled Folder/截屏2023-07-21 11.33.57.png' width=350 align=left>

























## 文件组织目录：

1.coco文件夹由coco.zip解压

2.coco2017labels-keypoints.zip为pose分支中需要的labels，将解压后的2个文件(train2017.txt, val2017.txt)1个文件夹(labels)移动到**coco_kpts**文件夹下

3.将coco文件夹下的images文件夹迁移到**coco_kpts**文件夹下



root@autodl-container-37fe40aa96-027a6242:~/autodl-tmp# tree -L 3
.
├── coco
│   ├── annotations
│   │   └── instances_val2017.json
│   ├── labels
│   │   ├── train2017
│   │   └── val2017
│   ├── LICENSE
│   ├── README.txt
│   ├── test-dev2017.txt
│   ├── train2017.txt
│   └── val2017.txt
├── coco2017labels-keypoints.zip
├── coco_kpts
│   ├── images
│   │   ├── test2017
│   │   ├── train2017
│   │   └── val2017
│   ├── labels
│   │   ├── train2017
│   │   └── val2017
│   ├── train2017.cache
│   ├── train2017.txt
│   ├── val2017.cache
│   └── val2017.txt
├── coco.zip
├── yolov7-pose
│   ├── cfg
│   │   └── yolov7-w6-pose.yaml
│   ├── data
│   │   ├── coco_kpts_128.yaml
│   │   ├── coco_kpts.yaml
│   │   ├── hyp.pose.yaml
│   │   └── scripts
│   ├── detect.py
│   ├── hubconf.py
│   ├── LICENSE.md
│   ├── models
│   │   ├── common.py
│   │   ├── experimental.py
│   │   ├── export.py
│   │   ├── hub
│   │   ├── __init__.py
│   │   ├── __pycache__
│   │   └── yolo.py
│   ├── onnx_inference
│   │   ├── img.png
│   │   ├── sample_ips.txt
│   │   └── yolo_pose_onnx_inference.py
│   ├── README.md
│   ├── requirements.txt
│   ├── runs
│   │   └── test
│   ├── test.py
│   ├── train.py
│   ├── utils
│   │   ├── activations.py
│   │   ├── autoanchor.py
│   │   ├── aws
│   │   ├── datasets.py
│   │   ├── figures
│   │   ├── flask_rest_api
│   │   ├── general.py
│   │   ├── google_app_engine
│   │   ├── google_utils.py
│   │   ├── __init__.py
│   │   ├── loss.py
│   │   ├── metrics.py
│   │   ├── plots.py
│   │   ├── __pycache__
│   │   ├── torch_utils.py
│   │   └── wandb_logging
│   ├── weights
│   │   └── yolov7-w6-person.pt
│   └── yolov7-w6-pose.pt
└── yolov7-pose.zip
