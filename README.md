## DL_Report2 Multi-Task Learning with Experience Replay

This repository contains Python code for a multi-task learning system that sequentially trains a single unified model on three distinct computer vision tasks: Semantic Segmentation (VOC), Object Detection (COCO), and Image Classification (Imagenette). A key feature of this system is the implementation of Experience Replay to mitigate catastrophic forgetting during sequential training.

# Report Notion Link :

https://www.notion.so/Unified-OneHead-Multi-Task-Challenge-2119b32cdbea801594f9c7370784ab36?source=copy_link

# Colab Link :

https://colab.research.google.com/drive/1583wthWhqaWKp67YzONm-BwBVPUAoQQr?usp=sharing

# Features

Unified Model Architecture: A single UnifiedModel is designed with a MobileNetV3 backbone, a Feature Pyramid Network (FPN) neck, and a shared single-branch head that outputs predictions for all three tasks.

Sequential Training: The model is trained in stages:

Stage 1: Semantic Segmentation

Stage 2: Object Detection (with replay of segmentation data)

Stage 3: Image Classification (with replay of segmentation data)

Experience Replay: To combat catastrophic forgetting, a portion of the original segmentation training data is replayed during the subsequent detection 

and classification stages. This helps maintain the model's performance on previously learned tasks.

Automated Data Preparation: A dedicated script handles the downloading, extraction, and organization of mini versions of the Imagenette, PASCAL VOC, and 

COCO datasets.

Comprehensive Evaluation: The training process includes evaluation metrics for each task (mIoU for segmentation, mAP and Top-1 accuracy for 

classification).

Performance Monitoring: Tracks model parameters, inference time, and performance drops across stages to ensure compliance with predefined requirements.

Training Visualization: Automatically generates plots to visualize training loss and metric evolution across all stages.

Here's a README.md for your project, combining information from the provided code snippets.

Multi-Task Learning with Experience Replay

This repository contains Python code for a multi-task learning system that sequentially trains a single unified model on three distinct computer vision 

tasks: Semantic Segmentation (VOC), Object Detection (COCO), and Image Classification (Imagenette). A key feature of this system is the implementation 

of Experience Replay to mitigate catastrophic forgetting during sequential training.

#  How to Run

Environment Setup
Python: Python 3.8 or higher is required.

Google Colaboratory: This project is designed to be run directly in Google Colab, which provides the necessary environment and GPU access.

Required packages: All necessary packages (like torch, torchvision, tqdm, scikit-learn, matplotlib, Pillow) will be automatically installed within the Colab notebook when you run the first code cell.

# Dataset Preparation
The dataset preparation is fully automated within the Colab notebook. When you execute the first relevant code cell, it will:

Clean up any existing data directory from previous runs.
Create the necessary directory structure (data/imagenette_160, data/mini_coco_det, data/mini_voc_seg).
Download and extract mini versions of the Imagenette, PASCAL VOC, and COCO datasets from their respective URLs directly into the Colab environment.
Process and organize images and annotations within these directories.
Clean up temporary raw download files to save space.
No manual download or extraction steps are needed outside of running the Colab notebook cells.

# Datasets Structure
.
├── data/
│   ├── imagenette_160/             # Prepared Imagenette data
│   │   ├── train/
│   │   └── val/
│   ├── mini_coco_det/            # Prepared mini COCO detection data
│   │   ├── train/
│   │   ├── val/
│   │   └── annotations/
│   ├── mini_voc_seg/             # Prepared mini VOC segmentation data
│   │   ├── train/
│   │   └── val/
│   └── raw_downloads/            # (Temporary) Raw downloaded data

# Open and Execute the Colab Notebook
Access the Notebook:

Open the colab.ipynb file directly in Google Colab.
Run All Cells in Order:

Once the notebook is open, click on Runtime -> Run all in the Colab menu.
Alternatively, you can execute each cell sequentially from top to bottom.
The notebook is structured into logical sections (similar to the "Cells" mentioned in your original prompt) that handle:

Installation and Imports: Installing libraries and importing necessary modules.
Dataset Preparation: The automated download and organization of data.
Model Definitions: The UnifiedModel architecture and custom Dataset classes.
Training Engines and Utilities: Functions for training each stage and evaluating performance.
Experiment Execution: The main sequential training process with experience replay.
Results Analysis and Plotting: Generating summary statistics and visualizations of training loss and performance metrics.

# Contact
If you encounter any issues or have questions, please reach out via Moodle or email to jooj30136@gmail.com.
