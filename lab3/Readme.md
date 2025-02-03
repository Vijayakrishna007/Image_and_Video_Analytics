## Overview

The process involves segmenting the target image to isolate potential objects, extracting relevant features (area, centroid, aspect ratio, and average color) 
from each segmented region, and comparing these features to a reference object's features.  A distance metric is used to determine the similarity between objects. 
If a close match is found, the object is labeled accordingly. The extracted features and labels are then saved to a CSV file, creating a labeled dataset.

## Features

* **Image Segmentation:** Uses HSV color space thresholding to create masks for the target objects (apples and oranges).  Morphological operations (opening) are applied to refine the masks.
* **Feature Extraction:** Extracts the following features from each segmented object:
    * Area: Number of pixels within the object's contour.
    * Centroid: The center point (x, y coordinates) of the object.
    * Aspect Ratio: The ratio of the object's width to its height.
    * Average Color: The average RGB color of the pixels within the object's mask.
* **Object Detection:**
    * Reference Object: Requires a reference image of the object to be detected.  Features are extracted from this reference object.
    * Feature Comparison: Uses Euclidean distance to compare features between the reference object and segmented regions in the target image.
    * Object Localization: Identifies and locates the target object by drawing bounding boxes and marking centroids.
* **Labeled Dataset Creation:** Generates a CSV file (`labeled_dataset.csv`) containing the extracted features (Area, Centroid_X, Centroid_Y, Aspect_Ratio, Average_Color) 
     and the assigned label for each detected object.
* **Visualization:** Displays the original images, masks, and the final image with detected objects, bounding boxes, centroids, and labels.
