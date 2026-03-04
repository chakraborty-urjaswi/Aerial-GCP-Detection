# Aerial-GCP-Detection
# Aerial GCP Detection & Classification

## 1. Approach
For this challenge, I used a **Multi-Task ResNet-18** model. This architecture uses a shared backbone to extract features, which are then fed into two separate "heads":
* **Classification Head:** Predicts the shape (Square, Cross, L-Shaped).
* **Regression Head:** Predicts the precise $(x, y)$ coordinates.

## 2. Training & Dataset Insights
Based on my Exploratory Data Analysis (EDA):
* **Brightness:** The dataset is well-balanced (~50% brightness), requiring no heavy radiometric correction.
* **Edge Strength:** Cross markers have $2.4\times$ stronger edges than Squares. I used **SmoothL1Loss** for regression to handle the "fuzzier" localization of Square markers.
* **Spatial Distribution:** Markers appear throughout the frame, so I used full-image resizing instead of center cropping.

## 3. Model Weights
The trained model weights (`.pth` file) are too large for GitHub and are hosted on Google Drive:
* **[Download Model Weights Here](https://drive.google.com/file/d/1LtrFRRo69rtMnX-sAZIPU38ST4nx7e5I/view?usp=sharing)**

## 4. How to Reproduce Results
1. Download the `gcp_model_weights.pth` from the link above.
2. Place the weights in the root directory.
3. Run the final cell in `Aerial_GCP_Detection.ipynb` to generate the `predictions.json` file.
