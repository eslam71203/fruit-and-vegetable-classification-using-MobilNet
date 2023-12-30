# fruit-and-vegetable-classification-using-MobilNet

## Overview
This project focuses on building a deep learning model for recognizing and classifying images of various fruits and vegetables. The goal is to create a system that can identify different food items from images, enabling applications such as recipe recommendation based on captured photos.

## Dataset
The dataset used for this project contains images of fruits and vegetables, including banana, apple, carrot, cucumber, etc. The images are divided into training, testing, and validation sets.

### Data Collection
The dataset was collected by scraping images from Bing Image Search for the purpose of building an image recognition application.

## Getting Started
### Prerequisites
- Python (3.x)
- TensorFlow
- NumPy
- Matplotlib
- Pandas

### Installation
```bash
pip install -r requirements.txt
```

### Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/fruit-and-vegetable-image-recognition.git
   ```

2. Change to the project directory:
   ```bash
   cd fruit-and-vegetable-image-recognition
   ```

3. Run the image recognition script:
   ```bash
   python recognize_image.py path/to/your/image.jpg
   ```

## Model Architecture
The model architecture is based on transfer learning using MobileNetV2 as the base model, with additional dense layers for classification.

```python
# Code snippet for model creation
import tensorflow as tf
from tensorflow.keras.applications import MobileNetV2

pretrained_model = MobileNetV2(input_shape=(224, 224, 3), include_top=False, weights='imagenet', pooling='avg')
pretrained_model.trainable = False

x = tf.keras.layers.Dense(128, activation='relu')(pretrained_model.output)
x = tf.keras.layers.Dense(128, activation='relu')(x)
outputs = tf.keras.layers.Dense(num_classes, activation='softmax')(x)

model = tf.keras.Model(inputs=pretrained_model.input, outputs=outputs)
model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])
```

## Training
The model is trained on the provided dataset using TensorFlow's ImageDataGenerator for data augmentation.

```bash
python train_model.py
```

## Evaluation
Model performance is evaluated on the test dataset, and a classification report is generated.

```bash
python evaluate_model.py
```

## Inference
To use the trained model for inference on a new image, you can utilize the `output` function.

```python
from your_module import output

result = output('path/to/your/image.jpg')
print(f'The predicted class is: {result}')
```

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Dataset source: [Your Dataset Source]

Feel free to customize and extend this template based on your project specifics. Ensure to include detailed information about your project, how to install and use it, and any additional resources or acknowledgments.
```
