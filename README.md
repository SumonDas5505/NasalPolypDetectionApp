# Nasal Polyp Detection App
# Computer Vision mini-project

This cross‑platform application uses a lightweight AI model to detect nasal polyps from endoscopic images. Users can capture or upload a photo of the nasal cavity, send it to an inference API and receive bounding boxes and confidence scores indicating potential polyps. The model was trained using YOLOv5 and converted to TensorFlow Lite, making it efficient enough for mobile deployment. The Flutter client was developed using Android Studio with Dart.

Tech Stack
Component	Purpose	Evidence
YOLOv5 training	The detection model (best-fp16.tflite) originates from a YOLOv5 object‑detection training pipeline and was later converted to TFLite. This training code is external to the repository.	Developer-provided information
Android Studio	Flutter and Dart code for the mobile client were written and debugged using Android Studio.	Developer-provided information
Flutter & Dart	Cross‑platform UI and logic are implemented in Flutter. The app uses stateful widgets and routing via Navigator to handle screens for the welcome page, image upload/scan and result display.	lib/main.dart shows Flutter UI code
Packages	The app depends on image_picker for camera/gallery access, http for API requests and tflite (declared for potential on‑device inference).	pubspec.yaml dependencies
TensorFlow Lite model	A pre‑trained TFLite model (best-fp16.tflite) and a labels file are included in the assets folder.	Asset declarations in pubspec.yaml
Backend API	The client sends selected images via HTTP POST to a prediction endpoint (e.g., http://10.0.2.2:5000/predict) and parses JSON responses to extract bounding boxes and confidence scores.	HTTP call in main.dart
Features

Image capture & upload: Users can take a picture or choose an existing image using the image_picker plugin.

AI‑powered detection: The app sends the image to a Flask-based API, which returns JSON with bounding box coordinates and confidence levels. This information is displayed to the user with a cautionary note that the model is for research purposes only.

Simple workflow: A welcome screen guides users to the scan page. After uploading, they are navigated to a results page that lists detections and confidence scores.

Cross‑platform: Built in Flutter, the app can run on Android, iOS, web and desktop without code changes.

How it works

Capture or select an image.
On the scan page, buttons invoke the camera or gallery via image_picker.

Upload to the inference server.
The chosen image is wrapped in a multipart HTTP POST request and sent to the /predict endpoint.

Receive model output.
The server, powered by a YOLOv5-trained model converted to TFLite, returns a JSON payload with bounding boxes and confidence scores.

Display results.
The app decodes the JSON and lists the detection results for the user, along with a disclaimer that the model is experimental.

Note

The detection model and training scripts are not part of this repository. The model (best-fp16.tflite) was created externally by training a YOLOv5 object detector and converting it to TFLite format. This app is intended for educational and research purposes and should not be used as a substitute for professional medical diagnosis.
