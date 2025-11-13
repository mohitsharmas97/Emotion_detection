<img width="666" height="757" alt="image" src="https://github.com/user-attachments/assets/2ff62687-1672-4d7a-864a-f2737345461f" />#  Real-Time Emotion Detection – Flask + OpenCV + ConvNeXt

A real-time facial emotion detection system built using Deep Learning (PyTorch), OpenCV, and Flask.
The model identifies emotions directly from your webcam feed, draws bounding boxes, and displays the predicted emotion with confidence scores.
---

## Key Features

- Live webcam feed streamed through Flask
- ConvNeXt Tiny deep-learning model for emotion classification
- Six-emotion recognition (happy, sad, angry, etc.)
- Uses extensive **image augmentation**
- Face detection using Haar Cascade
- Real-time inference using PyTorch
- Web-based interface (index.html)

---

##  Model Overview

- ConvNeXt-Tiny (PyTorch) → trained on the FER2013 dataset
- **Output Layer**: Modified to output 6 classes
- OpenCV Haar Cascade → real-time face detection

##Supported Emotion Classes
  | Label    | Description |
  | -------- | ----------- |
  | angry    | 😠 Angry    |
  | fear     | 😨 Fear     |
  | happy    | 😄 Happy    |
  | neutral  | 😐 Neutral  |
  | sad      | 😢 Sad      |
  | surprise | 😲 Surprise |

## Architecture

```mermaid
flowchart TD

A[User Browser] -->|Request Homepage| B[Flask Server]

B -->|Serve index.html| A

A -->|Request /video_feed| C[Streaming Route]

C --> D[Generate Frames]

D --> E[Webcam Input]

E -->|Frame| F[Haar Cascade Detector]

F -->|Face ROI| G[Convert to PIL]

G -->|Transforms| H[PyTorch Preprocessing]

H --> I[ConvNeXt Tiny Model]

I -->|Emotion + Confidence| J[Overlay on Frame]

J -->|JPEG Encode| C

C -->|MJPEG Stream| A
```
