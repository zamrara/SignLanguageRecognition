# SignLanguageRecognition

This repository contains a variety of tools to build up a system for recognizing signs of the german sign language (DGS).
The idea is to provide a live translation on a webcam stream. This could be on mobile or desktop.
For this we train a deep learning model (RNN) for predicting the actual signs made by a person filmed.
Therefore we use [MediaPipe](https://github.com/google/mediapipe), a framework for building ML pipelines, to extract face and hand positions, including multiple coordinates for each finger.

## Installation

1. Clone the repository.
2. Follow the instructions to [install MediaPipe](https://github.com/google/mediapipe/blob/master/mediapipe/docs/install.md).
3. To work with our `jupyter notebooks`, we recommend to install [Anaconda](https://www.anaconda.com/).
4. Install `TensorFlow 2.0` with `conda`, see <https://anaconda.org/anaconda/tensorflow-gpu>

## Workflow

### 1. Gathering video examples

For training we need many videos for each sign, we want to predict. Those examples are generated by users of our platform [Gebärdenfutter](https://gebaerdenfutter.de).

### 2. Extracting face and hand positions

For extracting multi hand and face detections for each frame of the videos and saving them, we built a pipeline with `MediaPipe`, e.g. have a look at the `DetectionsToCSVCalculator`, we implemented. It simply writes out the detections made by `MediaPipe` to CSV files.

### 3. Training deep learning model

The CSV files are used to train a deep learning model with `Keras`, a high level API for `TensorFlow`.
Therefore we use jupyter notebooks to simply write and comment scripts.
Check out the folder `lab`.

### 4. Live prediction

The trained model is used for predicting live video stream.
Therefore another `MediaPipe` pipeline was build.
***To be continued***
