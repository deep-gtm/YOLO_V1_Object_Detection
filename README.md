# YOLO (You Only Look For Once) V1 Object Detection
- I used Pascal VOC 2012 For Training of this project
  
![image](https://github.com/deep-gtm/YOLO_V1_Object_Detection/assets/70434931/60958917-945d-4718-bf32-092c8d20de49)
![image (1)](https://github.com/deep-gtm/YOLO_V1_Object_Detection/assets/70434931/446963fa-535b-4877-bde7-ebcee1b6a62d)

# Running Prototype of this project 
https://huggingface.co/spaces/deep42/YOLO_V1_Object_Detection

# What is Object Detection ?
Object detection is a computer vision task where a computer identifies and locates objects within images or videos.
- Localizing Objects: Predicting bounding boxes around objects to show where they are in the image.

- Classifying Objects: Assigning labels to these objects to say what they are (e.g., car, person, dog).

- Post-processing: Cleaning up multiple detections and low-confidence results.
  
# What is YOLO
- YOLO stands for "You Only Look Once," and it's a deep learning-based object detection algorithm.
- YOLO is designed to quickly and accurately detect objects within images or video frames.
- The key idea behind YOLO is that it performs object detection in a single pass, predicting both object bounding boxes and class probabilities directly from the entire image, rather than using a multi-stage approach.
- It treat's obejct detection as a Regression Task

# Key Points Of Yolo
- Unified Detection:
  
  - YOLO takes an image as input and divides it into a grid of cells.
  - Each cell is responsible for detecting objects that are located within its boundaries.
- Bounding Box Prediction:
  - In each grid cell, YOLO predicts multiple bounding boxes along with their associated confidence scores.
  - Each bounding box is defined by its center coordinates, width, height, and confidence score.
- Class Prediction:
  - Along with bounding box predictions, YOLO predicts class probabilities for each object category.
  - These class probabilities are calculated using softmax activation.

- Single Forward Pass:
  - Unlike traditional object detection approaches that involve multiple passes through the network, YOLO performs all predictions in a single forward pass.
  - This makes YOLO much faster and suitable for real-time applications.
 
- Anchor Boxes:
  - YOLO uses anchor boxes of various sizes and aspect ratios to improve the accuracy of bounding box predictions.
  - These anchor boxes help YOLO adapt to different object sizes and shapes.
 
- Non-maximum Suppression (NMS):
  - After predictions are made, YOLO applies non-maximum suppression to remove duplicate or overlapping detections, retaining only the most confident ones.

 # Yolo Loss
 It's most important part of yolo algorithm, Here are key points about yolo loss :

- Localization Loss:
  - Measures how well predicted bounding box coordinates match ground truth.
  - Calculates the Mean Squared Error (MSE) between predicted and ground truth coordinates (x, y, width, height).
  - Encourages the model to accurately predict the position and size of objects.
  - Weighted by λ_coord to balance its impact with confidence loss.
  
- Confidence Loss (Objects):
  - Evaluates how well predicted confidence scores match ground truth for grid cells containing objects.
  - Confidence score indicates whether the predicted bounding box contains an object.
  - The confidence loss uses MSE to align predicted and ground truth confidence scores.
  - Encourages the model to predict high confidence scores when the object is present.

- Confidence Loss (No Objects):
  - Measures predicted confidence scores for grid cells without objects.
  - Encourages the model to predict low confidence scores for empty cells.
  - Weighted by λ_noobj to balance its impact with confidence loss for cells with objects.
 
- Classification Loss:

  - Measures the accuracy of predicted class probabilities compared to ground truth class labels.
  - YOLO v1 predicts class probabilities for each object category within each grid cell.
  - Calculated using cross-entropy loss, quantifying the difference between predicted and ground truth probabilities.
  - Ensures the model accurately identifies the type of object present in each cell.
 

The total loss function in YOLO v1 is a combination of these four components, with appropriate weights (λ_coord, λ_noobj) applied to balance their influences. This comprehensive loss function guides the training of the YOLO model to accurately predict object bounding box positions, confidence scores, and class probabilities while considering the presence or absence of objects within grid cells.

