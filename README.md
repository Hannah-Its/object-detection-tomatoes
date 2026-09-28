# Tomato Object Detection Using YOLO

## Project Overview

This project focuses on building an object detection model capable of detecting and locating tomatoes in images.

The project demonstrates an end-to-end computer vision workflow, including data collection, image annotation, dataset preparation, model training, validation, and inference.

The goal is to develop a practical machine learning solution that can identify tomatoes in agricultural images and provide bounding-box predictions around detected tomatoes.

---

Project Objective

The main objective of this project is to develop an object detection model that can:

* Detect tomatoes in images
* Locate each tomato using bounding boxes
* Provide confidence scores for predictions
* Demonstrate how computer vision can be applied to agricultural use cases

This project is also part of my machine learning portfolio, demonstrating practical experience in computer vision and object detection.

---

## Model

The project uses **YOLO (You Only Look Once)** for object detection.

### Model Configuration

* **Model:** YOLO11n
* **Task:** Object Detection
* **Number of classes:** 1
* **Class:** Tomato
* **Image size:** 640 × 640
* **Epochs:** 50
* **Batch size:** 4
* **Train/Validation split:** 80/20

The model was selected because YOLO provides an efficient approach for real-time object detection and is suitable for applications where both detection speed and accuracy are important.

---

## Data Annotation

The tomato images were manually annotated using **CVAT (Computer Vision Annotation Tool)**.

Each tomato was annotated using a bounding box surrounding the visible tomato.

The annotation process involved:

1. Uploading tomato images
2. Creating the `Tomato` label
3. Drawing bounding boxes around individual tomatoes
4. Reviewing annotations
5. Exporting the annotated dataset
6. Preparing the dataset for YOLO training

This step is important because the quality of annotations directly affects the quality of the trained detection model.

---

## Dataset

The dataset consists of tomato images collected for the purpose of training an object detection model.

Each annotated image contains one or more tomatoes.

The dataset was organized into training and validation sets using an approximately **80/20 split**.

### Dataset Structure

```text
dataset/
├── images/
│   ├── train/
│   └── val/
│
├── labels/
│   ├── train/
│   └── val/
│
└── data.yaml
```

The YOLO dataset configuration defines one object class:

```yaml
names:
  0: Tomato
```

---

## Training

The model was trained using the Ultralytics YOLO framework.

Example training configuration:

```python
from ultralytics import YOLO

model = YOLO("yolo11n.pt")

model.train(
    data="data.yaml",
    epochs=50,
    imgsz=640,
    batch=4
)
```

The training process allows the model to learn visual patterns associated with tomatoes and subsequently predict their locations in previously unseen images.

---

## Inference

After training, the model can be used to detect tomatoes in new images.

Example:

```python
from ultralytics import YOLO

model = YOLO("runs/detect/train/weights/best.pt")

results = model.predict(
    source="test_image.jpg",
    conf=0.25
)
```

The model returns:

* Bounding boxes
* Confidence scores
* Predicted class

---

## Results

The trained model was evaluated on validation and test images to assess its ability to detect tomatoes.

The evaluation includes:

* Precision
* Recall
* mAP (mean Average Precision)
* Detection confidence
* Visual inspection of predictions

### Example Prediction

*Add prediction images here after training.*

```text
results/
└── predictions/
    ├── prediction_01.jpg
    ├── prediction_02.jpg
    └── prediction_03.jpg
```

> More detailed performance metrics will be added as the model evaluation is finalized.

---

## Technologies Used

| Technology       | Purpose                             |
| ---------------- | ----------------------------------- |
| Python           | Programming language                |
| Ultralytics YOLO | Object detection model              |
| CVAT             | Image annotation                    |
| Jupyter Notebook | Experimentation and development     |
| GitHub           | Version control and portfolio       |
| Computer Vision  | Image analysis and object detection |

---

## Project Structure

```text
object-detection-tomatoes/
│
├── README.md
├── tomato_detection.py
├── requirements.txt
│
├── notebooks/
│   └── tomato_detection.ipynb
│
├── data/
│   └── README.md
│
└── results/
    └── predictions/
```

---

## How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/object-detection-tomatoes.git
```

### 2. Navigate to the project

```bash
cd object-detection-tomatoes
```

### 3. Install the required packages

```bash
pip install -r requirements.txt
```

### 4. Run the Python script

```bash
python tomato_detection.py
```

---

## Future Improvements

Future versions of this project could include:

* Increasing the size and diversity of the dataset
* Adding images captured under different lighting conditions
* Detecting tomatoes at different growth stages
* Classifying tomatoes as ripe and unripe
* Improving model accuracy through hyperparameter tuning
* Testing larger YOLO models
* Deploying the model as a web application
* Building a real-time tomato detection system
* Using object detection to estimate tomato counts in agricultural environments

---

## Potential Agricultural Applications

Computer vision-based tomato detection can potentially support agricultural workflows such as:

* Automated tomato counting
* Crop monitoring
* Yield estimation
* Harvest planning
* Agricultural robotics
* Quality inspection
* Precision agriculture

---

## About Me

I am a **Machine Learning Engineer** interested in building practical machine learning and artificial intelligence solutions.

My interests include:

* Machine Learning
* Computer Vision
* Natural Language Processing
* Generative AI
* Data Annotation
* AI Data Quality
* AI Evaluation
* Applied AI

This project is part of my growing machine learning portfolio, where I document practical projects and experiments.

---

## Project Status

**Status:** Completed — Initial Model

Further improvements and experiments will be added as the project develops.

---

## License

This project is available for educational and portfolio purposes.
