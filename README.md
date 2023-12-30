# Fruit-and-vegetable-classification-using-MobilNet
## Overview
This project focuses on building a deep learning model for recognizing and classifying images of various fruits and vegetables. The goal is to create a system that can identify different food items from images, enabling applications such as recipe recommendation based on captured photos.

## Dataset
The dataset used for this project contains images of fruits and vegetables, including banana, apple, carrot, cucumber, etc. The images are divided into training, testing, and validation sets.

### Data Collection
The dataset was collected by scraping images from Bing Image Search for the purpose of building an image recognition application.

## Getting Started
### Prerequisites
- Python (3.11)
- TensorFlow
- NumPy
- Matplotlib
- Pandas
- Flask

### Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/Islam Nasser Saeed/fruit-and-vegetable-image-recognition.git
   ```

2. Change to the project directory:
   ```bash
   cd fruit-and-vegetable-image-recognition
   ```

3. Run the Streamlit application:
   ```bash
   streamlit run streamlit_app.py
   ```

4. Explore the Flask API (Optional):
   ```bash
   python flask_api.py
   ```

## Streamlit Application
The Streamlit application allows users to upload an image, make predictions, and get information about the predicted food item's category and calories.

## Flask API
The Flask API provides an endpoint (`/predict`) for making predictions on images. You can send a POST request to this endpoint with an image file attached, and the API will return a JSON response with the predicted class.

Example using `requests` in Python:
```python
import requests
from PIL import Image
from io import BytesIO

# Load an image
image_path = 'path/to/your/image.jpg'
image = Image.open(image_path)

# Convert the image to bytes
image_bytes = BytesIO()
image.save(image_bytes, format='JPEG')
image_bytes = image_bytes.getvalue()

# Send a POST request to the API
url = 'http://127.0.0.1:5000/predict'  # Update with your API endpoint
files = {'file': ('image.jpg', image_bytes, 'image/jpeg')}
response = requests.post(url, files=files)

# Print the prediction
print(response.json())
```

Ensure to update the API endpoint and adjust the code based on your specific project structure.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Dataset source: https://www.kaggle.com/datasets/kritikseth/fruit-and-vegetable-image-recognition
```

Feel free to customize and extend this template based on your project specifics. If you have any specific information you'd like to add or modify, please do so accordingly.
