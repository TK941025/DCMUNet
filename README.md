# A Multimodal Unsupervised Coating Defect Detection Method Based on Dual-Branch Hybrid CNN-Mamba UNet

## Abstract
&emsp;&emsp;In order to obtain high-resolution multimodal image information, we developed a stereo structured light rotating platform system, which consists of both a hardware system and a software system. The overall system comprises multiple subsystems that work together to achieve its functionality. The hardware structure has two degrees of freedom, allowing the acquisition of multimodal information from various angles, as shown in Fig. 1. 
<p align="middle"> 
  <img src="https://github.com/TK941025/Defect-Detection/blob/main/images/fig_1.jpg" width="450" /> 
  <br>
  Fig. 2.  Stereo structured light rotating platform physical prototype.
</p>

<!-- ![image1](https://github.com/TK941025/Defect-Detection/blob/main/images/fig_1.jpg) -->
&emsp;&emsp;The software system performs 3D reconstruction on the collected encoded images. We focus on curved coating workpieces in various orientations and utilize the stereo structured light rotating platform system to capture 2D image information and 3D point cloud data of the surface coating. Finally, we use the MVTec 3D-AD dataset as a reference to further process the collected images and point clouds, resulting in a standard multimodal coating defect dataset. The complete data collection and processing workflow is presented in Fig. 2.
<p align="middle"> 
  <img src="https://github.com/TK941025/Defect-Detection/blob/main/images/fig_2.jpg" width="450" /> 
  <br>
  Fig. 2.  Categories and analysis of multimodal coating defect dataset.
</p>

&emsp;&emsp;The multimodal coating defect dataset primarily consists of 2D and 3D defects, including six common types of coating defects: orange peel, scratch, bulge, particle, shrinkage hole, and stain, as shown in Fig. 3. 
<p align="middle"> 
  <img src="https://github.com/TK941025/Defect-Detection/blob/main/images/fig_3.jpg" width="450" /> 
  <br>
  Fig. 3.  Categories and analysis of multimodal coating defect dataset.
</p>

The structure of the multimodal coating defect dataset：

dataset  
&emsp;&emsp;├── ground_truth  
&emsp;&emsp;&emsp;&emsp;├── bulge  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── 1_mask.png  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── ... ...  
&emsp;&emsp;&emsp;&emsp;├── mixed  
&emsp;&emsp;&emsp;&emsp;├── orange peel  
&emsp;&emsp;&emsp;&emsp;├── particle  
&emsp;&emsp;&emsp;&emsp;├── scratch  
&emsp;&emsp;&emsp;&emsp;├── shrinkage hole  
&emsp;&emsp;&emsp;&emsp;└── stain  
&emsp;&emsp;├── test  
&emsp;&emsp;&emsp;&emsp;├── bulge  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── rgb  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── 1.png  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── ... ...  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;└── xyz  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── 1.tiff  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── ... ...  
&emsp;&emsp;&emsp;&emsp;├── mixed  
&emsp;&emsp;&emsp;&emsp;├── orange peel  
&emsp;&emsp;&emsp;&emsp;├── particle  
&emsp;&emsp;&emsp;&emsp;├── scratch  
&emsp;&emsp;&emsp;&emsp;├── shrinkage hole  
&emsp;&emsp;&emsp;&emsp;└── stain  
&emsp;&emsp;└── train  
&emsp;&emsp;&emsp;&emsp;├── good  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── rgb  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── 1.png  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── ... ...  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;└── xyz  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── 1.tiff  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├── ... ...

&emsp;&emsp;The dataset contains 248 samples, with 75 samples in the training set and 173 samples in the testing set. Each training sample consists of the corresponding RGB image and point cloud data, while each testing sample includes the corresponding RGB image, point cloud data, and a precise defect mask image. It is important to note that the point cloud data is used to generate depth anomaly samples, and only RGB images and depth images are used during network training and inference. 
## Results
TABLE I. Comparison of DCMUNet (only RGB) with State-of-the-Art Methods on Multimodal Coating Defect Dataset


 
|      Methods     |      I-AUROC     |    P-AUROC       | 
|:----------------:|:----------------:|:----------------:|
|         CFA    	|88.3             	|**98.8**          |
|CFLOW-AD          |92.3              |95.1              |
|EfficientAD 	     |85.3              |85.0              |
|FastFlow        	|93.5              |96.7              |
|PaDiM          	 |97.1              |94.9              |
|PatchCore	       |94.6              |94.7              |
|SimpleNet         |83.6              |84.9              |
|RD++	            |94.4              |95.2              |
|DCMUNet (Only RGB)	|**96.7**              |97.7        |


<p align="middle"> 
  <img src="https://github.com/TK941025/Defect-Detection/blob/main/images/fig_4.jpg" width="500" /> 
  <br>
  Fig. 4.  Comparison of coating defect detection results.
</p>


TABLE II. Comparison of DCMUNet with Other State-of-the-Art Multimodal Methods on Multimodal Coating Defect Dataset 
|      Methods     |      I-AUROC     |    P-AUROC       | 
|:----------------:|:----------------:|:----------------:|
|AST (RGB + depth) |91.8             	|83.5              |
|BTF (RGB + depth) |93.1              |95.9              |
|M3DM (RGB + depth)|77.8              |92.0              |
|Ours (RGB + depth)|**99.3**             |**98.2**            |


<p align="middle"> 
  <img src="https://github.com/TK941025/Defect-Detection/blob/main/images/fig_5.jpg" width="450" /> 
  <br>
  Fig. 5.  Qualitative results of the DCMUNet method for the detection of coating defects.
</p>

