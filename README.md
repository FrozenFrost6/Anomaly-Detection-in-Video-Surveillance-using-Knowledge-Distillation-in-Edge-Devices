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

## Methodology
	The system uses a technique called Knowledge Distillation to perform this task. 
 	Knowledge Distillation is a technique in machine learning where knowledge
	from a more complex model, known as the teacher model, is transferred to a
	simpler model, known as the student model. The primary objective of KD is to
	create a student model that can mimic the behavior and predictions of the teacher
	model, typically with fewer parameters and computational resources.

![knowledgeDistillation](https://github.com/user-attachments/assets/7185248e-231f-40d0-97dc-4efa2ddbb883)

 	Using this technique, we trained multiple models and tried to achieve optimal scores.

## Demonstration
	For the given dataset, it is considered an anomaly if there are any non pedestrians present on the street, 
 	so as the biker enters the scene the regularity score drops indicating an irregular/anomalous event
![Test001VidAndPlot](https://github.com/user-attachments/assets/9ea24209-205d-4bd9-9e82-abfb7b68273a)





