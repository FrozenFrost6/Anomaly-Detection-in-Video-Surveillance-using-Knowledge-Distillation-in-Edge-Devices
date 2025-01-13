# Anomaly Detection in Video Surveillance using Knowledge Distillation in Edge Devices
## Problem Statement
Automated surveillance systems are required to quickly identify any anomalies and
send an appropriate response immediately. Anomaly detection can be directly done
on edge devices to tackle the problem of central sever scalability and can avoid
latency in data transmission to the central server. However, in order to perform
anomaly detection on edge nodes, compact models must be made to deploy onto
the limited space and compute capability of edge devices are required. This project
focuses on building a compact model using KD for anomaly detection which can
be deployed onto an edge node.


## URL / Source for Dataset:
	http://www.svcl.ucsd.edu/projects/anomaly/dataset.htm

## Software and Hardware requirements
The project was conducted in an environment comprising both hardware and
software components conducive to deep learning research and development. The
hardware setup included a high-performance laptop equipped with advanced
specifications suitable for model training.

	Hardware:
		• NVIDIA GeForce RTX 3070 Ti Laptop GPU (8GB VRAM)
		• 12th Generation Intel i7-12700H processor
		• 32 GB DDR5 RAM
		• 2 TB SSD
	Software:
		• Anaconda distribution
		• Python 3.9.16
		• Cuda Toolkit 12.1
		• TensorFlow 2.10.1
		• Jupyter Notebook



## Dataset Description
- Opted to use the UCSD PED1 and UCSD Ped2 Datasets which contains video data of pedestrians walking through a street, taken at 10 frames per second (fps). 
- The train data doesn't contain any anomalies, whereas the test data contains some anomaly.
- The Ped1 dataset contains around 34 train videos each containing 200 frames each and 36 test videos that contain some form of anomaly with 200 frames each.
- The Ped2 dataset contains 16 train videos and 12 test videos, each video containing 200 frames.
![seq12](https://github.com/user-attachments/assets/54e16233-25ab-49a0-949a-f24feab5576b)


## Methodology
The system uses a technique called Knowledge Distillation to perform this task. Knowledge Distillation is a technique in machine learning where knowledge from a more complex model, known as the teacher model, is transferred to a simpler model, known as the student model. The primary objective of KD is to create a student model that can mimic the behavior and predictions of the teacher model, typically with fewer parameters and computational resources.

![knowledgeDistillation](https://github.com/user-attachments/assets/7185248e-231f-40d0-97dc-4efa2ddbb883)

Using this technique, we trained multiple models and tried to achieve optimal scores.

## Proposed Architecture

![proposedArchitectureTwoTeachers](https://github.com/user-attachments/assets/eb185591-7511-45a3-a9d7-cc8109418a85)

- Teacher 1: Recurrent Autoencoder is specifically designed to capture temporal dependencies and patterns within the data.
- Teacher 2: Convolutional Autoencoder localizes anomalies within images by analyzing reconstruction errors at the pixel level.
- Student: Vanilla Autoencoder is a compact and hybrid model of both teachers.
- Distiller
	- During the forward pass, the function computes both reconstruction loss, which measures the dissimilarity between the input data and its reconstruction by the student model, and distillation loss, which quantifies the discrepancy between the student's output reconstructed image and that of the teacher model(s).
	- The total loss is computed as a weighted combination of reconstruction loss and distillation loss, with weights determined by parameters such as γ (student weight), α (teacher 1 weight), and β (teacher 2 weight).
	- The 3 weight distribution strategies we employed for testing are Equal, Unequal and Dynamic Weight distribution strategy.


## Model Architectures
### Teacher 1
![teacher1Architecture](https://github.com/user-attachments/assets/8c7fdc3f-c9de-4d9c-854f-9f26a63647a9)

### Teacher 2
![teacher2Architecture](https://github.com/user-attachments/assets/94887cdb-58d0-4c8a-8a2f-b1c0de7d328a)

### Students
![studentArchitecture](https://github.com/user-attachments/assets/971730a4-34a3-421f-a406-a0e198c741de)

## Model training
- All student models have the same architecture showed above and are trained on the same data as the teacher.
- Student 1 does not employ KD and trains and predicts on the data as a standalone model.
- Student KD1-2 distills knowledge from a single teacher using Teacher 1 and Teacher 2 respectively.
- Student KD3-6 distills knowledge from Teachers 1 and 2 by assigning unequal weights to the individual losses.
- Student 7 follows average weight allocation strategy to distill knowledge from Teachers 1 and 2.
- Student 8 follows a dynamic weight allocation strategy to distill knowledge from Teachers 1 and 2

## Demonstration
For the given dataset, it is considered an anomaly if there are any non pedestrians present on the street, so as the biker enters the scene the regularity score drops indicating an irregular/anomalous event
![Test001VidAndPlot](https://github.com/user-attachments/assets/9ea24209-205d-4bd9-9e82-abfb7b68273a)

## Results

### Knowledge Distillation Evaluation

![1](https://github.com/user-attachments/assets/271e7c51-1002-4191-9bdf-60ee98cd84f4)

### Scores on PED1 Dataset

![2](https://github.com/user-attachments/assets/33941504-0f44-4a82-b487-6fb5a3ff037a)

### Scores on PED2 Dataset

![3](https://github.com/user-attachments/assets/070a5414-8318-4f75-8b74-bc6ddb7312ea)

### Comparison of AUC-ROC and EER values of different models on UCSD Ped1 and Ped2 Dataset
![4](https://github.com/user-attachments/assets/35eb86bf-0334-45c7-b960-b9621d75b985)






