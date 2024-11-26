# A Multimodal Unsupervised Coating Defect Detection Method Based on Dual-Branch Hybrid CNN-Mamba UNet
## Abstract
&emsp;&emsp;In order to obtain high-resolution multimodal image information, we developed a stereo structured light rotating platform system, which consists of both a hardware system and a software system. The overall system comprises multiple subsystems that work together to achieve its functionality. The hardware structure has two degrees of freedom, allowing the acquisition of multimodal information from various angles, as shown in Fig. 1. 
![image](https://github.com/TK941025/Defect-Detection/blob/main/images/fig_1.jpg)
&emsp;&emsp;The software system performs 3D reconstruction on the collected encoded images. We focus on curved coating workpieces in various orientations and utilize the stereo structured light rotating platform system to capture 2D image information and 3D point cloud data of the surface coating. Finally, we use the MVTec 3D-AD dataset as a reference to further process the collected images and point clouds, resulting in a standard multimodal coating defect dataset. The complete data collection and processing workflow is presented in Fig. 2.
![image](https://github.com/TK941025/Defect-Detection/blob/main/images/fig_2.jpg)
&emsp;&emsp;The multimodal coating defect dataset primarily consists of 2D and 3D defects, including six common types of coating defects: orange peel, scratch, bulge, particle, shrinkage hole, and stain, as shown in Fig. 3. 
![image](https://github.com/TK941025/Defect-Detection/blob/main/images/fig_3.jpg)
&emsp;&emsp;The dataset contains 248 samples, with 75 samples in the training set and 173 samples in the testing set. Each training sample consists of the corresponding RGB image and point cloud data, while each testing sample includes the corresponding RGB image, point cloud data, and a precise defect mask image. It is important to note that the point cloud data is used to generate depth anomaly samples, and only RGB images and depth images are used during network training and inference.
## Results
A detailed statistical analysis of the dataset is presented in Fig. 4.
|      Methods     |      I-AUROC     |    P-AUROC       | 
|:----------------:|:----------------:|:----------------:|
|CFA 	|88.3	|98.8|
|CFLOW-AD 	|92.3|	95.1|
|EfficientAD 	|85.3|	85.0|
|FastFlow 	|93.5|	96.7|
|PaDiM 	|97.1|	94.9|
|PatchCore	|94.6	|94.7|
|SimpleNet |	83.6|	84.9|
|RD++	|94.4|	95.2|
|DCMUNet (Only RGB)	|96.7	|97.7|

![image](https://github.com/TK941025/Defect-Detection/blob/main/images/fig_4.jpg)
|          |        | Seen             |                  |        | Similar          |                  |        | Novel            |                  | 
|:--------:|:------:|:----------------:|:----------------:|:------:|:----------------:|:----------------:|:------:|:----------------:|:----------------:|
|          | __AP__ | AP<sub>0.8</sub> | AP<sub>0.4</sub> | __AP__ | AP<sub>0.8</sub> | AP<sub>0.4</sub> | __AP__ | AP<sub>0.8</sub> | AP<sub>0.4</sub> |
| Ours     | 74.31  | 85.23            | 70.04            | 64.72  | 77.48            | 56.88            | 26.66  | 33.18            | 14.41             |
| Ours + CD| 75.39  | 86.75            | 70.60            | 65.75  | 78.82            | 57.52            | 27.38  | 34.17            | 14.56             |
![image](https://github.com/TK941025/Defect-Detection/blob/main/images/fig_5.jpg)
