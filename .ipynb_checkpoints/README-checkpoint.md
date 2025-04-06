# YOLO+Transformer

This project combines the power of YOLO (You Only Look Once) for fast object detection with the C3TR (Context-aware Cross-scale Transformer for Object Tracking) architecture to enhance accuracy and context understanding on a custom dataset.

The process of detecting and analyzing road surface damage plays a crucial role in improving traffic safety and reducing the cost of road infrastructure maintenance. Given the importance of this issue, automatic road damage detection using computer vision and deep learning has been proposed.
In this study, a custom dataset was first collected from the roads of Juybar County in Mazandaran. Then, through data augmentation and image processing techniques, the number and diversity of data samples were increased. Subsequently, YOLOv5, YOLOv8, and YOLOv10 models were trained on the prepared data, achieving mAP@0.5 scores of 0.858, 0.696, and 0.882 respectively.
Next, a semi-supervised learning approach was applied to leverage unlabeled data. This method achieved a satisfactory mAP@0.5 of 0.799, which is a promising result considering the limited amount of labeled data compared to the unlabeled portion.
Finally, to further enhance system performance, a Transformer-based module named C3TR was integrated with YOLOv5. This hybrid model achieved a mAP@0.5 of 0.858 with fewer training epochs than previous models.
The results demonstrate the effectiveness of combining Transformer-based modules with YOLO detection networks in the domain of road damage detection.

## colab code for train

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HastiRazipour/YOLO-C3TR/blob/main/YOLO-Transformer.ipynb)

## 📁 Structure
- `src/` contains training and evaluation code
- `model/` has the stracture model (.ymal file)
- `results/` includes evaluation results and plots

## 🧠 Model
The model is a yolo with C3TR trained on my dataset for juybar road damage detection.

## 🔧 Requirements
Install dependencies in Requirements.txt 


## link for our dataset
You can download the dataset from [Google Drive](https://drive.google.com/file/d/1G61lBk7_qMBkvVXO4S4wsAOa19HOr_QH/view?usp=sharing).


# Result
🧠 dataset inclide classes:
   Alligator Crack , Longitudinal Crack , Patching , Potholes , Transverse Crack
   
<img src="results/confusion_matrix_normalized.png" alt="confusion_matrix" width="600"/>  
The YOLO + C3TR hybrid model performs well in detecting road damages such as Alligator Cracks (with 0.91 accuracy) and Potholes (0.81), but it struggles to distinguish some classes from the background (like Longitudinal and Transverse Cracks), indicating a need for improved training data or model enhancement to better handle visually similar background conditions.

<img src="results/F1_curve.png" alt="F1_curve" width="600"/>  

The F1-Confidence curve shows that the optimal confidence threshold for the model is around 0.27, where the overall F1-score peaks at 0.84. Classes like Alligator Crack and Potholes perform more consistently, while Transverse Crack sees a significant drop in F1 at higher confidence levels, likely due to background similarity or limited data. As expected, all classes show a decline in performance at very high confidence values.

  
<img src="results/PR_curve.png" alt="PR_curve" width="600"/>  
The model demonstrates good performance in detecting road damages with an mAP@0.5 of 0.858. The highest accuracy is for the Potholes class at 0.914, while the lowest is for Patching, with 0.775.

<img src="results/results.png" alt="results" width="600"/>

<img src="results/P_curve.png" alt="P_curve" width="600"/> <img src="results/R_curve.png" alt="R_curve" width="600"/>

<img src="results/train_batch0.jpg" alt="train_batch0" width="600"/> <img src="results/val_batch0_pred.jpg" alt="val_batch0_pred" width="600"/>