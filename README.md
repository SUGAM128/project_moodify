# Moodify: Music Recommendation Using Facial Expressions

Overview:
Moodify is a real-time music recommendation system that uses facial emotion detection to suggest playlists. A CNN model trained on the FER-2013 dataset identifies seven emotions from live video input. Based on the detected mood, the app uses the Spotipy API to fetch and recommend playlists from Spotify.

Features:
- Real-time facial expression detection
- Automatic music recommendations based on predicted mood
- Playlists fetched using the Spotipy API

How to Run:
1. Install dependencies: pip install -r requirements.txt
2. Enter your Spotify Developer credentials in spotipy.py under auth_manager
3. Run the application: python app.py
4. Allow camera access when prompted

Tech Stack:
- Python, Flask, Bootstrap
- TensorFlow, Keras
- Spotipy API
- OpenCV

Dataset:
- FER-2013 dataset from Kaggle: https://www.kaggle.com/msambare/fer2013
- Contains seven emotion classes (e.g., happy, sad, angry)
- Dataset imbalance exists, with the “happy” class being dominant, which may affect accuracy

Model Architecture:
- Sequential CNN model with Conv2D, MaxPooling2D, Dropout, and Dense layers
- Conv2D layers: 32–128 filters with ReLU activation
- Pooling layers: size (2,2)
- Dropout rate: 0.25
- Final Dense layer: Softmax activation for 7-class classification
- Loss: categorical_crossentropy
- Optimizer: Adam
- Metric: Accuracy

Training and Performance:
- Images resized to 48x48 grayscale using Keras ImageDataGenerator
- Batch size: 64
- Trained for 75 epochs (~13 hours locally)
- Achieved ~66% accuracy on FER-2013

Current Status:
- Application runs successfully with real-time detection
- Multithreading ensures smooth video streaming with good frame rates

Project Components:
- spotipy.py – Spotify integration for fetching songs
- haarcascade – Face detection
- camera.py – Video streaming, frame capturing, emotion prediction, and recommendation
- main.py – Flask application entry point
- index.html – Frontend interface with basic HTML and CSS
- utils.py – Utility module for webcam streaming and threading
- train.py – Model training script
