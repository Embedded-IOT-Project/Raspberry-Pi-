# Raspberry Pi Flask Video Streaming with Face and QR Detection


## 🧠 Why Use Raspberry Pi?

Raspberry Pi 3 B+ is used in this project as a powerful yet affordable alternative to platforms like Pixy and ESP32. 

Pixy and ESP32, while suitable for lightweight detection tasks, often struggle with real-time streaming and image processing due to limited processing power and RAM. In testing, both platforms exhibited significant lag when handling live face or QR detection streams, especially when combined with camera and network tasks.

Raspberry Pi offers smoother performance for real-time video analysis and web streaming using OpenCV and Flask, with better support for USB webcams, multitasking, and Python libraries.

It provides a more stable and scalable solution for projects requiring moderate to complex computer vision without needing an external PC or cloud processing.
---


This project demonstrates real-time live video streaming on a **Raspberry Pi 3 B+** using a **USB webcam**, **Flask**, and **OpenCV**. The system supports three modes:

- `face_stream.py` – Detects human faces only  
- `qr_stream.py` – Detects QR codes only  
- `face_qr_stream.py` – Detects both faces and QR codes simultaneously  

All streams are viewable in any browser or Android app that supports `WebView`.

> ✅ Built and tested on **Raspberry Pi 3 B+** running **Raspberry Pi OS 32-bit (Full)** using **Thonny IDE**.

---

## 🧰 Hardware Requirements

- Raspberry Pi 3 B+  
- Raspberry Pi OS 32-bit (Full version recommended)  
- USB Webcam  
- Internet connection (for installing libraries)  
- Haar Cascade XML file for face detection ([Download from OpenCV GitHub](https://github.com/opencv/opencv/blob/master/data/haarcascades/haarcascade_frontalface_default.xml))  

---

## ⚙️ Initial Setup Instructions

1. Open the **Terminal** on the Raspberry Pi
2. Run the following commands:



1.sudo apt update

2.sudo apt install libzbar0

3.pip3 install flask opencv-python pyzbar --break-system-packages

Download and place the Haar Cascade file in a folder like:

/home/pi/Desktop/streaming


Update the path in your Python scripts as:


face_detector = cv2.CascadeClassifier('/home/pi/Desktop/streaming/haarcascade_frontalface_default.xml')

---

🚀 Running the Project
Open Thonny on Raspberry Pi

Load one of the Python files:

face_stream.py

qr_stream.py

face_qr_stream.py

Press the green Run button or press F5

Once the server is running, open a browser on any device connected to the same Wi-Fi network and go to:


http://your-raspberry-pi-ip:5000


---


🖥️ Output
You will see a live video stream showing:

Face detection

QR code detection

Or both, depending on which script you use

Face crops will be saved automatically in the detected_faces folder.

---

Webcam not detected?
Make sure it's plugged in and check with:


ls /dev/video*


Default device is /dev/video0. You can aslo try 1 if another camera is being used.

---


📏 Performance Tip


The video resolution is set to 640x480 for a good balance of speed and accuracy. You can change this in the code using OpenCV’s cv2.resize() or by setting:


camera.set(cv2.CAP_PROP_FRAME_WIDTH, 640)

camera.set(cv2.CAP_PROP_FRAME_HEIGHT, 480)


written by
SHIVESH
